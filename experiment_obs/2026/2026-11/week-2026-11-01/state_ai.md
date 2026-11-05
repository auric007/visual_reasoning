# Research state — week of 1–7 November 2026

Author: Codex. Human companion: [state.md](state.md).

Updated: 2 November 2026. Task: `RN-20261102-vlm-incomplete-audit`.

## Current status

- No VLM training or inference job is active.
- Recent C1 training/evaluation, grounding follow-up, all-80 audit, VLM/YOLO target overlap, instance ledger and recovered-box classification are complete.
- The historical R1 full Stage1 evaluation and 48-example contrastive grounding run were explicitly stopped by the researcher and should not resume automatically.

## Recommended next experiment

Evaluate fixed C1 on current Stage2/Test116 candidate boxes and/or a lower Stage1 confidence gate using aligned classes, IDs and IoU. Measure false positives as well as recovered targets. This is required before a deployable VLM/YOLO fusion rule or another hard-negative training run can be judged.

## Other pending work

- False-positive-aware fusion/re-checker rule.
- Train-only hard-negative dataset and new VLM training, conditional on the fair baseline and leakage preflight.
- CoT-faithfulness and VLM-data-selection paper study translated into one testable experiment.

[Audit details](../../2026-10/week-2026-10-25/review_ai.md) · [Daily evidence](daily/2026-11-02_ai.md).

## Client on-premises handover planning — 5 November 2026

- A consolidated client intake, data/annotation contract, infrastructure checklist, pilot evidence plan and acceptance-gate document is saved at `/sfs/end_to_end/docs/CLIENT_RESEARCH_READINESS_REQUIREMENTS.md`.
- C1 client sizing must use candidate density and natural class prevalence, not km² alone. Final acceptance still requires current Stage2/Test116 candidates, final-GPU-family qualification and a full C1 + HYBRID-v2 + fusion benchmark.
- This update is documentation only; no VLM training, inference or corpus change occurred.

[Daily evidence](daily/2026-11-05_ai.md).
