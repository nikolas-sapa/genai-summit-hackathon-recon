---
title: "sponsor fal"
type: source
tags: [hackathon, genai-summit, recon, sponsors]
aliases: ["sponsor fal"]
created: 2026-11-10
updated: 2026-11-10
status: active
---

# Sponsor teardown — fal (fal.ai)
Gen AI Summit Hackathon, Athens, 14–15 Nov 2026. Researched 9–10 Nov 2026.

## TL;DR
- fal is a **listed partner of this exact hackathon** (hackathon.polymath42.com). Expect on-site credits, a mentor table, and almost certainly a "best use of fal" partner award — their standard play.
- One API key → 1,000+ models: Veo 3.1, Sora 2, Kling 3.0/O3/4.0, FLUX 3/2, Nano Banana 2/Pro, Seedream, ElevenLabs full suite, Hunyuan3D, SAM 3, realtime WebSocket/WebRTC endpoints.
- Pitch is speed + zero ops: sub-second images, H3 Max renders 5s video in <3s, realtime video streaming (H3 Max Director behind fal.live), ElevenLabs Turbo TTS <75ms.
- No free API tier. New accounts: 2 concurrent requests, prepaid credits only. Fix: on-site sponsor credits (highest probability) + Builder Grant ($25–250, Greece eligible) + $10–25 self-funded top-up as floor.
- For "aura points" (literal judging criterion): realtime/live media beats everything. Prioritize H3 Max Director or Kling i2v with native audio, an ElevenLabs voice agent, and Nano Banana 2 image loop. A talking, self-directing media agent > another chatbot.

## Company snapshot
- Generative media inference infra, SF (Features & Labels Inc.), founded 2021 by Burkay Gür + Görkem Yurtseven. ~185 employees.
- **$16B valuation as of 3 Nov 2026** (11 days before the hackathon): $1.3B Series F led by Bessemer (NVIDIA, Sound Ventures, T. Rowe Price participating); combined Series E+F = $1.65B. >$800M annualized revenue. CEO admitted summer demand outstripped capacity → rate limiting.
- Business: hosted Model APIs (pay per output), fal Serverless (deploy own models, billed/sec GPU while runner alive), dedicated compute, fal WMA (World Model Accelerator — custom inference engine + WebRTC gateway for realtime streams, ~36ms p50 frame latency).
- Post-trains partner models themselves (H3 Max = their tuned MiniMax H3; FLUX 3 Max co-work with Black Forest Labs). Day-0 launch partner for frontier video models.

## API surface — what's actually on the key
Endpoint IDs; call everything the same way. Fetch `https://fal.ai/models/<endpoint>/llms.txt` for live schema + exact price (canonical, machine-readable, per their docs).

### Video (the flagship surface)
| Model | Endpoint ID | Price | Notes |
|---|---|---|---|
| Veo 3.1 | `fal-ai/veo3.1` | $0.20/s silent, $0.40/s w/ audio (720p/1080p), 4K up to $0.60/s | 4/6/8s clips. Name recognition for judges |
| Veo 3.1 Fast / Lite | `fal-ai/veo3.1/fast`, `.../lite` | Fast $0.10–0.15/s; Lite $0.03–0.05/s | Lite = draft tier |
| Sora 2 | `openai/sora-2` family | per listing | Yes, Sora 2 is listed on fal |
| Kling 3.0 Pro | `fal-ai/kling-video/v3/pro/{text,image}-to-video` | ~$0.14/s fal list; ~$0.168/s w/ audio per trackers | Arena-top motion quality, native audio |
| Kling O3 / 4.0 | `fal-ai/kling-video/...` | O3 $0.112–0.14/s; 4.0 $0.157–0.235/s | O3 does start+end frames; 4.0 goes to 30s |
| Kling 2.5 Turbo Pro | `fal-ai/kling-video/v2.5-turbo/pro/image-to-video` | $0.07/s | Cheap reliable fallback |
| FLUX 3 Max (video) | `blackforestlabs/flux-3-max/{text,image}-to-video` | $0.085/s | BFL frontier video w/ optional audio, post-trained w/ fal |
| MiniMax H3 Max | `minimax/h3-max/text-to-video` | $0.05/s | **fal's own post-train. 5s clip in <3s.** Up to 15s, 480p/768p, prompt adherence champ |
| H3 Max Turbo | `minimax/h3-max-turbo/text-to-video` | $0.025/s | Bulk/draft tier |
| **H3 Max Director** | realtime session API | **$0.08/s generated, 60s min** | Continuous steerable stream — send new prompts mid-generation. Powers fal.live. Top aura pick |
| Seedance 2.5 | `bytedance/seedance-2.5/text-to-video` | ~$0.30/s 720p w/ audio | Long single takes 16–30s, synced audio |
| Grok Imagine | `xai/grok-imagine-video/...` | $0.05/s | t2v/i2v/reference |
| LTX 2.3/2.5 Pro | `fal-ai/ltx-2.3/audio-to-video` | ~$0.12–0.17/s 720p | Audio-synchronized video, up to 4K on Fast |
| Flashtalk | `fal-ai/flashtalk` | per listing | Talking-head from 1 photo + voice clip |
| Others | Vidu Q3, PixVerse V6, Wan 2.5/3 | $0.025–0.20/s | Budget fillers |

### Image
| Model | Endpoint | Price | Notes |
|---|---|---|---|
| FLUX.2 pro/flex | `fal-ai/flux-2-pro` etc. | ~$0.03–0.05/MP | Current BFL flagship line |
| FLUX.1 schnell | `fal-ai/flux/schnell` | **$0.003/MP** | Sub-second, 1–4 steps. Throwaway iteration |
| FLUX.1 dev | `fal-ai/flux/dev` | $0.025/MP | Workhorse |
| Nano Banana 2 | `fal-ai/nano-banana-2` (+`/edit`) | $0.08/img 1K | Google Gemini 3.1 Flash Image; 14 ref images, char consistency ×5, optional web grounding (+$0.015) |
| Nano Banana Pro | `fal-ai/nano-banana-pro` | $0.15/img | Gemini 3 Pro backbone, reasoning-grade edits |
| Seedream 4.5/5.0 | `fal-ai/bytedance/seedream/...` | $0.035–0.04/img | Cheap, ~3s for 1K img |
| Z-Image Turbo | `fal-ai/z-image/turbo` | $0.005/MP | Speed tier + i2i variants |
| FLUX Kontext | `fal-ai/flux-pro/kontext` | ~$0.04/img | Instruction-based editing |
| GPT Image 2 | `openai/gpt-image-2` | $1/unit | Expensive; skip |
| Utility | `fal-ai/birefnet/v2` (bg removal, ~free), `fal-ai/clarity-upscaler`, `fal-ai/sam-3/image` ($0.005/unit) | | Glue for pipelines |

### Audio
- ElevenLabs full suite on fal: TTS **Eleven v4** (`elevenlabs/tts/eleven-v4`, ~$0.04–0.08/1K chars), v3 with audio tags, **Turbo v2.5 <75ms** for voice agents, text-to-dialogue, **Music** (~$0.60/min), Sound Effects v2, voice changer, dubbing, **Scribe v2 STT** (99 langs, word timestamps).
- MiniMax Speech 2.8 HD/Turbo (`fal-ai/minimax/speech-2.8-hd`), Dia TTS, Gemini 3.1 Flash TTS, MiniMax Music 2.6 (lyrics+style→full song), ACE-Step, Resemble Chatterbox voice conversion, Demucs stem splitting.
- **Sonilo v1.1** (`sonilo/v1.1/video-to-sound-effects`) and **Mirelo SFX v1.5**: video→timed SFX — bolt sound onto generated video for cheap wow.
- Whisper-family transcription (Wizper) for voice-in pipelines.

### 3D + vision
- **Hunyuan3D v3.1** (`fal-ai/hunyuan-3d/v3.1/{pro,rapid}/{text,image}-to-3d`): GLB/OBJ, up to 1.5M polys, PBR textures, 8-view input on Pro; part-splitting + smart-retopology endpoints.
- SAM 2/3/3.1 realtime segmentation/tracking (image + video), Moondream detection, FILM interpolation.

### Realtime surface (the "speed" moat)
- `realtime()` over WebSocket: fast-lcm-diffusion, fast-turbo-diffusion, SDXL Lightning — sub-100ms images, persistent conn keeps runner warm.
- `stream()` over SSE: progressive output (e.g., partial images, TTS chunks).
- WMA/WebRTC: StreamDiffusionV2 webcam restyle example (512² @16fps, ~63ms median frame gap on H100 — but that's your own Serverless deploy, not a Model API endpoint; heavier lift).
- FlashHead/SoulX: realtime streaming portrait video.
- H3 Max Director: continuous video stream you redirect live.

## Pricing mechanics
- Per-output billing: per image/MP, per second of video, per 1K chars, per request. **Never billed: queue wait, cold starts, HTTP 5xx.** 422s may bill if GPU time was spent.
- Prepaid credits. Purchased credits expire 365d; grant credits variable (1wk–1yr). Account locks below a balance threshold.
- Machine-readable pricing API: `GET https://api.fal.ai/v1/models/pricing?endpoint_id=...` — script cost estimates into the agent so it can pick models by budget.

## Latency profile (their whole pitch)
- FLUX schnell / Z-Image Turbo: sub-second–2s.
- Nano Banana 2: seconds; Seedream 1K img ~3s.
- H3 Max: 5s video <3s (fastest frontier-video claim on the platform).
- Kling/Veo-class: realistic plan = 1–5min per clip (queue-dependent); Veo/Seedance slower & pricier.
- ElevenLabs Turbo v2.5: <75ms TTS — genuinely real-time voice loop.
- WebSocket realtime image: <100ms after warm conn. WMA WebRTC video: ~36ms p50 frame latency.
- EU region: fal runs multi-region GPU pools + edge PoPs; Athens fine.

## SDKs & calling patterns
Clients: Python `fal-client`, JS/TS `@fal-ai/client`, plus Swift/Java/Kotlin/Dart. Auth: `FAL_KEY` env (create at fal.ai/dashboard/keys; `API` preset = submit+read+cancel). Raw HTTP: POST `https://queue.fal.run/<endpoint>` with `Authorization: Key $FAL_KEY`; sync host `fal.run`.

Five methods (docs.fal.ai → Model APIs → Inference):
```python
import fal_client
# 1) run — direct HTTP, short jobs only
fal_client.run("fal-ai/flux/schnell", arguments={"prompt": "..."})
# 2) subscribe — queue + block until done (most common)
fal_client.subscribe("fal-ai/kling-video/v3/pro/image-to-video",
    arguments={"prompt": "...", "image_url": "..."},
    on_queue_update=lambda u: print(u))
# 3) submit — queue, returns request_id immediately; poll or webhook
h = fal_client.submit("minimax/h3-max/text-to-video", arguments={...},
    webhook_url="https://.../fal-hook")
h.get()  # or status / result later
# 4) stream — SSE progressive output
for ev in fal_client.stream("fal-ai/flux/dev", arguments={...}): ...
# 5) realtime — WebSocket, sub-100ms, only realtime-flagged endpoints
ws = fal_client.realtime()  # connect("fal-ai/fast-lcm-diffusion")
```
```ts
import { fal } from "@fal-ai/client";
fal.config({ credentials: process.env.FAL_KEY });
const r = await fal.subscribe("fal-ai/nano-banana-2/edit", {
  input: { prompt: "...", image_urls: [...] }, logs: true });
// fal.queue.submit(..., { webhookUrl }) ; fal.stream(...) ; fal.realtime.connect(...)
```
Queue gives retries, status, cancel, webhooks — use it for anything >seconds. **Never ship FAL_KEY client-side; proxy it or use short-lived tokens for realtime.**

## Rate limits / free tier reality
- Concurrency-limited, not rate-limited: **new accounts = 2 in-flight**, auto-scales to 40 with purchase history. Over-limit requests queue, never rejected. Per-endpoint caps possible on hot models.
- **No free API tier.** Signup credit: none. Playground/sandbox freebies exist (e.g., 5 free H3 Max gens/day signed-in on fal.ai/minimax-h3-max) but promo coupons are playground-scoped — reports indicate they can't fund API calls. Grant/startup credits are proper balance and are API-usable.
- Practical floor: self-fund **$10–25** day one — enough for hundreds of images + ~20–40 video clips on mid-tier models; also starts bumping your concurrency.

## Credit acquisition plan (ranked for this weekend)
1. **On-site sponsor allocation — do this first.** fal is a named hackathon partner; deck promises partners get platform-usage numbers back → credits for participants are the mechanism. At kickoff ask the fal mentor table / organizers for the event API key or per-team grant code. Past fal hackathon precedent is strong (below).
2. **fal Builder Grant $25–250** (tally.so/r/D4bBER): Europe/Asia only (Greece ✓), solo/small teams, pre-revenue OK, no call needed (email-reviewed). Requires referral code from an approved fal partner — **the hackathon organizer/sponsor channel very likely qualifies; ask Abed or the fal mentor for a referral code at kickoff.** One app/team/3mo.
3. **Startup Program $1,000–5,000** (fal.ai/startup-program, tally.so/r/yPgMAB): Europe/Asia, needs real traction or institutional VC + intro call → **too slow for a 36h event; apply only if your team already qualifies, else skip.** Bumps at $1k/$2.5k monthly fal spend.
4. **Self-fund $10–25** as guaranteed floor; also unlocks >2 concurrency faster.
5. Fallback-freebies: playground H3 Max 5/day for prototyping prompts, not for the pipeline.

Budget math for the weekend (self-funded $25): ~800 schnell images, or ~300 Nano Banana 2, or ~12 min of H3 Max Turbo video, or ~5 Kling 3.0 Pro 5s clips + TTS. Mix accordingly; video is the budget-eater.

## Hackathon track record (they do this constantly)
- **fal × Sequoia Video Hackathon** (2026): own event, $150k credit prize pool, supported by Google DeepMind/xAI/Kling.
- **{Tech: Europe} London AI Hackathon** (recent): "Best Use of fal.ai" = **$1,000 credits** — winner: Explodify (CAD file → exploded-view product video; pyrender+ffmpeg render → Kling via fal).
- **Adapty × fal Istanbul** (Oct 2026): 30% of judging = "best AI feature with fal"; prizes incl. **$4k/$1.5k/$500 fal credits**.
- CUDA Mode IRL (Accel/PyTorch/NVIDIA): fal among $40k compute-credit sponsors. Emergency GPT Builders: $1k fal credits per podium.
- Pattern: credits for participants + a dedicated "best use of fal" award in the $500–4,000 range. **Engineer for the fal award explicitly — it's likely the most winnable prize category.**

## Demo-impact model picks for "aura points"
Judges reward live, multi-sensory output. Ranked:
1. **H3 Max Director** — realtime steerable video stream. Judge shouts a plot twist, video redirects live. Nothing else on any sponsor table touches this for a stage demo. $0.08/s, 60s min session — a 2-min stage run ≈ $10.
2. **Kling 3.0 Pro image→video w/ native audio** — cinematic motion+sound from a generated still; safest high-quality clip path.
3. **ElevenLabs Turbo v2.5 voice agent** — <75ms TTS makes a real-time spoken loop feel magical; pair with Scribe v2 for full duplex.
4. **Nano Banana 2 / FLUX Kontext edit loop** — agent iteratively edits an image on-screen ("now make it night") — fast enough for live rounds.
5. **Flashtalk** — one photo + TTS clip → talking avatar; uncanny-valley crowd-pleaser.
6. **Sonilo/Mirelo video→SFX** — auto-soundtrack generated video; cheap add-on, big perceived polish.
7. **fast-lcm-diffusion realtime canvas** — type-a-word-see-an-image websocket toy judges can touch (<100ms).
8. **Veo 3.1 w/ audio** — brand-name wow, but slower + $0.40/s; use for the final hero clip, not iteration.
9. **Hunyuan3D** — generate a GLB from the scene, drop into three.js — differentiator vs every image/video demo.

## Integration plan — "the agent produces a film"
Architecture that maximizes aura-per-hour: agent takes a goal → plans a 3-beat story → generates assets → narrates live.
```
Goal → LLM planner (your agent core)
  ├─ Nano Banana 2 (scene stills, consistent char via ref images)   [subscribe]
  ├─ Kling 3.0 i2v on each still (queue.submit × N, webhooks)        [parallel!]
  ├─ ElevenLabs v4 TTS narration + Eleven Music theme                [stream]
  ├─ Sonilo SFX on each clip                                          [submit]
  └─ ffmpeg concat → play; H3 Max Director for the LIVE finale      [realtime]
```
- Use `queue.submit` + `webhook_url` (or `submit` then `result()`) so video clips render in parallel while the agent keeps working — also sidesteps the 2-concurrency cap on fresh accounts (queue absorbs the bursts).
- Seed everything; keep prompts+seeds logged so demos are reproducible.
- Cost guard: model-picker keyed by env var (`DRAFT=schnell/H3 Turbo`, `FINAL=NB2/Kling3Pro`); print est. cost per call from the pricing API.
- Pre-wire fallbacks: Kling→H3 Max, Veo→FLUX 3 Max, NB2→Seedream — swap endpoint ID only.
- Frontend calls YOUR backend; backend holds FAL_KEY. Realtime: short-lived token or proxy WS.

## Gotchas
- `content_policy_violation` = non-retryable 422 — sanitize prompts (no real-people likeness for Flashtalk/Kling in a demo; judges may suggest edgy prompts live).
- Realtime endpoints only on flagged models; standard endpoints 404 on `realtime()`.
- Promo/playground credits ≠ API balance — verify balance on the API path, not just the dashboard.
- Status/cancel URLs use owner+app only (not the full endpoint path) — use the URLs the submit response returns, don't construct.
- Video latency is the demo risk: pre-generate hero clips Saturday night, keep live generation to fast models (schnell, NB2, H3 Max/Director, Turbo TTS).
- fal demand > capacity this summer per CEO — Sunday-evening queue spikes possible; don't leave the final render to 17:30.

## Sources
fal.ai/{pricing,models,startup-program,wma,realtime,h3-max-director,elevenlabs,hunyuan-3d,llms-full.txt}, docs fal.ai (inference, concurrency-limits, real-time, faq), fal.ai/explore/*, TechCrunch/Tech.eu/Bloomberg (Series F, 3–4 Nov 2026), hackathon.polymath42.com (+/llms.txt), luma.com/x1wxi5sn, coderspace.io Adapty×fal, LinkedIn (fal×Sequoia hackathon, Tech:Europe winner post), iterm.today/undercut.deals/aijobsdesk (grant terms), assetlab/vidcost/vibecoding pricing trackers, buildaicurrent (free-tier restrictions).
