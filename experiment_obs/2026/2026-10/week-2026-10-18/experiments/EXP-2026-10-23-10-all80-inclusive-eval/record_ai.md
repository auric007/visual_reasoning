# EXP-2026-10-23-10 — all80 inclusive C1 audit

Author:Codex. Human companion:[record.md](record.md).

### 2026-10-23T19:24:15.980567+05:30 — RN-20261023-c1-all80-audit: user-authorized expanded evaluation

User explicitly requestsall80 originaltestscenes,including12background-training scenes,plusGTmiss/misclassificationIDs. This request supersedes earlier no-evaluationrestriction only for a separately labeledtraining-exposed diagnostic;clean67held-outbenchmark staysunchanged. Newexperiment10,fixedC1model,no training or selection. Reuse4231savedcleanL40S outputs onlyifhardware/model/prompt/imagehashesmatch;generate2752additionalproposalanswers on12training-exposedscenes.

The80thscene23JAN27044234-P3DS-200012483678_01_P001 has0Stage1proposals atconf≥.50;sourceTIFF497×549 andSR994×1098,GTcoordinates reach1352native. Full80as-provided scorecountsits7annotationsasStage1missesmechanically (1radar,4camo,2vehicle);separatelyreport79geometry-validscores,andmarkthese7GTrows source_invalid. Do not claimthatdatum is a verifiedvisualmiss or a clean generalizationestimate. No guessedrescale or sourceedit.

Code root unversioned;notebookGit is separate. Interpreter:/sfs/envs/qwen_vl/bin/python3. GPUcurrentlyidleL40S,matchingpreviousprofile. Expected6983proposals from79scorableimages,5308GTannotationsacross80;no proposals forinvalid80thimage. No finalmetricyet.

### 2026-10-23T19:30:27.010804+05:30 — RN-20261023-c1-all80-audit: preparation and scoring tests passed

Newexperiment10 manifest6983unique(fullscene+proposalID)keys,80scenes/5308GT,79geometry-valid,12training-exposed;4231reusedcleananswers,2752new pending.131newlyincludedcollisionpairs repairedlocally. Synthetictemporaryscoring/exporttest passed:clean67exactscoreequality,all80GT206radar/307missile versus79GT205/307,oneinvalidradarFNincrement,5308uniqueofficialGTIDs,513targetGTIDs,and7invalidsourceflags. No syntheticmetricsclaimed. Repairedimages/sourcehash checks completed;no old evidencechanged. Detachedinference launch authorized. [Recipe](/sfs/vlm_qwen/experiments/2026-10-19/10_all80_inclusive_eval/README.md).

### 2026-10-23T19:31:40.027831+05:30 — RN-20261023-c1-all80-audit: background run verified

Detachedtmux vlm_c1_all80_audit is activelysavingnewanswers. Observed4365/6983saved,including4231verifiedreusedanswers;latestprogresssnapshot4361 at0.473s/newrow,~20.7minremaining (allow20–30minwithimagevariation). No finalnewmetricyet. GPU/model/imagehashchecks passed onL40S;no otherjob interrupted.

All80-as-provided,79geometry-valid,clean67,andtraining-exposed12 results willbe separated inreports/FULL_METRICS.md andeval/METRICS.json,includingTest1/Test2. PermanentGTmiss/errorIDs atreports/comparison_ids/ willflagtraining_exposed andsource_geometry_valid. Mechanicalall80 includes7knownsource-invalidannotationsasmisses;the1invalidradarisnotaverifiedvisualmiss. Completionhook appendsobservedmetrics/table/IDpaths to thisdaily andexperimentrecord andcopiesreportstothealreadyforwardedgalleryunder/all80_audit/. Host/processshutdown couldinterrupt;rawanswersareappend-onlyresumable. [Experimentrecipe](/sfs/vlm_qwen/experiments/2026-10-19/10_all80_inclusive_eval/README.md).

### 2026-10-23T19:52:03.408604+05:30 — RN-20261023-c1-all80-audit

Completed6983/6983all79availableproposalanswers,coveringall80originalscenes(zero proposals onknowninvalid80th). ModelC1fixed;4231cleananswersreused,2752newtraining-exposedanswers. Reports:/sfs/vlm_qwen/experiments/2026-10-19/10_all80_inclusive_eval/reports/FULL_METRICS.md;permanentGTmiss/errorIDs:/sfs/vlm_qwen/experiments/2026-10-19/10_all80_inclusive_eval/reports/comparison_ids/. Clean67 metrics verified exactlyunchanged. All80as-provided containsknownsource-invalidGT-counting;79geometry-valid reportandtraining-exposureflags separate. radar:P0.1981,R0.3107,F10.2420,TP64,FP259,FN142. missile:P0.2696,R0.4821,F10.3458,TP148,FP401,FN159. 

| Scope | Class | GT | TP | FP | FN | Precision | Recall | F1 |
|---|---|---:|---:|---:|---:|---:|---:|---:|
| All80_as_provided | radar | 206 | 64 | 259 | 142 | 0.1981 | 0.3107 | 0.2420 |
| All80_as_provided | missile | 307 | 148 | 401 | 159 | 0.2696 | 0.4821 | 0.3458 |
| Geometry_valid79_including_training_exposure | radar | 205 | 64 | 259 | 141 | 0.1981 | 0.3122 | 0.2424 |
| Geometry_valid79_including_training_exposure | missile | 307 | 148 | 401 | 159 | 0.2696 | 0.4821 | 0.3458 |
| Clean67_held_out | radar | 152 | 54 | 221 | 98 | 0.1964 | 0.3553 | 0.2529 |
| Clean67_held_out | missile | 235 | 114 | 344 | 121 | 0.2489 | 0.4851 | 0.3290 |
| Training_exposed12_diagnostic | radar | 53 | 10 | 38 | 43 | 0.2083 | 0.1887 | 0.1980 |
| Training_exposed12_diagnostic | missile | 72 | 34 | 57 | 38 | 0.3736 | 0.4722 | 0.4172 |

Fullsplit/class tables and permanentGTIDerrors are in the experiment reports. This is the same run,not extra independent experiments.

