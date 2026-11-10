---
title: "wonderful clients"
type: source
tags: [hackathon, genai-summit, recon, sponsors]
aliases: ["wonderful clients"]
created: 2026-11-10
updated: 2026-11-10
status: active
---

# Wonderful (wonderful.ai) — Greek Deployments Deep Recon
*For GenAI Summit Hackathon challenge-brief prediction. Athens, 14–15 Nov 2026.*

## Company baseline (context anchors)

- Founded Jan 2025, Tel Aviv founders (Bar Winkler CEO, Roey Lalazar CTO), legal HQ Amsterdam. ~850 staff, 35 countries, 150+ enterprise clients, 12 sectors. ARR ~$80M end-Sep 2026.
- Funding: $34M seed (Index, Jul 2025) → $100M Series A (Index, Nov 2025) → $150M Series B (Insight, Mar 2026, ~$2B) → $550M Series C (Sep 2026, ~$5B). Investors: Index, Insight, Bessemer, IVP, Vine, 9Yards, Salesforce.
- Product: **Wonderful AI OS** — model-agnostic orchestration layer for agents/workflows/apps over existing systems. Products: end-to-end workflow automation, employee productivity agents, AI-native apps, conversational agents (voice/chat/email). Primitives: Skills, Orchestrator, Workspaces, Knowledge, Evals, Guardrails, Permissions, CLI, A2A.
- Model: **FDE + Deployment Strategist pods** embedded on-site; take deployment to production, then transfer know-how so client self-serves ("deployment partner, not a vendor"; agents treated as evolving organisms needing upskilling). FDE JDs explicitly include **telephony solution architects** and Twilio/Asterisk-type telephony work. DSs are "measured on customer P&L outcomes."
- Greece = top-3 market globally (with Italy, Switzerland). Athens office opened mid-2025; 31 staff (mostly engineers), doubling by 2027; hub for GR, CY, MT, BG, TR (~50 staff). GM SEE: **Ilia Tzortzopoulou** (ex-Endeavor, Morphoses co-founder/COO; past client work incl. HERTZ, Interamerican, IKEA — explains the Autohellas/Hertz win and likely insurer pipeline). Site CTO SEE: **Georgios Kontogiannis**. Actively shopping for Greek AI acquisitions.

## 1. OTE / Cosmote TV (flagship)

- First-ever Wonderful project for the Deutsche Telekom group, started in Athens; now supports DT in **5 countries** (voice + written service).
- Scope: inbound subscriber calls for **Cosmote TV (now Magenta TV)**. Call types: subscriber authentication/ID, set-top-box technical troubleshooting, satellite service restoration, packages & pricing info, profile management, TV-listings search, password/PIN changes, subscription/billing issues. Later extended to **contracts and roaming**; internal-process pilots under consideration.
- Build: 8 weeks kickoff→production. **31 API integrations** across legacy + modern systems that didn't talk to each other; **10–11 customer journeys/service flows** (~2,500 inbound calls/day on that scope).
- Results: **~50% zero-touch containment** (reached within ~2 weeks of go-live, ~3× the ~20% baseline/initial benchmark), **−30% AHT**, "tripled deflection" per official blog (wonderful.ai/blog-articles/ote, May 21 2026 — JS-walled; numbers corroborated by Tzortzopoulou's LinkedIn + Greek press). OTE contacts named: Athanasios (Tom) Stratos, Yannis Vitzilaios.

## 2. Piraeus Bank

- **Voice agents (plural) into production May 2026, 12 weeks** — only publicly disclosed fact; workflow *not* published (support vs collections vs onboarding undisclosed). WSJ reportedly covered the speed of the Greek projects.
- Context to reason from: Piraeus' contact center = Piraeus Direct Services (Genesys + Omilia NLU IVR stack since 2014 — Omilia is a Greek competitor vendor). Piraeus also runs a GenAI "Virtual Assistant" in e-banking/app (GR+EN, voice) and an Accenture+Anthropic "AI Hub" (Apr 2026) — so the Wonderful piece is most plausibly **inbound call-center voice support** (auth → lookup → action), not the in-app assistant or collections.
- Analog from Wonderful's own banking case: **Bank Hapoalim** voice agent for appointment scheduling — <90s calls, 75% resolution, 97% positive sentiment, 4,000 interactions in 6 weeks, 72h integration. Expect Piraeus to be similar-shaped (bounded, high-volume, API-heavy).

## 3. ELTA (Hellenic Post) — best-documented after OTE

- Official blog (wonderful.ai/blog-articles/elta, Jul 14 2026): **24/7 automated parcel-tracking line**, live in **5 weeks**, started early 2026.
- Problem: ~40% of inbound calls dropped/abandoned at peak; prior automation failed on **spoken Greek tracking numbers** (mixed alphabets, regional pronunciation).
- Engineering that won it: guided alphanumeric capture in **segmented digit/letter groups**; phonetic disambiguation via familiar reference words; **targeted recovery** on misheard segments (no full restart); noise/accent/irregular-pacing handling. Pre-launch: **10 days UAT × 100 tests/day**; post-launch iteration on real pacing patterns.
- Results: **86% resolution in production**, calls/day **~500→~2,000 (4×)** with zero added headcount, peak wait **10min→0**, humans shifted to outbound sales/complex cases. Quote: Marios Tempos, Deputy CEO ELTA.

## 4. Ethniki, Viva, Hellas Direct, Autohellas/Hertz

- Named as clients at the Nov 4–5 2026 Athens hub press event (7 "announceable" partnerships total). **No published workflow detail** for any of the four.
- Probable shapes from Wonderful's sector pages + context: **Ethniki** (NBG-group insurer, #1 in Greece): service/FNOL claims intake — Wonderful's insurance page sells FNOL→payout, underwriting, servicing; Ethniki already automates small claims internally (≤€100 health, ≤€300 motor), so Wonderful's wedge is voice/service. **Viva** (viva.com, merchant acquiring/POS): merchant support/onboarding. **Hellas Direct** (digital motor insurer): claims/roadside/renewals. **Autohellas/Hertz**: reservations/roadside/fleet service — Tzortzopoulou's prior HERTZ relationship is the warm path.
- Also on the /greece page: "partnering with some of Greece's largest **banks, e-commerce companies, and airlines**" — unnamed; airline vertical page advertises Amadeus/Sabre/Navitaire integration + EU261 claims (Aegean the only plausible target). Nespresso Greece CEO provides the page's testimonial → retail/e-com beachhead.

## 5. Next verticals: energy, retail, shipping — target list

Stated targets (Tzortzopoulou): telecom, banking, **energy, retail, shipping (ναυτιλία)**, plus public sector + logistics.

- **Energy — near-certain first win: PPC/ΔΕΗ.** Her SEE team already put **PPC Romania's** voice agent live in **4 weeks** (Jul 2026): AHT 6min→90s, **77% containment**, 91% positive feedback, integrated with billing/contracts/IVR. PPC Greece is the same group → Greek utility deployment is the obvious next case study. Secondary: Heron, Protergia (Metlen), Elpedison, Zenith, NRG/Volton. Wonderful's site literally advertises "Billing resolved end-to-end for energy customers."
- **Retail:** Nespresso already a reference. Candidates: Public Group (Public+MediaMarkt), Jumbo, Kotsovolos, Plaisio, efood, Skroutz, AB/Sklavenitis e-commerce. Olympia Group's CEO is a Summit speaker (Olympia owns Alter Ego + retail interests).
- **Shipping:** wedge is ops/crewing/document workflows + travel/ferry customer service, not consumer calls. Candidates: Attica Group (Blue Star/Superfast), ANEK; ship managers Angelicoussis, Navios, Thenamaris, Minerva, Tsakos, Star Bulk, Costamare, Danaos, Capital, Dynacom/TMS, GasLog — plus maritime-adjacent logistics (ACS, Orphee Beinoglou). Piraeus is the world cluster; an Athens-hired FDE pod sells this hard.

## 6. Deployment pattern → what "compressed" means for a demo

- Real cycle: **4–12 weeks** (ELTA 5wk, PPC RO 4wk, OTE 8wk, Piraeus 12wk — banking heaviest). Shape: embed pod → discovery → integrations → structured UAT (ELTA: 10×100 tests) → go-live → iterate on live traffic → hand keys, client builds on platform, pod leaves. Zero perpetual professional services; recurring platform revenue.
- Hackathon compression: discovery/UAT/hand-off collapse into "working demo against live-or-mock systems"; the durable signature = **containment as the metric** (they report containment/resolution/AHT/sentiment in every case study), integrations into real systems, and error-recovery design. A team mimicking Wonderful should demo: real tool calls, a failure-recovery path, eval numbers — not a prompt.

## 7. Greek voice stack

- **No evidence of ElevenLabs.** Google Cloud case study: Gemini is the core of the real-time voice pipeline, "stitching together multiple speech and reasoning models" for dozens of languages; Vertex AI for orchestration; ZDR (in-memory only); GKE/Compute. OS is model-agnostic — routes per task. So: hybrid native-audio + STT→LLM→TTS chaining, model-swappable.
- Greek is a named supported language; "obsessed with locality" — Italy alone runs 20+ voice variants for dialects/gender → expect tuned Greek voices, and the ELTA work proves phonetic-level Greek engineering (alphabet mixing, accent recovery).
- Telephony: enterprise contact-center integration (IVR/billing/CRM per PPC; Genesys-era stacks at Greek enterprises; Twilio/Asterisk skills in FDE JDs). No public OTE-wholesale telephony detail.
- Sentiment: they publish sentiment metrics (97% Hapoalim, 91% PPC RO) → post-call/inline sentiment scoring exists; Greek-specific mechanism undisclosed.
- Competitive note: ElevenLabs separately signed a Greek-gov MOU (gov.gr, call centers; Alpha Bank, Sfakianakis, BOX NOW are EL clients); Omilia (Greek voice-AI) holds Piraeus' IVR legacy — Wonderful is fighting on their turf with a Gemini-centered stack.

## 8. Hackathon facts + challenge-brief prediction

Facts: 36h, Athens LifeTech Park, ~100 builders, teams 1–5, finalists pitch on GenAI Summit main stage at SNFCC Mon Nov 16. Theme: "Agents at Work" — real work end-to-end. Judged on usefulness, craft, "aura points"; "make it work and show the demo." Challenges plural, announced at event. **Prizes €5k/€2.5k/€1k funded by Quintessential + Wonderful** (Wonderful = partner + prize co-funder, not sole title sponsor). Tzortzopoulou is a Summit speaker/panelist → Wonderful sends mentors/judges; they're doubling Greek eng headcount → recruiting funnel motive.

**Predicted Wonderful brief — 3 candidates:**

1. **"Ship a production-grade voice agent (Greek-preferred) that survives a live call" — ~45%.** Their entire brand is voice agents for non-English markets; every Greek case study is a phone line; a live phone-call demo on the SNFCC stage = maximum aura. Likely spec: high-volume intent (tracking/booking/billing dispute), real telephony or browser voice, judged on containment + Greek robustness (accents, alphanumeric capture, recovery).
2. **"FDE sprint on a mock enterprise stack" — ~35%.** They provide synthetic enterprise APIs/KB + a workflow spec (insurance FNOL, utility billing, shipping ops, bank servicing); teams wire an agent end-to-end (auth→lookup→action→confirm) with evals/guardrails; judged on resolution rate over scripted eval calls. Mirrors their delivery model and "measured on outcomes" DS culture; most plausible if they supply the platform as substrate.
3. **Open "agent at work" track, Wonderful co-judges — ~20%.** No bespoke brief; they back the most deployment-real project (Greek voice/integration depth as tiebreaker). Fits "challenges announced at event" ambiguity but underuses their differentiation.

**Build-hint for us:** whichever lands, the winning Wonderful-flavored demo = e2e task completion on real tools + measured containment + one gnarly Greek edge case handled (spoken tracking number, Greeklish, name/address spelling) + a graceful failure/recovery path on stage.

## Sources (key)

- wonderful.ai (/, /agents, /ai-os, /industries/*, /greece, /blog-articles/{ote,elta}, /case-studies/financial-services)
- cloud.google.com/customers/wonderful (Gemini/Vertex/ZDR voice pipeline)
- euro2day.gr/en/article/2376776 (7 clients, funding, Cosmote detail, next sectors)
- insider.gr/epiheiriseis/431492; ot.gr 2026-11-04/05; newmoney.gr; forbesgreece.gr; cnn.gr; powergame.gr; nextdeal.gr; dealnews.gr (ELTA)
- LinkedIn: Ilia Tzortzopoulou posts (OTE 30+ APIs/10+ journeys; PPC Romania 4wk/77%/90s); wonderfulcx post (OTE tens of thousands of calls, 3× deflection, −30% AHT)
- jobs.ashbyhq.com/wonderful (FDE/DS roles incl. telephony architects); amplifyit JD (Twilio/Asterisk)
- hackathon.polymath42.com; luma.com/x1wxi5sn; genaisummitseeurope.com (speakers, Bernitsas panel w/ Tzortzopoulou)
- piraeusbank.gr virtual-assistant pages; omilia.com Piraeus IVR case; wsj.com seed-round piece; woshipm.com (ELTA recap)
- Gaps: Piraeus workflow undisclosed; Ethniki/Viva/Hellas Direct/Autohellas scopes undisclosed; TTS vendor unconfirmed (no ElevenLabs link found).
