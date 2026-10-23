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
