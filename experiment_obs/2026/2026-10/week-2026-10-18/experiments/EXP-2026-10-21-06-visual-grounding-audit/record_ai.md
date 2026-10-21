# EXP-2026-10-21-06-visual-grounding-audit — Does R1 use image evidence or language momentum?

Author: AI agent (Codex). Human companion: [record.md](record.md).

## Request and design

User asked whether visual-evidence and grounding text produced by Qwen3-VL R1 reflects its paired images or is mainly autoregressive continuation from prior text. The study uses the stopped, saved Stage-1 R1 subset. It does not change training, data, or the frozen benchmark.

Two complementary probes are planned:

1. **Free-decoding visual interventions.** Hold prompt and decoding fixed while using original paired images, swapped candidate images, close-crop-only evidence, context-only evidence, and neutral visual input. Measure answer flips and save paired rationales for inspection.
2. **Fixed-rationale answer probe.** Hold the original generated CoT prefix fixed through `<answer>` while changing images, then compare class-token likelihoods. This distinguishes direct image influence on the final answer token from influence already encoded into the earlier generated text.

The audit is stratified by post-hoc gold class from saved Stage-1 predictions, uses a deterministic seed, and keeps all raw generations and per-condition scores. It can demonstrate sensitivity to visual input; it cannot prove a human-style causal explanation.

## Setup and execution

Status: **preparing**. Source predictions: `/sfs/vlm_qwen/experiments/2026-10-11/04_reviewed_reject_sft/eval/stage1_r1/preds_single.jsonl`. Model: completed `R1_reviewed_reject` adapter. Original full evaluation remains stopped by user and will not be resumed.

## Results and failures

Pending.

## Decision and next proposal

Report answer stability, rationale similarity, per-class intervention effects, and fixed-prefix class-token shifts before interpreting any generated visual cue as grounded.

## 2026-10-21 — implementation and execution

- Script: `/sfs/vlm_qwen/experiments/2026-10-21/06_visual_grounding_audit/scripts/visual_grounding_audit.py`.
- Run wrapper: `run.sh`, tmux session `vlm_r1_visual_audit`.
- Environment: `/sfs/envs/qwen_vl/bin/python3`; source model `/sfs/vlm_qwen/global_qwen/models/Qwen3-VL-8B-Instruct`; adapter `R1_reviewed_reject`.
- Inputs are frozen partial Stage-1 predictions (`preds_single.jsonl`) and their immutable input manifest. The full Stage-1 inference was not resumed.
- Passed `python -m py_compile`, `bash -n`, and `--prepare-only` (48 balanced rows) before launch. The run stores every completed image-condition output immediately and skips it on restart.
- Pending observed outcome: `eval/r1_stage1_visual_audit/SUMMARY.md` once all 240 interventions finish.
