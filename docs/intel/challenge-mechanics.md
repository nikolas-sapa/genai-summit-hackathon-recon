---
title: "challenge mechanics"
type: source
tags: [hackathon, genai-summit, recon, intel]
aliases: ["challenge mechanics"]
created: 2026-11-10
updated: 2026-11-10
status: active
---

# Challenge/Track Mechanics — Gen AI Summit Hackathon (Athens, 14–15 Nov 2026)

Recon date: from live sponsor deck + precedent events. Sources inline.

## 0. The actual mechanics (from the live sponsor deck)

Source: `hackathon.polymath42.com/deck?sponsor=cognition` (SSR HTML, captured Oct 2026). `/deck` bare 404s; `?sponsor=` param required.

**Package ladder:**
- **Title Sponsor — €15,000, exclusive, one only.** Naming ("presented by X"), 10-min opening keynote Sat evening, **2 judges on main prize panel**, "your own sponsored challenge, defined and judged by your team," mentor table, all opt-in CVs, first refusal 2027.
- **Challenge Partner — €5,000, max three, "one challenge each."** "Set a real problem for teams to build against. **You brief it, judge it and award it on the Summit stage.**" 5-min tech intro Sat evening, **1 judge on the main prize panel**, logo on stage backdrop, mentor table, opt-in CVs.
- **Technology Partner — compute & tools (in-kind).** Credits/licences for 100–120 builders, 5-min intro Sat evening, mentor table, usage report. **No challenge, no judge seat.**
- **Supporter — €2,000.** Logo + mentor table + post-event report only.

**Main prize pool: €8,500** — 1st €5,000 / 2nd €2,500 / 3rd €1,000, "plus partner awards" (builders.zone listing). Judged on **usefulness, craft, and "aura points"** — "not a pitching competition, it's an agent at work."

**Deck's example challenge briefs** (what sponsors are told a challenge looks like):
1. Inbox→resolution: agent triages support tickets, drafts replies, closes simple ones.
2. Invoice reconciliation: matches invoices to POs through partner API, flags exceptions.
3. Codebase caretaker: picks up open issues, ships fixes with tests, opens PR.
4. "Your brief": real roadmap problem shaped into weekend-sized challenge + "a fair rubric."

**Key structural read:** challenges are *additive sponsor prizes on top of* the main €8.5k podium — not separate tracks. A Challenge Partner literally gets a seat on the main panel, so challenge and main prize share judging DNA. Title sponsor = also a challenge partner (1 + 3 → **max 4 sponsored briefs**).

## 1. Precedent: LifeHack Athens @ Panathēnea (27–28 May 2026, SAME venue — Athens LifeTech Park, Spata; co-org Endeavor + Longevity Hacks + Panathēnea)

Sources: luma.com/rquttffe, athenslifetechpark.com recap, Longevity Hacks LinkedIn wrap.

- 36h, 80 spots advertised → **60 participants, 13 teams, 22 mentors** actual.
- **Three industry-sponsored tracks, teams picked one:**
  - Metabolic Diseases — **Pfizer CDI Thessaloniki** — AI on obesity/metabolic disease/therapeutic targets. Prize: **€3,000 cash**.
  - Drug Discovery & Development — **Athens LifeTech Park** — computational design → target ID → translational. Prize: **6 months free lab/office + mentoring + VC intros**.
  - AI in Metabolic Diseases / "Synapsis AI Docathon" — **Dyania Health** — ML on clinical problem + head-to-head vs their Synapsis AI answering questions on clinical notes. Prize: **iPad + 1-month paid internship per member**.
- **Each sponsor crowned its own winner. NO overall winner** — "Three thematic tracks, three winners." All three pitched at Athens Life Sciences Day (May 29).
- Winners: MetNav (Pfizer; labs+CGM+genome+microbiome risk tool), RNAgents (ALTP; agent generating/scoring siRNA+ASO candidates — now literally incubated at ALTP), Dyania Challengers (MASH detection from unstructured medical data).
- ~4–5 teams per track. Lovable + Microsoft for Startups were **tech partners** (credits only, no challenge) — same tier split as the Nov event's deck.
- **Pattern confirmed: sponsor = brief + own judging + own prize. Winner per brief. Tech partners arm the builders.**

## 2. Precedent: Florent × Panathēnea AI Hackathon (28 May 2026, Zone01 Athens)

Sources: Florent VP LinkedIn, panathenea.org, acg.edu recap, winner's site (ertval.github.io) + github.com/ertval/keel-multi-agent-pipeline.

- **12h, apply as team of two, 25 teams selected from 100+ applicants** — curated, not open.
- Jury: Thomas Dohmke (ex-GitHub CEO), Lars Rasmussen (Google Maps/Panathēnea co-founder), Mads Rydahl (Siri founding PM), Christian Dorffer (Florent).
- **Freeform — "build a real AI product," no theme, no sponsor challenges.** €25k+ prizes (ACG reports €50k incl. credits: Mac Minis, iPads, PS5s, AWS credits, cash). Top-3 pitched on Panathēnea main stage.
- **1st place: Keel** — maritime demurrage reconciliation: LLM reads charterparty/SoFs/claims into Pydantic schemas → pure-Python laytime/demurrage state machine → deterministic evaluator per disputed weather window → reconciled number + audit trail + settlement letter. LangGraph orchestrator-worker-validator.
- **Top-3: Portside** — also maritime: voyage docs → fully cited delay claims in <60s.
- **How they won:** narrow real industry workflow with ugly unstructured docs + deterministic core wrapped around LLM (verifiable number, audit trail — not a chat demo). Judged by product people; they picked defensible depth over breadth.

## 3. Precedent: GenAI Summit 4 hackathon (24 Nov 2025, SNFCC)

Sources: dept.aueb.gr, GenAI Summit LinkedIn.

- **6h (10:00–16:00), students only, teams ≤4.**
- **Single sponsor brief for ALL teams**: "a real business challenge designed by Piraeus." Lovable licences exclusive to event. Jury: Lovable, OpenAI, Piraeus, AUEB. One winning team, iPad each (Piraeus-funded).
- **Pattern: one challenge partner → one brief → everyone builds the same thing.**

## 4. Decoded mechanics for Nov 14–15

| Question | Answer |
|---|---|
| Pick one challenge or freeform? | Deck implies teams build *against* a sponsored challenge OR the open theme ("agents doing real work"). No published rule forcing a challenge; precedent (LifeHack, Zürich, HKUST, Berlin "enter exactly one") says **you target ONE brief**, freeform almost certainly allowed as default. |
| One project → multiple briefs? | Not formally barred, but each partner "briefs it, judges it, awards it" their own challenge with their own rubric. A multi-brief project is a multi-master project — dilutes both. Don't. |
| Win challenge AND main prize? | **Yes — designed to overlap.** Challenge prizes are "partner awards" on top of €8.5k podium; CP's judge sits on main panel → your challenge win gives you an advocate inside main judging. This is the exploit. |
| Track isolation (LifeHack-style)? | No — LifeHack had *only* track prizes, no overall. This event has a real main podium, so challenge picks are portfolio entries, not track lock-ins. |
| Timeline | Doors/build Sat 12:00 → partner 5-min tech intros Sat evening (briefs likely dropped at kickoff 12:00 AND/OR elaborated Sat evening) → submissions close Sun 18:00 → finalists 21:00 → 5-min pitches + awards on Summit stage Mon 16 Nov. |
| Numbers | ~120 builders, teams 1–5 → ~25–30 teams. Per brief (if 4): ~5–8 teams. LifeHack ran ~4.3/track. |

## 5. Prediction: brief count at Sat 12:00

- **Max possible: 4** (Title gets a challenge too — "your own sponsored challenge, defined and judged by your team" is explicit in the €15k tier).
- **Realistic: 3–4.** Deck is still circulating (Cognition/Devin + NOFire variants live Oct 12+); Title likely still open or late-closing. 13 partner logos on site but tiers undisclosed — most are Supporter/Tech tier (fal, Firecrawl, Oumi, boxd smell like Tech Partners = credits, no brief).
- **Base case: 3 sponsored briefs + open-theme freeform.** Briefs will be shaped "with us into a weekend-sized problem and a fair rubric" → expect back-office agent shapes (triage, reconcile, caretaker patterns from deck examples), not R&D moonshots.

## 6. How to win BOTH a challenge prize and the main prize

1. **Pick ONE brief at kickoff** — the one with (a) fewest likely competitors and (b) most demo-able "agent does real work end-to-end" loop. Back-office briefs (invoice, ticket triage) demo better than infra briefs.
2. **Build it to the sponsor's rubric AND the main criteria simultaneously.** They're nearly identical anyway: sponsor wants "real problem solved" (usefulness), main jury wants usefulness + craft + aura. A winning challenge entry IS a top-3 main-prize candidate by construction.
3. **Your advocate is on the panel.** The Challenge Partner whose brief you aced has 1 vote and outsized voice on the main panel — they watched you solve *their* problem all weekend at the mentor table. Use their office hours; a sponsor who feels you built their roadmap will argue for you in the room.
4. **Keel pattern for craft/aura:** LLM parses messy real docs → typed schemas → deterministic core computes the thing → verifiable output + audit trail. Judges (product people + sponsor ops people) reward "it actually works and I can check the number," not agent-in-a-loop demos.
5. **Demo the loop live.** "Not a pitching competition, it's an agent at work" — show the agent take a goal and finish a job on stage, end-to-end. One crisp scenario, real artifacts (email sent, PR opened, invoice reconciled).
6. **Scope to Sunday 18:00, not Monday.** Submissions close before finalists are named — a finished boring thing beats an ambitious half-thing.
7. **Skip multi-brief hedging.** Entering two challenges with one project halves your rubric fit on both. Single-master execution.
8. **Hedge differently:** pick the brief whose sponsor you'd also want as an employer/customer — CPs get opt-in CVs; winning their challenge is the interview.
