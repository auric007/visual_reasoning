# EXP-2026-11-11-03 — controlled target-format ablation

Author: Codex. Human companion: [record.md](record.md).

Task: `RN-20261111-next-vlm-experiment` · authorized 11 November 2026.

Question: on identical R1 examples, does full five-section CoT supervision perform
differently from direct class-only supervision?

The paired corpus has 1,960 rows per arm and 490 examples/class. Both arms share
identical neutralized images, user prompt, row order, Qwen3-VL base, text+merger
LoRA r8/alpha16, LR 1e-4, effective batch 8, two epochs and seed. Only the assistant
target differs. The original class-bearing top-left IDs are covered identically.
Both arms will be evaluated on the same fixed 256-row clean Test1 diagnostic.

Status at launch: data build complete; two-arm GPU training/evaluation pending.
Evidence: `/sfs/vlm_qwen/experiments/2026-11-11/13_target_format_ablation/`.

## Final outcome — 12 November 2026

| Arm | Accuracy | Macro-F1 | Radar F1 | Missile F1 | Other F1 | Background F1 | Non-target acceptance |
|---|---:|---:|---:|---:|---:|---:|---:|
| Full CoT | .266 | .133 | .060 | .410 | .029 | .031 | .961 |
| Class-only | .590 | .517 | .682 | .710 | .617 | .061 | .273 |

Class-only won decisively with all non-target factors controlled. Full CoT predicted
missile for most rows: missile recall 1.000, precision .258. Background remained
weak in both arms, so target length/structure is causal here but negative-data
quality is an additional limitation. Both adapters were saved successfully.
