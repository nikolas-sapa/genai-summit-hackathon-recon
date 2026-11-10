---
title: "pitch craft"
type: source
tags: [hackathon, genai-summit, recon, intel]
aliases: ["pitch craft"]
created: 2026-11-10
updated: 2026-11-10
status: active
---

# Pitch Craft — Gen AI Summit Hackathon Finals Blueprint
**Compiled 10 Nov 2026 (deep2) · Scope: Sunday 18:00→21:00 internal judging gate + Monday 5-min SNFCC stage pitch**
**Load-bearing sources:** MASTER-BRIEF, rules-deck, org-panathenea, athens-meta, mentor-table, keel/docs/demo_workflow.md (the winning May'26 demo script), MLH judging guide, HackTribe 5-min structure, JetBrains judging notes, SIH winner retrospective, summit FAQ, PM office transcript.

---

## 0. THE TWO-GATE FRAME — read first

You are pitching twice, to different rooms, in different formats:

| Gate | When | Room | Format | What decides it |
|---|---|---|---|---|
| **GATE 1 — Sunday internal** | Sun 18:00 submissions → 21:00 finalists | ALTP venue, Spata | Science-fair table judging (most likely — see §1) OR rapid internal demos. Submission package (name/desc/screenshots/demo/video — these exact fields are enumerated in the Terms IP clause) is judge-pre-read | Working agent at the table, judge Q&A, mentor advocacy. **This is where the hostile questions live.** |
| **GATE 2 — Monday stage** | Mon 16 Nov, on the Summit main stage | SNFCC, ~5,000 attendees, speaker list, press | 5-min pitch, winners announced on stage | Crowd-moving live demo + one remembered sentence. Q&A on stage not published — prep anyway (Panathēnea competition format runs pitch+jury interaction). |

**Strategic consequence:** Sunday is won at a TABLE by builders; Monday is won at 20 meters by a crowd. Build two artifacts: a repeatable 3-4 min *table loop* and a 5-min *stage arc*. Do not confuse them — a stage pitch read at a table feels evasive; a table demo read at a stage feels small.

**The mandate one more time:** "make it work and show us the demo. This is not a pitching competition, it's an agent at work." Every structural choice below serves that sentence.

---

## 1. SUNDAY 18:00→21:00 — THE GATE THAT MATTERS MOST

### 1.1 Mechanics (inferred, high confidence)

- **Published:** submissions close 18:00 Sun; finalists announced 21:00. Endeavor deck: "after demos: closing dinner" → demos happen inside that window.
- **Team math:** ~100-120 builders / teams 1-5 → **~25-30 teams**. 3h window.
- **Two viable formats:** (a) science-fair table visits — MLH-recommended standard, ~4 min/judge visit, each team seen by ~3 judges, parallel; LifeHack (same venue, same co-organizers) used roaming judge/mentor evaluation. (b) Sequenced 4-5 min internal demos — 30 × 5min + transitions ≈ 3h, also fits.
- **Either way, same optimization:** the submission package is a first-pass filter, the live table/room demo is the decider, deliberation is comparative (projects that "stick out to everyone" win per judging-literature).
- **Submission fields (from Terms):** project name, description, screenshots, demo, video + team names. This IS the pre-read judges skim at 18:00 while walking to your table.

### 1.2 Submission package — the silent judge (due discipline)

| Artifact | Spec | Tactic |
|---|---|---|
| Name | one word, Greek-flavored or work-flavored | Judges must repeat it verbatim in deliberation. "Keel" beat "AI Demurrage Platform 3000". |
| One-line description | the anchor sentence | Keel's: "The shipowner claims $187,000. Keel reconciles it to $112,000 — and shows the clause and timestamp for every dollar." Persona + number + proof in one breath. |
| Screenshots | 3-4, big text, real data | The artifact output, the action log/tool-call feed, the human-approval gate. No mockups — screenshot the real run. |
| Video | 60-90s, standalone | Record ~16:00-17:00 of a perfect run. Doubles as Monday backup. Upload early — fal/ffmpeg queues spike Sunday evening (sponsor-fal.md warned). |
| Repo/build provenance | git log + Devin session link | Zindros: "proof is checked, not trusted." Machine-checkable build-in-window evidence disarms the pre-built DQ risk AND the "did you build this today" question. |

### 1.3 Sunday timeline — protect the demo

| Time | Do |
|---|---|
| ~14:00 | Feature freeze decision point. SIH rule holds: nothing new starts that isn't already working. |
| 15:00-17:00 | Record video, shoot screenshots, write submission copy, rehearse table loop 3×, nap/food rotation. |
| **17:00-17:30** | **SUBMIT. Not 17:59.** Form fields + upload always fight you at the deadline. |
| 17:30-18:00 | Reset demo state, restart run, stage the table (screens open, seeded data, restart button tested). |
| 18:00-21:00 | Table-mode: repeatable loop, all members present-ish (rotate rest in pairs — judges notice a dead team; Pantazi audits team dynamics). |

### 1.4 The table loop — 3-4 min, repeatable 10-20×

Science-fair visits are ~4 minutes including the judge's walk. Your loop must tolerate being entered at ANY second:

1. **Continuous-run trick:** keep the agent cycling on a queue of tasks (ticket inbox, doc batch, tender list). Whatever second a judge arrives, the agent is visibly mid-work — tool calls scrolling, artifacts landing. "It's working right now" beats "let me start it for you."
2. **The 20-second re-entry:** any member can catch a judge with the anchor sentence + "watch, it's on step 6 of 9." The presenter doesn't need to be free.
3. **Give the judge a trigger:** three scenario cards at the table — "pick one and watch it run." Judges who touch it themselves believe it (SIH: "they clicked around themselves"). Risk-managed: scenarios are pre-seeded, execution is live.
4. **The approval-gate moment:** if your agent has a human-in-the-loop step, let THE JUDGE press approve. That is the single highest-trust interaction available — they feel the control plane.
5. **Callback close:** "it's on step 7 — come back in 90 seconds and watch it file the doc" converts a short visit into a return visit. Judges re-visit favorites during deliberation.
6. **Artifacts on the table:** the action log on a second screen (signed receipts = Zindros), a live cost counter (treg receipts = usage-report sponsors), printed QR → project profile.
7. **Role signals at the table:** lead speaks problem+impact; engineer answers "how"; whoever owns the domain names the workflow. Every member talks to at least one judge — talent auditors (Pantazi, de Grey, Bouloutas) are checking whether the team is real.
8. **Mentor advocates:** "the mentor who watched your agent recover a real error at 3pm is your best advocate at 6pm" (mentor-table.md). At ~17:00, do a 2-min show-and-tell for your 2-3 warmest mentors — they sit IN the judging room or brief it.
9. **Honesty posture (the Abed play):** state what's seeded vs live before being asked — "the accounts are real, the scenario data is seeded, the execution you're watching is live." Keel narrated its own empty states and won. Microcopy = "anti-slop certificate."
10. **Watch for judge-list traffic:** sponsor judges come to the table whose brief you took. Have their brief's rubric taped to the monitor edge. Challenge Partner who feels you built their roadmap argues for you inside the room.

---

## 2. THE MONDAY 5-MINUTE BLUEPRINT — "parallel spine" structure

Earlier recon: 60s problem / 3m demo / 60s proof. **Refinement: the demo isn't a segment, it's the spine.** Agent runs are slower than pitch segments — start the run in the first 20 seconds and narrate the story OVER the working agent. The run finishing IS your climax.

### Timing marks (5:00 total, rehearse to 4:45)

| Mark | Beat | Script shape |
|---|---|---|
| **0:00-0:20** | **Cold open + trigger.** Screen already up. "Four minutes ago, backstage, I gave [name] a job. Watch the right side of the screen — it's working right now." Goal typed live or run pre-triggered at stage-left. | The agent visible mid-run from second one = "agents at work" made literal. Alternative opens in §3. |
| **0:20-1:10** | **Persona + problem (one person, one job, one number).** "Meet [persona]. Every [week] they spend [N hours] doing [tedious multi-step job]. It costs [€/hours/errors]. While I tell you this, the agent is on step 3." | Athens meta: named real person beats tech-first (Open Hackathon jury verbatim: "started from one real person, not a technology looking for a use"). Greek-vertical persona = local resonance + global framing later. |
| **1:10-1:30** | **Solution one-liner + build provenance.** "[Name] is an agent that does [job] end-to-end. We built it in the last 30 hours — on a harness we brought as boilerplate, and we'll tell you exactly which part is which." | Declaring boilerplate unprompted = pre-empts the DQ-shaped question AND is the honesty move this jury rewards. |
| **1:30-3:30** | **Live run = the spine.** Camera stays on product. Narrate the user journey, never the UI ("a developer pushes a commit — Sentinel is already scanning" not "I'm clicking here"). At the approval gate: "it's asking a human before it sends — watch." If a step stalls: it's the designed beat — "that retry you just saw is the point." | Judges watching tool calls scroll = the craft criterion scored live. Mazarakis wants failure-handling live; Petropoulos (8× winner) knows exactly what real looks like. |
| **3:30-4:00** | **The artifact + THE number.** It lands. "Done. [N tickets closed / the reconciled figure / the filed doc] — that took [90 seconds]. A person does it in [42 minutes]." | Keel's money shot: one number, traceable, no adjectives. |
| **4:00-4:35** | **Proof stack, 3 items max, all real:** (a) "it's done this [37] times since Saturday — [N] succeeded, [N] needed a human, here's the eval" (b) cost per run from actual receipts ("$0.03/task") (c) the craft line — policy gate / signed action log / SLM-beats-frontier table. | Pick the 3 that match YOUR build. Gianitsos kills LLM-judged vibes; Pittarokoili kills unverifiable claims; Koukoumidis wants the SLM line if you have it. |
| **4:35-4:50** | **Continuation.** "After Sunday it becomes [X] — [the wedge → global TAM one-liner]." | Panathēnea prizes are continuation fuel (RNAgents went hackathon→lab); Apostolakis needs the Greece-wedge→global frame. |
| **4:50-5:00** | **Callback close.** "Agents out of the demo, into the job. Ours did [N] real jobs since Saturday. We're [team]." | Theme verbatim echo = the headline Niko Efstathiou (WIRED Greece) could write. |

**Rehearsal discipline:** script memorized not improvised (SIH); rehearse against a 4:45 clock; the run must land inside a 2.5-min live window — if your agent's reliable runtime exceeds it, pre-trigger at walk-on (statement above assumes that) or shorten the scenario.

---

## 3. DEMO CHOREOGRAPHY

### 3.1 Cold-open menu (pick one, rehearse all)

| Option | Aura | Risk | When to use |
|---|---|---|---|
| **A. Mid-run open** (recommended) — run triggered at walk-on, agent visibly on step 2-3 as you speak | High — literal "agent at work" | Low — you control timing; run fits window because it started early | Default. Your run is probably 60-180s; pitch narrative covers the wait. |
| **B. Anchor-sentence open** (Keel) — "$187,000 claimed. It reconciles to $112,000." Numbers first, then trigger | Medium-high | Low | If the run is short (<60s) or the number is your best asset. |
| **C. Audience-triggered** — judge/crowd picks scenario live | Very high | High — uncontrolled input on stage | Only if scenario picker is a constrained menu (3 seeded options), never free input. Strong for Sunday table, risky for Monday stage. |
| **D. Live voice/phone call on stage** | Maximum | Maximum — audio, latency, recognition all live | Only if voice agent is the project AND you have a fallback video of the identical call. Never attempt without 10+ clean rehearsals. |

### 3.2 Screen layout

- **Split view:** agent work surface (browser/app/liveView) dominant-left + **action feed right** — tool calls, decisions, cost counter ticking. Judges should be able to SEE it working, not be told it works. Firecrawl /interact liveView or your run-log panel both work.
- **No slide deck until the proof beat** — if you use slides at all: hook line → (demo live) → proof numbers → close. The mandate punishes slideware; Panathēnea's design bar means any slide that exists must be beautiful or absent.
- **Microcopy as craft:** the run log's status strings are visible on a cinema-size screen — write them like the anti-slop certificate they are (Abed). "Retrying: gateway returned 502, falling back to cached PO" is a better line than anything you'll say aloud.
- **Phone mirroring if mobile:** test the venue's AV path during Monday soundcheck; bring the adapter chain.

### 3.3 Narration rules while the agent works

1. Narrate the **journey**, not the UI — the coderslingo rule: "A developer pushes a commit. Sentinel triggers, finds the key on line 47, blocks the push, alerts in the PR." Never "okay so here's the dashboard."
2. **Use agent wait-time for proof, not filler** — during a slow step, deliver the before/after number or the eval line. Dead air is the only unforgivable thing.
3. **No narrating over a spinner** — if there's nothing to show, explain the graph/architecture for 8 seconds, then check back (keel correction #11).
4. **Say the measured number, not the round number** — "about a second," not "90 seconds" (keel pre-flight: measure the run you'll claim).
5. **Name honesty beats unprompted** — the keel script's best 30 seconds was an honest empty state. "This panel says it can't load the source PDF rather than blaming a document server" — narrate your equivalent.

### 3.4 Failure playbook — rehearsed, not improvised

The demo-failure literature and this jury agree: **calm narration of a failure is a craft signal; silence is panic.** Mazarakis literally scores failure-handling live. Recovery drill:

1. **Narrate, don't go silent (0-10s):** "that just dropped — this is the failure case we designed for, watch the log." If the agent itself visibly recovers (retry/fallback), that's your BEST beat — the mandate asks for recovery.
2. **Switch to backup (<30s):** recorded run of the identical scenario on 2 devices + USB, OR seeded/offline mode, OR second laptop pre-staged. State it plainly: "let me show you the recorded run while this reconnects." Never blame wifi, never "demo gods."
3. **Diagnose aloud ≤60s** only if trivially fixable; else stay on backup — judges have a schedule.
4. **Convert:** "the recording shows the same run you'll find in the action log — here, it succeeded at step 8."

Backup stack (build Sunday, verify Monday soundcheck): video of perfect run (2 devices + USB + phone) · offline/seeded mode (WiFi off test) · boxd snapshot of the warm VM state · phone hotspot tested at SNFCC · spare laptop staged + mirrored · printed screenshots of the money shot · restart-run button (resets seeded state <30s). **Freeze the demo build after Sunday** — VM snapshot; no updates, no "one last feature."

---

## 4. STAGECRAFT FOR THE SNFCC ROOM

- **Language: English.** Official FAQ: "the GenAI Summit is conducted entirely in English." Mitsotakis's G4 fireside (with Mistral's Mensch, moderated by judge Nikos Efstathiou) ran in English. **Do NOT pitch in Greek.** Optional grace note: a single Greek word/phrase or a Greek-named persona ("a clerk we'll call Giorgos") lands local warmth without breaking flow — worth one line, not a paragraph.
- **The PM factor:** Mitsotakis closes the summit with a fireside (G4 precedent). Whether he sees the hackathon segment depends on scheduling — pitch as if he might walk in mid-demo: the segment must read to a head-of-state AND an infra engineer simultaneously. That means: legible one-sentence problem, visible real work, zero jargon-only jokes.
- **Press:** Kathimerini is main media partner; Efstathiou (WIRED Greece EIC) is literally on the org team; pitch clips will circulate (finalists' stage = "most-recorded surface"). Write the close so it can be quoted: "agents out of the demo, into the job."
- **Crowd physics:** 5,000 people. Gig Possible won Panathēnea partly by MOVING the room — a human stake (the worker's dignity, the clerk's Friday afternoon) inside the problem beat. Panathēnea's own jury rewarded emotion + traction. Your persona beat carries this load.
- **Stage presence:** Panathēnea's bar is broadcast-level (Olympics lighting designer, TV producer on the mentor bench). Stand where the screen doesn't eat you; the screen is the star — face the audience, narrate off the monitor edge, never read the screen with your back turned >3s.

---

## 5. Q&A PLAYBOOK — the hostile set, scripted honest

Assume Q&A happens at Sunday tables (certain) and possibly on stage (unpublished). Rule: **every answer ≤20s, honest, and ends on a strength.** Candor is itself a scored signal (de Grey, Pantazi, Zindros, Abed all reward it; the keel team's radical-honesty script is the local proof).

| Hostile question | Who'll ask | Scripted answer shape |
|---|---|---|
| **"Isn't this just a wrapper around an LLM?"** | Koukoumidis, Zeibekis, every infra judge | "The model fills a typed schema — it never produces the decision. The [reconciliation/routing/verdict] is deterministic code you can check, and the [router/verifier] is a fine-tuned [Oumi] SLM that beat [frontier model] on this task by [N] points." (If no SLM: "the LLM does extraction; code decides. Nothing the model writes reaches the output unverified.") |
| **"Why an agent and not a script / plain RPA?"** | VCs, practitioners | Point at ONE moment: "at step [X] it hit [unexpected input] — it planned around it. A script dies there. That's the whole argument." If you can't name such a moment by Saturday night, you built a script — find one. |
| **"What's the moat?"** | Kalliagkopoulos, Apostolakis | Don't fake one: "In 36 hours there's no moat, there's a wedge: [the workflow schema / the eval set / the sponsor's own API integration]. The moat claim would be [data flywheel from every run / domain eval suite nobody else has]." Naming the future moat honestly > pretending it exists. |
| **"Did you build this today?"** (the DQ trap) | Anyone; Abed bores of pre-built | "The harness — orchestrator, tool layer, eval loop — is boilerplate we brought, and it's declared in the submission. Everything you just saw — the [vertical], the workflows, the integrations — ran in-window; the git log and the Devin session history are linked in the profile." Preempt in the pitch (beat 1:10-1:30) and the question dies. |
| **"What does it cost per run?"** | Gianitsos, Kopsinis-type mentors, Wonderful rep | Real receipts: "[$0.03] per task — [X] model calls at [rate], [Y] tool calls on treg — the log carries the receipts." If you don't know the number by Sunday, you don't have craft. |
| **"What about hallucinations?"** | Pittarokoili, Zindros, Lioupi-types | "Outputs cite [source lines/clauses]. The verifier checks [them]; the eval set of [N] cases runs [pass rate]%. Where it can't verify, it escalates to a human — that gate is what you saw at step [X]." |
| **"What happens when it fails?"** | Mazarakis, enterprise reps | "Two honest answers: the run retries/falls back [you saw it at step X], and [N] of our [37] overnight runs still needed a human — the log says which and why." Stating your failure rate first is the Gianitsos/Zindros cheat code. |
| **"Who's the customer? Is this Greece-only?"** | Apostolakis | "[Greek wedge] because the pain is densest here and the data exists; the same job exists in [every market with X]. Greece is the proof, not the ceiling." |
| **"What did each of you build?"** | Pantazi, de Grey, Bouloutas | Crisp one-liners per member — role split must be real and audible. Then shut up; team-Q&A hogging by the presenter reads as a one-person team. |
| **"Why does this matter in 10 years?"** | Bouloutas-type | "'I lived this problem' + the arc" — one sentence on who you are to this problem + where the category goes. |
| **"Show me the code / is it real?"** | Zeibekis, Zindros | Walk them into the action log and the signed receipts, or open the repo at the table. "Proof is checked, not trusted" — offer the check. |
| **"What's the worst thing about it?"** | de Grey (welcomes the grilling), Abed | Name a REAL limitation and what you'd build next (keel: "the human sign-off screen doesn't exist yet — it's the first thing I'd build"). Never say "time." |

**Q&A mechanics:** lead presenter answers strategy/domain; architecture questions get handed to the engineer explicitly ("Kostas built that — 15 seconds, Kostas"). Hand-off = team signal + brevity. Never argue; if a judge's premise is wrong, concede the framing, correct the fact.

---

## 6. TEAM PRESENCE

- **One voice, one driver.** Convergent advice across every winner retrospective: 1 presenter + 1 person driving the machine — NEVER the same person. On SNFCC stage: presenter holds the room; driver sits stage-side at the laptop, hands visible on camera if possible.
- **Why not two presenters on stage:** mic passes cost ~15s and break momentum; the second presenter's function (credibility) is better served by the driver being visibly real + both answering in Q&A.
- **Roles signaled, not stated:** presenter = owns the story; driver = owns the machine; at tables/Q&A the third-fifth members each own a domain answer. Pantazi is auditing "crisp role split, candor, coachability" — the team IS a scored artifact.
- **Rest math:** Sunday 18:00-21:00 is 3 hours of table visits on ~30h of sleep. Rotate: 2 on-table, rest on-break, swap every ~40 min. A team that looks dead loses the talent judges' vote silently.
- **Solo pitcher note:** if pitching alone, the driver-role doubles as your credibility prop — narrate your own hands briefly ("I typed the goal before I walked out"), then let the screen carry it.

---

## 7. CHECKLISTS

### Pre-stage Monday (adapted from keel pre-flight — the winning team's actual list)
- [ ] Fresh boot of demo machine; ONLY needed apps open; notifications off; bookmarks bar hidden
- [ ] Exact URLs — mind `localhost` vs `127.0.0.1` CORS traps; warmed routes (first-request compile stalls show on cinema screens)
- [ ] DB/state reset and re-seeded; demo voyage/queue confirmed present (`curl` the endpoint, don't eyeball it)
- [ ] Warm run completed once; measure the runtime — say that number
- [ ] Video backup on 2 devices + USB; offline mode tested with WiFi actually off; hotspot tested at SNFCC
- [ ] boxd snapshot of warm state; spare laptop staged and mirrored
- [ ] Restart-run button resets demo state <30s
- [ ] Soundcheck: screen split legible from 20m, font bumps, clicker/shortcuts work
- [ ] Script rehearsed to 4:45 against a clock, ≥10 full runs since Sunday

### Sunday table readiness (by 17:30)
- [ ] Submission submitted: name/one-liner/4 screenshots/90s video/repo link
- [ ] Agent cycling continuously on task queue; restart+seed <30s
- [ ] 3 scenario cards printed for judge-triggered runs
- [ ] Action log / receipts / cost counter on second screen
- [ ] QR to profile + git log + Devin session visible at table
- [ ] Challenge-brief rubric taped to monitor edge
- [ ] Mentor advocate list (2-3 names) — shown the working thing at ~17:00
- [ ] Water, food, rest rotation roster

---

## 8. WHAT THE WINNERS DID — compressed precedents

- **Keel (Panathēnea×Florent 1st, May'26 — the infra-jury crown):** anchor sentence with numbers in first 10s; narrate limitations louder than features ("Delivery is not available — the most honest thing on the screen"); deterministic core framed as "the dollars never come from the model"; say measured numbers; contingency table for every failure.
- **Gig Possible (Panathēnea Startup Competition 1st, 2026):** human-stake emotion + hard traction (53k users, zero ad spend) — "moved both the crowd and the jury."
- **LifeHack winners (same venue, same co-org):** sponsor-track fluency, working systems on regulated data, quantified clinical outcomes.
- **AGI House pattern:** agent does real work on real systems live + one-sentence-legible problem + measurable artifact.
- **Universal 5-min skeleton (HackTribe/JetBrains/SIH convergent):** hook→problem 30-60s · solution 30s · demo 60-90s (ours: 150s, it's the spine) · evidence · what-you-built · close. And the universal failure: feature tour, narrated clicks, no problem clarity, demo stuffed in the last 60 seconds.
