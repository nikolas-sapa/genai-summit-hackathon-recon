---
title: "maritime"
type: source
tags: [hackathon, genai-summit, recon, intel]
aliases: ["maritime"]
created: 2026-11-10
updated: 2026-11-10
status: active
---

# MARITIME VERTICAL — Viability Recon (deep2)
**For:** Gen AI Summit Hackathon, Athens LifeTech Park, 14–15 Nov 2026 · Finals SNFCC 16 Nov
**Verdict:** GREEN, with a differentiation duty. Shipping is the proven Athens meta, the data is genuinely free/live, the paperwork is real and public, and the room contains multiple people whose money is already in Greek maritime tech. The trap: Keel won this org's May-2026 event with exactly this vertical — a re-skin loses; a step-change on live ops or a different doc-workflow wins.

---

## 1. The precedent: Keel (1st place, Panathēnea AI Hackathon May 2026)

Repo cloned + fully readable at `~/scratch/hackathon-recon/deep2/keel/` (github.com/ertval/keel-multi-agent-pipeline, MIT). Author: Ertval Karameta, now "Co-founder & AI systems engineer at Keel Technologies" — the hackathon project became a company. That is itself the judge story.

**Winning architecture (steal the pattern, not the product):**
- **LLM extracts → schema. Deterministic code does the money.** LLM reads CP + SOFs + claims into frozen Pydantic models (`extraction/extractor.py`, OpenAI structured output, `p<page>L<line>` citations resolved to real bboxes). Every dollar is arithmetic in `engine/state_machine.py` — states `BEFORE_NOR / ON_LAYTIME / WEATHER_PAUSE / ON_DEMURRAGE` — plus `rules/evaluators.py`. Tagline: "The dollars never come from the model."
- LangGraph, 7 nodes: `orchestrator → {cp_worker, sof_worker} → validator → (retry_fanout | laytime_engine) → adjudicator`. Real join edge, bounded retry ×3.
- Canonical demo: owner claims **$187,000**, charterer **$62,000**, reconciled **$112,000**. Dispute = 3 weather days (June 14–16), demurrage $50k/day, Bft-6/2mm-h threshold from the CP's own clause. Fixture: `fixtures/voyage_001/` — vessel "MV Hellenic Pioneer", load port **Piraeus**, extracted JSONs committed.
- Legal discipline worth copying: BIMCO *Laytime Definitions for Charter Parties 2013* cited only as measurement basis (definition 16); threshold + invocation test are the CP's own terms; rule_authority = `custom`. Letter is "advisory negotiation support," not legal advice. This precision is a moat against maritime-literate judges/mentors.
- 355 tests, 15-test canonical path; 4 hand-computed scenario cases (`test-cases/case_0{1-4}`: clean voyage 90k, owner-win 104k, charterer-win 90k, split 125k).

**What Keel did NOT build (the open lanes — explicitly documented):**
- No human sign-off gate, no send/delivery path (letter is HTML-only; "Send" dialog literally says nothing is connected).
- No live weather provider (fixture only). No live AIS. **No upload path exercised in demo** — public repo ships no PDFs; demo runs on a seeded voyage.
- No inbox/email ingestion, no time-bar logic, no multi-port voyages, no reversible laytime, no OCR, no extract-review screen.
- Implication: "post-hoc two-party reconciliation of one fixture voyage" is *taken*. Everything adjacent — live-triggered, fleet-scale, upstream/downstream — is open.

---

## 2. Vessel tracking — what's usable live in 36h

| Source | Cost | Shape | Hackathon fit |
|---|---|---|---|
| **aisstream.io** | **Free** (GitHub OAuth key) | WebSocket `wss://stream.aisstream.io/v0/stream`, bbox + message-type + MMSI filters, 25 decoded msg types, 3 conns/account | **Primary.** Live Aegean bbox `[[41.2,22.0],[35.0,28.5]]` covers Piraeus/Aegean. No history, no replay — missed msgs are gone, browser connections refused (server-side only). Pre-wire a Python client + SQLite sink NOW; key request by email before Saturday. |
| MyShipTracking | 2,000 credits / 10-day trial free | REST: positions, **port calls, expected arrivals** | Good complement — REST is easier than WS for a demo; trial timing works if activated ~12 Nov. |
| VesselFinder | Trial on request; €330/10k credits | REST positions + port calls (2 credits/record) | Backup only. |
| MarineTraffic (Kpler) | No free API tier; Essential ~$100/mo | REST positions/events | Skip — sales-gated since Kpler acquisition. Web-scrape free UI is fragile + ToS-risky. |
| AISHub | Free, but **requires running a contributing AIS receiver** | XML/JSON/CSV, 1 req/min | Dead end for us — receiver-gated. |
| Global Fishing Watch | Free API key, non-commercial | AIS history 2012→~96h ago + port-visit events | Best *historical* source; "port visits" endpoint = precomputed anchor/berth events. |
| AIS Trail | 500 credits/mo free, no card | REST, 7-day lookback | Fine backup for "recent Piraeus calls". |
| **Zenodo: Piraeus AIS dataset (vesselAI)** | Free, CC | DOI 10.5281/zenodo.10006470 — labeled historical Piraeus AIS + TSV extractor (github gsantipantakis/dataExtraction) | **Offline insurance.** If wifi/WS dies on stage, replay this as a fake live feed — same story, zero network. |

**Demo-critical:** record a 2–3h aisstream capture of the Piraeus anchorage bbox BEFORE the event (Friday night), so a "live" fallback exists that is actually real data, timestamped, replayable at 100× speed.

---

## 3. Demurrage/laytime domain pack

**How the money works (the workflow the agent replaces):**
1. Charterparty fixes: laytime allowance (hours or mt/day rate), SHEX/SHINC/FHEX day-count rule, NOR turn time (grace hrs), demurrage rate $/day pro-rata, despatch ~50%, weather clause (WWD etc. + its own numeric threshold), time bar (60/90/180d from discharge completion).
2. Vessel arrives → tenders **NOR** → laytime clock starts after turn time → **SOF** logs every event (arrival, anchor, pilot, all fast, cargo start/stop, weather stoppages, completion, docs aboard, sailed).
3. Owner's analyst turns SOF + CP into a laytime statement → invoice. Charterer's analyst **re-derives it from their reading** of the same docs → disputes. Gap lives in: SOF timestamp disagreements (two SOFs differ), clause interpretation (was the weather exception invoked? was NOR valid vs laycan?), excluded periods.
4. "Once on demurrage, always on demurrage": after laytime expires, exceptions stop applying unless CP says otherwise. Missed time bar = claim dead entirely.
5. Formula is trivial: `excess time × daily rate`. The hard part is entirely *document forensics* — extraction, reconciliation, evidence. Hence agent-shaped.

**Documents:** charterparty (GENCON dry bulk / NYPE time charter / bespoke riders), SOF (BIMCO/FONASBA 1975 standard form + tanker variant), laytime/timesheet statement, NOR, claim letter + supporting pack (B/L, LOP letters of protest, weather records, pumping logs for tankers).

**Why deterministic math, not LLM math** (Keel's defensible line, now industry table stakes per Veson/Marcura): laytime is a rule system — commence-time rules, exception rules, rate arithmetic, day-fractions. An LLM that outputs $ is unverifiable; an LLM that outputs `{laytime_hours: 72, shex: true, nor_turn_hrs: 6, dem_rate: 50000, weather_threshold_bft: 6}` with page/line citations, feeding a state machine whose every transition cites an SOF row + a clause, is auditable. Judges Pittarokoili (verifiable claims) + Zindros (proof not trust) + Gianitsos (real numbers) all independently reward exactly this.

**Market size hooks:** FMC: 9 carriers collected **$13.9B demurrage/detention in 41 months ≈ $4B/yr** (container alone). Veson: **$71B in claims processed** over 20 yrs, 1.1M claims; launched AI "Claims CoCaptain" — category validation. Marcura/DA-Desk, Dataloy, Burmester & Vogel (40yr, 2M voyages), Danaos (embedded in Greek operators). Demurrage is commoditized *math*; the unsold part is **claims-intake chaos** (email, mixed PDFs, time bars, two-SOF gaps) — Keel's own PRD §2 says this verbatim.

---

## 4. Demo fixtures — obtainable today

| Fixture | Where | Use |
|---|---|---|
| GENCON 1994 sample PDF | `pfri.uniri.hr/bopri/documents/38_sample_copy_gencon_94.pdf` | Canonical voyage CP, boxes for laytime/demurrage |
| GENCON 2022 sample PDF | `maritimecyprus.com/wp-content/uploads/2023/07/Sample-copy-GENCON-2022.pdf` | Current edition |
| NYPE 2015 sample PDF | `smf.com.sg/wp-content/uploads/2021/12/22-document-nype-2015-sample-copy.pdf` | Time charter form |
| BIMCO Laytime Definitions 2013 | `bimco.org/media/qy2neqim/laytime-definitions-for-charter-parties-2013-v2.pdf` (public) | The ruleset text itself — feed to agent |
| Sample laytime statement PDF | `getlayline.com/Layline_Sample_Laytime_Statement.pdf` | MV NORDIC DAWN, Rotterdam, $18k/day, SHEX, event table w/ NOR/all-fast/weather — perfect SOF-adjacent exemplar |
| Worked 4-port voyage | `laytimetech.com/sample` | Two NORs dispute worth $13,039.93; CP vs sale-contract non-reversible split $106,333 — **edge-case gold**: shows real disputes are about interpretation, not arithmetic |
| Draft laytime calc (real) | `repository.pip-semarang.ac.id/290/4/20.%20Draft%20Laytime%20Calculation%20MV%20%20Fermita.pdf` | Real XLS-style calc, $6k/day, 12h turn time |
| Tanker SOF event template | mysteriousmaritimeworld.com tanker SOF page; Operium free Excel SOF template (BIMCO/FONASBA-style) | Author your own SOF fixture |
| Real arbitration award w/ SOF | `unusualarbitrationawards.com/M-T-Lady-Sina-Arbitration-Award.pdf` | Actual tribunal reading SOF+NOR+laytime — shows the stakes language |
| Keel's extracted JSONs | `~/scratch/hackathon-recon/deep2/keel/fixtures/voyage_001/` + `test-cases/` | Field list for CP extraction schema; hand-computed expected answers for eval harness |
| Port weather | Open-Meteo archive API (free, hourly wind/precip at 37.94,23.65) | The live weather provider Keel never built |

**Authoring note:** Keel's method — "real-format docs + crafted numbers" — is the right one: model PDFs on GENCON/SOF layout, hand-compute expected $, assert pipeline reproduces it. Gives you an eval harness (Gianitsos/Pittarokoili) for free.

---

## 5. Greek shipping specifics

**Stats for the pitch (UGS Annual Report 2025/26, ugs.gr):**
- Greek-owned fleet: **~5,800 vessels, 19.1–20% of world fleet by dwt — #1 shipowning nation globally; 61% of EU-controlled fleet**.
- World's largest cross-trader: **>98% capacity serves third-country trade; >175,000 port calls in 171 countries in 2025**.
- Predominantly bulk/tramp (itinerant — exactly the voyage-charter/demurrage world); largest tanker + LNG fleet; orderbook 56.2M dwt (5× in 5 yrs).
- Shipping ≈ 7–8% of Greek GDP; Piraeus = Athens' port, #1 European gateway post-Suez (PPA/COSCO container terminal 1.1M TEU, 11 cruise berths).

**Open data / official sources:**
- **PPA (ΔΑΛ):** ppa.gov.gr/chartis-plion-on-line — port activity search (arrivals/departures, filterable). No API; scrape or screenshot.
- **OLP (Piraeus Port Authority SA, olp.gr):** publishes cruise berthing schedules (XLSM), container terminal ship-service schedule, regulations + tariffs (the DA-cost inputs).
- **data.gov.gr:** NEPA pleasure-craft company registry (public, CC-BY-4.0). GSIS/ΚΕΔ ship-registry web service exists but is ministry-gated — skip.
- **Ψηφιακό Νηολόγιο (niologio.gov.gr):** vessel registration behind taxisnet — skip.
- **Hellenic Coast Guard / ΥΝΑΝΠ:** no usable open API found; AIS + OLP pages are the practical port-feed.

**Company tech departments (proof buyers exist):**
- **Angelicoussis** (world's largest private tanker fleet, Athens): published IEEE paper on their digital-transformation roadmap; "Internet of Vessels" platform history.
- **Thenamaris:** just completed **93-vessel ABS Nautical Systems ERP rollout** (Mar 2026) + SAP + in-house e-forms.
- **Tsakos:** Athens Performance & Optimization Centre (2023), telemetry + weather routing + in-house "Ultima" platform.
- **Navios:** ERP + VSAT + IoT telemetry trials, public "digitalisation top priority" statements.
- All four: real ops teams, real paper flows, Athens offices — plausible mentors/judges network adjacency.

**Athens maritime-tech scene (the ecosystem mirror):**
- **HarborLab** — Athens, port-cost/DA platform, $30M+ raised (Atomico Series A $16M). **VentureFriends + Endeavor Catalyst + Signal Ocean are investors.** Acquired **SOFeXchange and DEMeXchange (2023)** — they literally bought SOF-digitization + demurrage-exchange companies. Our vertical is their roadmap adjacency.
- **Signal Ocean** — Tsakos-family-backed, tanker chartering data/AI, ~50% of oil-transport industry penetration (Exxon/Shell/Chevron clients).
- **DeepSea** — 95+ ppl Athens, voyage optimization AI, Nabtesco-owned.
- Also: Metis (vessel telemetry), ProcureShip, Seafair (crew platform), Nereus (digital bunkering), Danaos (laytime software incumbent).

---

## 6. Doc-processing task shape

**CP → terms extraction schema** (mirror of Keel's, use as checklist):
`vessel, owner, charterer, load/discharge ports(+coords), laytime_allowance_hours | rate_mt_per_day, laytime_type (reversible/non), shex|shinc|fhex, nor_turn_time_hours, demurrage_rate_per_day, despatch_rate, weather_clause_label, weather_thresholds (bft, mm/h), time_bar_days, incorporated_ruleset, clauses[] {page, bbox, text}`.
**SOF → event stream:** `{timestamp, event_type (NOR_TENDERED|ALL_FAST|CARGO_COMMENCED|WEATHER_DELAY|SHIFTING|CARGO_COMPLETED|DOCS_ABOARD|SAILED...), counts_toward_laytime?, remarks}` — the Layline sample shows exactly this table shape.
**Claim → amount + per-day breakdown.**
**Generation:** laytime statement (deterministic), settlement/response letter (LLM on computed numbers, cited), LOP draft.

Extraction eval harness: hand-computed fixtures + `expected.json` per voyage (Keel `test-cases/` pattern) = "self-built eval, not LLM-judged vibes."

---

## 7. Adjacency — which tedious workflow demos best

| Workflow | Demoability | Taken? | Verdict |
|---|---|---|---|
| **Demurrage reconciliation** (Keel's) | High — visceral $187k→$112k | **Taken by the org's own winner** | Only with a clear step-change (below) |
| **Live port-call ops agent** (AIS-triggered: vessel enters Piraeus anchorage → detect → assemble doc pack → clock laytime → flag weather window → draft claim/NOR) | **Highest aura** — real ships, live on a map; "the agent watched 4 ships this hour" | Open — Keel has zero live data | **Recommended twist #1.** Combines aisstream + the doc pipeline; Keel's math engine pattern still applies downstream |
| **Claims-inbox triage at fleet scale** (dump 30 mixed PDFs → classify doc type → route → extract → check time bar → rank claims by $ exposure; "time bar kills this claim in 11 days") | High — batch processing is visible, time-bar = built-in stakes clock | Open — Keel is single-voyage, no inbox, no time-bar | **Recommended twist #2.** Veson's stated #1 pain (claims team capacity/email volume) |
| **Bunker BDN short-delivery claim file** (bunkering: BDN vs ship ullage >0.5% → agent assembles dispute file: LOP, SOF extract, barge calibration cert, ORB note, notification to principal — "30 min at berth vs weeks later") | High, very concrete, nobody in Athens scene owns it (Nereus is procurement, not disputes) | Open | Strong dark horse; smaller market story |
| **Port disbursement (DA) audit** | Medium — invoices vs tariffs | **HarborLab literally owns this** | Don't compete with a judge's portfolio; do compliment ("we feed HarborLab") if touched |
| Crew certs/MLC doc-chase | Medium-low — real but bureaucratic, less $-visceral | Seafair adjacent | Skip |
| Laytime pure calculator | Dead — commoditized since the '80s (Keel PRD's own words) | B&V/Danaos/Veson | Never headline this |

---

## 8. Recommended demo design

**"Port-Call Claims Agent"** — one screen, three acts, <4 min:

1. **Live trigger:** aisstream WS on Piraeus anchorage bbox; agent detects a bulk carrier arriving (PositionReport → anchor-speed-drop heuristic or destination=Piraeus). Map + vessel card appears. Fallback = recorded Aegean capture or Zenodo Piraeus replay. *Aura moment.*
2. **The work:** agent pulls the voyage's doc pack (fixture CP + two conflicting SOFs + owner claim + real Open-Meteo hourly weather at 37.94,23.65), extracts→schema, runs deterministic state machine, adjudicates disputed weather days with per-day citations. Signed action log visible.
3. **The output:** reconciled claim letter + laytime statement, every dollar traced to SOF-row/clause/weather-obs; human sign-off gate ("approve to send" — the exact gate Keel's continuation plan lists as its #1 missing piece).

**Positioning line:** *"Keel reconciled one voyage after the fact. Ours watches the fleet live, catches the claim before the time bar runs, and shows its working."*
Eval slide: 4 hand-computed cases (borrow Keel's test-case methodology), before/after "analyst 4h → 90s", cost/doc in cents.
**DQ-safety:** do NOT reuse Keel code (different team, different product anyway); ideas are legal, product must be built there. Don't pitch "demurrage reconciliation tool" as the headline — pitch live claims-ops; the reconcile is one step inside.

---

## 9. Who in the room it flatters

- **Apostolos Apostolakis (VentureFriends, judge):** HarborLab is his portfolio — $30M Athens maritime SaaS in this exact doc-automation space. A credible maritime-claims agent = de-risked thesis validation + possible "HarborLab partnership" line. Also his "Greek wedge + global TAM" heuristic: shipping is THE Greek wedge (20% world fleet, Athens HQ'd) with global buyers.
- **Felix de Grey (Endeavor, judge):** Endeavor Catalyst co-invested in HarborLab's $16M round. Same flattery, second judge.
- **Nick Kalliagkopoulos (Big Pi, judge):** his published lens = data-moat + ROI + real customer value. Shipping claims = moat of messy private docs + hard ROI. Big Pi co-hosts the Summit.
- **Zindros:** deterministic engine + cited evidence + signed action log = "checked, not trusted."
- **Pittarokoili / Gianitsos:** hand-computed expected answers, live cost math, real reward signal.
- **Koukoumidis:** extraction schema → could train a small extractor (Krikri/Oumi fine-tune on CP→JSON) and show "SLM vs frontier on SOF-table extraction" table.
- **Assael (if judging):** agent amplifying a demurrage analyst = his human+AI signature.
- **The Panathēnea org itself:** shipping won for them before; a *better* shipping agent confirms their meta rather than copying it.
- **Caution:** Ertval/Keel founders may be in the room (same community). Frame as lineage, not competition.

---

## 10. Risks

- **Derivative read:** headline "demurrage" = "Keel again." Mitigate with the live-ops/fleet-inbox frame. This is the main risk.
- **WS fragility:** aisstream has no SLA, drops slow readers, no browser conns. Mitigate: pre-recorded real capture + Zenodo dataset replay.
- **Domain gotchas a shipping-literate person can spike:** WWD ambiguity (def 15 vs 16), reversible laytime, tanker pumping/3h doc rules, NOR-before-laycan invalidity, time bars from *discharge completion*. Mitigate: keep demo to the fixtures you hand-computed; say "advisory" everywhere like Keel does.
- **Paid-data temptation:** MarineTraffic/Kpler is a trap; everything needed is free.

## Key sources
- Keel repo + PRD + continuation plan: `~/scratch/hackathon-recon/deep2/keel/` (README, docs/prd.md, fixtures/, test-cases/)
- aisstream.io docs; aistrail.com AIS provider comparison; MyShipTracking/VesselFinder API pages; Zenodo 10.5281/zenodo.10006470
- handybulk.com laytime/demurrage guides; voyagerportal.com re-calculating laytime; charterdeck.io worked example
- UGS Annual Reports 2024/25 + 2025/26 (ugs.gr); FMC demurrage figure via Veson blog; Veson Claims CoCaptain launch
- GENCON 94/2022 + NYPE 2015 sample PDFs; BIMCO Laytime Definitions 2013 PDF; Layline/Laytimetech samples
- HarborLab (harborlab.com/about, TechCrunch Dec 2022, Atomico round); DeepSea; Signal Ocean (Elevate Greece registry); Thenamaris ABS NS rollout (Smart Maritime Network Mar 2026); Angelicoussis IEEE GCAIoT 2022 paper; Tsakos POC page; Navios via maritimes.gr
- Bunkering: usebase.io BDN field guide; Britannia P&I quantity-dispute guidance; Skuld bunker disputes
