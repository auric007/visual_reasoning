# Review — week of 25–31 October 2026

Author: Codex. Human companion: [review.md](review.md).

Reviewed on 2 November 2026 under task `RN-20261102-vlm-incomplete-audit`.

## Outcome

No VLM training or inference process is currently active, and no recent authorized run is silently waiting for completion. The only live project process observed was the notebook synchronization service.

## Completed work

- The fixed C1 all-80 audit completed all 6,983 available Stage1 proposals; the clean 67-scene result remains separate.
- C1 versus Stage2 m0001 target overlap completed on aligned permanent GT IDs. Clean 67-scene counts are 138 both correct, 30 VLM-only, 66 YOLO-only and 153 neither.
- The permanent disagreement ledger completed for the clean 67-scene and inclusive 80-scene scopes.
- The raw Stage1 tail audit clarified that `stage1_missed` at the evaluated confidence-0.50 gate can include threshold-filtered proposals.
- CPU-only C1 inference completed for recovered low-confidence boxes `18r01` and `1Br01`; both were correctly classified as radar.

## Numerically incomplete but deliberately stopped

| Experiment | Saved work | Why incomplete | Recommendation |
|---|---:|---|---|
| R1 full Stage1-box evaluation, EXP-2026-10-19-05 | 2,473 of 6,983 proposals | User stopped it after every saved prediction was radar or missile and rejection specificity remained zero. | Do not resume by default. C1 superseded it and has complete clean/all-80 evaluations. Resume only if a paper requires an exact full-R1 denominator. |
| Contrastive visual-grounding audit, EXP-2026-10-21-06 | 40 of 48 examples; 200 of 240 interventions | User explicitly accepted 40 complete balanced examples and stopped the GPU run. Offline analysis was completed. | Do not resume by default. The more targeted early-prefix follow-up later completed 72/72 continuations. |

These are preserved stopped experiments, not currently broken jobs.

## Pending experiments that were never launched

1. **Fair VLM/Stage2 benchmark and hand-off study (highest priority).** Move the VLM evaluation to the current Test116 definitions and feed it Stage2 boxes and/or lower-confidence Stage1 boxes. The two recovered radars show possible recall gain, but two selected cases do not measure the false-positive cost.
2. **False-positive overlap and deployable fusion/re-checker rule.** The existing oracle union measures target recall only. It does not count duplicate or unmatched false positives and therefore cannot establish deployable precision/F1.
3. **Next hard-negative VLM training experiment.** No new training recipe was finalized or launched. First establish the fair Stage2-box baseline, prepare Train-only hard negatives, and repeat the standing pixel/prompt leakage preflight.
4. **Paper-derived experiment.** The CoT-faithfulness and VLM-data-selection papers remain reading/design tasks; no new hypothesis-driven run was launched.

## Recommended order

Run the fair Stage2-box/lower-gate evaluation first, then build and validate a fusion rule including false positives. Only after that should new hard-negative training be considered. The stopped R1 and 48-example grounding runs are low priority and do not need completion for this path.

## Evidence checked

- Live tmux/process inventory on 2 November 2026.
- Completion and stop markers for EXP-2026-10-11-04 through EXP-2026-10-23-10.
- Exact saved row counts: R1 partial 2,473; grounding snapshot 200; early-prefix pilot 72; C1 clean 4,231; C1 all-80 6,983; recovered-box audit 2.
- Recent plans, states, daily notes, experiment records and the 29 October cross-project detailed report.

No training, inference, scoring or experiment resumption was performed by this audit.
