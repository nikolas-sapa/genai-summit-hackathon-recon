---
title: "Recon Delta 2026-11-12 — site diff + partner adds"
type: source
tags: [genai-summit-hackathon, recon, delta, sponsors]
aliases: ["Nov 12 recon delta", "hackathon site diff Nov 12"]
created: 2026-11-12
updated: 2026-11-12
status: active
---

Diff vs 2026-11-11 baseline (`~/scratch/hackathon-recon-2026-11-12/` captures vs `-11-11/`).

# Nov 12 deltas

## Site was down then back
- hackathon.polymath42.com showed Vercel "deployment temporarily paused" morning Nov 12; back 200 by ~10:35 UTC — consistent with Abed shipping the changes below (solo operator, one Vercel deploy).

## Partner list changes (homepage)
- **Google ADDED** — was "proposed Oct 19" in deck layer; now public partner = signed. Deal per deck: $100/builder credits (Gemini API + Nano Banana + Veo, ≤$10k) + €8.5k credit prize-match.
- **Cloud Office ADDED** — new partner, not in Nov 11 list. cloud-office.com.
- **SHAKE talent up ADDED** — new tier label: "Hackathon Hiring Partner" (Aspasia Gkotsi, linkedin.com/company/aspasia-gkotsi).
- Removed: "sponsor deck" link + "Sponsorship enquiries" email line from sponsor CTA — now just "Book a call" (cal.com/abed42/hackathon). Deck still public at /deck.

## Deck layer — new auto-overlay feature
- Yesterday: exactly 6 personalized decks (cognition, resolve, google, endeavor, treg, nofire); all other slugs generic.
- Today: **every partner slug renders a logo-watermarked proposal deck** (`sd-watermark-sponsor` + `sd-proposal-logo` img injected): wonderful, quintessential, bigpi, fal, firecrawl, oumi, prosperty, boxd, wiserwork, always-online, crowdcruit, cloud-office.
- **`?sponsor=marathon` also renders an overlay (partners/marathon.png)** — Marathon VC not on public partner list. Pending deal signal (Papadopoulos = judge candidate + NOFire investor).
- Unknown slugs (anthropic, openai, lovable, devin, cursor, resolveai, agentic, lifetech, panathenea, shake) → still generic, no overlay.

## Status checks (unchanged)
- Resolve deck: still "Proposal prepared 10 November 2026 … no partnership is confirmed" — **ResolveAI not signed**.
- Google deck content frozen Oct 19 ("75 applications reviewed").
- treg: AGREED tier. cognition/endeavor/nofire decks live.
- Agenda identical. Prizes still €8.5k (5k/2.5k/1k), Quintessential sole "Prizes sponsored by".
- /terms + /privacy HTML 200; `Accept: text/markdown` 404s on them (md render only covers index/agenda/llms).
- JSON-LD: maximumAttendeeCapacity 120.

## Attendance
- Luma: **164 → 171 going (+7)**, still Event Full / waitlist only.

## Implications
- Google signing = third confirmed cash/credit backer visible publicly (Quintessential prizes, Google credits, treg infra). Wonderful still track-terms only (IP landmine stands — see [[wonderful-track]]/Nov 11 delta §2).
- Marathon overlay + Papadopoulos on mentor bench → watch for Marathon-affiliated challenge brief at kickoff.
- Partner-slug overlays make `?sponsor=<x>` a live probe: any NEW slug getting an overlay = deal in progress. Re-probe Fri.
