---
title: "krikri"
type: source
tags: [hackathon, genai-summit, recon, intel]
aliases: ["krikri"]
created: 2026-11-10
updated: 2026-11-10
status: active
---

# Greek-LLM Play — Krikri-8B deep recon (Gen AI Summit Hackathon, 14–15 Nov 2026)

**Verdict up front:** Hybrid. Ship Krikri-8B-Instruct-v1.5 as-is for the Greek NL backbone (chat, translation, long-doc RAG) AND train LoRA adapters for 1–2 sharp sub-jobs (router + verifier/extractor) via Oumi on rented GPU (~1–2h, <$15). Fine-tuning is the aura; as-is is the safety net. Nobody else will touch Greek-native — it's literally white space (zero Krikri recipes in the Oumi repo as of recon).

---

## 1. Krikri-8B — the flagship

**Lineage:** `ilsp/Llama-Krikri-8B-Base` → `ilsp/Llama-Krikri-8B-Instruct` (Feb 2025, released on International Greek Language Day) → `ilsp/Llama-Krikri-8B-Instruct-v1.5` (chat-focused variant). ILSP / Athena Research Center. Paper: arXiv 2505.13772, EMNLP 2025 Findings (aclanthology 2025.findings-emnlp.268) — cite it, Papageorgiou will clock the reference.

**Base training:** Llama-3.1-8B + continual pretraining on **110B tokens** (upsampled from 91B): 56.7B Greek monolingual (62.3%), 21B English, 5.5B EL↔EN parallel, 7.8B math/code. **Tokenizer extended with Greek tokens** — same trick as Meltemi (whose vocab gave 1.52 vs 6.80 tokens/word vs stock Mistral → ~4.5× fertility drop). Cheaper+faster Greek inference than stock Llama and than any English-first model; this is a real cost-math line, not a vibe.

**Post-training (v1.5):** 2-stage SFT — Stage 1: 856,946 pairs (371k Greek + 485k English); Stage 2: 638,408 pairs (280k Greek + 358k English) — then length-normalized DPO: 92,394 preference triplets + pseudo on-policy sampled triplets. Greek SFT data built by translate+post-edit+regenerate via Gemma-2-27B-IT, scored by Skywork-Reward-Gemma-2-27B. Sources: tulu-3-sft-mixture, smoltalk, magpie-ultra, orca-agentinstruct, ifeval-like, ultrafeedback, HelpSteer2, UltraMedical, ELRC parallel data. **This whole recipe is published in the paper** — crib their data construction method for your adapters.

**Context:** 128k (~80k Greek words) vs Meltemi's 8k. Real RAG over Greek gov/legal docs without chunking gymnastics.

**Capabilities claimed (and bench-backed):** bilingual EL/EN chat, translation to/from FR/DE/IT/PT/ES, legal/financial/medical/scientific domain expertise, JSON/XML structured extraction, tool use / agentic formatting, CoT, polytonic + Ancient Greek support.

### Benchmarks (chat suite, from v1.5 card)
| Model | IFEval EL | IFEval EN | MT-Bench EL | MT-Bench EN |
|---|---|---|---|---|
| Qwen2.5-7B-It | 46.2 | 74.8 | 5.83 | 7.87 |
| EuroLLM-9B-It | 51.3 | 64.5 | 5.98 | 6.27 |
| Aya-Expanse-8B | 50.4 | 62.2 | 7.68 | 6.92 |
| Meltemi-7B-v1.5-It | 32.7 | 41.2 | 6.25 | 5.46 |
| Llama-3.1-8B-It | 45.8 | 75.1 | 6.46 | 7.25 |
| **Krikri-8B-It** | **67.5** | **82.4** | 7.96 | 7.21 |
| **Krikri-8B-It-v1.5** | 61.2 | 78.8 | **8.16** | 7.38 |

**Base vs Meltemi (paper):** +11.6% avg across all Greek benchmarks vs Meltemi-7B-v1.5; +10.8% vs Llama-3.1-8B. ARC-EL 49.4 (vs ~40), Belebele-EL 82.7 (+21.7 over Meltemi), Greek Medical MCQA 53.8 (+20.4 over Llama). Krikri-Instruct also runs Arena-Hard-Auto-EL; ILSP published `ilsp/m-ArenaHard_greek`.

**Instruct vs v1.5 — which to deploy:** v1.5 = best Greek *chat* (MT-Bench-EL 8.16); Instruct = best *instruction-following/format compliance* (IFEval-EL 67.5). For a router/extractor/verifier that must emit strict JSON → start from **Instruct** (IFEval leader). For user-facing Greek dialogue → **v1.5**.

**License:** Llama 3.1 Community License — fine for hackathon + commercial <700M MAU. (Meltemi is Apache-2.0 — cleaner, but strictly weaker.)

**Quantized variants (all official, in the ilsp org):**
- `ilsp/Llama-Krikri-8B-Instruct-GGUF` — 3.1k downloads/mo, runs llama.cpp/Ollama/LM Studio. Third-party quants exist too (3 quants on v1.5; card warns re-uploads may make 3rd-party quants stale → prefer official GGUF).
- `ilsp/Llama-Krikri-8B-Instruct-4bit-mlx` and `ilsp/Llama-Krikri-8B-Instruct-v1.5-4bit-mlx` — **official MLX** → local demo on Apple Silicon, ~5GB footprint. Live Greek inference on a MacBook on stage = aura.
- Full BF16 = ~16GB → single A100/H100 or 2×4090 for serving; no HF Inference Provider support (self-serve vLLM/SGLang/GGUF only).
- Try-it: chat.ilsp.gr (their hosted demo — use it to generate the "before" baseline in your pitch).

**Fine-tunes:** 4 community finetunes on v1.5, 3 on Base — tiny community, yours would be the visible one.

## 2. Meltemi — legacy, cite as lineage

- Meltemi-7B (v1: Mar 2024, 40B tok corpus; v1.5: 54.5B tok, 79.5% Greek) — Mistral-7B base, 8k ctx, **Apache-2.0**, Instruct variants exist. Paper arXiv 2407.20743 (25 citations).
- **Status: superseded.** ILSP's own v1.5 card carries a banner: "CONSIDER USING Krikri 8B Base… +11.6% on Greek tasks." Downloads tell it: Krikri-Instruct ~2.6–2.7k/mo vs Meltemi-It-v1.5 ~177/mo.
- Only reason to touch Meltemi: Apache-2.0 purity or a "two Greek models" benchmark row. Otherwise Krikri.

## 3. ILSP / Athena RC — the people and the prizes

**Haris Papageorgiou** — Research Director AND Vice Director of ILSP (confirmed on ilsp.gr + Athena RC people page + genaisummitseeurope.com/bio-haris-papageorgiou). NTUA EE '92 + PhD '96, 140+ papers, ex-Eurotra, coordinated **clarin:el** (Greece's national language-resource infrastructure — i.e., he controls the Greek corpus vault), co-founded 4 spin-offs. On stage + probably mentoring. **He's the highest-value non-judge in the building for this play.**

**Model authors (HF team members, likely reachable via him):** Dimitris Roussis, Leon Voukoutis, Georgios Paraskevopoulos, Sokratis Sofianopoulos, Prokopis Prokopidis, Vassilis Papavasileiou, Athanasios Katsamanis, Stelios Piperidis, Vassilis Katsouros (ILSP director — spoke at Koukoumidis's Greeks-in-AI workshop Jul 15 → Manos↔ILSP warm channel already exists). Konstantinos Kechagias (GDG Athens/GDE-AI) is an Athena RC researcher — the Google-side bridge.

**PHAROS AI Factory** — Greece's EuroHPC AI Factory (one of first 7 in EU), €30M, consortium: GRNET, Demokritos, NTUA, Athena RC, Growthfund + affiliates (CERTH, AUTH, NKUA, FORTH, UniPi, EKT). Sectors: **Health, Greek Language & Culture, Sustainability**. Compute = DAEDALUS supercomputer. Offers: HPC access, AI-ready datasets, pretrained models, POC support. **CEO = Afroditi Sevasti** (summit bio confirmed) — ex-CTO GRNET + Growthfund, EC research expert since 2014. Pitch Krikri work to her as "the exact use case PHAROS exists to fund" → ask about startup/SME compute access pathway.

**ILSP HF org (huggingface.co/ilsp): 55 models, 52 datasets.** Beyond Krikri/Meltemi:
- `ilsp/CoRM*` (182M–469M active, top-1/top-2) — Contrastive Routing for modular MoE, arXiv 2609.01100. **ILSP literally publishes router research** — name-drop CoRM when pitching a Greek router SLM to Papageorgiou.
- `ilsp/whisper-small-gad-transcribe-stage2-all` — ILSP Greek-tuned Whisper-small (0.2B, bare card). Greek ASR exists → a fully Greek voice-agent stack is feasible (Oumi's hack track IS voice agents).
- `ilsp/justice` — Greek text classifier.
- Fine-tune/eval data (usable): `ifeval_greek`, `mt-bench-greek`, `m-ArenaHard_greek`, `greek-hle`, `greek_culture_bench`, `panellinies-exams-dataset`, `greek-protipa-exams`, `GEAR`, `medical_mcqa_greek`, `mcqa_greek_asep`, `greek-history-trapeza-thematon-qa/co-qa`, `Greek_Myths_POIs_RAG`, + "Dialectal Resources" collection, + ILSP Greek Evaluation Suite collection (ARC/TruthfulQA/HellaSwag/MMLU-EL, Belebele-EL). Plus clarin:el + ELRC for parallel/domain corpora.

## 4. Feasibility — QLoRA/LoRA Krikri in hackathon hours

Krikri = standard Llama-3.1-8B architecture → **every Llama-3.1-8B Oumi recipe ports by changing one line** (`model_name: ilsp/Llama-Krikri-8B-Instruct`). No gated HF access needed (it's on ilsp, not meta-llama).

Local clone at `~/scratch/hackathon-recon/oumi` has exact templates:
- `configs/recipes/llama3_1/sft/8b_lora/train.yaml` — LoRA r=8 α=16 on q,v proj; TRL_SFT; bs 2×grad-accum 32; lr 3e-4 cosine; bf16 sdpa; max_len 8192.
- `configs/recipes/llama3_1/sft/8b_qlora/train.yaml` — q_lora nf4 + bf16 storage, all 6 target modules (q,k,v,o,gate,up,down), grad ckpt on. Use this for single-GPU.
- `…/8b_qlora/gcp_job.yaml` — SkyPilot job: `oumi launch up -c … --cluster krikri-qlora`; swaps to `cloud: runpod`/`lambda` via `resources.cloud` (launcher supports gcp, lambda, runpod, polaris, modal, local — confirmed in `src/oumi/launcher/clients/sky_client.py`).
- Inference recipes: `configs/recipes/llama3_1/inference/8b_infer.yaml` (+rvllm/sglang variants); eval: `…/evaluation/8b_eval.yaml`.

**Time/cost math (8B QLoRA, ~2–5k examples @≤2k tokens):** single H100/A100-80G ≈ 1–2h, RunPod ~$2–4/h → **<$10 all-in**. Single RTX-4090 QLoRA works but ~4–8h (overnight slot). Full LoRA on 4×A100 ≈ <1h. Oumi platform also advertises $50 free credits (per master brief) — check whether it covers training or inference-only.

**Pre-stage (do it NOW, not at the venue):** run the full pipeline on 500 examples beforehand to shake out chat-template/tokenizer quirks; checkpoint adapters to HF hub private repo; venue time = scale run + eval only. HF token + wandb login needed per config headers.

**Data needs for the three sub-jobs (Greek):**
- **Router** (pick tool/data-source/next-step): 1–3k examples. Synthesize: take English routing traces → translate utterances via Krikri itself (it does EL↔EN+6 officially) or frontier teacher → label with schema. 200–400 per class.
- **Verifier** (approve/reject plan or output): 1–2k pass/fail pairs — cheap to auto-generate negatives by mutating good plans.
- **Extractor** (Greek → JSON entities/intents): 2–5k; seed from ilsp datasets (panellinies/asep/medical MCQA → reformulate as extraction), diavgis/OASA/GEMH fixture docs from the master-brief stack.
- Method = ILSP's own recipe: translate + regenerate + score-filter; then held-out 10–15% eval + IFEval-greek sanity pass → the "our 8B beat GPT-5.4 on Greek X" table Koukoumidis/Gianitsos want.

## 5. The play — Greek-native agent NL layer

Nobody else ships this: **Krikri-v1.5 as-is = intent/entity/dialogue layer for Greek users; Oumi-trained LoRA adapter on Krikri-Instruct = deterministic router/verifier emitting schema-locked JSON.** Front it in Greek (bonus: `whisper-small-gad` for a voice demo, Greek TTS via pipecat if time). Lines for stage: "English brain, Greek-native senses" / "the only team whose agent thinks in Greek." Cost line: Greek tokenizer → fewer tokens/word → lower latency+cost vs frontier on Greek text; SLM at $0.49/1M vs frontier pricing.

## 6. Other Greek models worth knowing (for the "we checked alternatives" line)

- **GreekBERT** `nlpaueb/bert-base-greek-uncased-v1` (AUEB NLP Group): 110M encoder, Wikipedia+Europarl+OSCAR — encoder-only, fine for tiny NER/PoS sidecar, not a generator.
- **GreekLegalBERT v1/v2** (`nlpaueb/greek_legal_bert` family + community): domain encoder for legal Greek; finetuned-NER community versions hit F1 0.85 — relevant if vertical = legal/gov docs.
- **EuroLLM-9B, Aya-Expanse-8B**: multilingual EU models — Krikri beats both on every Greek row (table above). Use this in the eval slide.
- **CoRM** (ILSP MoE, EN-only base) — research cite, not usable.
- No other serious Greek generative LLM exists. Krikri IS the state of the art; Meltemi is its deprecated ancestor.

## 7. Who to impress + exact lines

- **Haris Papageorgiou** (speaker/mentor): "We fine-tuned Krikri via Oumi — your model on Manos's stack; there are zero Krikri recipes in the Oumi repo, we'd like to PR the first." Then ask about the 56.7B-token corpus provenance + clarin:el access + whether ILSP wants a community adapter listed on the model card. Mention CoRM if you're doing routing.
- **Manos Koukoumidis** (lead judge, Oumi CEO): SLM-beats-frontier table + "first Krikri Oumi recipe" + cost math. His thesis verbatim.
- **Afroditi Sevasti** (PHAROS CEO, speaker): pitch as PHAROS's poster use-case (Greek language + SME) → ask about Daedalus compute calls for startups.
- **K. Kechagias** (GDG/Athena RC): low-key ally, bridge to both Google and ILSP.
- **Elena Pittarokoili / Tim Gianitsos** (eval judges): your held-out Greek eval + signed before/after numbers land here.

## 8. Risks / gotchas

- License: llama3.1 (not Apache) — no issue for hackathon or normal commercial; note it if asked.
- v1.5 vs Instruct pick matters (chat vs format-strict) — decide per sub-job, or ship both (two adapters, one base).
- Official GGUF/MLX exist for Instruct (both versions); base + your merged adapters → quantize yourself via llama.cpp/MLX post-merge for the on-stage Mac demo.
- Don't train on `mt-bench-greek`/`ifeval_greek` (they're eval sets — contamination; Papageorgiou co-authored a contamination paper, arXiv 2502.01534 — he'd love that catch).
- HF Inference Providers don't serve Krikri — self-host vLLM or GGUF, don't burn time hunting endpoints.
- chat.ilsp.gr = stock model; use it for the live "before vs our fine-tune" A/B.
