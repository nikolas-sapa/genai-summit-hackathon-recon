---
title: "crowdcruit alwaysonline"
type: source
tags: [hackathon, genai-summit, recon, sponsors]
aliases: ["crowdcruit alwaysonline"]
created: 2026-11-10
updated: 2026-11-10
status: active
---

# Deep Dossier — Crowdcruit + Always Online (small Greek sponsors)
Gen AI Summit Hackathon, Athens LifeTech Park, 14–15 Nov 2026. Both = bottom-of-list partner logos → likely **Supporter tier (€2k)**: table + CV opt-in recruiting, NO own challenge brief, probably NO judge seat (Challenge Partner €5k max-3 + Title €15k hold those). Compiled Nov 2026, public sources.

---

## 1. CROWDCRUIT — crowdcruit.com

**What:** B2B technical-hiring platform, skills-first. Six verticals: Software Eng, Cybersecurity, AI/ML, Web3, Cloud/DevOps, Data. Self-serve SaaS (Console) + managed recruitment (Crowdcruiting) + AI assessment (CrowdVibe). Claims: 2,000+ vetted professionals, 30+ domain experts, "Top 3% talent network", 48h avg interview turnaround, 48–72h managed shortlists.
**Entity/status:** Founded Jan 2025, ~8 FTE (LinkedIn +14% YoY). EnvolveXL **cohort 3** (announced 6 Apr 2026, HRtech vertical) — NOTE: NOT among the 5 cohort startups that got the €12.5k initial Envolve investment tranche (FitKit, Joberos, Kiné Health, Pebole, Scoopterra, announced 7 Oct 2026). NVIDIA Inception member. Bootstrapped-looking; sponsorship = ecosystem/recruiting play.

### People
| Person | Role | Notes |
|---|---|---|
| **Evangelos "Vangelis" Mourikis** | Founder/CEO | **OSCE3** (certs listed: OSEP, OSWE, OSCE, OSCP, OSWP, CRTO). Ex-Deloitte Specialist Leader Cyber Risk Advisory (2021–22), ex-Director of Cybersecurity Services @ K3Y (Jan 2023–Jun 2026, Sofia/GR), pentester @ Neurosoft earlier. Now also runs solo shop **Aethersec** (Jul 2026–). Univ. Western Macedonia Informatics & Telecom (8.21/10). CVE-2018-1888 (IBM i Access DLL hijack), won 1st Pwnzilla CTF, blog vagmour.eu, 15k LI followers. Ran CC as side-project alongside K3Y until mid-2026. Moderates Eleven Ventures "Eleven Nexus" trust panel Nov 2026. |
| **Alexandros Modis** | Co-founder/CTO | Built the platform. |
| **Christos Gkatzoglou** | Founding engineer | |
| **Ignatios Iliopoulos** | Co-founder/founding engineer | |
| Advisors | — | Isidoros Monogioudis (Project Officer @ **EDA** — European Defence Agency), Georgios Papakyriakopoulos (**CISO @ Skroutz**), Antonis Chariton (Cisco researcher, ex-Google), Michail Bletsas (Director @ **National Cybersecurity Authority**), Sotiraki Sima (CEO Aquilax), Claudia Cuzuban Perri (Sales Dir @ Neurosoft — Mourikis's old shop). |

→ Advisor bench = defense/national-security/cyber heavy. Pentester CEO + security network = their whole credibility play.

### Product internals (the technical process)
**CrowdVibe** (from €500/assessment, pay-as-you-go, free for candidates):
- Flow: configure (role level junior→staff, stack **TypeScript/Node, React, Python/FastAPI**, scenario mix) → invite link → isolated sandbox auto-provisions → candidate works 3 real-world scenarios in **Monaco IDE** + embedded AI pair (**"same Claude model, same system prompt, same tooling" for every candidate**) → 6-tab report + time-synced session replay.
- **Telemetry (verbatim):** "every keystroke, AI prompt, paste, test run, and focus event in real time, all replayable."
- **5-axis weighted score:** AI Leverage **25%** (secondary AI model analyzes prompt specificity, problem decomposition, whether AI is used on architecture/edge cases vs rote codegen — "fix the code" = weak, targeted security-review prompts = strong) · Task Completion **25%** (automated test suites vs acceptance criteria/edge cases/error handling) · Critical Review **20%** (per-suggestion accept/edit/reject log; +4 accepted w/ edits, +6 caught incorrect suggestion, +3 modified output, **−2 pasted without review**) · Code Quality **20%** (**ESLint + Semgrep**: input validation, error handling, security anti-patterns, smells) · Speed & Efficiency **10%** (time normalized by difficulty + prompt-efficiency ratio, penalizes aimless looping).
- **6 report tabs:** Performance, Behavior, **Provenance**, Grading, **Integrity**, Methodology. AI-written summary, prompt analysis, **integrity flags** on replay, PDF export, side-by-side compare. Custom scenarios still grade on identical 5 axes (comparability preserved).
- Scenario generation: from JD PDF, repo, or freeform brief (e.g. "refactor rate-limit middleware for per-tenant budgets").

**Expert interviews (Crowdcruiting):** certified "Crowdcruiters" — domain-matched, calibrated, paid per interview (tiered rates, not placement-contingent). **45–60 min** structured interview via built-in video+code platform, rubric-guided but expert-autonomous, deliverable = detailed report (skill breakdowns, strengths, concerns, hire recommendation). **The ~30-expert pool is the scaling bottleneck** — supply-limited like any marketplace; CrowdVibe is their scale-out answer.

**Console SaaS:** job listings, pipelines, AI scoring w/ analysis summary (evidence-linked: every score points to the artifact that produced it), AI-generated interview questions per candidate profile, native video+recording+notes, hiring analytics, ATS integrations (Pro+), Crowd Bounty Program. Pricing: Starter €169/mo · Pro €424/mo · Enterprise custom.

**Differentiator doctrine:** "Evidence-linked scoring" — every score links to session/interview artifact. AI-native stance: don't ban AI, observe how they use it ("hiring processes pretending AI doesn't exist filter for test-takers, not builders"). Integrations: Cantina + Code4rena on-chain results on profiles.

### AI roadmap (crowdcruit.com/features — public voting board)
In progress: Smart Profile Score, AI Career Pathing. Planned: AI Job Curator (Jun'26), Verified Skill Badges (Jul'26), Skill Endorsements (Jul'26), **Interview Prep Assistant** (AI mock interviews, Sep'26). Done: AI Mentor Matching (Dec'25). Proposed: Peer Circles, Learning Path Builder. → Direction: candidate-side AI tooling + more automation around the human-expert loop.

### Who staffs the table (prediction)
- **Likely:** Gkatzoglou + Iliopoulos (founding engineers — demo CrowdVibe live, recruit builders into talent pool; CV opt-in = their inventory). Modis if technical questions get deep.
- **Mourikis** = the face (15k followers, conference regular, moderating Eleven Nexus same month) — likely drops by rather than tables all weekend. Don't pitch him like a bizdev; talk adversarial-detection tradecraft.
- **Approach:** ask to see a CrowdVibe report; ask what the Integrity tab actually flags today vs what they wish it caught. Their pain = expert supply doesn't scale + provenance detection is an arms race.

---

## 2. ALWAYS ONLINE — thealwaysonline.com

**What:** AI strategy + implementation boutique. Tagline "Building AI agents. The operating layer of modern business." "Most companies do not have an AI problem. They have an execution problem."
**Entity:** ALWAYS ONLINE TECHNOLOGIES Ι.Κ.Ε., Dig. Griva 2, Agios Dimitrios 17342 Athens · ΑΦΜ 802975403 · ΓΕΜΗ 186570803000. Founded ~Aug 2025. **Team of 3** + 56 LI followers. Tiny.

### People (all 3)
| Person | Role | Notes |
|---|---|---|
| **Andriana Lazana** | Co-founder & AI Solutions Architect | ~4 yrs total exp. **KPMG Greece = 3-month Management Consulting INTERN** (Strategy, Operations & Customer team, ended Jul 2025 — "ex-KPMG" oversells it). Before: **Shenergy** Head of Community Growth & Marketing Strategy + Event Team Coordinator (youth energy nonprofit). AUEB Software & Data Analysis Technologies degree in 3.5 yrs. 1.9k LI followers, heavy poster (🚀 emoji style). Strategy + workshops + client-facing. |
| **Marietta Lazana** | **Board Member** (Jan 2026–) | Almost certainly her sister. **Ex-McKinsey Senior Consultant / Digital Expert, Berlin** (Sep 2024–Dec 2025, top-5% rated). Now founder **HouseMaster** (real-estate marketplace, Dec 2025–). Girls in Tech Greece co-MD, AUEB best-business-plan award. = the McKinsey pedigree in the pitch. |
| **Giorgos Papageorgiou** | AI Solutions Architect (Feb 2026–) | The technical hire. **Ex-EY AI Engineer** (agentic systems + RAG pipelines, Jul 2025–Feb 2026), ex-EY Tech Consultant, AI Advisor @ INSEAD. AUEB Mgmt Science & Tech grad; AUEB researcher on autonomous agents in the data-science pipeline; guest-lectures for Prof. Lekakos. Attended GenAI Summit 4, liked Petropoulos's hackathon post → **likely the second person at the table.** |

### Offering — Discovery → Build → Enablement
1. **AI Discovery:** structured interviews across every department, workflow analysis, prioritized use-case roadmap. "Map what is worth building before you spend anything."
2. **AI Implementation:** "**We build inside your existing stack. No new tools to buy. No long rollouts. The first system goes live within weeks**, documented and owned by your team." — agents, automations, system integration, custom products.
3. **AI Enablement:** workshops per team/function, AI for Leaders (CEO sessions), AI newsletter, ongoing advisory.
**Delivery shape (their diagram):** 01 Connect (your existing systems) → 02 Intelligence (AI agents & skills) → 03 Action (business outcomes).
**Principles:** Clarity "no hype, just facts" · Impact "results that matter" · Speed "ship fast, hand over" · People "built with your team".
**Tool surface they train/build on:** ChatGPT, Claude, Gemini, MS Copilot, Excel, Teams, **Power Automate**, ElevenLabs → i.e. commodity-office stack, not deep eng. Orchestration almost certainly n8n/Power Automate + LLM APIs.

### Clients & SMEs served
- Claimed footprint: **Greece, Dubai, Brussels** (about page verbatim).
- **Named client:** **LAMDA Development + The Ellinikon** — AI Marketing Training for their marketing teams at the National Gallery, Jun 2026 (insight generation, content, campaign execution, automation, perf analysis).
- Other cases are anonymized ("Client Confidential"), tagged by function: **AI sales ops** (agents wired into CRM: lead scoring, meeting briefs, no-missed-follow-ups) · **executive command center** (AI-assisted exec reporting, ops) · legal ops · enterprise AI strategy roadmap · AI assistant on business systems.
- Solution pages exist per function: sales, finance, legal, marketing, operations, HR → **SME/mid-market back-office functions**, not vertical software. Sweet spot: companies with commodity stacks (M365/Google + CRM + spreadsheets) and zero AI staff.

### Who staffs the table (prediction)
- **Lazana + Papageorgiou** (Marietta is board-side, running HouseMaster — may swing by). Table = lead-gen for Discovery engagements + hiring-adjacent scouting.
- **Approach:** she sells speed-to-value + adoption ("people matter more than tools"). Ask which function pages get the most inbound (probably finance/sales). Their pain = every engagement is bespoke; anything that productizes Discovery (auto workflow-mapping) or shrinks implementation = interesting. Small shop — flattery via concrete SME use-cases, not scale-talk.

---

## 3. Challenge-brief predictions + judges

**Structural check:** briefs/judge seats attach to Title (€15k) + Challenge Partner (€5k, max 3) tiers. CC + AO sit at Supporter level → **neither likely owns an official brief or judge seat.** Predictions below = what their tables champion + what an agent aimed at them should look like; main judging stays with organizers/VCs per judges.md.

- **Crowdcruit brief-shape (if they had one):** "agent that evaluates technical work like an expert" — evidence-linked scoring, provenance/integrity forensics on AI-assisted work, or interviewer-assist (structured debriefs). Map to their bottleneck: make the 30 experts 10x faster, or catch what proctors can't.
- **Always Online brief-shape:** "agent doing a tedious SME back-office job inside tools the client already has" — receivables/follow-ups/CRM hygiene/reporting. Their mantra: live in weeks, in the existing stack, handover-ready.
- **Who judges for them:** none officially. Table reps (Iliopoulos/Gkatzoglou; Lazana/Papageorgiou) may act as **mentors** (mentor ticket type exists; mentors drawn from Summit speaker list but small sponsors slip in as experts). Mentors advocate at judging → worth a table visit pre-vertical-commit Saturday 12:00.
- **Cross-leverage:** a build that ingests CrowdVibe-style telemetry OR uses AO's Connect→Intelligence→Action framing gives both tables a reason to remember you; CC's CV pipeline = post-event recruiting surface, AO = potential implementation partner/client-referrer.

---

## 4. Refined agent concepts

### A. Crowdcruit — "Debrief+Integrity Agent" (refines MASTER-BRIEF direction #6)
**One-liner:** agent that turns raw assessment-session telemetry into a signed, evidence-linked CrowdVibe-style report — and catches cheating the human eye misses.
**Build (36h):**
- Input: synthetic/real session telemetry stream (keystroke timing, AI prompts, paste events w/ length+source, test runs, focus-loss events, file diffs) — pre-generate 2–3 fixture sessions incl. one clean, one paste-farm, one "colluding AI" pattern.
- Pipeline: telemetry → feature extractor (paste-to-type ratio, paste bursts >X chars in early window, time-to-first-keystroke, inhuman WPM/flight-time variance, focus-loss↔paste correlation, verbatim-AI-output detection) → SLM/rules hybrid classifier → **integrity verdict w/ timestamp citations**.
- Output: the 6 tabs — Performance, Behavior, Provenance, Grading, Integrity, Methodology — every score hyperlinked to replay offset ("03:41 — 2,300-char paste after 47s focus loss"). Plus expert-debrief mode: interview transcript → rubric-aligned draft report for a Crowdcruiter to sign (attacks the 30-expert bottleneck: experts review, not write).
- Judges' candy: signed action log + machine-checkable citations (Zindros); SLM verifier beats frontier-model judge on the integrity task (Koukoumidis/Gianitsos); live before/after "expert writes report in 25min → agent drafts in 40s" (evals crowd).
- **Why it flatters CC:** it IS their Integrity/Provenance tabs, productized as a service — and pentester-CEO respects adversarial detection over vibey "AI scores."
**Demo aura moment:** replay fast-forwards to a paste event; agent freezes frame, flags it, cites three corroborating signals, renders verdict. Microcopy: "Proof is checked, not trusted."

### B. Always Online — "SME Receivables Agent" ("Ταμείο")
**One-liner:** agent that lives inside an SME's existing stack and chases overdue invoices end-to-end — connect Monday, live Friday, owned by the client (their methodology, verbatim).
**Build (36h):**
- Connect: aging report (Excel/Sheet/CSV — every Greek SME has one) + email + optional mock accounting API (Soft1/Entersoft shape).
- Agent loop: read aging → prioritize (amount × days-overdue × customer history) → draft dunning sequence in the company's voice (Greek + English) → send/schedule follow-ups → watch replies → log promise-to-pay → escalate past thresholds → weekly CFO digest (recovered €, DSO delta).
- Policy gate (ties to core harness): every outbound email above threshold → human approval; signed log of every action — enterprise-safe, mirrors AO's "documented and owned by your team."
- **Why AO:** literally their Connect→Intelligence→Action diagram running live; receivables = universal SME pain (Greek B2B late payment is endemic); demo shows emails actually sent + sheet cells actually updated = "agent at work," not a pitch.
**Demo aura moment:** a debtor reply arrives live mid-demo; agent reads intent ("paying Friday"), updates the ledger, drafts the polite Greek confirmation, asks approval. CFO digest renders as the "beautiful deliverable" (100mentors/wiserwork judges love finished artifacts).
**Handover line:** "documented, inside your own M365/Sheets, your team owns it" — say it in the pitch; it's their §2 verbatim.

---

## Cross-cutting table-intel
- Both are ~1-yr-old micro-teams buying visibility + hiring/leads, not customers-at-scale. Recruiting surface is real: CC gets builders into Crowdcruit ID; AO scouts implementation talent/clients.
- Shared vulnerability to needle: CC = expert-marketplace cold-start (30 experts vs "2,000+ professionals" supply/demand imbalance); AO = every delivery bespoke, no product moat yet (tools listed are clients' tools, not theirs).
- Neither is in EnvolveXL's funded five / neither publishes pricing power — they're sponsoring for pipeline, treat as mentors+future-customers, not kingmakers.
- Conversation hooks that work on both: "evidence over vibes" (CC doctrine ≈ Zindros), "ship fast, hand over" (AO principle ≈ hackathon ethos). Both companies' language already rhymes with the judging rubric.
