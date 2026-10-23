# EXP-2026-10-23-10 — all80 inclusive C1 audit

Author:Codex. Human companion:[record.md](record.md).

### 2026-10-23T19:24:15.980567+05:30 — RN-20261023-c1-all80-audit: user-authorized expanded evaluation

User explicitly requestsall80 originaltestscenes,including12background-training scenes,plusGTmiss/misclassificationIDs. This request supersedes earlier no-evaluationrestriction only for a separately labeledtraining-exposed diagnostic;clean67held-outbenchmark staysunchanged. Newexperiment10,fixedC1model,no training or selection. Reuse4231savedcleanL40S outputs onlyifhardware/model/prompt/imagehashesmatch;generate2752additionalproposalanswers on12training-exposedscenes.

The80thscene23JAN27044234-P3DS-200012483678_01_P001 has0Stage1proposals atconf≥.50;sourceTIFF497×549 andSR994×1098,GTcoordinates reach1352native. Full80as-provided scorecountsits7annotationsasStage1missesmechanically (1radar,4camo,2vehicle);separatelyreport79geometry-validscores,andmarkthese7GTrows source_invalid. Do not claimthatdatum is a verifiedvisualmiss or a clean generalizationestimate. No guessedrescale or sourceedit.

Code root unversioned;notebookGit is separate. Interpreter:/sfs/envs/qwen_vl/bin/python3. GPUcurrentlyidleL40S,matchingpreviousprofile. Expected6983proposals from79scorableimages,5308GTannotationsacross80;no proposals forinvalid80thimage. No finalmetricyet.
