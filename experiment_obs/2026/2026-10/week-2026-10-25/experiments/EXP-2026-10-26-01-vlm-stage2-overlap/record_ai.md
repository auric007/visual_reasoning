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


