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

## 2026-10-22T15:16:42+05:30 — visual-intervention audit on40 accepted recipients

Observed: paired image replacement follows the contrasting donor40/40 (only four unique donor pairs); close-only changes22/40, second-view-only25/40. Both views can influence the output under conflicting inputs, with no established global context dominance. All20 original non-target cases are still assigned radar/missile. Fixed-final-rationale top class never changes, but all supplied Synthesis passages already name the answer. Blank inputs exactly combine the background template's first four sections with the other template's Synthesis and answer.

These are selected-subset, repeated-donor observations. They do not quantify image-versus-language causal fractions or rationale faithfulness, and the wider-view test does not isolate scenery from the second target image. The early-prefix intervention requested in the human daily note remains unrun. Source: `/sfs/vlm_qwen/experiments/2026-10-21/06_visual_grounding_audit/analysis_40/DEEP_ANALYSIS.md`; [experiment record](../2026/2026-10/week-2026-10-18/experiments/EXP-2026-10-21-06-visual-grounding-audit/record_ai.md).

## 2026-10-22T17:22:53+05:30 — P0/P2 source reconciliation

Among772 INCLUDED reviewed-teacher records,128 have188 substantively changed selected fields (85 Visual evidence,41 Synthesis,31 Discrimination,18 Planning,13 Grounding). This is the final selected-text denominator, distinct from all reviewer assignments. Absence-term reductions40 versus increases7 are a lexical pattern, not a verified teacher error rate.19 fragments in12 image pairs received explicitly unblinded AI review (8 coarse supported fragments,11 unresolved); no expert hallucination percentage claimed. [Reports](/sfs/vlm_qwen/experiments/2026-10-19/07_early_prefix_grounding/offline/P2_CORRECTIONS.md).

## 2026-10-23T00:48:10+05:30 — class-only corpus/recipe comparison

On identical256 clean-Test1 proposals,C1 macro-F1.553 versus R1.202;non-target false acceptance33/128 versus128/128. This supports improved classification/rejection in this diagnostic,not a causal effect of rationale removal (data also changed). Missile precision improves with reduced recall;both models produce short outputs when asked,so no meaningful inference-speed gain measured. [Report](/sfs/vlm_qwen/experiments/2026-10-19/08_class_only_fourway_sft/reports/COMPARISON.md).
