# Research status — week of 25–31 October 2026

Author: Codex. Human companion: [state.md](state.md).

Updated: 26 October 2026, 15:56 IST. Task: `RN-20261026-week-start`.

## Current priorities

1. Compare VLM and Stage2 YOLO instance-level errors.
2. Define and run the next VLM training experiment.
3. Read the grounding/data-selection papers and design an experiment.

You confirmed all three tasks on 26 October, with the comparison first. The earlier “selection pending” status is no longer current.

## Completed baseline

The previous all-80 audit finished successfully. All 6,983 predictions and the comparison-ID exports were verified. Keep its training-exposed and invalid-source cases distinct from the clean 67-scene benchmark.

## Work in progress

The Stage2 baseline has been identified as `m0001_sep_w1_ensemble`. Prediction files and evaluation settings still need to be aligned before computing the VLM–YOLO comparison. No cross-model results have been produced yet.

## Training status

No new training or inference has started. The next training recipe and paper-based experiment have not been defined. Today's project-environment check reported no CUDA device.

[Weekly TODO](plan_ai.md) · [Today's log](daily/2026-10-26_ai.md).

## 26 October 2026, 16:11 IST — Previous-week conclusions reviewed

The human report is unchanged. A sourced claim review and suggested wording are saved in the [previous weekly AI report](../../week-2026-10-18/weekly_report_ai.md#review-of-your-conclusions). The confusion matrix is correct; causal claims and cohort/recall wording need qualification. This review produced no new model results.
