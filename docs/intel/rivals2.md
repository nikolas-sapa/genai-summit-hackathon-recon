---
title: "rivals2"
type: source
tags: [hackathon, genai-summit, recon, intel]
aliases: ["rivals2"]
created: 2026-11-10
updated: 2026-11-10
status: active
---

# Gen AI Summit Hackathon — Rivals Deep-Pass 2
Recon date: 10 Nov 2026 · Event 14–15 Nov, Athens LifeTech Park · 162 Luma regs / ~100 selected · FULL
Companion to: `deep/competition.md` (pass 1), `MASTER-BRIEF.md`, `deep/mentor-table.md`
Method delta vs pass 1: named-member confirmation, repo/product archaeology, mentor-vs-competitor verdicts, post-Nov-1 signal sweep.

---

## 1. REELIO SQUAD — all 5 confirmed, project decoded, reformation read

**Reelio (the project):** AI video editor — raw footage → social-ready content: cuts, captions/subtitles, effects, audio cleanup, platform-specific copy. Origin = **Leonardou's own OSS skill** `artemisln/edit-greek-reel` (~40★, gained from a single IG story) — Build Week gave it a UI. Won 1st at OpenAI Build Week Athens (20 Jul 2026; 6 teams/18 builders, community-voted, $8.5k OpenAI credits). Post-win: "private beta is coming" + waitlist DM — so Reelio is semi-alive as her side product, not dead. (NB: reelio.ai "faceless video" SaaS is a same-name product, likely unrelated; a Callour Studio design post suggests external design help touched the brand.)

**The five, with roles:**

| Member | Confirmed | Strength in squad | Where they are now |
|---|---|---|---|
| **Artemis Leonardou** (@artemisln) | Winner-posted, team lead ("the 4 people who said yes to MY idea") | Idea owner, eng + pitch + audience | SWE+DevRel NOFire (Orchestration/Context), NKUA top-1%, 590k IG views/mo, HackathonHub ambassador ATH |
| **Panagiotis Mavrikos** (panosmaurikos) | Named in all posts | Deepest eng — systems/sandbox | NOFire MTS Core Infra (agent execution envs), ex-Nubificus urunc CNCF, Omnyo co-founder, MSc in progress |
| **Eleni Zafeiri** (@elenizafeiri) | Named; posted hackathon promo 28 Oct | Pitch + content (technotesgr 100k+ views) | NKUA CS 3rd yr, HackathonHub ambassador ATH, "10 hackathons, 3 wins" |
| **Odisseas M. Karypis** (@odisseasmk) | **CONFIRMED attending** — "Will I see you at Gen AI Summit Hackathon?" 1 Nov | Narrative/strategy, vibe-build | Digital strategist 18y, Vibe&Build founder, "3x AI Hackathon Winner" |
| **Anastasia Michail** (@anmichail) | Winner-posted | Product/strategy framing, demo polish | AI Product/Strategy, Lovable ambassador (Athens city lead), Top-50 AI Experts 2026, Athens·Zürich |

**Reformation verdict:** Partial, not full-five. Karypis confirmed in; Zafeiri promoted the event (in, or organizing-adjacent via HackathonHub); Leonardou is Athens-based + hackathons are literally her brand (10+, 3 firsts) — probable. Mavrikos = the swing seat (NOFire's unsigned sponsor status decides table-vs-builder). Michail probable. **Most likely shape: TWO nuclei** — a creator/vibe axis (Zafeiri+Karypis+Michail) and a NOFire eng axis (Leonardou+Mavrikos, possibly + Ioannidis/Omnyo). Two nuclei = two finalist slots spoken for.

---

## 2. ARTEMIS LEONARDOU — dossier

- **Day job is the theme:** NOFire Orchestration & Context team — "decides what context an agent gets and how its actions are coordinated" (welcome post, Jun 2026). She builds agent-orchestration infra professionally.
- **Stack:** full-stack TS/Next.js + Tailwind (Open Conf workshop tags: AI-augmented dev, agentic engineering, Next.js); Lovable UGC creator → vibe-to-prod workflow; prior prod: KanoParty (payments, pipelines, pricing — 1.5y founding eng).
- **Win history:** 10+ hackathons, **3 firsts** — OpenAI Build Week (Reelio), EpirusBank OpenHackathon (`epirus-shield` scam-call detector — real-time voice fraud), +1. YC AI Startup School '25 (~3k selected). Speaker: React Summit, SREday SF (Oct 2026), DevConf.US (Sep), Open Conf workshop (21 Nov — she's in town the whole week).
- **Content:** @artemis.codes + @artemisvibecodes — 590k IG views/mo, 2M+ lifetime; AI-assisted building, prompting technique w/ receipts, event coverage. She will almost certainly post the event → halo effect with judges + recruting-cycle attention.
- **Mentor-or-competitor verdict: 65/35 COMPETITOR.** NOFire is courted (deck `?sponsor=nofire` exists in llms.txt) but NOT on the public partner list → unsigned → she's a free agent. Watch: if NOFire confirms a table this week she flips to DevRel-duty mode.

---

## 3. AGENTIC ATHENS — confirmed MENTOR crew (not competitors)

- Official announcement 29 Oct: "bringing the Agentic Athens crew to the hackathon as mentors" — signed Tsolakidis + Kollaros. Mentor package: scoping help, architecture/tool-use, debugging, demo feedback. They also told their ~63-person community to "form a team, sign up" → feeder pool.
- **Konstantinos Tsolakidis:** founder/fractional-CTO WeAreFabbrik (3-person Athens studio, est. 2018 Estonian OÜ). Shipped **Callen AI** — production Greek voice receptionist for dental SMBs: Twilio + streaming STT + GPT-4 + ElevenLabs + Next.js, self-serve in ~30min, billing/RBAC/metering, ~14 weeks to 90% prod. **The only production Greek voice agent in the room — sits mentor-side.** Blog posts the full voice-pipeline architecture publicly.
- **Nikiforos Kollaros:** Head of Design @ The Signal Group (~20y, ADPList mentor, KEIK Bureau co-founder). Built **Promptotype** (OSS, MCP server + Chrome ext) — point-and-click visual editing of running UI → structured markdown feedback to coding agents. Design-engineer with agent-tooling taste; also WeAreFabbrik's UI/UX arm.
- **Marios Tasos:** Fabbrik senior full-stack — likely third mentor at their table.
- **Community:** founded Jan 2026, meets ~bimonthly at SuiHub (Agiou Markou 22), EN-language. #1 ~64 went, #2 (20 Oct, "Building Production-Ready Agents" + fireside w/ Alex Christopoulos-Panoutsos) 63 went. **#3 announced: engineering deep-dive (evals, observability, cost, latency, guardrails)** — date TBD; if it lands before 14 Nov it's the last pre-hack formation mixer. Contact hello@agenticathens.com; **no public Discord** — community lives on Luma + LinkedIn page.
- **Visible members who may register:** Enes Hoxha, Evangelia, Yasser zghinou (Luma attendee names).
- **Exploit, don't fear:** their table is free consulting on the two hardest parts — agent scoping (Tsolakidis ships them for clients) and Greek voice (Callen AI's exact stack). Kollaros can un-jank demo UX in one pass.

---

## 4. HACKATHONHUB — Athens node

- Athens has **TWO ambassadors, both Reelio members: Leonardou (ann. 25 Aug) + Zafeiri (ann. 2 Sep)** — the local hub IS the Reelio network.
- Hub itself: hackathonhub.eu, 347 events listed, 40+ partner societies, 110+ ambassador network across 25+ countries, **Discord exists but "early development"**. Athens chapter formation = whoever the two ambassadors rally; expect them to pull student followers (technotesgr + artemis.codes audiences) into the event.
- **Net effect:** the hub amplifies the Reelio axis + brings NKUA/AUEB student traffic. No third Athens hub figure of note found.

---

## 5. CHRISTOS PORIOS — gov-tech, mentor-or-compete 55/45

- **Schema Labs** (nonprofit, steward-owned + for-profit sub, Helidoni founding donor): 6-person team — Porios (tech/product), **Andreas Kouloumos** (tech, 946 commits), Gkimitzoudi, Papadogiannis, Plemmenou, Georgakopoulos (board).
- **OpenCouncil** (`schemalabz/opencouncil`, 61★, AGPLv3, TS/Next.js): 14 municipalities, 773 meetings; transcription → speaker ID (voiceprints) → subject splitting → summaries → citizen notifications → AI-generated podcasts/TikToks/Reels ("AI journalist for council meetings") + Diavgeia decision-linking.
- **Agent-native builder:** repo contributors include `claude` (212 commits), `openhands-agent`, `cursoragent` — he literally ships with coding agents. Also `diavgeia-cli` (TS client for the transparency API — the same data plane our procurement-watchdog direction uses) and `nix-openclaw`.
- **Verdict: 55/45 mentor-leaning** (Agents Anonymous co-host; civic-tech credibility makes him speaker-mentor material; running a 6-person org). **If he competes, the gov/civic lane closes** — his read-side (transcribe/summarize) is done; he'd build the action-side (watchdog/audit agent) which is exactly our #2 direction. Check his badge before committing.

---

## 6. ZONE01 ATHENS — Abed's old house

- **Link:** Abed was Bocal/pedagogy-ops staff there Jan–Dec 2024 (01-Edu/School42 model, Nea Ionia). Zone01 hosts hackathons (Open Hackathon 2026 ran ON their campus). Expect organizers to seed Zone01 students — and judges to have a soft spot for them (Abed's narrative = bootcamp-to-SF).
- **Squads to watch:**
  - **Siraj team** — {Re}solve Hackathon 2025 3rd: **Ioannis Michalopoulos** (was Head of Technology @ Zone01; now Cyber Analyst @ Obrela — escape-room-founder turned coder, elite pitch/presentation) + **Georgia Marouli** + **Andriana Stas** (Zone01 students). Blockchain+AI microfinance trust stamp.
  - **Team Cloud9** — Open Hackathon 2026 (Sep, at Zone01) **1st + Most Evolved Idea**: Panagiotis Tsotros, Ioannis Velachoutakos, Thodoris Tolis, Nikoleta Akrivou — AHEAD: offline CV+motion-tracking → 3D spatial audio for the visually impaired. Hardware-adjacent, offline-first — rare profile.
- Zone01 LinkedIn posted the event 9 Oct. Threat level: pitch-strong, engineering mid — but AHEAD showed they can ship working systems under time pressure.

---

## 7. POST-NOV-1 SIGNAL SWEEP (LinkedIn/X)

- **Karypis** "Will I see you at Gen AI Summit Hackathon?" — 1 Nov, only confirmed intent post.
- **NOFire @ FOSSCOMM, 1 Nov:** Nanos/Sapranidis/Moustafellos/**Mavrikos** ran "Run A Coding Agent In A MicroVM With **brig**" — microVM sandboxing, egress policies, credential scoping, urunc/hull/hvi. Their agent-sandbox craft is hot and fresh, days before the event.
- **Enes Hoxha** published "AGI Will Need an Operating System" — **8 Nov** — Sophon 2.1 (30 Oct): model routing, local-first semantic memory, workspace-bound CLI coding agent w/ diff approvals + undo journal, DAG plan-recovery, durable human-approval gates. He's building the policy-gate pattern as a PRODUCT — likely host/networking not competitor, but his thesis = our craft axis; don't pitch him our architecture as novel.
- **X:** quiet as pass 1. **IG:** no hackathon-tagged posts; Leonardou stories unverifiable — assume she'll post.
- Formation channels: Agentic Athens mentor CTA, HackathonHub ambassadors, builders.zone calendar listing, on-site Sat 12:00.

---

## 8. STUDENT SQUADS — detail

- **NP-TRYHARDS (AUEB DET, 1st Challenge-Track AI Hackathon Greece Mar 2026):** Gerasimos + Simos Athanasiadis (AI Eng @ SPOKBEE, ex-Navy), Giannis Karyotakis (NTUA ML MSc, Educoach co-founder), Foivos Timotheos Proestakis, Evangelos Talos. **BillSense:** photo of PPC bill → citation-backed analysis, consumption comparisons, anomaly detection, savings recs — "enterprise-ready" doctrine, won PPC's own challenge among 32 teams/20 judges. Pre-formed 4–5, doc-agent muscle.
- **FlexGrid AI (NTUA, 1st Innovation Marathon Feb/Mar 2026):** Panagiotis Bampatsias (NTUA student), Georgios Tzamouranis, Nikolaos Katsaidonis (**Data & AI Eng @ D ONE**, MSc ECE NTUA — working eng, not just student). Agentic-pipeline EV-charging load mgmt: demand forecasting, real-time charging optimization, multi-point coordination. Energy-vertical specialists; won on concept — live-build execution unproven.
- **Crowdless five (1st Open-Track AUEB + 1st Greek Cassini '25):** Mariglena Reci, Stelios Rotas, Alexandros Gkiafis (@AlexTuring010, Android/Kotlin), Theodoros Exarchos (@EXARTeo), Panagiotis Thivaios. Serial unit — **recycled the same idea to two wins** (idea-recycling is legal here: boilerplate yes, prebuilt product DQ'd). Pitch/business-case carries them.
- **TTLabs** (2nd Challenge-Track): unified public-service issue reporting, GDPR-compliant case mgmt — civic-lane collision risk w/ Porios.
- **Matilda-Edu** (3rd Open-Track): no-code agent-builder platform — meta-fit for theme, members unknown.
- **GIGPOSSIBLE** (2nd Open-Track): voice-input job posting + photo-CV — voice lane dabblers.
- **UPatras:** no confirmed squad. Robotics Club UoP is hardware-focused; CEID produces ML eng but no named entrant found. Low signal.
- **OpenConf/OpenHackathon circuit names** (may register): Cloud9 (above), Voston Labs (HexProtect, {Re}solve 1st), Vitreous (Rettina eye-comms, 2nd).

---

## 9. RANKED THREAT BOARD — top 10

Scoring: (attendance probability × lethality vs our formula — real work live · SLM sub-job · policy gate + signed log · measured deltas · Greek wedge → global TAM · aura moment · Devin-built).

| # | Rival | P(in) | Build style | Likely vertical | Counter-positioning |
|---|---|---|---|---|---|
| 1 | **Artemis Leonardou** (+NOFire nucleus w/ Mavrikos) | High | Vibe-to-prod speed, real eng behind polish; agent-context/orchestration is her day job; native aura | Creator/content agent (Reelio lineage) or agent-orchestration demo | Can't out-present her — out-prove her. Judges who matter (Zindros/Gianitsos/Koukoumidis) reward verifiable runs: signed action log + live eval table beat stagecraft. If she demos content tooling, our "agent does real work on real systems" contrast is built-in |
| 2 | **Mavrikos (+Ioannidis Omnyo axis)** | Med-High | Deepest systems eng present: microVM sandboxing (brig/urunc), k8s, reproducible agent envs; FOSSCOMM workshop 1 Nov | Agent infra: sandbox/isolation/observability demo — could out-craft our policy gate | Infra-for-infra's-sake loses on usefulness + "people want". Anchor every infra claim to a visible end-user outcome. Our gate is a means to a story, theirs risks being the story |
| 3 | **Eleni Zafeiri** | High | Killer pitcher, consumer-grade polish, HackathonHub megaphone; mid eng | Consumer/student-facing agent, creator tooling (w/ Karypis+Michail nucleus) | Same counter as #1 — let her win the room, we win the scorecard. Craft judges + "make it work" mandate penalize vibe-only depth |
| 4 | **NP-TRYHARDS** | Med-High | Pre-formed unit, enterprise-doc muscle, citation-backed UX, "enterprise-ready" doctrine | Sponsor-brief doc/inbox agent (the CROWDED lane) | We're not in their lane. If a doc brief is forced: real cross-system execution (actual doc chase across live systems) vs their single-doc citation UX |
| 5 | **Odisseas Karypis** | **Confirmed** | 3x winner, elite narrative, vibe-tier eng — needs an eng partner to podium | Strategy/biz-agent w/ slick demo; whichever strong eng he recruits | His ceiling = partner's floor. Monitor who he squads with Sat 12:00; if he lands a systems partner, upgrade to #3. His demos historically demo-well-but-shallow — the live-failure Q&A is where he bleeds |
| 6 | **Christos Porios** | Med | Agent-native builder (his repo's top contributors are Claude/OpenHands/Cursor), gov-data pipelines, ex-Google/Palantir rigor | If competing: civic action-agent (diavgeia audits, council watchdog) — OUR #2 direction | Check his badge first. If he's builder-side: pivot to Prosperty doc-chase or voice lane — don't fight the diavgeia incumbent on his own data. If mentor-side: USE him — he knows every Greek gov API's sharp edges |
| 7 | **FlexGrid AI trio** | Med | Agentic pipeline, energy-domain depth (Katsaidonis = working data eng) | Energy/grid ops agent if an energy brief lands; else generic enterprise | Their win was concept-stage; mandate is "agent at work". If they go energy, niche overlap is minimal — ignore |
| 8 | **Ryan Zidago** | Med | Product-eng rigor, spec+evidence doctrine (Higherlevel), ex-Sona Raffy agent builder; Build Week HM | Dev-tool/eval-harness demo — spec/review agent | He sells evals; we SHOW evals (SLM-beats-frontier table, measured before/after). Solo-founder velocity vs our team's parallel build — out-ship him |
| 9 | **Triantafyllos "Rose" Samaras** | Med | 290-tool MCP platform founder, sales polish, Build Week 2nd (Hygeia health) | MCP-heavy agent — health/docs/AI-visibility | Tool-breadth demos fracture under "does it work end-to-end". Keep ours single-thread flawless; his strength (integrate everything) is the judge-mandate's weakness |
| 10 | **Hlöðver Sigurðsson** (hlolli) | Med-Low | Quiet deep eng — SRE, NixOS, working agentic-trading demo (OpenClaw+Codex) | Trading/crypto infra agent | If he builds trading: real-work mandate vs simulated P&L — judges want verifiable business action. If he pivots to infra, same counter as #2 |

**Next five:** Crowdless five (serial recycled-win unit — pitch-first); Anastasia Michail (Lovable city lead — fast consumer builds, pitch-strong, eng thin); Christos Ioannidis (if not absorbed into Mavrikos axis — enterprise-challenge proven); Team Cloud9/Siraj (Zone01 pitch squads — org-favorite halo); TTLabs (civic GDPR lane).

**Non-threats (confirmed other-side):** Tsolakidis + Kollaros + Tasos (Agentic Athens mentors — exploit freely); Papoulakos, Palaiokosta (org); Pantazis (hardware profile, odd fit); Hoxha (Sophon founder, hosting/networking); Vasilis Tsolis (OpenAI ambassador — MC energy, not a builder here).

---

## 10. STRUCTURAL READS

1. **Two Reelio nuclei ≈ two finalist slots** — the real fight is for the 3rd–5th final seats + challenge-partner awards.
2. **Mentor bench outclasses the field** — Callen-AI voice stack, Promptotype agent-UX, Porios gov-data, Zografos agent-economics are all mentor-side. Using mentors = asymmetric weapon; rivals who skip the tables lose an hour of free senior consulting.
3. **The eng-poor/pitch-rich cluster** (Karypis, Michail, partly Zafeiri) will shop for engineering partners Sat 12:00 — that's when threat #5 either dissolves or doubles. Watch pairings.
4. **Lane forecast:** doc/inbox agents = NP-TRYHARDS + sponsor-followers (crowded) · civic/gov = Porios or nobody · energy = FlexGrid only · voice = EMPTY (the one production voice builder is mentoring) · agent-infra/eval = Mavrikos/Zidago/Sigurðsson triangle · creator/content = Leonardou's home turf.
5. **Our edge remains the same:** verifiable real work + the eval/audit receipts the builder-judges invented. The field is heavy on narrative; the mandate is "make it work and show us the demo."

## GAPS / WATCH (pre-Sat)
- NOFire sponsor decision → flips Leonardou+Mavrikos to table-side (removes top-2 threats, adds best mentors).
- Porios badge. Agentic Athens #3 date (formation mixer if pre-14th).
- Luma guest-list rotation (names appear on approval); Leonardou/Zafeiri/Michail IG stories 12–14 Nov.
- hackathon.polymath42.com for /challenges or schedule posts; builders.zone for team listings.
- Unknown internationals flying in with Abed/Ion's SF network — un-Googleable ringers.
