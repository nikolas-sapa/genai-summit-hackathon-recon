---
title: "strategy"
type: source
tags: [hackathon, genai-summit, recon, intel]
aliases: ["strategy"]
created: 2026-11-10
updated: 2026-11-10
status: active
---

# Gen AI Summit Hackathon — Competitive Recon & Battle Plan
Recon date: 10 Nov 2026 · Event: 14–15 Nov 2026, Athens LifeTech Park (Spata) · Finals: 16 Nov, GenAI Summit 5 main stage, SNFCC

---

## 1. CONFIRMED INTEL (primary sources)

### Mechanics (site + terms + sponsor deck + LinkedIn announcement)
- **Prize pool: €8,500 cash** — 1st €5,000 / 2nd €2,500 / 3rd €1,000 (confirmed on official GenAI Summit LinkedIn post, 2 Oct 2026). PLUS extra challenge prizes set by up to 3 Challenge Partners + Title Sponsor.
- **Judging: usefulness, craft, "aura points"** — judges' decisions final.
- **Timeline:** Doors + build start Sat 14 Nov 12:00 noon → submissions close Sun 18:00 → finalists announced ~21:00 Sun → **5-minute pitches** on Summit main stage Mon 16 Nov, winners announced in front of 5,000-attendee conference.
- Teams 1–5 (LinkedIn says "2–5, solo welcome"). 18+. Free. Food included. You own your IP; they get promo rights.
- Build must start at 12:00 Sat — "substantially pre-built → disqualification." Ideas, tooling, **boilerplate explicitly allowed beforehand**. This is the loophole: build reusable agent harness plumbing in advance, not the project.
- **Challenges announced AT the event** — Challenge Partners "brief it, judge it, award it on the Summit stage." Example briefs in the deck: (1) support inbox→resolution, (2) invoice→PO reconciliation + exception flagging, (3) codebase caretaker (issue→fix→tests→PR), (4) partner's own roadmap problem.
- **Judging panel structure (from deck):** Title Sponsor gets 2 judges on main panel + own challenge; each Challenge Partner (max 3) gets 1 judge + own challenge. Mentors drawn from Summit speaker list. Assume jury ≈ organizers + Wonderful (or whoever took Title) + 2–3 sponsor reps + Summit speakers.
- Terms mention a **participant profile/portfolio system** ("everyone who applies gets a profile… engineering portfolio") — not live publicly yet (all probed routes 404). Means participants' work is showcased; also means opt-in CVs go to Title/Challenge sponsors → recruiting is a sponsor motive.
- Event shows **162 registered / FULL, waitlist open** (Luma). Luma lists Standard + Mentor ticket types, both approval-gated.
- Hidden pages: only /, /index.md, /terms, /privacy, /llms.txt, /deck exist. /prizes /judges /faq /rules /schedule /challenges /winners = all 404. /deck is the prize source of truth.
- /deck has targeted variants ?sponsor=cognition and ?sponsor=nofire → they are courting Cognition (Devin) as sponsor. Unconfirmed as partner.

### Sponsors decoded (all confirmed partners + what they sell → their likely challenge interests)
| Partner | What it is | Angle for us |
|---|---|---|
| **Wonderful** (wonderful.ai) | Israeli-Dutch enterprise "agentic OS," $5B val, $550M Series C Sep'26, 650 staff, explicitly expanding in Greece | Probable Title Sponsor. Enterprise agent deployments; wants Greek eng talent. Build on/show enterprise workflow. |
| **Prosperty** (theprosperty.com) | #1 Greek proptech, Eurobank-backed Series A, Endeavor company, 800k visits/mo, auctions + mortgages + "AI redesign" | Likely Challenge Partner. Doc-heavy workflows: listings ingestion, title/permit verification, auction monitoring, lead triage. |
| **Crowdcruit** | Greek skills-first tech-hiring SaaS (AI scoring, expert interviews) | Challenge: candidate screening/interview/reporting agent. They receive participant CVs — hiring motive. |
| **Wiserwork** | AI meeting agent → deliverables; **product of 100mentors (co-host)** | Inner-circle sponsor. Meeting→action/deliverable workflows. |
| **100mentors** | Greek GenAI-adoption company — **produces GenAI Summit itself** | Co-organizer. Judges likely include their people. |
| **Panathēnea** | Athens' flagship tech/startup festival (10k+, Zappeion; speakers: ElevenLabs, Deel, Sequoia, OpenAI EMEA) | Co-organizer → high-caliber network, judges likely investor-grade. |
| **Polymath Labs / Abed Hamami** (polymath42.com) | Abed's product-studio; ex-Zone01 Athens ops, co-founded intechgration bootcamp, ex-Social Hackers Academy | Organizer/judge. Values: product craft, shipped end-to-end, education/community. |
| **Big Pi Ventures** | Greek deep-tech VC (Alex Eleftheriadis = Summit speaker) | Investor judge likely; fundable-startup framing scores. |
| **fal.ai** | Generative media inference (image/video models) | Tool partner — use fal for any media-gen in project. |
| **Firecrawl** | Web→LLM-ready scraping for agents | Tool partner — use for web ingestion. |
| **Oumi** | Open-source model train/eval/deploy (Venrock-backed PBC) | Tool partner — open-model fine-tuning angle if needed. |
| **boxd.sh** | Persistent cloud VMs/sandboxes for coding agents (MCP, snapshot/restore) | Infra partner — run agent workers on it. |
| **treg.to** | "OpenRouter for tools" — one key → 4,100+ endpoints (enrichment, scraping, social, ads, media), MCP | Huge leverage: instant tool catalog for any agent. |
| **Quintessential** | Athens product agency, "Aletheia AI" arm (agentic automation); built Waiz for National Bank of Greece, PPC EV chargers | Local-enterprise perspective; bank/PPC domain hints. |
| **Endeavor Greece** | Global entrepreneur network (Prosperty is an Endeavor co.) | Ecosystem presence, judges likely. |
| **Always Online** | Greek digital/infra brand | Minor sponsor. |

## 2. PRIOR EDITIONS
- **GenAI Summit 3 (2024): no hackathon** — pure conference (speakers: PM Mitsotakis, Digital Governance Minister, Palantir, AWS, General Catalyst, Microsoft GC&M).
- **GenAI Summit 4 (Nov 2025): "Data meets GenAI"** — a *1-day, student-only* hackathon (10:00–16:00) at SNFCC with Piraeus Bank + Lovable + AUEB MSc Business Analytics. Teams ≤4, one business challenge set by Piraeus, judges from Lovable/OpenAI/Piraeus/AUEB. Prize: iPads. Vibe-coding format, nothing like 2026.
- **GenAI Summit 5 (2026): first real builder hackathon** — 36h, ~100 selected builders, independent organizer trio (Polymath Labs × Panathēnea × 100mentors). No incumbent meta. Everyone is guessing; the org team is builder-led and prizes are serious.
- Lesson from G4: sponsor-set challenge + sponsor jury. That pattern persists, now formalized via Challenge Partner slots.

## 3. WHAT WINS AGENT HACKATHONS (2025–26 global pattern)
Winners at AGI House events: **Deal Pilot** (1st, Web Agent Day Oct'25 — agent browses real stores, applies coupons, ranks by unit price; "not a single AI product does this"), **WatchDoc** (2nd — live alerts on changing critical docs), **Job Use** (3rd — one upload → mass job applications), **AutoRL** (1st, Anthropic partner event), **GTO Copilot** (2nd, AgentHacks — real-time voice poker advisor).
Pattern of winners:
1. **Agent does real work on real external systems live** — browser clicks, API writes, emails sent. Not a chat UI, not a mock.
2. **Legible problem in one sentence** — "finds the cheapest deal for anything," "applies to jobs for you." A judge repeats it verbatim.
3. **Measurable artifact at the end** — € saved, tickets closed, applications sent, PR opened. A number, not a narrative.
4. **Multi-step + proactive** — plan→tools→recovery from error→done. Organizers here literally say "deliver real work end-to-end, proactively."
5. **Demo-as-proof, not pitch** — "make it work and show us the demo. This is not a pitching competition, it's an agent at work" (Luma). Judges are builders; infra elegance (checkpointing, evals, guardrails) is "craft."
6. Sponsor-stack usage → automatic goodwill (treg tools, boxd sandboxes, fal media, Firecrawl, Oumi).

## 4. ATHENS ANGLE
Locally resonant for a Greek/SEE jury + Summit audience (banking, tourism, shipping, public sector, real estate = Greek economy):
- **Bureaucracy/documents:** Greek public-sector paperwork is a national pain; Summit has had the Digital Governance Minister on stage. gov.gr-adjacent agent = instant resonance.
- **Real estate:** Prosperty + Eurobank + Golden Visa/diaspora buyers. Transactions = 10+ docs, agents, notaries, municipalities. Peak "tedious multi-step."
- **Shipping/logistics:** Greece owns ~20% of world merchant fleet; crew certs, charter-party docs, port ops are paper-heavy. Impressive if demoable, but harder to fake live.
- **Tourism/hospitality:** bookings, guest comms, multi-language ops. Legible, live-demoable.
- **Banking ops:** Piraeus was G4's challenge-setter; Eurobank owns 25% of Prosperty; NBG is Quintessential's client. Back-office doc/triage agents land with this room.
- **Hiring:** Crowdcruit's entire business + sponsors literally receiving participant CVs.

## 5. BATTLE PLAN

### (a) Five concept directions, ranked by win probability

**#1 — "Hired Gun": challenge-adaptive agent harness (meta-strategy).**
Pre-build (allowed boilerplate): orchestrator + tool layer on treg/boxd + browser agent + eval/logging + human-escalation UI. On Sat, snap whichever announced Challenge brief onto it (inbox→resolution / invoice→PO / issue→PR all share 80% plumbing). Challenge prizes are separate from main pool — you can win a sponsor prize AND the main prize. Highest expected value because you hedge across 3 sponsor briefs + open category.

**#2 — "Symboylio / Property Paperwork Agent": end-to-end Greek real-estate transaction agent.**
Give it a listing → it pulls docs (title, building ID/e-ID, energy cert, tax clearance), cross-checks them, flags encumbrances, drafts the buyer dossier + lawyer checklist, chases missing items by email. Prosperty's business verbatim; Eurobank/diaspora narrative; visible doc-by-doc progress = great live demo. Wins usefulness + local resonance + probable sponsor alignment.

**#3 — "Ops Inbox Zero": enterprise ticket/email → resolved, for a Greek vertical.**
Agent works a real inbox (support@ or info@): triages, retrieves account data via tools, drafts+sends replies, escalates edge cases with reasoning, closes the loop. Maps to deck example #1 (likely an actual challenge), Wonderful's enterprise-Agent thesis, every bank/utility in the room. Demo: live counter of tickets closed while pitching.

**#4 — "Talent Machine": recruiting pipeline agent (Crowdcruit-adjacent).**
Job spec → sources candidates → screens CVs + repos → generates role-specific assessments → schedules interviews → writes structured eval reports. Crowdcruit's product as an agent; recruiters-in-the-room legible. Risk: reads as feature-of-sponsor rather than company.

**#5 — "Deal Pilot for Greece": browser agent that books/buys the best real option live.**
Travel (ferry+hotel+flight combo), or consumer purchase across Greek e-commerce — agent navigates real sites, compares total cost incl. fees, executes booking live on stage. Maximum aura (audience watches it click through a real checkout) but weakest usefulness/defensibility vs. #1–3 and echoes AGI House's known winner.

### (b) What the winning demo must show
- Goal spoken/typed live → agent plans visibly (step list on screen) → executes on **real external systems** (real sites, real APIs, real sent emails/docs) → one visible error recovery → finished artifact + **quantified outcome** ("14 invoices reconciled, 3 flagged, 42 min → 90 sec").
- Secondary screen/judge takeaway: run log + eval pass = "craft."
- Monday's 5-min stage format: 60 sec setup (who hurts, what the agent does), 3 min live run (pre-seeded but executing live), 60 sec outcome + "this ran overnight 37 times" proof. Backup video exists but is plan-B — live is the aura.
- Pre-stage: real accounts, realistic data, idempotent run, sandbox on boxd, warm caches. Kill risk of live failure = rehearse 10x; have "restart run" button.

### (c) Pitch framing per criterion
- **Usefulness:** name a real person/workflow ("every week, an ops person spends 6 hrs…"), state volume + time saved; tie to a sponsor domain where possible.
- **Craft:** one architecture glance + the boring-hard parts done: audit trail, tool permissions, human-in-loop escalation, eval set, error recovery. Builder-judges reward seeing the harness, not the slide.
- **Aura:** engineered live moment — the thing visibly completes on real infra during the pitch (email arrives on judge's phone, doc appears, ticket closes). Aura = "I can't believe it just did that," not polish.
- Overall framing: PG-quote the theme back — "agents out of the demo, into the job. Ours did [X real jobs] since Saturday."

### (d) Prize/rules intel
- €5k/€2.5k/€1k main + up to ~4 extra challenge prizes (Title + 3 Challenge Partners).
- Challenges announced at kickoff Sat; judge = sponsor who set it; award on Summit stage.
- No public schedule yet — llms.txt explicitly says don't quote one; Sat-evening sponsor tech talks confirmed (5-min each; Title gets 10-min keynote).
- Solo allowed; team forms Sat afternoon; every registration reviewed; event currently FULL → apply/waitlist now.
- IP stays with team; code must be substantially built in-window; credit non-built parts.

## 6. OPEN GAPS / ASSUMPTIONS
- Title Sponsor unnamed publicly → assume Wonderful (size, Greece expansion) but unconfirmed; briefs drop at kickoff anyway → strategy #1 hedges.
- Judge names unpublished → jury = organizers + sponsor reps + Summit speakers (G4 precedent).
- Participant profile system in Terms suggests public team/project pages coming — worth rechecking pre-event.
