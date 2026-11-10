---
title: "greek data"
type: source
tags: [hackathon, genai-summit, recon, intel]
aliases: ["greek data"]
created: 2026-11-10
updated: 2026-11-10
status: active
---

# Greek-Vertical Agent — Data Source Recon (Gen AI Summit Athens, 14–15 Nov 2026)

Ranked catalog of real, programmatically reachable Greek data sources for a 36h build.
Legend: **[LIVE]** = usable in demo with real data today · **[KEY]** = needs API key (fast) · **[SCRAP]** = scrape via Firecrawl · **[BETA]** = works but friction · **[NO]** = not realistically usable in 36h.

---

## TIER 1 — Plug-and-play, real data, no/low auth

### 1. Diavgeia (Δι@ύγεια) transparency API — [LIVE], no auth
- **What:** Every administrative act of the Greek public sector (contracts, appointments, payments, legislation refs), keyed by ΑΔΑ. Millions of decisions.
- **Endpoint:** `https://diavgeia.gov.gr/luminapi/opendata/` — REST, JSON/XML.
  - `GET /decisions/{ada}` · `GET /search` (advanced query by type/date/org/subject) · `GET /decisiontypes` · `GET /organizations/{uid}` · dictionaries for org structure.
- **Access:** All read endpoints public, zero credentials. Writing needs auth.
- **Tooling:** `pip install diavgeia` (community client, PyPI `diavgeia` v1.0), official samples at github.com/diavgeia/opendata-client-samples-python.
- **Why it wins:** Single-bidder contracts, suspicious amounts, procurement analysis — perfect agentic-analysis demo ("find me contracts awarded with 1 bid by municipality X").

### 2. KIMDIS (ΚΗΜΔΗΣ) public-contracts registry — [LIVE], no auth
- **What:** Central registry of public contracts — structured fields (CPV codes, VAT no., amounts, number of bids, procedure type).
- **Endpoint:** `https://cerpp.eprocurement.gov.gr` — Open Data API, JSON.
  - Docs: `https://cerpp.eprocurement.gov.gr/khmdhs-opendata/help` and `…/khmdhs-opendata/swagger-ui/`
- **Access:** Free under CC-BY 4.0 (Open Data API; the submission API needs credentials, not needed for demo).
- **Killer shortcut — Diavgis:** `https://diavgis.gr` already JOINED Diavgeia + KIMDIS + EU TED into one clean dataset (2.35M acts, 271k reconstructed procurement chains) and exposes **a REST API + an MCP server** (free key via email/Google signup in ~30s). For an agent hack, wiring to diavgis MCP gives you procurement-chain queries out of the box. This is the single highest-leverage source found.

### 3. data.gov.gr open-data API — [KEY], minutes to get
- **What:** ~50+ maintained datasets via unified query API: `sailing_traffic` (ferry passengers/routes!), `oasa_ridership`, `road_traffic_attica`, EVs, telecom indicators, education results, etc.
- **Endpoint:** `GET https://data.gov.gr/api/v1/query/{dataset}?date_from=…&date_to=…` · Swagger: `https://data.gov.gr/api/v1/docs/swagger/` · full schema mirror: `https://kauth.github.io/govgr-opendata-api-schema/`
- **Access:** Register at data.gov.gr → token emailed (usually fast, but **request it NOW, don't wait for the event**). Add `download/` prefix for CSV/JSON dump.
- **Tooling:** `pip install pydatagovgr` — wraps auth + retries.
- **Demo angle:** `sailing_traffic` = real ferry passenger counts by port; `oasa_ridership` + `road_traffic_attica` for a mobility agent.

### 4. OASA Telematics — Athens real-time transit — [LIVE], no auth
- **What:** Live bus/trolley positions, stop arrivals, routes, schedules for all Athens public transport.
- **Endpoint:** `GET/POST https://telematics.oasa.gr/api/?act=<action>&p1=<param>`
  - `webGetLines`, `webGetRoutes`, `webGetStops`, `getStopArrivals` (ETA in minutes), `getBusLocation`, `getClosestStops`, `getDailySchedule`.
- **Access:** Unofficial/undocumented but stable, no key. Docs: `oasa-telematics-api.readthedocs.io`; Home Assistant integration exists (`oasa_telematics`).
- **Demo angle:** "Where's my bus" agent in Greek — real ETAs. Fair-use caveat (polite rate limiting, maybe contact OASA for production).

### 5. GEMH business registry OpenData API — [KEY], instant test key
- **What:** ΓΕΜΗ company data — name, VAT (ΑΦΜ), status, filed documents, legal type; search by ΑΦΜ/name/ΚΑΔ/region.
- **Endpoint:** `https://opendata-api.businessportal.gr/opendata/` — Swagger UI: `/opendata/docs/`, spec: `/api-docs`.
- **Access:** Header `api_key`. Docs explicitly let you test everything with the literal key **`api-docs-key`** (rate-limited per IP) — enough for a demo. Real key via registration form at `opendata.businessportal.gr`.
- **Tooling:** npm pkg `@infinitypartners/gemi-opendata-client` (typed TS client).
- **Demo angle:** "Is this company legit?" — agent pulls filing history, status, linked decisions.

### 6. Mitos — gov.gr service catalog API — [LIVE/KEY]
- **What:** Εθνικό Μητρώο Διοικητικών Διαδικασιών — machine-readable registry of ~2k gov.gr administrative procedures (steps, documents, deadlines, fees). The knowledge backbone for a bureaucracy agent.
- **Endpoint:** `https://api.digigov.grnet.gr/v1/services?page=1&limit=100` and `/v1/services/{id}` — JSON, bilingual titles.
- **Access:** API key via email to `api@mitos.gov.gr` — **email now**. Docs: `https://api.digigov.grnet.gr/info/`.
- **Note:** The procedure *catalog* is public; individual citizen operations (submitting applications, taxisnet) are NOT public APIs.

### 7. aisstream.io — live vessel AIS — [KEY], instant
- **What:** Real-time AIS positions/identity of ships globally via WebSocket. Bounding-box the Aegean → live ferry/shipping traffic demo.
- **Endpoint:** `wss://stream.aisstream.io/v0/stream` — subscribe with APIKey + `BoundingBoxes: [[[39.5,22.0],[35.0,28.5]]]` + `FilterMessageTypes:["PositionReport","ShipStaticData"]`.
- **Access:** Free, GitHub login → instant API key. Max 3 concurrent connections, server-side only (browser WS refused), live-only (no history/replay).
- **Alternatives:** MarineTraffic API = paid, skip for 36h. AIS Hub (aishub.net) free but registration is slower.
- **Demo angle:** Map of live Aegean ferries + agent narrating positions/ETA. Very visual.

---

## TIER 2 — Strong sources, some friction

### 8. Ferryhopper MCP + API — [KEY/BETA]
- **What:** Ferry routes/schedules/prices, 220+ operators, 4k+ routes.
- **Access:** **Ferryhopper has an MCP server for AI agents** (`partners.ferryhopper.com/mcp`) — contact/partnership needed for a key; affiliate program has widget API keys (self-serve-ish). B2B `FerryhAPI` needs a contract — too slow unless they sponsor/help.
- **36h fallback:** data.gov.gr `sailing_traffic` for historical stats + Firecrawl scrape of Ferryhopper/ferries.gr search pages for "live" itineraries.
- **Pitch angle:** If Summit organizers can broker a Ferryhopper API/MCP key, this is a headline integration for a tourism agent.

### 9. Ktimatologio (Cadastre) open data — [BETA]
- **What:** National cadastre parcel boundaries for areas in the "operating cadastre".
- **Endpoints:**
  - WMS: `http://gis.ktimanet.gr/inspire/rest/services/cadastralparcels/CadastralParcelWMS/MapServer/exts/InspireView/service` (INSPIRE view service)
  - Full shapefile parcels dataset: `data.ktimatologio.gr` (DKAN portal — dataset `a7870ace…` / `0dee2302…`), CC open.
- **Caveat:** Geometry only (no owner/attribute data — that's paywalled on ktimanet). Useful for map overlays on a property agent, not ownership lookup.

### 10. Banking APIs — sandboxes real, production impossible in 36h
- **NBG:** `developer.nbg.gr` — real sandbox (register app → subscribe → OAuth sandbox flow; Berlin Group v1.3.6 AIS/PIS/CoF + Cards API). Mock data only in sandbox.
- **Alpha Bank:** `developer.api.alphabank.eu` — sandbox `https://gw.api.alphabank.eu/api/sandbox`, OAuth2, signup self-serve.
- **Piraeus:** `rapidlink.piraeusbank.gr` — PSD2 AIS/PIS + PB APIs, sandbox.
- **Eurobank:** API Portal (PSD2 + premium open-finance), registration required.
- **Viva.com (Viva Wallet):** `demo.vivapayments.com` + `demo-api.vivapayments.com` + `demo-accounts.vivapayments.com` — easiest of the bunch: demo merchant account, test cards, OAuth `client_credentials`. **Best pick for a payments demo.**
- **Reality check:** PSD2 production APIs need TPP eIDAS certs — never in 36h. Use sandboxes; the demo story is "Greek open-banking agent that CAN run against real infra."

### 11. Spitogatos / XE.gr — [SCRAP]
- **Spitogatos:** Cloudflare-protected Next.js app. Internal search API `POST /n_api/v1/properties/search-results` (offset pagination, ~30/page) — Apify actors reverse it by driving it from a real browser. Direct curl likely blocked.
- **Firecrawl feasibility:** Public listing pages may extract OK (Cloudflare is the risk — test early). Alternatives: Apify actors (`automation-lab/spitogatos-property-scraper`, `haketa/spitogatos-scraper`, ~free-tier runs), or api.sh Spitogatos endpoints (1 credit/call, ~free trial).
- **XE.gr:** same game, less documented; treat as harder scrape.
- **36h verdict:** Doable for a real-estate agent — pre-build a cached dataset the night before (hackathon-legal if you collected it), and hit Firecrawl live as the "fresh" story with cache fallback.

### 12. Athens municipal open data — [LIVE], CKAN
- **What:** City of Athens datasets + Athens Smart Neighbourhood (WiFi usage, environmental sensors, registries).
- **Endpoint:** `https://opendata.cityofathens.gr/api/3/action/{package_search,datastore_search,datastore_info}` — standard CKAN API, public, no key.
- **Postman docs:** `documenter.getpostman.com/view/51309911/2sBXinJWVo` · RDF dump: `/catalog.rdf?fq=is_nsip:No`.

### 13. OSM Greece + geodata.gov.gr — [LIVE]
- Overpass (`overpass-api.de`), Nominatim geocoder — full Greece coverage for POIs, municipal boundaries.
- `geodata.gov.gr` national geoportal — WMS/WFS layers (admin boundaries, environment).
- Athens metro/tram GTFS: OASA publishes static GTFS (check `oasa.gr`/transportforathens mirrors); telematics API covers real-time anyway.

---

## TIER 3 — Limited/paywalled/no-API (flagged)

### 14. Athens International Airport (aia.gr) — [BETA]
- No official public API. aia.gr publishes an RTFI arrivals/departures page (refreshing every 2 min) — scrape via Firecrawl.
- Real API options: aviation-edge.com, airlabs.co, aviationstack — all have free keys/tiers covering ATH. Pick one, key in minutes.

### 15. taxisnet / GSIS interop — [NO]
- No public API. GSIS web services are inter-agency only. Any "tax assistant" must be a RAG agent over published guides (aade.gr documents via Firecrawl) + Mitos procedures — NOT live citizen data.

### 16. INSETE / ELSTAT — [NO as API, OK as data]
- INSETE: tourism stats as PDFs/XLSX only → RAG material, not API.
- ELSTAT: Excel/PDF dissemination, no clean public API. Use **Eurostat SDMX API** instead: `https://ec.europa.eu/eurostat/api/dissemination/sdmx/3.0/data/dataflow/ESTAT/{ID}/1.0` — free, covers all Greece indicators (tourism nights, unemployment…). `linked-statistics.gr` SPARQL endpoint also exists (2011 census).

### 17. TEE (Technical Chamber) — [NO]
- No public API; permit/engineer data behind member portal. Skip.

---

## Greek LLM / NLP resources — the differentiator play

- **Llama-Krikri-8B (ILSP/Athena RC)** — the NEW flagship Greek LLM, successor to Meltemi. `huggingface.co/ilsp/Llama-Krikri-8B-Instruct` (+`-Base`, +GGUF variants). Llama 3.1-8B base, 56.7B Greek tokens CPT, **128k context** (~80k Greek words), polytonic/Ancient Greek support, Llama 3.1 license. Try it: `chat.ilsp.gr`.
- **Meltemi-7B (v1/v1.5, +Instruct)** — Mistral-7B Greek CPT, 8k ctx. ILSP officially says use Krikri instead (+34.8% on Greek IFEval), but Meltemi is smaller/cheaper to LoRA-tune in 36h.
- **Fine-tuning with Oumi:** Krikri/Instruct fine-tunes with standard Llama recipes — Oumi supports Llama-family configs; a 36h LoRA on Greek Q&A data (diavgeia procedures, Mitos steps) is realistic on sponsor credits. "Oumi + Krikri + Athena RC" = maximum local resonance; ILSP is literally an Athens institution.
- **Other Greek NLP assets:** `nlpaueb/greek-bert` (GreekBERT), Greek spaCy/Stanza models, ILSP corpora, Greek parliamentary proceedings corpus on HF, `ilsp` HF org datasets, Greek eval suite integrated in lm-eval-harness.
- **ASR/TTS:** Whisper handles Greek fine; for TTS, check XTTS-v2 (supports el) — good enough for a voice agent demo.

---

## Firecrawl (sponsor) — highest-value targets
1. **Ferryhopper/ferries.gr search results** → live ferry itineraries for tourism agent.
2. **Spitogatos/XE listing pages** → property agent real data (mitigate Cloudflare w/ crawl+map endpoints; cache fallback).
3. **aia.gr RTFI page** → live Athens flights.
4. **aade.gr / gov.gr guides, ergani.gov.gr, ypergasias** → RAG corpus for bureaucracy agent.
5. **marinetraffic pages** as AIS fallback; **epixeirisi/company pages** as GEMH supplement.

---

## Recommended 36h combos (real-data-first)

| Vertical | Stack | Demo kill-shot |
|---|---|---|
| **Bureaucracy agent** | Mitos catalog + Diavgeia search + Krikri via Oumi | "What do I need for X?" answered from live gov registry + cited ΑΔΑs |
| **Procurement watchdog** | diavgis MCP (Diavgeia+KIMDIS+TED) | "76% of awards had a single bid" — instant wow |
| **Property agent** | Firecrawl→Spitogatos + Ktimatologio WMS + OSM + GEMH | Listing → parcel overlay → check seller's company on GEMH |
| **Shipping/marine** | aisstream.io Aegean bbox + data.gov.gr sailing_traffic | Live ferry map + historic route stats narration |
| **Tourism/mobility** | OASA telematics + cityofathens CKAN + ferry scrape | "Next bus to Piraeus + ferry to Hydra" one agent turn |
| **Fintech** | Viva demo + NBG/Alpha sandbox | Payment-initiation agent on real demo rails |

**Pre-event checklist (do NOW, not day-1):** request data.gov.gr token, GEMH api_key, Mitos API key (email api@mitos.gov.gr), diavgis key, aisstream key (GitHub), Viva demo account, Alpha/NBG sandbox signup, test one Firecrawl scrape of spitogatos.gr to gauge Cloudflare blocking.
