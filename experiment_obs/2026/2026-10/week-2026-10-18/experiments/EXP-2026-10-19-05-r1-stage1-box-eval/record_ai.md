# EXP-2026-10-19-05-r1-stage1-box-eval — R1 four-way verifier on frozen detector boxes

Author: AI agent (Codex). Human companion: [record.md](record.md).

## Request and design

User authorized evaluation of completed R1 on Stage-1 boxes to determine whether explicit `other/background` training fixes the end-to-end false-positive collapse. The comparison is against EXP-2026-09-21-03 using the same frozen n0005 detector proposals and crop pixels.

## Setup and execution

- Status: **running**; started 2026-10-19 17:52 IST on one L40S after the GPU was attached.
- Model: `runs/R1_reviewed_reject` adapter from EXP-2026-10-11-04.
- Input set: 6,983 frozen Stage-1 proposals at confidence ≥.50, IoU match threshold .50, 79 test scenes. These scenes have zero overlap with the 148 R1 train scenes.
- Post-hoc gold distribution: radar 119, missile 249, other 3,580, background 3,035. Ground truth is not in VLM pixels or prompt; it is used only after generation for scoring.
- Pixels: reuses prior Level-2 cyan detector-target/grey detector-neighbor close+context crops without alteration.
- Execution: `run_stage1_r1.sh`; single-GPU fallback on idle L40S, resumable JSONL output. The runner supports two ≥30GB GPUs when available.

## Results and failures

No final metrics yet. At the latest observed checkpoint, 848/6,983 boxes were generated at about 9.87 s/box. This rate is an observation, not a completion estimate; inference is resumable if GPU availability changes.

Planned report views: end-to-end radar/missile P/R/F1 against all GT objects; four-way proposal classification; and rejection specificity on the 6,615 non-target proposals.

## Decision and next proposal

Do not compare the new result to the R1 positive-only four-way macro-F1 because that test has zero rejection support. Compare it to EXP-2026-09-21-03 on the same frozen Stage-1 benchmark. Evidence: [manifest](/sfs/vlm_qwen/experiments/2026-10-11/04_reviewed_reject_sft/eval/stage1_r1/MANIFEST.md), [runner log](/sfs/vlm_qwen/experiments/2026-10-11/04_reviewed_reject_sft/logs/stage1_r1_single.log), [original baseline](/sfs/vlm_qwen/experiments/2026-09-21/03_level2_spotter_boxes/reports/FINAL.md).
