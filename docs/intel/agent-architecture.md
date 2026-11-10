---
title: "agent architecture"
type: source
tags: [hackathon, genai-summit, recon, intel]
aliases: ["agent architecture"]
created: 2026-11-10
updated: 2026-11-10
status: active
---

# Self-Sufficient Agent — Cross-Sponsor Architecture
Gen AI Summit Hackathon, Athens, 14–15 Nov 2026 · Design date: Nov 10 2026
Thesis: **an agent that provisions its own compute (boxd fork), buys its own tools (treg), drives its own browser (Firecrawl), and thinks with models we trained (Oumi)** — built by Devin. Every sponsor is a load-bearing organ, not a badge.

---

## 0. Architecture diagram (text)

```
                         ┌──────────────────────────── OUR LAPTOP (stage UI) ───────────────────────────┐
                         │  demo UI: goal input · DAG view · live browser iframes · spend ledger ·      │
                         │  signed action log · APPROVE button (human gate)                             │
                         └───────▲───────────────────────────────────────────────▲──────────────────────┘
                                 │ SSE/poll (status, costs, liveViewUrls)         │ POST /approve
┌────────────────────────────────┴─────────────────────────────────────────────────────────────────────┐
│                         boxd machine  hq.boxd.sh  (2vCPU/8GiB, auto-hibernate OFF)                   │
│  ┌───────────────────────────────────────────────────────────────────────────────────────────────┐ │
│  │ COORDINATOR (Python, FastAPI)                                                                 │ │
│  │  · planner SLM  ── Oumi-FT Qwen3.5-0.8B, llama.cpp/vllm-mlx, localhost:8001/v1                  │ │
│  │    goal → task DAG (JSON, parallel leaves only fork)                                          │ │
│  │  · verifier SLM ── Oumi-FT, localhost:8002/v1   step output → VALID/INVALID+reason              │ │
│  │  · dispatcher: boxd.machines.fork() per parallel workstream                                   │ │
│  │  · budgeter: per-worker treg pinned token + X-Treg-Route-Max-Cost                             │ │
│  │  · ledger + hash-chained action log (ed25519-signed JSONL → /work/log.jsonl)                  │ │
│  │  · human gate: writes/irreversible calls queue until UI approval                              │ │
│  └───────┬───────────────────────┬───────────────────────┬───────────────────────────────────────┘ │
│          │ fork (<200ms, CoW: code+deps+auth inherit)                                              │
│  ┌───────▼───────┐       ┌───────▼───────┐       ┌───────▼───────┐                                 │
│  │ worker-1      │       │ worker-2      │       │ worker-3      │   each = full Linux VM           │
│  │ (research)    │       │ (enrichment)  │       │ (browse)      │   w/ own IP, browser, budget     │
│  └─┬─────────┬──┘       └─┬─────────┬───┘       └─┬─────────────┘                                 │
└────┼─────────┼────────────┼─────────┼─────────────┼────────────────────────────────────────────────┘
     │         │            │         │             │
     │   treg.to│            │  treg.to│             │ api.firecrawl.dev
     │  catalog_search → catalog_get → /call/<id>      │ POST /v2/interact → {id, liveViewUrl,
     │  (X-Treg-Token pinned per worker,               │   interactiveLiveViewUrl}
     │   X-Treg-Route-Max-Cost cap,                    │ /v2/interact/{id}/execute (playwright)
     │   X-Treg-Cost-Micro receipt → ledger)           │ DELETE on done · 2cr/browser-min
     │         │            │         │             │
     ▼         ▼            ▼         ▼             ▼
 result.json written to /work/out/<task>.json  +  POST https://hq.boxd.sh/status (heartbeat)
        parent pulls artifacts via boxd.machines.fs / exec (pull model = no inbound deps)
```

---

## 1. boxd fork-swarm

**API shape (Python SDK, `BOXD_API_KEY`):**
```python
boxd = Boxd()
hq  = boxd.machines.create(name="hq")
boxd.machines.set_auto_hibernate_timeout(hq.id, 0)   # CRITICAL: hibernate watches net traffic, not CPU
forks = [boxd.machines.fork("hq", f"worker-{i}") for i in range(n)]  # <200ms each, CoW mem+disk+procs
boxd.machines.exec(fid, ["python3", "/work/worker.py", task_json])
art   = boxd.machines.fs.read(fid, "/work/out/result.json")          # pull artifacts, no inbound needed
boxd.machines.delete(fid)                                             # or deleteSelf() from inside
```

**"Agent spawns agents" — the legit version:** in-machine boxd CLI is *pre-authenticated* — the lead agent on hq can literally run `boxd machine fork hq worker-3` itself mid-task. Demo beat: the agent's own tool call list includes `spawn_clone`.

**Parent↔child comms (recommended hybrid):**
- **Task down:** `exec` argv / write `/work/in/task.json` via fs API post-fork (fork inherits the warm disk — deps, treg CLI auth, Firecrawl key, cloned repo — then diverges; NOT a shared FS).
- **Status up (push):** worker POSTs heartbeats to `https://hq.boxd.sh/status` (every machine gets its own HTTPS URL; put hq + workers on a boxd `network` for VM-to-VM if you want it private).
- **Artifacts up (pull):** parent reads `/work/out/*.json` via `machines.fs`. No inbound networking, no auth, survives flaky push.
- **Skip:** Redis/SQS — overkill for ≤8 nodes / 36h. Files + one HTTP endpoint win.

**Concurrency reality:** org cap = **2 machines without a payment method → add card NOW** (still free, €30 credits ≈ 1,000 machine-h at ~€0.03/h). With card: 50 machines/org default, raisable same-day via `contact@boxd.sh`. Forks count toward cap. Demo uses ≤6 (hq + 3 workers + 1 spare + 1 pre-warmed fork).

**Legit vs gimmick — the on-stage answer:** fork only when workstreams are (a) parallel, (b) independent, (c) profit from inherited warm state (installed deps, authed CLIs, warm browser profile). "Why not threads?" — *isolation + blast radius + each clone is a whole computer with its own IP, browser, and treg budget; a worker can nuke itself and hq doesn't notice.* Serial/dependent steps stay in-process — planner DAG enforces it (visible in UI: judges see we chose deliberately).

## 2. treg mid-task purchase

**The loop (MCP `catalog_search`→`catalog_get`→`call`, or HTTP `GET https://treg.to/call/<id>`):**
```bash
treg catalog search "verify a work email"        # tools + prices, unauthenticated
treg catalog get hunter.people.email.verify      # params, price, measured `works`%/`p50`
curl "https://treg.to/call/hunter.people.email.verify?email=x@y.z" \
  -H "X-Treg-Token: $TREG_TOKEN" -H "X-Treg-Route-Max-Cost: 0.05"
# → response headers: X-Treg-Cost-Micro: 3400  ·  X-Treg-Call-Id: cl_...   (→ ledger row on UI)
```
**Payment model:** prepaid fiat balance (Stripe `/billing/topup`), NOT crypto. Agent = wallet holder: team token + $20/builder hackathon credit. Per-worker attribution via pinned tokens (`treg org agent-new worker-2 --pin customer=worker-2`) → per-clone spend column in the ledger. **Budget-cap:** `X-Treg-Route-Max-Cost` per call (→ `402 route_max_cost`, nothing charged) + coordinator-side per-worker ceiling; `402 insufficient_balance` returns machine-readable `{balance_micro, estimated_cost_micro, topup_url}` — agent can *show* it reacting to being broke.
**The moment (script it):** worker hits unknown capability → "no local tool" → `catalog_search` → price table visible → **BUY → `X-Treg-Cost-Micro` receipt ticks the balance down live** → call → result. Zero-friction fallback: `POST /demo/sandbox` mints a throwaway treg sandbox, no signup.

## 3. Firecrawl /interact

Standalone browser: `POST /v2/interact` → `{id, cdpUrl, liveViewUrl, interactiveLiveViewUrl}` → `POST /v2/interact/{id}/execute` (Playwright node/python, or `agent-browser` bash) → `DELETE`. Scrape-bound variant: `/v2/scrape` → `scrapeId` → `/v2/scrape/{id}/interact` (inherits profile/auth state — use for login-walled targets). Cost 2cr/browser-min. **UI:** embed `liveViewUrl` in an iframe per worker — judges watch 3 browsers move in parallel; `interactiveLiveViewUrl` = click-to-take-over (human-in-the-loop garnish). Free tier: keyless works, **2 concurrent browsers, 2/min interact** → pace sessions; Hobby $19 = 5 conc / 20/min — buy it or STUDENTEDU (10K cr) before Saturday. Screenshot fallback: `page.screenshot()` → serve stills if live stream dies on venue wifi.

## 4. Orchestration pattern

```
goal → [planner SLM] task DAG (JSON) → [dispatcher] fork-per-parallel-leaf
     → workers {treg tools, firecrawl} → [verifier SLM] VALID/INVALID+reason (retry≤1)
     → hash-chained signed action log → human gate (writes only) → artifact + cost report
```
- **Planner:** Oumi-FT Qwen3.5-0.8B (full FT on MPS or Platform SFT $0.49/1Mtok, $50 free credits). Output = typed DAG JSON. Serve `llama.cpp`/`vllm-mlx` on hq — <100ms/hop, no cloud dependency.
- **Verifier:** second Oumi-FT SLM checks every tool/browse result before commit; HallOumi-8B-classifier as base (CC BY-NC — fine for demo). **The Banking77-style table is mandatory:** your-SLM vs GPT-5.x/Claude on routing+verification, accuracy·p50·$/1k.
- **Signed action log:** JSONL, `prev_hash` chain + ed25519 signature per entry, written inside hq (disk persists on forks), re-verifiable on stage — Zindros bait.
- **Human gate:** reads run free; writes (send/post/purchase-over-cap) queue → UI APPROVE. Containment metric on screen = Wonderful/Quintessential bait.

## 5. Failure modes & fallbacks (stage-hardened)

| Component | Stage risk | Fallback |
|---|---|---|
| Venue wifi | everything | Phone hotspot backup; coordinator+SLMs local on hq — only sponsor APIs need net. Pre-recorded 90s video of full run as last resort |
| boxd | org cap (no card → 2 machines) | **Add card pre-event.** API down → workers become local subprocesses on hq (same protocol, degraded visual, honest) |
| boxd | auto-hibernate mid-run | `set_auto_hibernate_timeout(id,0)` + `set_idle_ignore_outbound`; pre-fork a warm worker before demo |
| treg | empty balance | Top to $20 Sat AM; cap `X-Treg-Route-Max-Cost`; `402` body is machine-readable → agent narrates "I'm out of budget" (recovers as a *feature*) |
| treg | catalog miss / upstream dead | Routed `treg.<capability>` endpoints waterfall automatically; cache 3 pre-searched tools (known-good ids) as scripted targets |
| Firecrawl | free tier: 2 conc browsers, 2/min | Hobby key ($19) or STUDENTEDU 10K cr pre-redeemed; serialize browser use; screenshot stills if liveView streams drop |
| Firecrawl | target site blocks/changes | Pick resilient fixture (gov/data site, not Instagram); `maxAge` cache on scrapes |
| Oumi SLM | misroutes on live goal | Retry via verifier rejection; frontier model as stated fallback router — SLM still gets the first shot (narrative intact: "SLM-first, frontier-backstop") |
| Cold start | fork/model warm-up | Everything pre-warmed: hq up 30min prior, llama.cpp loaded, one fork already made and deleted |

## 6. Feasibility — honest verdict

**Full swarm in 36h = over-scope.** MVP that still shows every sponsor:
**1 goal → planner DAG (3 leaves) → 2–3 forks → exactly 1 visible treg purchase → 1 live browser → verifier → 1 human-gated write → signed log + cost ledger.** All 5 sponsors, ~4 min demo. Stretch (only if Sun AM looks good): N>3 forks, second purchase, hibernate/resume mid-task beat, weights-lab edit.

### Component → sponsor map
| Piece | Sponsor | Surface |
|---|---|---|
| fork-swarm compute | **boxd** | fork API, per-clone VMs, `*.boxd.sh` URLs, €30 credits |
| tool marketplace + wallet | **treg** | catalog_search/get/call, X-Treg-Cost-Micro receipts, $20/builder |
| live browser | **Firecrawl** | /interact liveViewUrl iframes, STUDENTEDU 10K |
| planner + verifier SLMs | **Oumi** | train/eval/serve, the beat-frontier table, $50 credits |
| built by | **Devin** | harness coded visibly by agent; "agent built by an agent" |
| (fixture data) | Greek vertical | pick Sat 12:xx from mentor briefs (diavgis/Prosperty/maritime) |

### Build order
**Pre-Sat (boilerplate-legal, do NOW):** boxd card+credits, kill-hibernate script, treg token+$20, Firecrawl key (STUDENTEDU/Hobby), Oumi $50 acct; train router+verifier on synthetic planner/verify JSONL; harness skeleton (coordinator, ledger, signer, gate) in repo.
**Sat 12–15:** mentor tables → lock fixture; hq up; e2e skeleton w/ mocked treg/firecrawl (fork + exec + collect real).
**Sat 15–02:** real treg purchase loop + receipt UI; real /interact + iframe; SLMs wired at :8001/:8002; DAG view.
**Sun 09–15:** verifier loop + retry; signed log; human gate; fallbacks; cost ledger polish.
**Sun 15–18:** 3× full rehearsal on venue wifi + hotspot; record backup video; submit 18:00.

**One-line pitch:** "We gave an agent a wallet, a browser, and the ability to photocopy itself — then made two small models we trained decide whether that's a good idea."
