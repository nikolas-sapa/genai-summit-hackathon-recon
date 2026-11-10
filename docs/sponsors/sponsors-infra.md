---
title: "sponsors infra"
type: source
tags: [hackathon, genai-summit, recon, sponsors]
aliases: ["sponsors infra"]
created: 2026-11-10
updated: 2026-11-10
status: active
---

# Sponsor Recon — Gen AI Summit Hackathon (Athens, 14–15 Nov 2026)

Compiled 10 Nov 2026. Event facts: 36h hackathon, Athens LifeTech Park, ~100–120 selected builders, teams 1–5, finals on GenAI Summit stage at SNFCC Mon 16 Nov. Judging: usefulness, craft, "aura points". Organizer contact: Abed Hamami (abedhamami42@gmail.com). Co-organized by Panathēnea.

Key structural fact from sponsor deck (`/deck`): partner tiers = Supporter €2k, Challenge Partner €5k (max 3, brings a sponsored challenge + judge), Title €15k, and **Technology Partner = credits/licences contribution** — meaning infra sponsors like fal/Firecrawl/Oumi are almost certainly there as tech partners handing out credits and measuring platform usage ("post-event report including actual usage numbers on your platform"). Building visibly on their stack is literally what they paid for.

---

## 1. fal — https://fal.ai

**What:** The generative-media inference cloud. One API / one credit balance across 1,000+ image, video, audio and 3D models — open- and closed-weight (incl. OpenAI Sora, DeepMind Veo, FLUX, Kling, MiniMax, Seedance, Grok Imagine). Pay-per-output prepaid credits (per image/MP, per second of video, per request). Also fal Serverless = deploy your own model on their GPUs ($2.49–4.50/H100-hr), billed per second. Day-0 support for new model releases is their calling card; in-house researchers post-train models for speed (licensing/rev-share deals with model devs). MCP server available (server itself free).

**HQ/people:** San Francisco. Founded 2021 by Burkay Gur (CEO, ex-Coinbase ML lead, ex-Oracle) and Gorkem Yurtseven (CTO, ex-Amazon).

**Funding:** Nov 2026: $1.3B Series F at **$16B valuation** (Bessemer lead; Nvidia, Sound Ventures, T. Rowe). Series E+F combined $1.65B. Prior: Sequoia-led D ($140M, Dec 2025, $4.5B), Meritech-led C ($125M, Jul 2025). Other investors: a16z, Kleiner, Kindred, First Round, Unusual, Salesforce/Shopify Ventures, Google AI Futures Fund. >$800M annualized revenue; ~185 employees. Customers: Adobe, Shopify, Canva, Quora.

**For agent builders:** any agent whose output IS media (video reports, ad creatives, product shots, voice/audio, avatar clips) is trivially buildable — one API key covers the whole media layer. Speed is their pitch (fastest FLUX/video inference).

**Credits:** Yes. New accounts get small free starter credits. Startup Program (fal.ai/startups): $1,000 → $5,000 credits for Europe/Asia teams with traction/VC backing — Greece eligible. Accelerator deals: YC/a16z up to $50K, EF $10K. As a listed hackathon partner they will likely hand credits/coupons on site — ask their mentor table day one.

**Impress them with:** an agent that produces finished media artifacts end-to-end — e.g. "brief in, rendered campaign out" (Firecrawl research → LLM copy → fal video/image/audio generation). Bonus: chaining several fal models in one pipeline; using brand-new Day-0 models; noting cost-per-asset.

**Exploit angle:** fal is the only realistic way to give your demo generated video/audio in 36h. "Aura points" judging rewards flashy generative output. Their usage gets measured post-event — high, visible consumption is the metric they report.

---

## 2. Firecrawl — https://www.firecrawl.dev

**What:** "Web data for AI" API. Endpoints: /scrape (URL → clean markdown/JSON/screenshot), /crawl, /map, /search (web search + full page content), /extract (prompt → structured data), /interact (cloud browser sandbox: click, fill, navigate — 2–7 credits/browser-min), /agent (autonomous web research agent, 5 free runs/day). New: Alexandria — unified source-discovery layer over live web + licensed data providers + Firecrawl indexes.

**HQ/people:** San Francisco. YC S22. Founders: Caleb Peffer (CEO), Eric Ciarla (CGO), Nicolas Silberstein Camara (CTO). Previously built Mendable (AI docs chat).

**Funding:** ~$91M total — $14.5M Series A (Nexus), then **$75M Series B Sept 2026 led by Smash Capital** (Altos, Nexus, YC, Freestyle, Offline). 200K+ GitHub stars (top-100 repo), 1.5M+ devs, 5B+ requests. Used by Zapier, Shopify, Replit, hedge funds.

**For agent builders:** the canonical way to give an agent live web access — retrieval, monitoring, extraction, form-filling actions. Open source core (self-hostable) + hosted API.

**Credits:** Free tier 1,000 credits/mo, no card. Students: code **STUDENTEDU** → instant 10,000 credits (edu email). Sponsor presence likely means event coupons — ask.

**Impress them with:** agents that close a loop on the web: e.g. competitor-watch agent that crawls → extracts diffs → acts; lead-enrichment or ticket-resolution agents pulling live data; /interact for "agent does the clicky work nobody wants" — on-theme ("tedious multi-step jobs").

**Exploit angle:** combine /search+/extract for a "deep-research analyst" or use Interact to automate a genuinely annoying web workflow (portals with no API). Their KPI: requests served per developer — burn free credits liberally and visibly.

---

## 3. Oumi — https://oumi.ai — THE insider sponsor

**What:** Open-source (Apache 2.0, Public Benefit Corp) platform for the full foundation-model lifecycle: data synthesis/curation, SFT/LoRA/QLoRA/DPO/GRPO/RLVF training (10M–400B+ params), evals (LLM judges), deployment (vLLM/llama.cpp), YAML-config reproducibility, runs laptop→multi-node cloud. New Nov 2026 (days before the hackathon!): **agent development + FAiE "Frontier AI Engineer"** — describe the agent, FAiE designs evals/tools/environments, trains the models behind it, turns production failures into training data. **BYOH (Bring Your Own Harness)**: keep your orchestration, expose an HTTPS endpoint, Oumi evals it and synthesizes datasets. Supports OpenAI/Anthropic/Gemini/Together/Fireworks/OpenRouter models + custom Oumi models.

**HQ/people:** Seattle. CEO/co-founder **Emmanouil "Manos" Koukoumidis — also a GenAI Summit organizer/insider**: ex-Google Cloud Senior Eng Manager (bootstrapped Cloud PaLM → Gemini, led Cloud NL/multimodal services, 300-person v-team), ex-Meta (Portal Assistant, Integrity), ex-Microsoft (Zo, Cortana), MIT, MSR, SMART Singapore, CERN, ICCS/NTUA Athens. Princeton PhD (mobile-cloud co-design → "edge intelligence"). Co-founders: Matthew Persons (ex-Google Cloud PaLM/NL lead), Jeremiah Greer, William Zeng, Kostas Aisopos, Oussama Elachqar (ex-Apple/Twitter/MS). Advisors: Salakhutdinov (CMU), Gkioxari (Caltech), Levine (Berkeley).

**Funding:** $10M seed (Jan 2025), Venrock + Obvious Ventures, Plug & Play, Ascend.

**Open source:** github.com/oumi-ai/oumi (9.4K★). **github.com/oumi-ai/hack-with-oumi** = their official hackathon starter kit — problem statement ("SLMs for Voice Agents"), starter voice-agent template (STT→LLM→TTS pipeline done for you), and the explicit requirement pattern they use at sponsored hacks: *use Oumi to fine-tune + star the repo*. They ran tracks at Nebius.Build SF & Eclipse 6.0 (2026). Their suggested SLM submodels list is a cheat-sheet: guardrails/judges, query rewriting, execution/retrieval/model routing, planner, verifier, executors, memory mgmt.

**For agent builders:** fine-tune a small (<10B) specialist model for ONE subtask inside your agent (router, verifier, guardrail, extractor). Free (open source); platform FAiE does evals/data-synth/training for you.

**Impress them with:** anything where a fine-tuned SLM does a real job inside the agent — their whole thesis is "specialized trained models beat prompt-engineering on giant generic models" (Manos said exactly this days ago). Star the repo. Name-drop FAiE/BYOH — launched 4 Nov, they want hackathon proof points.

**Exploit angle:** the single highest-leverage sponsor — the CEO is co-organizing the event your finals happen at. A project demoing "agent improved by Oumi" (even one QLoRA'd router/guardrail SLM via their template) speaks his exact language. Low cost: pip install, one YAML, small model.

---

## 4. Big Pi Ventures — https://www.bigpi.vc

**What:** Largest multi-stage VC platform in Greece/SEE. Two vehicles: early-stage fund + **Big Pi Growth I** (first Greek/SEE growth-equity fund; €130M first close Jun 2026 → €200M target; firm AUM ~€250M). Tickets: €0.5M–€30M firm-wide; Growth leads €7–20M+, 8–12 deals, ~3/yr, always lead. EU-fund backed (EIF, HDBI, EquiFund).

**Thesis/criteria:** tech at core of value prop; defensible moats/IP; large markets; well-rounded visionary teams; scientists/engineers commercializing lab work; international ambition with Greece/SEE operating-hub angle. Nick's personal lens (RaiseKit): biology + robotics as major waves; high-quality real-world data; deep technical capability + customer evidence automating previously-manual tasks.

**Key person (Summit speaker):** **Nick Kalliagkopoulos, Partner.** Ex-Prime Ventures Amsterdam (~$1B AUM) partner; led €5–30M rounds; invested/boarded Blueground, Holidu, aiMotive (→Stellantis), Zappi, Bright Computing (→NVIDIA). At Big Pi: boards of Acumino (general robot intelligence), Astrato, Corsmed, Numan, tileDB. CompEng Patras + RSM finance. VC since 2012.

**Portfolio signal:** ~35 companies — robotics (Acumino, AliciaBots, August Robotics), AI/data (Intelligencia, tileDB, Astrato, Dataviva, Bryq), health/deep-tech heavy. **Notable: Prosperty (theprosperty.com) is BOTH a Big Pi portfolio company AND a hackathon partner.**

**Impress them with:** treat the pitch like a seed deck — real problem, big market, defensible data loop, team that ships. Agents automating vertical workflows (their portfolio skews industrial/health/proptech) > consumer toys. The "codebase caretaker"/"invoice reconciliation" example briefs in the deck mirror their automation thesis.

**Exploit angle:** a proptech-flavored agent (document/contract/portfolio ops) quietly flatters Prosperty+Big Pi. Frame as "company we'd keep building" — they're the money in the room scouting founders, not just tech.

---

## 5. Endeavor — https://endeavor.org

**What:** Global nonprofit high-impact entrepreneur network (45+ markets): selects via International Selection Panels, then mentors/connects/co-invests. **Endeavor Catalyst**: rules-based co-investment fund, $850M+ AUM, 437 companies, 83 unicorns (ElevenLabs, Bending Spoons), invests $1–3M alongside institutional leads into Endeavor-entrepreneur rounds. Fund V: $320M — **$70M (22%) from 17 Greek investors**, most of any market. Greek-founder companies backed: 15, incl. **Runway, Reflection AI, Arena AI** ($25M+). Selection bar: can it scale ≥10x; growth-mindset founders; pay-it-forward.

**Key person (Summit speaker):** **Felix de Grey, AI & SaaS Portfolio Manager, Endeavor Greece** — picks/supports Greek-connected AI/SaaS cos; portfolio incl. **Runway, Reflection AI, Resolve AI, Arena AI, Omilia**. Ex-founder/COO of Cogs AI (neurodivergence software, Bethnal Green Ventures-backed, ~4yrs). Cambridge BA, LSE MSc. London→Athens 2023. NOTE: endeavor.org.gr now lists him "EX Manager (AI and SaaS)" — summit bio still says current; may have just transitioned, still repping them on stage. felix.degrey@endeavor.org.

**Impress them with:** founder-shaped ambition — scale story, "why this becomes a company", Greece/diaspora hook. Felix ran a startup himself; substance over slideware. AI agents doing measurable real work = his portfolio pattern (Runway/Reflection/Resolve all "agents doing a job").

**Exploit angle:** pitch finals at SNFCC as a founder audition — Endeavor feeds Catalyst co-investment + the global mentor network. If your project could plausibly become a Greek AI startup, say so.

---

## 6. Cognition AI — https://cognition.ai — shadow sponsor, confirmed pipeline

**What:** Makers of **Devin** (autonomous AI software engineer), **Windsurf** (IDE, acquired Jul 2025), DeepWiki, Devin Review, own model SWE-1.6 (up to 950 tok/s). ~$900M ARR run-rate; customers NVIDIA, Citi, Mercedes, Goldman, Ramp.

**Funding:** $2B Series E Sep 2026 at **$48B** (a16z + Accel lead; FF, GC, Avenir, Benchmark, Lux…). Founders Scott Wu (CEO), Steven Hao, Walden Yan — IOI-gold-medalist team, SF.

**Public traces to this event:**
- `hackathon.polymath42.com/deck?sponsor=cognition` = **"A proposal for Cognition"** — a personalized ask, live on the site: (1) match the €8,500 prize pool in **Devin credits** (€5k/€2.5k/€1k to winners), (2) **Devin as the on-site development harness** for the weekend, (3) €5,000 F&B. Offered **coding-agent exclusivity** ("competing coding-agent sponsorship is excluded").
- Cognition is NOT yet on the public partner list — sponsorship proposed/negotiating, not announced.
- **Devin x CityJS Athens meetup, 22 Oct 2026** (3 weeks before the hackathon): hosted by **Nader Dabit (Growth @ Cognition, ex-AWS/Eigen Labs DevRel)** + Erasmo Hernández (Cognition Regional Ambassador). Gave out Devin credits + swag. Cognition is actively courting Athens devs.

**Would building with Devin/Windsurf curry favor?** Almost certainly yes — the deck's core ask is Devin-as-harness + exclusivity; if they closed, winners get Devin credits and judges/organizers will be primed to see it used. Even if pending, organizers pitching them will love demos that prove the "Devin harness" concept. Using a competing coding agent as your headline is the one move that could sting.

**Impress them with:** "built by Devin" workflow receipts — delegate whole tickets, parallel Devin sessions, Devin Review on diffs. Cognition's internal dogma: engineers as architects orchestrating agent swarms; >95% of Devin's own codebase is Devin-written.

**Exploit angle:** if Devin access is offered on-site, take it and say so in the pitch ("this was substantially built BY an agent — meta with the 'Agents at Work' theme"). Agent-built-agent = maximum aura.

---

## 7. NOFire AI — https://nofire.ai — Greek AI-SRE startup, proposed sponsor

**What:** "Safe autonomous operations for production." Context & Control Model (CCM): live, time-versioned causal model of your production env (services, deploys, deps, incidents) + policy gate before every agent action + full audit record. Product = **AI-SRE/on-call agents**: take the page first, investigate, resolve L1/L2 tickets, incident co-pilot, proactive workflows from runbooks ("skills"). Read-only investigations; actions need policy approval. SOC 2 II, SSO/SCIM, no training on your data.

**HQ/people:** Dover DE + Athens engineering (17 ppl, ~76% Greece), founded 2024. Founders: **Spiros Economakis** (CEO — ran Mattermost cloud ops, co-author "Argo CD in Practice"), **Panos Moustafellos** (CTO — 9yrs Elastic, Distinguished Engineer, observability/infra), **Anastasios (Tassos) Nanos** (Chief Scientist — unikernels/container runtimes; **urunc is a CNCF sandbox project**; Nubificus).

**Funding:** $2.5M seed, May 2026 — Marathon Venture Capital lead + a16z scout fund.

**Hackathon link:** `deck?sponsor=nofire` = generic "A proposal for NOFire.ai" (no custom ask) — early-stage sponsor conversation. NOT on public partner list.

**Impress them with:** on-theme overlap is total — the deck's example challenge "Inbox to resolution" IS their product surface (triage → draft → close). An ops/on-call/incident agent or a policy-gated "agent that acts on prod safely" demo = their exact thesis: context graph + runbooks + policy-before-action + audit.

**Exploit angle:** tiny Greek team, hungry, their first sponsored event — a working "pager-duty agent" or incident-investigation demo in 36h would be a direct compliment and networking magnet (they're hiring; founders are in the room).

---

## Cross-cutting playbook

1. **Cover 3 sponsors in one architecture:** Firecrawl (ingest live web) → Oumi-fine-tuned SLM (route/guard/verify) → LLM brain → fal (produce video/image/audio deliverable). Optionally built with Devin. Every tech partner sees their stack on stage.
2. **On-theme beats flashy:** "agent does tedious multi-step work end-to-end" + usefulness/craft/aura. NOFire-style ops automation, ticket resolution, invoice/doc processing = safe, impressive, sponsor-aligned.
3. **Credits to grab day 1:** fal partner credits (+ fal Startup Program $1K for later), Firecrawl free 1K/mo or STUDENTEDU 10K, Oumi is free OSS (+ ask for platform credits), Devin credits if Cognition deal closed.
4. **Room dynamics:** Manos (Oumi) = organizer/judge-adjacent; Nick (Big Pi) + Felix (Endeavor) = investors scouting founders; sponsor mentor tables = where challenges get seeded. Ask each partner "did you bring a sponsored challenge brief?" — Challenge Partners get their own problem+prize.
5. **Pitch framing:** end with "and here's the company this becomes" — two VCs and an entrepreneurship network are judging.
