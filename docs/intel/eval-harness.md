---
title: "eval harness"
type: source
tags: [hackathon, genai-summit, recon, intel]
aliases: ["eval harness"]
created: 2026-11-10
updated: 2026-11-10
status: active
---

# Eval + Audit Layer — Spec for the 2-file pre-built module
Gen AI Summit Hackathon, Athens, 14–15 Nov 2026 · Design date: Nov 10 2026
Companion to `agent-architecture.md` (this file formalizes its "hash-chained signed action log" + adds the eval layer it assumes).
Boilerplate status: legal. FAQ says "come with tooling and boilerplate ready; build starts 12:00 Saturday." Pre-build all of this; in-window work is wiring + the golden set.

**Thesis:** the eval layer IS the demo, not a slide. Every number on screen is traceable to a signed log line a judge can re-verify. Zero LLM judges anywhere: every grader is a pure deterministic function, and that same function is the GRPO reward. That one sentence feeds all five targets at once.

---

## 0. Judge decoding (what this design is optimized for)

| Judge | Verified identity | What their kill-shot looks like | Our counter |
|---|---|---|---|
| **Koukoumidis** | Oumi CEO. Canonical recipe: baseline → evals/test sets → failure modes → targeted data → train → re-eval. Nov 4 launched FAiE: "turn production failures into evaluation sets and training data," BYOH, GRPO preview. Respects measured real-world numbers (SignalGuru PhD: 20.3% fuel savings on deployed systems) | "What's your baseline? What are your failure modes?" unanswered; a prompt-wrapper | Frozen golden set + measured human baseline BEFORE first agent run; failure-mode taxonomy drives the retrain dataset; retrain path = his own Oumi GRPO/BYOH |
| **Pittarokoili** | OpenAI (Human Data → Consumer Devices). Stanford Ed-Data-Sci 4.0, Onassis scholar. Susan Athey's lab: RCTs on 800k Coursera learners. Causal inference + experimental design | Unverifiable claims, no baseline, unscoped "10× faster," means that hide per-task failures | Paired per-task deltas on a pre-registered frozen task set, Wilson CI on pass rate, sign test for tiny n, claims scoped verbatim to the measured set |
| **Gianitsos** | AMD AI Research (ex-Lamini). GEAK kernel agents: profiler feedback as reward signal. RL mini-course author (GRPO covered). "He'll respect a 36h project that built its own grader" | LLM-judging-itself as the only eval; unmeasured "it works" | Graders are pure functions over the signed trajectory; `reward()` emits the same numbers to `rl_log.jsonl` for GRPO. Live metric tiles during demo |
| **Zindros** | Common Prefix CEO — runs agents that write Lean 4 proofs. "The proof is checked, not trusted." NIPoPoWs; light-client/transparency-log world | "Trust us" claims; metrics without methodology; hidden authority | ed25519-signed hash-chained log + Merkle checkpoints; verifier runs live on stage; public key + `verify` script in the repo; threat-model stated out loud (what the log does NOT prove) |
| **Varvadoukas** | Fireworks FDE lead, ex-Palantir 10y. SFT/RFT + rigorous eval + fast inference is literally his job. Mentor, not judge | A demo that can't ship Monday | $/task + p50 latency tiles; Fireworks LoRA job spec committed; BYOH endpoint stretch |

---

## 1. Deliverable shape

```
eval/                          (pre-built boilerplate repo dir)
├── audit.py                   FILE 1 — signed append-only action log (~180 lines)
├── evals.py                   FILE 2 — deterministic eval harness (~300 lines)
├── golden.json                data: 8–10 pre-registered tasks (authored Sat 12:xx, frozen)
├── baseline.json              data: human timings per task (pre-hack + live re-time)
├── tools.schema.json          data: JSON schema per tool (for schema grader)
└── dashboard.py               OPTIONAL FILE 3 — Streamlit read-only view (~80 lines)
```

Integration contract: **the agent touches exactly one function** — `@logged_tool(...)` wraps each tool implementation, and one `log.log(kind="llm_call", ...)` in the model client. ~10 lines of wiring in agent code, whichever stack wins on Saturday (the boxd coordinator from `agent-architecture.md`).

Everything else — graders, baselines, dashboard, reward, verification — reads the two artifacts (`audit.jsonl` + payload sidecars) and never touches agent internals. **Evals score observable signed behavior, not the agent's memory.** If we swap agent frameworks at hour 6, the eval layer doesn't change.

---

## 2. Framework decision — picked: custom pytest-style harness

**Decision: custom pytest-style harness over the signed log. Deterministic graders only.**

| Option | Verdict | Why |
|---|---|---|
| **Custom pytest-style** | ✅ **PICK** | (a) Agent-agnostic: scores the signed transcript, so the boxd/coordinator architecture is untouched. (b) Zero LLM-judge path is natural (frameworks default the other way). (c) Graders are literally reusable as GRPO reward functions — Gianitsos + Koukoumidis in one move. (d) `pytest` IS the runner; we reinvent nothing. (e) Rejected-framework knowledge becomes a panel answer: "we evaluated Inspect, here's why we score the signed trace instead." |
| inspect-ai | Runner-up | The real agent-eval framework (UK AISI; Task/Solver/Scorer; transcripts; Inspect View; scanners for reward-hacking). Costs: our boxd-fork agent would have to become an Inspect solver or we convert our log to `.eval` format — hours of adapter work in a 36h window. Its free transcripts are strictly weaker than our *signed* transcript. Stretch: post-hoc `.eval` export via their log-writer API for Inspect View. |
| DeepEval | Rejected | Headline metrics are LLM-judged (G-Eval, faithfulness, task-completion) — exactly the "vibes" Gianitsos kills on sight. Its deterministic tool-correctness is shallow (name/arg matching, no ordering/policy/grounding). pytest entry (`deepeval test run`) is nice but not worth the judge-attraction liability. |
| promptfoo | Rejected | Prompt/response assertion layer (contains/regex/similarity/rubric), not trajectory-native; YAML-centric; treats the agent as a text function. Wrong abstraction level for tool-call correctness + signed traces. |
| Oumi evals | Rejected *for harness*, kept *for retrain* | Oumi OSS eval wraps lm-eval-harness (model benchmarks, not agent trajectories). BUT Oumi is the retrain destination: VERL_GRPO is GA in OSS (bypasses platform private preview), multi-reward summation landed Nov 9 (#2735, Androna's commit), BYOH = Oumi evals *against our harness*. Correct placement of Oumi is §5, not here. |

The methodological point to say out loud (Koukoumidis's own recipe): **framework choice matters less than ordering.** Baseline first, golden set frozen, failure modes named, then train, then re-eval. A team that leads with "we measured the baseline before writing the agent" beats a team that name-drops a framework.

---

## 3. `audit.py` — the signed action log (~180 lines)

Deps: `cryptography` (ed25519) only. Everything else stdlib.

### 3.1 Entry schema (`audit.jsonl`, one JSON object per line)

```json
{"v":1,"seq":41,"run_id":"r_7f3a","task_id":"t04","ts":"2026-11-14T15:23:11.492Z",
 "kind":"tool_call","tool":"treg.call","args_hash":"sha256:9f2c…","result_hash":"sha256:1ab7…",
 "status":"ok","duration_ms":812,"tokens_in":0,"tokens_out":0,"cost_usd":0.0034,
 "prev_hash":"sha256:6e11…","entry_hash":"sha256:c4d0…","sig":"ed25519:8f3a…"}
```

- `kind`: `tool_call` | `tool_result` | `llm_call` | `decision` | `human_gate` | `checkpoint`.
- `args_hash`/`result_hash` bind to **payload sidecars** `payloads/<seq>.json` (full I/O). Keeps the chain small while making any payload tamper detectable: graders re-hash sidecars and compare.
- Chain: `entry_hash = sha256( prev_hash_bytes ‖ canonical_json(entry_minus_{entry_hash,sig}) )`; `sig = ed25519_sign(entry_hash)`. Genesis `prev_hash = sha256("eval-audit-genesis-v1")`.
- Canonical serialization: `json.dumps(obj, sort_keys=True, separators=(",",":")).encode()` — one definition, reused by verifier.
- **Checkpoint every N=25 entries**: Merkle root over the segment's `entry_hash`es, appended as a `kind:"checkpoint"` entry with its own sig. Mini Certificate-Transparency (RFC 6962) lineage — Zindros's exact mental model. Checkpoint root displayed on dashboard; optional external anchor (tweet/gist/QR on slide).

### 3.2 API

```python
class AuditLog:
    def __init__(self, path: str, key_path: str, run_id: str): ...
        # loads or creates ed25519 keypair; if file exists, scans to resume seq + tip
    def log(self, kind, tool=None, args=None, result=None, status="ok",
            duration_ms=None, tokens_in=0, tokens_out=0, cost_usd=0.0,
            task_id=None, meta=None) -> dict      # canonicalize → hash → sign → append → fsync
    def checkpoint(self) -> dict                  # signed merkle root entry
    @property
    def tip(self) -> str
    def public_key_b64(self) -> str               # printed on slide + committed to repo

def logged_tool(log: AuditLog, name=None, cost_fn=None):
    # decorator factory: wraps fn → logs tool_call(args_hash) + tool_result(result_hash),
    # duration_ms, status (error re-raised after logging), optional per-call cost

def verify(path, pubkey_b64=None, payloads_dir=None) -> VerifyReport
    # {ok, entries, first_bad_seq, reason, tip, checkpoints_verified}
    # checks: seq contiguity · prev_hash continuity · every sig · checkpoint roots
    #         · (if payloads_dir) sidecar hashes match args_hash/result_hash

def merkle_root(hex_hashes: list[str]) -> str
```

CLI: `python audit.py verify audit.jsonl` → prints `OK n=341 tip=c4d0… checkpoints=14` or `FAIL seq=88 prev_hash mismatch`. Exit code propagates (CI-able, demo-able).

### 3.3 The stage beats (Zindros package)

1. Dashboard re-runs `verify()` every refresh — green "chain verified, n=…" that ticks up live.
2. **Tamper demo (20s):** flip one byte mid-file (or swap two lines) in a *copy*, run verify → red, exact seq named. Then re-run on the real log → green. "Checked, not trusted" performed.
3. Public verification: pubkey + `audit.jsonl` + `audit.py` in the repo; QR on the final slide → `python audit.py verify`. He can literally run it.
4. **Adversarial honesty (say it before he asks):** "The log proves the agent made these calls and got these results, and that nothing was dropped or rewritten. It does not prove the work is correct — that's what the task verifiers against the live environment prove. A signed lie is still a lie; we sign the trace AND check the outcome." That bound is the difference between crypto-buzzword garnish and a trust argument.

---

## 4. `evals.py` — the eval harness (~300 lines)

Deps: `pydantic` (tool arg schemas), `pytest` (runner), `scipy` optional (Wilcoxon). No LLM imports. If any future grader needs a model, it goes in a separate file labeled advisory-only and is excluded from `reward()`.

### 4.1 Layer 0 — Baseline (the before/after)

- `golden.json`: 8–10 tasks authored Sat 12:xx once the fixture locks; **commit-frozen before the first agent run** (hash goes on the slide — pre-registration a judge can check).
- Human baseline: a teammate performs each task manually, screen-recorded, wall-clock timed → `baseline.json {task_id: human_s}`. n=1 disclosed as n=1; **one task re-timed live during the demo** so the baseline isn't just asserted (Pittarokoili + Mazarakis both eat this).
- Metrics: per-task paired delta `human_s vs agent_s` + `agent_$`; **median** speedup (robust, not mean-of-ratios); pass rate n/N with **Wilson 95% CI**; sign test on paired deltas (honest at n=10), Wilcoxon if scipy present.
- Claim discipline, verbatim template: *"median 6.4× faster on our frozen 10-task golden set (n=1 human rep per task, measured today; 9/10 pass, Wilson CI 0.59–0.98)."* Never a naked "10×."

### 4.2 Layer 1 — Task evals (did the work complete?)

Verifier registry — deterministic predicates against the real environment, not the agent's story:

```python
VERIFIERS = {
  "file_json":      v_file_json,      # path exists + jsonschema validates
  "file_regex":     v_file_regex,     # artifact contains/forbids pattern
  "http_state":     v_http_state,     # GET url → jsonpath == expected (system actually changed)
  "db_row":         v_db_row,         # sqlite query returns expected row
  "artifact_match": v_artifact,       # normalized compare vs golden artifact, numeric tol
}
# each → Check{passed: bool, detail: str}
```

Binary pass/fail per task. `http_state`/`db_row` are the strong ones: they prove state changed in the world, which no transcript inspection can fake.

### 4.3 Layer 2 — Trajectory evals (tool-call correctness)

Pure functions over the run's log entries + verified payload sidecars. Six graders:

| Grader | What it checks | Violation examples |
|---|---|---|
| `schema_validity` | Every `tool_call` args validate against `tools.schema.json` | missing required arg, wrong type, hallucinated param |
| `policy` | Tool whitelist, banned arg regexes, host/scope limits | called a tool outside task scope; `DELETE` in args |
| `ordering` | `must_precede` invariants from golden spec | `issue_refund` before `get_invoice`; write before read |
| `efficiency` | Call count vs `max_calls`, retry rate, redundant calls (dup `args_hash` in window) | same call 3× in a row; 40 calls where 6 suffice |
| `recovery` | `error` → success retry **with changed args** counts positive; identical-arg retry = violation | blind retry loops vs adaptive recovery |
| `grounding` | IDs/amounts/values cited in final artifact must appear in some `result_hash` payload | agent asserts an invoice total never returned by any tool — deterministic anti-hallucination |

`grounding` is the sleeper pick: it operationalizes Koukoumidis's HallOumi thesis ("verifiability > accuracy") with zero LLM — entity-level check that outputs are backed by observed tool results.

### 4.4 Layer 3 — Outcome evals (business metric + cost/latency)

- Per-task business KPI via golden `outcome.fn` (e.g., `invoice_amount_matches(tol=0.01)`, `ticket_resolved_and_categorized`, `fields_complete_ratio`).
- Accounting from the log itself: `cost_usd` summed → **$/task**, `duration_ms` → **p50/p90 per task**, tokens → model cost split (SLM-local vs frontier-backstop vs treg spend — three columns, Varvadoukas wants the receipt ledger anyway for treg's `X-Treg-Cost-Micro`).
- `compare_baseline()` emits the markdown table that goes on the dashboard AND the final slide — same numbers, one source.

### 4.5 Reward = the graders (the Gianitsos lock)

```python
def reward(entries, ctx) -> tuple[float, dict]:
    # r = clip( 0.50*task_pass + 0.15*schema + 0.10*policy
    #         + 0.10*efficiency + 0.10*grounding + 0.05*recovery
    #         - 1.0*hard_violation , 0, 1 )
    # returns (scalar, per-component breakdown) — breakdown columns =
    # Oumi VERL_GRPO multi-reward fields (commit #2735): correctness/format/tool-validity
```

One sentence for the room: *"Every scorer on that dashboard is a deterministic function, and that function is our reward model."*

### 4.6 Runner + emitted artifacts

- `pytest evals.py --replay audit.jsonl` → parametrized `test_task[t01]…[t10]` re-grades any recorded run without re-running the agent. **Demo-safe:** grade live runs as they complete AND re-grade a known-good log if live is shaky.
- Emits `eval_results.jsonl` (one row/task/run: pass, per-grader scores, cost, latency, violations, log-tip hash) and `rl_log.jsonl` (one row/run: `{task_id, traj_hash_span, reward, breakdown}` — the training dataset accumulating from minute one).
- Failure-mode taxonomy auto-bucketed from violations (top-3 failure modes is a Koukoumidis slide, and it's also the retrain manifest).

---

## 5. The self-improving loop — feasible tiers

**Tier-0 (real from minute one, zero risk):** `rl_log.jsonl` accumulates `{trajectory, reward, breakdown}` for every run, failures included. The dataset exists whether or not retraining ever fires. This alone is "every mistake becomes training data" — FAiE's sales loop, manually.

**Tier-1 (realistic in-window, Sunday AM):** failure modes → corrected trajectories → **Fireworks hosted LoRA SFT** on Qwen3-4B/Qwen2.5-7B (`firectl` job, minutes to submit; or Oumi platform SFT $0.49/1M tokens). Deploy, re-run `--replay` + one live task, show before/after on the SAME frozen golden set. This is the "we actually closed the loop" artifact — commit the config even if the run finishes during judging.

**Tier-2 (stretch, commit the spec either way):** GRPO via Oumi OSS `VERL_GRPO` — K=8 rollouts/task on the golden set, reward = `reward()` multi-component breakdown registered via `@register(name, RegistryType.REWARD_FUNCTION)` × 3 (correctness/format/tool-validity = the Nov-9 multi-reward feature, Androna's #2735). LoRA r=16, ~200–400 steps, 1×A100/H100 ≈ 1–2h ≈ $3–8. **Pre-run option:** since the harness is legal boilerplate, fire one toy-domain GRPO run *before* Saturday so the loop is proven end-to-end; then the in-window run only needs in-window data. Disclose both timestamps — disclosed pre-training = credible plumbing, hidden = disqualifying.

**Honest numbers:** expect ~40–80 usable failure-pairs and ~200–240 logged trajectories over the event; realistic uplift +5–15 pts on the dominant failure mode. Say "directional, measured on n=10" — never promise the delta.

**BYOH stretch (one line):** expose the coordinator as a BYOH endpoint (`POST /submit`, `GET /get_status`, `GET /collect_output`, `POST /cancel`) → Oumi's own evals + simulated users run against our harness. "We brought our own harness" is Koukoumidis's freshest sentence.

---

## 6. Live dashboard — the demo surface

Streamlit (`dashboard.py`, ~80 lines, fragment rerun every 2s) reading `audit.jsonl` + `eval_results.jsonl` + `baseline.json` + `golden.json`. Read-only — it can never lie differently than the log.

- **Top tiles:** tasks passed `n/N` (+Wilson CI) · median speedup vs human baseline · p50 agent latency · total cost `$` (split: SLM / frontier-backstop / treg) · tool calls · retry rate.
- **Per-task table** (the Pittarokoili table — paired, nothing hidden): `task | human_s | agent_s | speedup | pass✓/✗ | $ | calls`.
- **Trajectory health:** violation counts by grader + scrolling violation list (first_bad_seq links to log line).
- **Audit panel:** entries `n` · tip hash (truncated) · last checkpoint root · **VERIFY: OK** badge re-computed live; button "verify now" re-runs full chain check.
- **Live action feed:** tail of the log — each agent action appears as a signed line as it happens.
- Kill-shot moment available at all times: the tamper demo (§3.3).

All tiles derived only from the JSONL artifacts — the dashboard is a view, not a second source of truth.

---

## 7. What NOT to do

1. **No LLM-as-judge anywhere.** Not for quality, not "just for the demo," not as a secondary score. If a property can't be checked deterministically, it's not in `reward()` — rubric it or drop it. Gianitsos will ask "what scored this?" and the only survivable answer is a function.
2. **No unscoped claims.** Every number carries set-size, CI, and measurement context. "Median 6.4× on 10 frozen tasks," not "10× faster."
3. **No averages that hide failures.** Per-task table always visible; a 90% pass rate that hides one catastrophic task is worse than an honest 80% with named failure modes.
4. **No cherry-picked or moving golden set.** Freeze before run 1, commit the hash, show the diff discipline. A mutable eval is an LLM-judge by other means.
5. **Never truncate/reset the log between runs.** The audit panel's `n` must only grow on stage.
6. **No claiming self-improvement if the retrain didn't run.** "Closed-loop ready, job spec committed, dataset accumulating" is honest; "the agent improves itself" without a retrain artifact is the kill-shot sentence.
7. **No unverifiable ROI.** $/task and minutes/task from the ledger, not a consultant's spreadsheet.
8. **No "the model decided" hand-waving on failures.** Failure-mode taxonomy with counts from `eval_results.jsonl`.
9. **Don't bury the human gate.** Containment metric on screen (writes queued vs executed) — it's an eval number too.

---

## 8. Wiring into the 36h plan (amends `agent-architecture.md` build order)

- **Pre-Sat (boilerplate):** `audit.py` + `evals.py` complete and unit-tested (tamper test included); `dashboard.py` stub; Oumi GRPO config + Fireworks job spec committed; optional toy GRPO pre-run; boxd card, treg $20, Firecrawl key, Oumi $50 (existing list stands).
- **Sat 12–15:** fixture locks → author `golden.json` (10 tasks) + freeze-commit → human baseline timing (2 people, ~1h) → `@logged_tool` wiring lands WITH first tools (not Sunday — evals depend on the log; move signer earlier than the arch doc's Sun block).
- **Sat 15–02:** real tools logging → dashboard live → first `--replay` grading on partial trajectories → failure taxonomy v1.
- **Sun 09–15:** full golden-set runs → baseline table → Tier-1 retrain job fired → checkpoint cadence on → tamper demo rehearsed.
- **Sun 15–18:** 3× rehearsal incl. verify-live beat → backup video + pre-graded `--replay` fallback → submit.

Effort: `audit.py` ~3h pre-hack · `evals.py` ~5h pre-hack · dashboard ~1h · golden set ~1.5h in-window · baseline ~1h.

---

## 9. Soundbites (memorize, one per judge)

- **Koukoumidis:** "Baseline measured before the first run. Our failure modes became our dataset; the retrain path is your GRPO trainer — we brought our own harness."
- **Pittarokoili:** "Paired per-task deltas on a frozen pre-registered set, Wilson CIs, every claim scoped to what we measured."
- **Gianitsos:** "Zero LLM judges — every scorer is a pure function, and that function is the GRPO reward. The eval harness is the reward model."
- **Zindros:** "Every action ed25519-signed and hash-chained with Merkle checkpoints; the dashboard re-verifies live; flip one byte and it goes red — checked, not trusted."
- **Varvadoukas:** "$/task and p50 latency on the wall, Fireworks LoRA spec committed — this ships Monday."
- **Mazarakis (bonus):** "Watch the agent handle being broke — it narrates the 402 and recovers. That failure recovery is measured, not staged."

---

## 10. Verification checklist before "done"

- [ ] `python audit.py verify` green on a real run; byte-flip copy → red at correct seq
- [ ] `pytest evals.py --replay` grades all 10 tasks; pass count matches manual count
- [ ] Every dashboard tile traceable to a JSONL line (spot-check 3)
- [ ] `reward()` output == sum of grader components (no hidden term)
- [ ] `rl_log.jsonl` + Fireworks/Oumi config committed; job ID or "spec-only" label honest
- [ ] Baseline table on slide = same numbers as dashboard (one source)
- [ ] Pubkey + verify command on final slide; repo public
