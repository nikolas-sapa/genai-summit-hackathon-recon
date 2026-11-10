---
title: "sponsor infra plumUing"
type: source
tags: [hackathon, genai-summit, recon, sponsors]
aliases: ["sponsor infra plumUing"]
created: 2026-11-10
updated: 2026-11-10
status: active
---

# Sponsor Infra Plumbing — Deep Teardown
Gen AI Summit Hackathon, Athens, 14–15 Nov 2026 · Recon date: Nov 2026
Three infra sponsors that form one agent plumbing stack: **Firecrawl** (web ingestion), **treg** (tool access + payments), **boxd** (compute/runtime). All three are agent-native: each ships an `llms.txt`/`SKILL.md` designed to be fed straight to a coding agent.

---

## 1. Firecrawl — the context API for agents
firecrawl.dev · YC S22 · ~$75M raised (Series B, mid-2025) · OSS core (github.com/firecrawl/firecrawl, self-hostable) + managed cloud.

### API surface (v2, `api.firecrawl.dev`)
| Endpoint | What | Credits |
|---|---|---|
| `POST /v2/search` | Web search returning **full page content**, not snippets. Filters: date, domain, PDF, country, `safe` | 2 per 10 results |
| `POST /v2/scrape` | URL → clean markdown/HTML/JSON. `formats:["json"]` = LLM extraction w/ schema (+4 cr). `actions` for pre-scrape clicks. `maxAge` cache = ~500% faster | 1/page (+4 JSON, +4 prompt-injection check) |
| `POST /v2/crawl` | Depth-first site traversal, async job + webhooks | 1/page |
| `POST /v2/map` | All URLs on a domain, fast | 1/call |
| `POST /v2/batch/scrape` | Batch URLs (shares crawl rate limit) | per page |
| `POST /v2/agent` | **Preview.** Prompt-only deep-research-for-data: autonomously searches/navigates, returns schema-conformant JSON. `urls` optional, `maxCredits`, `location`, `threadId` follow-ups, webhook. Replaces legacy `/extract` | 5 free runs/day, then dynamic |
| `POST /v2/interact` | **Standalone browser sandbox** → `{id, cdpUrl, liveViewUrl, interactiveLiveViewUrl}`; `POST /v2/interact/{id}/execute` runs Playwright (node/python) or `agent-browser` bash (60+ cmds, `@ref` accessibility snapshots); `DELETE` closes. `ttl`/`activityTtl` | 2 per browser-minute |
| `POST /v2/scrape/{scrapeId}/interact` | Prompt- or code-drive the browser on an already-scraped page (scrape→interact→`DELETE` loop). Profiles persist auth state across calls | 2/browser-min |
| `POST /v2/parse` | PDF/DOCX/20 file types → markdown/JSON, OCR | 1/page |
| Monitor | Recurring checks on URLs/crawls/searches, same/new/changed/removed labels → webhook/email/Slack | 1/page/check |
| Research Index | Academic papers (`search_papers`, `read_paper`…) | **free** |
| Alexandria | Marketplace of data providers through one API (`alexandria.firecrawl.dev`) | varies |
| Developer Index | Search over 70M+ docs/READMEs/GitHub issues/PRs for coding agents (DevDex 63.1% R@10) | — |

### Agent-ingestion patterns they document
- **Find → Extract → Clean → Use** loop: Search (full content) → Scrape markdown → JSON-mode schema extraction → feed LLM.
- `scrapeId`-bound Interact for auth/pagination/multi-step flows; persistent **profiles** save browser state across calls.
- `/agent` when URLs are unknown; JSON-mode scrape when URL known (cheaper, synchronous).
- Keyless free tier: `Firecrawl()` with **no API key** works for search/scrape/interact at low limits — frictionless hackathon start.
- Agent onboarding is first-class: `firecrawl.dev/SKILL.md` (agent-onboarding), `auth.md` = agentic registration via WorkOS ID-JAG (`POST /agent/auth` → returns `fc-` key, no human signup, 60 regs/hr/IP); MCP server; `npx -y firecrawl-cli@latest init --all --browser` installs CLI + skills; Stripe Projects provisioning (`stripe projects add firecrawl/api` writes `FIRECRAWL_API_KEY` to `.env`).

### Pricing & credits
Free: **1,000 cr/mo**, no card, 2 concurrent browsers. Rate limits (free): 10/min scrape+map+search, 2/min crawl+agent, 2/min interact. Hobby $19 (5K cr, 5 conc, 100/min, 20/min). Standard $99 (100K, 25 conc, 500/min, 100/min interact). Growth $399, Scale $749. PAYG top-ups $5 increments on paid plans. Failed scrapes (empty result) not charged; HTTP-error pages cost 1 cr.
SDKs: Python `firecrawl-py`, Node `firecrawl`, Go, Rust (official); Java/Ruby/.NET/PHP/Elixir (community). CLI `firecrawl-cli`.

### Free-credit acquisition
- **STUDENTEDU** → 10,000 credits. Verified on firecrawl.dev/student-program: sign up with academic email → Settings → Billing → redeem coupon. No card. (Needs a .edu/academic inbox; eligibility = enrolled students, edu/personal use.)
- Keyless free tier (no key at all) or standard free 1K/mo.
- Hackathon sponsors typically hand out coupon codes at the booth — credit coupons redeem in Billing, not Stripe checkout.

### 36h integration recipe
```python
from firecrawl import Firecrawl
app = Firecrawl(api_key="fc-...")            # or no key for keyless tier
r = app.scrape(url, formats=["markdown"])    # 1 cr — clean LLM-ready text
# browser moment:
s = app.browser(ttl=180)                     # → s.live_view_url (embed in demo UI!)
out = app.browser_execute(s.id, code='await page.goto("...") ...', language="node")
app.delete_browser(s.id)
```
Best pattern: `search → scrape top hits → interact for anything dynamic`. Show `liveViewUrl`/`interactiveLiveViewUrl` in an iframe — judges watch the agent's browser live.

---

## 2. treg — "OpenRouter for agent tools"
treg.to · github.com/superdesigndev/treg (7.7k★) · **Apache 2.0 + additional terms** (NOT AGPL — sole restriction: don't re-host it as a competing managed registry; calling hosted API or self-hosting internally is free). Founder Jason Zhou (jason@superdesign.dev), built by the SuperDesign team.

### What it actually is
A credential-injecting **reverse proxy + catalog**: agent makes the *real upstream request* to `https://treg.to/call/<endpoint-id>` (or `/call/<team-tool>/<path>`, even `/call/https://api.stripe.com/v1/charges`); treg injects the provider credential server-side and relays the response verbatim. **4,100+ endpoints, 126 providers.** The proxy "relays, never models" — upstream API changes don't break it, agents never hold keys.

### The agent loop (CLI / MCP / HTTP — same semantics)
```bash
treg catalog search "find a work email"      # by job, not vendor; shows prices
treg catalog get hunter.people.email.find    # params, price, reliability, ready call line
treg call hunter.people.email.find --query domain=reddit.com --query full_name="A. Ohanian"
```
- HTTP: `GET https://treg.to/call/<id>?k=v` + `X-Treg-Token: trg_live_...` (team token) or + `X-Treg-Org: <slug>` (personal token). Never put the treg token in `Authorization` on `/call/` — it relays to the provider.
- MCP `https://treg.to/mcp/` (Bearer/OAuth): `catalog_search`, `catalog_get`, `call`, `call_media`, `balance`, `my_tools`, `resources_list`, `catalog_request`, `feedback`, `review`.
- Catalog search/browse is unauthenticated — agents can discover tools before signup.

### Money — how an agent pays
**Prepaid fiat balance, NOT x402/crypto.** No crypto rails anywhere in the API; billing = `POST /billing/topup` / `treg topup` (Stripe-backed) + autotopup. **$1.00 free credit** once per new verified account on first eligible team. 0% markup ("provider rate + $0.000"); treg earns on vendor volume pricing.
- `X-Treg-Cost-Micro` response header = settled micro-USD per call; `X-Treg-Call-Id` for ledger joins (`GET /calls/{id}/result` re-fetches a paid answer).
- `X-Treg-Route-Max-Cost: <usd>` caps a single call → else `402 route_max_cost`, nothing charged.
- Out of balance → `402 insufficient_balance` JSON with `balance_micro`, `estimated_cost_micro`, `topup_url` — machine-readable, agent can react.
- Credential ladder per call: team's own key (unmetered) → team-stored secret → verified public route (free) → treg's key (billed). BYOK always wins.
- Per-customer resale: `X-Treg-Meta: customer=cust_123` tags + `PUT /orgs/{id}/budgets/<dim>/<val>` daily caps + `GET /orgs/{id}/usage/by-tag` ledger invoicing. Pinned agent tokens (`treg org agent-new bot --pin customer=...`).

### Catalog categories (landing + skill.md)
Keyword/rank tracking, backlinks/authority, AI-visibility (LLM citations), trending & discovery (TikTok, X, IG, YouTube, Reddit, LinkedIn), publish-on-socials (OAuth), people/company enrichment (email find/verify, PDL, Crunchbase-style funding), buying signals (hiring, headcount), ads campaign mgmt (OAuth: Google/Meta/TikTok/Microsoft), competitor ad libraries, measurement (GA4/Search Console OAuth), Slack messages, Apify-style actor runs, Google Trends — plus **generative media**: Seedance, Veo, Wan, Gemini/GPT Image, Seedream, Fish Audio TTS/voice cloning.
**Routed endpoints** `treg.<capability>` (`treg.web.extract`, `treg.web.search`, `treg.google.serp.organic`, `treg.people.email.find`…): treg picks provider, waterfalls on miss/429/5xx, bills only returned answer; headers control behavior (`X-Treg-Route-Verify`, `-Complete`, `-Waterfall:0`, `-Strict-Filters`).
Provider choice is evidence-based: `catalog_get` shows measured `works` (success rate over real calls), `hit`, `p50` latency, `last_ok_days`, `verified` stamps.

### Agent-facing extras
- `install.sh` puts CLI + `skill.md` operating guide into every detected agent; `--token <team-token>` = headless; Claude Code plugin: `/plugin marketplace add superdesigndev/treg`. Hosted assistants: add `https://treg.to/mcp/` connector.
- **`POST /demo/sandbox`** (+ `/demo/sandbox/live`, `/demo/sandbox/skill`): mints a throwaway demo sandbox — perfect for live demos without signup friction.
- Hub: publish your own paid tools (`/hub/tools`, earnings endpoints) — agents can sell tools too.
- `X` (Twitter) via treg's app is billed per call even on own connections; verified-contact caveat: always `X-Treg-Route-Verify: true` before "sending" to found emails.

### 36h recipe / demo moment
Give the agent a token + a goal requiring data it can't reach (e.g. "find this competitor's backlinks + the CEO's verified email"). On-screen loop: `catalog_search` → price shown → `call` → `X-Treg-Cost-Micro` debit → `balance` drops. **The agent autonomously buying a capability mid-task with real money is the most novel demo beat of the three** — show the ledger, not prose. Cap with `X-Treg-Route-Max-Cost: 0.05` so a runaway loop can't burn the $1.

---

## 3. boxd — composable computers for agents
boxd.sh · Azin Tech Operating Company B.V., Amsterdam · **€2M pre-seed, Sep 2026**, BlueYard Capital lead + Antler, OVNI, s20, Script Capital, General Intuition angels. Founders: Michiel Voortman, Laurentiu Ciobanu, Hidde Kehrer. Self-hosted VMM (custom kernel work: `import_cow_range(2)` for cross-process CoW); bare metal in Frankfurt + New York region. Hackathon-native team (won Best Technical Build, Anthropic × Whale Hackathon).

### The bet
"**The agent lives inside the machine**, not outside it" — a real hardware-isolated Linux VM (own kernel, KVM boundary), not a tool-API sandbox. The VM *is* the durable context: disk, processes, shell state persist; suspend/resume ~10ms; hibernate to disk ≈ free.

### Primitives
| Op | How | Speed |
|---|---|---|
| Create | `boxd new name` / `machines.create` | **<10ms** boot |
| Fork | `boxd machine fork src dst` — live copy: memory, disk, running processes | **<200ms** |
| Snapshot | `snapshots save` → named state, machines created from it | survives machine deletion |
| Checkpoint | in-place rollback (`machine checkpoint save/restore`) | undo button |
| Pause/resume/hibernate | standby keeps RAM warm; hibernate = disk-only billing | resume sub-ms |
| Delete-after / self-delete | cron/time/auto; `machine remove --self` | agent can kill its own box |

Machine: 2 vCPU/8 GiB/100 GB default (1/4, 4/16, 8/32 sizes, `resize`). SSH alias `ssh name.boxd`; auto HTTPS `name.boxd.sh` (serves ports 80/443/8080/8000/3000/5000/5173, fallback 8000); subdomain proxies per port; custom/wildcard domains; TCP/UDP port forwarding. Networks scope VM-to-VM; egress allowlists; `--isolated` strips in-machine CLI/logins. Env vars/secrets org-scoped, injected. Docker/Compose/Buildx preinstalled, daemon running. **Desktop** = live clickable view of the machine display in a browser (watch the agent work, take over). `*.run.ts` automations: triggers/schedules/jobs with hibernation between runs. Integrations (GitHub, Linear, Slack, 100+) connect once → present in every machine.

### API / SDKs
- CLI: `curl -fsSL https://boxd.sh/downloads/install.sh | sh` (`--yes` for agent installs) → `boxd auth login`.
- TypeScript `@boxd-sh/sdk`, Python `boxd` — `BOXD_API_KEY` from `boxd auth keys create`. `machines.create/exec/fork/waitUntilReady`, `machines.fs` (file API), `snapshots`, `checkpoints`, `deleteSelf()`. REST API behind `auth keys` for CI/fleets.
- **In-machine boxd CLI is pre-authenticated** — a box can create, exec, and expose sibling machines itself (intended; use `--isolated` if you don't want that).

### Agent story
Claude Code, Codex, OpenCode **preinstalled on every machine**, each with a platform-aware instructions file (`~/.claude/CLAUDE.md` etc. — agent already knows fork/snapshot/proxy primitives). Org-level Claude/Codex login served to all private machines (encrypted; stripped on share); `ANTHROPIC_API_KEY` via env var alternative. Delegate non-interactively: `boxd machine exec m -- claude -p '...' --dangerously-skip-permissions`. tmux + `/remote-control` = always-on agent reachable from claude.ai/mobile. ⚠ Auto-hibernate watches *network traffic*, not CPU — for unattended runs: `boxd machine config set m auto-hibernate.timeout 0` (else agent hibernates mid-job).
Use cases documented: agent swarm intelligence (fan-out + merge), sandboxes, agentic SaaS (machine-per-user), reproducible RL envs, Claude Managed Agents, OpenAI Agents API. Frameworks already on it: Flue, Bindu, Harbor. Proof: Moyai ran **279,577 benchmark machines**, 5ms median boot.

### Pricing / free tier
Metered per second, settled every 15 min, **only active resources billed**: vCPU €0.039/vCPU-h (active only — ~10% avg), RAM €0.012/GiB-h (resident), disk €0.00008/GiB-h (written). Typical 2vCPU/8GiB ≈ **€0.03/h running**, €0.03/h standby, **€0.0016/h hibernated**. **€30 free credits** on signup — at €0.03/h that's ~1,000 machine-hours; trivially covers a 36h hack. Self-host free ≤16 vCPU (KVM/AWS/GCP, no license key).

### 36h recipe / demo moment
```python
from boxd import Boxd
boxd = Boxd()                                   # BOXD_API_KEY
m = boxd.machines.create("agent-0")             # ~6ms
boxd.machines.exec(m.id, "claude -p '...' --dangerously-skip-permissions")
forks = [boxd.machines.fork("agent-0", f"agent-{i}") for i in range(1, 6)]  # 5 clones, <200ms each
```
**Demo beat: fork a running agent into N live copies mid-task** — same memory, disk, processes; each explores a branch; Desktop view shows them browsing in parallel. Or machine-per-agent swarm with a lead merging. Second beat: hibernate mid-task → resume with full state (agent literally picks up mid-thought).

---

## Head-to-head: strongest "agent at work" demo
| | Demo moment | Setup cost | Risk |
|---|---|---|---|
| **Firecrawl** | Embeddable `liveViewUrl` — judges watch the agent's real browser click/login/extract in real time | Lowest (keyless tier → STUDENTEDU 10K) | Free tier = 2 concurrent browsers, 2/min interact — fine for a stage demo |
| **treg** | Agent discovers a needed tool, reads the price, pays from its own balance, uses result — visible ledger debit | Low (one token, `demo/sandbox` for zero-signup) | $1 credit = hundreds of calls, but cap `X-Treg-Route-Max-Cost`; crypto-payments storyline absent — it's fiat prepaid, still reads as "agent with a wallet" |
| **boxd** | Fork → 5 agent clones branching in parallel on live machines; hibernate/resume mid-task | Medium (CLI + API key + machines) | Auto-hibernate kills idle-looking runs — disable it; most moving parts |

**Verdict:** treg's tool-purchase is the most differentiated narrative (no one else demos agents spending money). Firecrawl's live browser view is the most *visual* per unit effort — combine them. The full-stack story: **an agent living inside a boxd machine forks itself into a swarm; each clone buys tools via treg and browses via Firecrawl** — all three sponsors in one coherent "agent at work" loop.

### Stack recipe (all three, ~1h setup)
1. `curl -fsSL https://boxd.sh/downloads/install.sh | sh -s -- --yes && boxd auth login` → `boxd new hq` → `boxd machine config set hq auto-hibernate.timeout 0`.
2. Inside hq: `curl -fsSL https://treg.to/install.sh | sh -s -- --token $TREG_TOKEN` (or `treg login`); `pip install firecrawl-py` or use keyless tier / STUDENTEDU key.
3. Lead agent on hq; `boxd.machines.fork` per subtask; sub-agents call `treg catalog search`→`call` for data tools, Firecrawl `browser()`+`interact` for web work; embed `liveViewUrl`s + treg balance/cost ledger + boxd machine list in the demo UI.
