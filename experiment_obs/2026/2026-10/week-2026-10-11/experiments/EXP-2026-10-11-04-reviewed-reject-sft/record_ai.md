# EXP-2026-10-11-04-reviewed-reject-sft — Analyst-reviewed positives plus rejection SFT

Author: AI agent (Codex). Human companion: [record.md](record.md).

## Request and design

Train Qwen3-VL-8B-Instruct on analyst-reviewed radar/missile CoT examples, then add explicit `other` and `background` answers so the verifier can reject the non-target proposal majority revealed by EXP-2026-09-21-03. R0 isolates reviewed-positive data quality; R1 is the deployable four-way classifier. Selection is Test1-only; Test2 is report-only once.

## Setup and execution

- Status: **completed for GT-box evaluation**; subsequent Stage-1-box evaluation is tracked separately in EXP-2026-10-19-05.
- Positive source: `/sfs/cot_generation/dataset/cot_radar_missile_reviewed_v2`.
- R0: 980 balanced reviewed positives, radar 490/missile 490, 148 train scenes.
- R1: 1,960 balanced rows, 490 each radar/missile/other/background. `other` crops are train-scene labeled non-target objects; `background` crops have IoU <.01 against every annotation. Train/Test scene overlap and image references were verified zero.
- Test1: 313 positives (radar 103/missile 210, 33 scenes). Test2: 200 positives (radar 103/missile 97, 25 scenes). These GT-box tests have no other/background support, so four-way macro-F1 there is not a rejection metric.
- Model/recipe: Qwen3-VL-8B-Instruct; bf16; 2 epochs; answer-only loss with EOS; LoRA r8/alpha16 on language and visual merger (22.4M trainable). R1 used two V100s, 490 DDP steps, 26h55m.

## Results and failures

| model / split | radar P/R/F1 | missile P/R/F1 | macro-F1 |
|---|---|---|---:|
| R0 reviewed-positive Test1 | .700/.544/.612 | .804/.881/.841 | .727 |
| R1 four-way Test1 selection | .843/.417/.558 | .771/.962/.856 | .354* |
| R1 four-way Test2 report-only | .783/.524/.628 | .626/.845/.719 | .337* |

\*`other` and `background` support are zero in these positive-only GT-box files; their F1 is necessarily zero and pulls four-way macro-F1 down. Do not interpret it as rejection failure.

Observed implementation failure: the first R1 Test1 evaluator reused one variable for generation tokens and result records, failing after one row. It was fixed, compiled, and evaluation resumed without retraining; Test2 was then touched once as pre-registered.

## Decision and next proposal

R0 establishes that analyst-reviewed positives improve the Level-1 classification result. R1 must be evaluated on the frozen detector-box distribution to measure rejection; that is EXP-2026-10-19-05. Evidence: [data manifest](/sfs/vlm_qwen/experiments/2026-10-11/04_reviewed_reject_sft/reports/DATA_MANIFEST.md), [leaderboard](/sfs/vlm_qwen/experiments/2026-10-11/04_reviewed_reject_sft/reports/LEADERBOARD.md), [experiment README](/sfs/vlm_qwen/experiments/2026-10-11/04_reviewed_reject_sft/README.md).
