---
title: "greek voice"
type: source
tags: [hackathon, genai-summit, recon, intel]
aliases: ["greek voice"]
created: 2026-11-10
updated: 2026-11-10
status: active
---

# Greek Voice Agent — Buildable Stack Recon
**For:** Gen AI Summit Hackathon, Athens, 14–15 Nov 2026 (36h). Predicted Wonderful brief = Greek enterprise voice agent. Voice lane unclaimed.
**Verdict up front:** Cascaded pipeline (Deepgram nova-3 `el` → streaming LLM → ElevenLabs Flash/multilingual Greek voice on **fal**) inside **Pipecat**, telephony via **Twilio outbound calls to +30 mobiles** (no Greek DID needed). Gemini Live 3.x native-audio as the single-API fallback. Greek DIDs are NOT provisionable in 36h (regulatory bundle). Build for outbound + browser demo.

---

## 1. STT for Greek — ranked

| Option | Greek support | WER (Greek, FLEURS unless noted) | Streaming | 36h verdict |
|---|---|---|---|---|
| **ElevenLabs Scribe v2 / Scribe Realtime** | ✅ `ell` native | **≤5% tier** (3.1% FLEURS / 5.5% CommonVoice claimed) | Realtime WS exists | Best accuracy + it's **on fal** (`elevenlabs` endpoints) = sponsor story. Keyterm prompting (100–1000 terms) for Greeklish/brand words. |
| **Deepgram nova-3** | ✅ `el` monolingual model GA'd (changelog 16 Jul 2026); also inside `language=multi` (55 langs, code-switch native) | ~est. mid-single→low-double; nova-2 measured 17.97% (Speechmatics bench), nova-3 materially better | ✅ WS streaming, keyterm prompting | **Primary pick.** Battle-tested streaming path, `language=multi` handles El↔En code-switching mid-sentence. Deepgram has SDKs + Pipecat/LiveKit plugins. |
| **Speechmatics Enhanced** | ✅ | **6.58%** (their benchmark — best independent number) | ✅ | Premium accuracy option if Deepgram misbehaves on Greek; free eval. |
| **Whisper large-v3** (API or self-host) | ✅ | **11.45–12.32%** FLEURS | Batch only (needs chunked/VAD wrapper for "streaming") | Fine-tuned `whisper-large-v3-turbo-greek` on HF gets ~11% WER turbo-speed. Good enough, but no native streaming = extra plumbing. |
| **Google Chirp 2 / Azure STT** | ✅ el-GR | 14.91% / 13.21% (Speechmatics bench) | ✅ | Skip unless already on GCP/Azure creds. |
| **mlx-whisper large-v3 (local, Mac)** | ✅ | same weights ≈11.5% | Chunked | **Offline insurance** — if venue wifi dies, a Mac can still transcribe at ~real-time on M-series. Pre-install + pre-download weights. |
| **Parakeet TDT v3** | partial | 35% measured | — | Skip. |

**Decision:** Deepgram nova-3 streaming (`language=el` primary, `language=multi` if callers code-switch hard). Scribe v2 Realtime via fal as equal-rank alternative — test both in hour 1, keep whichever is cleaner on noisy phone audio (μ-law 8kHz degrades everything; test on actual call audio, not mic demos).

## 2. TTS for Greek — ranked

| Option | Greek | Latency (TTFB) | Quality notes |
|---|---|---|---|
| **ElevenLabs** `eleven_flash_v2_5` / `eleven_multilingual_v2` / `eleven_v3` | ✅ el in all multilingual models | Flash ≈75–135ms; **fal serves Turbo v2.5 <75ms** | Best Greek available. Named GR voices: **Theos** (warm male, most popular), **Eleni** (young Athenian female), Stefanos, Kyriakos, Georgios, ~16 GR voices total. Voice cloning works cross-lingual → clone a teammate's Greek voice for aura. **Caveat:** HN reports non-English langs sometimes leak English accent — A/B test 3 voices on Greek text before committing. |
| **Cartesia Sonic 3.6** | ✅ `el` | ~40–90ms (fastest class) | Only **2 Greek voices** in library; EU endpoint exists. Lowest-latency fallback if ElevenLabs accent offends. |
| **Azure edge-tts** `el-GR-AthinaNeural` / `el-GR-NestorasNeural` | ✅ monolingual el-GR neural | ~300ms+, non-streaming lib | **Free, unlimited, zero key.** Correct native accent, "robotic-pleasant." Perfect offline/dev fallback; good enough on stage if APIs fail. New `el-GR-Athina:DragonHDLatestNeural` HD variant exists in Azure. |
| **Google Cloud TTS** el-GR WaveNet/Neural2/Chirp-HD | ✅ | ~200–400ms | Solid, boring. Backup. |
| **OpenAI TTS / gpt-realtime voices** | works but unlisted | low | Community reports (May 2026): gpt-realtime-1.5/2 **regressed non-English accents** — flat, anglicized. Avoid for Greek output unless verified. |
| **Gemini Live 3.x native audio** | ✅ `el` (3.x audio models only — **NOT** in 2.5-flash-live's 24 langs) | ~600–1300ms e2e S2S | Single-model path; naturalness good, voice personality limited. |

**Decision:** ElevenLabs Flash/multilingual via **fal** (one FAL_KEY covers TTS + Scribe + media garnish; on-site sponsor credits likely; ask fal mentor table at kickoff for event key). edge-tts `AthinaNeural` pre-wired as the zero-dependency fallback — costs nothing, works offline.

## 3. Telephony in 36h — the honest matrix

| Path | Greek number? | Time to live | Verdict |
|---|---|---|---|
| **Twilio GR local DID** | +30 local | **NOT feasible** — since Aug 2025 requires approved RC bundle: Greek local address matching prefix + utility bill/ID. Manual review, days. | ❌ unless a teammate has a Greek utility bill pre-verified |
| **Telnyx GR DID** | +30 (Thessaloniki 231, Patras 261, Heraklion 281…) | **NOT feasible** — needs local/EU ID + VAT + LOA signed + proof of address ≤3mo; "end-user must be physically present." | ❌ same wall |
| **Twilio US/UK instant DID → receive calls** | No (+1/+44) | **~5 min**, self-serve | ✅ **inbound fallback.** Athenians can call it (intl rates ~€0.1–0.3/min — trivial for a 2-min demo). Put number on screen. |
| **Twilio OUTBOUND call to +30 mobile** | Caller ID = your US num | **~15 min** — REST call + TwiML `<Connect><Stream>` to your WS | ✅✅ **PRIMARY DEMO PATH.** No Greek DID needed at all. Agent calls a volunteer's Greek phone live. Pipecat has this exact dial-out flow documented (`TwilioFrameSerializer` + FastAPI WS). Rate to GR mobile ≈$0.10–0.25/min. |
| **LiveKit SIP / Telnyx SIP trunk** | Same DID problem | adds SIP config hours | Skip unless LiveKit-native |
| **Browser WebRTC demo** | n/a | 0 min | ✅ **always-on backup.** LiveKit/Pipecat SmallWebRTCTransport or Daily room; laptop mic + speaker. Zero telephony risk. |
| **Vonage** | no meaningful GR self-serve | — | skip |

**Demo design (who calls whom):** Stage screen shows QR → volunteer judge enters their +30 mobile → your server fires Twilio REST `calls.create` → **agent phones them live in ~5s**, mic'd room hears it over speaker. Higher aura than dial-in (proactivity = Wonderful's theme word), zero regulatory dependency. Backup 1: dial-in US number on screen. Backup 2: browser room URL. Backup 3 (dead air): pre-recorded call video.

## 4. Latency architecture & turn-taking

**Target: ≤1s mouth-to-ear.** Benchmarks (Livetok/LinkedIn 1k-call study, same providers): Retell 985ms, LiveKit ~1012ms silence-gap, Vapi 1084ms, Pipecat 1108ms — all with EN-optimized turn detection. Greek adds a wrinkle:

| Turn-taking piece | Greek OK? |
|---|---|
| Deepgram **Flux** (model-native EOT, ~260ms) | ❌ **No Greek** — `flux-general-multi` = 10 langs (en es fr de hi ru pt ja it nl). Do not plan around it. |
| LiveKit **turn-detector** MultilingualModel | ❌ 14 langs, **no `el`** — thresholds missing → falls back to English behavior. Risky on Greek phrase-final intonation. |
| **Silero VAD** (Pipecat/LiveKit plugin) | ✅ language-agnostic — works, needs tuned `min_silence` (~400–600ms) since Greek has lively pauses. |
| STT **endpointing** (Deepgram `endpointing` param / utterance_end) | ✅ language-agnostic — safest for Greek. Combine VAD + endpointing, accept ~300–500ms EOT cost. |
| Gemini Live / OpenAI Realtime built-in VAD | ✅ server-side, model-native |

**Barge-in:** all frameworks handle via VAD-interrupt → flush TTS buffer. Works with Greek fine. LiveKit interruption recovery benchmarked 78ms (best-in-class).

**Recommended pipeline (sub-1s achievable):**
```
Phone/WebRTC audio (μ-law 8k) 
→ Deepgram nova-3 WS (interim results; endpointing ~500ms; keyterms: ΟΤΕ/Cosmote/κωδικός/tracking terms)
→ LLM stream (GPT-4o-mini or Claude Haiku — Greek system prompt, sentence-chunked output)
→ ElevenLabs Flash/multilingual WS via fal (Greek voice, per-sentence streaming)
→ Twilio media stream back
= ~800–1100ms e2e. Show the live latency waterfall on the dashboard — honesty + metrics = Zindros/Gianitsos points.
```

**Framework call:** **Pipecat** (Python) — Twilio dial-out documented end-to-end, you see every stage (flatters "inspects plumbing" judge Zeibekis), Swarma/Deepgram/11labs plugins all exist. **LiveKit Agents** equally good if you want WebRTC-native + free cloud tier (1k agent min) — but accept plain VAD endpointing for Greek (no semantic turn detector). **Vapi/Retell** = managed speed-run option (configure Deepgram `el` + 11labs multilingual + BYO Twilio in ~30min) — use only if the pipeline build eats hour 6; you lose plumbing-craft points. Retell lists "from $0.07/min", Vapi $0.05/min + provider costs; both need card.

## 5. Greek-specific gotchas

- **Code-switching is the norm:** "το tracking number", "έκανα login", "το Wi-Fi", "λογαριασμό". Deepgram `language=multi` transcribes mid-sentence switches; monolingual `el` may garble English terms → prefer `multi` + keyterms, or prompt LLM that transcript may mix scripts. STT output may render English words in Latin chars inside Greek text — LLM must tolerate.
- **Greeklish:** SMS-generation users may speak or spell in Latin-alphabet Greek ("parakalo"). STT won't produce Greeklish, but RAG/knowledge docs might contain it.
- **Numbers/addresses:** phone numbers, tracking codes, AFM (tax ID) read digit-by-digit or grouped ("εξήντα εννέα…"); enable numerals/formatting; confirm-readback pattern ("σας επαναλαμβάνω: …") is expected politeness AND error-check.
- **Formality register:** enterprise agent should default to **εσείς plural + polite forms** ("θα ήθελα", "παρακαλώ περιμένετε"). Set in system prompt explicitly — LLMs drift into εσύ. Demo persona choice: telco/bank agent → formal; this detail is free authenticity aura with Greek judges.
- **Tonos/orthography:** Whisper-family outputs proper accents; fine-tuned models that strip tonos score worse on eval — irrelevant for voice, matters if transcript shown on dashboard.
- **Accent variance:** Athenian standard dominates training data; Cypriot/Northern/Cretan speakers degrade WER — pick the demo caller accordingly.

## 6. Sponsor angles

- **fal:** one `FAL_KEY` → ElevenLabs TTS (Turbo v2.5 <75ms) + Scribe v2 STT + media garnish. "Best use of fal" is historically the most winnable partner prize ($500–4k credits precedent). Say it in the pitch: "whole voice loop runs through fal."
- **Wonderful:** speak their metrics verbatim — **containment rate** (Telefónica 91.5%, Cosmote 50% zero-touch, -30% AHT). Dashboard widgets: live containment gauge (resolved vs escalated counter), per-call AHT timer vs "human baseline 6min", tool-call ledger (ticket created, SMS sent), cost/call, latency waterfall. Frame the demo as "a 36-hour FDE deployment with handover docs" — their doctrine.
- **OpenAI judge (Pittarokoili, Human Data):** measured before/after — log every call, show eval numbers, not vibes.

## 7. Hour-0 checklist
1. Test call: Twilio US num → outbound to +30 mobile → Pipecat WS echo bot (proves audio path before any AI). ~45 min.
2. A/B: Deepgram `el` vs `multi` vs Scribe-via-fal on recorded noisy Greek.
3. Pick voice: ElevenLabs Theos/Eleni vs Cartesia `el` vs edge-tts Athina — 3 judges listen blind.
4. Fallback S2S spike: Gemini Live 3.x (`el` in supported list) or gpt-realtime-1 (avoid 1.5/2 for accents) — 30 min to confirm it speaks acceptable Greek.
5. Offline kit: `pip install edge-tts mlx-whisper`, pre-pull large-v3 weights, pre-cache voice audio of the 6 demo lines ("Καλησπέρα, είμαι η ψηφιακή βοηθός…") as WAVs — worst case, agent reads canned lines.
6. ngrok/tunnel + Twilio webhook pre-configured; boxd VM kill auto-hibernate (per master brief).

## Sources
ElevenLabs docs (STT/TTS/agents language pages), Deepgram docs (nova-3 multilingual, Flux, changelog Jul 2026), Speechmatics Greek benchmark page, AliacAI whisper-base-el-en HF card, Cartesia docs Sonic 3.6, Twilio GR regulatory guidelines + Aug-2025 bundle update, Telnyx Greece DID requirements, LiveKit turn-detector HF/docs, Pipecat Twilio dial-out docs, Livetok latency benchmark, Prashant Srivastav 1k-call platform study, OpenAI community (gpt-realtime regression threads), glbgpt ElevenLabs multilingual review, HN #44195004.
