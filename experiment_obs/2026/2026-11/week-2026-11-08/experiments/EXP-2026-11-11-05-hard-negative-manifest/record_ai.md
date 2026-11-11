# EXP-2026-11-11-05 — hard-negative manifest checkpoint

Author: Codex. Human companion: [record.md](record.md).

Task: `RN-20261111-next-vlm-experiment` · authorized only for manifest preparation.

The queue will save evaluation error strata as nontrainable exemplars and then stop.
Because those rows come from evaluation scenes, they must not be copied into
training. A later Train-only mining pass, leakage review and explicit authorization
are required before any hard-negative retraining. Experiment 6 is not queued.

Evidence: `/sfs/vlm_qwen/experiments/2026-11-11/15_hard_negative_manifest/`.
