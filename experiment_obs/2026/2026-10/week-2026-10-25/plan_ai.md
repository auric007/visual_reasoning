# Experiments for 25–31 October 2026

Author: Codex. Human companion: [plan.md](plan.md).

Updated: 26 October 2026, 15:56 IST. Task: `RN-20261026-week-start`.

We plan to work on all three items this week. Start with the VLM versus Stage2 YOLO comparison.

## This week's TODO

- [x] **Compare VLM and Stage2 YOLO target outcomes — completed.** Permanent GT IDs were aligned and correct-instance overlap was measured under a shared raw-label, IoU 0.50 rule. See [EXP-2026-10-26-01](experiments/EXP-2026-10-26-01-vlm-stage2-overlap/record_ai.md).
- [ ] **Optional continuation:** compare false-positive overlap and test a prospective fusion rule. The completed oracle-union analysis is not itself a deployable fusion result.
- [ ] **Define and run the next VLM training experiment.** Decide what to change in the data or training recipe, choose the baseline, and check the final images and prompts for label leakage before training.
- [ ] **Read the grounding and data-selection papers, then design an experiment.** Select a specific hypothesis and a way to test it before implementing the idea.

## Time to set aside

- [ ] Make time to review the VLM–YOLO comparison and inspect examples where they disagree.
- [ ] Make time to prepare and review the next training dataset and recipe.
- [ ] Make time to read the two papers and write down an experiment idea.

These are reminders. No calendar appointments have been scheduled.

## Reading list

- [Measuring Faithfulness in Chain-of-Thought Reasoning](https://arxiv.org/abs/2307.13702).
- [Data Selection for Fine-Tuning Vision Language Models via Cross Modal Alignment Trajectories](https://arxiv.org/abs/2510.01454).

## Where we are now

The previous all-80 evaluation has finished. Its metrics and permanent instance-ID exports are available in [today's log](daily/2026-10-26_ai.md).

The Stage2 baseline has been identified as `m0001_sep_w1_ensemble`, which combines YOLOv8m-OBB and YOLO11l-OBB. We have not yet computed the instance-level comparison. The next step is to locate its saved predictions and align them with the VLM results.

The first comparison can use saved results if they are complete. The project environment reported no available GPU during today's check. No new training or inference has started.

## Evaluation rules to retain

Keep the clean 67-scene results separate from the all-80 diagnostic. The all-80 result includes 12 scenes used for background training and one scene with an image/label mismatch.

Do not directly compare Stage2's P04 headline scores with the VLM scores. They use different class rules. Match the evaluation settings first.

## Decision history

- **26 October, 15:38 IST:** the new week's experiment had not yet been selected.
- **26 October, 15:41 IST:** you clarified that all three items belong on this week's TODO list, with the VLM–YOLO comparison first.

This plan responds to your [23 October comparison note](../week-2026-10-18/daily/2026-10-23.md).
