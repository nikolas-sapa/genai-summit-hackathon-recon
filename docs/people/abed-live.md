---
title: "aUed live"
type: source
tags: [hackathon, genai-summit, recon, people]
aliases: ["aUed live"]
created: 2026-11-10
updated: 2026-11-10
status: active
---

# ABED HAMAMI — LIVE TASTE SIGNALS (scraped Nov 10, 2026, ~15:00 local)
Baseline: `deep/judge-abed.md`. This file = deltas + freshest evidence only. Event T-4 days.

---

## 1. FRESHEST X ACTIVITY — @abed_hamami (teapawt mirror, last 14 days)

| Date (2026) | Signal | Decode |
|---|---|---|
| Nov 10 | reply "sick 🔥" → **@sochar__** (Socrates Charisis, Quintessential prize sponsor) | prize-sponsor circle actively posting this week; Abed watching |
| Nov 8 | reply to @parisbayarea: "**paulgraham.com/ds.html**" | still prescribing PG essays days before the event — ds.html = Do Things That Don't Scale |
| Nov 7 | reply "the Brycent effect" → @brycent | gaming/creator-economy banter |
| Nov 5 | replies "🔥 📦" → @michielmv; "agreed!" → @JSC40_; "😂 pretty much" → @ZacksJerryRig; "was thinking the same thing 😂" → **@jesslivingston** | mingling with PG's partner, hardware builders |
| Nov 4 | reply → **@evilrabbit_** (Vercel design): "great video. any chance of open sourcing or productizing the tool?" | begs for tool releases — respects shipped craft over content |
| Nov 3 | "@Suhail looks younger here than in his pfp" → @spenserskates | Suhail Doshi orbit |
| Nov 2 | "🚀🚀" → @parisbayarea; "🔥" → @JohnPhamous | |
| Nov 1 | **RT "using bots to do gtm is low aura"** | THE aura definition — still pinned to top of his values |
| Oct 30–31 | "if you're using claude code in vs code, it's not your fault you got hacked, it's natural selection" (reply to @TheHackersNews re: supply-chain hack) | terminal-native snobbery, security-aware |
| Oct 30 | "GMI 🚀"; "this's making me wanna go on a long drive"; "😂😂" → @Jason | |
| Oct 29 | "@paulg" + media | PG content again |

**3-month arc:** Oct 3 "Opus 5.5 is seriously good!" + dropped his own luma link; Sep 29 the famous "hand it to your clanker" anti-slop certificate; Sep 18 "joined @UseCorgi for a full 10 minutes, to carry the @ycombinator office hours simulator booth" (playful); Sep 17 "Renaissance or Slopaissance?"; "bangers are better than the models" (Sep 24). Arc/Dia saga Oct 22–26: "whatever that dia thing is, it's NGMI" + "OPEN SOURCE IT YOU COWARDS" + "you build something people want and love but you're so arrogantly convinced you know better…" — he HATES product abandonment + corporate second-guessing of users.

### GitHub signals (api.github.com/users/abed42)
- Bio now "**let me cook**", company "**unreal.town**", blog abed42.xyz (**dead DNS — do not cite**).
- Public events (only 3 in window — repo work is private):
  - Nov 5 ★ `boxd-sh/sdk` — **studying the sponsor's SDK**
  - Nov 5 ★ `ericzakariasson/x-feedback-agent` — friend Eric Z's feedback agent
  - Nov 2 ★ `Hardalion/agent-delegated-authority` — **delegated authority for agents — literally the hackathon's problem space**
- No public commits since Sep 21 (`expo-forge`). No orgs, no gists. All building is private → hackathon site repo NOT public; it's his code (Next.js/Turbopack = his documented stack, microcopy = his voice, hosted on his domain).

---

## 2. LINKEDIN — /in/abed42 (last ~6 weeks)
- Headline "i make things" · 1,489 followers · location now **"San Francisco Bay Area"**.
- Oct 27: reshare — venue announce (Athens LifeTech Park, free Endeavor bus).
- Oct 13: "**making these videos is so fun! feel free to dm me if you want tips on making videos like this with ai**" — he produces the hackathon's AI promo videos himself and openly invites DMs. High-access posture.
- Oct 5: "🛸🛸🛸" reshare of Socrates Charisis/Quintessential post (the "no slop in the UX, right thing/right rails/real customer" doctrine).
- Oct 2: "it's time to build!" launch reshare.

## 3. THE SITE AS TASTE SPECIMEN — hackathon.polymath42.com (re-audited today)
- **Stack:** Next.js App Router + **Turbopack** (`turbopack-*.js` chunks, `/_next/static/immutable/`), Tailwind, custom **Departure Mono** pixel font (`departure_*-module`, `.pixel` class), `next/image`, `acropolis.webp` hero, dynamic per-route OG/Twitter images, JSON-LD Event+FAQ+Org graph.
- **Easter egg:** full **Space Invaders canvas game** embedded in homepage (desktop only): "Press space to play" · "← → move · space fire" · **sound toggle** ("sound off"). Pixel-art isometric **podium SVG with trophy** for prizes section. Live countdown "**Hacking starts --D:--H:--M:--S**" with blinking alert dot.
- **Agent-native engineering:** `llms.txt` ("Agent instructions"), **every page negotiates `Accept: text/markdown`**, `/index.md` mirror, sitemap.xml, and even the **404 page is agent-legible** ("Nothing else is wrong: the server is healthy… Try one of these instead"). OG image alt: "the Acropolis on a floating island". The whole site is a demo of "built for people AND agents" — the tagline made literal.
- **Microcopy voice:** "Can you build something that people and agents want?" · "the tedious, the multi-step, the things nobody wants to do twice" · "Make something people want." (links to paulgraham.com/good.html) · "Judged on usefulness, craft, and aura points rather than polish alone" · "a project that was substantially finished beforehand will not fare well."
- **Badge system (viral mechanic):** `/badge/[slug]` per-person pages (noindex, own OG "Abed Hamami is in"). **Canvas-rendered badge you can drag to swing + flip** (physics lanyard sim), and it generates a **6-second video** client-side (canvas→MediaRecorder) in 16:9 ("LinkedIn, X"), 9:16 ("Stories, Reels, TikTok"), or both. Microcopy: "**Your badge. Your feed.**" · "A six-second video, ready for your socials." · "You're in." · "Getting your badge ready…" · "Not registered? Sign up". He turned acceptance letters into a shareable-motion-artifact generator.
- **Status:** Luma shows **Event Full — 162 going** vs ~100–120 cap → waitlist only ("Join waitlist" nav). Challenges **not published**: "Challenges will be announced during the event." `/challenges`, `/agenda`, `/podium` all 404 — no early briefs exist.

## 4. ADJACENT ARTIFACTS (what he's shipping NOW)
- **formbase.us** — HIS product, live (Next.js/Vercel): AI conversational forms. Origin story on homepage: Anthropic's "Built with Opus 4.7" hackathon application form was a chat w/ Claude; he wanted that UX everywhere → built it. Demo form literally titled "**AI Hackathon Application — Powered by Formbase**". Digs: "Tally (which i like) and Typeform are still in the web 2 era." → taste = interfaces that converse, follow up when answers are thin, skip ahead when covered.
- **ionandabed.com** (Astro) — their TBPN-style weekly show ("We are building @tbpn on a budget"). Oct 12 tweet: **interactive explainer video** — "I asked our explainer video a question and it answered with a new scene… Claude writes the scene, voices it, and splices it in at the next break. Scene 07 didn't exist when I hit enter." → media that responds to the viewer = his current wow-bar.
- **cal.com/abed42** — top event: "Chat about: Gen AI Summit Hackathon - Athens Greece" (30m) · "15 Min Formbase Meeting" · Gamerplug 20m.
- **polymath42.com** — "/copy" 404s; homepage copy: "If you're making something people want — we'll help you build it." · "tell you the truth the whole way there" · "No deck, no fluff" · "Full-stack, type-safe, tested… the parts nobody sees" · "Calm, intentional interfaces."
- **unreal.town** — GitHub company field; waitlist e-comm project, dormant publicly.

## 5. CO-ORGANIZER / SPONSOR-CIRCLE FRESH SIGNALS
- **@ionpetropoulos:** shipping agent-powered learning toys weekly — `skepsis` (skepsis-greek.vercel.app, "learn ancient greek using your agents. Open source, all local", github.com/JobMachine/skepsis) + carpe-latin.vercel.app. Nov 3: "**To master agents you need to achieve quality and trust**". Nov 2: "Did I just do 🧠 22% 💵 $406.42 overnight?" — quantifying agent output. "That's one prompt…" demos. **NB: he RT'd @NikolasSapa twice this week (Nov 2–3) — the user is already on his radar.**
- **@sochar__** (Quintessential): Nov 9 "Painted Athens, real map is happening! OSM + Google 3D + Nanobanana" + "joining the mad map game"; Nov 5 "**Trust the craft. It was always craft. The differentiator.**"; Nov 1 "best skill is to describe what you want then step aside and let the models cook… less detailed prompting → better results."
- No "what we look for" thread exists. Judging remains: usefulness · craft · aura. Quintessential's Oct 5 doctrine is still the closest thing to a public rubric.

## 6. DELTA vs PRIOR DOSSIER — what changes the winning formula
1. **Shareable artifact > silent demo.** He built a badge→6s-video machine so attendees broadcast the event. Projects that emit a shareable artifact (video, badge, score, card) match his current love language.
2. **The demo should be interrogable.** Interactive explainer video + formbase: he's obsessed with artifacts that answer back. A live agent judges can redirect mid-run ("ask it why") > a linear scripted run.
3. **Agent-legibility is now table stakes.** His site serves markdown to agents, ships llms.txt, agent-readable 404s. Ship your project's own llms.txt/README-for-agents + clean tool surface; "agents want" is literal — he checks.
4. **His current GitHub stars = the problem space.** agent-delegated-authority + x-feedback-agent + boxd sdk → scoped delegation, feedback loops, audit. A demo w/ delegated permissions + visible action log hits the live nerve.
5. **Craft-word of the week: "Trust the craft"** (sponsor circle). Minimal-prompting confidence + maximal sweat on invisible parts.
6. **Scarcity pressure:** 162 approved vs ~100 cap — the room is oversubscribed; aura must survive a crowd.
7. **He makes the promo videos himself, DMs open** — video craft is a respected skill in this room; crisp 6–30s artifacts will be noticed.
8. Challenges are sealed until kickoff — don't prep for briefs, prep the *shape* (live, interrogable, shareable, agent-legible, delegation-aware).

## SOURCES
teapawt.net/{abed_hamami,abed_hamami/with_replies,/media,ionandabed,ionandabed/media,ionpetropoulos,sochar__} · api.github.com/users/abed42 (+repos,events,orgs,gists) · hackathon.polymath42.com (+llms.txt, sitemap, /badge/abed-hamami, markdown probes) · luma.com/x1wxi5sn · linkedin.com/in/abed42 posts (Oct 2/5/13/27) · formbase.us · ionandabed.com · polymath42.com · cal.com/abed42 · genaisummitseeurope.com (JS-rendered, no Abed mention in HTML)
