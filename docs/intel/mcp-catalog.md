---
title: "mcp catalog"
type: source
tags: [hackathon, genai-summit, recon, intel]
aliases: ["mcp catalog"]
created: 2026-11-10
updated: 2026-11-10
status: active
---

# MCP Catalog — Gen AI Summit Hackathon (Athens, 14–15 Nov 2026)

Recon: every MCP server worth pre-wiring, grouped by sponsor/official, Greek ecosystem, and general agent infra. Plus composition architecture and the demo design that maximizes judge impact. Verified against vendor docs/repos 2026-11.

---

## 1. Sponsor / Official MCPs

### 1.1 Firecrawl MCP — CONFIRMED, flagship-grade
- Endpoint (hosted): `https://mcp.firecrawl.dev/v2/mcp` (bearer API key) or `https://mcp.firecrawl.dev/v2/mcp-oauth` (OAuth browser sign-in). **Keyless tier exists**: `firecrawl_search`, `firecrawl_scrape`, `firecrawl_parse` work with no account inside daily limits — ideal hackathon fallback.
- Local OSS option: `github.com/firecrawl/firecrawl-mcp-server` (stdio/SSE), cloud or self-hosted backend.
- Tools: `firecrawl_search`, `firecrawl_scrape` (markdown or JSON-schema extraction), `firecrawl_map`, `firecrawl_crawl` + `firecrawl_check_crawl_status`, `firecrawl_parse` (PDF/doc/xlsx/html), `firecrawl_agent` + `firecrawl_agent_status` (autonomous multi-source research), `firecrawl_interact` + `firecrawl_interact_stop` (click/type/navigate), `firecrawl_monitor_*` (change detection), `firecrawl_find_tools` (Alexandria provider catalogue), usage/credit tools.
- Demo value: turn any buyer/ministry/TED webpage into structured records live on stage. `firecrawl_scrape` with JSON schema is the crowd-pleaser.

### 1.2 Wiserwork MCP — CONFIRMED (made by 100mentors)
- Endpoint: `https://mcp.wiserwork.ai/mcp` (Streamable HTTP, OAuth sign-in, read-only).
- Tools (4): `list-meetings` (schedule from synced Google/Outlook calendar, filters "my next meeting"/"today"/"last week"/free-text), `get-transcript` (speaker segments + timestamps), `get-summary` (TL;DR, key points, decisions; single or multi-meeting), `get-action-items` (assignee, due date, status).
- Hard requirement: needs a real Wiserwork account with calendar connected and **recorded meetings** — empty account returns empty results. Pre-wire before day 1: create account, sync calendar, record one kickoff meeting so the agent can query "what did we decide."
- Demo value: agent reads team decisions from this morning's meeting and acts on them. Very "agent at work."

### 1.3 Oumi MCP — CONFIRMED, in OSS repo
- Install: `pip install "oumi[mcp]"` → `oumi-mcp` stdio entry point (built on FastMCP).
- Tools (14): `get_started` (call-first catalog), `search_configs`, `get_config`, `list_categories`, `validate_config`, `pre_flight_check`, `run_oumi_job` (local/cloud, dry-run default), `get_job_status`, `get_job_logs`, `list_jobs`, `cancel_job`, `stop_cluster`, `down_cluster` (destructive), `get_docs`, `list_modules`.
- Resources: `guidance://mle-{workflow,train,synth,analyze,eval,infer}` + built-in prompts (train/infer/eval/synth/analyze/mle_workflow).
- Caveats: path-sensitive tools need `client_cwd`; env creds (HF_TOKEN, WANDB) via config `env` block; cloud launch needs provider extras + `sky check`.
- Demo value: "agent launches a LoRA fine-tune from chat" is a strong ML-cred moment; dry-run default makes it safe on stage.

### 1.4 NOFire — CONFIRMED MCP + Brig sandbox (two assets)
- NOFire MCP: `https://mcp.nofire.ai/mcp` (hosted, read-only bearer token). 9 read-only tools for production map/incident context: `nofire_search_entities`, `nofire_get_entity_dependencies`, `nofire_get_entity_changes` (changes + correlated commits/PRs), `nofire_get_recent_deploys`, `nofire_assess_deployment_risk` (0–100 score), `nofire_analyze_blast_radius` (failure by hop depth), plus incident-history tools.
- Requires a workspace with ≥1 connected data source (Grafana/Prometheus/Datadog/k8s agent) else empty results.
- Brig: `brig.sh`, Apache-2.0 microVM sandbox for coding agents (`curl -fsSL https://brig.sh/install | sh`), profiles for Claude Code/Codex/Cursor. Not itself MCP — but "our demo agent runs inside Brig microVMs" is a security-story bonus and flatters the sponsor.
- Demo value: run the whole agent harness inside Brig and say so on stage.

### 1.5 Ferryhopper MCP — CONFIRMED, public, no auth shown
- Endpoint: `https://mcp.ferryhopper.com/mcp` (Streamable HTTP). Docs: `ferryhopper.github.io/fh-mcp`. First MCP in the ferry industry (launched Dec 2025).
- Tools (6, all read-only): `search_ferry_trips` (1–5 legs: one-way, round-trip, island-hopping chain; human-readable place names), `trip_details` (vessel specs/amenities/photos/prices by option id), `get_ports`, `get_direct_connections_for_ports`, `get_disruptions` (strikes/weather/cancellations by country+date, e.g. GR), `search_trips` (deprecated).
- Bonus: 4 MCP-apps UI widgets (`ui://widgets/*`) — hosts that render MCP apps get interactive trip pickers.
- Demo value: pure Athens flavor. "Agent checks disruptions then books the site-visit ferry" lands perfectly at an Athens hackathon with a Ferryhopper sponsor.

### 1.6 Diavgis.gr MCP — CONFIRMED, the big one
- Endpoint: `https://mcp.diavgis.gr/mcp` (Streamable HTTP; supports protocol revs 2024-11-05 → 2026-07-28). Repo: `github.com/omegaaistudio/diavgis-mcp`. REST twin: `api.diavgis.gr/v1` + `openapi.json`.
- Auth: `Authorization: Bearer dvg_xxx` (also `X-API-Key`). Works keyless at lower rate limits; free account → key in 30s. One key covers REST + MCP.
- Tools (10): `search_tenders`, `expiring_contracts` (running contracts ending soon), `find_entity`, `get_act`, `get_entity`, `get_chain` (tender→award→contract→payments as one story), `rank_entities`, `spend_by_cpv`, `entity_counterparties`, `get_quota`.
- Data: 858k acts, 60k entities from Diavgeia + KIMDIS + EU TED, cross-linked into procurement chains, OCDS 1.1, GDPR-safe (natural persons redacted).
- Demo value: THE flagship data source. "Which cleaning contracts expire in 30 days in Thessaloniki" / "who wins the most awards at org X" — instant civic-tech wow.

### 1.7 treg — CONFIRMED MCP (their proxy IS tool-calling)
- Endpoint: `https://treg.to/mcp/` + `Authorization: Bearer <token>` (or `X-Treg-Token`). Live at treg.to, OSS self-hostable (`superdesigndev/treg`).
- Tools (5): `catalog_search` (find by job, not vendor), `catalog_get`, `call` (result carries `cost_usd`), `balance`, `my_tools`.
- What it is: OpenRouter-for-tools. One token reaches 4,100+ catalogued provider endpoints across ~126 providers (SEO/SERP, backlinks, social, enrichment, ads, scraping, image/video gen), priced per call at cost, + team's own registered keys/CLIs/skills callable without credentials leaving the server. Credentials injected server-side.
- Demo value: escape hatch — any external API the demo needs but nobody wired an MCP for, treg covers via `catalog_search` → `call`. New teams get $1.00 free.

### 1.8 boxd — PARTIAL: agent spawning yes, native platform MCP no
- boxd = persistent KVM microVMs for agents (<10ms boot, <200ms fork, Europe-hosted). Agents spawn machines via `boxd` CLI/API (`boxd machine new/exec`), not via an MCP endpoint — their own blog concedes no built-in platform MCP transport (unlike competitor sprites.dev).
- MCP angle: `boxd manage integrations mcp linear claude` injects 100+ integrations (GitHub, Linear, Slack…) as MCP servers into Claude Code/Codex/OpenCode running on boxd machines. Claude Code ships pre-installed + pre-authed in the image.
- Demo value: "each sub-agent gets its own forked microVM" — parallelism story + sponsor infra, not an MCP you call.

### 1.9 fal MCP — CONFIRMED
- Endpoints: `https://mcp.fal.ai/mcp` (bearer `FAL_KEY`) and `https://mcp.fal.ai/mcp-relay` (OAuth sign-in). One-command installer: `curl -fsSL https://fal.ai/mcp/install.sh | bash` wires every coding agent on the machine.
- Tools: discovery (`search_models`/`browse_models`, `recommend_model`, `get_model_schema`, `get_pricing`, `estimate_cost`, `search_docs`/`search_guidance`/`read_guidance`), execution (`run_model`, `submit_job`/`submit_jobs` up to 8, `check_job`), utility (`upload_file`, account tools). 1,000+ generative models: image, video, audio, 3D, upscale.
- Demo value: generate the deliverable's hero image / narrated video / report illustration live. Cheap, fast, visual.

### 1.10 Wonderful — NOT an MCP provider (consumer signal)
- Enterprise AI-agent OS (Index/Insight/IVP/Bessemer-backed, ~790 staff, hiring FDE/Agent Engineer in Greece). No public MCP server found. ~25 JDs list "APIs, MCP, data flows, system integrations" as required skill — they *consume* MCP to wire agents into enterprise systems.
- Read: MCP fluency is literally their hiring bar. An MCP-orchestrated build speaks their language.

---

## 2. Greek Ecosystem MCPs

| Server | Endpoint / Install | Tools | Auth | Notes |
|---|---|---|---|---|
| **diavgis.gr** (flagship) | `https://mcp.diavgis.gr/mcp` | 10 (see 1.6) | Bearer `dvg_` or free tier | Diavgeia+KIMDIS+TED cross-linked |
| diavgeia-mcp-server (michalisKout) | GitHub, self-run | `search-decisions`, `get-decision` | none | Raw Diavgeia alternative — use only if diavgis rate limits bite |
| **oasa_mcp** (fabianhogger) | `npx -y oasa-mcp` | 10: `stop_arrivals`, `find_stops`, `routes_at_stop`, `list_lines`, `line_routes`, `route_stops`, `vehicle_positions`, `route_shape`, `line_schedule`, `line_service_days` | none (public telematics) | Live Athens bus arrivals, Greek+Latin script names. "Live bus data on stage" = local delight |
| oasa-mcp (ManosMrgk) | GitHub, stdio | 7 similar tools | none | Backup OASA impl |
| **gemh-mcp-server** (whybothercoding) | GitHub | 12 read-only: `gemh_search_companies`, `gemh_get_company`, `gemh_get_company_documents`, `gemh_download_file`, `gemh_search_activities` (ΚΑΔ), + reference-data tools | GEMH open-data key | Greek Commercial Registry — pairs with diavgis for supplier due-diligence |
| mcp-data-gr (pipeworx) | `https://gateway.pipeworx.io/data-gr/mcp` | `search_datasets`, `dataset`, `query_resource` (CKAN DataStore rows) | gateway | data.gov.gr via Pipeworx (971+ sources on full gateway) |
| datagovgr-mcp-server (ilias-ant) | Docker self-run | data.gov.gr API wrapper | datagovgr key | Alternative data.gov.gr path |
| ELSTAT | — | — | — | **No MCP found.** statistics.gr has an API — gap = opportunity if you need stats |

Judges' note: diavgis + GEMH + OASA + Ferryhopper in one agent = "Greek civic data agent" — every local sponsor sees their MCP exercised.

---

## 3. General Agent MCPs (pre-wire list)

| Server | Install / URL | Auth | Why |
|---|---|---|---|
| **GitHub** (official) | remote `https://api.githubcopilot.com/mcp/` or local `github/github-mcp-server` | OAuth or PAT; `--read-only` / toolset flags | repo, issues, PRs, Actions; agent commits its own report PR |
| **Slack** (official) | `https://mcp.slack.com/mcp` | OAuth via Slack app (confidential OAuth, user token; no DCR) | `search_public(+_private)`, `read_channel`, `read_thread`, `send_message`, `schedule_message`, canvases — the "deliverable lands in #channel" closer |
| **Filesystem** (reference) | `npx -y @modelcontextprotocol/server-filesystem <dirs>` | n/a | scratchpad + report output; sandbox to a work dir |
| **Postgres** | reference archived → use Postgres MCP Pro (`crystaldba/postgres-mcp`, restricted/read-only mode) or DBHub `npx -y @bytebase/dbhub --dsn ...`; Supabase/Neon host their own | DSN | if the demo stores analysis |
| **Playwright** (Microsoft) | `npx -y @playwright/mcp@latest` | n/a | accessibility-tree browser automation — deterministic UI agent beats screenshot-based |
| Fetch / Time / Memory / Sequential Thinking | `modelcontextprotocol/servers` reference set | n/a | cheap primitives; Time fixes model "today" bugs |

Remote-first for demos: HTTP MCPs = zero local process management, one config block each.

---

## 4. Architecture Intel — composing N MCPs in 36h

### Client library choice
- **Python**: official `mcp` SDK. `ClientSessionGroup` connects to many servers and merges `group.tools` into one dict; `group.call_tool(name)` routes to owning session automatically. Name collisions raise `MCPError` at connect → fix with `component_name_hook` (prefix tools per server, e.g. `diavgis.search_tenders`). Transports: `StdioServerParameters`, `StreamableHttpParameters`, `SseServerParameters`.
- **TypeScript**: `@modelcontextprotocol/sdk` `Client` + per-server transport, or higher-level **mcp-use** (`MCPClient` multi-server + `server.proxy({...})` to aggregate local stdio + remote HTTP into ONE namespaced endpoint), or **mcp-orchestrator** (multi-server + code-mode where the LLM writes TS calling tools). LangChain/LangGraph → `langchain-mcp-adapters`.
- **Aggregator pattern** (recommended): proxy all servers through one FastMCP (Py) or mcp-use proxy (TS) endpoint → the demo UI/harness sees a single MCP with namespaced tools. One config, one auth surface, one "tool wall" screenshot for the pitch.

### Auth patterns (ranked for hackathon practicality)
1. **Static bearer/API-key headers** — zero ceremony: diavgis (`Bearer dvg_`), treg (`Bearer`/`X-Treg-Token`), NOFire (read-only token), fal (`Bearer $FAL_KEY`), GitHub PAT. Headless-agent friendly. **Use these.**
2. **OAuth 2.1 remote** — Slack, fal relay, Firecrawl OAuth, Wiserwork: browser consent once, token cached after. Do the dance BEFORE the event on the demo machine; never live on stage.
3. **stdio + env vars** — filesystem, OASA, Oumi, Playwright: secrets via config `env` block (GUI clients ignore `.zshrc`).

### Failure modes to pre-empt
- Tool-name collisions across servers (mitigate: namespacing hook / proxy).
- Empty-result traps: Wiserwork (no recorded meetings), NOFire (no data source) return empty, not errors — seed accounts beforehand.
- Rate limits: diavgis keyless tier is low — get the free `dvg_` key now.
- `run_oumi_job`/`down_cluster` and Slack `send_message` are write paths — keep the agent read-mostly; put destructive calls behind a manual gate.

---

## 5. The MCP-Native Demo Design (recommended)

**"Procurement Copilot" — an agent that watches Greek public tenders and does the busywork.**

Pipeline (each arrow = one MCP, every sponsor touched):

1. `diavgis.search_tenders` + `diavgis.expiring_contracts` → find relevant tenders ("medical consumables closing this week in Attica").
2. `diavgis.get_chain` + `rank_entities` + `spend_by_cpv` → competitive landscape: who wins these awards, incumbent pricing.
3. `gemh_search_companies` → due-diligence the winning supplier (or the buyer).
4. `firecrawl_scrape` (JSON schema) on the tender PDF/buyer page + `firecrawl_search` → extract deadlines, CPVs, docs.
5. `wiserwork.get-summary` → "what did our team decide about pursuing healthcare tenders in Tuesday's meeting" — memory that flattens.
6. `ferryhopper.get_disruptions` (GR, date) + `search_ferry_trips` (Piraeus→island legs) → site-visit logistics for island tenders.
7. `oasa_mcp.stop_arrivals` → "and your bus to the submission office leaves in 8 min" (local color, live data).
8. `fal.run_model` → generate the bid one-pager illustration.
9. `filesystem` write → `bid-brief.md`; `github` → PR with the brief; `slack.send_message` → deliver to #procurement with booking link.
10. Fallback: anything missing → `treg.catalog_search` → `treg.call`.

Why it wins: 4 sponsor MCPs + 3 Greek MCPs + 3 general MCPs in ONE coherent story; read-only except the final deliverable; every tool call is a visible "agent at work" beat for judges. Wiserwork ships MCP into Claude/Cursor, Firecrawl ships MCP — an MCP-native build IS the ecosystem's lingua franca.

**B-side pitch**: same harness, swap domain → "Incident co-pilot" (NOFire blast-radius → GitHub PR → Slack) flatters NOFire specifically. Keep as backup.

**36h pre-wire checklist**: diavgis `dvg_` key, fal key, treg team token ($1 credit), GitHub PAT, Slack app OAuth done once, Wiserwork account + 1 recorded meeting, Firecrawl free key; stdio servers (oasa, filesystem, playwright) smoke-tested; aggregator proxy exposing one endpoint.
