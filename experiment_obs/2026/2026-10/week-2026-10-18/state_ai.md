# Week of 2026-10-18 — state

Author: AI agent (Codex). Human companion: [state.md](state.md).

Notebook setup on October 19 is the only work recorded here so far.
Notebook-only publication to company repo `auric007/visual_reasoning` succeeded;
the dedicated service started at 18:03 IST with a 30-second wait between cycles.
This is a dated observation; use the controller for current service status.
[Daily task](daily/2026-10-19_ai.md) records intent, observed milestones and verification.
No new model experiment was run by notebook setup. Earlier October 18 research is
available only through linked original project evidence, not a complete daily log.

## 2026-10-19 — active experiment

[EXP-2026-10-19-05](experiments/EXP-2026-10-19-05-r1-stage1-box-eval/record_ai.md) is the current running R1 four-way evaluation on frozen detector boxes. It reuses the comparable Level-2 pixels and records results separately from positive-only GT-box testing.

## 2026-10-21T18:25:12+05:30 — current experiment state

The full R1 Stage-1 benchmark remains stopped at user request. EXP-2026-10-21-06 visual-grounding audit was restarted after startup/probe corrections; 240 interventions are pending. No completed visual-grounding finding is yet available. [Daily evidence](daily/2026-10-21_ai.md).

## 2026-10-21T19:22:30+05:30 — donor protocol corrected

User rejected confounded gold-class-cycle swaps. The 28-output exploratory run is stopped and preserved. Corrected prediction-contrasting audit is launched in `vlm_r1_contrastive_audit`, first verifying correct radar/missile donors on the current GPU. Same 48 recipients; explicit donor ledger; results pending. See [daily evidence](daily/2026-10-21_ai.md).

## 2026-10-22T01:39:00+05:30 — audit stopped at accepted sample size

User stopped corrected visual audit to detach GPU. 40 complete examples / 200 interventions retained (10 per gold class). Frozen snapshot and report at `06_visual_grounding_audit/eval/contrastive_verified/`. Offline analysis is next; no resume authorized. [Daily note](daily/2026-10-22_ai.md).

## 2026-10-22T15:16:42+05:30 — accepted 40-example audit analyzed

Offline all-40 analysis is complete at `/sfs/vlm_qwen/experiments/2026-10-21/06_visual_grounding_audit/analysis_40/DEEP_ANALYSIS.md`. Close-only/second-view-only answer changes22/40 and25/40; full replacement follows four reused donor pairs40/40; fixed-final-rationale top class unchanged; gray outputs exactly recombine rejection templates. These demonstrate sensitivity/continuation behavior, not expert visual faithfulness. All40 image pairs reviewed and per-case notes saved. Original20 rejection-class cases all remain target predictions. Mid-generation cut-point experiment is pending user approval; no model execution resumed. [Daily evidence](daily/2026-10-22_ai.md).

## 2026-10-22T16:42:12+05:30 — weekly experiment priorities documented

[Ranked plan](plan_ai.md) covers all human ideas recorded this week. P0 integrity prerequisite; P1 early-prefix continuation is first proposed GPU study; P2 claim/correction review can proceed offline in parallel. Rejection and paired-box diagnostics come before new training comparisons. This task only writes planning notes; no jobs restarted, data rebuilt, or Test2 rescored. [Daily record](daily/2026-10-22_ai.md).

## 2026-10-22T17:22:53+05:30 — P0/P2 offline audit and P1 pilot started

User approved P0/P2 offline then P1 GPU. Offline integrity/correction audit saved, with expert fine-feature/taxonomy questions still unresolved. New12-case/72-continuation Test1-only early-prefix pilot is running in tmux `vlm_p1_early_prefix` on NVIDIA L4; prior40-case run remains stopped. No training or sealed Test2 model evaluation. [Experiment record](/sfs/vlm_qwen/experiment_obs/2026/2026-10/week-2026-10-18/experiments/EXP-2026-10-22-07-early-prefix-grounding/record_ai.md).

## 2026-10-22T17:47:34+05:30 — P1 pilot completed and checked

P1 completed at17:41IST with72/72 continuations,exit0. Strict grouping/prefix/split checks passed. Opposite-pair answer changes4/12 after Visual evidence and1/12 after Grounding;same-class controls0/12. No training,ID removal,or new Test2 inference. [Results](/sfs/vlm_qwen/experiments/2026-10-19/07_early_prefix_grounding/eval/pilot_l4/RESULTS.md). Interpretation remains diagnostic; fine-feature/semantic review is not complete.

## 2026-10-22 — class-only four-way v2 dataset prepared

`/sfs/vlm_qwen/data/class_only_fourway_v2/` is READY with 1,764 two-image, class-only rows: radar 290, missile 490, other 492 and background 492. Other support is uniform across six requested Train classes and balanced hard/easy by a documented proxy. Background contains only strict saved Stage-2 target false positives from 12 now-embargoed Test1/Test2 scenes; all selected boxes have zero overlap with saved GT. Automated validation and AI visual-integrity review passed; annotation completeness remains an expert-review limitation. No training was started. [Daily evidence](daily/2026-10-22_ai.md).


## 2026-10-22T20:54:26+05:30 — class-only SFT running

User authorized recommended training on class_only_fourway_v2. [EXP-2026-10-22-08](/sfs/vlm_qwen/experiment_obs/2026/2026-10/week-2026-10-18/experiments/EXP-2026-10-22-08-class-only-fourway-sft/record_ai.md) is running in tmux vlm_c1_class_only on L4,2epochs/492updates,1968 balanced rows per epoch from1764 unique examples. Roughly2.25–2.5h total training at observed speed; comparison additional. All12 training-background source scenes embargoed; queued evaluation is only the filtered256-proposal Test1 diagnostic. No unfiltered Test1/Test2 score is valid for this trained corpus.
