---
title: "award patterns"
type: source
tags: [hackathon, genai-summit, recon, intel]
aliases: ["award patterns"]
created: 2026-11-10
updated: 2026-11-10
status: active
---

# Award Patterns — Sponsor-Side Prize Playbook
## Gen AI Summit Hackathon · Athens LifeTech Park · 14–15 Nov 2026

Event context (from hackathon.polymath42.com + Luma): 36h, ~100 selected builders, teams 1–5, theme = "agents that take a goal and deliver real work end-to-end." Judged on **usefulness, craft, aura points** — "make it work and show us the demo, not a pitching competition." Cash prizes €5k/€2.5k/€1k + partner awards; finalists pitch on GenAI Summit main stage at SNFCC (Mon 16 Nov). Confirmed partners include **fal, Firecrawl, boxd, Oumi, Wonderful**.

---

## 1. fal — "Best Use of fal"

**Hackathon history (dense, systematic):**
- **{Tech: Europe} circuit** (Amsterdam, London, ×VEED London): recurring "Best Use of fal" award. Winners:
  - **Lantern** (London, ×VEED): overall winner + Best Use of fal — scrapes old property listings, fal turns photos/floor plans into a video walkthrough briefing firefighters before arrival.
  - **Explodify** (London): **$1,000 fal credits** — CAD file → exploded-view product video, Kling via fal reskins renders with photoreal materials.
  - **Tona** (Amsterdam): fashion try-on, fal image models superimpose clothes on your photo.
- **ElevenLabs × a16z Worldwide Hackathon** (Feb 2025, 9 cities): **Global fal Prize track = $24,000 in fal credits** for "best use case of generative media models via fal API."
- **Nano Banana Hackathon** (Cerebral Valley × Google DeepMind, Sep 2025): partner; every winner package included **$1,000 fal credits** + a special prize for outstanding fal usage. 832 submissions.
- **fal × Sequoia 72-Hour Video Hackathon** (Jul 2026, virtual): their flagship owned event — **$150k credit pool**, supported by DeepMind, xAI, Kling. Cannes-for-builders framing: AI-native storytelling.
- **HACK THE FLUX Berlin** (Black Forest Labs × fal × Merantix): evening hack, **$1,000 fal credits**.
- **Uncanny Valley Fest at YC HQ** (Nov 2025, Machine Cinema × Koyal × fal × YC): 200 people, short films in 12h, 3 categories; prizes incl. YC partner interview.
- Older: Poe API Hackathon (2024), Emergency GPT Builders (2023, $1k fal credits per podium spot); AGI House ImageGen Hackathon (2023 — co-founder Burkay Gur in the room, pre-sponsorship era). Partner slots: Gemini 3 SuperHack, HackBarna, SIDE QUEST (e2vc × Arcadia × fal, Istanbul), a16z AI Infra Day.
- YC relation: not a YC hackathon sponsor per se — fal runs a **YC Bookface deal** ($50k serverless or $20k model API credits) and co-hosts events *at* YC.

**Prize amounts:** $500–$1,000 credits typical for single-day sponsor slots; $24k for global tracks; $150k for owned flagship. Matches the $500–4K hypothesis at the low/mid tier.

**Community-growth charter:** literally a job posting — **"Community Growth @ fal"** (Marketing, SF, $165–200K) owns "community growth across events, hackathons, creator competitions, webinars, Discord, Reddit, demos." Plus an Event Marketing Manager role owning hackathon execution. Stated goal: *"find and engage the best builders in generative media, give them reasons to keep building with fal."* Credits → Startup Program ($1k→$5k for EU/Asia teams) is the retention funnel.

**What wins (pattern across 3 winners):** generated media is the **visible payoff of the demo inside a useful product** — not an art piece, not a backend call. Lantern = video brief in an emergency tool; Explodify = video in a CAD workflow; Tona = image in a consumer app. Utility frame + live generation + novel model routing (Kling/Veo/image-edit via one API).

**Show their table:** an agent whose output IS media generated live during judging — e.g., agent researches a problem → produces a narrated video brief or generated imagery as deliverable. Bonus: multi-model pipeline through fal's one API, and a credible "we'd keep building" story (their funnel metric).

---

## 2. Firecrawl — "Best Use of Firecrawl" / best agent

**Hackathon history:**
- **Platanus Hack ft. Firecrawl** (Mexico City 2026, 36h, 100 hackers, hosted by Fintual): Firecrawl as named co-sponsor. **Best Use of Firecrawl → Sendero**: missing-persons research platform; 3 parallel agents scraping government databases (messy HTML, PDFs, images), social, news. Judge's wording: *"the team that used it the most — and generated the most impact with it."* Team deleted an entire pipeline stage (scraper+LLM guessing sources) when Firecrawl search returned real articles as markdown in one call.
- **Build Club × SXSW Sydney** (Nov 2025): **$1,000 dedicated Firecrawl track prize** + 20,000 credits as a universal perk.
- **TillyHacks** (DMV, first edition): Best Use of Firecrawl → **Medstack**.

**"Best agent" pattern:** Firecrawl's brand is agents-as-customers — they ran the viral YC job ad hiring an *AI agent* for $10–15k/yr and floated $1M for three agent "employees." At hackathons they reward **usage depth × impact**: agents that genuinely need live web data, call scrape/search/extract/parse at runtime, and collapse what would've been a bespoke scraping pipeline into one API call.

**Show their table:** an agent consuming genuinely hostile real-world sources (Greek gov portals, PDFs, mixed-language sites are ideal — mirrors Sendero's messy gov DBs) with Firecrawl calls visible in the demo; be ready to state call volume ("we fired N scrapes/searches"). Usage + social/real impact is their exact judging language.

---

## 3. boxd — what they'd reward (they've never sponsored; they *won*)

**Their win — Anthropic × Whale "Build Local"** (Amsterdam, 25–26 Apr 2026; 100 builders from 600+ applicants; Raspberry Pis as prizes):
- Co-founder **Hidde Kehrer's** team (w/ Dhruv Ghulati, ex-Adyen; Diala E., Hummingbird) won **Best Technical Build** with **Safethread**: a bidirectional Amber-alert system for war zones (War Child brief). Push → SMS (Twilio) → **Bluetooth mesh (forked bitchat)** fallback when networks die; a triage agent clusters inbound reports (alert × region × time), a Claude agent reasons over the cluster, acts on low-risk, escalates high-stakes to a human operator.
- Other winners at that event: Mark (fully offline emergency assistant on quantized Gemma, on-device RAG+maps), SAFER (vibecoded women's-safety routing — no engineer on team), a War Child donor-comms tool ("Real Ones" prize = real-world viability).

**Taste proxy:** the winning project tells you their taste — **infrastructure-grade technical depth (mesh networking, graceful degradation, agent triage) aimed at real-world/community utility**, not demo polish. Their product thesis reinforces it: persistent KVM microVMs (<10ms boot, <200ms live fork incl. memory/processes, snapshot/checkpoint/hibernate), "the agent lives inside the machine," agent-per-machine parallelism. Early-stage: €2M pre-seed Sep 2026 (BlueYard, Antler, OVNI, s20, Script), Amsterdam, founders Michiel Voortman / Laurentiu Ciobanu / Hidde Kehrer. €30 free credits/new account.

**Show their table:** use their primitives *as architecture*, not hosting — fork a machine mid-run to branch two agent approaches, checkpoint before a risky agent action, N agents on N isolated machines with per-machine live URLs. Bonus resonance: resilience/offline/underserved-community angle (their winning taste) and EU-sovereign/self-host mentions (they're a European sovereignty story).

---

## 4. Oumi — "Hack with Oumi" (fine-tunes, not calls)

**Their events:** own problem-statement track (github.com/oumi-ai/hack-with-oumi) at **Nebius.Build SF** (Mar 15, 2026, Cerebral Valley/Shack15) and **Eclipse 6.0** (Apr 4–5, ACM Thapar). Earlier: WeMakeDevs **AI Agents Assemble 2025** Oumi track — cash prizes (3rd = **$3,000** → **Vriksha AI**, a no-code node UI for Oumi SFT→RL pipelines); Feb hackathons advertised $30k pool.

**Stated requirements/criteria (their repo):**
- **Must use Oumi to fine-tune** the models + star the GitHub repo (community-growth KPI baked into rules).
- Track theme: **SLMs (<~10B) for voice agents** — STT → SLM agent → TTS; domain unrestricted but "specific, realistic use case."
- Judged on **Creativity, Real-world impact, Technical quality**. No evals required, "but latency benefits should be clear." Open-weight models encouraged.
- They hand you a Pipecat starter template and a menu of SLM sub-roles: guardrail/judge, query rewriter, execution router, retrieval router, model router, planner, verifier, executor, memory manager.

**What wins:** an actual artifact — **weights trained during the event** and running live in the demo. Nebius.Build 1st place overall (Injester) shows the room's bar: agentic infra with a working loop. For the Oumi track specifically, modular multi-SLM designs (specialized SLM per agent role) are exactly what their brief is fishing for.

**Show their table:** fine-tune a small model on Oumi *during the hack* (Greek-domain dataset = instant differentiation nobody else will have), show the training run and the tuned model driving one agent role live (e.g., SLM router/verifier in a voice agent). Star the repo, document the tune, mention latency numbers.

---

## 5. Wonderful — doesn't do hackathons (yet); think "Best Enterprise Agent"

**Sponsorship record:** zero hackathons found. Their motion is enterprise stages and award ceremonies — PyData Amsterdam (Platinum), AWS Summit Dubai (Gold), HK FinTech Week (Gold), Tech Show Frankfurt, DALA Awards (Premier), Agentiq World Amsterdam (keynote+demo+roundtable), Portafolio AI Day Bogotá, Poland Tech Week GTM talks. $550M Series C at $5B (Sep 2026); HQ Amsterdam, founded Tel Aviv; 35+ markets; **wedge = agents for non-English-speaking markets** (voice/chat/email, >80% resolution claim), forward-deployed engineer pods.

**Agent Builder** (launched Jan 23, 2026, co-built with Anthropic): an agent that autonomously builds/tests/refines other agents — ingests policy docs, KBs, call recordings, iterates to production readiness; –50% time-to-production, –20% early-prod issues; chat-based control for non-technical teams.

**What they'd reward (inference, high confidence):** enterprise-plausible agents — a named business workflow (customer service, claims, compliance, scheduling), grounded in real org documents, with governance/escalation behavior and measurable resolution. Their founding thesis makes **Greek-language voice/chat agents** the single highest-resonance demo at this event — local-market enterprise agent IS their origin story.

**Show their table:** a vertical agent with an identifiable enterprise buyer, real document grounding, escalation-to-human path, and Greek-language fluency. Framing the build as "an agent that configures/evaluates other agents" mirrors Agent Builder directly.

---

## 6. Cognition / Devin playbook (reference — not a listed partner, but the strongest codified "sponsor award" playbook in the space)

- **Lux Capital AI Agent & Infra Hackathon** (NYC, Aug 2025, w/ Modal + AWS + Ramp): **"Best Agent Hack sponsored by Cognition"** — 1st: $3,000 + 1yr Windsurf Pro + 1yr Devin Team (~$9k). Criterion verbatim: "any project building an agent or a custom MCP client or server."
- **Hack the North 2026** (Waterloo, 347 teams): **"Cognition: Best Use of Devin"** → **God's Plan** (3D god-mode Toronto sim, thousands of autonomous AI residents). Devpost breakdown of the Devin usage: code review, Vercel deploy, SPA routing, custom domain/DNS — and crucially **Devin opened the deployed app in a browser and caught a frontend-backend disconnect** a HTTP-200 check would miss. Judges rewarded *Devin as a real teammate across the lifecycle*, not LoC farmed.
- **Oxford FinHack** (Nov 29, 2026): no-code-needed, business students + engineers, "Devin credits to outstanding teams" — Devin positioned as the engineer for non-engineers.
- **Dhaka** (community program): Devin meetups + community hackathon on Devin Desktop; **Agentic Hackathon** nationwide (online round → Dhaka finals, ~$480 cash) — judged on problem selection, execution, **working demo**; "encouraged to use Devin during the online round."
- So: **not** "most PRs merged." Evidence says the winning pattern = a shipped product where Devin demonstrably did real work — parallel sessions on separate features, deploy + browser-verify, tickets cleared is supporting evidence, not the award itself.

---

## 7. Pattern synthesis — (a) creative API use · (b) visible product in demo · (c) post-event usage potential

| Sponsor | (a) Creative API use | (b) Visible in demo | (c) Post-event pull | Dominant |
|---|---|---|---|---|
| fal | novel multi-model routing | **media IS the demo** | creators keep generating (credits funnel) | **b > a > c** |
| Firecrawl | endpoint depth (search/extract/parse) | live scrape of hostile sources | agents keep crawling | **a = c > b** |
| boxd | fork/snapshot/parallel-machine primitives | per-agent live URLs | persistent machines retained | **a (technical depth)** |
| Oumi | modular SLM-per-role design | tuned model running live | starred repo + real tune | **a + artifact** |
| Wonderful | agent-builds-agent pattern | enterprise workflow demo | real buyer/deployment path | **c > b** |
| Devin (ref) | lifecycle breadth (plan→verify) | deployed URL verified live | product subscriptions | **b > a** |

**Composite play (one build can sweep multiple awards):** an agent that pulls hostile real-world sources via **Firecrawl** (Greek gov/NGO data — Sendero pattern), reasons with a domain **SLM fine-tuned on Oumi during the event**, produces a generated-media deliverable via **fal** (Lantern pattern), runs as N parallel agents on **boxd** machines with fork-branching shown live, was built/deployed/verified by **Devin**, and is framed as a sellable **enterprise agent for the Greek market** (Wonderful). Literally Lantern × Sendero fused — both already proven winners of exactly these awards.

**Suggested award names matching each sponsor's documented vocabulary:**
- "Best Use of fal" ($1–2k credits is their standard single-event number)
- "Best Use of Firecrawl" / "Best Agent" ($1k track + credits for all)
- "Best Technical Build" (boxd — the exact award they themselves won)
- "Best Fine-tune / Hack with Oumi" (requirement: Oumi-tuned model + repo star)
- "Best Enterprise Agent" (Wonderful — multilingual, production-path framing)
