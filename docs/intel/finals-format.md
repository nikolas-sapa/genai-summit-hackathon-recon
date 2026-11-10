---
title: "finals format"
type: source
tags: [hackathon, genai-summit, recon, intel]
aliases: ["finals format"]
created: 2026-11-10
updated: 2026-11-10
status: active
---

# FINALS FORMAT — Stagecraft Spec
## Gen AI Summit Hackathon finals · GenAI Summit 5 · SNFCC, Mon 16 Nov 2026

*Recon date: 10 Nov 2026. Primary source: the summit's own agenda data — the agenda page is JS-rendered off a published Google Sheet CSV (saved `deep2/agenda-2026.csv`). Agenda is marked "tentative, work in progress" — re-verify weekly. Secondary: snfcc.org venue docs, Luma/FAQ, sponsor deck verbatim (per `challenge-mechanics.md`), Panathēnea precedent files.*

---

## 0. BOTTOM LINE

- Your slot: **18:00–18:30, BOOK CASTLE stage** (NOT the 1,400-seat Central/SNH). "HACKATHON WINNERS · Presentation — Winning teams (Hackathon)" · session descriptor: **"Mini use cases"**. 30 min hard block.
- Room: **220-seat theater** inside the National Library lobby (Agora), glass-fronted → real audience = 220 seats + standing overflow + constant walk-by traffic. 10×4m projection screen, removable stage.
- Format: **5-min pitches** (master brief/deck) ≈ 4–5 winning teams + intro + award moment inside 30'. "Mini use cases" = demo-first, pitch-second.
- Judging: done **Sunday at LifeTech** (submissions 18:00, finalists 21:00). Monday stage = showcase + **awards on the Summit stage** (sponsor deck verbatim: "You brief it, judge it and award it on the Summit stage"). No published audience-vote mechanism.
- **Live demo: YES, feasible and on-brand.** The summit books "Demo" slots on every stage all day (Wonderful, Helvia, Epsilon, Asteri, Panoptic, Tools for Humanity, Google ×2 — including live-agent demos). 2024 edition was literally branded "Demo Days"; the Digital Minister did a live mAIgov demo on the main stage.
- After you: Prodyna 18:30–18:50 on your stage → then room closes, **"everyone to Central for the PM"** (security check 19:00–19:30, Mitsotakis fireside 19:30–20:15). You are the last content block before the PM wind-up — a high-exit-risk slot. **Your demo must hook in the first 60 seconds or the room drains.**

---

## 1. THE SLOT — exact position in the day (verified from agenda CSV)

| Time | Your stage (BOOK CASTLE) | Pulling audience away |
|---|---|---|
| 17:10–17:50 | — | CENTRAL: Shipping panel (Bain 17:50–18:30 follows) |
| 17:30–18:00 | 17:40–18:00 **TOOLS FOR HUMANITY Demo** (their PM + Sr SWE) | FAROS: Google Demos 17:30–18:00 (Gemini Agent "in Action" — live) |
| **18:00–18:30** | **HACKATHON WINNERS · Presentation · "Mini use cases"** | CENTRAL: Bain panel ends 18:30; then EY×Pierrakakis (Eurogroup President) 18:30–18:50 |
| 18:30–18:50 | Prodyna presentation | CENTRAL: Pierrakakis; FAROS closed 18:30 (party setup) |
| 19:00–19:30 | Room closed | **Security check** for PM — everyone to Central |
| 19:30–20:15 | — | **PRIME MINISTER Mitsotakis closing fireside** (w/ TII CEO Najwa Aaraj) |
| 21:00–23:30 | — | Party at Faros |

**Reads:**
1. **Back-to-back stage flip at 18:00** — Tools for Humanity's demo ends at 18:00; winners start at 18:00. Zero turnover buffer → be pre-staged, or you eat your own 30'.
2. **Competition at 18:00:** tail of the Bain panel (OpenAI's Elena Pittarokoili + Microsoft + Dialectica on stage) — a strong concurrent draw; then the PM-adjacent gravity begins (Pierrakakis at 18:30, security sweep 19:00). Expect a tired, thinning, partially migrating crowd — this is a "last slot before the headliner" problem. Winners get whoever chooses demos over politics.
3. **Pitch order:** not published. Slot labeled "HACKATHON WINNERS" ⇒ likely 3 podium teams + possibly challenge-partner winners ("partner awards"). Order likely set by organizers Sunday night, not random-drawn on stage. **Confirm with Abed.**
4. Award announcements happen on/near this stage moment (CPs "award it on the Summit stage" per deck) — possibly inside your 30' block or a short ceremony after. Budget that an emcee + award handoff eats 3–5 min of the block → effective pitch time ≈ 4–5 teams × ~5'.

---

## 2. THE ROOM — Book Castle physical/AV spec (snfcc.org + rentals PDF)

- **Location:** ground floor of the National Library of Greece (NLG) lobby (the Agora). A 20m×20m square tower, 18m tall, four balconies of book stacks above. **Glass façade onto the Agora** — visible to all passing traffic; enclosed by soundproof curtains for events.
- **Capacity:** Theater 220 · Classroom 112 · Banquet 136 · U-shape 53 · standing lobby overflow possible.
- **Screen: 10 × 4 m cinema projection screen** (2.5:1 face; assume a 16:9 image is projected inside it — verify at tech check). **Projection, not LED wall** → contrast matters: dark, saturated UI beats pale dashboards; thin grays die.
- **Stage:** removable stage; orange Scandinavian chairs; wood-paneled walls. Intimate room — you are CLOSE to the audience; eye contact and voice carry; a slick over-produced read feels wrong, builders-on-stage energy fits.
- **House AV:** projection system, hearing-assistance system. Book Castle is an NLG room (not GNO) — the "preferred production partner View Master" rule applies to SNH + Alternative Stage only; but Summit-wide production (Event Architect: **HÄST**) almost certainly runs one AV vendor across all stages.
- **Input chain:** unknown until confirmed. Standard for this room = presenter sends HDMI → production switcher → projector. Assume you get a table or podium + HDMI; **bring the laptop that runs the demo** but be ready to hand them a rendered file instead (see backup ladder §7).
- **Network:** SNFCC has public WiFi, but 5,000 attendees on shared venue WiFi is not a demo substrate. Production stages typically get a **dedicated wired/production network** — ASK. Regardless: bring your own failover (see §7).
- **Acoustics/atmosphere:** library atrium — soundproof curtains when closed; still, expect ambient conference noise bleed through the glass at standing-room. Audio of any in-demo sound (agent voice, notification pings, music) must go through house PA — confirm a 3.5mm/DI feed exists; otherwise design demo to work **silently**.

---

## 3. FORMAT MECHANICS — what "5-min pitch" means here

| Parameter | Status | Source |
|---|---|---|
| Pitch length | **5 min/team** | master brief + sponsor deck ("5-min pitches" lineage; LifeHack precedent) |
| # of teams on stage | ~3–6 ("winning teams"; podium 3 + partner awards) | agenda "HACKATHON WINNERS" + €8.5k podium + CP "partner awards" |
| Q&A on stage | **None published** — 30' ÷ 5-6 teams leaves ~0; assume no Q&A, possibly 1 emcee softball question | inference from block math |
| Presenters/team | Not published; stage + 5' ⇒ **1 presenter + optional 1 driver** | inference; Panathēnea/Slush norm |
| Timer enforcement | 20'-slot stage culture + hard 18:30 out (Prodyna next, PM sweep) ⇒ **hard timer; overruns get cut** | inference |
| Judging on stage? | **Finalists picked Sunday 21:00 at LifeTech.** Monday = winners present "mini use cases" + awards. Treat stage as **showcase with an award moment**, not a scored final — but design the pitch as if still scored (see §8 ambiguity flag) | hackathon FAQ + agenda label |
| Audience vote | **No mechanism published.** Panathēnea finals: jury decides; "moved the crowd" mattered informally (Gig Possible "moved both the crowd and the jury") | org-panathenea.md |
| Pitch order | Not random-published; set by organizers | confirm |

**Panathēnea stagecraft precedent (their co-host DNA):** Zappeion main-stage finals ran 6 finalists pitching to investors + live audience, jury deliberated, winner announced in an evening ceremony; prizes framed as fuel to continue the project. Expect the same polish bar: clean name/logo, a story arc, one emotional beat. Their TechOps lead (Konstantinos Martinis) runs volunteer+tech logistics — the person who can answer AV questions.

---

## 4. LIVE DEMO FEASIBILITY — verdict: GO, armored

**Evidence live demos are the house format:**
- Agenda 2026 is peppered with explicit "Demo"/"DEMO" slots on all four stages: Wonderful (Faros), Epsilon Net + Helvia + Asteri + Tools for Humanity (Book Castle — your exact room!), Panoptic (Faros), **Google ×2 live "Gemini Agent in Action"** (Faros), EntersoftOne, Databricks/Salesforce product presentations.
- Summit 4 (Nov 2025): UBITECH hands-on demo on **Stavros Niarchos Hall main stage** (14:40–15:00); Deloitte AskNexus session = product walkthrough (video on YouTube).
- 2024 edition branded "**Demo Days**": Digital Minister Papastergiou + UBITECH ran a **live mAIgov product demo** on stage — the riskiest possible demo (government prod system) and they did it live.
- The mandate: *"make it work and show us the demo. This is not a pitching competition, it's an agent at work."* A video of the agent would read as a cop-out to this jury and this organizer.
- **Tools for Humanity demos at 17:40–18:00 on your exact stage → your free tech rehearsal.** Arrive 17:15, watch how their input switch, screen crop, network, and mic actually behave in that room.

**Constraints:**
- Presenter laptop → HDMI into production switcher (assumed) — OR they may insist on a production machine for reliability. **Ask now** (question list §8). If production-machine-only: your "live" demo must run from a **browser on their machine** hitting your hosted stack → then the demo MUST be reachable via plain HTTPS on a clean browser, no local deps. Design for that path regardless — it doubles as your failover.
- WiFi: don't rely on attendee WiFi. Ask for the production network. Bring own uplink anyway.
- Power: podium power almost certain, but stage laptop on battery at 18:00 after 36h hacking = stupid risk. Plug in, battery-saver off, display sleep never.
- Failover expectations of the org: they run 70+ sessions/day; they will **not** pause the program for a hung demo. If your input fails, you get ~60–90s before the emcee moves on. Design a 15-second abort path.

---

## 5. JUDGING / AWARDS / MEDIA

**Judging:** panel judges Sunday at LifeTech (the ~14 judge-map from `judges.md`/`MASTER-BRIEF.md`): submissions 18:00 → deliberation → finalists 21:00. Stage = presentation + awards. Two readings remain possible — (a) podium already decided Sunday, stage is coronation; (b) finalists pitch Monday and order/places announced on stage. Agenda literally says "Winning teams," and CPs award their challenges "on the Summit stage" ⇒ lean (a)+(b) hybrid: podium decided, challenge awards + podium announced on stage. **Design pitch to function as both** (see choreography).

**Media — the surface that outlives the prize:**
- **Recorded, not livestreamed.** Summit FAQ: "not livestreamed, but the majority of speaker videos available after on YouTube @GenAISummit." Assume your set is filmed → the YouTube cut is the durable artifact. Design for the camera: the screen IS the shot (Book Castle camera will frame presenter + 10m screen or cut to input feed).
- **Press bench inside the summit:** Kathimerini (Iliana Magra moderates), Wired Greece (EIC Niko Efstathiou moderates), Athens Voice (Lukas Velidakis moderates ×2), Euronews Greece (Symela Touchoutidou moderates), Fortune Greece, Startupper/powergame, Innews (media enabler). PM + Eurogroup President + 4 ministers ⇒ national press pool + ERT on site for the closing — you are adjacent to the biggest Greek tech-news day of the year.
- Press will NOT be in Book Castle at 18:00 unless given a reason → see media plan §9.

---

## 6. STAGECRAFT SPEC — designing the 5-minute finale

### 6.1 The decision: LIVE-ON-RAILS (live agent, staged substrate)

```
Decision matrix
─────────────────────────────────────────────────────────────────
Option          Verdict      Why
Full live       RISKY-OK     Highest aura payoff, highest tail risk.
(wild inputs)                Only if venue net confirmed + you've
                             rehearsed the exact scenario ≥10×.
LIVE-ON-RAILS   ✅ PICK      Live agent + real systems, but every
                             input is pre-staged (seeded inbox,
                             fixed doc set, known-good targets).
                             Indistinguishable from "wild" live.
Hybrid (live    FALLBACK-1   If net is degraded: agent runs on
trigger +                    localhost/offline corpus or the last
pre-render)                  real run is replayed frame-true.
Video + live    FALLBACK-2   If input chain fails: narrate over a
voiceover                    90-120s screen-capture on USB + cloud.
Slides only    FALLBACK-3   If everything dies: 4 stills of real
                             artifacts (sent email, merged PR,
                             reconciled ledger) + talk track.
Pure video      DO NOT       Reads as fake to this jury ("not a
submission                   pitching competition…"). Only as backup.
─────────────────────────────────────────────────────────────────
```

**Why live-on-rails wins here specifically:** Book Castle is small and close — the audience sees your screen and your hands; a video is legible as a video. Judges (Koukoumidis, Zindros, Gianitsos, Abed) audit realness. But "live" does NOT mean improvising inputs — you control the corpus, the fixtures, the time. The agent's *decisions* are live; its *environment* is staged. That's honest and it's how the Minister demoed mAIgov.

### 6.2 The 5-minute choreography (build to 4'30", never past 5')

```
0:00–0:20  COLD OPEN — agent already running on screen.
           Don't say hi. The screen is already mid-job: tool calls
           streaming, artifacts appearing. Talk OVER the motion:
           "While you've been watching, it's done X." (aura beat 1)
0:20–0:50  THE JOB — one sentence: who, what tedious multi-step
           job, what "done" means. Named persona + stakes.
           ("[Name] spends 6h a week doing X. Watch it end.")
0:50–2:40  THE RUN — the engineered centerpiece. 2–3 visible,
           consequential actions on REAL systems (email sent,
           doc filed, PR opened, invoice matched). Narrate decisions
           not mechanics. Show the receipt as it lands (audit log /
           policy gate fires = Zindros/Quintessential beat).
2:40–3:10  THE RECEIPTS — artifacts on screen, BIG: the produced
           deliverable (report/message/PR), the signed action log,
           the one-line eval + cost ("42min→90s · $0.03").
3:10–3:40  THE AURA MOMENT — the one choreographed <20s delight
           (the SLM-beats-frontier table, the graceful failure-
           recovery, the perfect microcopy). Then STOP.
3:40–4:30  CLOSE — what it is, built-in-36h cred, what Monday
           looks like (continuation path = Panathēnea/LifeHack DNA),
           one line of team story. Final frame: product name +
           "it just finished" (the run completes on cue).
4:30–5:00  BUFFER — absorb applause, emcee question if any.
```

Rules: **the run starts before you speak** (the clock eats intros); **artifacts > dashboards** (one huge produced thing beats a busy console); **end on the artifact, not on a thank-you slide.**

### 6.3 What reads on a 10×4m projected screen in a 220-seat library

- **One thing at a time.** Back row is ~20m out; a dashboard with 6 panes is wallpaper. Full-screen the artifact; zoom the browser to 150–200%; terminal font ≥28px equivalent.
- **High contrast, dark or saturated.** Projection in a lit atrium: light-gray-on-white dies. Use dark theme with bright accent, or pure-white bg with ≥14px-equiv black text. No hairlines, no 11px captions.
- **Motion over text.** The eye reads a moving cursor/tool-call stream from 20m; it cannot read a paragraph. If text is on screen, it must be ≤8 words per block, ≥60pt equiv.
- **Pre-commit the screen layout.** Single window, full screen. No alt-tabbing between windows on stage (switcher lag + dead frames look like failure). Sequence = scroll or in-app navigation inside ONE app/window.
- **Kill chrome.** Hide bookmarks bar, tabs, dock, menu-bar clock/battery/VPN icons — everything that says "laptop." Full-screen/kiosk mode. Notifications off (Do Not Disturb + signed-out of anything that can pop). TrueTone/Night Shift off (color shift reads on camera).
- **Cursor is a prop.** Visible, deliberate pointer movement; enlarge cursor 1.5–2×; use it to point at receipts while narrating.
- **No sound dependence.** Design the demo to work muted; if agent voice/audio matters, confirm 3.5mm/DI to PA — otherwise skip.
- **Name/brand on screen from frame 1.** The recording crops tight — your product name/logo should live in the app UI itself (custom header/watermark), not just the first slide. If the video surfaces, your brand is in it.

### 6.4 Network & hardware ladder

```
PRIMARY   Venue production wired/dedicated network (request by email NOW)
BACKUP-1  Own uplink: 5G/LTE router or tether (Cosmote/Vodafone 5G
          covers Kallithea/SNFCC area well) — bonded or auto-switch
          preferred; manual switch rehearsed <15s.
BACKUP-2  OFFLINE MODE: the entire demo must run against a localhost
          mirror / recorded API corpus with ZERO net (agent serves
          cached tool responses — flag in your narration only if asked;
          never claim it's live if it isn't, but don't volunteer).
BACKUP-3  Video of the winning run: 90-120s screen capture, 1080p+,
          exported Mon morning to USB-A + USB-C + cloud link + email
          to organizers. If you hand it to production, it must be a
          boringly compatible file: H.264 MP4, 16:9, no weird codecs.
HARDWARE  Laptop: the exact one that ran it at LifeTech; power brick;
          HDMI + USB-C→HDMI adapter ×2; a second team laptop with the
          demo stack mirrored (warm standby, signed in, pre-cached).
          Freeze: sleep never, updates off, VPN off, scaling fixed,
          wallpaper = black, Do-Not-Disturb on, auto-lock off.
```

### 6.5 Team choreography & stage logistics

- **1 presenter + 1 driver max on stage.** Presenter faces audience, narrates, does NOT touch the keyboard mid-run. Driver (or same person in practice, but prefer two) sits at the laptop/podium — if a dialog pops, the driver kills it while the presenter keeps talking. Everyone else: front row, phones on the artifacts.
- **Stage flip:** in the room by **17:15** (watch TfH demo = live tech rehearsal; clock the input ritual). Meet the stage tech at 17:45 during their setup. Handshakes: HDMI EDID/resolution (force 1080p60 output — avoid 4K weirdness on switchers), network, mic (headset/lav > handheld for a demo).
- **Timer discipline:** assume a hard 5'00" and a confidence/timer monitor may or may not exist → bring your own: second team member front-row with fingers-up countdown at 3/2/1 min. Finish at 4'30".
- **Mic:** request lav/headset (hands free). If handheld only, driver does all keyboard work.
- **If the run hangs:** 15s rule — presenter narrates the expected outcome while driver attempts recovery once; at 60s cut to the video artifact (driver has it queued, full-screen, play = one keypress). Never apologize twice; the recovery IS the aura moment if handled with wit (Abed scores "aura," Quintessential scores "no slop").
- **Security sweep relevance:** 19:00–19:30 security check for PM — don't leave gear backstage; take everything with you at 18:30; room closes.

### 6.6 Design the artifact FOR the recording

The YouTube cut is the deliverable that outlives the €5k. Optimize:
- The screen is the B-roll — make the app UI look like a product (name, logo, clean layout, your accent #006bff), not a dev console.
- The single best 60–90s of your run should be self-explanatory without context (press will clip it).
- Have your own 90s cut ready to hand journalists Sunday night (see §9) — don't wait for summit post-production (weeks lag historically).

---

## 7. FAILURE/RISK TABLE

| Risk | Likelihood | Mitigation |
|---|---|---|
| Attendee/production WiFi congestion | HIGH (5,000 devices) | Production wired request + own 5G + offline mode (3 layers) |
| Input switch / adapter fail | MED | Force 1080p60, carry 2 adapters, rehearse switch at 17:45, video file pre-staged on the machine |
| Agent nondeterminism (run takes 8min or derails) | MED-HIGH | Seeded fixtures + tight scope (2-3 actions) + pre-recorded same-scenario run as abort target; rehearse ≥10× Sat night AND Sun AND Mon AM |
| 5' overrun → cut | HIGH if unrehearsed | Script at 4'30"; front-row countdown; kill entire 3:10 aura beat if behind (it's the only removable block) |
| Room drains toward Central for PM | MED | Cold open with agent running + hook by :20; place own people front to hold energy; accept the room is half-full — the camera is the audience |
| Slot moves (agenda is "tentative") | MED | Re-pull the agenda CSV weekly; check again Mon morning — the whole schedule is a live Google Sheet |
| Organizers switch format (Q&A, order) | MED | Confirm w/ Abed Sun night; rehearse a 60s "answer version" of the demo for a possible emcee question |

---

## 8. OPEN QUESTIONS — email Abed / Panathēnea TechOps (Konstantinos Martinis) NOW

1. Confirm slot/stage: 18:00–18:30 Book Castle — final? How many teams pitch? Pitch order decided how/when?
2. Are podium places decided Sunday, or is anything scored/announced on stage? When do challenge-partner awards happen?
3. Input: presenter laptop via HDMI at the podium, or production-machine-only? If production machine — OS/browser constraints?
4. Is there a dedicated stage/production network (wired or hidden SSID)? Can we get creds Sunday night for testing?
5. Confidence/timer monitor at Book Castle? Lav/headset mics available? Audio feed (3.5mm/DI) for in-demo sound?
6. Can finalists do a 10-min tech check in Book Castle Monday morning or during the 17:10 slot change?
7. Will the hackathon block be filmed (and when do recordings post)? Press/photog accreditation — can our own photographer be in the room?
8. Screen: native resolution of the Book Castle projection? 16:9 inside the 10×4m face?

---

## 9. MEDIA PLAN (compress — the 48h surface)

- **Sun 21:00 (finalists announced):** team photographer shoots the LifeTech moment; draft press one-pager (Greek + English): name, what it does, 3 artifact stills, team, contact.
- **Mon 09:00:** post teaser on LinkedIn tagging GenAI Summit, Abed, Panathēnea, sponsor brands used (Quintessential/Wonderful/etc.) — "today 18:00, Book Castle."
- **During the slot:** own photographer front row (stills of screen + reaction); teammate screen-records the live run for the 90s cut.
- **Mon 20:30 (after PM):** 90s demo cut + 3 stills → posts tagging summit; DM the moderating journalists you mapped (Kathimerini/Wired/Athens Voice/Euronews GR are all on-site) + Fortune Greece/Startupper; pitch angle: "built in 36h in Athens, demoed on the GenAI Summit stage" + Greek-vertical hook if applicable.
- **Tue:** YouTube/LinkedIn long post with full clip + build story; submit to summit's social for re-share; the recording posts to @GenAISummit later — request the raw file or the clip timing from production.

*Assumption flags: pitch count/order, Q&A, judging-final-vs-showcase mechanics, and the Book Castle AV chain are inferred/unconfirmed — §8 list resolves them. The agenda itself is marked tentative.*
