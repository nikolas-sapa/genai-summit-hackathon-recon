---
title: "chatter3"
type: source
tags: [genai-summit-hackathon, recon, chatter]
aliases: ["chatter3"]
created: 2026-11-14
updated: 2026-11-14
status: active
---

# Chatter Sweep 3 — Gen AI Summit Hackathon (Athens, 14–15 Nov 2026)
Swept: Sat 14 Nov 2026, morning (day-of, T-0; doors open 12:00 EET). Window: ~Nov 11–14. Web + direct fetches (curl; webfetch unavailable). Prior sweep: `chatter2.md` (Nov 10).

---

## TOP SIGNALS (new or materially updated since sweep 2)

### 1. SITE WENT OPERATIONAL — agenda, tracks, credits all live (Nov 12–13)
Sitemap grew 5 → 13 URLs. New pages: `/agenda` + `/shuttle` (lastmod Nov 12), `/prep` + `/credits` (lastmod Nov 13).
- **Full run-of-show confirmed**: Sat 12:00 arrival → **12:30 kickoff "rules, tracks and how the weekend runs"** → 13:00 hacking starts. Sun **18:00 code freeze** (repo + demo video + project details) → 18:00–19:00 shortlist → **8 semifinalists** pitch ~19:00 (3 min each) → **4 finalists** announced ~20:00–20:30 → Mon: Book Castle SNFCC 18:00–18:30 (3 min/team), **winners announced 18:50**.
- **CORRECTION to chatter2's leaked 19:00-Saturday challenge reveal**: tracks are revealed at kickoff 12:30, not 19:00. The cached index.md line was from a reverted draft.
- Sources: `https://hackathon.polymath42.com/agenda` (also `agenda.md`; `?role=judge` / `?role=mentor` expose role notes), `https://hackathon.polymath42.com/prep`.

### 2. CHALLENGE TRACKS PUBLISHED (prep page, Nov 13)
- **Voice & Enterprise Agents — with Wonderful**
- **Biotech & AI — with Athens LifeTech Park** (the host venue)
- **Content & Digital Art — with fal**
- **Open Track — BYO idea; "Hardware gets extra points"**
Briefs themselves still gated to kickoff ("We'll cover the challenges, tools, and practical details at kickoff"), but track verticals are now public ahead of doors.

### 3. CREDITS PAGE LIVE — sponsor track prizes beyond the €8,500
- **Google AI**: inference credits, everyone.
- **fal**: US$50/builder + **US$1.5k fal-track credit prize**.
- **treg**: US$20/builder + **US$500/250/100 top-3 team prizes**.
- **boxd**: €50 everyone. **Oumi**: TBA everyone. **Wonderful**: TBA, **selected teams only**.
- builders.zone listing corroborates "€5,000/€2,500/€1,000 **plus partner awards**".
- Source: `https://hackathon.polymath42.com/credits`.

### 4. ION PETROPOULOS OUT — Abed running solo
LinkedIn, Nov 3: *"To anyone I promised something to at the GenAI Summit Hackathon, please reach out to Abed Hamami who's handling it from here."* Bio now "Founding Engineer at GamerPlug". Explains the reverted `cc ionpetro@gmail.com` line spotted in sweep 2's stale cache. Organizing team now Abed + Konstantinos Papoulakos (self-announced Oct 8). `@ionandabed` X acct dead since Oct 12.
- Source: `https://www.linkedin.com/posts/ionpetro_to-anyone-i-promised-something-to-at-the-activity-7523418481921310721-TVab`

### 5. LUMA: 176 going (was 162), new ticket tiers Judge + Sponsor
Ticket types now: Standard / Mentor / **Judge** / **Sponsor** (all Require Approval). Visible attendees incl. **Ilias Pantazis** and **Lars Rasmussen** — Rasmussen is Panathēnea co-founder (Google Maps co-creator, angel). Given the new Judge tier, plausible judge presence. Still "Event Full → waitlist" with organizers pushing RSVP releases ("long waitlist" per prep guide).
- Source: `https://luma.com/x1wxi5sn`

### 6. DISCORD LIVE — comms moved off X
`https://discord.gg/gqU8FW45qf` — guild "GenAI Summit Hackathon", ~86 members, inviter `abed42`, manual-approval membership gate (not publicly readable). Channels per prep: #general, #find-a-team, #announcements, #transport, #carpooling. All pre-event coordination is now in-server.

### 7. PARTNER LIST FINAL — Google + Cloud Office + SHAKE are late adds
Live index.md lists 16 partners: Quintessential, Wonderful, Google, Big Pi, fal, Prosperty, boxd, Firecrawl, Cloud Office, treg, Wiserwork, Endeavor, Oumi, Always Online, SHAKE talent up (Hiring Partner), Crowdcruit. Search-engine-cached index.md (older) lacks Google, Cloud Office, SHAKE → all three added within ~last week. Context: **Cloud Office ran Google Cloud Day Athens Nov 10** — likely the conduit for the Google inference credits.
- Source: `https://hackathon.polymath42.com/index.md`, `https://www.cloud-office.com/gr/events/google-cloud-day-athens-2026`

### 8. `/deck` + `/terms` FAMILY — live after all (verified 2026-11-14)
Initial read reported styled 404s; direct verification shows `/deck?sponsor=marathon|wonderful|google` all return HTTP 200 WITH `sd-watermark-sponsor`/`sd-proposal-logo` overlays, and `/terms` + `/terms/wonderful` both return 200. Marathon overlay still live = deal signal still pending per Nov-12 convention. `/terms/wonderful` content fetched in full → see `wonderful-terms.md` (§4.1 IP assignment is real and scoped to on-Platform output).

## ANNOUNCEMENTS (sourced)
- **Pre-party happened**: "Hustle Hours × Gen AI Summit Hackathon Pre-Party", Fri 13 Nov 19:00–22:00, Amber Athens (Kolokotroni 38-40). 111 going, hosted by Dinos Papargyriou + Abed; Hustle Hours = SF hacker-house crew (Philoxenia) back in Athens. `https://luma.com/ki4ckvc7`
- **Shuttle schedule** (`/shuttle`): Sat meet 10:30 at X95 stop Syntagma, dep 11:00 → venue 11:45; return 22:00. Sun meet 08:45, dep ~09:15 → 10:00; return 21:30. Seat-cancel deadline was Fri 17:00.
- **Judge notes** (`/agenda?role=judge`): judges split across Sun/Mon; Sun arrive <18:00, shortlist→8 semis→pick 4; Mon Book Castle <18:00. **Voting web app** + **"AI-assisted review of the submissions"** notes provided to judges. Judging framing: "what the team has shipped, how well it works, potential in team + build; focus on work completed during the hackathon."
- **Mentor notes** (`/agenda?role=mentor`): walk-the-floor format; most useful windows Sat 13:00–18:00 (team formation) and Sun to 18:00 freeze.
- Venue address confirmed: Athens LifeTech Park, Block 49, 31st Street, Foinikas, 190 04 Spata.
- Prep-guide logistics: no alcohol (research facility rules), BYO water bottle, extension cord, sleeping gear encouraged; overnight stay allowed but sleep encouraged.

## SPONSOR MOVES
- **Wonderful**: confirmed as Voice & Enterprise track sponsor; credits gated to "selected teams only" (implies platform/workspace provisioning rather than open API keys). Athens bench for on-site staffing: Ilia Tzortzopoulou (GM SEE, on Monday Summit panel), Panos Michelakis (FDE/Pod Tech Lead), Natalia Vavoula (Deployment Strategist) — all Athens-based. Prizes co-funded w/ Quintessential since Oct 7 post.
- **fal**: Content & Digital Art track + $1.5k track credit prize + $50/builder.
- **treg**: cash-equivalent credit prizes $500/250/100 for its top-3 — effectively a second parallel prize ladder.
- **Google/Cloud Office**: inference credits for all; partnership landed ~Nov 10–13 (Cloud Office's own Google Cloud Day Athens ran Nov 10).
- **Marathon VC**: NOT on final partner list, but `?sponsor=marathon` overlay verified still live (200 + watermark markers) — pending-deal signal persists. Papadopoulos judge seat plausibly tied to it closing.
- **Big Pi**: partner, no public hackathon post; Guy Krief (partner) is hackathon-circuit regular — candidate judge.
- **Oumi**: partner, credits TBA; CEO Koukoumidis on Summit speaker list. No public post.
- **Prosperty, Wiserwork, Always Online, Crowdcruit, Firecrawl, boxd, Endeavor, SHAKE**: listed, no fresh announcements indexed.

## PARTICIPANT SIGNAL
- Discord (86 members) is where team-formation chatter lives — gated, not indexable. Expect #find-a-team to have done the matching pre-event.
- Named mentors confirmed via LinkedIn: **Agentic Athens** (Konstantinos Tsolakidis + Nikiforos Kollaros, Oct 29 post — scope/debug/demo-feedback brief), **Paraskevi Kivroglou** (Nov 10; Product @ wiserwork.ai — partner employee mentoring).
- Adjacent event same weekend: "GenAI Summit Workshop: Ship real work with AI agents" (Sun Nov 15, €390, Tsolis + Muller, Wiserwork demo) — separate ticketed track, same orbit.
- No team/project announcements, leaked briefs, or "we're building X" posts indexed in window. No public X chatter — Summit has no official X; abed42's last activity Nov 10 was an unrelated RT. All signal moved to Discord + LinkedIn.
- Luma attendee count 176 vs stated capacity ~100–120 → includes mentors/judges/sponsors/organizers (multi-ticket-type rollup).

## BRIEF / WATCH ITEMS
- **Wonderful track IP terms** (from Nov-12 delta): RESOLVED — `/terms/wonderful` is live (200). §4.1: Wonderful owns everything built **inside their Platform**, assigned on creation; your own repo/infra outside the Platform stays yours. Full analysis → `wonderful-terms.md`. Recheck at kickoff — §10 lets them change terms without notice.
- **Marathon overlay** (from Nov-12 delta): STILL OPEN — `?sponsor=marathon` overlay live (verified 11-14). Watch whether Marathon appears on the partner list or a Papadopoulos judge seat gets confirmed on-site.
- **Challenge briefs**: drop at 12:30 kickoff today — verticals known (Voice/Enterprise, Biotech, Content/Art, Open+hardware-bonus); grab exact brief text + per-track judging weight then.
- **Credits claim mechanics**: all "How to claim: TBA" — watch /credits + Discord #announcements at kickoff; Wonderful credit access is selective, apply early if relevant.
- **Semifinalist format**: 3-min pitch Sunday ~19:00 → judges pick 4. Optimize for a punchy live-demo 3 minutes; Book Castle slot Monday is equally tight (3 min/team).
- **"AI-assisted review of submissions"**: judges get AI-generated notes on repos — README/demo video quality matters for the automated pass, not just human eyes.
- Recheck `/agenda` Sunday — working doc, times have shifted once already.
