---
title: "quintessential founders"
type: source
tags: [hackathon, genai-summit, recon, people]
aliases: ["quintessential founders"]
created: 2026-11-10
updated: 2026-11-10
status: active
---

# Quintessential — Founder Dossier (Gen AI Summit Hackathon, 14–15 Nov 2026)

**Recon date:** Nov 2026 · **Subject:** the three co-founders of Quintessential SFT I.K.E. (Chamosternas 16, Petralona, Athens — founded Feb 2018, ~20–30 people). Prize co-funder of the hackathon (€8.5k with Wonderful: €5k/€2.5k/€1k). One or more founders will judge.
**Companion file:** `deep/sponsor-quintessential.md` (company-level teardown). This file goes person-deep + compiles the literal rubric.

---

## FOUNDER 1 — Konstantinos "Kostas" Kopanidis
*Co-Founder & Managing Partner · systems architect · Conduit creator*

### Identity & history
- Full name **Konstantinos Kopanidis**, goes by **Kostas**. GitHub `kkopanidis`, X `@Kostaskopanidis`, LinkedIn `kkopanidis` (~1.3k followers), personal blog **kkopanidis.com** ("Tek and Kode", Ghost, launched May 2023 — bite-size tech posts; his newer writing migrated to the Quintessential blog).
- AUEB CS (Athens University of Economics and Business). Software engineer since 2013. Prior: **Lead Developer at Fingerwaiter LTD** (where Daskalakis was CEO/co-founder — the founders' history predates Quintessential), Founder/CEO/Lead Dev at **Fably**. Quintessential CEO 2018–2020, then Managing Partner.
- Self-description (kkopanidis.com/about): "I've dabbled with pretty much everything, from hardware engineering, networks and security to software development, DevOps, cloud and on-prem infrastructure… When not writing code, or creating system architectures, I mentor engineers, lead teams and run the day-to-day operations." Slide-deck tagline: **"I mostly break things."**
- Fortune Greece **40under40** (Nov 2023, age ~28, jointly with Charisis).

### Conduit — his architecture made flesh
- **github.com/ConduitPlatform/Conduit** — ~922–926★, 67–71 forks, **Apache 2.0** (site; repo header shows MIT — license drift), NodeJS/TypeScript, created Jan 2022, actively pushed Nov 2026, v0.17. Homepage getconduit.dev (which also serves `/llms.txt` — same agent-first pattern as the agency site).
- **What it is:** self-hosted, modular BaaS — "an OSS Firebase alternative" now positioned "**for the intelligence era**". Core orchestrates modules + config + service discovery; Router module = single gateway for REST + GraphQL + realtime. Modules: Authentication, Database (MongoDB/PostgreSQL, GraphQL), **Embeddings** (text-to-vector, queued backfills, semantic search — new), **Authorization** (fine-grained, relationship-based access), Storage (S3/Azure/GCS/local), Communications, Chat, Functions (webhooks/events). Docker Compose, k8s/Helm, CLI (`npx @conduitplatform/cli`).
- **2026 positioning is the tell:** "AI builds fast. Conduit starts ready." / "Your assistants can scaffold a backend in an afternoon. Conduit gives them a modular platform that's already built." / "**Use AI for speed. Your backend isn't generated — it's already built.**" There's a literal "Start with AI" onboarding prompt + `/docs/getting-started/with-llms`. His thesis: agents are fast at generating but you can't trust improvised infrastructure — the backend should be *configured* by agents, not *written* by them.
- **Original design thesis** (Fosscomm 2022 deck): "Most software requires the same things. Engineering talent is sparse. Time to market is difficult without huge budgets" → a "less code" platform that "makes you feel like you own it, not like a third party"; modular ("not force you to run all features when you only need 2"); extensible via micro-services; claims 80% fewer backend devs, ~30% less code even when extending. Production-proven inside Quintessential (BeWell app backend: Conduit custom service for push notifications in a pnpm/Lerna monorepo with shared `conduit-types`).

### Architectural taste (decoded)
- **Boring infrastructure, sharp seams.** Declarative, reviewable, auditable. IaC "turned out to be the agent's native language" — he prizes plan/diff/rollback because it gives agents a sane interface.
- **Sovereignty:** self-hosted by default, "You own the data", no vendor lock-in. Runs against "rented" black boxes.
- **Reuse over bespoke:** the entire Conduit thesis is that 70% of backend needs are commodity — don't regenerate them per project. Same instinct as their Cursor rules/skills/design-system-markdown rails.
- **Security realism:** agent = non-human identity, first-class IAM problem. See rubric §5.

### Talks
- **Fosscomm 2022** — "Conduit: An OSS Firebase Alternative" (Nov 2022).
- **Athens AI Summit 2026** (11 Nov 2026, Divani Caravel — 3 days before the hackathon) — billed speaker; conference theme "AI: from strategy to production operation". He is literally speaking on productionizing AI the week of the event.
- Personal blog posts: Tailwind, React Server Components, CSR evolution, "Why Software Architecture Matters", and the 2023 "Mastering DevOps" he publicly retracts/amends in the Oct 2026 Quintessential post.

---

## FOUNDER 2 — Socrates Charisis (Σωκράτης Χαρίσης)
*Co-Founder, Managing Partner & design lead · Figma Config 2026 keynote speaker*

### Identity & history
- LinkedIn `scharisis` (~4k followers), Figma community `@sochar3`, Dribbble `SocratesCharisis`, bento `sochar3`, personal site charisis.design ("Designing oceans, surfing on their waves"). Stockholm University exchange (Business IT/InfoSec).
- Actual marathon runner — the Config talk is built on the metaphor. Designlab mentor; **NN/g UMXC** (Nielsen Norman UX Master cert); **Friends of Figma Athens user-group leader**; Figma Community Advocate.
- Digitized'26 speaker (Dec 2026, Athens — Quintessential is premier sponsor). Into Design Systems Athens speaker (Oct 7, 2026).
- Co-founded Quintessential Feb 2018 (8+ yrs). "Leading business, design and all creative initiatives."

### Config 2026 keynote — "The Marathon Designer: creative endurance beyond prompts and pixels"
(June 25, 2:35pm PDT, ~21 min, video youtu.be/Rb2XLYSgn7A. His 4th Config, first as keynote.) The framework, per confpad summary + Quintessential posts:
- **Three-part practice: sustainable pacing · builder culture · versatile hiring.**
- **Versatile hiring = side projects over CVs:** hired "one unlookable hire from 56 applicants" because of side projects (variable fonts, iOS games, NFT art) — paid off. Quintessential's recruiting line verbatim: "A tiny game, a weird tool, something you built just for the sake of it — that's what makes you stand out."
- **Builder culture = "maker months":** every other month, Friday mornings, 3 hours of free making → produced Figma plugins, internal tools, a route planner that generated a client lead, an in-house short film.
- **Sustainable pacing:** ran a full in-house rebrand while delivering ~20 heavyweight projects across seven domains; pacing rules "stop burnout at the 30 km point". Talk chapters include "Trading ideas for execution" and "AI won't replace human creativity". Tagline: **"Design's biggest threat isn't AI — it's burnout."**

### Design Fleet — his agent-governance artifact (IDS Athens, Oct 2026)
- Talk: "Design Systems: Born Again. Teaching Agents to Ship High-Quality Components."
- **Design Fleet**: a shared design standard for **Codex, Cursor, and Claude Code** that "enforces design rules, acts as a written project contract, and **fails the build when standards slip**." Described by the meetup recap as their "custom agent network for client codebases."
- The core rule, verbatim: **"every piece of knowledge must prove the AI didn't already know it, and gets deleted when it catches up."** Backed by before/after examples and hard metrics from real client work.
- His framing: "agents must do all the labor so we focus on the craft and raise the bar in the output."

### Portfolio/taste signals
- Dribbble shots: **Carge EV-charging UI** (client work), **PS5 DualSense UI vector freebie**, **Figma Cards UI game**, a **Michael Jordan digital portrait**, custom iconography for Greek Nomads, community-poster work. Mix of client UI + playful self-initiated pieces (the maker-months energy, public).
- Figma community plugins (`@sochar3`): **UI Gems** ("designs from the world's best products"), **Essential Tokens** ("parse tweakcn variables, match your shadcn theming, scan & search variables, print colors & type"), **"print my type"** — he ships design tooling, not just screens.
- Personally builds in code: authored the BeWell post — "me shaping the experience and the interface in code, Spyros holding the architecture." Cursor + Claude Opus 4.6, Expo previews, on-device feel testing.
- He wrote THE sponsorship rubric post (Oct 5, 2026) — see §5.

---

## FOUNDER 3 — Alexandros Daskalakis
*Co-Founder & Managing Partner · the senior commercial hand · confirmed attending*

### Identity & history
- LinkedIn `daskalakisalexandros` (~2.5k followers). Headline: "Turning product ideas into shipped software | Co-Founder @ Quintessential SFT | Serving tech & product leaders in Europe & North America." Agia Paraskevi, Athens. **~23 years experience** — the veteran of the trio (the other two are ~early-30s).
- Founder/Partner **Techalise** (Aug 2013–present, small digital agency — Quintessential's predecessor DNA). **CEO/Co-founder Fingerwaiter LTD** (where Kopanidis was lead dev). VP **Vespr** (2018–20 — the founders' own dating-app product, later a Quintessential portfolio piece). Director of BD **ebnb.gr** (2017–18). Quintessential co-founder since Jan 2018.
- **Confirmed attending:** reshared the GenAI Summit hackathon announcement Oct 3, 2026 with "**See you all there!**" #AgentsAtWork #Hackathon. Also reshares craft content (BeWell technical post: "Always proud of the team and the friends we sometime call 'clients'").

### BD philosophy — what it means for judging
- His April 30, 2026 post "A small reflection on growth and business development": tried structured outbound, concluded "Not every accepted growth tactic is the right tactic for every company… the best relationships have usually started in a more natural way. Through trust, reputation, shared problems, meaningful conversations, and a genuine interest in what someone is trying to build." Took personal responsibility when outreach "felt a little too automated": "**More thoughtful. More relevant. More human. More us.** Because growth matters, but alignment matters more."
- Read: he judges like a buyer. Authenticity, real relationships, and a real customer with a real problem will land harder with him than technical theater. He is the "for a real customer" clause in the rubric, personified.

---

## THE BLOG CANON — their literal rubric, in their words
*(All 6 posts on quintessential.gr/blog read exhaustively. Attribution: DevOps + front-end posts are Kopanidis's voice — they continue his kkopanidis.com 2023 series; design/craft posts are Charisis's voice — "sitting at the founder's table", designer-in-code.)*

### Post 1 — "Did you make this, or was this AI?" (Feb 16, 2026 · AI · Charisis)
- "**The real question is not whether AI was involved. The real question is whether the human was.**"
- "No, AI didn't make this. I made this with AI. That distinction is everything."
- "People assume AI requires minimum effort. So they put in minimum effort. They prompt a couple of times, accept the initial outputs, and ship it. The result is slop."
- "**Slop is not an AI problem. Slop is a human problem.** The variable is not the tool. The variable is who's holding it."
- "The moment you accept that what you've built is AI's and not yours, you stop caring. You disengage. You become a passenger." → dispatcher vs. driver framing: "The first framing turns you into a dispatcher. The second keeps you in the driver's seat."
- "**The work isn't in the generation. It's in the curation.**" — "you don't know which outputs to reject. You don't know which details matter."
- "**Stop asking: 'Did you make this, or was this AI?' Start asking: 'Is the maker visible in the work?'**"
- "Craft was never about the specific motions of your hands. It was about the quality of your decisions."
- "AI can generate. But it can't care. **And care is still the rarest ingredient in good work.**"
- "I made this with AI. The AI did the labor. I did the craft."

### Post 2 — "Design is dead" (Jan 5, 2026 · Design · Charisis)
- Anti-process-compliance: the old lane was "efficiency inside an inefficient lane"; fighting over a sidebar icon for a week = "**discreet punishment**".
- "**AI lowers the floor and raises the ceiling.**" / "More people can enter the field, but only those who reskill can climb to the new heights."
- Reskilling > upskilling: prototype in code, Three.js/WebGL, React Native, "commands like npm can be as natural as choosing a font weight", "use AI as a co-designer… do your design dishes."
- "**The reskilled designer is not a pixel pusher, nor a prompt jockey. They are ultimate craftspeople and orchestrators of possibility.**"
- The anti-slop aesthetic clause: we are in an "AI 'sameness' era, where it is now possible to tell which product, website, image, flow, is AI made (they all look the same). **Be the one who brings in the missing expressiveness, and the lost delight in details.**"
- "Design must always begin and end with humans — with our intent, our taste, our imagination."
- Measured by: "how clearly they define intent, how courageously they explore expression, and how seamlessly they bridge imagination with execution."

### Post 3 — "The Last Mile in agency work" (Feb 26, 2026 · Design · founder voice)
- "Projects break right before release." At 80–85% "the brain checks out early… the last mile isn't heavy work. It's **careful work**."
- "Most last-mile problems are born early" → unclear success criteria, vague scope, postponed decisions = "paying interest on early decisions."
- "Everyone imagines a different last mile — unless it is **ruthlessly defined** by someone with ownership and self-agency… 'this is what done looks like, this is the pace, this is when we ship.'"
- Craft checklist, verbatim: "**the pixel-perfect details. The edge cases. The error states. The loading experiences. The copy that nobody reads until something goes wrong.**"
- Last mile = "a mode switch": explicit definition of done, frozen scope, fast decisions, daily alignment, "leadership when energy is gone."
- "**Projects ship once. Reputation compounds.**"

### Post 4 — "Designed and built in code: BeWell" (Sep 28, 2026 · Product · Charisis + Spyros Sellas)
- "**Vibe coding is accepting whatever the model gives you. Designing in code means** the interface idea that used to take days on a canvas now gets crafted once at high fidelity, then translated directly into production."
- "With AI handling the labor, **we invested every hour it gave back into quality.**"
- "**You have to know when the model is bluffing.**" (RN specifically: "the confidence stays high while the accuracy drops.")
- "I broke things. Hardcoded color values where tokens should be. Drift from the design system markdown… **Two decades of product context is the difference between building with AI and producing slop with it.**"
- "This works because of the setup, not despite it. A developer sets up the environment. **Rules, skills and templates keep the project on rails.** I know what I don't know."
- What they chose to brag about = their taste bar: real squircles (`borderCurve:'continuous'`, not oversized borderRadius; honest Android fallback "not a compromised clone"), native `NativeTabs` liquid glass "no fakery", haptics "on everything" via `selectionAsync`, a scroll-morph `ScreenCard`/`ModalCard` system reused across screens, floating hearts/hourglass micro-delights "**nobody needed — that's exactly why they matter**", design tokens in CSS vars + cva variants + shared types across monorepo, CMS deep enough that clients never touch code.
- Process flex: one-pager instead of brief → working Figma Make prototype at meeting 2 → ~1.5 months net for a 31,000-person festival app.

### Post 5 — "Un-mastering DevOps" (Oct 23, 2026 · Software Dev · Kopanidis)
The **agent-in-production doctrine** — the single most rubric-like artifact they own:
- "The newest member of the team isn't human." Their engineers "increasingly start incidents by **reviewing** an agent's triage instead of doing the triage."
- "An agent that touches infrastructure is **a non-human identity**. Treat it exactly like you'd treat a new privileged service account": own identity (never shared/human creds) · least-privilege scoped credentials · time-bounded tokens · tool allowlists · full audit trail ("every action attributable, every session reconstructable").
- **The five patterns that work, verbatim:** 1. **Gateway-mediated access** — "the agent doesn't talk to prod. It talks to a broker that enforces policy, scopes what it can see, and logs everything." 2. **Read-only by default** — "start here. Most teams should stay here longer than they want to." 3. **Writes only through PRs** — "No direct kubectl, no console access, no 'just this once.'" 4. **Human approval for prod mutations** — "an actual review of an actual diff," not a Slack rubber stamp. 5. **Blast-radius limits** — "design the ceiling before the incident, not after."
- "**GitOps became the safety layer for agents**… the merge gate is the point." / "The plan/apply review gate matters more now, not less. The value is **compressed authoring with human judgment at the gate.**"
- Threat model: "**The failure mode is not rogue AI… The failure mode is a human wiring an over-privileged agent into prod on a Friday**, skipping the guardrails because the demo went well… **the threat model is us, moving fast.**"
- New first-class practice: "**agent identity and access** — scoped credentials, allowlists, audit trails, offboarding." Owned by the platform team; "if nobody owns the paved road, agents will drive off it."
- Adoption advice: "Give agents the boring work first" (triage, drift detection, log summarization, PR-shaped fixes); "Keep humans at the merge gate"; "Treat agent identity as seriously as employee offboarding."
- Kicker: "The workflow still isn't seamless. **But the seams are where the humans belong.**"

### Post 6 — "Mastering front-end development" (Jun 2023 · Kopanidis)
- Fundamentals over framework-of-the-month: state lives in URL/storage/cookies/server not just Redux; back/forward/refresh/tab/enter must work; keyboard accessibility "a priority, not an afterthought"; "don't be a 'React Developer'… be an excellent front-end developer who happens to use React." → They notice broken web basics. A demo where the back button kills the app = blood in the water.

### Their own machine-readable posture
- quintessential.gr serves `/llms.txt`, `/index.md`, `/agent-view.md`, `Accept: text/markdown` content negotiation, `/.well-known/ard.json`, **`/.well-known/agent-skills/index.json` publishing SKILL.md files**, and `/404.md` that "answers HTTP 404… never a 200." They built the agent-consumable website they want contestants to build. Same pattern on getconduit.dev. **This is dogfooded doctrine.**

---

## ALETHEIA AI — the practice
- Ἀλήθεια = "truth": "**truth is uncovered, not stated. Same with AI: it's not a product you buy, but a capability you build** with experienced people." Anti-consultancy positioning: "Most AI consultancies sell you a strategy document and disappear. **We stay until the job is done** — until AI is embedded, adopted, and delivering measurable outcomes."
- Four offerings: AI Strategy & Roadmapping ("a roadmap your leadership can act on — **not file away**") · Process Automation & Agentic AI ("agents that execute complex multi-step operations **without human bottlenecks**") · Custom AI & LLM Implementation (fine-tunes, RAG, "we build the right thing — **not the trendy thing**") · Training/Workshops. Process: Discovery & Audit → Strategy & Design → Build & Integrate → Deploy & Embed. Claims ISO 27001, "30+ expert team", cross-industry (fin services, healthcare, manufacturing, public sector, travel, telecoms, shipping, retail).
- **Named-client evidence for AI specifically is not published as case studies** (portfolio pages are product builds). What exists:
  - **NBG / Waiz**: brought in 2021 to lead the full design+dev revamp of National Bank of Greece's money-management app (multi-bank aggregation: Alpha, Eurobank, NBG, N26, Piraeus/Winbank). Multi-year banking relationship = their enterprise trust anchor; Aletheia sells into exactly this account profile.
  - **Up Hellas**: repeat client (2024 rebrand site → FlexOne benefits platform). Signal: Up Hellas is now hiring an in-house "Web & Agentic AI Specialist" (Nov 2026) — their ecosystem is going agentic on rails Quintessential built.
  - **In-production claims (their words):** the DevOps post is written from "my experience **running this for clients**" — i.e., they operate agent triage/guardrail setups on client infra today. Agents "handle incident triage, routine-fix PRs and drafted pipelines" for them internally. BeWell shipped "automated uploads" agentic CMS features mid-launch.
  - **Design Fleet** = their productized agent-governance layer for client codebases (rules contract, fails builds). Likely the seed of the teased "**AI Labs**" nav item ("Soon").
- War-story texture they repeat: production incidents at 3am, App Store review roulette ("be proactive about permissions… have a fallback for the ones you can't defend"), expedited review to hold a launch date, staging-vs-release client fear ("release is exposure — make the release date real").

---

## THE QUINTESSENTIAL JUDGE'S MENTAL SCORECARD
*(Synthesized; every row traces to a quote above.)*

| # | Question they're silently asking | Pass | Fail |
|---|---|---|---|
| 1 | **Is the maker visible in the work?** | You can defend every choice — what you rejected, why this tool, where you overrode the model | "The AI built it" energy; can't explain your own code |
| 2 | **Does the agent do real work end-to-end?** | Goal → plan → tools → verified output, live, on a tedious multi-step task for a named user | Chatbot-in-a-trench-coat; narrator demo; mock data theater |
| 3 | **Is it on rails?** (guardrails by construction) | Scoped tool allowlist, least-privilege identity, plan-vs-apply/dry-run, human gate on irreversible writes, audit log | Root token YOLO agent — to them that's not naive, it's *the threat model* |
| 4 | **Did curation beat generation?** | Evidence of rejected outputs, evals/sanity checks, knowing "when the model is bluffing" | Prompt-twice-ship-it; flawless-theater demo that breaks on input #2 |
| 5 | **Last-mile craft** | Error states, empty states, retries, timeouts, loading UX, the edge case handled; ONE signature detail "nobody needed" | Stock-gradient slop UI; happy-path only; AI sameness aesthetic |
| 6 | **Right thing, real customer** | A specific workflow/persona with real pain (ops, banking-adjacent, DevOps, admin drudgery — bonus if Greek-market-real) | Generic "chat with X"; idea that dies Monday |
| 7 | **Honest engineering** | Typed contracts, monorepo-ish shared types, reuse (Conduit/MCP/skills) over bespoke slop, boring-proven infra | Hand-rolled auth/backend an agent improvised (their Conduit pitch is literally "don't") |
| 8 | **Aura / maker energy** | Weird, joyful, personal; side-project soul; a detail that makes judges grin | Corporate sameness; deck-first team; pre-built project (they weigh the 36h window) |
| 9 | **Fundamentals** | Back button works, keyboard works, states are real | Broken web basics (their 2023 canon still applies) |
| 10 | **Post-hackathon survivability** | "A meaningful idea reaching its starting line" — something that could be a real product/customer Monday | Demo-ware built to win, not to live |

**Instant-fail signals:** slop admissions ("we just prompted it"), over-privileged agent credentials, vibe-coded incomprehension, pitch-deck polish over working software ("this is not a pitching competition").

---

## WHO LIKELY JUDGES

| Founder | Probability | Evidence |
|---|---|---|
| **Socrates Charisis** | **HIGH** | He *authored* the sponsorship rubric ("We're not going to look for the flashiest demo… **right thing, right rails, real customer, no slop in the UX**… **We'll be there** with industry leaders"). He is the public face of the prize and their craft doctrine. If one founder judges, it's him. Expect him to probe UX, design decisions, and "what did the human decide?" |
| **Alexandros Daskalakis** | **HIGH (attending) / MEDIUM (judging)** | Explicitly confirmed attendance ("See you all there!"). BD lens → he'd score the "real customer" axis and team dynamics. Could be judge or roving sponsor-mentor. |
| **Konstantinos Kopanidis** | **MEDIUM** | Speaking at Athens AI Summit Nov 11 (same week, Divani Caravel) — in town, in "production AI" mode. His guardrail doctrine is the technical rubric; if he judges, expect questions about agent identity, tool scoping, failure modes. Slightly less public about the hackathon specifically. |

**Scenario read:** Charisis + Daskalakis near-certain in the room; Kopanidis probable. Team could split duties: Charisis on craft/UX, Daskalakis on usefulness/customer, Kopanidis on rails/architecture. Prepare for all three interrogation styles in one demo — it decomposes exactly into usefulness / craft / aura + rails.

---

## PROBABLE CHALLENGE BRIEF (if they author one)
Briefs are announced at the event; the official theme is fixed ("agents doing real work — the tedious, the multi-step, the things nobody wants to do twice"). A Quintessential-flavored challenge, mapped to their canon:

1. **Most likely: the guardrailed ops agent.** An agent that completes a multi-step business/ops workflow end-to-end *with* scoped permissions, a human approval gate, and an audit trail. Their DevOps post is a ready-made spec: gateway/broker, read-only default, writes-via-PR, blast-radius ceiling. A "propose → human merges" loop demo would hit all five patterns in miniature.
2. **Strong alternate: agent-consumable interfaces.** Make a real-world service legible to agents — tools/MCP/SKILL.md/structured surfaces. They built `ard.json` + agent-skills for their own site and Design Fleet for codebases; "something people **and agents** want" is the event tagline they co-signed.
3. **Dark horse: the last-mile agent.** An agent that does the finishing work nobody does twice — QA sweeps, edge-case/error-state coverage, release checklists, docs. Direct lift from "The Last Mile."

Whatever the brief, their scoring overlay is fixed: **right thing · right rails · real customer · no slop in the UX.**

## TACTICAL NOTES (aimed at this judge)
- Say the quiet part in the demo: "agent has scoped tools, proposes via PR/diff, human approves irreversible actions, everything logged" — that's quoting their doctrine back to them.
- Demo a failure caught and escalated, not just the happy path. Trust is built there (their words, twice).
- Show one human decision the model didn't make — the rejected output, the override. That's "the maker visible."
- One signature craft detail (your domain's squircle/haptics equivalent) beats ten half-features. Then nail the boring fundamentals: error/empty/loading states, back button, timeouts.
- If you can make your artifact agent-legible (skill file, MCP tool, clean schema), you're speaking their newest dialect — they literally publish SKILL.md files for their own agency.
- Bonus resonance: a real Greek/customer-adjacent workflow (agency ops, benefits/HR admin, DevOps triage, banking-adjacent, festival/event ops) over generic demos.
- Name-drop nothing; show everything. "This is not a pitching competition, it's an agent at work."

---
*Sources: quintessential.gr (+ /llms.txt, /agent-view.md, all 6 blog posts, Aletheia + Waiz + Up Hellas pages), kkopanidis.com, github.com/ConduitPlatform/Conduit, getconduit.dev, pretalx Fosscomm 2022, EELLAK Conduit deck PDF, config.figma.com speakers, confpad.io Config 2026 recap, everydayux.net Config takeaways, luma.com/ids-athens + recap posts, LinkedIn (scharisis, daskalakisalexandros, kkopanidis, quintessentialsft), dribbble.com/SocratesCharisis, figma.com/@sochar3, hackathon.polymath42.com, ai-athens-summit.gr, digitized.gr, fortunegreece.com, linkedin.com/company/quintessentialsft workforce data.*
