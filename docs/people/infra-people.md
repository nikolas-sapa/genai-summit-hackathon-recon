---
title: "infra people"
type: source
tags: [hackathon, genai-summit, recon, people]
aliases: ["infra people"]
created: 2026-11-10
updated: 2026-11-10
status: active
---

# Infra Sponsors — People Dossier
Gen AI Summit Hackathon · Athens LifeTech Park · 14–15 Nov 2026 · finals on SNFCC main stage Mon 16 Nov.
Event context: ~100–120 builders, teams 1–5, judged on **usefulness, craft, aura points**. Prizes €8,500 (€5k/€2.5k/€1k) + partner awards. Organizers: Abed Hamami, Ion Petropoulos, 100mentors, Panathēnea. Brief: "agents that take a goal, use the tools available, deliver real work end-to-end, proactively — make it work and show the demo."
Companion files: `../deep/sponsor-infra-plumbing.md` (API teardown + stack recipe), `../sponsors-infra.md`.

---

## 1. treg (treg.to) — "OpenRouter for agent tools"

### The people

**Jason Zhou — founder, the public face.**
- b. 1993. Chongqing University (thermal energy engineering) → Australia for interaction design.
- Ex-**Relevance AI** (Sydney agentic startup, Series B): led product & AI teams 3+ years, built fully-automated sales/SDR agents. Left late 2025.
- YouTuber **"AI Jason"** (@AIJasonZ, ~100–200k subs): agent/coding-agent tutorials, "loop engineering," "I don't prompt agents anymore." X: **@jasonzhou1993**. GitHub: **JayZeeDesign** (top treg committer). Email: ask@ai-jason.com. Runs paid Skool communities (AI Builder Club).
- Serial pivoter, openly so: **SuperDesign** (open-source design agent, ~7.6k★ — IDE extension → now web app + Claude Code skill) → **Coolant** (fully-automated growth agent — killed; his verdict: "zero-person company won't be viable for 6–12 months") → **treg** (Aug 2026). treg hit several× SuperDesign's revenue ~3 weeks after launch, pure usage pricing.
- Angel investor in Orca ADE/Stably AI (agentic QA — he backs agent-infra).
- Spoke at AI Coding Summit 2025 (GitNation). LinkedIn: 8.3k followers, posted "Treg is getting popular in 🇫🇷" (Sept 2026).

**Shi Tianxin (石天鑫) — founding engineer, likely GitHub "stonexer"** (石 = stone). b. 1994, UESTC Chengdu (embedded systems), Apple China test-eng internship, ~10 yrs at **Alibaba + ByteDance**. Self-describes as "maybe even more introverted than Jason" — unlikely to be the one flying out.
Company = ~2–6 people. Sydney-based (team possibly distributed CN/AU/PH). Handles: @treg_ai, @SuperDesignDev.

**Attends Athens? UNCERTAIN — probably remote or Jason only.** Sydney→Athens is a 20h+ trip for a 2-person company; no Athens posts found on his LinkedIn/X. Verify via @jasonzhou1993, LinkedIn jasonzhoudesign, or the treg Discord (discord.gg/6mQYYfFMAn) in the days before. Even remote, he's extremely reachable and video-native.

### What treg is (his framing)
"OpenRouter for data and tooling — a data and API marketplace for agents. Instead of buying subscriptions one by one, one key accesses any data or tools you need." ~2,800–4,100 endpoints, 114–126 providers, pay-per-call from ~1 cent, 0% markup, credential-injecting reverse proxy (agents never hold keys), per-agent call logs, self-hostable. **#1 paid use case by his own account: B2B customer prospecting; then SEO and social content.** Also ships Jev (open-source typesafe LLM toolkit — classification/onboarding/search-rerank, "10× cheaper, 18× faster, 30% more accurate than GPT6-luna in our tests") and an open-source **AEO toolkit** (finds which sites AI answers cite, then finds the people behind those sources).

### His stated thesis (Crossing podcast, Oct 2026) — use this verbatim in conversation
- "The agent is the real user." Build single-point tools around the Claude Code/Codex ecosystems, don't rebuild the agent stack.
- Open source + plugin marketplaces = the most effective marketing for AI products (treg's Codex plugin drove the growth curve).

### Dream demo (win their table)
An agent given a **goal, not a tool list**: e.g. "find 50 fintech CTOs who raised this month, verify their emails, draft outreach" — it `catalog_search`es by task ("find a work email"), reads per-endpoint prices + success rates, calls across 5+ providers, and the screen shows the live ledger (`X-Treg-Cost-Micro` debits, balance dropping by cents). The beats Jason will screenshot: **task→tool discovery** ("ask for the task, not the tool"), **agent spending its own money mid-task**, and the **team vault** angle (call shared keys/skills without ever holding them — per-agent audit log). Bonus beats: agent uses `catalog_request` for a missing endpoint, or publishes its own paid tool to the hub. Free $1 credit covers the whole demo; `POST /demo/sandbox` exists for zero-signup demos.

### Likely award criteria
Most end-to-end work done through the single key — breadth of distinct providers chained + a business outcome, not a tech demo. His north star is prospecting that actually books something.

---

## 2. Firecrawl (firecrawl.dev) — web data for agents · YC S22

### The founders
- **Caleb Peffer — CEO.** UNH; ex-Air Force Civilian Service, AgaMatrix; earlier micro-startups (FlutterBricks, HallHub). Co-built Mendable + SideGuide before Firecrawl. Present at their SF events (helped host Firecrawl After Dark).
- **Eric Ciarla — co-founder, Chief Growth Officer.** UNH; ex-Ford, Fracta; MDRemindME, SideGuide, Mendable. The voice on their launches ("We're Eric, Caleb, and Nick") and **personally judges Firecrawl sponsor tracks** (named judge, ElevenHacks 2026).
- **Nicolas Silberstein Camara — co-founder, CTO.** Built Mendable; taught ~50k people via @flutterguide. Judges sponsor tracks with Eric. 19.6k LinkedIn followers. SF-based.

### Who actually staffs the table (Firecrawl's hackathon machine)
- **Mark Russell Mercer — Chief of Staff, employee #12, their events engine.** Ex-Wefunder (built the CX org), ex-theater producer/director (13 yrs, 50+ productions — the showmanship shows). **Conceived + emceed "Hack the Stackathon"** at YC SF (Jan/Feb 2026, w/ Resend + Reducto: 495 applicants, 250 hackers, 92 submissions, >$45K cash, grand prize = guaranteed YC interview + 500k credits + office day). Created **"Firecrawl After Dark"** monthly dev arena; hosts events on Luma (@markatfirecrawl). **Notably ran a Firecrawl team offsite in Greece** — he has Athens logistics and affinity. Highest-probability table presence.
- **Abimael Martell — MTS (Tijuana).** Repped Firecrawl solo at **Platanus Hack CDMX (Aug 2026)**: gave the "give your agents web access" talk, then sat the table all weekend debugging with teams. Their pattern = send an engineer who can debug, not a marketer.
- Other event hosts on their Luma: Cody Menefee, Alex Nucci, Nicole Grossmann. They also hired a **Developer Relations Engineer** (Nov 2025, $140–250k, SF/remote) — that seat likely exists now.
- Founders themselves appear as track judges when it's their own event (Eric + Nicolas at ElevenHacks). For Athens, expect Mark/DevRel/an engineer; founder attendance possible but not proven.

### Hackathon sponsorship record + what they awarded
| Event | When | Prize pattern |
|---|---|---|
| Hack the Stackathon @ YC SF (co-host) | Jan–Feb 2026 | $45K+ cash, 1.5M+ credits, YC interview, "work at Firecrawl office for a day," swag |
| ElevenHacks Hack #1 (ElevenLabs, online) | Mar 2026 | $10k + 500k credits (1st); brief: "combine Firecrawl Search with ElevenAgents"; 178 submissions; **judges: Eric Ciarla + Nicolas Camara** |
| Platanus Hack ft. Firecrawl, CDMX | Aug 2026 | "Best use of Firecrawl" → **Sendero** (missing-persons platform scraping govt HTML/PDF/image sources) |
| SXSW Sydney × Build Club | Nov 2025 | Dedicated **$1,000** "best use of Firecrawl" track + 20k credits/attendee |
| TillyHacks, Modern Stack Hackathon (Convex) | 2026 | "Best use of Firecrawl" prize; Growth-plan months |
Attendee perk standard: ~10k free credits.

**Award criteria, empirically: most usage × most real-world impact.** Sendero won as "the team that used it the most AND generated the most impact." The line their own winner used: "Firecrawl search returns real articles with markdown extracted, in one call — we deleted an entire pipeline stage."

### Their public writing on agent workflows
- `/agent` launch (Dec 2025): prompt→structured-data "deep research for data" (spark-2 model, 30–60s, 5 free runs/day), replaces /extract.
- **firecrawl-agent** open framework: plan-act loop + parallel sub-agents + structured output, BYO model, `firecrawl create agent` — "Firecrawl handles the web layer. You own everything else."
- Retrieval-pattern guide: /search (find+content) vs /scrape (known URL) vs /crawl (site) vs /agent (no-URL research) — they teach exactly when to use which; using /agent inside your agent = two-layer orchestration, sanctioned for deep research.
- LangGraph tutorial: ReAct scraping agent in ~300 lines.

### Dream demo (win their table)
Repeat the Sendero pattern with Greek civic data: **an agent pointed at a real, messy public problem** — it finds its own sources via /search, extracts schema-clean JSON from awful HTML/PDFs (scrape JSON-mode or /agent), and for anything dynamic drives a real browser via /interact — with `liveViewUrl` embedded so judges *watch the agent click*. The winning formula: "we deleted a pipeline stage" + visible requests burned + an outcome a human cares about. Bonus: use firecrawl-agent's scaffold so your sub-agents fan out in parallel.

---

## 3. boxd (boxd.sh) — composable computers for agents

### The founders (all hackathon natives — highest in-person probability of the three)
- **Michiel Voortman — co-founder/CPO.** UvA grad; ex-Microsoft, Booking.com; Head of Engineering at Accountable (crypto lending); co-founded **Rule1** (agent-first ad-creative analysis, 100+ marketing teams); Melchior Analytics; **Antler founder-in-residence Berlin (Sep–Dec 2025) — where he met Laurentiu**; Azin co-founder. The demo guy: "charmed the audience with a live demo" at Azin's launch. LinkedIn 3.9k followers, writes the manifesto posts.
- **Laurentiu Ciobanu — co-founder/CTO.** Brașov → Bucharest (Transilvania U, ASE Bucharest); ex-CTO **Sessions** and **Webmarc**; dev at FintechOS, Mondly, Retargeting. Bucharest-based, **literally flies in for hackathons** (was head-down hacking during Hidde's own event intro). Bucharest→Athens ≈ 1.5h — if anyone staffs the table, bet on him + Hidde.
- **Hidde Kehrer — co-founder, the community one.** Leiden; ex-COO WorkPi, senior consultant Boer & Croon, commercial director Eevery; Azin co-founder. **Co-organized Hackaway Amsterdam** (Mar 28 2026: 50 handpicked builders, with Antler/Fini/Picnic/MLOps/AI Foundry, sponsored by OpenAI/ElevenLabs/Kilo Code): "I need to be around these people more often." Hosted the day himself. Posts the team's LinkedIn content.
- Engineers **Alexandru Jonny Șerban** and **Ștefan Ghegoiu** (Bucharest); team ~6, "half-Dutch, half-Romanian." Company: boxd.sh, Azin Tech Operating Company B.V., Amsterdam. fka **Azin** (agentic one-command deploy infra) → pivoted to microVMs. **€2M pre-seed Sept 2026** (BlueYard lead, Chad Fowler; Antler, OVNI, s20, Script Capital).

### Their own hackathon win — Anthropic × Whale "Build Local" (Amsterdam, Apr 25–26 2026)
**Best Technical Build → "Safethread."** Team: Michiel + Hidde + Diala E. (Hummingbird Ventures) + Dhruv Ghulati (Adyen/ex-Factmata). Brief from War Child: child trafficking spikes in wars while connectivity collapses. Built a **bi-directional Amber alert for broken networks**: NGO case → app push → Twilio SMS fallback → **Bluetooth mesh via forked bitchat** when nothing else works; a triage agent classifies/geocodes/clusters inbound reports (200 reports → 1 case); a Claude agent reasons per cluster, picks tools, handles low-risk actions itself, escalates high-stakes to the operator. 100 builders selected from 600+ applicants; jury Adriaan Mol, Duco van Lanschot, Clare Jones; prizes incl. Raspberry Pis. **They also launched boxd itself at a hackathon (~Apr 2026, team of 3)** — this event format is literally their origin story.

### Why they'd show up in Athens
Hackathons are their GTM (launched at one, organize their own, won one); half the team is a short Bucharest hop away; fresh €2M to convert into developer mindshare; EU-sovereign infra (GDPR/DORA/NIS2, self-hostable single Rust binary) is a tailor-made pitch for a Greek/EU summit; they're hiring Amsterdam + Bucharest.

### What boxd is (manifesto: "Billions of Machines," Aug 2026)
Persistent KVM microVMs on their own Rust hypervisor (**Ignition**, no Firecracker): <10ms create, **fork a running machine — memory, disk, processes — in <200ms**, suspend/wake <1ms, hibernated ≈ €0.0016/h, own HTTPS URL, single-binary self-host, EU-hosted. Their nine agent-machine requirements: isolation, speed, **branches** (fork from live state), whole computer, composition (compose once → stamp N), memory, **handoff** (human enters the same live machine mid-task), API ("software creates machines — machines create machines"), idle≈free. "The app runs where the agent works — reviewing an agent stops being a diff you read and becomes a thing you click." Claude Code/Codex/OpenCode preinstalled; in-machine CLI pre-authed so a box can spawn sibling boxes. €30 free credits ≈ 1,000 machine-hours.

### Dream demo (win their table)
The fork beat, no contest: **an orchestrator that forks a running agent into N live branches mid-task** — five copies explore five approaches in parallel (<200ms each, visible in the Desktop/browser view), a judge picks the winner, losers hibernate to near-zero. That's the demo no container sandbox can fake and the exact image in their manifesto. Second-best: **live handoff** — agent gets stuck, a human opens the same machine's URL/Desktop, takes over, hands it back. Third: **persistent overnight agent** — it works, hibernates mid-thought, resumes with identical memory/processing state; show the €-near-zero idle bill. Their own win was socially-resilient infra (mesh when networks die) — a degraded-environment or fault-tolerant agent story will land emotionally too. Prize guess: "best use of boxd" rewarding parallelization/persistence, judged with technical depth bias (their win was Best *Technical* Build).

---

## The combined table-sweeper (from plumbing teardown)
One agent loop hitting all three tables: **orchestrator on a boxd machine live-forks a swarm → each clone discovers + buys tools via treg (visible ledger) → browses/extracts via Firecrawl (visible liveViewUrl browsers)** — pointed at a real local problem (their shared winner DNA: Sendero/Safethread = civic stakes, degraded conditions, real data). Each company sees its own product doing the one thing it exists for: boxd = machines creating machines, treg = agent buying capability by the task, Firecrawl = agent owning the web layer.

### Fast contact map
| Who | Where | Reply odds |
|---|---|---|
| Jason Zhou | X @jasonzhou1993 · jasonzhoudesign (LI) · ask@ai-jason.com · treg Discord | High — solo founder, lives online |
| Eric Ciarla / Caleb Peffer / Nicolas Camara | X + LI via firecrawl.dev/about | Medium — CGO is the events/judging face |
| Mark Mercer | Luma @markatfirecrawl · LI markrussellmercer | High — runs their events |
| Abimael Martell | LI abimaelmartell · abimael.me | Medium — their hackathon rep |
| Michiel Voortman | LI michiel-voortman | High — active poster |
| Hidde Kehrer | LI hidde-kehrer | High — the community guy |
| Laurentiu Ciobanu | LI (via boxd page) | Medium — CTΟ, quieter |
