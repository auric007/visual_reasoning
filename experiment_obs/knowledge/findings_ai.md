# Findings

Author: AI agent (Codex). Human companion: [findings.md](findings.md).

No new model finding was established by notebook setup. Prior research findings remain
in original reports indexed by [legacy evidence](../legacy/README_ai.md).
Add future findings with original evidence, comparable conditions and uncertainty;
read human findings and historical corrections before relying on a claim.

## 2026-10-19 — evidence-backed historical findings

- Level-1 GT-box CoT classification improved from sweep-01 to v2, but this was an upper-bound setting. Source: [EXP-2026-09-07-01](../2026/2026-09/week-2026-09-06/experiments/EXP-2026-09-07-01-cot-sft-v1/record_ai.md), [EXP-2026-09-14-02](../2026/2026-09/week-2026-09-13/experiments/EXP-2026-09-14-02-v2-cot-sft/record_ai.md).
- The frozen detector-box benchmark demonstrated the central end-to-end failure: absent reject labels, 94.7% non-target proposals were forced into radar/missile predictions. Source: [EXP-2026-09-21-03](../2026/2026-09/week-2026-09-20/experiments/EXP-2026-09-21-03-level2-spotter-boxes/record_ai.md).
- Analyst-reviewed positives plus explicit reject data have completed Level-1 SFT evaluation, but their detector-box result is still pending; no rejection conclusion is established yet. Source: [EXP-2026-10-11-04](../2026/2026-10/week-2026-10-11/experiments/EXP-2026-10-11-04-reviewed-reject-sft/record_ai.md), [EXP-2026-10-19-05](../2026/2026-10/week-2026-10-18/experiments/EXP-2026-10-19-05-r1-stage1-box-eval/record_ai.md).
