# EXP-2026-11-11-04 — false-positive-aware fusion

Author: Codex. Human companion: [record.md](record.md).

Task: `RN-20261111-next-vlm-experiment` · authorized 11 November 2026.

Status at launch: pending experiment 2. Detector-only, C1 agreement filtering,
C1 reclassification and detector-or-C1 union will be compared with all false
positives and duplicates included. Rule and gate are selected on clean Test1 by
radar/missile macro-F1; the frozen winner is then scored once on Test2.

Evidence: `/sfs/vlm_qwen/experiments/2026-11-11/14_fp_aware_fusion/`.

## Final outcome — 12 November 2026

Test1 selected detector-only at confidence 0.30 by radar/missile macro-F1. No C1
filter/reclassification/union policy surpassed it.

| Test2 class | GT | TP | FP | FN | Precision | Recall | F1 |
|---|---:|---:|---:|---:|---:|---:|---:|
| Radar | 144 | 65 | 17 | 79 | .793 | .451 | .575 |
| Missile | 168 | 85 | 271 | 83 | .239 | .506 | .324 |

Test2 micro-F1 was .400 and macro-F1 .450. This includes false-positive cost and
is not an oracle union.
