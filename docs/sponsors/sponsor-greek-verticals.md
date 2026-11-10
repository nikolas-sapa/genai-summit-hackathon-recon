---
title: "sponsor greek verticals"
type: source
tags: [hackathon, genai-summit, recon, sponsors]
aliases: ["sponsor greek verticals"]
created: 2026-11-10
updated: 2026-11-10
status: active
---

# Deep teardown — Greek sponsor verticals
Gen AI Summit Hackathon, Athens LifeTech Park, 14–15 Nov 2026 · finals SNFCC 16 Nov
Companion to ../sponsors-local.md (shallow scan). This file: what each platform actually does, AI already shipped, real pain points, the agent they'd ship, and local data/APIs you can wire in 36h.

---

## 1. Prosperty — theprosperty.com

### What the platform actually is
Hybrid real-estate transaction platform + proprietary property-data company, not just a portal. Four revenue surfaces:

- **B2C marketplace** — 12,000+ active listings, 800k+ monthly visitors. Verified/inspected properties ("majority undergo technical inspection"), 360° video, floor plans, photorealistic AI redesign for renovation candidates. Buyer premium package: certified lawyers/notaries, mortgage pre-approval in 3–4 working days via Eurobank, single coordination point. Seller promise: "sale in 60 days", free Electronic Building ID (Ηλεκτρονική Ταυτότητα Κτιρίου) included, "up to 3× faster sale".
- **B2B institutional channel** — the Eurobank deal is the real business: 800 bank-owned REOs onboard at signing (Apr 2025), target 2,000 by year-end. Positioning per Despotakis: "B2B technology and data platform" for institutional investors, asset managers, servicers, developers, family offices. Products built for Prosperty are also sold as SaaS to B2B clients.
- **Agent-enablement product** ("Services for Agents") — recruit independent agents; they get leads (pre-qualified, ~30% mortgage-approved, 30,000+ buyer pool), CRM with AI assistant + WhatsApp integration + automated workflows, SmartMatch similarity scoring, AVM access. Hiring agents in Athens, Thessaloniki, Patras, Crete. This is a brokerage-in-a-box play.
- **Private auctions + transaction orchestration** — private (not judicial) property auctions on-platform; "transfer in 90 days" service coordinating lawyer, notary, engineer.

### AI already shipped (CPO Antonis Despotakis, LinkedIn — literal list)
- **AVM** — automated valuation on actual property transfers + per-area market prices + real-time supply/demand
- **SmartMatch** — buyer↔property matching with similarity scoring across 30k+ buyers
- **AI-enabled search**; **AI redesign** (generative renovation renders)
- **AI assistant in custom CRM** + WhatsApp integration + lead-management automations
- **Investment analysis app** (price, rent, yield per property — public on buy pages)
- **Greek cadastre price map**; **dynamic newsletter**; workflow automations

So: don't demo "an AVM" or "property matching" — they have both and will say so on stage.

### Real Greek-market pain points (attack surface)
- **Μεταβίβαση doc-chase.** A sale needs: Electronic Building ID (Taftotita Ktiriou, mandatory since 2023-ish), cadastre KAEK extract + topographic diagram, ENFIA property-tax cert, TAP/municipal cert, energy cert (ΠΕΑ), engineer legality/unauthorized-works cert, tax clearance, no-debt EFKA cert, seller's E9 alignment. These live in ~6 different systems (gov.gr, AADE myProperty, cadastre office, municipality, engineer, accountant). Human runners do this today; it's why "transfer in 90 days" is a *marketed promise*, not a default.
- **Dual land-registry mess.** Greece runs κτηματολόγιο (cadastre, KAEK-keyed) alongside υποθηκοφυλακείο (mortgage registry, person-keyed) in transition regions — title verification is manual.
- **Diaspora/foreign buyers.** Golden-visa demand + Greeks abroad need: AFM/TIN without presence, digital POA (gov.gr issues e-POA now, consulates otherwise), translated docs, currency/banking coordination, remote signing choreography.
- **Bank REO pipeline ops.** 800→2,000 properties: intake, verification, valuation, listing enrichment, broker dispatch — all ops headcount today.
- **Judicial auctions** on eauction.gr are XML/PDF dumps — unstructured, no clean API.

### The agent they'd ship — "Μεταβίβαση Runner" (transfer doc-chase agent)
An agent that takes a signed preliminary agreement and drives the file to notary-ready: builds the doc checklist per property (cadastre region? arrears? engineer cert needed?), requests/collects each document from its system or human owner (nags the seller's accountant on email/Viber, books the engineer visit, pulls KAEK extract), OCRs/validates each doc against the property file (KAEK matches listing? surface area discrepancy? mortgage/lien flags?), maintains a live deal-status board, and schedules the notary signing window when green. Output: the "90 days" promise becomes instrumented — every deal has a bottleneck score.

**Why they ship it:** it's their single biggest ops cost and their marketing promise ("90 days") made real; uses their proprietary data; sells to every Greek brokerage + Eurobank's REO pipeline as SaaS. Bonus: demo-able in English *and* Greek doc samples.

**Alternates:** diaspora buyer concierge (POA + AFM + remote-signing orchestration); REO intake/triage agent for the Eurobank backlog (valuate → verify → enrich → dispatch to broker); eauction.gr monitor that turns seizure-report PDFs into structured investment memos scored by their AVM.

### Local data sources / APIs
| Source | What | Access |
|---|---|---|
| data.ktimatologio.gr | Cadastre open-data portal (DCAT/DKAN, CSV + API) | Public |
| webktim.ellak.gr/api | Cadastre API (KAEK lookups, diagrams, certs) | Restricted — notaries/public bodies; demo against mock |
| GSIS/KED webservices | e-Μεταβίβαση, cert requests (ΣΠΕΚ) | Public-sector only |
| eauction.gr (IL.SY.PLEIS) | ALL judicial auctions since Feb 2018 | Public browse/search; bidder reg via TAXISnet; scrape |
| deltio.tnomik.gr | Auction publication bulletin (seizure reports) | Public, unstructured PDF |
| AADE myProperty | E9 auto-fill, transfer tax filing, KAEK pull (new Oct 2026) | TAXISnet-auth, no public API |
| gov.gr | Electronic Building ID, digital POA (e-εξουσιοδότηση) | Citizen-auth |
| Spitogatos / XE.gr | Listing + SPI price index | No public API; SPI index published periodically |
| Bank of Greece / ELSTAT | Residential price indices, transactions | Public datasets |
| geodata.gov.gr | Cadastral parcels WMS/WFS | Public |

36h demo path: mock the restricted endpoints, live-hit cadastre open data + eauction.gr scrape + BoG index; the *chase-and-validate* loop is the demo.

---

## 2. Crowdcruit — crowdcruit.com

### What the product actually is
Skills-first technical hiring platform, founded Jan 2025, ~8 people, EnvolveXL cycle-3 (Apr 2026). Three consumption models:

- **Crowdcruit Console** (self-serve SaaS): skills-based evaluation, side-by-side candidate comparison, integrated video interviews, hiring pipeline.
- **Crowdcruiting** (managed): certified domain expert ("Crowdcruiter") runs a structured 45–60 min technical interview — requirements brief → domain-matched expert → interview w/ rubric + code environment → detailed evaluation report w/ skill breakdown, strengths, concerns, hiring recommendation, recording. 48h average turnaround.
- **CrowdVibe** (flagship differentiator): sandboxed full IDE with an *embedded AI pair-programmer* — candidates solve real-world scenarios while allowed to prompt/push back on AI. Score on 5 axes: **AI Leverage, Task Completion, Critical Review, Code Quality, Speed** — "one score, five dimensions, no black box." This is deliberately anti-ban: they assess how you work *with* AI.
- **Crowdcruit Connect**: peer-to-peer knowledge community (their "ecosystem" moat).
- Domains: Cybersecurity, SWE, AI/ML, Data, Blockchain/Web3, Cloud/DevOps. 2,000+ vetted pros, 30+ interviewing experts.
- Team: Evangelos Mourikis (CEO — OSCE3 offensive-security specialist, also runs Aethersec), Alexander Modis (CTO), Ignatios Iliopoulos (SWE).

### Real pain points
- **Expert bottleneck** — 30 humans is the supply side; every interview is 45–60 min + write-up. Scaling = margin-killing unless the write-up/calibration is automated.
- **Report consistency** — rubric quality varies by expert; calibration across 30 people is a data problem.
- **Cheating-vs-leverage ambiguity** — CrowdVibe *sanctions* AI use inside the IDE, but out-of-band help (second device, live human, proxy) still exists. For an OSCE3 CEO, session-integrity is core credibility for remote assessment.
- **Matching ops** — domain-matching brief→expert→candidate is manual.

### The agent they'd ship — "CrowdVibe Debrief + Integrity Agent"
Two-headed agent on top of session telemetry:

1. **Debrief agent** — consumes IDE session logs (prompts to the AI assistant, diffs, test runs, review comments on AI suggestions) + the expert interview recording → drafts the structured evaluation report *in Crowdcruit's rubric format* (5-axis CrowdVibe score + strengths/concerns/recommendation + timestamped evidence links). Expert edits and signs — human stays the verifier, machine kills the 40-min write-up.
2. **Integrity agent** — replays session telemetry for out-of-band-assistance signatures: paste-burst cadence vs typing entropy, solution provenance mismatches, suspicious "Critical Review" inversion (accepting everything → leverage theater), timing anomalies vs population baseline. Flags, never auto-fails — matches their "humans verify" ethos.

**Why they ship it:** attacks their two scaling constraints (expert write-up cost, remote-integrity trust) and is a *data* product — every session makes calibration better. The integrity half flatters a pentester CEO without claiming to replace his experts. Strongest demo: replay a staged cheating session vs a legit high-leverage session, show the report diffs.

**Alternates:** brief→rubric generator (turn a JD into the structured interview brief + scenario their experts use); interviewer-matching agent on Crowdcruit Connect profiles; candidate-feedback agent generating growth-oriented reports for rejected candidates (community goodwill → supply growth).

### Local data sources / APIs
- ESCO skills taxonomy API (EU, free, official) + O*NET — skills graph for matching/rubrics
- GitHub/GitLab APIs — candidate artifact enrichment
- Greenhouse/Lever/Workable webhooks — ATS handoff for "report delivered" events
- CrowdVibe session telemetry — their proprietary gold; you'd demo on synthetic logs
- DYPA/ΕΡΓΑΝΗ ΙΙ (labor-market, no public API — mention only)

---

## 3. Always Online — thealwaysonline.com

### What they actually sell
AI strategy + implementation micro-agency, ALWAYS ONLINE TECHNOLOGIES Ι.Κ.Ε., founded 2025, Agios Dimitrios, Athens, 3 people. Andriana Lazana (co-founder, AI Solutions Architect — ex-KPMG consulting, ex-Shenergy community/marketing, AUEB software+data). Giorgos Papageorgiou (AI Solutions Architect). Clients: Greece, Dubai, Brussels. Visible client: **LAMDA Development / The Ellinikon** (enterprise AI training for marketing teams). Claim: "100+ AI use cases mapped across industries."

Three-pillar offer, verbatim their roadmap:
- **AI Discovery** — structured interviews across departments → workflow analysis → prioritized use-case roadmap. Sold *before* any build.
- **AI Implementation** — "build inside your existing stack. No new tools to buy. No long rollouts. First system live within weeks, documented and owned by your team." Agents, automations, integrations, custom products.
- **AI Enablement** — workshops, leadership sessions, newsletter, ongoing advisory.

Positioning: "practitioners, not theorists"; "most companies don't have an AI problem, they have an execution problem"; ownership transfer to client team. Target customer = Greek/regional mid-market & SME (plus LAMDA-tier enterprises for training).

### Real pain points of a 3-person implementation shop
- Discovery is unscalable consulting labor (interviews → maps → roadmap decks).
- Every proposal needs a credible "weeks not months" reference demo.
- Greek SME stack reality: invoices via myDATA, accountant external, comms on Viber/WhatsApp + Gmail, ERP = SoftOne/Entersoft/EShop/EpsilonNet, payments Viva.com, everything else in Excel.

### The agent they'd ship — "Greek SME Receivables Agent" (reference implementation)
An agent living in an SME's existing stack that: pulls issued/received docs via **myDATA API** (RequestMyIncome/RequestMyExpenses), reconciles against bank feed (Viva.com API) and emailed invoices, drafts + sends overdue-payment chasers in natural Greek over Viber/email (tone-matched, escalating cadence), flags myDATA↔book discrepancies for the external accountant, and posts a weekly cash-flow digest to the owner's WhatsApp. Runs on whatever the SME already has — the literal "agents in your existing stack in weeks" pitch, demoed end-to-end.

**Why they ship it:** instantly resellable to every Greek SME client; every artifact (Greek chaser emails, myDATA XML handling, reconciliation rules) is a deliverable they can productize; it's their own sermon preached back to them. The meta-version — "Discovery-in-a-box" agent that interviews departments and emits their prioritized use-case roadmap — is a strong alternate (productizes their most expensive hour) but harder to demo convincingly in 36h.

**Alternates:** grant/ΕΣΠΑ-funding watchdog agent for SMEs (scans diagoumos.gr/ΕΣΠΑ calls, matches eligibility, drafts application checklist); Viber customer-service agent for a typical SME e-shop.

### Local data sources / APIs
- **myDATA REST API** (AADE) — free dev environment (mydatapi-dev.aade.gr), XML; OSS client `firebed/aade-mydata` (PHP) + invoicemaker.gr docs
- **Viva.com API** — Greek PSP, clean REST/smart-checkout APIs, sandbox
- **ΓΕΜΗ** business registry via data.gov.gr API — company lookup/enrichment
- **Viber Business Messages** (Rakuten — huge in Greece), WhatsApp Business API
- SoftOne/Entersoft/EpsilonNet (E-SHOP) ERP APIs — the actual Greek SME ERP layer
- diagoumos.gr / ΕΣΠΑ (espa.gr) public calls — grant scanning
- gov.gr document wallet — no public API (mock)

---

## 4. Wiserwork — wiserwork.ai (organizer's own product — DO NOT rebuild)

### Coverage map — everything between "calendar invite" and "finished deliverable"
Product of 100mentors (the summit organizer — impressing them = impressing the house). Already shipped:

- **Ingestion:** calendar sync (Google/Outlook); bot joins Meet/Teams/Zoom as participant w/ consent + waiting-room flow.
- **Curator Agent** — structured agenda in <3 min via guided chat (pre-meeting).
- **Moderator Agent** — real-time: keeps discussion on-agenda, per-topic timing, live action items (during meeting).
- **Project Manager Agent** — post-meeting: summary, decisions, action items, timestamped + searchable, delivered to *all participants* (team-shared, not private notebook).
- **Skills / SkillBase™** — role-specific deliverable templates (PRD, campaign brief, scorecard, proposal, client-recap tone) built on team "first principles"; your A-player's workflow becomes everyone's default.
- **AskWiser** — chat over entire meeting history ("what did we promise the client…"), emits answers or *finished artifacts*.
- **MCP** — meetings exposed inside Claude/GPT/Cursor; **webhooks** on Business plan.
- **Pricing quirk:** unlimited users, pay per meeting-minute (~€50/15h → €150/60h) — explicitly anti-seat-pricing.

**Red zone (they own it):** meeting capture, notes, recaps, action-item extraction, meeting→deliverable generation, meeting memory/Q&A, agenda creation, live moderation.

### What's safe + flattering (green zone)
- **Pre-meeting context agent** — builds the research/diligence brief that *feeds into* a wiserwork-moderated meeting (CRM history, prior promises via AskWiser webhook, external data). You're upstream, not competitive.
- **Action-item executor** — wiserwork emits action items (webhook); your agent actually *does* them: files the Jira ticket, drafts+sends the client follow-up on approval, books the vendor call. "The follow-up does itself" → "the follow-through does itself." Completes their story rather than cloning it.
- **Vertical Skill packs** — Skills are a library; contribute domain Skills they don't have: a *notary/closing-meeting Skill* (Prosperty flavor) or *interview-debrief Skill* (Crowdcruit flavor). Cross-sponsor play = judges see three sponsors in one demo.
- **MCP server for Greek data** — expose cadastre/myDATA-style lookups as an MCP tool that wiserwork (or any agent) calls mid-meeting.

---

## Judging frame (all four)
Sponsor judges score one question: "would we ship this?" Pick ONE vertical, name the agent after their vocabulary (Μεταβίβαση, CrowdVibe, "in your existing stack", SkillBase), show real local data (even one live source beats full mock), and end on the artifact they'd put in front of a customer. Cross-sponsor demos (e.g., Crowdcruit-flavored Skill delivered through wiserwork, or Prosperty doc-runner built the Always Online way) compound aura.
