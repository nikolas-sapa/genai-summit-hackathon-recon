---
title: "greek pains"
type: source
tags: [hackathon, genai-summit, recon, intel]
aliases: ["greek pains"]
created: 2026-11-10
updated: 2026-11-10
status: active
---

# Greek Pain-Point Catalog — "agents doing work nobody wants to do twice"
Gen AI Summit Hackathon recon · compiled Nov 2026 · for pitch + build selection.
Summit frame: post-experimentation — deployment, ROI, governance. Rank = (pain × quantified cost) × (36h demo-ability) × (sponsor/judge alignment, cf. MASTER-BRIEF ranked directions).

**Sponsor map (confirmed):** hackathon partners = Quintessential, Wonderful, Big Pi, fal, Prosperty, boxd, Firecrawl, treg, Wiserwork, Endeavor, Oumi, Always Online, Crowdcruit. Piraeus / NBG / Ethniki are summit-level (conference) sponsors — their briefs surface via the Summit, not hackathon partner challenges. Crowdcruit + Always Online ≈ Supporter tier (€2k, no own brief per deep2 dossier).

---

## 1. Property transfer dossier chase — ★ top pick
- **Workflow:** every sale needs a seller-side dossier: title deed, Electronic Building ID (HTK — mandatory since Apr 2022, "most time-intensive requirement, frequent cause of delay"), energy cert (PEA), ENFIA 5-yr certificate, tax + social-security clearance, land-registry sheet/diagram, AFM+IDs, plus myPROPERTY tax declaration. New law 5293/2026 makes the notary a one-stop-shop who must *retrieve all docs himself* from Taxisnet/Ktimatologio/etc.
- **Persona:** notary's secretary (the actual chaser); real-estate advisor coordinating seller + engineer + accountant; Prosperty ops agent moving distressed/auction stock.
- **Manual cost:** weeks of serial back-and-forth per file; deals die in the gap. Docs span ~6 systems (gov.gr auth, myAADE, Ktimatologio, engineer-issued HTK/PEA, EFKA, notary).
- **Incumbents:** gov.gr digital transfer authorization (2023), myPROPERTY platform, notary software, engineer portals — each retrieves *one* doc; nobody owns completeness, expiry, or the chase.
- **Why agents beat incumbent:** the pain is orchestration across portals + remembering which doc blocks which step + re-requesting expired certs — a checklist that acts. Deterministic doc-graph + status scraping + chase messages is exactly "tedious, multi-step."
- **Sponsor/judge match:** Prosperty (partner; Big Pi portfolio co → judge Kalliagkopoulos). MASTER-BRIEF ranks this #3 overall; "transfer in 90 days" instrumented = measurable ROI story.
- **Demo:** upload deed → agent emits dossier checklist, simulates retrieval status per doc, flags missing HTK, drafts chase emails/SMS to seller+engineer, tracks to readiness.

## 2. myDATA bookkeeping grind: expense characterization + client doc chase
- **Workflow:** every incoming invoice must be *characterized* (expense category) in myDATA before books reconcile; accountants also re-date late-received expenses, can't void buyer-accepted invoices, and absorb AADE-side errors (Dec 2024 eSend→myDATA migration broke values/numbering — fixes pushed onto businesses).
- **Persona:** freelance accountant (logistis) carrying 30–80 SME clients; SME owner who hands a shoebox of PDFs monthly.
- **Manual cost:** ΟΕΕ's official defect log lists 15+ unresolved workflow problems creating "extra work and difficulty" daily; trade press calls the accountant "a modern Sisyphus." Hours/client/month on classification + chasing missing invoices.
- **Incumbents:** ERP/accounting suites (Epsilon Net/Entersoft/SoftOne), myDATA API, e-invoicing providers — they transmit; a human still characterizes every doc and hunts stragglers.
- **Why agents beat incumbent:** classification is judgment-at-volume (LLM sweet spot); the chase loop (detect missing/counterparty-untransmitted docs → email client → verify arrival → retry) is pure agent work. Human approves exceptions = governance story.
- **Sponsor match:** Always Online (SME back-office is literally their solution pages); banks' SME-banking angle (Piraeus/NBG sponsor-ish).
- **Demo:** drop 20 Greek invoices → auto-characterization vs accountant answer key (eval table = Koukoumidis/Pittarokoili bait), exception queue, drafted client-chase emails in Greek.

## 3. Demurrage claim pack assembly — best stats in the catalog
- **Workflow:** ~45 discrete steps per claim: collect charterparty+recap, NORs, Statements of Facts from port agents, pumping/port logs, letters of protest; reconcile master's vs agent's vs terminal SOF; compute laytime with every exception shown; submit inside the time bar; chase to settlement.
- **Persona:** demurrage/laytime analyst at owner/charterer ops desk (Piraeus = global ship-management hub; Greeks control ~20% of world tonnage).
- **Manual cost (Marcura, 20k claims/yr):** 75% of analyst time = process tasks (doc collection, chasing agents, SOF data entry, formatting); 99% of SOFs still manual ≈ 12M hrs/yr industry-wide; one portfolio logged $450k in missed time bars in a year; rates $15–30k/day make every transcription slip expensive; late SOF arrival (weeks post-sailing) kills dispute position.
- **Incumbents:** Excel + email + shared drives; Veson IMOS, DA-Desk, Marcura DA-Desk/Voyager emerging — high-end, foreign, priced for majors.
- **Why agents beat incumbent:** SOFs arrive as PDF/email heterogeneity; extracting event timelines, cross-checking 3 SOF versions line-by-line, generating the laytime statement, and *watching time bars proactively* is multi-step agent work incumbents leave to the analyst.
- **Sponsor match:** shipping aura (Keel won this org's May '26 hackathon — proven Athens meta); Big Pi/Greek-GDP framing; no direct sponsor but strongest "ROI per hour saved" narrative.
- **Demo:** drop SOF PDFs + CP → extracted timeline, conflict flags, laytime calc with clause citations, time-bar countdown, claim-pack PDF. (Note: keel/ already exists in repo — reuse as fixture base.)

## 4. Bank KYC refresh & onboarding doc chase
- **Workflow:** periodic KYC refresh for existing clients + onboarding: ID, AFM doc, tax-residency proof, income docs (payslips, E1s, employer cert), utility bills, certified translations/apostilles for foreigners; every datum must be backed by written proof; banks default to max-threshold checklists ("asked for everything" to be audit-safe).
- **Persona:** branch/back-office KYC analyst; compliance officer (Piraeus CCO on record: KYC needs "a multitude of data verified by documents or reliable sources" + recurring updates); foreign customer bounced between branch visits.
- **Manual cost:** eGov-KYC handled ~350k requests in 7 months = 350k physical visits *avoided* — implies the pre-existing volume of branch doc-chasing; onboarding reports: 2h+ appointments, multi-week cycles, doc re-requests, mid-June queues for appointments.
- **Incumbents:** eGov-KYC gov rails, bank apps' upload+videocall flows (Eurobank DCO), internal compliance systems — digitized submission, not digitized *chasing*: missing/expired/wrong-doc detection and customer follow-up still manual.
- **Why agents beat incumbent:** per-risk-profile checklist generation, doc-validity checking (expired? right cert? name/AFM match?), multilingual doc intake (foreigners!), proactive re-request loop, audit log of every verification = governance theme verbatim.
- **Sponsor match:** Piraeus + NBG (summit sponsors; NBG already markets 48h pre-approval — speed is the battleground).
- **Demo:** synthetic customer pack → agent validates each doc, issues precise re-request ("your ENFIA cert covers 2020–24; transfer needs 5 yrs"), fills refresh file, logs verification trail.

## 5. Motor insurance claim intake + document completeness
- **Workflow:** strict clocks — 8 days to notify (L.2496/1997), 3 months for insurer's reasoned offer on motor TPL; docs: accident declaration (amiviaia dilosi), police report, photos, vehicle registration, licenses, IDs, bank details; Φιλικός Διακανονισμός fast-track when both insurers participate; payout promised "within 48h of complete file" — the file is never complete.
- **Persona:** claims handler (lit. claim-settlement officer) juggling 100+ open files; insured customer uploading wrong/partial docs.
- **Manual cost:** cycle time dominated by doc ping-pong; each handler round-trip adds days; direct insurers (Gan Direct, Hellas Direct) compete on 24h settlement promises.
- **Incumbents:** insurer portals (myinteramerican), friendly-settlement rails — intake exists, completeness-check + customer chase does not.
- **Why agents beat incumbent:** per-claim-type checklist, photo/PDF sufficiency check, deadline engine (8d/3mo), customer nudges in Greek, escalation to human on liability doubt — auditable, human-gated = summit governance fit.
- **Sponsor match:** Ethniki Asfalistiki (insurance sponsor).
- **Demo:** FNOL via chat → agent builds doc checklist, ingests uploads, rejects incomplete, starts clock tracker, assembles adjuster-ready file.

## 6. SME receivables dunning (invoice chasing)
- **Workflow:** Greek B2B = 56% on credit; chasing = owner/accountant manually calling, emailing, re-sending invoices, logging promises-to-pay, escalating to lawyer/factoring.
- **Persona:** SME owner or their external accountant doing 3rd-party dunning.
- **Manual cost (Atradius 2026 GR barometer):** ~1/3 of B2B invoices overdue (vs 1/4 W. Europe); 2 in 3 companies pay late; 50% say non-payment risk squeezes operating cash; main cause = customer liquidity (66%).
- **Incumbents:** ERP aging reports, email reminders, collection agencies, factoring — none run the persistent polite-relentless follow-up loop.
- **Why agents beat incumbent:** tone-calibrated dunning cadence, promise-to-pay capture + tracking, dispute detection ("we never got the invoice" → resend via myDATA mark), escalation rules, human gate before legal — cheap, no new stack.
- **Sponsor match:** Always Online (SME finance ops); adjacent to banks' SME lending narrative.
- **Demo:** AR ledger CSV → prioritized chase queue, drafted Greek dunning emails per aging bucket, promise tracker, weekly owner digest.

## 7. Recruiter pipeline admin: screening, scheduling, feedback chase
- **Workflow:** CV intake → screening → candidate doc/portfolio requests → multi-party interview scheduling → interviewer-feedback nudges → status updates.
- **Persona:** agency recruiter / in-house TA (Crowdcruit's managed-recruiting arm; expert-interview coordinator).
- **Manual cost:** Eurobank pre-ATS: ~1,000 CVs/mo screened into folders manually; industry: 17.7h admin per vacancy (2 lost workdays, ~€18k/yr per recruiter), 2.6h scheduling alone, 29% of candidates drop out because process drags; Crowdcruit's own bottleneck = ~30-expert interview pool scheduling.
- **Incumbents:** Workable/Recruitee ATS (Greek cos already adopt — M&S Greece halved time-to-hire). **Implication:** screening/scoring is incumbented; agents must own what ATS doesn't — the *chase* (feedback nudges, candidate docs, calendar tetris, expert-pool dispatch).
- **Why agents beat incumbent:** cross-tool persistence (email+calendar+ATS), skill-verification scheduling into scarce expert slots, interview-debrief extraction to rubric reports — Crowdcruit's Integrity/Debrief angle.
- **Sponsor match:** Crowdcruit (Supporter; MASTER-BRIEF direction #6: Debrief+Integrity Agent flatters pentester-CEO).
- **Demo:** job + candidate pool → scheduling agent negotiates slots, sends reminders, extracts interview notes to rubric, flags integrity anomalies.

## 8. Municipality citizen-request triage + Diavgeia posting
- **Workflow A:** citizen requests arrive via KEP, 1560, email, gov.gr support — triaged by hand to directorates (new national CRM coming, unproven).
- **Workflow B:** every expenditure/administrative act must be posted to diavgeia.gov.gr with correct act-type, KAE codes, metadata; understaffed municipalities post late/malformed; 2025 ministerial decision tightened timing + technical fields.
- **Persona:** municipal secretary / finance-department clerk; mayor's office fielding status calls ("where is my request?").
- **Manual cost:** myOTA: diavgeia data usable but needs "hundreds of work-hours to detect" anything; small municipalities have 1–2 engineers/administrators covering everything; non-compliance = acts legally non-opposable.
- **Incumbents:** diavgeia API/posting portal, municipality ERPs (mostly document management, e.g. Greek soft), KEP protocols — digitized forms, manual routing/metadata.
- **Why agents beat incumbent:** classify inbound request → route to right unit + draft reply skeleton; auto-format decisions into diavgeia-compliant postings (act type, amounts, KAE), catch missing fields pre-posting — verifiable, low-risk, civic.
- **Sponsor match:** Apps4Athens/municipality themes; civic aura (Mene/Abed); pairs with ranked direction #2 (procurement watchdog on diavgis data).
- **Demo:** inbox of citizen emails → routed tickets + draft responses; decision PDF → validated diavgeia posting draft with field-diff warnings.

## 9. ERGANI seasonal-hire compliance pack (hospitality)
- **Workflow:** every hire declared to ERGANI *before day 1* (undeclared = illegal); third-country seasonal worker approval = 8 documents + €100 + 10-day SLA (L.5038/2023): recall request, pre-signed contract, accommodation proof, return-cost declaration, tax/insurance docs; inspection-ready file per worker (contract, ERGANI statement, AFM/AMKA/EFKA, permit, payroll proof, housing docs).
- **Persona:** island hotel HR/owner during Apr–May ramp (sector short tens of thousands of workers; islands compete for staff as hard as guests).
- **Manual cost:** per-hire paperwork × dozens of hires under deadline; foreign-worker permits still partly courier-based; fine exposure per inspection.
- **Incumbents:** ERGANI II + Quick Hire app (digitized *declaration*, not pack assembly); payroll bureaus; agencies.
- **Why agents beat incumbent:** per-worker checklist by nationality/role, deadline countdowns, doc collection from workers (photo→validated), inspection-folder generation.
- **Sponsor match:** hospitality GDP narrative; no direct sponsor — mid rank.
- **Demo:** hire list → per-worker packs, missing-doc chase messages (worker-language), inspection-day binder.

## 10. Citizen benefit navigator (ΔΥΠΑ / e-ΕΦΚΑ)
- **Workflow:** unemployment card/benefit applications, individual action plans, supporting docs via gov.gr/DYPA portals; platform outages block issuance for days (Kozani: 4 days unable to issue card, benefits clock ticking); citizens rejected because docs submitted electronically instead of handwritten (SKAI complaint).
- **Persona:** unemployed citizen (often low digital literacy); KEP clerk re-explaining steps.
- **Manual cost:** lost benefit days; repeat office visits; 1555 helpline overload.
- **Incumbents:** gov.gr flows, 1555 line, KEP in-person — digitized but fragile and literal-minded (a checkbox bug voids weeks).
- **Why agents beat incumbent:** eligibility pre-check, doc checklist, form pre-fill, submission-status tracking + retry, plain-Greek explanation. Low $ ROI but max civic resonance.
- **Sponsor match:** civic/aura lane; risky as core pitch (little enterprise buyer) — keep as demo garnish or fallback.

## 11. Building-permit dossier tracker (engineers/ΥΔΟΜ)
- **Workflow:** dozens of studies + docs via e-Άδειες; third-party opinions (archaeology 2–6 mo, forestry, fire service, coast guard) arrive serially; ~170 municipalities run ΥΔΟΜ, 160+ don't; 1 in 4 offices >3 months/permit, extreme cases 5 yrs; TEE: "citizens and engineers trapped in legal-administrative ambiguity."
- **Persona:** civil engineer (mechanical/electrical + architect) shepherding files; ΥΔΟΜ officer.
- **Manual cost:** months per permit; fee-bearing idle time; completion letter chase.
- **Incumbents:** e-Άδειες platform (auto Cat-3 issuance), TEE e-services — submission digitized, cross-agency opinion chase manual.
- **Why agents beat incumbent:** pre-submission completeness gate (kills the #1 delay cause — incomplete files), opinion-status tracking across agencies, resubmission drafting.
- **Sponsor match:** adjacent to Prosperty (pre-sale permit legality feeds HTK); secondary.
- **Demo:** project brief → required-studies map by zone, doc checklist, agency-opinion tracker, deficiency-letter draft.

---

## Pitch synthesis
- **Sponsor-direct picks:** #1 Prosperty, #2 Always Online, #7 Crowdcruit — each flatters a partner table; #1 is already a MASTER-BRIEF top-3 direction.
- **Best ROI numerals for the deck:** demurrage (75% of analyst time, 45 steps, $450k time-bar loss, $15–30k/day); receivables (1/3 invoices overdue, 50% cash squeeze); recruiting (17.7h/vacancy admin); KYC (350k avoided visits/7mo); diavgeia (hundreds of hrs/municipality).
- **Governance hooks (summit theme):** every entry = "agent drafts + human approves + signed action log" — KYC/claims/diavgeia especially, since misfiling has legal consequences (that's why incumbents stall — agent + gate is the unlock).
- **Anti-picks:** broad "gov.gr assistant" (commodity chatbot, no chase), generic hotel chatbot (booking ops = solved by incumbents; the pain is compliance, not guest comms — multilingual guest messaging is the weakest sub-pain, hotels already use canned tools).

## Sources
- myDATA pain: e-forologia.gr/cms/viewContents.aspx?id=230705 (ΟΕΕ defect log) · foronews.gr "λογιστής ως σύγχρονος Σίσυφος" · lsa.gr/portal/enimerosi/epikaira-themata/10835
- KYC/banks: newmoney.gr eGov-KYC 350k requests (Piraeus CCO Kasapaki) · ellytic.com Greek banking for foreigners · expat.com NBG account-opening thread · eurobank.gr digital onboarding
- Public sector: naftemporiki.gr gov.gr→CRM (2,257 services, 19.1M avoided visits) · dnews.gr case-tracking platform · e-ota.gr diavgeia expenditure ruling · myota.gr diavgeia underuse · skai.gr DYPA complaint · kozan.gr DYPA outage · karfitsa.gr OPSKE grant delays
- Shipping: marcura.com demurrage leakage (75%/45 steps/12M hrs/$450k) · voyagerportal.com claim steps · xdqlabs.com laytime · atlas-claims.com doc checklist
- Property: engelvoelkers.com transfer-doc guide (HTK "most time-intensive") · sofokleousin.gr notary one-stop-shop (ν.5293/2026) · aade.gr ENFIA cert · metaxopouloslaw.gr buying-guide PDF
- Permits: tovima.com planning reform (¼ offices >3mo, 5yr extremes, 170 vs 160 municipalities) · tovima.gr TEE complaints · michanikosgpt.gr permit timelines · batistatos.gr
- Insurance: fthiniasfalia.gr claims guide (8d/3mo clocks) · interamerican.gr claims docs · gandirect.com 24h settlement
- SMEs: tovima.com Atradius 2026 GR (1/3 overdue, 2/3 late, 50% squeeze) · atradius.com GR barometers 2023/2025 (56% credit, 36-day terms)
- Recruiting: workable.com Eurobank case (~1,000 CVs/mo manual) · recruitee.com M&S Greece (halved TTH) · irishjobs.ie recruiter guide (17.7h/vacancy admin, 29% drop-out)
- Hospitality: en.mitos.gov.gr seasonal-worker procedure (8 docs, €100, 10d) · atlasconsulting.gr ERGANI guide · work-in-rhodes.com employer FAQs · qwiza.ai Greece hiring
