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

First run an offline paired radar transition audit between B1/A7 and C1 on the same
119 Stage1 radar boxes. Identify recovered, persistent and regressed instances and
join analyst radar attributes. This resolves whether C1 changed the historical
radar shortcut and requires no GPU.

Then run a fair fixed-C1 evaluation on the current Stage2/Test116 candidates and/or
a pre-registered lower Stage1 gate, including the false-positive and candidate-cost
impact. After that, evaluate a deployable fusion/re-checker rule. New hard-negative
training should follow only if that benchmark shows classification/rejection remains
the bottleneck.

Readiness audit on 11 November found the L40S idle and all inputs for experiments
1–4 available, although experiments 2–3 require new manifests/scripts before their
runs. Experiments 5–6 remain intentionally gated: hard negatives depend on earlier
outputs, and the paper-derived experiment lacks a defined hypothesis. Nothing was
launched by the audit. Estimated elapsed time is 13–22 hours for experiments 1–4,
or 21–36 hours if a reviewed experiment 5 is later authorized.

## Update — 11 November 2026, 20:32 IST

The researcher authorized and launched the staged queue. Experiment 1 is complete:
C1 recovered 21 B1 errors, regressed on 15 and improved paired radar correctness
from 58/119 to 64/119. Experiments 2–4 now have isolated resumable scripts; experiment
5 is constrained to a nontrainable review manifest and a hard stop before retraining.
Experiment 6 remains unqueued. Runtime status is authoritative in
`/sfs/vlm_qwen/experiments/2026-11-11/QUEUE_11_15/state/status.json`.

## Update — 12 November 2026, 02:43 IST

Experiment-2 preparation is complete: 45,501 candidates and 91,002 images passed
integrity checks. A post-write JSON summary error stopped the first queue; it was
fixed without rebuilding data. The detached queue resumed fixed-C1 inference on
the L40S. First checkpoint rate was 1.973 rows/s, giving 6.39 hours for that
inference stage and approximately 13–17 hours for the remaining full queue.

## Secondary work

- Finish the two recent paper notes and define one controlled paper-derived study.
- Preserve clean67 as the held-out comparison; keep all80 labeled as diagnostic because
  it includes training-exposed scenes and one invalid source case.

[Daily recap](daily/2026-11-10_ai.md).

