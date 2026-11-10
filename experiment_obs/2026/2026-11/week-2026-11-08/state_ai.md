# Research state — week of 8–14 November 2026

Author: Codex. Human companion: [state.md](state.md).

Updated: 10 November 2026. Task: `RN-20261110-vlm-recap`.

## Where the project is

- Current artifact: Qwen3-VL-8B-Instruct plus four-way class-only C1 LoRA.
- C1 training, clean67 evaluation, all80 diagnostic, grounding follow-up,
  C1-versus-YOLO target overlap, permanent disagreement ledgers and the selected
  low-confidence-box audit are complete.
- No VLM training or inference job is active. Two older partial runs were intentionally
  stopped and should not be resumed automatically.

## Next priority

Run a fair fixed-C1 evaluation on the current Stage2/Test116 candidates and/or a
pre-registered lower Stage1 gate, including the false-positive cost. Then evaluate a
deployable fusion/re-checker rule. New hard-negative training should follow only if
that benchmark shows classification/rejection remains the bottleneck.

## Secondary work

- Finish the two recent paper notes and define one controlled paper-derived study.
- Preserve clean67 as the held-out comparison; keep all80 labeled as diagnostic because
  it includes training-exposed scenes and one invalid source case.

[Daily recap](daily/2026-11-10_ai.md).

