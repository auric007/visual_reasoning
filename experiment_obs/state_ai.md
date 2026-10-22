# Notebook state — 2026-10-19

Author: AI agent (Codex). Human companion: [state.md](state.md).

- Canonical project: `/sfs/vlm_qwen`; notebook: `/sfs/vlm_qwen/experiment_obs`.
- Registered for documentation in `/sfs/research-notebook/projects.json`.
- Root code Git: absent at inspection; code revision is unversioned, not a notebook SHA.
- Independent notebook metadata: `/sfs/markdown-sync/git/vlm_qwen`.
- Company notebook destination: `auric007/visual_reasoning`, main; public access approved.
- Initial audited notebook publication succeeded. Service `vlm_qwen-experiment-sync`
  started with PID 6134 and a successful cycle at 2026-10-19 18:03 IST.
  It waits 30 seconds after each cycle; check current status rather than assuming
  this dated observation proves future uptime. Mac scheduling has not been configured here.
- Original research evidence remains in `/sfs/vlm_qwen/experiments/`.
- Research interpreter: `/sfs/envs/qwen_vl/bin/python3`, per root CLAUDE.md.
- Latest inspected `04_reviewed_reject_sft/status.json` reports `complete` at
  2026-10-18T01:11:19+00:00. This is a file observation, not a fresh model evaluation.
- Root CLAUDE.md separately records a staged Stage-1 R1 evaluation. Its live execution/completion
  was not checked by this documentation task.
- No training, inference, scoring or model/environment changes were made for notebook setup.

Evidence: [daily setup](2026/2026-10/week-2026-10-18/daily/2026-10-19_ai.md),
[original evidence index](legacy/README_ai.md). Missing notebook history before setup
does not imply no earlier research activity.

## 2026-10-19 — experiment history recorded

Five evidence-backed experiment records now link the original Qwen SFT/Level-2/reviewed-data runs without moving code or artifacts. Current active work is [EXP-2026-10-19-05](2026/2026-10/week-2026-10-18/experiments/EXP-2026-10-19-05-r1-stage1-box-eval/record_ai.md): R1 four-way inference on 6,983 frozen Stage-1 boxes. At the latest observed checkpoint it was running; final metrics remain pending.

## 2026-10-22T15:16:42+05:30 — visual-grounding offline analysis

The accepted40-example/200-output audit is analyzed; main report `/sfs/vlm_qwen/experiments/2026-10-21/06_visual_grounding_audit/analysis_40/DEEP_ANALYSIS.md`. No GPU work resumed. Findings and limits are in the [October22 daily note](/sfs/vlm_qwen/experiment_obs/2026/2026-10/week-2026-10-18/daily/2026-10-22_ai.md). Earlier running-status statements are historical.

## 2026-10-22T17:22:53+05:30 — P0/P2 offline audit and P1 pilot started

User approved P0/P2 offline then P1 GPU. Offline integrity/correction audit saved, with expert fine-feature/taxonomy questions still unresolved. New12-case/72-continuation Test1-only early-prefix pilot is running in tmux `vlm_p1_early_prefix` on NVIDIA L4; prior40-case run remains stopped. No training or sealed Test2 model evaluation. [Experiment record](/sfs/vlm_qwen/experiment_obs/2026/2026-10/week-2026-10-18/experiments/EXP-2026-10-22-07-early-prefix-grounding/record_ai.md).

## 2026-10-22T20:54:26+05:30 — class-only SFT running

User authorized recommended training on class_only_fourway_v2. [EXP-2026-10-22-08](/sfs/vlm_qwen/experiment_obs/2026/2026-10/week-2026-10-18/experiments/EXP-2026-10-22-08-class-only-fourway-sft/record_ai.md) is running in tmux vlm_c1_class_only on L4,2epochs/492updates,1968 balanced rows per epoch from1764 unique examples. Roughly2.25–2.5h total training at observed speed; comparison additional. All12 training-background source scenes embargoed; queued evaluation is only the filtered256-proposal Test1 diagnostic. No unfiltered Test1/Test2 score is valid for this trained corpus.
