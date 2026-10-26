# Saved VLM and YOLO reports: evaluation comparability audit

Author: Codex. Human companion: [evaluation_comparability.md](evaluation_comparability.md).
Updated: 26 October 2026, 19:50 IST. Task: `RN-20261026-vlm-stage2-report-audit`. Correlation: `RN-20261026-week-start`.

## Status

Completed a metadata and aggregate-report audit. This is not a new model evaluation or an instance-level overlap experiment. No training, inference, rematching, confidence selection, label changes or asset-level detected/missed lists were produced. Aggregate counts cannot establish which particular instances two models share.

## Verified inputs

The latest completed four-class class-only adapter found in the VLM experiment tree is **C1_class_only**:

`/sfs/vlm_qwen/experiments/2026-10-19/08_class_only_fourway_sft/runs/C1_class_only`

Its training completion marker records update 492, and training/evaluation exit codes are zero. Its final adapter configuration and weight hashes match the hashes frozen for the clean evaluation. This verifies checkpoint identity; it is not a new test of model quality. Output supervision is the class answer tag plus EOS. The four labels are radar, missile, other and background. The training configuration uses a fresh Qwen3-VL-8B-Instruct base with language/merger LoRA and frozen vision blocks.

The supplied [Stage2 guide](/sfs/stage2/experiment_obs/knowledge/test_predictions_guide_ai.md) identifies two distinct references: the fixed **m0001** ensemble and a test-selected **best_per_class** collection. The latter combines four model sources and test-selected class thresholds; it is not one independently validated checkpoint. The phrase “single-model output” in the guide should not be read as one backbone: m0001 itself contains two backbones.

All three Stage2 folders referenced by the guide—m0001 deployment predictions, best-per-class predictions and the draft GT export—contain files for all 80 expected scene stems. Their contents were not rescored in this audit.

## Cohort checks

| Check | Observed result | Interpretation |
|---|---:|---|
| Original scene-manifest intersection | 80 of 80 | Both projects refer to the same original scene names. |
| Clean VLM cohort | 67 scenes; 4,231 proposals | Separate from the inclusive diagnostic. |
| Inclusive VLM cohort | 80 scenes; 6,983 proposals | Includes training exposure and a known invalid source. |
| Training-exposed subset | 12 scenes | These were used for VLM background training; not fully held out. |
| Geometry-valid subset | 79 scenes | One original source has inconsistent image/label geometry. |
| VLM all-annotation inventory | 5,308 annotations | Includes historical non-target labels. |
| Stage2 eight-class inventory | 5,100 annotations | Different inclusion and mapping policy. |

Identical scene names do not establish identical GT objects, taxonomies, pixels or candidate boxes. The 208-annotation inventory difference must not be treated as a model miss count. The later VLM audit preserves the earlier clean classification and end-to-end aggregate results exactly.

## Why the published headline scores cannot be ranked directly

| Evaluation detail | Saved VLM reports | Saved Stage2 headline reports | Consequence |
|---|---|---|---|
| Task | Four-way classification of frozen Stage1 proposals; separate end-to-end target accounting | Eight-class detection | Four-class macro-F1 and eight-class macro-F1 measure different averages. |
| Box population | Fixed Stage1 proposals | Independently generated YOLO boxes | The same scene does not imply the same candidate set. |
| IoU | Polygon IoU at least 0.50 | Headline uses polygon IoU at least 0.30 | Geometric success requirements differ. |
| Matching | Frozen confidence-ordered, class-agnostic one-to-one assignments | Confidence-ordered matching within each predicted class | TP/FP/FN are assigned differently, even for identical boxes. |
| Target taxonomy | Exact historical raw target labels; other annotated classes collapse to other | Official simple labels or attribute-remapped draft P04 v2 | Neither label policy can silently replace the other. |
| GT inclusion | All historical annotated classes can receive proposal assignments | Eight trained classes; several raw classes excluded | Background and false-positive definitions differ. |
| Coordinate representation | Frozen proposal linkage uses source geometry | Stage2 exported boxes use a 0.30 m grid | Coordinate compatibility must be established explicitly before any geometric comparison. |
| Held-out status | Clean67 separately reported from the exposed all80 diagnostic | Guide headlines use all80 | These cohorts cannot be pooled into one held-out result. |
| Threshold/model selection | Fixed C1 checkpoint and fixed Stage1 proposal cutoff | Deployment settings or choices optimized on test80 | Best-per-class values are exploratory and selection-biased. |
| Recall denominator | Proposal recall excludes Stage1 misses; end-to-end recall includes them | Detection recall counts eligible GT under its own mapping | Always name the denominator. |
| Background label | No annotation matched under the frozen protocol | Some raw labels are excluded from evaluation | Annotation-unmatched does not guarantee physically empty ground. |

## What this audit establishes

The saved model and report paths are available, and the original scene manifests agree. The C1 checkpoint identity and existing report arithmetic checks pass. The principal obstacle to interpreting the published numbers is evaluation incompatibility, rather than a missing checkpoint.

This does **not** establish which model finds a particular asset, shared misses, complementary successes, an integration benefit or a model improvement. Those quantities cannot be recovered from marginal confusion matrices or aggregate TP/FP/FN totals. No new accuracy, precision, recall, F1 or overlap result is claimed here.

## Evidence and reproducibility

- [C1 training configuration](/sfs/vlm_qwen/experiments/2026-10-19/08_class_only_fourway_sft/config.json).
- [Clean VLM report](/sfs/vlm_qwen/experiments/2026-10-19/09_c1_full_stage1_eval/reports/FULL_METRICS.md) and [aggregate JSON](/sfs/vlm_qwen/experiments/2026-10-19/09_c1_full_stage1_eval/eval/METRICS.json).
- [Inclusive VLM report](/sfs/vlm_qwen/experiments/2026-10-19/10_all80_inclusive_eval/reports/FULL_METRICS.md) and [aggregate JSON](/sfs/vlm_qwen/experiments/2026-10-19/10_all80_inclusive_eval/eval/METRICS.json).
- [Stage2 model card](/sfs/stage2/models/BEST/MODEL_CARD.md).
- [Stage2 aggregate validation](/sfs/stage2/experiment_obs/2026/2026-10/week-2026-10-25/experiments/EXP-2026-10-26-02-best-pred-files-guide/best_per_class_check_ai.json). Its two saved sets pass arithmetic consistency checks; neither was rescored here.
- [Machine-readable audit evidence](evaluation_comparability_checks_ai.json) contains source hashes, metadata checks and revision identifiers, with no instance outcome lists.

Executed verification: `/usr/bin/python3 /tmp/audit_saved_evaluation_reports.py`, using Python standard library only. No model environment setup or dependency changes were needed. The documented model interpreter remains `/sfs/envs/qwen_vl/bin/python3`.

VLM research root is unversioned. Stage2 research code HEAD is `e5af44c4bcc6763cb5031887bc9c56b071ad4508` and its working tree was already dirty; no code files were edited. Notebook revisions are recorded separately in the JSON evidence. Source datasets, predictions, evaluation protocols and checkpoints are unchanged.
