# Week of October25–31 — experiment checklist

Author: Codex. Human companion: [plan.md](plan.md).

Updated 2026-10-26T15:41:40.503217+05:30; task RN-20261026-week-start. **User clarified: do all three this week; start the VLM-versus-Stage2 comparison first.** The earlier selection-pending entry below is superseded by this clarification.

## This week's TODO

- [ ] **1. Compare VLM vs Stage2 YOLO errors — first priority.** Align permanent GT IDs and compatible scenes/taxonomy/IoU; list shared misses, unique successes, misclassifications and false positives. Saved-output discovery is starting; no new model inference is required if the outputs are complete.
- [ ] **2. Define and run a new VLM training experiment.** First settle the data/recipe change and baseline; inspect final inputs for label leakage. Training is not launched by this checklist; CUDA currently reports no available device.
- [ ] **3. Read the grounding/data-selection papers and define the paper-based experiment.** Previous reading list: arXiv2307.13702 and2510.01454. Choose a testable hypothesis before implementing or running it; these papers have not been newly read in this session.

## Time to set aside

- [ ] Reserve focused time this week to review the VLM–YOLO comparison and inspect the disagreement instances.
- [ ] Reserve time to prepare/review the next training data and agree the experiment question.
- [ ] Reserve time for the two papers, notes, and translating one idea into an experiment.

These are checklist reminders, not calendar events or automatic scheduled jobs. No durations or times have been invented.

## Earlier kickoff notes — historical

As of 2026-10-26T15:38:32.484789+05:30;taskRN-20261026-week-start. User says to startthisweek's experiment;nohumanweeklybriefexistsyet. Awaitthependingclarificationratherthanchoosingtrainingoraresearchdirectionfromoldnotes.

## Candidate starting points (not selected)

1. **Offline VLM versus Stage2 errorcomparison**, motivatedby [the humanOctober23note](/sfs/vlm_qwen/experiment_obs/2026/2026-10/week-2026-10-18/daily/2026-10-23.md). IdentifytheexactStage2baseline,alignpermanentGTIDs,thenmeasure sharedmisses,complementarycorrectcases,andfalsepositives. Keepidenticalinput/candidatecomparisonsseparatefromdifferentdetectorend-to-endcomparisons. NoGPUneededifsavedoutputsarecomplete.
2. **NewVLMtraining**:requiresastateddatachange/recipequestion;do notretrainwithoutknowingtheexperimentobjective. CUDAcurrentlyunavailable.
3. **Grounding/data-selectionpaperstudy**:theprevioushumanplanlinks2307.13702 and2510.01454. Reading/implementationchoicepending;no paperclaimedreadthissession.

Currentcheckpointbaseline and verifiedscores are in [today'snote](daily/2026-10-26_ai.md). All80diagnosticincludestraining-exposedscenes andonesource-invalidcase;clean67held-outscores stayseparate. No newexperimentallocatedor modelrunstarted.
