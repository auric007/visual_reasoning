# EXP-2026-10-23-09 — C1 full clean Stage1 evaluation

Author: Codex. Human companion: [record.md](record.md).

Task:RN-20261023-c1-full-stage1-eval. Created2026-10-23T13:59:33.895724+05:30. User explicitly requests all-scene Stage1 metrics. New fixed-model evaluation,not training or resumption of stopped R1. Test2 authorized here only for report-only clean final evaluation; no selection.

Question:does the class-only four-way model reject non-target proposals and classify radar/missile across the natural frozen proposal population? Baseline reference is the earlier256-row diagnostic,not a matched full-population or same-GPU model comparison.

[Run and recipe](/sfs/vlm_qwen/experiments/2026-10-19/09_c1_full_stage1_eval/README.md). Model:Qwen3-VL-8B-Instruct plus C1_class_only adapter from08_class_only_fourway_sft. No seed-driven sampling; deterministic greedy batch1/bf16/SDPA,maxnew32. GPU observed idleL40S. Interpreter:/sfs/envs/qwen_vl/bin/python3. Code unversioned;script/input hashes recorded separately from notebookGit.

Cohort:source6983/79scenes;permanently omit2752 proposals/12training-background scenes. All242 source-train scenes excluded.4231 clean proposals/67scenes:Test1 1539/37scenes;Test2 2692/30scenes. Count TP/FP/FN/P/R/F1 for all4classes;target end-to-end recall uses filtered full-sceneGT,not global79scene totals. No balanced sampling.

Integrity issue observed:131 duplicate shortIDs across two original scenes caused shared crop paths. Correct clean-scene131 image pairs regenerated locally from canonical relocated SR source,matching original render/padding. No old dataset/evidence edits. Prior256-row diagnostic has zero entries from this affected scene. Assertions reverify original one-to-one confidence-order polygon matches,source gold,confidences,image paths,and scene embargo. Initial preparation deliberately failed its uniqueness check,then missing historical image-root check; canonical images relocated under/sfs/data. Scoring selftests passed;final preparation/execution pending.

Outputs:raw eval/predictions.jsonl;progress.json;eval/METRICS.json;reports/FULL_METRICS.md;reports/PER_SCENE.md. No final metric yet. Classification correctness is not explanation faithfulness; geometric unmatched gold is not expert proof of empty ground.

## 2026-10-23T14:00:45.887688+05:30 — RN-20261023-c1-full-stage1-eval:preparation passed;detachedtmux launch authorized on idleL40S.4231proposals;GT totals152radar/235missile,of whichStage1found95/195. Finalscores pending. Syntheticreporttest verifiesStage1missFN57/40,strictparsing,undefinedprecision,embargo and uniqueGTmatching. [Experiment](/sfs/vlm_qwen/experiments/2026-10-19/09_c1_full_stage1_eval/README.md).

### 2026-10-23T14:02:06.077281+05:30 — RN-20261023-c1-full-stage1-eval: running verified

- Detachedtmux vlm_c1_full_stage1 is producing freshL40S predictions:at least124/4231 saved (latest progress snapshot120;0.470s/row;rough early remaining32.2min,allow35–60min due image-size variation). Not a final metric. No training,selection,or embargo-scene inference.
- Passedpy_compile,undefinedprecision/FPFN/strictparser/missedGTtests;complete syntheticperfectlabel report pipeline validates67scene output and57radar/40missile Stage1misses. Synthetic results were temporary and not published as model performance. All4231 rawgold classes reverified against confidence-order one-to-one polygon matching.131 collision repairs separate;prior256diagnostic unaffected.
- Final outputs on normalcompletion: [09_c1_full_stage1_eval](/sfs/vlm_qwen/experiments/2026-10-19/09_c1_full_stage1_eval/reports/FULL_METRICS.md),[per-scene](/sfs/vlm_qwen/experiments/2026-10-19/09_c1_full_stage1_eval/reports/PER_SCENE.md);rawpredictions and progress preserved. Completion/failurehook appendsobservedoutcome to daily,experimentrecord,weeklystate andCLAUDE. Hostshutdown caninterruptanyjob.
- Notebook saved locally. Sync status check reports **Supervisor not running**;lastsuccess01:00IST is historical,not proof these new notes were pushed. No service restarted.


## 2026-10-23T14:34:51.723201+05:30 — observed outcome

Completed4231/4231 fresh C1 predictions on NVIDIA L40S; reports saved at [09_c1_full_stage1_eval](/sfs/vlm_qwen/experiments/2026-10-19/09_c1_full_stage1_eval/reports/FULL_METRICS.md), [per-scene](/sfs/vlm_qwen/experiments/2026-10-19/09_c1_full_stage1_eval/reports/PER_SCENE.md). No training or model selection;12 embargo scenes excluded. Combined:accuracy0.5479,macroF10.4097. Test1:accuracy0.4997,macroF10.4395. Test2:accuracy0.5754,macroF10.3511. 

### 2026-10-23T15:19:48.511072+05:30 — RN-20261023-c1-full-stage1-eval: completed results verified

- User asks update. Confirmed EXIT0,4231/4231 unique savedpredictions,67clean scenes;completion2026-10-23 14:34:51IST. Detachedsession ended normally. No new inference/training. Recomputed TP/FP/FN from allrawoutputs for allsplits/classes and verified end-to-end FN decomposition.
- Combined proposal-classification P/R/F1:radar.1964/.5684/.2919;missile.2489/.5846/.3492;other.7505/.6223/.6804;background.3092/.3262/.3174. Accuracy.5479,macroF1.4097,non-target acceptance.1358.
- Combined end-to-end:radar54TP/221FP/98FN,152GT,R.3553,F1.2529;missile114TP/344FP/121FN,235GT,R.4851,F1.3290. Stage1misses57radar/40missile plusverifiermisses41/81.
- Test1 end-to-end radarP/R.2313/.3579;missile.3298/.5529. Test2 radar.1562/.3509;missile.1156/.3077. CleanTest2 weaker,especiallymissile;benchmark retains annotation/taxonomy limitations. Fullnaturalprevalence only290/4231=6.85%targets,versus50%targets in256diagnostic;differentcohort and GPU prevent attributing score differences to modelchange. No fullR1 samecohort comparison run.
- [Fullmetrics](/sfs/vlm_qwen/experiments/2026-10-19/09_c1_full_stage1_eval/reports/FULL_METRICS.md),[per-scene](/sfs/vlm_qwen/experiments/2026-10-19/09_c1_full_stage1_eval/reports/PER_SCENE.md),[rawscores](/sfs/vlm_qwen/experiments/2026-10-19/09_c1_full_stage1_eval/eval/METRICS.json). Twelveembargoscenes remainexcluded;131 repairedpairs local only.

### 2026-10-23T17:03:55.001480+05:30 — RN-20261023-c1-full-stage1-eval: reference tables preserved inline

User requests that small experiments and metric tables remain readable in daily AI notes and experiment records for future reference. Earlier entries already held numeric summaries and report links; the formatted tables below are added explicitly. This is documentation of the same completed run, not another experiment.

**Experiment09: C1 class-only Qwen3-VL-8B-Instruct, frozen Stage1 boxes.** 4,231 proposals across 67 held-out scenes; Test1 1,539/37 scenes, Test2 2,692/30 scenes. Detector confidence ≥0.50, polygon IoU ≥0.50. Twelve training-background scenes (2,752 proposals) excluded. Fresh L40S inference; no training or checkpoint selection in this run.

**Combined proposal-classification table (the table shown in chat):**

| Class | Precision | Recall | F1 |
|---|---:|---:|---:|
| Radar | 19.6% | 56.8% | 29.2% |
| Missile | 24.9% | 58.5% | 34.9% |
| Other | 75.1% | 62.2% | 68.0% |
| Background | 30.9% | 32.6% | 31.7% |

**Full source report snapshot (fractions, not percentages):**

# C1 — full clean frozen Stage1 evaluation

4231 proposals across 67 scenes. Stage1 confidence >=0.50; polygon IoU >=0.50. Twelve training-background scenes (2752 proposals) excluded permanently. No balancing or subsampling. Single fixed checkpoint; no Test2 model selection.

Gold is assigned by original one-to-one class-agnostic matching. Background means unmatched annotated GT, not confirmed empty ground. Other includes radome and all annotated non-target classes under the historical taxonomy.

## Proposal classification

| Split | Class | Support | TP | FP | FN | Precision | Recall | F1 |
|---|---|---:|---:|---:|---:|---:|---:|---:|
| Combined | radar | 95 | 54 | 221 | 41 | 0.1964 | 0.5684 | 0.2919 |
| Combined | missile | 195 | 114 | 344 | 81 | 0.2489 | 0.5846 | 0.3492 |
| Combined | other | 2920 | 1817 | 604 | 1103 | 0.7505 | 0.6223 | 0.6804 |
| Combined | background | 1021 | 333 | 744 | 688 | 0.3092 | 0.3262 | 0.3174 |
| Test1 | radar | 65 | 34 | 113 | 31 | 0.2313 | 0.5231 | 0.3208 |
| Test1 | missile | 140 | 94 | 191 | 46 | 0.3298 | 0.6714 | 0.4424 |
| Test1 | other | 883 | 468 | 236 | 415 | 0.6648 | 0.5300 | 0.5898 |
| Test1 | background | 451 | 173 | 230 | 278 | 0.4293 | 0.3836 | 0.4052 |
| Test2 | radar | 30 | 20 | 108 | 10 | 0.1562 | 0.6667 | 0.2532 |
| Test2 | missile | 55 | 20 | 153 | 35 | 0.1156 | 0.3636 | 0.1754 |
| Test2 | other | 2037 | 1349 | 368 | 688 | 0.7857 | 0.6622 | 0.7187 |
| Test2 | background | 570 | 160 | 514 | 410 | 0.2374 | 0.2807 | 0.2572 |

## End-to-end targets (includes Stage1 misses)

| Split | Class | All GT | Stage1 found | Stage1 missed | TP | FP | FN | Precision | Recall | F1 |
|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| Combined | radar | 152 | 95 | 57 | 54 | 221 | 98 | 0.1964 | 0.3553 | 0.2529 |
| Combined | missile | 235 | 195 | 40 | 114 | 344 | 121 | 0.2489 | 0.4851 | 0.3290 |
| Test1 | radar | 95 | 65 | 30 | 34 | 113 | 61 | 0.2313 | 0.3579 | 0.2810 |
| Test1 | missile | 170 | 140 | 30 | 94 | 191 | 76 | 0.3298 | 0.5529 | 0.4132 |
| Test2 | radar | 57 | 30 | 27 | 20 | 108 | 37 | 0.1562 | 0.3509 | 0.2162 |
| Test2 | missile | 65 | 55 | 10 | 20 | 153 | 45 | 0.1156 | 0.3077 | 0.1681 |

End-to-end retains the historical fixed Stage1 one-to-one assignments; duplicate/unmatched proposals remain false positives. This is a frozen-pipeline metric, not a new independent class-wise AP rematching. Proposal-classification recall excludes Stage1 misses. All scores inherit annotation completeness and taxonomy limitations. Previous 256-row scores were class-balanced and measured on L4; do not interpret differences from this natural-prevalence L40S run as training gains.

## Classifier summary

| Split | Proposals | Accuracy | Macro-F1 | Non-target acceptance |
|---|---:|---:|---:|---:|
| Combined | 4231 | 0.5479 | 0.4097 | 0.1358 |
| Test1 | 1539 | 0.4997 | 0.4395 | 0.2106 |
| Test2 | 2692 | 0.5754 | 0.3511 | 0.0974 |


[Full report](/sfs/vlm_qwen/experiments/2026-10-19/09_c1_full_stage1_eval/reports/FULL_METRICS.md) · [Per-scene table](/sfs/vlm_qwen/experiments/2026-10-19/09_c1_full_stage1_eval/reports/PER_SCENE.md) · [Exact JSON metrics](/sfs/vlm_qwen/experiments/2026-10-19/09_c1_full_stage1_eval/eval/METRICS.json) · [Experiment record](/sfs/vlm_qwen/experiment_obs/2026/2026-10/week-2026-10-18/experiments/EXP-2026-10-23-09-c1-full-stage1-eval/record_ai.md)

Snapshot source SHA256: `e03b64769694b0d0f026c4a24d7c3d2e71d30e918dd8ef2968779c382ab2c76f`.
