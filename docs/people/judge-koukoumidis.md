---
title: "judge koukoumidis"
type: source
tags: [hackathon, genai-summit, recon, people]
aliases: ["judge koukoumidis"]
created: 2026-11-10
updated: 2026-11-10
status: active
---

# Deep Dossier — Emmanouil "Manos" Koukoumidis
**Who:** CEO & co-founder, Oumi (oumi.ai) · co-organizer GenAI Summit SE Europe · likely lead judge, Gen AI Summit Hackathon (Athens, 14–15 Nov 2026)
**Why he matters:** He is the most technical person on the panel and the only judge who has *personally shipped* the thing this hackathon is about — agents backed by trained models. Fake demos and prompt-wrappers are dead on arrival with him. He built Cloud PaLM→Gemini, built chatbots in 2016, and his entire company exists to prove one thesis. Align with the thesis = align with the judge.

---

## 1. TL;DR — The single highest-leverage read

His worldview in one line (his own words): **"Consume what is generic. Build and own what differentiates you."** For a hackathon project this translates as: an agent whose *brain* is specialized and owned (a fine-tuned open-weights model doing a real job), wrapped in a working harness, proven with numbers. He is allergic to the word "agents" used loosely — he literally said he tries to avoid saying it because he hears it so much — so the demo must show an agent *doing work end to end*, not a chat loop. If any component can show evals → failure modes → targeted training → improvement, you are speaking his mother tongue.

**Timing kicker:** Oumi shipped its Fall Launch (FAiE building agents + BYOH + GRPO) on **Nov 4, 2026 — ten days before the hackathon**. "Agents that learn from their own work" is his freshest talking point; a project that embodies it will feel like his thesis come alive.

---

## 2. At a glance

| Field | Detail |
|---|---|
| Name | Emmanouil (Manos) Koukoumidis |
| Born/educated | Greece; NTUA Diploma ECE 2001–2006 (Athens native — Greek pride matters to him, see §10) |
| PhD | Princeton, Computer Engineering, 2006–2011 (deposited 2012). Advisors: **Margaret Martonosi + Li-Shiuan Peh**. Visiting MIT CSAIL 2009–2011 |
| Thesis | "Collaborative and Adaptive Mobile Device-Resident Service Architectures" — mobile-cloud co-design; self-describes it as seeding what was "seven years later called edge intelligence" |
| Citations | >12,000 claimed on official bio (much of it via the Gemini tech report); ~1,850 personal h-index ~10 pre-industry |
| Employer history (rev. chrono) | **Oumi** (May 2024–now) → **Google Cloud AI**, Senior SWE Manager (~2020–2024) → **Biscuit Labs**, Dir. of Eng (Sep 2019–Jun 2020, stealth smart-building IoT startup, since folded) → **Facebook/Meta**, ML SWE (Portal Assistant, Integrity) → **Microsoft** (Zo chatbot, Cortana; ~2011–2017) → research posts: **MIT, Microsoft Research, SMART Singapore, CERN, ICCS Athens** |
| Signature claim | "Bootstrapped the Cloud PaLM efforts establishing a v-team of over 300 contributors across >30 teams" — training/quality, infra, safety, pricing, all the way to GA (May 2023); effort moved to DeepMind as Gemini, he kept contributing |
| Oumi | PBC (Public Benefit Corp), HQ Bellevue/Seattle WA; ~30–40 staff (+110% YoY), distributed US/UK/**Greece**/India; $10M seed (Jan 29, 2025) led by **Venrock + Obvious Ventures**, w/ Plug & Play + **Ascend** (Greek-focused pre-seed fund — posted Oumi's Athens roles) |
| Backers/advisors | Founding scholars incl. **Ruslan Salakhutdinov (CMU), Georgia Gkioxari (Caltech), Sergey Levine (Berkeley)**; 13+ university partners at launch (Princeton, MIT, Stanford, Cambridge…), now 15–20 |
| X | @Koukoumidis (~1.8k followers; launch posts get amplified by Oumi eng team) |
| LinkedIn | linkedin.com/in/koukoumidis (~5.8k followers) — his megaphone; posts go viral-ish (Aug 11, 2026 post: ~1M views, 120+ quote-posts in 4h) |
| Personal site | koukoumidis.com — sparse bio + three quotes: Mark Twain "sail away from the safe harbor… Explore. Dream. Discover." / "If there is no wind, row." (Polish proverb) / "Imagination is more important than knowledge" (Einstein). **Risk-taking + hustle + creativity is his self-image** |

---

## 3. Career timeline (verified)

- **2001–2006** NTUA Diploma, Electrical & Computer Engineering, Athens. Early research at **ICCS** (NTUA-affiliated institute) and **CERN** Geneva.
- **2006–2011** Princeton PhD under Martonosi & Peh. Research stints at **SMART** (MIT–Singapore alliance — SignalGuru's Singapore deployment), **Microsoft Research**, and **MIT CSAIL** (2009–2011, followed advisor Peh).
- **~2011–2017** Microsoft — mobile/cloud systems (Bing mobile-search caching patents) then conversational AI: **Zo chatbot (2016, LSTM-based "ChatGPT precursor" + early RAG prototype)** and Cortana. He has "been working on GenAI systems since 2016."
- **~2017–2019** Facebook/Meta, ML SWE — Portal Assistant (on-device assistant) + Integrity (harmful-content ML).
- **Sep 2019–Jun 2020** Biscuit Labs, Director of Engineering — pre-Series-A stealth smart-building/energy IoT (SF; backed by Two Culture Capital; folded 2022).
- **~mid-2020–May 2024** Google Cloud — Senior SWE Manager, Cloud AI. Led eng+science for all Natural Language + some multimodal AI services. **Bootstrapped Cloud PaLM**: 300+ person v-team across 30+ teams — quality, infra, safety/RAI, pricing — to GA May 2023; continued contributing post-handoff to DeepMind/Gemini. The Gemini model-customization tooling used by enterprises "was built by my team at Google, and by some of my now co-founders."
- **May 2024–now** Oumi, CEO. Founded with **Oussama Elachqar** (ex-Apple/Twitter/MS ML eng — built SOTA SLMs at Apple), **Matthew Persons** (Head of Eng, ex-Google Cloud PaLM & NL lead, Cornell), **Jeremiah Greer** (Head of Research, ex-Google Gemini Alignment, built HallOumi), **William Zeng** (ex-Google Cloud Gemini Responsible-AI lead, Stanford), **Kostas Aisopos** (ex-Google staff eng, ex-MS — Greek). Also Greek staff: **Panos Achlioptas** (well-known Greek AI researcher; sat the Summit-4 "LLMs Made in Greece" panel), **Konstantinos Anastasiou** (product design). Jan 29, 2025: public launch, $10M seed, GitHub #1 trending within 24h. Now 9.4k★.

### Research DNA (what his PhD actually was)
- **SignalGuru** (MobiSys 2011, **Best Paper Award**): windshield-mounted phone cameras collaboratively detect/predict traffic-signal schedules → GLOSA speed advisory; deployed in Cambridge MA + Singapore; predicted within 0.66s pre-timed / 2.45s adaptive; **20.3% fuel savings**. Crowdsensing from commodity devices, measured on real systems in two cities.
- **Pocket Cloudlets** (ASPLOS 2011): cache cloud services in phone NVM to dodge 3G latency; PocketSearch served 66% of a user's Bing mobile queries locally, 16× faster. Evaluated on **200M real queries**.
- **RegReS** (PerCom 2011): middleware keeping service density in opportunistic vehicular networks; outdoor parking-availability service deployed on ORBIT testbed.
- Patents (Microsoft era): crowd-sourced parking advisory; community cache for mobile search; geofences from context/crowdsourcing.
- **Pattern to mirror:** cheap commodity hardware + collaboration + measured real-world deployment = his idea of beautiful work. A hackathon demo with *real measured numbers on a real deployment* resonates harder with him than any architecture diagram.

---

## 4. Oumi — the company, product, and why it exists

**Structure:** Public Benefit Corporation; "unconditionally open" mission legally bound. Open-core: Apache-2.0 OSS library (oumi-ai/oumi, ~9.4k★ — "DevOps layer for foundation-model R&D": data curation/synthesis, SFT/DPO/GRPO, evals, inference, any compute from laptop to 1,000+ GPU HPC) + commercial platform ($25/mo/org + usage; scale-to-zero autoscaling; per-GPU-second billing; ~50–60% of platform improvements trickle back to OSS).

**Product thesis (evolved 2025→2026):** OSS train/eval platform → **"Compounding AI Factory"** (Aug 11, 2026 — build→deploy→monitor→retrain loop, every production interaction becomes eval/training data; customers own+export weights, data, *and recipes*) → **FAiE "Frontier AI Engineer"** (agent that automates the whole engineer loop from a prompt — he calls it "Agentic AI Development" / **"VibeML"**) → **Fall Launch Nov 4, 2026**: FAiE extended to agents; **BYOH — Bring Your Own Harness** (keep your orchestration/tools/memory; Oumi evals + retrains the brain underneath); DPO GA alongside SFT; GRPO private preview.
**Adjacent artifacts:** **HallOumi** (claim-verification/"AI lie-detector" model by Jeremiah Greer; powers the NYT study), Rent-vs-Own calculator (demo math: $212,500/mo API → $6,944 Oumi, 96.7% less), AI Atlas (580 ready-to-build AI tasks), Oumi Labs ("a city of small models doing real jobs"), "2026 State of Owned AI Report".

**Athens presence:** real — Research Scientist (Athens, hybrid) and SWE-Platform (Greece) roles were posted (€30–60k + equity); Greek co-founder (Aisopos) + Greek researchers; Ascend (Greek pre-seed fund) on the cap table; Archimedes Talks appearance Feb 2025 where he said **"Greece could be a key player and leader in this."** He is an official GenAI Summit organizer ("builders behind the Summit") AND a Summit 5 speaker.

**Hiring signal:** `#hiring` in his LinkedIn headline; field engineers, research scientists, growth — the hackathon's CV opt-in is a real recruiting channel for Oumi.

---

## 5. The verbatim doctrine — what he actually says

### 5.1 Own, don't rent (his load-bearing framing)
- **"Don't just rent your intelligence. You should own it and let it compound for yourself. For every interaction your customers have with your business and with the AI that powers your business, your AI should be getting better. That should be your core asset — not OpenAI's, not Anthropic's, not Google's."** (Data Exchange, Jul 2026)
- **"Consume what is generic. Build and own what differentiates you."** (LinkedIn, Aug 11, 2026)
- "In one year, renting all of your intelligence from a frontier lab… will look as strange as outsourcing all of your proprietary software." (LinkedIn, Aug 2026)
- "We can't be renting our AI." / enterprises exploring other strategies (PYMNTS, Aug 2026)
- "The winners of the next AI era will be the companies that turn their own data, expertise, and experience into specialized intelligence that nobody else can rent." (LinkedIn, Aug 2026)
- Rule of thumb: **"Rent what is generic. Build and own what differentiates you or what costs you the most."** (Talking AI, Oct 2026 — e.g. a bank uses Claude Code for coding but owns the model processing mortgages)
- "Every company renting AI has the same edge as its competitors: none." (Summer Launch 2026, "The Enterprise AI Paradox")

### 5.2 Specialized > biggest
- **"A model built for everything is optimized for nothing."** (Oumi blog, Mar 31, 2026)
- **"The right model beats the biggest model… The moat no longer lives in which model you access. It lives in how well that model is built for your specific work."** (Oumi blog)
- "Waiting for the next off-the-shelf model update… is not a strategy for differentiation, it is a guarantee for mediocrity." (Oumi blog)
- Specialization results he cites repeatedly: **"10, 20, or 30 points of improvement, at a fraction of the cost"**; a 200–400M-param on-device model matching a 4B model for invoice line-item classification; "models 10×, 100×, even 1,000× bigger than they need to be" is "wildly irrational."
- "80% vs 96% accuracy is the difference between a feature you can't ship and a competitive moat." (Oumi blog)
- "It's not about having more AI than your competitors. It's about picking your bets… Solve those specific problems with your own specialized AI." (Data Exchange)

### 5.3 Agents — the brain matters more than the harness
- **"The word 'agents' — I don't know how many times I've heard it. So many times that I often try to avoid using the word myself."** (Data Exchange — he is buzzword-fatigued; demo > vocabulary)
- **"The biggest gap we saw was that people took these generic things and created agents out of them… Then they asked, 'Why is this not reliable?' It's because they never put in the effort to make the model reliable — to teach it how to do the specific thing."** (Data Exchange)
- "The ones that succeed will improve **by training the weights of the models powering them, learning from their own work**." (SiliconANGLE, Nov 4, 2026)
- "You can build extra harnesses around it. All of that is good. You should have it. But you should start by putting specialized intelligence — the specialized model — at the core." (Data Exchange)
- Nuance — he also credits the harness: "Two identical models. Two identical harnesses. A 20-point performance gap… it's the difference between handing a scalpel to a person off the street versus a surgeon." (AI Masterminds w/ Raffi Krikorian, Sep 2026). **Read: both must be engineered; neither alone impresses.**
- Agents are systems now: "it's not just a model in isolation. It's becoming a more complex system, and you need to be able to train it and evaluate it as a more complex system." (Data Exchange)
- Best agents call *your* tools: the best model for tool use is "something you teach specifically how to do this, as opposed to a generic model that you just prompt and hope it will be able to use all the tools." (Data Exchange)

### 5.4 Evals-first engineering (his canonical recipe)
- **"The first step, like a good AI engineer, is to establish your baseline. You need evaluations for this problem. Here are the right metrics… You need test sets."** Then: evaluate baseline (closed + open), **"go deep and tell you the most common failure modes and the patterns in which this model fails,"** synthesize targeted training data, train, re-evaluate, iterate. (Data Exchange — this is literally the FAiE loop)
- "What most platforms do is assume you've done everything… run the algorithm for you, which is, in many ways, the easiest part of the whole process." (Data Exchange — i.e., he respects the hard parts: eval design, failure analysis, data curation)
- On contributions: "If a recipe moves a trusted benchmark positively with no regressions (including safety), it bubbles up." (Data Exchange, May 2025)
- **Production→data loop:** "The model doesn't stop learning when it reaches production. It compounds." / "Every mistake your model makes in production is usually wasted" elsewhere. (Aug 2026 launch)

### 5.5 Reliability, verifiability, groundedness
- **HallOumi × NYT study** (his proudest artifact): at NYT's request, Oumi ran 4,326 SimpleQA queries through Google AI Overviews (Gemini 2 then 3). Findings: **only ~39% fully trustworthy** (correct AND all claims supported by citations); **1-in-3 claims unbacked**; accuracy rose 85%→91% but ungrounded citations rose 37%→56%; Facebook & Reddit were top-4 cited sources. Manos's post: "AI hallucinations have now become a legal liability." Oumi's moral: **verifiability > accuracy; "create a model that can be checked."**
- "For many use cases, having a model that is 90% accurate doesn't make the cut. It's just not good enough… I'm very excited about making AI more reliable for organisations." (Startup Pirate)
- He built claim-verification *because* "hallucinations are a major blocker for enterprises adopting AI in production." Any agent that *checks itself* speaks to this.

### 5.6 Open source / sovereignty / the oligarchs
- **"AI needs its Linux… The greatest technology innovations are developed in the open."** (launch PR)
- "Unconditionally open" = open data + open code + open weights + **open collaboration** — "If something is open but people can't push it forward, it doesn't help much." Llama/DeepSeek/Mistral are merely open-weights; "it's almost impossible for anybody to reproduce what they did." (Startup Pirate)
- "Only a few aspiring AI oligarchs (OpenAI, Anthropic, and Google) want closed AI to succeed. Nobody else." (Startup Pirate)
- "The open community is still the sleeping giant of AI. If awakened, coordinated, and equipped with the right tools, it can and will outbuild, outscale, and outlast the silos." (AI_dev EU 2025 talk — talk titled "The Imperative for Open Source AI — The Path Forward to **Take Down the AI Oligarchs**")
- Two horses: closed does everything alone at full cost vs. open harnessing "all the cumulative innovation… of a large global community. Which horse would be faster?… I would bet on open source outpacing closed source AI every time." (Startup Pirate)
- Supply-risk pragmatism: open-weights can be withdrawn (Cursor clause) → so specialize YOUR copy now and let it compound; "it is an alarm for organizations to get that AI independence as soon as possible." (Data Exchange)
- On sovereignty: even non-regulated enterprises now fear dependence — "If I'm renting this… I'm going to be in trouble one day. That's not a viable strategy." (Data Exchange)
- Safety stance: aligns with LeCun over Hinton; "the best way to address safety is to do it openly… build 'protector AI' that can detect and prohibit misuse." (Data Exchange, May 2025)
- Not a doomer, not a hype man: "I don't think AI is a bubble, but I do think some specific companies may become bubbles." + Jevons paradox bullishness on compute. (Data Exchange)

### 5.7 Culture/taste tells
- Live-demo ethos: on Talking AI he did a **live demo — fine-tuned Qwen beating Sonnet on a bank-ticket classifier in ~20 min of human effort**; Summer Launch demos were "watch a production model get built live." He *respects* live demos.
- Decision tree for execs: **rent what is generic → route → fine-tune → train** (escalating ownership). 
- "Four assets" to own to avoid lock-in (Talking AI): model weights, training/test data, recipes (and evals/harness around them).
- AI-native org craft: "function collapse," "no code reviews for code you don't understand" — he appreciates small teams shipping like much bigger ones.
- Greek-flavored wit on X: "Don't follow Odysseus' journey to building your AI. Don't take 20 years. Do it with Oumi. In 20 hours max."
- On strategy: "A strategy that relies on surprises is not a strategy." (Data Exchange)

---

## 6. Map of every public appearance found

| Date | Venue | What he said (link) |
|---|---|---|
| Mar 4, 2025 | **Eye On A.I. #240** (Craig S. Smith, ex-NYT) | "Why the Future of AI is Open-Source" (youtu.be/pl1Yh6bA9Q4) |
| Mar 7, 2025 | **Startup Pirate** (Alex Alexakis, Marathon VC) | The Path Forward for AI — richest personal-mission interview (blog.startuppirate.com/p/the-path-forward-for-ai) |
| Mar 16, 2025 | **AI Engineering Podcast E48** (Tobias Macey) | "The Power of Community in AI Development" — Oumi architecture, Linux ambition, community governance |
| Feb 13, 2025 | **Archimedes Talks** (Athena RC, Athens) | "The Imperative for Open Source Frontier AI — Oumi's Platform & Strategy"; call to action: "Greece could be a key player and leader" (archimedesai.gr) |
| May 2, 2025 | **UC Davis AIFS Speaker Series** | Same Imperative talk; notes Oumi powers "AgTech hackathons" |
| May/Jun 2025 | **Data Exchange** (Ben Lorica) | "How a Public-Benefit Startup Plans to Make Open Source the Default for Serious AI" — HallOumi, governance, safety (youtu.be/eD_Fj6Dq8wM) |
| Aug 29, 2025 | **AI_dev OSS GenAI Summit EU, Amsterdam** | TWO talks: keynote "The Future for AI-First Enterprises is 'Open'" (youtu.be/XgOPYzj1sIo, 10m) + "Take Down the AI Oligarchs" (youtu.be/7fjmWNeSVa8, 22m). Stats he used: open-closed quality gap 8%→1%, 10× smaller/faster specialized models, 8k★/1k Discord |
| Jul 9, 2026 | **Data Exchange** (Lorica, return) | "Stop Renting Generic Intelligence" — the deepest agent/eval discourse; full transcript available (youtu.be/2g_LVUXXqJE) |
| Oct 14, 2026 | **Talking AI** (Matt Paige, HatchWorks) | Rent-vs-own decision tree; K&E vs Harvey; live fine-tune demo; "don't forget to train the brain"; open-core rationale |
| Oct 21, 2026 | **AI Masterminds** (Oumi's own show; he co-hosts) | w/ Raffi Krikorian (Mozilla CTO): compound interest of owned AI; 40–50× cheaper OSS per Mozilla research; harness+scalpel metaphor; "pick one critical workload" |
| 2026 | **Oli Dinov podcast** | "Experiment, experiment, experiment" — model selection for agents |
| Aug 11, 2026 | **Compounding AI Factory launch** | PR + Summer Launch video: "Every company is becoming an AI company…" (oumi.ai/press-release/compounding-ai-factory) |
| Nov 4, 2026 | **Fall Launch** | FAiE builds agents; BYOH; GRPO; "learning from their own work" |
| Nov 16, 2026 | **GenAI Summit 5, SNFCC** | Speaker + organizer — hackathon finalists pitch on *his* stage |
| Nov 24, 2025 | GenAI Summit 4 | Promoted it on LinkedIn ("shape what's next"); Oumi's Panos Achlioptas on "LLMs Made in Greece" panel |
| 2026 | Slush | Listed speaker |
| Writing | Oumi blog byline | "The Case for Specialized Intelligence" + "The Era of General Purpose AI Is Over" (Mar 31, 2026); "Hours, Not Months" (Oct 9, 2025); launch notes |
| Notable LinkedIn posts | Aug 11, 2026 "Enterprise AI is in a wildly paradoxical state" (~1M views) · Jul 22, 2026 "inflection point" (Satya: renting "makes no economic sense"; Karp echoes; "you're not early anymore. You're right.") · "AI hallucinations have now become a legal liability" (NYT study) · ~Nov 2025 platform launch ("VibeML", $50 credit) |

---

## 7. What HIS hackathon brief rewards (github.com/oumi-ai/hack-with-oumi)

Oumi ran its own tracks at Nebius.Build SF (Mar 15, 2026) + Eclipse 6.0 (Apr 4–5, 2026). Their brief — authored by staff — is the clearest written signal of what an Oumi-side judge wants:

- **Theme was "SLMs for Voice Agents":** SLM <~10B params; "when fine-tuned for specific tasks, SLMs can even outperform much larger models"; latency-critical real-time use; "**multiple specialized SLMs working together** may achieve lower latency and better performance than a single large general-purpose model."
- **Judged on: Creativity · Real-world impact · Technical quality.**
- **Required:** fine-tune with Oumi, star the repo, "specific, realistic use case." Encouraged (not required): open weights.
- **Their suggested agent submodels to specialize** — a menu of what impresses: guardrails/LLM-judges, query rewriting, execution routing, retrieval routing, **model routing** (big model vs SLM), planner, verifier ("what would happen if we carried out the plan — is it a good idea?"), executors (plan→tool calls), memory management.
- Recommended reading in repo: "Small Language Models are the Future of Agentic AI" (arXiv 2506.02153), "Agentic AI Needs a Systems Theory" (arXiv 2503.00237), Stefan Webb's "Small Fine-tuned Models are All You Need" blog.

**Translation for THIS hackathon:** fine-tune ONE small open-weights model to own one sharp job inside your agent (router, verifier, guardrail, extractor, planner). That single move converts your project from "another agent wrapper" into a demonstration of his life's thesis — and makes you the only team whose agent literally *owns part of its brain*.

---

## 8. Scoring map — what a project should DO to win him

Mapped to the official criteria (usefulness · craft · aura) + his taste:

1. **Own a piece of the intelligence.** Include at least one fine-tuned open-weights SLM doing a real job in the pipeline (classifier/router/verifier/extractor). Best case: trained with Oumi OSS (star the repo, name-drop the config — he will check). This is the single strongest signal.
   - *If no training capacity:* use a small open model (Qwen/Gemma/gpt-oss via Ollama/vLLM) for a bounded subtask and **say why** — latency, cost, sovereignty. The reasoning is the point.
2. **Show the eval loop, not just the output.** Baseline number → failure-mode count → improvement. Even crude: "we built a 30-case eval set; generic model scored 63%; our fine-tuned router scored 91%; cost per call dropped 40×." That's his FAiE pitch in miniature — he'll recognize it instantly.
3. **Verifiability feature.** Any mechanism where the agent checks/grounds its own work (citation checking, plan verification, tool-output validation) echoes HallOumi — his flagship artifact and NYT-validated thesis. A "HallOumi-style verifier step" is a bullseye.
4. **Real work end-to-end on a real system.** His career is deployed systems (SignalGuru on real streets; PaLM to GA; production compounding). Emails actually sent, tickets actually closed, docs actually filed. Mocked CRUD = invisible to him.
5. **The tedious/multi-step framing.** Official hackathon framing — "tedious, multi-step, things nobody wants to do twice" — is precisely his enterprise-automation worldview (document classification, entity extraction, RPA-style workflows are his named examples).
6. **Cost/latency math on screen.** He thinks in "10× cheaper, 10× faster, higher quality" and 40–50× OSS deltas. One number slide quantifying cost-per-task vs frontier API = catnip.
7. **Compounding story.** "Every run makes it smarter" — log production failures as tomorrow's training data (even simulated). This is his Aug 2026 product; saying "the model learns from its own work" is his Nov 4 quote verbatim.
8. **Ownership/sovereignty angle for a Greek/EU context.** Data stays local; model runs on-prem/edge; no dependency that can be deprecated or repriced. He made a 400M-param on-device model a centerpiece anecdote — an agent with an on-device component would be a standout.
9. **Aura, his dialect:** live demo with real numbers (he demos live himself), one choreographed "model catches a failure the generic model missed" moment, and — tasteful — a Greek-flavored name/nod (he jokes in Odysseus himself). Do NOT overdo mythology kitsch; one line lands it.
10. **Recruiting adjacency.** Oumi is #hiring in Greece — a project showcasing post-training chops is effectively a job audition to a co-organizer who sponsors hiring-motivated tracks.

**Landmines — what loses him:**
- Agent buzzword bingo (MCP/sandbox/orchestration name-drops without working behavior) — he's explicitly fatigued.
- Pure prompt-engineering over a frontier API presented as "the product" — his entire thesis is that this is rented, generic, and fragile.
- No evals / "it seemed to work" — he'd ask for the baseline.
- Claiming reliability without a verifier — his NYT study is literally about unverified AI output.
- Vague mega-agent ("AGI assistant") — he wants "specific, realistic use case" (his hackathon wording).
- Slideware — the mandate he co-owns: "make it work and show us the demo. This is not a pitching competition, it's an agent at work."

---

## 9. Rapid-fire quote bank (for pitch/scripts)

- "Consume what is generic. Build and own what differentiates you."
- "The right model beats the biggest model."
- "A model built for everything is optimized for nothing."
- "Don't rent a generic tool. Build and own a specialized one."
- "Train the brain" (harness vs. model — Talking AI)
- "Learning from their own work" (agents that improve — Nov 4 launch)
- "You need evaluations for this problem… the most common failure modes."
- "Given enough eyeballs, all bugs are shallow" (Linus's Law — his governance stance)
- "The open community is still the sleeping giant of AI."
- "What ultimately wins is whoever can harness the most minds." (AI_dev talk)
- "Make it work and show us the demo." (hackathon mandate — co-signed ecosystem)

---

## 10. The Greece factor

NTUA undergrad → ICCS Athens (his first research post) → global career → back as Summit co-organizer, Oumi hiring in Athens, telling Archimedes/Athena-RC that **"Greece could be a key player and leader"** in open AI. He promotes the Summit as "the region's flagship event" and praises Nikoletakis's organizing publicly. A project that plausibly lives in the Greek context (Greek-language capability, Greek public sector/property/shipping/tourism workflow, local data sovereignty) gets double resonance: his thesis + his homeland agenda. Oumi literally has Greek staff building this ecosystem (Achlioptas, Aisopos, Anastasiou).

---

## 11. Confidence & gaps

- **High confidence:** career timeline, quotes (verbatim from transcripts/posts), product details, investor list, hack-with-oumi criteria, Athens hiring, Summit role.
- **Medium:** exact judge-panel composition (organizers haven't published judges; master brief's "likely lead judge" is inference), Oumi Athens office vs. remote-Greece (job posts say Athens hybrid — a physical hub is probable but unconfirmed).
- **Not verified:** whether the Ascend seed contributor is the Greek pre-seed fund (Ascend.vc hosts Oumi's Greece job posts — strong circumstantial), his sailing hobby (nautical quotes only), GenAI Podcast episode featuring him (podcast exists; EY episode found, his episode not confirmed).
- **Sources:** koukoumidis.com, oumi.ai (PR/blog/platform/company), LinkedIn posts, twstalker X mirror, Data Exchange transcripts ×2, Talking AI, AI Engineering Podcast, Startup Pirate, AI_dev sched+confpad, SiliconANGLE/TokenPost/GeekWire/PYMNTS/The Decoder, hack-with-oumi repo, Princeton DataSpace, ACM/USENIX records, Google Scholar, jobs.ascend.vc, genaisummitseeurope.com, hackathon.polymath42.com, eventsindex.org.
