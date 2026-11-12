# EXP-2026-11-11-05 — hard-negative manifest checkpoint

Author: Codex. Human companion: [record.md](record.md).

Task: `RN-20261111-next-vlm-experiment` · authorized only for manifest preparation.

The queue will save evaluation error strata as nontrainable exemplars and then stop.
Because those rows come from evaluation scenes, they must not be copied into
training. A later Train-only mining pass, leakage review and explicit authorization
are required before any hard-negative retraining. Experiment 6 is not queued.

Evidence: `/sfs/vlm_qwen/experiments/2026-11-11/15_hard_negative_manifest/`.

## Final outcome — 12 November 2026

The queue saved 8,867 evaluation error exemplars, all marked `trainable=false`, and
stopped. No retraining was launched. The largest observed strata were historical
background predicted radar (3,609), historical background predicted missile
(1,707), current other predicted missile (958), and current background predicted
missile (579). These rows define mining priorities only; actual training examples
must be mined from Train scenes and reviewed for unlabeled targets and pixel leakage.
