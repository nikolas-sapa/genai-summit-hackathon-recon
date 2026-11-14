---
title: "Recon Delta 2026-11-14 — site diff + tracks/credits revealed"
type: source
tags: [genai-summit-hackathon, recon, delta, sponsors]
aliases: ["Nov 14 recon delta", "hackathon site diff Nov 14"]
created: 2026-11-14
updated: 2026-11-14
status: active
---

Diff vs 2026-11-12 baseline (`~/scratch/hackathon-recon-2026-11-14/` captures vs `-11-12/`). Event day 1 — site is live, no deploy gaps observed.

# Nov 14 deltas

## What changed on the site
- **Three new public pages** (all in sitemap, all serving `Accept: text/markdown` via `.md` too):
  - `/prep` (lastmod 11-13) — participant prep guide, signed "Abed". Reveals the tracks, Discord invite, no-alcohol rule (LifeTech Park is a research facility), food/rest logistics.
  - `/credits` (lastmod 11-13) — per-partner credit table, claim instructions "TBA".
  - `/shuttle` (lastmod 11-12) — shuttle schedule, Syntagma X95 stop, seat-cancel deadline was 17:00 Fri.
- `/llms.txt` updated to reference `/prep` and `/credits`.
- Sitemap lastmods bumped on `/` and `/agenda` to 2026-11-12.

## Partner adds/removals
- **None.** Homepage partner list identical to Nov 12 (16 names): Quintessential, Wonderful, Google, Big Pi, fal, Prosperty, boxd, Firecrawl, Cloud Office, treg, Wiserwork, Endeavor, Oumi, Always Online, SHAKE talent up (Hiring Partner), Crowdcruit.
- **Athens LifeTech Park elevated to track host** — prep guide names "Biotech & AI — with our hosts, Athens LifeTech Park" as a track. Venue was public before; sponsor-track role is new.

## Deck-overlay probe results
Every slug checked for `sd-watermark-sponsor`/`sd-proposal-logo` on `?sponsor=<slug>`:

| Slug | Overlay | Change vs Nov 12 |
|---|---|---|
| cognition, resolve, google, endeavor, treg, nofire | yes (personalized decks) | none |
| marathon | yes (partners/marathon.png) | none — still pending-deal signal |
| wonderful, quintessential, bigpi, fal, firecrawl, oumi, prosperty, boxd, wiserwork, always-online, crowdcruit, cloud-office | yes | none |
| shake, anthropic, openai, lovable, devin, cursor, microsoft, databricks, elevenlabs, parloa, omilia, kaizen, vodafone, pharos | no (generic) | none |

- **Zero new overlays. Zero removals.** 19/33 slugs render overlays, same set as Nov 12.
- Resolve deck still "Proposal prepared 10 November 2026 … no partnership is confirmed" — **ResolveAI still not signed** as of event morning.
- Generic deck slide content byte-identical to Nov 12.

## Agenda/logistics changes
- **Finals pipeline now explicit:** 8 semifinalists selected 18:00–19:00 Sun → 3-min pitches to judges ~19:00 → **4 finalists** announced ~20:00–20:30. (Previously just "shortlist/semifinalists/finalists" with no counts.)
- **Monday finals moved earlier:** 4 finalists pitch at Book Castle 18:00–18:30 (3 min each), **winners announced 18:50** (was 19:30).
- **Shuttle replaces "bus riders gather":** Sat meet Syntagma 10:30, depart 11:00, arrive venue 11:45, return 22:00. Sun meet 08:45 by X95 stop, depart ~09:15, arrive 10:00, return 21:30.
- Sunday schedule filled in: all-day hacking, breakfast, ~14:30 lunch, 18:00 code freeze (repo + demo video + project details).
- Friday pre-party with Hustle Hours (luma.com/ki4ckvc7) unchanged.
- Index copy updated to match: "The 4 finalists are announced around 20:00–20:30".

## Tracks (new — from /prep)
- **Voice & Enterprise Agents** — with Wonderful
- **Biotech & AI** — with Athens LifeTech Park (hosts)
- **Content & Digital Art** — with fal
- **Open Track** — own idea; "hardware gets extra points"

## Credits (new — from /credits)
- **Google:** AI inference, everyone
- **Wonderful:** TBA, selected teams only
- **fal:** $50/builder + $1.5k fal-track credits, everyone
- **boxd:** €50, everyone
- **Oumi:** TBA, everyone
- **treg:** $20/builder + $500/$250/$100 top-three bonus, everyone

## Status checks (unchanged)
- Prizes €8.5k total (5k/2.5k/1k), Quintessential sole "Prizes sponsored by".
- JSON-LD `maximumAttendeeCapacity` 120; site copy "~100 selected builders".
- /terms + /privacy HTML 200, still 404 on markdown accept. Terms still dated "Last updated 9 November 2026".
- Discord now public: discord.gg/gqU8FW45qf (#transport, #carpooling, #find-a-team, #announcements).

## Attendance
- Luma: **171 → 176 going (+5)**, still Event Full / waitlist only. 176 going vs ~100 capacity suggests organizer overbooks against no-shows or counts team+partners.

## Implications
- Tracks map 1:1 to signed partners (Wonderful→voice, LifeTech Park→biotech, fal→content) — the three named tracks ARE the partner-challenge briefs. Marathon overlay persists but no Marathon track named → deal likely still pending or converted to judge/mentor presence only.
- Wonderful locked to "selected teams only" for credits — consistent with tighter track terms; IP-landmine flag from Nov 11/12 deltas still stands pending a look at what "selected" means at kickoff.
- treg now gives direct cash-equivalent prizes ($500/250/100 top three) on top of Quintessential's €8.5k — second prize-backed partner.
- No new sponsor signals at event start: partner set is frozen for the weekend. Any post-weekend addition would land via the `/deck?sponsor=` probe.
