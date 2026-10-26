# Review of 18–24 October 2026

Author: Codex. Human companion: [review.md](review.md).

Compiled on 26 October from the available experiment outputs and notes. Readability corrected: 26 October 2026, 15:56 IST.

This review supplements the partial report written on 22 October. It preserves the original results and distinguishes observations from explanations that have not been tested.

## What finished

### Experiment 07: early-prefix pilot

The pilot produced 72 continuations for 12 recipient examples. Replacing images with a different-class pair changed the answer in 4 of 12 cases after the Visual Evidence section and 1 of 12 after Grounding. Same-class replacements changed none of the answers.

This measures sensitivity under an intervention. It does not establish whether an explanation is faithful or whether a section can be removed without affecting accuracy.

### Experiment 08: class-only SFT

Training completed 492 updates over two epochs. On the balanced 256-proposal diagnostic, C1 achieved macro-F1 **0.553**, compared with **0.202** for R1.

Both the data and output format changed, so this comparison cannot isolate which change caused the gain. Both models emitted about nine tokens with the same class-only question; no clear inference-speed benefit was measured.

### Experiment 09: clean Stage1-box evaluation

The evaluation covered **4,231 proposals across 67 scenes**. A legacy filename collision affected 131 image pairs; correct pairs were regenerated in the new experiment folder without changing the source files.

There were **221 false radar predictions** and **344 false missile predictions**. Permanent GT IDs, error lists and a radar-first gallery were saved.

### Experiment 10: expanded all-80 audit

The user-authorized audit finished on 23 October with exit code 0. It contains **6,983 proposal answers**, including **2,752 new answers** from the 12 scenes used for background training.

The previous clean 67-scene scores were verified to be exactly unchanged. Reports separate all 80 scenes as provided, 79 scenes with valid geometry, the clean 67-scene subset, and the 12 training-exposed scenes.

## Final metrics

Recall in this table is end-to-end and includes Stage1 misses.

| Evaluation scope | Class | Precision | End-to-end recall | F1 | TP | FP | FN |
|---|---|---:|---:|---:|---:|---:|---:|
| All 80 scenes, as provided | radar | 19.8% | 31.1% | 24.2% | 64 | 259 | 142 |
| All 80 scenes, as provided | missile | 27.0% | 48.2% | 34.6% | 148 | 401 | 159 |
| Clean 67-scene subset | radar | 19.6% | 35.5% | 25.3% | 54 | 221 | 98 |
| Clean 67-scene subset | missile | 24.9% | 48.5% | 32.9% | 114 | 344 | 121 |

## What remains uncertain

- Class-revealing text and repetitive targets were observed in the old training data. Their contribution to each failure has not been isolated by a controlled experiment.
- Visual token counts do not establish which image controls the answer.
- Results from different GPUs or different class proportions should not be interpreted as a controlled training comparison.
- Fine-feature correctness and the treatment of radomes remain open annotation questions. The raw radome labels were not silently changed.
- The all-80 score includes training-exposed scenes and one image/label mismatch. It is not a wholly held-out generalization estimate.

## Carry forward

Your 23 October note asks whether the VLM and Stage2 YOLO fail on the same instances. The permanent ID exports are ready for that comparison. On 26 October, the Stage2 baseline was identified as `m0001_sep_w1_ensemble`; the instance-level comparison has not yet been computed.

The previous plan also lists the CoT-faithfulness and cross-modal data-selection papers. No new paper-based experiment has been run. On 26 October, you selected all three directions for the new week, with the model comparison first.

## Evidence

- [Experiment 09: clean results](/sfs/vlm_qwen/experiments/2026-10-19/09_c1_full_stage1_eval/reports/FULL_METRICS.md).
- [Experiment 10: all-80 audit](/sfs/vlm_qwen/experiments/2026-10-19/10_all80_inclusive_eval/reports/FULL_METRICS.md).
- [Permanent IDs and error exports](/sfs/vlm_qwen/experiments/2026-10-19/10_all80_inclusive_eval/reports/comparison_ids/).
- [Earlier partial weekly report](weekly_report_ai.md).
- [Original weekly plan](plan.md).

The research code is unversioned; notebook Git history is separate. This review covers the evidence available in the saved files and does not claim to capture unobserved manual work.
