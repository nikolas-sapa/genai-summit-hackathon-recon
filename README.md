# Gen AI Summit Hackathon — Recon HQ

**14–15 Nov 2026** · Athens LifeTech Park, Spata · Finals **Mon 16, 18:00–18:30, Book Castle stage, SNFCC**
**Theme:** "Agents at Work" · **Judged on:** usefulness · craft · aura points
**Prizes:** €8,500 (5k/2.5k/1k — Quintessential + Wonderful) + up to 4 sponsor challenge prizes
**Site:** [hackathon.polymath42.com](https://hackathon.polymath42.com/) · [Summit](https://genaisummitseeurope.com)

> 52-agent deep recon on judges, sponsors, event mechanics, and the winning technical architecture. 80 notes in [`docs/`](docs/).
> **Nov-14 refresh:** +6 judge dossiers (Rasmussen, Papadopoulos/Marathon, Bellonia, Mallios, Tsirekas, Bannerman), +7 mentor dossiers (Kontogiannis/Wonderful-CTO, Forte, Mandalis, Marcus, Zacharopoulos, Konstantzos, Aljaberi), +3 sponsor dossiers (Google, Cloud Office, SHAKE), tracks+credits revealed, Wonderful IP terms analyzed, PG reading list. Ion Petropoulos out as co-organizer.

**Start here:** [docs/START-HERE.md](docs/START-HERE.md) — the 8-note reading list (~25 min)
**Prizes + build plan:** [PRIZES-AND-BUILD.md](PRIZES-AND-BUILD.md)
**Pre-event checklist:** [CHECKLIST.md](CHECKLIST.md)

## Timeline

| When | What |
|---|---|
| Sat 12:00 | Arrival, team forming |
| Sat 12:30 | **Kickoff — tracks + briefs revealed** — commit vertical only after this |
| Sat 13:00 | Hacking starts |
| Overnight | Build (bring sleeping gear; venue open, no alcohol) |
| Sun 18:00 | Code freeze — submit repo + **demo video** + project details |
| Sun ~19:00 | 8 semifinalists → 3-min pitches |
| Sun ~20:00 | **4 finalists picked — the real gate** |
| Mon 18:00 | Finals, Book Castle stage (3 min/team) · winners ~18:50 |

**Rules:** teams 1–5 · boilerplate legal, pre-built product = DQ · you own IP · 18+

## The architecture (every serious judge converged on it)

**Policy-gated agent with verifiable core + owned intelligence:**

```
goal → planner SLM (Oumi fine-tune, Krikri-8B for Greek) → DAG
  → boxd workers (fork clones mid-run)
  → tools bought via treg (visible cost receipts)
  → browse via Firecrawl (liveViewUrl on screen)
  → deterministic core does ALL math (LLM only fills typed schemas)
  → verifier SLM + signed action log (ed25519 hash-chain)
  → POLICY GATE: writes require human approval (judge presses it live)
  → artifact delivered (finished, shareable, beautiful)
```

Why: Wonderful ("routes/approves/executes within guardrails"), Quintessential ("writes only through PRs"), NOFire (policy gate = their product), Zindros ("checked, not trusted") — same architecture, four judges. Keel won the last Athens edition with "dollars never come from the model."

## Vertical call — decide at 12:30 kickoff when briefs drop

Tracks now public (Nov-14): **Voice & Enterprise** (Wonderful — read [wonderful-terms](docs/intel/wonderful-terms.md) first: they own on-Platform output) · **Biotech & AI** (Athens LifeTech Park) · **Content & Digital Art** (fal) · **Open Track** (hardware bonus). Credits: Google inference for all · fal $50+$1.5k · boxd €50 · treg $20+$500/250/100 · Wonderful selected teams.

1. **Greek voice agent** — lane is empty; Wonderful's predicted brief (~45%); outbound call to a judge's phone live = the aura moment
2. **Maritime claims agent** — live AIS at Piraeus; proven Athens meta (Keel); flatters VentureFriends + Endeavor
3. **Prosperty Μεταβίβαση copilot** — property-transfer doc orchestration; their roadmap + Big Pi/Eurobank
4. Procurement watchdog — only if Porios isn't competing (check his badge)
5. Or snap to whichever sponsor brief fits best

## Docs index

### People (judge/mentor dossiers) — [`docs/people/`](docs/people/)
Lead judge [Koukoumidis](docs/people/judge-koukoumidis.md) (Oumi) · organizer [Abed](docs/people/judge-abed.md) (sole — Ion stepped back Nov-3, note kept for craft value) · new: [Rasmussen](docs/people/judge-rasmussen.md) · [Papadopoulos/Marathon](docs/people/judge-papadopoulos.md) · [Bellonia](docs/people/judge-bellonia.md) · [Mallios](docs/people/judge-mallios.md) · [Tsirekas](docs/people/judge-tsirekas.md) · [Bannerman](docs/people/judge-bannerman.md) · [Big Pi](docs/people/judge-bigpi.md) · [VentureFriends](docs/people/judge-venturefriends.md) · [VC trio](docs/people/judge-vc-trio.md) · [OpenAI pair](docs/people/judge-openai-pair.md) · [tech trio](docs/people/judge-tech-trio.md) · [100mentors](docs/people/judge-100mentors.md) · [org roster](docs/people/org-roster.md) · [mentor table](docs/people/mentor-table.md) · sponsor-side people: [Wonderful](docs/people/wonderful-people.md) · [Quintessential](docs/people/quintessential-founders.md) · [Cognition](docs/people/cognition-people.md) · [Oumi](docs/people/oumi-people.md) · [infra](docs/people/infra-people.md)

### Sponsors — [`docs/sponsors/`](docs/sponsors/)
[Overview (local)](docs/sponsors/sponsors-local.md) + [infra](docs/sponsors/sponsors-infra.md) · [Wonderful](docs/sponsors/sponsor-wonderful.md) + [founders](docs/sponsors/wonderful-founders.md) + [clients](docs/sponsors/wonderful-clients.md) · [Oumi](docs/sponsors/sponsor-oumi.md) · [fal](docs/sponsors/sponsor-fal.md) · [Firecrawl+treg+boxd](docs/sponsors/sponsor-infra-plumbing.md) · [Quintessential](docs/sponsors/sponsor-quintessential.md) · [Prosperty](docs/sponsors/prosperty.md) · [Greek verticals](docs/sponsors/sponsor-greek-verticals.md) · [Endeavor](docs/sponsors/endeavor.md) · [NOFire etc](docs/sponsors/sponsor-remaining.md)

### Intel — [`docs/intel/`](docs/intel/)
Mechanics: [rules+deck](docs/intel/rules-deck.md) · [challenge mechanics](docs/intel/challenge-mechanics.md) · [logistics](docs/intel/logistics.md) · [finals format](docs/intel/finals-format.md) · [submission](docs/intel/submission.md) · [pitch craft](docs/intel/pitch-craft.md)
Strategy: [win strategy](docs/intel/strategy.md) · [Athens meta](docs/intel/athens-meta.md) · [past winners' code](docs/intel/past-winners-code.md) · [award patterns](docs/intel/award-patterns.md)
Field: [competition](docs/intel/competition.md) · [rivals deep-scan](docs/intel/rivals2.md) · [chatter sweep](docs/intel/chatter2.md)
Build: [agent architecture](docs/intel/agent-architecture.md) · [eval harness](docs/intel/eval-harness.md) · [MCP catalog](docs/intel/mcp-catalog.md) · [Krikri-8B](docs/intel/krikri.md) · [Greek voice](docs/intel/greek-voice.md) · [maritime](docs/intel/maritime.md) · [Greek data/APIs](docs/intel/greek-data.md) · [Greek pains](docs/intel/greek-pains.md)
