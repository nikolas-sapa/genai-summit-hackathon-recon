---
title: "sponsor remaining"
type: source
tags: [hackathon, genai-summit, recon, sponsors]
aliases: ["sponsor remaining"]
created: 2026-11-10
updated: 2026-11-14
status: active
---

# Deep Recon — NOFire · Endeavor · Marathon VC · Site Sweep
Gen AI Summit Hackathon, 14–15 Nov 2026, Athens LifeTech Park · Finals SNFCC 16 Nov
Compiled 10 Nov 2026 from public sources + saved decks. Parent files: `MASTER-BRIEF.md`, `sponsors-local.md`, `sponsors-infra.md`, `judges.md`.

---

## 1. NOFire AI — https://nofire.ai (SHADOW SPONSOR, deal pending)

**Status:** NOT on the public 13-partner list. Live personalized deck at `/deck?sponsor=nofire` — confirmed via llms.txt which openly lists it ("base + NOFire logo"). Diff vs `deck-base.html`: **only** the "A proposal for NOFire.ai" header + close button. NO custom overlay — unlike Cognition's deck which carries a bespoke ask (match €8.5k in Devin credits + Devin harness + €5k F&B + coding-agent exclusivity). NOFire is being pitched the standard menu: Supporter €2k / Challenge Partner €5k (max 3, gets a sponsored challenge + judge seat) / Title €15k exclusive / Technology Partner (in-kind). For a $2.5M-seed co, likeliest landing = **Challenge Partner (€5k)** or in-kind Tech Partner. If they sign as Challenge Partner, expect an **incident-response/SRE-agent challenge brief** — that's their whole surface.

### Product — Context & Control Model (CCM) for Production
- Positioning: "Safe autonomous operations for production: autonomous on-call, L1/L2 ticket resolution and incident response, within your policies and control. Every action is recorded."
- CCM = live, time-versioned model of production (every service, dependency, event, deploy, config change, failure pattern, reconstructable at any point) + runtime enforcement gating every action. "Causal, not probabilistic. Live, not snapshotted." Sits ON TOP of existing observability via APIs — no data migration, no new DB.
- **Policy model (their signature):** every agent action = **allowed / needs approval / denied** by your policy; approvals in Slack; every action recorded (which agent asked, what policy decided, who approved). Write actions held/refused when predicted blast radius exceeds bound.
- **Brig** — their **open-source agent governance layer, Apache 2.0, free**: microVM isolation sandbox, host-side observation, workload identity, policy before action. Sold commercially as "Control Room" for running your own agents under enforceable controls. **THIS IS THE HACKATHON-LEGIBLE ARTIFACT — wiring Brig into your build = open-source-flavored sponsor love.**
- Product family: AI SRE (agents take every page first), AI Incident Response (Slack-native declare/investigate/approve), Free On-Call (≤15 users, Opsgenie migration), L1/L2 ticket resolution (Zendesk/Linear/Jira via Slack, runbooks as skills), Production Context Graph, Agent Studio, Agent Memory (approved learnings + runbooks/post-mortems as knowledge).
- Infra hooks: **MCP server** for giving agents live production context; docs.nofire.ai; openapi.json; **llms.txt + Accept: text/markdown on every page — agent-friendly site, same trick as the hackathon site.** Evaluated on SREGym (independent k8s benchmark).
- Competitors they name: Resolve AI (⚠️ ALSO an Endeavor Greece portfolio co — Felix de Grey's book), Traversal, Cleric, Datadog Bits AI, Rootly, PagerDuty/Opsgenie, Anyshift.

### Founders & team
- **Spiros Economakis** — co-founder/CEO. Ex-Head of Cloud at Mattermost, ex-Lenses.io (→ Celonis), literally co-authored "Argo CD in Practice" (GitOps book).
- **Panagiotis "Panos" Moustafellos** — co-founder/CTO. 9 yrs Elastic Distinguished Engineer, ran Elastic Cloud + observability/infra products.
- **Anastasios "Tassos" Nanos** — co-founder/Chief Scientist. Director of Nubificus Ltd, creator of **urunc (CNCF sandbox)** — unikernels/container runtimes/attestation; HiPEAC member. The microVM isolation in Brig comes from his lineage.
- **Antonios Chalkiopoulos** — co-founder/COO (4th founder, less public).
- Founding eng: Stelios Charmpalis (product), George Skoumas (AI).
- **Funding:** $2.5M seed, 28 May 2026, led **Marathon VC** (partner Panos Papadopoulos on board), a16z scout fund participating. Angels: Amit Kanfer (VP Elastic), Tom Weisman (advisor). Founded 2024 (fka ZeroOps AI Inc.), Delaware HQ, ~17 staff ~76% in Greece. Hiring: Growth Marketing Lead, People/Ops.
- Marathon's thesis post ("No err twice"): AI codegen velocity has outpaced human SRE → need an AI-SRE layer with cross-domain reasoning + autonomous remediation at machine speed.

### Adjacent hackathon project (if their challenge lands, or to flatter them)
**Incident-response agent:** simulated microservice stack breaks (run it on boxd VMs for the double sponsor play) → agent gets paged, reconstructs blast radius from dependency graph, identifies culprit deploy/config, proposes remediation ranked by risk → **each action gated: allowed / needs-human-approval / denied**, approvals rendered in Slack/UI, full audit log. One graceful recovery moment = aura. Speak their language: "the blocker isn't agent capability, it's production context + control" (Economakis verbatim). Bonus: name-drop Brig or their MCP as the governance layer.

---

## 2. Endeavor — https://endeavor.org (public partner; Felix de Grey on judge/speaker list)

### What it is
Global nonprofit network for "high-impact entrepreneurs" (50+ markets, Greece chapter = first Endeavor office in Europe, est. 2012). Selects founders, gives them mentors/markets/capital access, co-invests via Endeavor Catalyst.

### Greece leadership & board
- **Panagiotis Karampinis** — Regional MD for Europe (Jan 2026) + MD Endeavor Greece since 2018; joined 2012. Made the Greek diaspora the chapter's wedge (~half the portfolio is abroad); launched the Scale Up pipeline program. Also a Panathēnea mentor.
- **Felix de Grey** — EX (Entrepreneur eXperience) Manager, AI & SaaS; summit bio: "AI and SaaS Portfolio Manager." Finds/selects/mentors AI+SaaS companies with a Greece connection. Portfolio: **Runway, Reflection AI, Resolve AI, Arena AI, Omilia**. Ex-founder Cogs AI (ADHD/autism tech, Bethnal Green Ventures, ~4 yrs) — has sat in the founder seat. Cambridge BA, LSE MSc; London→Athens 2023.
- **Board:** Chair Costantza Sbokou Constantakopoulou (Phaea/TEMES); Vice Chair Andreas Stavropoulos (Threshold Ventures, ex-DFJ); Marco Veremis (Big Pi / Upstream / Persado — bridges to Big Pi judges); Nikos Moraitakis (Workable); Alexis Pantazis (Hellas Direct); Dimitri Papalexopoulos (Titan); Eftichios Vassilakis (Aegean/Autohellas); Neil Rimer (Index Ventures co-founder); Yiannis Stassinopoulos (Viohalco); Kallissa Apostolidis (Raycap); Michael Chandris; Dean Dakolias (Rithm Capital); Ioanna Papadopoulou (EJP biscuits); Christos Konstantakopoulos (Faliro House); Lamda Dev (Odysseas Athanassiou); NBG (Pavlos Mylonas). Heavy: old-industry chairs + tech-founder operators.
- Endeavor Greece portfolio companies incl.: Reflection AI, Runway, Arena AI, Resolve AI, Omilia, Hack The Box, TileDB, Blueground, Workable, Hellas Direct, Softomotive (→Microsoft), Harbor Lab, Spotawheel, Nova Credit, Cameo, Numan, Acumino, Miroculus (→INTEGRA), Numa.

### Endeavor Catalyst Fund V (closed ~2 Nov 2026 — fresh news)
- **$320M closed oversubscribed** ($300M target); Catalyst AUM >$850M; 437 cos backed, 44 markets, 83 unicorns.
- **Greece = largest single LP bloc: $70M from 17 Greek investors (~22%)**, incl. all four systemic banks + diaspora families.
- Model: co-invests **only in Endeavor Entrepreneurs' companies**, $1–3M alongside institutional leads (Sequoia, Founders Fund etc. on same terms). $25M into 15 Greek-origin cos so far.
- Latest adds: **Arena AI** (Anastasios Angelopoulos — $200M round @ $3.2B) and **ResolveAI** (Spiros Xanthos — AI incident diagnosis/resolution — note: Endeavor-backed direct NOFire competitor).

### How selection works (what impresses them)
- Pipeline 12–18 months: local scouting → Local Selection Panel → **International Selection Panel (ISP)** — 2.5 days, 3× one-hour interviews with pairs of global panelists (founders/investors/c-levels) → **unanimous vote required**. Acceptance ~1.6–2% (81 cos selected globally in 2024). Scale Up program = earlier-stage feeder.
- **Selection Triangle:** (1) **Entrepreneur first** — ambition, transparency, role-model/multiplier DNA ("will they pay it forward and inspire the next generation"); (2) **Business** — can it credibly scale 10x from here (defensibility, growth strategy); (3) **Timing** — at an inflection point, market ripe NOW.
- Translation for the room: de Grey judges through a "could this team compound into an Endeavor Entrepreneur" lens — named persona, real pain, honest scope, 10x-shaped ambition, founder quality over demo flash. He talks to Runway/Reflection/Arena founders daily: zero hype tolerance, admit limitations.

---

## 3. Marathon VC — https://marathon.vc (NOT a sponsor — in the room only via NOFire)

- Athens seed/deep-tech VC, founded 2017 by **George Tziralis** + **Panos Papadopoulos** (ex-Bugsense → Splunk; built Greek founder community since 2007). **Alex Alexakis** made Partner with Fund III. Fund III: **€75M** (closed May 2025, EIF+HDBI LPs); AUM ~€175M. Self-described "day one partners," first-money-in, non-consensus.
- Thesis (Papadopoulos, verbatim-ish): "founders who do something hard in important markets — hard because of unique knowledge (PhD) or high agency (regulated/overlooked industry). Not a sector fund — we back people changing their sectors." Early defense-tech (Delian/Lambda Automata pre-Ukraine-war).
- Portfolio: NOFire, Causaly, Hack The Box, LearnWorlds, Delian Alliance Industries, Augmenta (→CNH $110M), Lenses (→Celonis — Economakis's old employer, connective tissue), Ariadne, PolyModels Hub, Bota Systems, SMPnet, Progressive Robotics, Archiboost AI.
- **Hackathon relevance:** zero direct presence (not on site, not in summit speaker list). Presence = NOFire shadow sponsorship + Papadopoulos's board seat. If NOFire signs as Challenge Partner, Marathon's DNA is in the room by proxy: they reward hard-tech depth (runtime, causal models, k8s-native) over demos.

### VC/angel presence sweep (full picture around the event)
**Confirmed present:** Big Pi Ventures (partner + judge Kalliagkopoulos; also Endeavor board via Veremis), VentureFriends (Apostolakis, speaker), Endeavor (partner + de Grey), Northzone (Pantazi, talent partner), ex-Techstars (Bouloutas), ex-Chapter One (Mazarakis), Bernitsas law firm (speaker; runs "Building, Funding, Scaling and Exiting in the AI Era" panel). Enterprise checks in the room: Piraeus Bank (12 mentions, summit sponsor), Kyndryl, Deloitte, EY, Microsoft, MSD, Viohalco, Olympia Group, PM Mitsotakis.
**Checked, ABSENT:** Marathon VC (except NOFire proxy), Genesis Ventures (the one "Genesis" hit is crypto DCG), Metavallon (only as historical Prosperty investor), Uni.Fund, Eleven Ventures, 24 Media, Velocity Partners, OpenFund, HDBI, Diorama. Nobody from NOFire's team or Karampinis on the summit speaker list either.

---

## 4. Site sweep — diff vs first check

- **Partner list: still 13, unchanged** (Quintessential, Wonderful, Big Pi, fal, Prosperty, boxd, Firecrawl, treg, Wiserwork, Endeavor, Oumi, Always Online, Crowdcruit). NOFire + Cognition remain shadow sponsors — llms.txt still advertises both personalized decks, so both deals are still open/pending.
- **/privacy + /terms: still 404** (both were 404 at first capture too). Sitemap lists them with lastmod 2026-10-26 — pages existed ~2 weeks ago, since pulled; Wayback has no snapshot → content unrecoverable. **No IP clause, code-review requirement, submission format, or judging rubric exists anywhere public.** The "IP yours" line in MASTER-BRIEF is unverifiable from current sources — flag it; only written rules are the FAQ (boilerplate allowed; build starts Sat 12:00; "judges weigh what was made during the build window"; submissions close Sun 18:00; finalists 21:00 Sun).
- **Luma: EVENT NOW FULL** — 162 registered vs ~100–120 target (oversubscribed, waitlist only). Ticket types: Standard + Mentor, both approval-gated. No new rules on Luma.
- llms.txt reconfirms: no hour-by-hour schedule published ("do not quote one"); every page serves `Accept: text/markdown`.
- NOFire's own site is agent-native too (llms.txt, openapi.json, /md prefix, MCP server) — they think exactly like Abed's site design. Cheap wink available.

## 5. Play implications
1. **If a NOFire challenge brief drops at kickoff, it's the single best-aligned sponsor brief in the room** for an agent-infra build: policy-gated remediation agent on a live breaking stack. Pre-wire: allowed/needs-approval/denied action model + audit log + Slack approval UI + Brig or MCP mention.
2. Endeavor/de Grey scoring = founder-potential lens: pitch the team + the 10x-shaped company hiding inside the project, not just the demo. Endeavor Catalyst is flushed with Greek LP money right now (Nov 2 close) — Greek-origin founder momentum is his exact brief.
3. No new sponsors since first check; Cognition still unsigned → the Devin-harness exclusivity window is still open. Building visibly on Windsurf/Devin remains live.

---

## Nov-14 additions (freshness sweep)

Partner list grew 13 → 16. Three names added publicly ~Nov 12:

- **Google** → `sponsor-google.md` — in-kind "AI inference" credits on /credits; Google Cloud Day Athens ran Nov 10, same-week ecosystem push; likely DevRel-staffed table.
- **Cloud Office** → `sponsor-cloud-office.md` — Premier Google Cloud Partner (Sofia HQ, Athens–Marousi office); hiring + market-entry play, no credits.
- **SHAKE talent up** → `sponsor-shake-talent-up.md` — "Hackathon Hiring Partner"; Aspasia Gkotsi's boutique recruiter routing builders into Welcome Pickups/HarborLab-orbit clients.

Notes: `/deck` now 404s in markdown mode (HTML still 200) — decks may be mid-pull; llms.txt still advertises Cognition + NOFire personalized decks, so both shadow deals read as still open.
