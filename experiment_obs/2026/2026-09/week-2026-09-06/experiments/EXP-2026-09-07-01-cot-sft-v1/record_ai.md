# EXP-2026-09-07-01-cot-sft-v1 — Initial CoT SFT sweep

Author: AI agent (Codex). Human companion: [record.md](record.md).

## Request and design

Historical experiment reconstructed from its durable final report at [01_cot_sft](/sfs/vlm_qwen/experiments/2026-09-07/01_cot_sft/reports/FINAL.md). The question was whether Qwen3-VL-8B-Instruct could learn radar/missile classification with five-stage chain-of-thought (CoT) outputs from paired close/context crops. Selection used Test1; Test2 was sealed and evaluated once on the selected winner.

## Setup and execution

- Status: **completed**; actual run 2026-09-11 21:19 to 2026-09-12 03:02.
- Data: `/sfs/cot_generation/dataset/cot_radar_missile_v1`; 276 train, Test1 n=150, Test2 n=102.
- Model: Qwen3-VL-8B-Instruct; LoRA text r=8/alpha=16 plus vision merger LoRA for winner A7.
- Ten SFT arms; 2 epochs. A7 used class-balanced training and 22.4M trainable parameters (0.25%).
- Evaluation level: **Level 1**. Training and both tests used ground-truth OBBs drawn cyan on the paired images; this is an upper bound and not detector-to-VLM performance.

## Results and failures

Winner **A7_bal_merger**:

| split | macro-F1 | radar P/R/F1 | missile F1 |
|---|---:|---|---:|
| Test1 selection, n=150 | 0.633 | .490/.522/.505 | .761 |
| Test2 sealed, n=102 | 0.618 [0.516, 0.711] | .583/.651/.615 | .621 |

Observed findings: class balancing materially raised radar recall; merger LoRA helped modestly; a larger text LoRA rank overfit despite lower train loss. The original context-resolution conclusion was later superseded: context presence is load-bearing for radar in the larger v2 study.

## Decision and next proposal

The winning SFT recipe became the baseline for the larger v2 dataset. Test2 remains sealed for this sweep; do not rescore it with another SFT arm. Evidence: [final report](/sfs/vlm_qwen/experiments/2026-09-07/01_cot_sft/reports/FINAL.md), [test seal](/sfs/vlm_qwen/experiments/2026-09-07/01_cot_sft/eval/TEST2_SEAL.md).
