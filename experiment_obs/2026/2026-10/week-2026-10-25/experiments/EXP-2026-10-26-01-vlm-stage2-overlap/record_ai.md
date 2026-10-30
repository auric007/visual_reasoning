# EXP-2026-10-26-01 — C1 VLM versus m0001 YOLO overlap

Author: Codex. Human companion: [record.md](record.md).

Status: completed on 26 October 2026, 20:19 IST. Task: `RN-20261026-vlm-stage2-overlap`. Correlation: `RN-20261026-week-start`.

## Question

On the same radar and missile GT instances, how much do the latest four-class class-only VLM and deployable Stage2 YOLO agree, and how often is only one system correct?

## Compared systems

- VLM: Qwen3-VL-8B-Instruct with the completed `C1_class_only` adapter.
- YOLO: Stage2 `m0001_sep_w1_ensemble` deployment output, combining YOLOv8m-OBB and YOLO11l-OBB.
- No training, inference, threshold tuning or model selection was run. Existing saved outputs were rematched under one common rule.

## Common protocol

- Primary cohort: 67 geometry-valid scenes excluded from VLM background training.
- Targets: 152 radar and 235 missile GT instances, using permanent GT IDs and raw target classes.
- Matching: m0001 predictions sorted by score and assigned class-agnostically, one-to-one, to the highest-IoU unmatched object among all 5,308 raw GT annotations.
- Primary IoU: 0.50, matching the VLM benchmark. IoU 0.30 is a sensitivity check.
- Correct means that an assigned prediction has the exact raw radar or missile class.
- VLM outcomes are the saved permanent-ID results. The VLM uses separate frozen Stage1 proposals, so this is an end-to-end correctness comparison rather than an identical-box classifier comparison.

## Primary results — clean 67 scenes, IoU 0.50

| Class | GT | Both correct | VLM only | YOLO only | Neither | VLM correct | YOLO correct | Oracle union |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| Radar | 152 | 46 | 8 | 35 | 63 | 54 | 81 | 89 |
| Missile | 235 | 92 | 22 | 31 | 90 | 114 | 123 | 145 |
| **Combined** | **387** | **138** | **30** | **66** | **153** | **168** | **204** | **234** |

The correct-set Jaccard overlap is 0.590. Of 168 VLM-correct targets, 138 (82.1%) are also correct for YOLO. YOLO uniquely recovers 66 targets and the VLM uniquely recovers 30. YOLO corrects 30.1% of VLM errors; the VLM corrects 16.4% of YOLO errors.

The oracle union would increase target recall from 52.7% for YOLO alone to 60.5%. This is only an analysis ceiling: it assumes perfect knowledge of which system is right and does not measure extra false positives from a real fusion rule.

## Origin of unique successes

| Class | YOLO-only from VLM Stage1 miss | YOLO-only from VLM misclassification | VLM-only from YOLO no box | VLM-only from YOLO wrong class |
|---|---:|---:|---:|---:|
| Radar | 20 | 15 | 4 | 4 |
| Missile | 7 | 24 | 11 | 11 |

Radar is mainly a YOLO advantage. Missile shows more balanced complementarity. Among YOLO's remaining errors, radar is dominated by no matched box (48) and vehicle confusion (16); missile is split between no matched box (41) and vehicle confusion (47), with smaller arty, radar, logistic and camo confusions.

## IoU 0.30 sensitivity — same clean scenes

| Class | GT | Both correct | VLM only | YOLO only | Neither | VLM correct | YOLO correct | Oracle union |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| Radar | 152 | 50 | 4 | 46 | 52 | 54 | 96 | 100 |
| Missile | 235 | 94 | 20 | 31 | 90 | 114 | 125 | 145 |
| **Combined** | **387** | **144** | **24** | **77** | **142** | **168** | **221** | **245** |

## All-80 diagnostic at IoU 0.50

| Class | GT | Both correct | VLM only | YOLO only | Neither | VLM correct | YOLO correct | Oracle union |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| Radar | 206 | 53 | 11 | 44 | 98 | 64 | 97 | 108 |
| Missile | 307 | 121 | 27 | 37 | 122 | 148 | 158 | 185 |
| **Combined** | **513** | **174** | **38** | **81** | **220** | **212** | **255** | **293** |

This inclusive table is diagnostic because 12 scenes were used for VLM background training and one scene has invalid image/label geometry.

## Artifacts and execution

- Full report: `/sfs/vlm_qwen/artifacts/EXP-2026-10-26-01-vlm-stage2-overlap/reports/OVERLAP_REPORT.md`.
- Machine-readable aggregate results: `/sfs/vlm_qwen/artifacts/EXP-2026-10-26-01-vlm-stage2-overlap/reports/overlap_metrics.json`.
- Reproducible script: `/sfs/vlm_qwen/artifacts/EXP-2026-10-26-01-vlm-stage2-overlap/code/compare_overlap.py`.
- Environment: `/sfs/envs/tide/bin/python3`.
- Command: `/sfs/envs/tide/bin/python3 /sfs/vlm_qwen/artifacts/EXP-2026-10-26-01-vlm-stage2-overlap/code/compare_overlap.py`.
- VLM project root: unversioned. Stage2 code HEAD: `e5af44c4bcc6763cb5031887bc9c56b071ad4508`; its dirty state was pre-existing and untouched.

## Verification

The script compiles. All overlap partitions sum to their support, correct-set identities hold, known VLM totals reproduce exactly, input hashes match, all 513 VLM target IDs resolve to Stage2 geometry, and both source manifests contain the same 80 scene names. The final report SHA-256 is `ce259c7dd3b18acfaa2a5912450ef3415402fdde01a1a4c0ada88a36095eae36`; the JSON SHA-256 is `66fbcff0ced6162b405d9a30fa1cdab686cc74072ce41a934d7a80253db722a4`.

## Conclusion and limits

YOLO is stronger overall and particularly on radar. The VLM's correct instances are mostly a subset of YOLO's, but 30 clean-cohort targets are uniquely correct for the VLM, including 22 missiles. This is real complementarity in saved outcomes, but no deployable fusion benefit is established. False-positive overlap and a prospective fusion rule remain untested.

## 28 October 2026, 00:30 IST — permanent unique-success ledger

The researcher requested every instance behind the VLM-only and YOLO-only counts, including whether a YOLO-only target never reached the VLM or reached it and was misclassified. The analysis script now writes:

- `/sfs/vlm_qwen/artifacts/EXP-2026-10-26-01-vlm-stage2-overlap/reports/INSTANCE_LEDGER.md`: readable tables containing every unique-success ID.
- `INSTANCE_LEDGER_CLEAN67.csv`: 96 held-out unique-success rows.
- `INSTANCE_LEDGER_ALL80.csv`: 119 rows, retaining training-exposure and source-validity flags.

### Clean 67-scene categories

| Category | Radar | Missile | Total |
|---|---:|---:|---:|
| VLM correct; YOLO has no matched box | 4 | 11 | 15 |
| VLM correct; YOLO assigns wrong class | 4 | 11 | 15 |
| YOLO correct; no Stage1 box reached VLM | 20 | 7 | 27 |
| YOLO correct; box reached VLM but VLM misclassified | 15 | 24 | 39 |
| **Total** | **43** | **53** | **96** |

For the 39 cases that reached the VLM but were wrong: 20 missiles became `other`, 4 missiles became `radar`, 7 radars became `other`, and 8 radars became `missile`. For the 15 VLM-only cases where YOLO assigned a wrong class, YOLO predicted vehicle 7 times, radar 3, missile 2, and arty/camo/logistic once each.

The ledger records GT ID, scene, split, class, category, clean eligibility, training exposure, geometry validity, VLM reachability/status/prediction/proposal ID and YOLO status/prediction/score/IoU. Validation passed for syntax, row counts, unique IDs, clean flags, category semantics, VLM reachability and JSON metadata. Output hashes:

- `INSTANCE_LEDGER.md`: `8105f04b3879ffcc4db89e13fcb578a4c55cc9ec682c70174c1f5706bba606c9`
- `INSTANCE_LEDGER_CLEAN67.csv`: `1c4fbb574826e69ccb3029581df355b3e35dd08894cb375f8d198026e52eba49`
- `INSTANCE_LEDGER_ALL80.csv`: `4d8d8581001019e9e020d00a6bd8152b30a8317f4ffcbb999e90d950bdf4e582`

### All-80 unique-success categories

| Category | Radar | Missile | Total |
|---|---:|---:|---:|
| VLM correct; YOLO has no matched box | 6 | 12 | 18 |
| VLM correct; YOLO assigns wrong class | 5 | 15 | 20 |
| YOLO correct; no Stage1 box reached VLM | 24 | 11 | 35 |
| YOLO correct; box reached VLM but VLM misclassified | 20 | 26 | 46 |
| **Total** | **55** | **64** | **119** |

Thus the inclusive 80-scene diagnostic contains 38 VLM-only successes and 81 YOLO-only successes. Of the 81 YOLO-only targets, 46 reached the VLM and were misclassified, while 35 never reached it because Stage1 supplied no matching proposal. Twenty-three of these 119 disagreement rows come from VLM-training-exposed scenes, so this table is diagnostic rather than a clean held-out estimate. No source-invalid target appears among the 119 disagreement rows.

## 30 October 2026 — clarification of `stage1_missed`

A raw-tail audit showed that the status means no qualifying Stage1 box at the Level-2 operating threshold (confidence >= 0.50), not necessarily no raw detection at any confidence. Among three queried radar IDs, `18r01` had a confidence-0.1765 box at IoU 0.5460 and `1Br01` had a confidence-0.2472 box at IoU 0.6838; both were filtered before VLM inference. `08r02` had no overlapping prediction even in the saved confidence >= 0.001 tail; its nearest candidate had zero IoU and a 7.61-pixel edge separation. The permanent outcome remains `stage1_missed` under the evaluated pipeline, but the causal subtype is threshold-filtered for `18r01`/`1Br01` and true raw proposal miss for `08r02`.

### Recovered-box VLM audit queued

The fixed C1 four-class checkpoint will classify the exact recovered `18r01` and `1Br01` candidates using the evaluated close/context format. Reproducible code, manifest, metadata and verified views are under `artifacts/EXP-2026-10-26-01-vlm-stage2-overlap/low_conf_vlm_audit/`. The detached session `vlm_lowconf_two_box_audit` is waiting for the currently occupied GPU; no result is claimed until `RESULTS.md` exists.

### Recovered-box C1 result

At the researcher's request, the waiting GPU queue was cancelled and the two-row diagnostic completed on CPU only (`CUDA_VISIBLE_DEVICES=-1`, BF16, greedy, 32 threads). C1 returned `<answer>radar</answer>` for both radar GTs: `18r01` (Stage1 confidence 0.1765, IoU 0.5460, 52.7 seconds) and `1Br01` (confidence 0.2472, IoU 0.6838, 9.9 seconds). Thus both were recoverable classifier true positives if their low-confidence boxes were forwarded. This selected-case result does not measure global false-positive inflation from lowering the Stage1 threshold.


