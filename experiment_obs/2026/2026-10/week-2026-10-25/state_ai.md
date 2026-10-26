# Research status — week of 25–31 October 2026

Author: Codex. Human companion: [state.md](state.md).

Updated: 26 October 2026, 15:56 IST. Task: `RN-20261026-week-start`.

## Current priorities

1. Define and run the next VLM training experiment.
2. Read the grounding/data-selection papers and design an experiment.
3. Optionally extend the completed VLM–YOLO comparison to false-positive overlap and a prospective fusion rule.

You confirmed all three tasks on 26 October, with the comparison first. The earlier “selection pending” status is no longer current.

## Completed baseline

The previous all-80 audit finished successfully. All 6,983 predictions and the comparison-ID exports were verified. Keep its training-exposed and invalid-source cases distinct from the clean 67-scene benchmark.

## Work in progress

The Stage2 baseline has been identified as `m0001_sep_w1_ensemble`. Prediction files and evaluation settings still need to be aligned before computing the VLM–YOLO comparison. No cross-model results have been produced yet.

## 26 October 2026, 20:19 IST — VLM–YOLO target overlap completed

[EXP-2026-10-26-01](experiments/EXP-2026-10-26-01-vlm-stage2-overlap/record_ai.md) aligned permanent target IDs and rematched m0001 using the VLM's IoU 0.50 convention. On the clean 67-scene cohort, 138 targets are correct for both systems, 30 only for the VLM, 66 only for YOLO and 153 for neither. YOLO gets 204/387 targets, the VLM 168/387 and the oracle union 234/387. No fusion rule or false-positive overlap has been tested.

This supersedes the earlier work-in-progress paragraph above; it remains as dated history.

## Training status

No new training or inference has started. The next training recipe and paper-based experiment have not been defined. Today's project-environment check reported no CUDA device.

[Weekly TODO](plan_ai.md) · [Today's log](daily/2026-10-26_ai.md).

## 26 October 2026, 16:11 IST — Previous-week conclusions reviewed

The human report is unchanged. A sourced claim review and suggested wording are saved in the [previous weekly AI report](../../week-2026-10-18/weekly_report_ai.md#review-of-your-conclusions). The confusion matrix is correct; causal claims and cohort/recall wording need qualification. This review produced no new model results.


## 26 October 2026, 19:50 IST — Aggregate comparison preflight completed

Verified checkpoint and scene-manifest identities; saved the [report-comparability audit](/sfs/vlm_qwen/experiment_obs/knowledge/evaluation_comparability_ai.md). Existing VLM and Stage2 headline scores have incompatible taxonomies, matching rules and denominators. No new model result or instance-overlap experiment was produced. This dated update supersedes the earlier statement that the Stage2 prediction-file locations were still unknown.
