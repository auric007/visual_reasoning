# EXP-2026-09-14-02-v2-cot-sft — Larger corrected CoT SFT sweep

Author: AI agent (Codex). Human companion: [record.md](record.md).

## Request and design

Historical experiment reconstructed from [the final report](/sfs/vlm_qwen/experiments/2026-09-14/02_v2_cot_sft/reports/FINAL.md). It tested whether the A7 recipe held on a larger CoT corpus and whether balance, merger LoRA, and context resolution materially changed radar/missile classification.

## Setup and execution

- Status: **completed** on 2026-09-17.
- Data: `/sfs/cot_generation/dataset/cot_radar_missile_v2`; raw train 1,008 rows (radar 364, missile 644, 177 scenes); balanced train 1,288 rows (644 each). Test1: 313 rows, 33 scenes; Test2: 200 rows, 25 scenes. Train/Test scene overlap was verified zero.
- Model: Qwen3-VL-8B-Instruct, greedy evaluation on one L40S.
- Arms: B1 balanced + merger (headline), B2 balanced no merger, B3 unbalanced + merger, B4 balanced + merger with 512px context at training.
- Evaluation level: **Level 1** using GT-box overlays; results are classification upper bounds.

## Results and failures

Headline B1 combined Test1+Test2 n=513: macro-F1 **0.690 [0.646, 0.731]**, radar P/R/F1 .69/.53/.60, missile .73/.84/.78. B3 unbalanced had 0.705 combined macro-F1 but its CI versus B1 crossed zero; B4 ctx512 had 0.696 and halved training time.

Observed findings: at this dataset size the four recipe variants were within 0.033 macro-F1, so recipe knobs no longer resolved the main limitation. Radar recall remained low on Test1 (.43–.53), consistent with a scene/data coverage problem. Preserving the context image matters for radar; reducing its training resolution to 512px was inexpensive, but removing it at inference was harmful.

## Decision and next proposal

Use B1 as the comparable headline, keep context present, and evaluate with detector boxes before treating Level-1 performance as deployable. Evidence: [final report](/sfs/vlm_qwen/experiments/2026-09-14/02_v2_cot_sft/reports/FINAL.md), [data manifest](/sfs/vlm_qwen/experiments/2026-09-14/02_v2_cot_sft/reports/DATA_MANIFEST.md).
