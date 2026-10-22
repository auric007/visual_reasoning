# October notebook state

Author: AI agent (Codex). Human companion: [state.md](state.md).

The notebook was enrolled on 2026-10-19. Current evidence:
[setup daily](week-2026-10-18/daily/2026-10-19_ai.md) and
[root state](../../state_ai.md). Prior work is indexed under
[legacy](../../legacy/README_ai.md), with incomplete notebook coverage before enrollment.

## 2026-10-19 — research history and active evaluation

Historical Qwen records were added from durable source reports. The active Stage-1-box rejection evaluation is documented in [EXP-2026-10-19-05](week-2026-10-18/experiments/EXP-2026-10-19-05-r1-stage1-box-eval/record_ai.md); it is running and has no final metrics yet.

## 2026-10-22T15:16:42+05:30 — visual-grounding offline analysis

The accepted40-example/200-output audit is analyzed; main report `/sfs/vlm_qwen/experiments/2026-10-21/06_visual_grounding_audit/analysis_40/DEEP_ANALYSIS.md`. No GPU work resumed. Findings and limits are in the [October22 daily note](/sfs/vlm_qwen/experiment_obs/2026/2026-10/week-2026-10-18/daily/2026-10-22_ai.md). Earlier running-status statements are historical.

## 2026-10-22T17:22:53+05:30 — P0/P2 offline audit and P1 pilot started

User approved P0/P2 offline then P1 GPU. Offline integrity/correction audit saved, with expert fine-feature/taxonomy questions still unresolved. New12-case/72-continuation Test1-only early-prefix pilot is running in tmux `vlm_p1_early_prefix` on NVIDIA L4; prior40-case run remains stopped. No training or sealed Test2 model evaluation. [Experiment record](/sfs/vlm_qwen/experiment_obs/2026/2026-10/week-2026-10-18/experiments/EXP-2026-10-22-07-early-prefix-grounding/record_ai.md).

## 2026-10-23T00:48:10+05:30 — class-only comparison complete

EXP-2026-10-22-08 finished training/comparison successfully. Fixed256-proposal clean-Test1 diagnostic:macro-F1.202→.553,accuracy.312→.559,non-target acceptance100%→25.8%. Missile recall falls.969→.797 while precision improves;radar recall improves.281→.531. Both models output~9tokens here,no clear speed improvement. Data/format changes are confounded;not full-set or deployment scores. [October23 evidence](/sfs/vlm_qwen/experiment_obs/2026/2026-10/week-2026-10-18/daily/2026-10-23_ai.md).
