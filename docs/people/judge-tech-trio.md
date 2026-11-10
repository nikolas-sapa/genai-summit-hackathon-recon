---
title: "judge tech trio"
type: source
tags: [hackathon, genai-summit, recon, people]
aliases: ["judge tech trio"]
created: 2026-11-10
updated: 2026-11-10
status: active
---

# Deep Dossiers — Technical Organizing-Team Trio (likely judges)
GenAI Summit Hackathon, Athens LifeTech Park, 14–15 Nov 2026 · Finals on GenAI Summit 5 stage @ SNFCC Mon 16 Nov
Judging criteria (verbatim from hackathon site): **usefulness · craft · aura points**. Mandate: "make it work and show us the demo. This is not a pitching competition, it's an agent at work."
Companion to `../judges.md` (has the shallow versions). This file = the deep cuts.

---

## 1. Menelaos "Mene" Mazarakis — product craft personified

### Who he is right now (Nov 2026, verified)
- **Founder & Managing Partner, Mene Capital** — his own early-stage vehicle. Thesis is anti-thesis: backs "unpattern-matchable founders" (his ETN Espresso framing at Panathēnea, 2 Jun 2026): "every great business, team and product is premised on a secret," the right time for OpenAI/SpaceX was years before they were hot. Predicts Silicon Valley will NOT lead physical AI/robotics manufacturing. Side project: "Everything is Factory Tour" (5 cities, 5 factories, 5 days, filmed doc).
- **Just exited Anon** — he was founding team / Head of Product & Growth (Jun 2024→). **Anon was acquired by Sierra (Bret Taylor's agent co) announced 5 Nov 2026 — NINE DAYS before this hackathon.** The deal is the freshest thing in his life. Anon = "Plaid for AI agents" (USV's words): user-permissioned auth layer so agents can act as users on sites with no API. Raised $13M+, hundreds of customers, hundreds of thousands of production browser-agent tasks. CEO Daniel Mason: "Reliability is the hardest problem in browser use" — they solved MFA, hours-long runs, failure recovery. He lived the hardest version of "agents at work" — agents that break in prod.
- Prior: Chapter One first hire → Partner & Head of Product (2021–Aug 2024), ran the $50M product/design-first web3 fund. Instagram PM Civic Products (US2020: 75M reached, 4.4M voter registrations — "largest voter turnout operation in US history"; offense AND defense). Facebook Misinformation/Integrity PM. Novi (Meta crypto wallet) PM. Google AI APMM (TensorFlow, Quantum marketing/policy). Wharton + Universidade Nova de Lisboa; Princeton RA; UN/EU advisor early career; Kenya mobile-payments research → Novi "aha" (move money "at the speed of a text message, cost of a fraction of a percentage point").
- Bio line: "tinkering indefinite optimist" / "do we participate in a politics of cynicism or a politics of hope?"

### Greek ecosystem role — he's an insider, not a visitor
- **Panathēnea 2026 speaker + moderator** (the festival co-hosting this hackathon): moderated Markus Villig (Bolt founder) opening keynote "Secrets of the Untracked Path," Shuo Wang (Deel) "$1.5B ARR hidden systems," and the Lowercarbon panel on energy/material-abundance investing. The moderator slots = organizer trust — they hand him their biggest guests.
- Panathēnea's own LinkedIn announcement frames him as ecosystem bridge: "helping startups since 2020… product, growth, and early-stage investing."
- Signal/NFX profile, Crunchbase angel (Caretta pre-seed).

### Product philosophy (what to quote back at him)
- Chapter One manifesto (he was Head of Product, this is his voice): products create "magical moments of speed, human connection, and learning"; broad adoption "starts with a single, groundbreaking, yet unrealized product opportunity accessed through intuitive, elegant, and familiar-feeling user experiences." Human-centered design as the unlock for frontier tech.
- "Unpriced is the new underpriced" (Mar 2025 tweet — his most-cited aphorism).
- Defended Meta's civic/political-content policies publicly — he believes products carry societal weight and ships through the controversy anyway ("just keep shipping," "internal mentality and focus on impact is right").
- Investor lens at Mene Capital: secrets + non-consensus founders, not demo-day pattern matches. He literally warns AGAINST judging by pattern.

### In the judging room — what makes him argue FOR a team
1. **Product craft as the criterion.** He owns "craft" and "aura" on the rubric. Elegant, intentional, opinionated UX on an agent = his love language. A demo with one perfect interaction beats ten features.
2. **Reliability realism.** He just spent 2 years selling the truth that "AI computer use software is great for demos but not reliable in production" (Anon homepage, his positioning). An agent that visibly handles failure, retries, edge cases in the LIVE demo — especially a long-running/multi-step task that doesn't die — gets him defending you.
3. **Agentic-web literacy.** Delegated auth, acting-as-user, sessions, permissions, the 70%-of-the-web-without-APIs problem — he will probe exactly here. Don't fake "our agent logs in for you" — he built the company that does this and knows where the bodies are buried.
4. **A secret, not a trend.** Mene Capital's thesis: show the non-obvious insight ("every great product is premised on a secret"), not "agents are hot."
5. **Civic/social resonance.** Voting, access, institutions, boring-but-load-bearing workflows. A "politics of hope" flavor lands personally — he spent his Meta years on exactly this.
6. Kill shots: thin frontier-API wrapper, no named user, fake reliability claims, pattern-matched "X for agents" pitch.

---

## 2. Dr. Dionysis Zindros — verify, don't trust

### Who he is
- **CEO & co-founder, Common Prefix** — ~29-person research+engineering firm across 15 countries, Athens-rooted, Palo Alto time-split. Tagline that matters for this hackathon: "Our products use **agent-driven formal proofs** to reduce risk." They literally run AI agents in production to write Lean 4 proofs — and the posture is pure Zindros: "**The proof is checked, not trusted. Lean either verifies it or it does not.**" Their XRPL formal-verification engagement (Lean 4 model ↔ C++ `xrpld` differential harness, bit-for-bit) surfaced real deployed bugs.
- **Took lead stewardship of the entire Axelar Network (Dec 2025)** — owns its tech, product, vision: permissionless PoS interoperability hub, 2026 roadmap = co-staking, institutional readiness (privacy/compliance), gasless bridging, new asset classes. Attended Sibos (SWIFT's payments conference) en route to this Summit — institutional agent/payments plumbing is his current commercial context.
- Stanford post-doc w/ David Tse (EE). PhD cryptography, U. Athens (Aggelos Kiayias). NTUA MEng. Ex-Google Security Incident Response (Zürich), Twitter Product Security (encryption/compression research), IOHK (built Cardano), co-invented OpenBazaar. Published IEEE S&P, CCS, FC, DISC, ESORICS, AFT; Black Hat EU/Asia talks. Teaches Blockchain Foundations grad course at NTUA (marabu.dev). Hosts **Honest Majority** podcast. Ethereum Foundation grantee.

### Research spine (the papers he'd cite in conversation)
- **NIPoPoWs** — Non-Interactive Proofs of Proof-of-Work (FC'20, w/ Kiayias & Andrew Miller): succinct proofs a chain is what it claims; foundation of superlight clients + sidechains. Follow-ons: superblock compact storage, gas-efficient Solidity Bitcoin client (AFT'20), Velvet fork (AFT'21), **Blink: optimal proof of PoW** (FC'25), Mining in Logarithmic Space (CCS'21).
- **Sidechains/interop**: PoW sidechains (FC'19 WS), **Proof-of-Stake Sidechains** (IEEE S&P'19 — first rigorous PoS construction), SoK: Communication Across Distributed Ledgers (FC'21 — THE interoperability survey), proof-of-burn (FC'20), Rollerblade cross-ledger emulation.
- **Consensus foundations**: pod (DISC'25 — optimal-latency, accountable generalized consensus, spun out as "pod network" startup by his students), Consensus Under Adversary Majority Done Right (FC'25), Better Safe Than Sorry recovery, Light Clients for Lazy Blockchains, On-Chain Timestamps Are Accurate, better PoW fork-choice rule.
- **Payments/trust prehistory**: Trust Is Risk (FC'17 — decentralized trust for finance, his first paper), Brick payment channels (FC'21), Principal-Agent Problem in Liquid Staking (FC'23 WS), Hours of Horus keyless wallets, Soft Power soft-fork upgrades, Cryptocurrency Egalitarianism.
- Shipping: Kevlar + Patronum (verified Ethereum RPC proxies — distrust your RPC, verify responses against trusted hashes), XRPL payment-system spec, Bitcoin MPC/threshold sigs.

### Worldview (he states it flatly)
"Let's use cryptography and political code to build systems **beneficial to all and owned by no one**." Decentralization, privacy, transparency demanded FROM the powerful; supports Signal/Tor, pirate-friendly copyright; publishes CC, codes GPL/MIT. "I appreciate elegant foundational research, but also the pragmatic deployment of real applications." Dislikes authority, hand-waving, and unverifiable claims. Blockchain ethics is a stated interest.
- On agent payments/x402: **no public artifact found tying him to x402 specifically** — closest is XRPL payment-system spec, Axelar interop stewardship, Sibos attendance, and "institutional readiness" work. If you pitch x402/agent-commerce, do it as *protocol rigor + verifiability*, not hype — he'll know the payment-channel literature cold (he wrote parts of it).

### In the judging room — what makes him argue FOR a team
1. **A claim that's actually verified.** His life's work = succinct proofs of claims. An agent whose output is machine-checkable — citations that resolve, a checker, a test that runs, a proof artifact, a replayable trace — maps 1:1 onto "checked, not trusted." Show the verifier, not the assertion.
2. **Agents + trust rails.** Agent identity, attestations, signed action logs, on-chain or cryptographic accountability, verified delegation ("prove you were authorized to do that"), agent-to-agent commerce with real settlement = his intersection. XRPL/Axelar-adjacent plumbing especially.
3. **Adversarial honesty.** Threat-model your own demo out loud: "here's how this fails, here's how a malicious tool/user breaks it, here's our bound." A security mindset (ex-Google IR) — he finds the edge case; beat him to it.
4. **Foundational elegance + pragmatic ship.** A clean abstraction doing real work — he respects both the theorem and the deployment.
5. **Open source.** GPL/MIT ethos; public repo, inspectable prompts/traces, reproducibility score.
6. Kill shots: "trust us" claims, metrics without methodology, blockchain-buzzword garnish without a trust argument, centralization-dressed-as-decentralization. He will ask the one question your hand-wave can't survive.

---

## 3. Tim (Efthimios) Gianitsos — measurable improvement or it didn't happen

### Who he is
- **Research Scientist, AMD (May 2026→)**, AI Research, SF. Previously Senior MTS (Jun 2025–May 2026); joined via **Lamini acquisition** (MLE, Jan–Jun 2025, LLM fine-tuning). Before: freelance deep-learning consultant (2.5 yrs), Stanford MS CS/AI, UT Austin BS, **Amazon SDE** (his "ex-Amazon" line).
- Member of **AMD GenAI** team (amdgenai.github.io): fully open-source foundation models — **Instella** family (Math = "first math LLM with long-CoT RL on AMD GPUs," MoE 16B-A3B, Long, T2I) trained on MI300/MI325 — everything released: code, weights, recipes.
- **NeurIPS 2025 tutorial presenter** (Mexico City, Dec 2025): "How to Build Agents to Generate Kernels for Faster LLMs" — listed presenter as Efthimios Gianitsos (AMD), alongside Sina Rafati, Hao Li, Sharon Zhou + Stanford/GDM/Arm/Nvidia/Meta/Modular/UCI/MLCommons collaborators. The tutorial's core loop is EXACTLY a hackathon-relevant pattern: LLM agent → generate kernel → **compiler/profiler feedback as tools** → iterative refinement → **correctness validation** → automated benchmarking → **runtime/profiler metrics as reward signals** → inference-time scaling. Datasets: KernelBench, KernelBot.
- Adjacent to **GEAK** (AMD's agent family for GPU kernel generation): GEAK-Triton v2 = OptimAgentv2 + OpenEvolve — multi-offspring evolution, hardware-aware feedback, quality-diversity search, up to 3.42× speedups; slime Day-0 support for multi-turn kernel-agent RL training.
- Built **AMD AI Academy's first mini-course: "Reinforcement Learning with LLMs"** (Feb 2026): ~30 min covering OpenAI/DeepSeek/Qwen RL algorithms + math primer; his stated lens: "RL algorithms are affected by constraints imposed by GPUs… getting a model to learn both efficiently and stably on any hardware is a challenge." Colleagues contributed inference-engine + MI300X lab-notebook modules. Made the quiz "hard enough that a frontier LLM won't get all the answers right."
- Teacher DNA: CS109 head TA ~2 yrs + summer lecturer at Stanford ("I can attest to the benefit that a strong foundation in probability affords"). 
- Fun/credible crossover: **LaTeCH-CLfL 2019 paper "Stylometric Classification of Ancient Greek Literary Texts by Genre"** (Quantitative Criticism Lab, w/ Chaudhuri/Dexter — ML on classical Greek texts) + TAPA 2025 Latin stylometric criticism co-author. GitHub: CS236G GAN course, emoji-gan, english-diachronic-corpus.

### Technical cares (his own words)
- RL as "the missing ingredient that turned neat autocomplete into problem-solving chatbots," now accessible via open source + GPU memory.
- Hardware truth: algorithm↔GPU constraint coupling; efficiency AND stability; memory hierarchy, occupancy, batch-size multiples, profiler literacy.
- Verifiable reward: profiled latency/throughput/energy as the reward signal — not vibes, not LLM-judge alone.

### In the judging room — what makes him argue FOR a team
1. **Numbers on screen.** Speedup %, tokens/sec, cost/task, accuracy delta, before/after — measured live in the demo. His whole job is turning runtime metrics into reward signals; a project that quantifies its own improvement loop speaks his language natively.
2. **Self-improving agent loops.** Generate → measure → feed metric back → iterate, inside the demo. Bonus: a real reward signal (test pass, latency, $) rather than "the LLM said it was good."
3. **Evals as first-class.** Correctness validation harness, regression set, "here's our KernelBench-style eval for this domain." He'll respect a 36-hour project that built its own grader.
4. **Efficiency/hardware awareness.** Small models where they suffice, inference-cost accounting, quantization/batching awareness, maybe ROCm/open-weights flavor (AMD pays him; AMD GenAI's creed is open models). Runs-anywhere efficiency > frontier-API burn.
5. **Teachability.** He's a lecturer — a demo that explains its mechanism crisply ("here's the loop, here's the reward") wins. Clarity of mechanism = craft.
6. **Greek-heritage resonance.** He literally published ML on ancient Greek genre classification — a classics/Greek-language angle is a personal bullseye if it arises naturally.
7. Kill shots: unmeasured claims, LLM-judging-itself as the only eval, wasted compute for show, mystery-meat architecture he can't interrogate.

---

## Synthesis — the trio's shared frequencies

| Judge | Core identity | Argues FOR | Sniffs out instantly |
|---|---|---|---|
| **Mene** | Product craft + non-consensus secrets; just exited agent-infra to Sierra | Elegant opinionated UX, named user, failure handling shown live, "the secret" | Thin wrappers, pattern-match pitches, fake reliability |
| **Dionysis** | Checked-not-trusted; agent-driven formal proofs in prod | Machine-verifiable outputs, trust rails, self-aware threat model, OSS | Unverifiable claims, buzzword crypto, hidden authority |
| **Tim** | Measurable improvement via benchmark reward signals | Live metrics, self-improving loops, real eval harness, efficiency | Vibes-based evals, unmeasured "it works," compute waste |

**The overlap play:** a working agent doing a tedious multi-step job end-to-end **with a visible verification/eval layer** (checked outputs, measured deltas) wrapped in **one beautifully-crafted interaction** and a **non-obvious insight** about why this agent should exist. That single configuration simultaneously feeds Mene's craft+secret, Dionysis's verifiability, and Tim's measured-reward frequency. Aura points live exactly at that intersection — taste backed by proof.
