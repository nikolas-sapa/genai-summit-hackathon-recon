---
title: "logistics"
type: source
tags: [hackathon, genai-summit, recon, intel]
aliases: ["logistics"]
created: 2026-11-10
updated: 2026-11-10
status: active
---

# Gen AI Summit Hackathon — Complete Logistics Recon (deep2)
**Event:** Sat 14 – Sun 15 Nov 2026, Athens LifeTech Park (Spata) · Finals Mon 16 Nov @ SNFCC
**Compiled:** 10 Nov 2026 · Sources: hackathon.polymath42.com (live HTML/JS/JSON-LD/decks), genaisummitseeurope.com agenda-2026 (embedded `AGENDA_CSV`, tentative), luma.com/x1wxi5sn (event JSON), athenslifetechpark.com, LifeHack Athens Luma (same-venue precedent), summit FAQs, prior `deep/rules-deck.md`

---

## 1. TIMELINE (all published times)

### Saturday 14 Nov — Athens LifeTech Park
| Time | What |
|---|---|
| **12:00** | Doors open; **build window starts** (schema `startDate` = 12:00+02:00). Pre-built = DQ. |
| Sat afternoon | **Team formation** — teams 1–5 form right after doors; organizer-facilitated matching (Luma opt-in checkbox "I'd like to be matched with other hackers to form a team") |
| Sat evening | **Partner stage slots**: Title Sponsor 10-min opening keynote to full room; Challenge/Tech Partners 5-min technology intros each. Challenge briefs announced at kickoff |
| Meals | Lunch, snacks, dinner — all included, all non-alcoholic (Endeavor meals deal) |
| Overnight | **Confirmed** — "36-hour overnight hackathon… build through the night" (Google deck). Venue stays open all night |

### Sunday 15 Nov — Athens LifeTech Park
| Time | What |
|---|---|
| Meals | Breakfast, lunch |
| **18:00** | **Submissions close** (hard deadline; build window ends) |
| 18:00–21:00 | Judging/demos window |
| **21:00** | **Finalists announced** (schema `endDate` = 15 Nov 21:00+02:00) |
| After | **Closing dinner party** (~140 guests, "could be pizzas", non-alcoholic) + proposed buses back to central Athens (Endeavor) |

### Monday 16 Nov — SNFCC (GenAI Summit 5)
| Time | What |
|---|---|
| 09:00–10:00 | Summit registration/coffee opens (all 4 stages) |
| **18:00–18:30** | **HACKATHON SLOT: "Mini use cases" — Winning teams (Hackathon) — BOOK CASTLE stage** (verbatim from embedded agenda CSV) |
| 19:00–19:30 | "Security check" (short break, Central Stage — VIP sweep before PM) |
| 19:30–20:15 | Closing fireside: PM Kyriakos Mitsotakis × Dr. Najwa Aaraj (Central Stage) |

- Pitch format: **5 min each** → 30-min slot ≈ **5–6 finalists**. Winners announced on stage w/ partner recognition.
- **Workshops during the weekend: NONE.** Workshops are Summit-Monday only, exclusive to summit ticket holders: Maker Space (Bernitsas 11:00–14:00), Multi Purpose 1 (HDB, WiserWork, Deloitte A+B), Multi Purpose 2 (AUEB 11:00–13:00, Kyndryl), EY sessions 10:00–19:30.
- ⚠️ **Luma metadata discrepancy:** Luma event JSON says start 14 Nov 11:00Z (=13:00 Athens) / end 15 Nov 17:00Z (=19:00 Athens) — official site + schema (12:00 → 21:00) wins; treat Luma as stale placeholder.

## 2. VENUE — Athens LifeTech Park
- **Address:** Block 49 (O.T. 49), 31st Street, Foinikas industrial zone, Spata 190 04 (maps: goo.gl/maps/i3xsSA3Mocm8iYL38; coords 37.978, 23.934). Tel +30 214 40 80 700.
- **What it is:** ELPEN's brand-new biotech park/incubator — opened Sept 2026 (PM-visited). Labs+offices building, ~10 km from ATH airport.
- **Getting there:**
  - **Free bus:** Endeavor Greece — round-trip **central Athens ↔ venue**, accepted builders only (confirmed partner; scope = buses + meals per their custom deck).
  - **Same-venue precedent:** LifeHack Athens (May 2026) ran shuttles from **Doukissis Plakentias** metro (Line 3 / Proastiakos interchange) → ALTP and back.
  - DIY transit: Metro L3 or Proastiakos to Athens Airport (or Koropi), then taxi ~10–15 min. No direct OASA bus to Foinikas industrial zone.
  - Drive: Attiki Odos (airport/Spata exits), ~30–40 min from centre; on-site parking at business park (not officially documented but industrial-zone venue).
- **Facilities:** power/wifi **not spec'd anywhere published** — "bring your own laptop and whatever hardware your project needs" is the only line. **No published sleeping or shower policy** — overnight building is sanctioned; bring sleeping bag/mat + earplugs as hedge. All food/drink covered for 36h.
- **Bring:** laptop + hardware, chargers/power strip (hedge), sleeping gear, ID (prize delivery may require it), GitHub+LinkedIn polished (used in screening).

## 3. BADGE SYSTEM — live & verified
- URL pattern: `hackathon.polymath42.com/badge/<slug>` — `/badge/abed-hamami` returns **200** (verified today); unknown slugs return styled "Badge not found" 404.
- **What a badge page shows:** name + "You're in", interactive **3D draggable badge card** ("Drag the card to swing it", "Flip badge" — lanyard physics), summit/panathēnea logos, per-badge generated OG image (`/badge/<slug>/opengraph-image`), "Not registered? Sign up" CTA for visitors.
- **Share videos:** downloadable **6-second badge video**, format picker: 9:16 vertical (Stories/Reels/TikTok), 16:9 horizontal (LinkedIn/X), or both. "Your badge. Your feed."
- **System mechanics (terms):** every applicant auto-gets a public profile + badge page (name/role/skills/links/team/projects/results; email/phone never public). Editable/hidable/deletable; unaccepted applicants' data ≤12 months.
- **Recruiting link:** profile/badge is the CV funnel — **CV opt-in** consent gates partner introductions; Title Sponsor receives ALL opt-in CVs, Challenge Partners get their opt-ins. Badge sharing = organic marketing loop.

## 4. EASTER-EGG GAME — Space Invaders (fully decoded from JS)
- **What:** canvas **Space Invaders clone** embedded in the site **footer** (aria-label "Space invaders mini game"), under the FAQ, above footer links. Pixel font, matches starfield/space theme (Luma theme literally "space-war"; OG art = Acropolis on floating island).
- **Mechanism:** "Press space to play" — keys (← → move, Space fire) active only while footer in viewport (IntersectionObserver gate). 24 invaders, classic edge-drop + accelerate-as-fewer-remain; enemies return fire (≤3 bullets); hit or invaders-reach-your-line = "Game over"; clear all = "Cleared". **+10 pts/kill**, 4-digit score top-right. WebAudio bleeps, "sound off/on" toggle.
- **Scoring/rewards: NONE.** Score lives in a React ref in-memory — **zero fetch/API/localStorage calls**. No leaderboard, no attendance points, no persistence. Pure aura artifact — consistent with organizer's "aura points" judging axis. Playing it well buys nothing except, arguably, aura.

## 5. MONDAY SNFCC LOGISTICS
- **Venue:** SNFCC, Leoforos Syngrou 364, Kallithea. Summit = 1 day, 4 stages: **Central Stage** (plenary — PM fireside), Alternative Stage, Lighthouse, **Book Castle** (= NLG tower reading room — mid-size, NOT the plenary; "main stage" in marketing is loose).
- **Hackathon slot:** Book Castle **18:00–18:30** — "Mini use cases / Winning teams (Hackathon)". Sandwiched between Tools for Humanity demo (17:40–18:00) and Prodyna SI talk (18:30). Summit runs to ~20:30.
- **Audience:** 5,000+ attendees, 1,200+ companies, 200+ speakers — but Book Castle holds a subset of that, not the full plenary.
- **Finalist transport Spata→SNFCC (~40 km):** **no published shuttle.** Weekend Endeavor buses are venue↔central Athens only (Sun-night return proposed). Options: taxi/ride-hail 40–50 min via Attiki Odos; Metro M2 to **Syggrou-Fix** + **free SNFCC shuttle bus**; drive — SNFCC parking exists but "fills up quickly" per FAQ. Since pitches are 18:00, finalists have all day to transit — and could watch summit sessions meanwhile.
- **Stage/equipment:** nothing published on HDMI/demo-laptop/screenshare. The mandate is live demo: "make it work and **show us the demo**. This is not a pitching competition, it's an agent at work." Submission licence covers "demo/video" → prepare live demo + recorded fallback. 5 min hard. SNFCC stages are pro AV; expect walk-up HDMI/wireless — confirm with organizers day-of.
- **Summit food:** free coffee/water/refreshments all day + finger-food buffet lunch.
- **No livestream**; talks recorded for YouTube later → a video'd pitch is your fallback artifact.

## 6. REGISTRATION / CHECK-IN / MENTORS
- **Registration (Luma only):** luma.com/x1wxi5sn — ticket types **Standard** + **Mentor**, both `require_approval`, both **sold out → waitlist active** (162+ going). Screening target: 300+ applicants → ~120 places; GitHub+LinkedIn drive automated screen + human review.
- **Application questions (verbatim):** GitHub username (optional) · **"Tell us about a time you most successfully hacked some (non-computer) system to your advantage"** (required — signature aura screen) · "What's a recent project you're most proud about?" (required) · LinkedIn profile (required) · team-matching opt-in checkbox · dietary restrictions.
- **Check-in:** standard Luma flow — approved ticket → QR code in Luma → scan at door. No custom check-in system published.
- **Mentor mechanics:** "**mentor table both days**" is the standard sponsor perk (Supporter €2k through Title €15k all include it) → sponsor-staffed mentor tables run both days. Mentors = Summit speaker list + sponsor engineers (Oumi, fal, Firecrawl, boxd, treg, Wonderful, Prosperty, Quintessential likely all staff tables). No published assign/roam system — model = **tables you walk up to**; Cognition's draft deal says "work alongside participants… no booth, no badge scanning" (consistent with table/roaming mentors, not a formal matching desk).

## GAPS (not published anywhere — ask organizers)
Hour-by-hour venue schedule · wifi/power spec · sleeping/shower policy · Monday finalist transport · pitch A/V spec (HDMI? screenshare? live vs video policy) · pitch order · judge list · challenge briefs (announced at kickoff) · agenda is stamped "tentative" and can move.
