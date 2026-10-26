# Review of week October18–24 — completed evidence

Author: Codex. Human companion: [review.md](review.md).

Reviewcompiled2026-10-26T15:38:32.484789+05:30fromavailableoriginaloutputs andhuman/AI notes. This supplements theearlierpartialOctober22weeklyreport;it does notoverwriteit or humanhistory. Rootresearchcodeisunversioned;notebookGit is separate.

## Completed outcomes

- Experiment07early-prefixpilot:72continuationson12recipients;different-classswapanswerchanges4/12afterVisualevidence,1/12afterGrounding,same-classcontrols0/12. Diagnostic sensitivity,notproofthatanysectionisfaithfulor dispensable.
- Experiment08class-onlySFTcompleted492steps/2epochs. Balanced256-proposaldiagnosticreportedC1macroF1.553versusR1.202;dataandoutputformatbothchanged,socausecannotbeisolated. Bothmodelsoutputabout9tokensundermatchedclass-onlyquestion;no clearinference-speedbenefitwasmeasured.
- Experiment09fullcleanStage1eval:4,231proposals/67scenes;131legacyshort-IDimagecollisionsrepairedlocally;sourceunchanged. RadarFP221/missileFP344 dominateprecision. PermanentGTIDsandradar-firstgallerysaved.
- Experiment10user-authorizedall80auditfinishedOctober23exit0:6,983proposalanswers,including2,752newanswersfrom12training-exposedscenes;priorclean67scoresverifiedexactlyunchanged. Distinctall80-as-provided/79geometry-valid/clean67/exposed12scoresandIDflagsretained.

| Evaluation scope | Class | Precision | End-to-end recall | F1 | TP | FP | FN |
|---|---|---:|---:|---:|---:|---:|---:|
| All80 as provided | radar | 19.8% | 31.1% | 24.2% | 64 | 259 | 142 |
| All80 as provided | missile | 27.0% | 48.2% | 34.6% | 148 | 401 | 159 |
| Clean67 held out | radar | 19.6% | 35.5% | 25.3% | 54 | 221 | 98 |
| Clean67 held out | missile | 24.9% | 48.5% | 32.9% | 114 | 344 | 121 |

## Corrections and limits

Training-labeltextleakageandrepetitivetargetswereobserveddataissues;theircausalcontributionstoallerrorswerenotisolated. Visualtokencountimbalanceisnotameasureofwhichimagecontrolstheanswer. Different-GPUorbalanced-versus-naturalprevalencescoresare notattributionexperiments. Fine-featuretruthandradometaxonomyremainunresolved;rawradomelabelswerenotsilentlychanged. All80contains12training-exposedscenesandonesource-invalidthumbnail;do notpresentitaswhollyheld-out.

## Carry-forward tasks

HumanOctober23noteaskswhetherVLMandStage2YOLOfailonthesameinstances;permanentIDexportsarenowreadyforthatcomparison,thoughnoStage2checkpoint/outputhasbeenselectedhere. PrevioushumanplanalsolistsCoTfaithfulnessandcross-modaldata-selectionpapers;no newpaper-basedexperimenthasbeenexecuted. Thisweek's scopeawaitsuserclarification.

Sourceevidence:[experiment09](/sfs/vlm_qwen/experiments/2026-10-19/09_c1_full_stage1_eval/reports/FULL_METRICS.md),[experiment10](/sfs/vlm_qwen/experiments/2026-10-19/10_all80_inclusive_eval/reports/FULL_METRICS.md),[IDexports](/sfs/vlm_qwen/experiments/2026-10-19/10_all80_inclusive_eval/reports/comparison_ids/),[earlierpartialreport](weekly_report_ai.md),[humanplan](plan.md). Coverageislimitedtoavailablefiles;no claimthatunobservedmanualworkwaslogged.
