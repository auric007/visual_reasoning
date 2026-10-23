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

