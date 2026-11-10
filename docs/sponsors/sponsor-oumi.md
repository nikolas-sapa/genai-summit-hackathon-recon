---
title: "sponsor oumi"
type: source
tags: [hackathon, genai-summit, recon, sponsors]
aliases: ["sponsor oumi"]
created: 2026-11-10
updated: 2026-11-10
status: active
---

# Sponsor Teardown: Oumi (oumi.ai)

**Recon date:** 2026-11-10 · **Event:** Gen AI Summit Hackathon, Athens, 14–15 Nov 2026
**Why it matters:** CEO Manos Koukoumidis co-organizes the summit (listed on genaisummitseeurope.com organizing team) and Oumi is a hackathon partner. His Nov 4 launch keynote closes on "Build and own specialized intelligence" — that is the exact frame to pitch back at him.

---

## 1. What Oumi actually is (two products, don't confuse them)

### A. Oumi OSS — `github.com/oumi-ai/oumi`
- 9.4k★, 798 forks, Apache 2.0, very active (pushed Nov 9, 2026). Formerly "reliable-ai" (old repo still visible).
- One CLI/config system for the whole model lifecycle:
  - `oumi train` — SFT, LoRA, QLoRA, DPO (TRL), GRPO (verl), FSDP/DeepSpeed, pretraining
  - `oumi evaluate` — lm-eval-harness benchmarks + custom evals + `oumi judge` (LLM-as-judge, built-in judge rules)
  - `oumi infer` — engines: NATIVE (HF), VLLM, REMOTE_VLLM, SGLang, LLAMACPP, plus OpenAI/Anthropic/Gemini/Vertex/Together/Fireworks/Parasail/OpenRouter/DeepSeek (LiteLLM-backed)
  - `oumi launch` — SkyPilot jobs → AWS, GCP, Azure, Lambda, RunPod, Nebius, k8s, Slurm (`oumi[aws|gcp|lambda|runpod|nebius|kubernetes]` extras)
  - `oumi synth` — synthetic data generation (LLM teachers); `oumi tune` (HP sweeps); `oumi quantize` (GGUF); `oumi analyze` (dataset stats); `oumi deploy`
- YAML-driven; built-in configs referenced via `oumi://configs/...` URIs.
- **MCP server** (`pip install "oumi[mcp]"`, experimental): lets Claude Code/Cursor find recipes, launch/monitor train/eval jobs, poll status — all from chat. Real time-saver at a hackathon.
- Supported model families (recipes under `configs/recipes/`): Llama 3.1/3.2/3.3/4, Qwen2.5/3/3.5/3.6/coder/next, Phi3/4, Gemma2/3/4, gpt-oss, DeepSeek-R1 distills, SmolLM (135M), Olmo3, GLM4, Falcon-H1, QwQ + VLM variants (Qwen-VL, SmolVLM, LLaVA). Claim: 10M → 405B params.

### B. Oumi Platform — `platform.oumi.ai` (hosted, docs.oumi.ai, Mintlify)
- **FAiE (Frontier AI Engineer)** — launched **Nov 4, 2026** (Business Wire). A chat agent inside the platform: describe a goal → it creates datasets/evaluators/evals, trains, deploys, monitors, explains failures. Approval gates on anything billable; `Auto-approve` toggle. `@`-mention resources. Can't upload files or touch billing/API keys.
- **BYOH (Bring Your Own Harness)** — register your agent's public HTTPS endpoint; Oumi evals/synthesis call YOUR loop. Protocol v1 = 4 routes: `POST /submit`, `GET /get_status`, `GET /collect_output`, `POST /cancel`. OpenAI-format messages incl. tool_calls. Each submit carries `model_connection` = `{base_url: https://inference.oumi.ai/v1, model, scoped api_key}` — your harness calls the model-under-test through Oumi; prompts/tools/memory stay in your runtime. 30s response limit, 15min turn limit, sessions per dataset row, `input_required` pauses for user questions (Oumi simulates the user).
- **Agent eval/synthesis**: define tools (name/desc/JSON schema), tool implementations (your HTTPS/MCP endpoint | ask-user | fixed answer | LLM-simulated), simulated users w/ personas → generate multi-turn tool-use conversations in bulk → SFT a small model on the best traces. DPO available; GRPO in private preview.
- **Pricing:** Free $0 with **up to $50 credits / 3 months** ($50 corp email, $25 personal, no card). SFT ≤16B = **$0.49 per 1M training tokens** (a 500k-token set × 3 epochs ≈ $0.75). Eval judgments 1k/$1, synthesis 1k rows/$1. Weight download: 1/mo on Pro ($25). FAiE agent tokens: $6.25/$31.25 per 1M in/out.
- Hackathon-specific credits for Athens: **none found publicly.** Ask Oumi mentors at kickoff; their last hackathon starter required fine-tuning with Oumi + starring the repo — expect similar.

---

## 2. `hack-with-oumi` starter kit — what it actually scaffolds

Repo: `github.com/oumi-ai/hack-with-oumi` (11★, built for Nebius.Build SF Mar 15 2026 + Eclipse Apr 4–5 2026 — **not Athens-specific yet, but it's their playbook**).

**Theme there:** "SLMs for Voice Agents" — SLM = <10B params. Requirement: fine-tune with Oumi + star the repo. Judged on creativity, real-world impact, technical quality.

**Template** (`/template`): a Pipecat-based voice agent, Mac-first:
- `server/server.py` — FastAPI + Pipecat pipeline: SmallWebRTC transport → Silero VAD → **mlx-whisper STT** → SLM via OpenAI-compatible endpoint → **Kokoro-82M-bf16 MLX TTS** → audio back.
- `server/agent.py` — `RewriteTextFrames` FrameProcessor: intercepts LLM digit output (intent ID), maps to label, injects `TTSSpeakFrame`. The "agent" is literally a classifier SLM + a frame rewriter.
- `client/` — Next.js + voice-ui-kit (RTVI).
- SLM served by **vLLM-MLX** (`vllm-mlx serve <hf-model> --port 1234`) → OpenAI API at `127.0.0.1:1234/v1`.
- Model: `stefanwebb/banking77-intent-classifier-mlx` — fine-tuned to output a single integer ID over Banking77's 77 banking intents; huge system prompt lists all IDs + disambiguation examples (in `platform/banking77-classifier/` of the main repo: preprocessing spec, in-context examples, results).
- Requirements pin a stefanwebb pipecat fork + torch 2.10, transformers 5.3, mlx stack. Setup is fiddly (phonemizer-fork dance); budget 1–1.5h or skip Pipecat entirely for text agents.

**Their explicit submodel menu** (README "Agent Submodels" — this is what they'll reward):
guardrails/LLM-judges, query rewriting, execution routing, retrieval routing, model routing, planner, **verifier**, executors, memory management. They argue "multiple specialized SLMs working together" beats one big model on latency + cost.

## 3. The Banking77 result — their flagship narrative

`oumi/platform/banking77-classifier/banking77-results.md`:

| Model | Banking77 acc | p50 lat | $/1k |
|---|---|---|---|
| **Qwen3.5-0.8B fine-tuned w/ Oumi** | **88.8%** | ~80ms | ~$0.01 |
| GPT-5.4 (5-shot) | 82.5% | ~1.2s | ~$1.08 |
| Opus 4.6 (5-shot) | 81.3% | ~2.0s | ~$2.13 |

A sub-1B model trained with Oumi beats frontier APIs on a narrow classification task. **This table is the pitch format to copy** — fine-tuned SLM vs named frontier baselines, accuracy + latency + cost.

## 4. HallOumi — their verifier model

- `oumi-ai/HallOumi-8B` (generative: per-sentence verdicts, subclaim decomposition, citations) + `HallOumi-8B-classifier` (claim-level + confidence, cheaper). Config: `configs/projects/halloumi/8b_train.yaml`.
- 77.2% macro-F1 on their groundedness benchmark — beats Sonnet 3.5 (69.6), o1-preview (65.9), DeepSeek-R1 (61.6), Llama-405B (58.8). Trained entirely with Oumi.
- Serve via SGLang or their `halloumi-demo` (Next.js UI repo). **License CC BY-NC 4.0** — fine for hackathon, flag if pitching "product."
- Direct relevance: a claim-verification/guardrail SLM is the highest-status component in their taxonomy.

## 5. `weights-lab` — the wildcard

New repo (7★, v0.5 experimental): an **agent skill for weight-space programming** — Claude Code/Codex/Cursor plugin. Your coding agent loads a model once, applies reversible Python weight edits (surgical edits, ablations, clamps), measures behavioral effect, exports. Tested on CPU, **Apple MPS**, H200, 72B across 8×H100, SkyPilot/Slurm. Inspired by the weight-space-programming paper. Almost nobody will touch this at the hackathon — a live weight-edit demo ("we didn't just fine-tune, we rewired a neuron") is a strong aura-points play. Risk: experimental, snippets run as trusted Python.

## 6. Mac vs cloud — what actually trains where

- **Apple Silicon only** (PyTorch dropped Intel Macs). `uv pip install oumi` works natively on M-series.
- **QLoRA = CUDA-only** (bitsandbytes 4-bit). On Mac: **full FT for ≤1B, LoRA for ≤3B** on MPS (`device_map: auto`, `torch_dtype bfloat16`→`float32` if flaky). Verified path in their own template: train then convert to MLX (vllm-mlx / mlx-lm) or llama.cpp GGUF (`oumi quantize`) for serving.
- Realistic 36h Mac budget: SmolLM-135M/Qwen3.5-0.8B full FT on a few k rows = minutes-to-tens-of-minutes on M-series; Llama-3.2-3B LoRA = hours, only if you start early.
- Cloud path: `oumi launch up -c <gcp_job.yaml>` (SkyPilot) on GCP/Lambda/RunPod — needs cloud account + quota set up **before** the event. Or Oumi Platform SFT ($0.49/1M tokens — cheapest, zero infra).
- **Recommended:** fine-tune on Oumi Platform or local MPS, serve locally via llama.cpp/vllm-mlx. No cloud dependency on hackathon wifi.

## 7. Docs, community, gotchas

- Two doc sites: OSS sphinx docs (`oumi.ai/docs/en/latest`) — good recipe index, per-model train/eval/infer jobs incl. `gcp_job.yaml`; Platform docs (`docs.oumi.ai`, Mintlify, has `llms.txt`). Quality: solid, current.
- Discord: `discord.com/invite/oumi` — active; Manos + eng team (oelachqar, nikg4, wizeng23, kaisopos…) reachable there. Contributing is community-first; a tiny docs/example PR before the event = name recognition.
- Gotchas: `hack-with-oumi` requirements are pinned to a personal pipecat fork; Banking77 recipe needs HF gated-model acceptance for Llama (use Qwen3.5 to skip the gate); HallOumi is non-commercial; BYOH eval can't synthesize with custom Oumi models (eval only); FAiE can't import files (you upload via UI).

---

## 8. Build plan — Oumi inside an agent harness in <4h

**Architecture (their thesis, mirrored back):** one orchestrator (frontier API or local SLM) + **two specialized SLMs we trained**: a **router** (intent→tool/agent dispatch) and a **verifier/guardrail** (approve/flag each step's output before it commits). Demo-able end-to-end latency story + the eval table.

**T-4h → T-3h — environment (pre-do this before the event if possible):**
```bash
uv venv .oumi && source .oumi/bin/activate
uv pip install "oumi[mcp]" vllm-mlx        # or llama.cpp
# platform.oumi.ai signup w/ corp email → $50 credits
# oumi://configs/recipes ready: llama3_2/sft/1b_full, qwen3 recipes, smollm/135m
```

**T-3h → T-1.5h — data + train (parallel with building the harness):**
1. Pick YOUR domain (the hackathon challenge), not banking. Write 300–800 JSONL rows in Oumi chat format `{messages: [system,user,assistant]}` — router: `query → tool_id`; verifier: `context+step_output → VALID/INVALID + reason_id`. Generate more via `oumi synth` or platform FAiE ("generate 500 tickets labeled by intent").
2. `oumi train -c your_router.yaml` — base: **Qwen3.5-0.8B or Llama-3.2-1B full FT** on MPS, or `use_peft` LoRA on 3B. On platform: same YAML, SFT job ≈ $0.50.
3. `oumi evaluate` on a held-out 20% split; also run the same prompts through GPT-5.x/Claude via `oumi infer --engine OPENAI` for the baseline column.

**T-1.5h → T-0.5h — wire into the harness:**
4. Serve: `vllm-mlx serve <your-ft-model>` (Mac) or `llama-server` on a quantized GGUF → OpenAI-compatible `localhost:PORT/v1`.
5. In your agent loop: point `router_call()` and `verify_step()` at that endpoint (OpenAI client, `temperature=0`, `max_tokens` tiny → <100ms/hop). Frontier model only sees pre-routed, post-verified traffic.
6. Optional aura: register your agent as a **BYOH harness** (implement the 4 routes; ngrok/cloudflared for public HTTPS) and run one Oumi eval through it — you demo the exact "production failures → eval set → training data" loop FAiE sells.

**T-0.5h → T-0 — proof artifacts:**
7. The Banking77-style table: your SLM vs GPT/Claude on YOUR task (accuracy, p50 latency, $/1k). Screenshot the Oumi eval run.
8. Stretch: `weights-lab` live edit ("watch us flip one weight and fix the misroute") — 10min demo, high risk/high aura.

**Fallbacks:** Mac too slow → Platform SFT or `oumi launch` on RunPod/Lambda. Pipecat template too heavy → text-only agent, keep the router+verifier SLM pair (the voice pipeline is optional garnish, not the point).

## 9. What to say to Manos

- "We own the intelligence, not the wrapper" — every decision node (router, verifier) is a model we trained with `oumi train`; weights on our laptop; frontier API is a fallback, not a dependency.
- "Multiple specialized SLMs beat one big model" — quote their own starter thesis; show latency table.
- "We ran your loop": eval → failure modes → synth data → retrain — ideally once live, on stage-ready numbers. Name-drop BYOH if you implement it.
- Star the repo. Say you starred the repo. Their last hackathon literally required it.

**Bottom line:** most teams will bolt Oumi on as a checkbox. The winning play is architectural: an agent whose control plane is two small models you trained, evaluated, and own — the exact product thesis Oumi sells to enterprises.
