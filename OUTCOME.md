# Outcome — Post-Event Retrospective

Event ran 14–16 Nov 2026 as scheduled. Source for every fact below: the official [submissions page](https://hackathon.polymath42.com/submissions) (all 47 submissions listed with track, team, demo video). Anything not on that page is marked unknown, not guessed.

## Results

| Place | Project | Track | Demo |
|---|---|---|---|
| 🥇 1st (€5,000) | **Otty** — an SMB's own AI agent: paste the shop's site, it opens an MCP door customer assistants can order/book through; owner re-settles orders in one sentence; every action and refusal gets a signed, tamper-evident receipt | Open Track | [video](https://youtu.be/wi6PpO3ClFg) |
| 🥈 2nd (€2,500) | **Steptrace** — turns any how-to video into an AR guide that highlights the exact part per step | Open Track | [video](https://youtu.be/itl3_OurC98) |
| 🥉 3rd (€1,000) | **Flux** — end-to-end sign-language ↔ speech translation for the deaf community | Open Track | [video](https://youtu.be/E-xKTwRW93E) |
| Finalist | **FIREYE** — wildfire command console (Nikolas Sapalidis, Marco Serat) | Open Track | [video](https://youtu.be/F1bdtWd3L4o) |

Field: 47 teams submitted, **9** semifinalists, 4 finalists pitched Mon 16 Nov on the Summit stage.

## FIREYE (our entry — Finalist, top 4 of 47)

Wildfire command console for fire chiefs/incident commanders. Per the official listing: 14 simulated camera sources (6 drones × visible+thermal, 8 fixed) + 24 ground sensors on one 3D satellite map; an orchestrator tasks drones to scout areas fixed cameras can't see, each task carrying its stated reason; alerts fire only on material change (new fire, ≥20% spread acceleration, earlier arrival ETA, newly threatened location); every evidence item shows source, capture time, and simulated-or-not; consequential actions require approval from the current human Chief — approvals expire, stale/duplicate inputs rejected; the whole incident replays exactly as known at any moment. Demo replays the 2018 Mati fire, 14:00–22:00.

## What the recon called correctly

- **The track map.** All four predicted tracks ran: Open (28 entries) · Content & Digital Art/fal (7) · Voice & Enterprise/Wonderful (6) · Biotech & AI/LifeTech Park (6).
- **The convergence architecture was the meta.** The winner embodies it almost verbatim: Otty asks the owner "only when a rule would break" (policy gate) and issues "signed, tamper-evident" receipts per action/refusal (signed action log). Semifinalist Solon ran on "models read, code decides, you approve" — the Keel doctrine this repo extracted from past winners. FIREYE shipped the same spine: human-approved consequential actions, expiring approvals, per-task reasons, full replayability.
- **"Real work over polish"** ([judge-abed](docs/people/judge-abed.md), [abed-live](docs/people/abed-live.md)): every finalist is a workflow — SMB ops, repair guidance, accessibility, incident command — not a wrapper demo.
- **Interrogable demos:** FIREYE's replay-as-known and source/timestamp-per-evidence design exists precisely so judges can probe mid-run.

## What it missed

- **The vertical.** FIREYE is none of the five pre-ranked options — the wildcard branch ("snap to whichever brief fits", Open Track) was the one taken. The ranked lanes (Greek voice, maritime claims, Prosperty, procurement) went unused.
- **Sponsor-brief leverage on the podium.** The [challenge-mechanics](docs/intel/challenge-mechanics.md) doctrine ("win one brief, that sponsor advocates you on the main panel") did not materialize: all four finalists are Open Track. The two sponsor-track semifinalists (never alone/Voice·Wonderful, ClinRadar/Biotech·LifeTech) stopped at semis.
- **Scale.** 47 submissions vs the ~100-builder selected field the recon planned around.
- **Semifinalist count.** 9 actual vs the 8 in the pre-event timeline (README).

## Unknown / not published

- Whether the sponsor challenge prizes (Wonderful, fal, Oumi, Firecrawl, boxd, Cognition/Devin) were awarded at all, and to whom. The page marks only 1st/2nd/3rd/Finalist/Semifinalist.
- FIREYE's internal ranking among the four finalists; only podium order is public.
- Whether any sponsor brief matched the recon's Wonderful-voice prediction (~45%); brief texts were never published on the site.
