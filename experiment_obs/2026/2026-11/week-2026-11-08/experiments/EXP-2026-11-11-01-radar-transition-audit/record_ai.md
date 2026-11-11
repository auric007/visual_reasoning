# EXP-2026-11-11-01 — paired radar transition audit

Author: Codex. Human companion: [record.md](record.md).

Task: `RN-20261111-next-vlm-experiment` · authorized and completed 11 November 2026.

Question: on the same 119 Stage1 radar proposals, which historical B1/A7 decisions
were recovered, retained or regressed by fixed C1?

| Transition | Boxes |
|---|---:|
| Both correct | 43 |
| Recovered by C1 | 21 |
| Regressed in C1 | 15 |
| Both wrong | 40 |

| Model | Correct | Conditional recall |
|---|---:|---:|
| B1/A7 | 58/119 | 0.487 |
| C1 | 64/119 | 0.538 |

No training or inference was run. Saved predictions were joined by full scene and
proposal ID. The analyst CSV join is scene/crop-level, not exact per proposal.
Evidence: `/sfs/vlm_qwen/experiments/2026-11-11/11_radar_transition_audit/`.
