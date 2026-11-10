---
title: "past winners code"
type: source
tags: [hackathon, genai-summit, recon, intel]
aliases: ["past winners code"]
created: 2026-11-10
updated: 2026-11-10
status: active
---

# Past Winners' Build Artifacts — The Actual Craft Bar

**Target event:** GenAI Summit Hackathon, Athens LifeTech Park (Spata), 14–15 Nov 2026, 36h, ~100 builders, teams 2–5 (solo OK). Brief: *"build autonomous AI agents and learn new agentic tools."* €5k/€2.5k/€1k prizes. Finalists pitch on the GenAI Summit 5 main stage at SNFCC on Nov 16. Panathēnea is a partner. **Abed Hamami (Claweyes/Origami winner) is on the organizing side** — he made the announcement videos.

**Recon date:** Nov 2026. Keel repo cloned and read at `~/scratch/hackathon-recon/deep2/keel` (28 commits, sanitised public copy).

---

## 1. KEEL — the benchmark (1st place, Florent×Panathēnea, May 28 2026)

- **Repo:** `github.com/ertval/keel-multi-agent-pipeline` (MIT, public since Jul 2026)
- **Author:** Ertval Karameta (Athens, ex-Metagalerie founder, Zone01 Athens) — sole git author; PRD says "2-person team." Now "Keel Technologies" co-founder.
- **One-liner the demo was built around:** *"The shipowner claims $187,000. Keel reconciles it to $112,000 — and shows you the clause and the timestamp for every dollar of the difference."*
- **Size:** ~5,900 lines app Python + **5,285 lines of tests** (≈1:1 ratio — unheard of for a 12h build), Next.js 16/React 19/Tailwind4/shadcn frontend, 38 Playwright e2e green.

### Architecture: LLM reads, Python decides

`orchestrator → {cp_worker, sof_worker} → validator → (retry_fanout ⇄ workers, ≤3) | laytime_engine → adjudicator → END`

- **LangGraph StateGraph, 7 nodes** (`pipeline_agents.py:642-689`). The join is a real list-form edge `add_edge(["cp_worker","sof_worker"], "validator")` — and `test_agent_graph.py:302-336` builds a two-independent-edges **mutant** to prove `builder.waiting_edges` separates them. They test the *topology*, not just behavior.
- **Validator → bounded retry with routed feedback.** Each `ValidationIssue` is tagged `{message, document, field}`; `_errors_for` forwards only the findings addressed to that worker's document into its re-extraction prompt. Max 3 retries, then forced `calculate` — the graph degrades, it never hangs.
- **Workers** call the LLM only to fill strict JSON schemas; **claim amounts are never re-extracted on retry** (`sof_worker_node` comment: "no validation error concerns a claim amount, and re-reading one would move the dollars").

### "The dollars never come from the model" — how determinism is implemented

1. **Extraction (`extraction/extractor.py`, 496 lines):** raw OpenAI SDK `chat.completions` with strict `json_schema`, `temperature=0`, 3 attempts × 2s apart, 30s timeout. NOT LangChain. Model `gpt-4o` default; `OPENAI_BASE_URL` allows NVIDIA NIM. Prompt feeds lines as `p<page>L<line> [x0,y0,x1,y1] text` — the LLM cites **anchors**, never coordinates; unresolvable anchor → `NO_BBOX` sentinel, never a guess.
2. **Laytime engine (`engine/state_machine.py`, 393 lines):** pure-Python state machine `BEFORE_NOR → ON_LAYTIME → ON_DEMURRAGE` + `WEATHER_PAUSE`. Hour-by-hour SHEX Sunday exclusion, turn-time, once-on-demurrage-stays-on-demurrage. Every state transition appends an `AuditEntry` with `rule_applied`, `clause_citation`, `sof_citation`, running totals. **Zero LLM.** Module docstring (110 lines) honestly records what it does NOT model: FHEX, definition-15 pro-rata, definition-17 artificial day.
3. **Weather evaluator (`rules/evaluators.py`, 244 lines):** deterministic majority-of-hours test over hourly port observations. Threshold = charterparty's own extracted figure, else Keel default **labeled as unverified**. Three separate provenance fields on every verdict: `rule_id` (`CP_WEATHER.MAJORITY_OF_HOURS` — names no document), `measurement_basis` (`Laytime Definitions 2013, def. 16`), `rule_authority` (`custom`). A tie is reported as a tie ("half of the observed hours"), not a shortfall.
4. **Reconciliation:** `reconciled = charterer_base + Σ items favoring owner` — canonical invariant owner $187k / charterer $62k → **$112,000**, asserted by 15 tests.

### The differentiator nobody else had: epistemic honesty as a feature

- The generated **settlement letter itself states the product's own limits**: *"a majority of the observed hours met the threshold … is not a finding that every claimed hour was an interrupted period"* and *"that document supplies the measurement basis only: it states no Force 6 and no majority test."* Judges (incl. a maritime lawyer) get a tool an analyst can defend in arbitration, not a magic box.
- **README leads with "What this is not"** — no auth, no PDFs ship, no email/PDF export, no SOC2 claims, no fake customers. Every non-feature is named with file:line.
- **Fixture-first demo:** `fixtures/voyage_001` (Piraeus) ships 5 cached `extracted_*.json` files → Demo Mode button runs the full graph with **zero LLM calls**, deterministic $112k in ~1.2s cold / 7ms warm. An API key is only needed for live extraction of new uploads.
- **Parsing hardened:** PDF parsing runs in a fork+exec sandbox with `RLIMIT_AS` set *before* pdf libs import; 200-page / 1.2M-char caps, 120s timeout, results pickled on stdout (`parsing/sandbox.py`, `limits.py`).

### Docs-as-weapon (post-win polish, ~July–Sept 2026)

- `docs/demo_workflow.md` — 276-line recording script: pre-flight checklist, per-scene beats, contingency table ("empty page → you're on 127.0.0.1, not localhost"), and a **corrections log** for lines that were wrong vs. the running app.
- `docs/hosting-demo-report.md` — killshot analysis written *for the demo*: dead `reconcile/adjudicator.py` hardcoding canonical dates = *"a judge reading it kills the 'deterministic rules engine' claim instantly. Fix before demo."* ngrok-vs-Cloudflare-tunnel comparison (interstitials, SSE), `NEXT_PUBLIC_API_URL` fallback trap, `USE_MOCK` build-time inlining trap → recommends `?demo=1` runtime override.
- `docs/market-moat-report.md` — 10 parallel research agents mapped 5 real competitors (Marcura, Burmester & Vogel, Veson, Voyager, Demurrage.IA — the last ships *their exact spec*: "deterministic 80-rule engine, zero LLM in calc path, citation chain"). Every claim carries a source URL; unverified marked `[unverified]`.
- `docs/archive/critique/` — **7 multi-model critiques of their own repo** (gpt, gem, kimi, qwen, glm, deep, meta + merged). They fed their code to every frontier model and kept the brutal reviews in the repo.
- `test-cases/` — 4 hand-authored reconciliation scenarios w/ independent expected values (`case_01` $90k clean → `case_04` split), one proven via live NVIDIA NIM run.
- `.agents/skills/`, `.claude/skills/`, `.gemini/skills/` — they drove the frontend with design skills (ui-ux-pro-max, frontend-design); **11 landing-page designs** behind a `?v=` server-side router.
- Companion repo `ertval/two-tier-safe-ai-gate` (Go/Inngest/MCP): same thesis — Tier-1 LLM exploration → deterministic validation boundary → Tier-2 durable execution. This is the author's *philosophy brand*: **bounded autonomy**.

---

## 2. PORTSIDE — 2nd place, same event (what lost to Keel)

- **Team:** Dimitris Kalligaridis (returning SDE @ Amazon, ex-TabbPay founder — carried the build), Roman Dolgopolyi, Panagiotis Koulakoglou. Deree/ACG students; mentor Christian Dorffer. Evolved from a Zone01 hackathon concept in <10h.
- **Product:** voyage docs → **fully cited delay claim in <60s**. Now live at `portside-intelligence.com` as "Maritime Operational Decision Intelligence" (voyage inbox: demurrage, shortage, split-B/L, pilotage, underperformance claims; agent messages + timeline UI).
- **No public repo found.** Public artifacts: LinkedIn posts, live marketing site (JS-only, minimal crawlable content).
- **Why it lost (inference):** same problem space as Keel but positioned as *speed* ("<60 seconds"), Keel positioned as *proof* ("every dollar cited, determinism stated out loud"). At judge-Q&A depth, "fast LLM summary" < "auditable reconciliation with named limitations." Portside still became a real product — the bar wasn't idea quality, it was *verifiable depth under questioning*.

---

## 3. LifeHack Athens winners (May 27–28 2026, Athens LifeTech Park — same venue as target event)

36h, 60 participants, 13 teams. **No public repos found for any of the three** — artifacts are LinkedIn writeups only.

| Winner | Track/prize | Team | What they built (per posts) |
|---|---|---|---|
| **MetNav** | Pfizer CDI metabolic, €3k + Microsoft for Startups Tech Prize (best across all tracks) | Aggelos Ladas + Minas Papageorgiou (tech) + Ilias Alamoudi, Ioannis Gkinis, Giannis Sotiriadis (bioscience, met at venue) | Precision-medicine platform: **calibrated ML models + LLM agent w/ RAG over clinical guidelines + "programmatic audit harness for zero hallucinations"** — every output traceable to patient data, quantified uncertainty. Labs+CGM+genome+microbiome → personalized interventions. |
| **RNAgents** | ALTP drug discovery, 6mo free lab (first hackathon→lab transition) | Marjon Gjika (Hydra Tx CEO), Evie Maifoshie PhD, Anastasios Kollias, Shaurya Nathan Mathur | Agent that **generates, scores, refines thousands of siRNA/ASO candidates** across the transcriptome — generate→evaluate→optimize loop at scale. |
| **Dyania Challengers** | Dyania Health clinical AI docathon, iPads + paid internships | incl. Maria-Myrto Bakatsia (MD, now Dyania Clinical Innovations) | **Secure OCR → local-LLM pipeline** detecting preclinical MASH from unstructured medical records. Local inference = privacy story for clinical data. |

**Pattern repeats:** the winning formula is *deterministic/scored core + LLM at the edges + auditability*. MetNav literally used Keel's playbook vocabulary ("zero hallucinations," "fully traceable," "quantified uncertainty").

---

## 4. Abed's own wins (he now co-organizes the target event)

**Abed Hamami** — SF, product engineer, founder Polymath Labs (Jan 2026–), ex-Social Hackers Academy Athens head of education. Recurring teammate: **Ion Petropoulos** (Austin, GamerPlug founding eng, ex-Zone01 Athens head of tech, x8 winner).

### Claweyes — 1st, "Hack on OpenClaw w/ Codex" (Wordware Beach House SF, Feb 19–20 2026)
- ~5h build, 30 projects, judges incl. Wordware CEO Filip Kozera. "The vision port for OpenClaw."
- Repo not public; Ion's demo talk "IonPetro-ClawEyes" is on the hackersquad event page.
- **The pattern it rode:** OpenClaw (self-hosted agent runtime, exploded early 2026) had eyes in software but not in the physical world. The canonical public implementation of the same architecture is **`sseanliu/VisionClaw` (366★)**: iOS app → ~1fps JPEG frames + 16kHz PCM → **Gemini Live** WebSocket (native audio, no STT step) → tool calls → **OpenClaw Gateway** → 56+ skills (messaging, web, smart home). Glasses/phone = sensors+speaker; Gemini = eyes+mouth; OpenClaw/Claude = hands+brain. ClawEyes demoed this loop **live, in the room, on real hardware** — a talking, seeing agent that *acts*.

### Origami — 2nd, Cursor SDK hack @ a16z offices SF (June 11 2026)
- Team: Ion + Abed + Stephan Nicklow (repeated trio). Built *with* Cursor hacking the Cursor SDK.
- "A blank app that you code on it whatever you want" — self-rebuilding iOS app: app contains an agent harness that rewrites its own code via the Cursor agent. No public repo/video found.
- Lost 1st to a 13-year-old's Alzheimer's app for his grandmother (emotional-impact outlier; "over-18 bracket, we certainly won" — Nicklow).

**Abed's demo choreography (extracted):** physical/live artifact in judges' hands (glasses/phone camera, real agent actions), built *on the sponsor's own runtime/SDK* (OpenClaw at Wordware; Cursor SDK at a16z) = sponsor flattery + proof of tool mastery, playful-but-real branding (🦞, "vision port"), team of 2–3 that ships every time.

---

## 5. REELIO — 1st, OpenAI Build Week Athens (Jul 20 2026, SuiHub, 6 teams/18 builders)

- **Team:** Artemis Leonardou (founding eng NOFire AI, SREday speaker), Anastasia Michail, Odisseas M. Karipis, Panagiotis Mavrikos, Eleni Zafeiri. $8.5k OpenAI credits.
- **What it is:** UI on top of Artemis's already-public Claude Code skill **`artemisln/edit-greek-reel` (40★)** → now `edit-reel` plugin v2 (6 skills): Whisper transcribe+proofread → trim silence/retakes → karaoke word-by-word subs (any language) → subtle zooms (1.08–1.10x) → SFX + logo overlays → 9:16 ffmpeg crop. One skill is literally `/demo-reel-capture` — Playwright records your product demo and cuts it into a reel.
- **Pattern:** winner = *pre-existing proven artifact* (40★ OSS tool, real users) + new UX layer in one evening. "Not a new idea — the old one I never made time for." Live demos; broken things fixed at the podium (organizer's words). Judging: community vote on problem/originality/Codex-use/execution/impact.

## 6. Ion Petropoulos — the 8-win record (public artifacts)

| Event | Result | Artifact |
|---|---|---|
| AUEB/ACE first Greek AI Hackathon (~late 2024) | 3rd | eunomia.ai legal research (posts only) |
| Supabase @ YC SF (Nov 2024) | Finalist | "Digital Twins / Human Consciousness" w/ Abed, Nicklow, Calvin Gee, Kylie |
| OpenClaw×Wordware (Feb 2026) | **1st** | Claweyes (above) |
| AITX×OpenAI Codex (May 2026) | **2 prize tracks** | **TxMoney** — NL agent over TX campaign-finance filings, "every dollar amount linked to its source filing" (demo video on LinkedIn) |
| Cursor SDK @ a16z (Jun 2026) | 2nd | Origami (above) |
| CloudflareMCP / Supabase-cybersecurity hackathons | claimed in bio | no public artifacts found |
| GenAI Summit Hackathon (Nov 2026) | participant | post-event handoff to Abed |

Recurring craft signature: **source-linked money** (TxMoney = Keel's citation pattern in civic data), sponsor's own SDK, small fixed trio (Ion+Abed+Nicklow), live physical demos.

---

## 7. CROSS-PATTERN — what every winner shares

**The invariant across ALL winners: "dollars never come from the model."**

1. **Deterministic core, probabilistic edges.** Keel: Python engine + evaluator (LLM only fills schemas). MetNav: calibrated ML + audit harness (LLM only narrates via RAG). RNAgents: scored candidate generation. Dyania: deterministic OCR/local pipeline. Reelio: ffmpeg+Whisper pipeline (LLM orchestrates, doesn't fabricate). TxMoney: figures linked to source filings. *Judges can now smell "LLM demo" — a green output that can't be verified loses to a smaller claim that's provably true.*
2. **Structured-output extraction with citations.** Keel's `p<page>L<line>` anchors→real bbox geometry; unresolvable→NO_BBOX not a guess. MetNav: "every output traceable." Portside's only stated edge was also "fully cited."
3. **Bounded autonomy, stated out loud.** Validator node + retry cap (Keel); "policy boundary" (two-tier-gate); "audit harness zero hallucinations" (MetNav). Winners *name their limits in the product itself* — Keel's letter discloses its own test isn't BIMCO's; the demo clicks the "Delivery is not available" button on purpose.
4. **A canonical fixture = a deterministic demo.** Keel's voyage_001 cached extractions → same $112k every run, no API key. MetNav quantified uncertainty on a fixed patient profile. *Never make a live LLM call the centerpiece* (Keel's own hosting-report rule).
5. **Agent topology is real, not a prompt chain.** Keel: actual LangGraph join + conditional retry edges (tested against mutants). RNAgents: generate→score→refine loop. The "multi-agent" claim survives a judge opening the code.
6. **Tests at hackathon scale.** Keel: 5,285 test lines, structural graph assertions, 4 golden reconciliation cases. This is the single biggest craft gap vs. typical hackathon repos (0 tests).
7. **Docs engineered for the evaluator:** honest-status table, "what this is not," demo script with contingency table, killshot analysis. Judges reward knowing exactly what doesn't work.
8. **Sponsor-native stack.** Claweyes on OpenClaw at Wordware; Origami on Cursor SDK at a16z; Reelio on Codex at OpenAI week; MetNav on Azure/Microsoft. Winning the room = shipping on the sponsor's runtime.
9. **Local resonance wedge.** Maritime demurrage in Athens (Greek fleet, Piraeus) — Keel and Portside both picked it; LifeHack winners picked sponsor challenge tracks literally handed to them.
10. **Small senior teams:** 2–5, everyone ships; several were Zone01 Athens alumni (Keel, Portside, Ion).

**What runners-up lacked:** speed/novelty positioning without a verifiable core (Portside's "<60s" vs Keel's "provable $112k"), LLM-call-dependent demos, claims wider than the code (Keel's docs exist *because* reviewers kept catching claims the code didn't support).

## 8. The bar to beat — concrete checklist

Match Keel, then exceed on agent autonomy (the event's actual brief):

- [ ] One canonical scenario with a **headline number** testable end-to-end ("$187k→$112k" style) + golden tests asserting it.
- [ ] LLM→strict-schema extraction; **all money/risk arithmetic in pure code**; say it on stage.
- [ ] Every output field carries provenance (source anchor, rule id, authority) — and *unverified* is a first-class value, never silently filled.
- [ ] Real agent graph: fan-out workers, a genuine join, validator with **routed** bounded retry. Bonus: deterministic **policy gate** before any side-effecting action (two-tier pattern) — nobody at the event will have durable/policy-gated execution.
- [ ] Fixture/cached path so the demo runs with **zero live LLM calls** in <2s; demo script with contingency table.
- [ ] Honest-limits surface in-product (the letter that says what it isn't) + README "what this is not."
- [ ] Sponsor-track framing + Athens-resonant problem; physical/live moment if hardware fits (Claweyes lesson).
- [ ] ~1:1 test code; at minimum: canonical-path test, graph-topology test, adversarial cases.

**Key gap in ALL precedents to exploit:** none had genuinely *autonomous* agents doing real-world actions with a deterministic safety boundary — Keel is a one-shot pipeline, Claweyes was a gateway demo, Origami self-rewrites but wasn't shown as verified. The brief ("autonomous agents + agentic tools") + a policy-gated, auditable agent loop = uncontended territory.
