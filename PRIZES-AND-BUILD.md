# Prizes & What We Build

## Prize board

| Prize | Value | Who awards | What it takes |
|---|---|---|---|
| 🥇 1st place | **€5,000** | Main judge panel | Best overall agent — usefulness + craft + aura |
| 🥈 2nd place | €2,500 | Main judge panel | — |
| 🥉 3rd place | €1,000 | Main judge panel | — |
| Title Sponsor challenge | TBD (~brief-dependent) | Title sponsor's own judge | Their brief, their rubric |
| 3× Challenge Partner prizes | TBD | Each sponsor's own judge | "Brief it, judge it, award it" — max 4 sponsor briefs total |
| Cognition/Devin track *(pending)* | ~€8.5K equivalent in Devin credits (proposed in private deck) | Cognition rep (likely Psorakis) | Build visibly via Devin — parallel sessions, Review on real PRs, receipts shown |
| Google tech partner *(pending)* | $100/builder credits + possible €8.5K prize match | TBD | Gemini/Gemma-3 in stack if deal closes |
| Fal "best use of fal" | Credits/product | fal table | Media as the *visible payoff* of a useful workflow, not a toy |
| Oumi award | Credits/product | Oumi | **Weights trained during the event** (their rule — pre-stage recipe, train Sat night) |
| Firecrawl award | Credits/product | Firecrawl (Mercer/Martell) | Most usage × most real-world impact — hostile-source extraction |
| boxd award | Credits/product | boxd founders | Fork primitives as real architecture, not a demo trick |

**Non-cash upside:** summit access + closing dinner (Endeavor buses), 100 selected builders network, job/acquisition audition (Wonderful doubling Athens office, Greek acquisition talks live), Devin startup credits pathway, Endeavor pipeline visibility.

## What we build

**One product, one brief, one architecture.** The vertical is chosen at 19:00 Sat when briefs drop — everything below it is pre-built and legal.

```
goal (Greek, voice or text)
  → planner SLM — Oumi fine-tuned Krikri-8B (trained Sat night, ON camera)
  → 3-leaf DAG → boxd forks (2-3 workers, isolated state, visible)
  → tools bought via treg (catalog_search → catalog_get → call; cost receipts on screen)
  → Firecrawl browser (liveViewUrl — judges watch it browse)
  → deterministic core: ALL money/date/claim math in code, LLM only fills typed schemas (temp=0, citations)
  → verifier SLM + ed25519 signed action log (hash-chain + Merkle checkpoints + live `verify` CLI)
  → POLICY GATE: external writes need human approval — a judge presses it live
  → artifact out (finished, beautiful, shareable — Wiserwork standard)
  → evals dashboard: pass n/N + CI, human baseline speedup, latency, cost split, VERIFY badge
```

## Vertical decision tree (at 19:00)

| If the brief is… | We build | Sponsors it sweeps |
|---|---|---|
| Wonderful (likely: enterprise agent, ~45% voice) | **Greek voice agent** — ELTA-style workflow (auth → tool calls → write → confirm + refusal) w/ containment %, AHT, latency waterfall. Aura: outbound call to a judge's phone live | Wonderful + Oumi + fal (TTS) + Devin |
| Maritime/logistics flavored | **Claims agent** — live AIS detects ship arriving Piraeus → assemble claims pack → deterministic reconcile → signed letter (human-approved) | boxd + treg + Firecrawl + Endeavor/VF |
| Prosperty/property | **Μεταβίβαση copilot** — chases ~9 transfer docs across parties, status board, citations, deadline math, approval-gated sends | Prosperty + Big Pi + Quintessential |
| Open/civic | Procurement watchdog **only if Porios isn't competing** — diavgis MCP, single-bid patterns, signed evidence trail | Google (if closed) + Endeavor + Zindros |
| Anything else | Snap harness to it — orchestrator + gate + log + evals stay identical | All infra sponsors regardless |

## Pre-builds (legal boilerplate — done before Sat)

- `@logged_tool` decorator → signed audit entries
- Policy gate + read-only default
- `audit.py` (ed25519 chain) + `evals.py` + read-only dashboard
- Oumi recipe staged (Krikri qlora, synthetic data — NOT ILSP eval sets); GRPO config committed, executed Sat night
- Offline Demo Mode (cached deterministic run — Keel doctrine) + 90s MP4 fallback
- Voice stack e2e-tested (Pipecat + nova-3 `multi` + ElevenLabs-via-fal + Twilio)

## The one-line pitch spine

> "Consume what is generic. Build and own what differentiates you." — Koukoumidis's thesis, embodied: our 0.8B beats the frontier model on this one job, at 80ms and $0.01/1k — and every action it took is signed, gated, and verifiable.
