# EXP-2026-11-11-02 — fixed-C1 candidate/gate benchmark

Author: Codex. Human companion: [record.md](record.md).

Task: `RN-20261111-next-vlm-experiment` · authorized 11 November 2026.

Status at launch: pending in the detached queue. Fixed C1 will classify each
lowest-gate candidate once. Higher confidence gates are deterministic subsets.
The cohorts are historical clean67 Stage1 proposals and current Test116 raw
proposals after excluding 11 C1-training-overlap scenes, leaving clean105.
Current gate selection is restricted to clean Test1; Test2 is withheld from scoring
until the fusion rule is fixed. Full scene-level one-to-one TP/FP/FN accounting,
cross-class deduplication and delete-region filtering are required.

Environment: image preparation/scoring uses `/sfs/envs/yolo_models/bin/python3`;
Qwen inference uses `/sfs/envs/qwen_vl/bin/python3`. Code root is unversioned.
Evidence: `/sfs/vlm_qwen/experiments/2026-11-11/12_candidate_gate_benchmark/`.
