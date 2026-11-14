---
title: "judges overview"
type: source
tags: [hackathon, genai-summit, recon, people]
aliases: ["judges overview"]
created: 2026-11-10
updated: 2026-11-14
status: active
---

# GenAI Summit Hackathon — Judge Recon
Athens, 14–15 Nov 2026 · Finals on GenAI Summit 5 stage at SNFCC 16 Nov · Theme "Agents at Work" · Judged on usefulness, craft, "aura points" · Prizes €5k/€2.5k/€1k (sponsored by Quintessential) · ~100 builders, teams 1–5.

Key structural fact: mentors drawn from Summit speaker list; judges almost certainly = organizers + speakers + sponsors. Prize sponsor Quintessential publicly stated: "not looking for the flashiest demo… the team that builds the right thing, on the right rails, for a real customer. With no slop in the UX." Organizer brief: "make it work and show us the demo. This is not a pitching competition, it's an agent at work." → Working end-to-end agent doing real tedious multi-step work > pitch polish.

---

## TIER 1 — Almost certain lead judge

### 1. Emmanouil "Manos" Koukoumidis — CEO/Co-founder, Oumi (hackathon sponsor + organizing team + speaker)
- **Role/employer/country:** CEO & co-founder Oumi (Open Universal Machine Intelligence), Seattle/Bellevue WA; Public Benefit Corp, $10M seed (Venrock, Obvious, Plug&Play, Ascend); 30–40 employees across US/Greece/India. Organizer, sponsor CEO, speaker → lead judge.
- **Background:** Princeton PhD (pioneered hybrid cloud/edge AI), research posts at MIT, Microsoft Research, SMART Singapore, CERN; NTUA undergrad. 12k+ citations. At Google Cloud (2020–24) bootstrapped Cloud PaLM → became Gemini: led ~300-contributor v-team across 30 teams covering SFT/RLHF/serving/pruning/APIs/pricing. Earlier conversational AI at Meta and Microsoft (built a ChatGPT-style bot at Microsoft in 2016).
- **Public theses (verbatim hooks):**
  - "Don't just rent your intelligence — own it and let it compound." Rent what's generic; build/own what differentiates you or costs most. Three reasons to own: quality/differentiation, economics at scale, control/sovereignty.
  - Frontier models for narrow tasks = "a Swiss Army knife you overpay for." Specialized smaller models beat frontier on domain tasks (demo: fine-tuned Qwen beats Sonnet on bank ticket classification in ~20 min).
  - "AI needs its Linux" — open code, open data, open weights, open collaboration. Anti-lock-in: the four assets an enterprise needs to own.
  - Agentic engineering: small AI-native teams, "function collapse", production failures → next training run in four clicks; "don't forget to train the brain" (harness AND model).
  - Podcasts: Talking AI ("Stop Renting Generic Intelligence"), Ben Lorica's Data Exchange, PYMNTS, Great Entrepreneurs.
- **Presence:** LinkedIn ~5.8k followers (koukoumidis), koukoumidis.com, X less active.
- **Wins him over:** Agents that do REAL work end-to-end on proprietary/narrow domains where a specialized or fine-tuned open model beats a giant API. Bonus: open-weights models, local/owned deployment, evals + data flywheel (agent gets better from production feedback), cost math shown live, sovereignty/no-lock-in story. He has deep eng credibility — sloppy plumbing gets noticed; a working eval loop or specialized model angle is catnip. Skeptical of thin wrappers around a frontier API doing a generic task.

## TIER 2 — OpenAI / frontier-lab researchers (organizing team)

### 2. Elena Pittarokoili — Human Data → Consumer Devices, OpenAI (organizing team)
- Stanford MS Education Data Science (4.0, Onassis Scholar, Susan Athey's lab at GSB); AUEB top of class. Ex-Age of Learning analytics engineer (adaptive learning, 200k+ students), GoGuardian efficacy research, Stanford Digital Education. Joined OpenAI Human Data Jul 2025; now listed "Consumer Devices @OpenAI". Based SF. LinkedIn ~3.5k followers (elena-pittarokili-367661120).
- **Theses:** causal inference, experimental design, human-data quality for training/evaluating frontier models; education as the outcome that correlates with everything; built an LLM adaptive tutor that doubled difficulty-matching precision.
- **Wins her over:** Measurable utility — a metric, an eval, a before/after. Agents that learn from human feedback/data quality angle. Education/learning applications land personally. She thinks like a data scientist: show evidence it works, not vibes.

### 3. Elena Chatziathanasiadou — Strategic Initiatives & Operations, OpenAI (organizing team)
- ~7.5 yrs on OpenAI's founding recruiting/people team (led Residency program — pathway for non-AI researchers into AI), moved to Strategic Initiatives Sep 2025. UC Berkeley background (psych research assistant); ex-Genentech. Emceed OpenAI Girl Geek dinners; talent-programs lead. LinkedIn ~1.7k followers (eleni-chatzia).
- **Wins her over:** She's people/talent, not model-depth. Craft, clarity, team story, accessibility — tools that open AI to non-specialists, workforce/skills angle, inclusive design. A crisp demo a non-technical audience groks.

## TIER 3 — VCs / ecosystem (speaker + partner logos on hackathon site)

### 4. Nick Kalliagkopoulos — Partner, Big Pi Ventures (speaker; Big Pi is hackathon partner)
- Athens-based, ex-Partner Prime Ventures Amsterdam (~$1B AUM, 8 yrs), ex-Randstad Innovation Fund, Dutch Expansion Capital; founded Startupbootcamp HighTechXL. MSc Computer Engineering (Univ. Patras), MSc Finance (Rotterdam, cum laude). Board: Acumino, Astrato, Corsmed, Numan, TileDB; prior: Blueground, aiMotive (→Stellantis), Bright (→NVIDIA). LinkedIn ~7.5k followers (kalliagk). Endeavor mentor. Writes on Greek ecosystem (Big Pi blog "Embracing Change").
- **Wins him over:** Deep-tech credibility + venture-scale market. He funds "exceptional technologies or ingenious business models" — technically defensible agent infra, dev tools, vertical agents with a moat beats a demo toy. €5–30M check writer: show a market, a wedge, why now. CS degree: don't fake the tech.

### 5. Apostolos Apostolakis — Co-founder/Partner, VentureFriends (speaker)
- Serial founder before VC: e-shop.gr, e-food (→Delivery Hero), Doctoranytime, early investor/board Beat (→Daimler/Freenow). BCG, Merrill Lynch; NTUA civil eng, Columbia MBA. VF: €170M/3 funds, fintech/marketplaces/consumer sweet spot; Blueground, Instashop, Plum, WelcomePickups, HarborLab, Huspy. Preaches founder ambition + international markets. Athens-based. Signature investing heuristic: does the founder actually act on bold ambition?
- **Wins him over:** Business viability + founder hustle. Marketplace/fintech/consumer-flavored agent ideas with real transaction volume, monetization path, and a team that behaves like founders (ship, sell, iterate). Least impressed by research-for-research's-sake; most impressed by "this could be a company Monday morning."

### 6. Felix de Grey — AI & SaaS Portfolio Manager, Endeavor Greece (speaker; Endeavor is hackathon partner)
- Selects/mentors Endeavor's AI portfolio: Runway, Reflection AI, Resolve AI, Arena AI, Omilia. Founded/ran Cogs AI (tech for ADHD/autism, Bethnal Green Ventures-backed) ~4 yrs — operator who has sat in the founder seat. Cambridge BA, LSE MSc; London→Athens 3 yrs. LinkedIn ~1.5k followers (felixdegrey).
- **Wins him over:** Founder empathy + high-impact-entrepreneur lens: real user pain, thoughtful scope, agent that demonstrably removes tedious work for a named persona. Neurodiversity/accessibility or humane-tech angles resonate. He talks to top AI founders daily — hype-free pitch, honest limitations.

### 7. Menelaos "Mene" Mazarakis — ex-Partner & Head of Product, Chapter One (organizing team)
- SF/Palo Alto. Now: founding team/Head of Product & Growth at Anon (anon.com — "automated internet" dev tooling; note: Anon is literally agentic-web infra). Chapter One first hire ($50M fund, product/design-first VC, web3). Instagram PM civic products (US2020 election: 75M reached, 4.4M registrations), Facebook misinformation PM, Novi (crypto wallet) PM, Google AI marketing/policy. Princeton + Wharton social-impact fellow. UN/EU advisor early career.
- **Wins him over:** PRODUCT CRAFT is his whole identity (product-and-design-first fund). Agentic-web/automation infra, developer tools, consumer-grade UX on agents. Civic/social-impact applications resonate (his Instagram voting work). "Aura" judged through product taste: elegant demo, intentional design, opinionated UX.

### 8. Sylvia Bouloutas — ex-Investor, Techstars SF (organizing team)
- Now "Investor & Operator", recently Hippocratic AI-affiliated per LinkedIn scrape; Techstars Aug'22–Mar'25 investing AI/ML, deep tech, enterprise SaaS, fintech; ran sourcing for ~24 investments/yr. Ex-NYC family-office principal (8 deals), started as fintech founder (wealth mgmt/impact). Duke MBA, St Andrews BA; Greek-American, vocal on immigrant/female founders. LinkedIn ~8.9k followers; Medium essays ("Accelerometry — how Techstars picks winning cohorts"). Palo Alto.
- **Wins her over:** She wrote the framework for picking early-stage winners: team, market, traction velocity. Enterprise SaaS/fintech agent with a credible GTM story. Impact mission ("invest in a world she wants to live in") + founder story matter. Show coachability and speed of execution — accelerator investor lens = "could this team compound?"

### 9. Elena Pantazi — Partner, Talent & Portfolio Development, Northzone (organizing team)
- London; Northzone's first talent-focused partner (fund: Spotify, Klarna, Personio, Trustpilot; >$1.5B AUM). Ex-Bain Capital PE ops director, Third Bridge VP research (early employee), Impetus, UBS IB. INSEAD MBA, Cambridge MPhil, UCL BSc; Co-Active coach. Advises founders on team-building/hiring.
- **Wins her over:** Team composition and how you work: division of labor, hiring-ready thinking, agents applied to org/talent/ops workflows would intrigue her. She's ops-fluent — appreciates process rigor and clarity over jargon.

## TIER 4 — Deep-tech / academic judges

### 10. Dionysis Zindros — CEO/Co-founder Common Prefix; Stanford postdoc (organizing team)
- Consensus/cryptography: NIPoPoWs, sidechains, light clients; papers in IEEE S&P, CCS, FC, DISC; Black Hat talks. Ex-Google security IR (Zürich), Twitter product security, IOHK (built Cardano), co-invented OpenBazaar. PhD Univ. Athens (Kiayias), NTUA MEng. Cypherpunk ethos: decentralization, privacy, Signal/Tor, GPL/MIT licensing, "systems beneficial to all and owned by no one." Splits Palo Alto/Athens.
- **Wins him over:** Mathematical/technical rigor, provable claims, security thinking. Decentralized/agent-to-agent trust, verifiability, privacy-preserving agents, crypto x agents (agent payments, attestations, on-chain agents) = bullseye. Open-sourcing the project scores. Hates hand-waving and authority — no fake metrics.

### 11. Tim Gianitsos — Research Scientist, AMD (organizing team)
- Ex-Lamini MLE (LLM fine-tuning; acquired by AMD), Amazon SDE, Stanford MSCS (CS109 head TA/lecturer), UT Austin BS. Works on RL for LLMs + GPU/hardware constraints; built AMD AI Academy RL mini-course; NeurIPS kernel-generation-agents tutorial (Sharon Zhou's team, KernelBench-adjacent). SF Bay. LinkedIn ~2.7k followers.
- **Wins him over:** Technical depth: RL, fine-tuning, inference efficiency, agents that generate/evaluate code or kernels, self-improving loops with real reward signals. Teacher mindset — a project that explains itself well. Quantify: latency, cost, accuracy deltas. He's junior-ish on the panel; align with him for credibility with researcher judges.

### 12. Yannis Assael — Senior Staff Research Scientist, Google DeepMind (speaker list)
- Famous Greek AI researcher: Ithaca (Nature 2022 — restoring ancient Greek inscriptions; human+AI collaboration lifted historian accuracy 25%→72%), Vesuvius Challenge scroll-reading, LipNet lip-reading; Gemini 1.5 report contributor. MIT Innovators Under 35, Forbes 30u30, Greece's delegate to GPAI/OECD. Ex-Oxford PhD. Site: assael.gr.
- **Wins him over:** AI for culture/science/humanity — agent + expert-in-the-loop collaboration (his signature: tools that amplify experts, not replace them). Greek-heritage/classics applications = instant resonance. Novel multimodal use, ambitious scope executed cleanly. If he judges, a "wow, didn't think that was possible" demo is the play.

## TIER 5 — The organizer himself

### 13. Abed Hamami — Founder, Polymath Labs (runs the hackathon; abedhamami42@gmail.com, cal.com/abed42)
- Self-taught product engineer; born Greece, raised partly in Syria, returned as refugee — learned to code at Social Hackers Academy (Athens bootcamp for refugees/migrants), became its Head of Education (Vodafone World of Difference award), co-founded intechgration (tuition-free coding bootcamp for refugees/vulnerable groups, WDX-180° curriculum). Ex-ILO data analyst, Zone01 Athens, Na'amal TPM; Product Engineer at LINQ; founding engineer at Gamerplug (Austin, social app). Founded Polymath Labs Jan 2026 (solo AI co); runs this hackathon with 100mentors + Panathēnea teams + Ion Petropoulos. SF Bay-based, deep Athens ecosystem ties. LinkedIn ~1.5k (abed42). "i make things."
- **Why he runs it:** community-builder DNA + ecosystem play (education→jobs→founders); sponsors incl. Oumi, Big Pi, Endeavor, Quintessential (prizes), fal.ai, Firecrawl, Wonderful, Prosperty.
- **Wins him over:** BUILDER authenticity — he is the "agents at work, not a pitch competition" line. Working demo end-to-end > slideware, always. No-slop UX (echoing Quintessential). Scrappy, self-taught, real-user energy; social-mobility/accessibility undertones welcome. Don't overclaim.

---

## Panel archetypes & how to pitch each

Speaker-list scan: Summit theme is explicitly post-experimentation — "deployment, ROI, governance." Speaker mix = enterprise adopters (Kyndryl, Deloitte, EY, EPAM, Microsoft GM, Lloyds, MSD, Piraeus, Viohalco, Olympia Group, chamber-of-commerce types incl. PM Mitsotakis), Greek VCs, frontier researchers, ecosystem orgs. The hackathon jury concentrates 4 archetypes:

1. **Frontier-lab researcher** (Koukoumidis, Pittarokoili, Zindros, Gianitsos, Assael): proof it works — real end-to-end execution, evals/metrics, technical honesty. Specialized model, RL/fine-tuning, or verifiability angle scores. Kill: thin wrapper, fake numbers.
2. **VC / investor** (Kalliagkopoulos, Apostolakis, Bouloutas, Mazarakis, de Grey, Pantazi): could this be a company? Named user pain, market wedge, moat, monetization, team speed. Kill: toy demo, no customer, hype.
3. **Enterprise adopter / operator** (Endeavor/Northzone lens + the Summit audience they'll pitch to at finals): deployment realism, ROI framing, governance/safety, integration into real workflows. Pitch with "who pays and why Monday morning."
4. **Indie-builder/organizer** (Abed + sponsor Quintessential): craft, aura, no-slop UX, shipped-in-36-hours authenticity. The "aura points" criterion lives here — taste, originality, personality in the demo.

**Composite winning project:** an agent that autonomously completes a genuinely tedious multi-step real job for a named persona (usefulness), built with clean craft and great UX (aura), demoed live working end-to-end (builder credibility), with a one-line eval/metric and cost math (researchers), and a plausible path to a real customer (VCs). Differentiators: specialized/fine-tuned or open-weights model component (Manos), human-expert-in-the-loop framing (Assael), verifiable/trust elements (Zindros), accessibility or Greek-context resonance (Abed, Felix, Sylvia).

---

## Nov-14 additions — judge-candidate dossiers written

Site sweep on event day (Sat 14 Nov): hackathon site still publishes **no named judge list** — bench is invite-email based (agenda `?role=judge` notes now live: some judges attend Sun only, some Mon only, some both; voting via web app + AI-assisted submission review). No fresh public judge declarations found on LinkedIn/X since Nov 10 (LinkedIn authwalled to crawlers; Nitter dead — X C&D Sep 2026). Discord (discord.gg/gqU8FW45qf, created ~Nov 12-13) is member-verification gated — judge chatter likely inside, invisible outside.

Six candidates flagged in Nov-11/12 deltas had no dossiers — now written:

| Dossier | Who | Judge signal |
|---|---|---|
| [[judge-rasmussen]] | **Lars Rasmussen** (Florent VC / Google Maps co-founder / Panathēnea co-founder) | Luma featured guest; judged Florent×Panathēnea May 2026; mentor bench → near-certain |
| [[judge-papadopoulos]] | **Panos Papadopoulos** (Partner, Marathon VC) | Volunteered on Ion's post; `?sponsor=marathon` overlay pending; Panathēnea bench |
| [[judge-bellonia]] | **Marilena Velonia Bellonia** (GenAI Guardrails PO, Lloyds) | **Org team** + speaker → bench member; THE policy-gate judge |
| [[judge-mallios]] | **Kostas Mallios** (ex-MSFT GM, ex-Applied Materials CVP) | Speaker + **Panathēnea board director** → org-side judge; ROI lens |
| [[judge-tsirekas]] | **Mark Tsirekas** (Senior Staff PM, Meta) | Owns LLM-judges/evals at Meta scale — the eval-fluent judge |
| [[judge-bannerman]] | **Tey Bannerman** (ex-McKinsey Partner, Head of Design Europe) | Speaker; the "aura points" judge — design craft on AI products |

Already covered: **Georgios Kontogiannis** (Wonderful Site CTO SEE — Wonderful-Track judge) lives in [[wonderful-people]] §2. Unprofiled Ion-post volunteers (weaker, mentor-ambiguous — watchlist only): Orestis Skoutellas, hari chronis, Orlando Kalossakas, Adam Markakis, Spiros Economakis, Antonis Despotakis, Kai Hackbarth.

**Fresh judge-mechanics facts (Nov 13-14 site state):** tracks published in /prep — Voice & Enterprise Agents (Wonderful), Biotech & AI (Athens LifeTech Park hosts), Content & Digital Art (fal), Open Track (hardware extra points). Track sponsors supply track judges → expect Wonderful (Kontogiannis), fal, and LifeTech Park delegates at Sunday semifinals. Judges choose the 4 finalists Sunday ~20:00 and final rankings Monday at Book Castle, SNFCC 18:00–18:50.
