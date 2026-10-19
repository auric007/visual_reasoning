# EXP-2026-09-21-03-level2-spotter-boxes — Frozen detector-box evaluation

Author: AI agent (Codex). Human companion: [record.md](record.md).

## Request and design

Historical Level-2 evaluation reconstructed from [the final report](/sfs/vlm_qwen/experiments/2026-09-21/03_level2_spotter_boxes/reports/FINAL.md). It replaced perfect GT boxes with frozen n0005 class-agnostic Stage-1 detector proposals, keeping ground truth strictly post-inference for IoU scoring.

## Setup and execution

- Status: **completed** on 2026-09-21.
- Model: v2 headline `B1_a7` from EXP-2026-09-14-02.
- Detector data: 6,983 n0005 proposals at confidence ≥0.50 across 79 usable scenes; greedy GT matching IoU ≥0.50 after inference.
- Input: detector box cyan; other detector proposals grey. No GT neighbor boxes or GT-derived target boundary appeared in the VLM input.
- Runtime: 6.1h on one L40S, batch 6.

## Results and failures

| view | radar F1 | missile F1 | macro-F1 |
|---|---:|---:|---:|
| End-to-end detector→VLM | .075 | .075 | **.075** |
| Classifier-only on 368 matched radar/missile boxes | .569 | .835 | **.702** |

Observed failure: 94.7% of detector proposals were non-target (3,035 background and 3,580 other-class boxes), while v2 had only radar/missile vocabulary. It called 3,034/3,035 background boxes radar or missile. This was a rejection-vocabulary failure, not primarily a detector-box geometry failure. Stage-1 itself capped radar recall at .581 (119/205 found) and missile recall at .811 (249/307 found).

## Decision and next proposal

The evidence directly motivated four-way `radar/missile/other/background` SFT in EXP-2026-10-11-04. The frozen detector archive remains the canonical comparable Level-2 benchmark. Evidence: [final report](/sfs/vlm_qwen/experiments/2026-09-21/03_level2_spotter_boxes/reports/FINAL.md), [frozen Stage-1 README](/sfs/vlm_qwen/experiments/2026-09-21/03_level2_spotter_boxes/stage1_predictions/README.md).
