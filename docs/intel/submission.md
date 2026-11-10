---
title: "suUmission"
type: source
tags: [hackathon, genai-summit, recon, intel]
aliases: ["suUmission"]
created: 2026-11-10
updated: 2026-11-10
status: active
---

# What Judges Actually REVIEW — Submission Surface Analysis
Gen AI Summit Hackathon, Athens, 14–15 Nov 2026 · compiled 11 Nov 2026
Thesis: **"craft" is judged through artifacts, not the demo alone.** The demo gets you remembered; the repo/README/commits/video/profile get you defended in the deliberation room after you've left the table.

---

## 1. Submission format — what the terms actually say

**Verified against live `hackathon.polymath42.com` (11 Nov):**

- `/terms` + `/privacy` are **live now** (both "Last updated 9 November 2026"; sitemap lists them; local copies `deep/fresh/terms-extracted.txt`, `privacy-extracted.txt`). `/terms` returns 404 under `Accept: text/markdown` but 200 as HTML — cosmetic quirk, page is real.
- **Terms §3–5:** build starts Sat 12:00, "projects substantially built before then may be disqualified"; OSS/APIs/partner tools allowed — **"Credit what you did not build"**; you own IP; submission grants licence to show "name, description, screenshots, demo and video" + team names.
- **Privacy (the smoking gun for format):** "Event details: your team, the project you build, **your submission (repository, demo, video, slides)**, judging results and any prizes."
  → **The submission package = repo + demo + video + slides.** All four are enumerated as collected data. No weights are published.
- **No Devpost, no /submit endpoint.** Probed: `/submit /projects /teams /submissions /results /podium /account /login /profile /dashboard /api/*` → all 404. Submission mechanics are unpublished — they will be announced at kickoff (probably via the site's own profile system, see §7).
- **Deadline:** submissions close **Sun 18:00** (deck + schema endDate); finalists 21:00; finalists pitch 5 min on Summit stage Mon.
- **Build-window proof is enforced socially:** "Judges weigh what was made during the build window" (FAQ) — your commit timestamps ARE the evidence. This is the one place git history is load-bearing in the rules themselves.

**Athens/Greek submission norms (precedent scan):**

| Event | Submission surface |
|---|---|
| **LifeHack Athens @Panathēnea** (same venue, same co-hosts, May 2026) | Live demos + next-day stage pitches. No Devpost. Sponsor judges their own track. |
| **Florent × Panathēnea AI hack** (May 2026, Zone01) | Live judging + public repo expected (winner Keel has a public repo — analyzed §3). |
| **GenAI Summit 4 hackathon** (Nov 2025, SNFCC) | 6h side-room, live demos to jury. |
| **MATLAB hackathon NTUA, The Merge 2026** | Devpost — but student/corporate events, not this org's style. |
| **Abed's own events** (Wordware×OpenClaw SF, Cursor×a16z, Moltathon ATX) | Live demo only — he won with working software + screenshots in a thin README. |

**Read: this org is live-demo-first.** The Devpost-style form doesn't exist here; the profile/badge system + the repo are the written record. But since the privacy policy enumerates repo+demo+video+slides as "your submission," produce all four — the profile system likely ingests them on Sunday.

## 2. What the organizer looks at (Abed's own fingerprint)

Abed's own hackathon repo (`abed42/Supabase-YC-hackathon`) is the tell: **README = title + team name + 4 screenshots. Zero prose.** 16 commits in 2.5h with terse lowercase messages ("speed", "positioning", "Make messages dynamic"). His winners (Claweyes, Origami) were demoed live — the artifact trail is thin because the demo carried it.

But that's the competitor's minimum, not the bar to beat. His judging vocabulary (dossier `deep/judge-abed.md`): "maker visible in the work," microcopy as "anti-slop certificate," honesty about what's stubbed. A README that *over-documents* with buzzwords reads as slop; a README that's honest, scannable, and screenshot-forward reads as craft.

## 3. README spec — the Keel model (Athens's own winning standard)

`ertval/keel-multi-agent-pipeline` (1st place, Florent × Panathēnea, May 2026 — same ecosystem, same judge archetypes) is the canonical craft README in this scene. Its structure, adapted for the policy-gated agent harness:

```
# <name>
one-line what + for whom          (Keel: "A demurrage reconciliation tool for
                                    maritime charterparties. One analyst uploads…")
[badges: Python/TS, key deps only — not a wall]

## What this is not          ← THE signature craft move. Keel itemizes every claim
                               the code doesn't support, each with file:line cites
                               ("No authentication… proxy.ts is a UI convenience
                               whose own first line says it is not authentication")
## Honest status by subsystem ← table: works / works-but-unexercisable / not built,
                               each row with code refs. Judges cross-check ONE row.
## Architecture               ← the text diagram from agent-architecture.md §0,
                               plus ONE sentence per load-bearing decision
## Canonical scenario          ← fixture with REAL numbers verified via real output
                               ($62,000 + $50,000 = $112,000, verified by curl paste)
## Measured results            ← the beat-frontier table (SLM vs frontier:
                               accuracy · p50 · $/1k), cost ledger totals
## Run it                      ← prereqs, 3 commands to reproduce, env vars listed
## Tests / evals               ← real output including expected failures, quarantined
## Security posture & limits   ← the policy gate, threat model, what it does NOT stop
## Known limitations           ← honest, docstring-referenced, numbered
## Repository layout           ← tree with per-dir/per-file comments, DEAD code
                               flagged honestly (Keel marks database.py "# DEAD")
## Built with                  ← Devin sessions linked, tools credited (terms §3
                               requires: "Credit what you did not build")
```

**Craft signals this emits, by judge:**
- **"What this is not" + honest-status table** → Zindros (checked-not-trusted), Quintessential ("maker visible," last-mile honesty), Abed (anti-slop, no overclaiming). It also pre-answers every "is this real?" probe.
- **File:line citations everywhere** → invites inspection; says "we know exactly where the bodies are." Costs nothing, reads like surgical confidence.
- **Real command output pasted, including failures** → Gianitsos/Koukoumidis (measured, reproducible, evals-first).
- **"The dollars never come from the model"**-style line → Keel's wrapper-thinness rebuttal. Our equivalent: *"The LLM proposes; the policy gate disposes. No irreversible action executes without a signed log entry and a human or policy decision."*

**README anti-patterns for this room:** badge walls, marketing prose, feature lists exceeding the honest-status table, TAM/business framing (VC judges get that live, not in the repo), AI-generated docs smell (docs written by a model that never read the code — Quintessential literally published "the work isn't in the generation, it's in the curation").

## 4. Code-review likelihood — what gets inspected in 5 minutes

**Who reads code:** Zeibekis (Wiserwork CTO — "inspects plumbing, no thin wrappers"), Koukoumidis (Oumi CEO — eng credibility, notices sloppy plumbing), Kopanidis (Quintessential systems architect — "I mostly break things"), Zindros, Gianitsos, Mene (Anon/Sierra — knows where agent bodies are buried). That's 6+ credible code-readers on a ~15-judge panel. Assume the repo IS read.

**The 5-minute inspection path (what they open first):**
1. `git log` — before any file (see §5)
2. Top-level tree — is there a legible `coordinator/ workers/ policy/ ledger/ eval/` structure, or a monorepo of vibes
3. **The policy gate implementation** — our architectural claim. They'll open `policy/` or wherever the gate lives first because the demo claims it. It must be real code with real enforcement points, not a prompt saying "be careful." Quintessential's published doctrine (scoped creds, tool allowlists, writes-only-through-gate, audit trail) is the checklist they'll pattern-match against.
4. **Wrapper-thinness test:** what does the agent do that isn't one LLM call? Show: DAG planner (SLM), verifier (SLM), deterministic ledger/gate logic in pure code, tool adapters with typed schemas. Line to have true: *the LLMs decide, plain code enforces.*
5. Error handling — grep-able evidence: retries with bounds, timeouts on every external call, the 402-budget path, failure → gate escalation. One honest `// fallback:` comment beats silent swallowing.
6. A random file pull — does the rest match the front door?

**Make it read well in 5 min:**
- Entry point discoverable: `main.py`/`coordinator.py` at a predictable path, README's repo-layout section names it.
- Module docstrings that say the true thing ("DEMO STUB — not authentication" beats a judge discovering it).
- Typed contracts between components (Pydantic/zod schemas at the LLM boundary) — the single highest signal-per-line craft marker for this panel.
- No dead imports, no `node_modules` committed, `.env.example` present, `.env` gitignored (judges flag committed secrets as instant disqualifiers of craft).
- One comment at each non-obvious constraint ("hibernate watches net traffic, not CPU — hence the heartbeat") — teaches the mechanism, shows we hit the wall and understood it.

## 5. Commit history — yes, it matters doubly here

Two distinct functions at THIS event:
1. **Build-window proof.** Terms/FAQ make the 36h window the scoring boundary; timestamps in `git log` are the only machine-checkable evidence. MLH's organizer guide literally tells judges to check: "Did they start before the event? Is it one big commit?" A repo initialized Sat 12:05 with steady commits through Sun 17:xx IS the compliance artifact.
2. **Craft narrative.** Judge-facing finding (corroborated in judge write-ups): "fifteen commits that narrate a story" beats "Initial commit + Published your App." Judges read the log as the build's timeline — they can see where you hit walls and recovered.

**Spec:**
- Init the repo **Sat ~12:05** (not before — a Fri-night repo with Sat-morning force-push is an anti-signal; boilerplate stays in a separate pre-built skeleton repo, clearly labeled).
- Commit every 30–60 min of real work; messages = short imperative, human-voiced, occasionally wry (Abed's own style: "speed", "positioning"). Never "wip", "fix", "final", "update" walls.
- **Devin PRs as receipts:** where Devin wrote a component, let the PR show it (`devin-ai-integration[bot]` authored PRs, merged, with the session link in the PR body). This is *positive* evidence — "built visibly by an agent" is a stated winning-formula line (MASTER-BRIEF #7) and manufactures the Cognition case study. Human commits interleaved show direction/curation (the maker stays visible — Quintessential's exact test).
- Do NOT squash everything into one commit before submission. Do NOT push after 18:00 (post-deadline pushes are a listed cheat-check flag).
- Repo public from first commit or by Sun 15:00 latest — judges may pull during the afternoon.

## 6. Video — yes, part of submission

Privacy enumerates "video" in the collected submission package; terms license the org to show "demo and video" in promo. No duration/format published.

**Spec (Devpost-derived norm + stage-realism):**
- **90 seconds** is the sweet spot (60–120s range; hackathonplaybook standard is 60–90s). Judges rewatch during deliberation — it must tell the story without you in the room.
- Content: 10s problem → 70s live agent run (screen record the actual UI: goal in → DAG spawns → treg purchase receipt → browser liveView → policy gate APPROVE → signed log → cost ledger) → 10s "what's real/what's next."
- Real-time footage, not renders. The honest edge is a feature (Abed demos himself constantly; fake-it tells are obvious).
- Host unlisted/public on YouTube (or Vimeo); link at top of README + in the profile.
- **Also record the fallback video Sat night/Sun early** (agent-architecture.md already prescribes "pre-recorded 90s video of full run" as venue-wifi last resort) — same asset can serve both purposes. Two takes: wifi-degraded-real and clean-run.
- fal credits can garnish the hero/intro frame, but the run itself must be real — a fal-rendered "demo" is exactly the slop tell.

## 7. The badge/profile system — a live submission surface

- `/badge/<slug>` is live per registrant: animated draggable card, "You're in", downloadable **6s badge video (9:16 + 16:9)** for socials.
- Terms/privacy: every applicant gets a profile + `/badge/<name>` page showing "name, role, skills, links, team, **projects and results**" — public, "visible to participants, partners, **judges, recruiters** and anyone with the link." Profiles persist post-event as an engineering portfolio.
- **Implication:** the badge/profile page is where Sunday's submitted project lands in the org's own system — it's the Devpost-page-equivalent here. Populate it: project name, one-line description, links (repo, video, live demo), the badge video shared on socials (the org literally built the 6s clip to be posted — posting it is free aura surface and pre-event visibility).
- Our badge slug: TBD — `badge/nikolas`, `badge/nikolas-sapalidis` 404 (not yet created or different slug). Confirm the actual slug at check-in and fill the profile the moment project fields exist.
- Recruiters see it too: Quintessential is hiring "AI-first, loves craft" builders and gets opt-in CVs — the profile + repo IS the interview.

## 8. Slides — the fourth artifact

Privacy lists "slides" in the submission package. Given "not a pitching competition," slides are a *support* artifact: 4–6 slides max, likely only seen if judges request or for Monday's stage backdrop.
- Slide 1: name + one-liner + hero screenshot
- Slide 2: architecture (the text diagram, prettified — same content, no new claims)
- Slide 3: the numbers (SLM-vs-frontier table, cost ledger, before/after timing)
- Slide 4: what's real / what's stubbed (the honest-status table condensed)
- Slide 5: continuation path (Panathēnea rewards follow-on stories — RNAgents went hackathon→lab)
- Keep it exportable as PDF; no deck-first energy anywhere else.

## 9. The judge's <10-minute path — ordering everything

Design the artifact stack so a judge starting cold at the repo lands on proof within minutes:

| t | Surface | What they see |
|---|---|---|
| 0:00 | Profile/badge or repo link | Name, one-liner, links |
| 0:30 | README top | What/for-whom + "What this is not" + honest-status table |
| 2:00 | Architecture diagram + canonical scenario | The mechanism + verified numbers |
| 3:30 | `git log` + policy gate file | Build-window proof + the real enforcement code |
| 5:00 | Tests/evals output, cost table | Measured claims, reproducible |
| 6:00 | 90s video | The end-to-end run they missed live |
| 8:00 | Repo layout + "Built with" | Credit, Devin PR trail, where to ask questions |

Rule: **every claim in the README is checkable in one click** (file:line, PR, curl output, video timestamp). Zindros's bar — "checked, not trusted" — is the design principle for the whole package.

## 10. THE CHECKLIST — what to produce beyond the working demo

**Build-window (Sat 12:00 → Sun 18:00):**
- [ ] Public repo initialized Sat ~12:05; steady commits all weekend; zero pushes after 18:00
- [ ] `.gitignore` from minute one; `.env.example` committed; no secrets in history (rotate anything that touched a commit)
- [ ] Devin-built components land as PRs w/ session links (visible "built by agent" trail)
- [ ] Module docstrings that tell the truth; typed schemas at every LLM boundary
- [ ] Policy gate as real enforced code + hash-chained signed log (the artifact Zindros/Quintessential will open first)

**By Sun ~15:00 (before final rehearsal):**
- [ ] README per §3 spec — "What this is not" + honest-status table + verified-numbers scenario + cost/eval tables + repo layout + credits
- [ ] 90s demo video recorded (clean run), hosted, linked top-of-README — doubles as wifi fallback
- [ ] 4–5 annotated screenshots (DAG view, gate APPROVE, ledger, browser liveView)
- [ ] Slides: 5 max per §8, PDF-exported
- [ ] Profile/badge page populated: project, links, description; badge video posted on socials

**By Sun 18:00 (submission):**
- [ ] Whatever form the org announces at kickoff — assume it takes repo URL + demo link + video URL + slides + description (privacy policy's enumeration); have all five ready by 15:00 so the submission is copy-paste, not creation
- [ ] Honest limitations written down (same content in README + submission form — consistent claims)
- [ ] One team member owns the submission form; another owns final repo hygiene pass (dead code flagged, stray files out, README renders)

**The meta-check:** after submitting, read the package as a stranger — repo → README → git log → video. If any claim requires you present to defend it, fix the artifact. Judges pick winners after you've left the room; the package argues alone.

---
*Sources: live hackathon.polymath42.com (/, /terms, /privacy, /badge/*, sitemap, /submit probes — 11 Nov); luma.com/x1wxi5sn; deep/rules-deck.md, deep/judge-abed.md, deep/judge-tech-trio.md, deep/sponsor-quintessential.md, deep/org-panathenea.md, deep2/challenge-mechanics.md, deep2/agent-architecture.md; github.com/abed42/Supabase-YC-hackathon; github.com/ertval/keel-multi-agent-pipeline; MLH organizer guide (cheat-check); hackernoon "The Git Log Never Lies"; hackathonplaybook.dev submission guide; Devpost help docs.*
