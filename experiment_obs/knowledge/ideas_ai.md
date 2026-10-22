# Untested ideas

Author: AI agent (Codex). Human companion: [ideas.md](ideas.md).

No new research proposal was introduced by this setup. Read the human plan and
original project reports for pending questions. Future ideas should name motivating
evidence, an expected test and success criterion; they are proposals until authorized.

## 2026-10-22T15:16:42+05:30 — pending early-prefix visual intervention

The human October22 daily note asks to freeze only early sections, substitute image content, then regenerate Discrimination/Synthesis/Answer. Existing late-answer probing does not do this. Proposed cut points: after Planning+Visual evidence and after Grounding. Use identical-prefix original/new-image controls, verified contrasting donors and free-generation controls; rebuild complete multimodal inputs rather than reusing image-conditioned caches. This is a proposal requiring the user's requested separate go-ahead and GPU availability; not executed. Motivating report: `/sfs/vlm_qwen/experiments/2026-10-21/06_visual_grounding_audit/analysis_40/DEEP_ANALYSIS.md`.

## 2026-10-22T16:42:12+05:30 — ranked weekly proposals

RN-20261022-experiment-priorities: [weekly priority plan](../2026/2026-10/week-2026-10-18/plan_ai.md) maps all ideas in the weekly plan, Paper1 and October21–22 notes. First CPU priorities are label/overlay integrity and visual-claim/analyst-correction review; first proposed GPU experiment is early-prefix continuation. Rejection diagnostics precede new training; concise targets and controlled wording precede token-budget, split-view pipeline, concept-loss and broad checkpoint comparisons. All are proposals; no new execution authorization.

## 2026-10-22T17:22:53+05:30 — early-prefix proposal authorized and started

The user approved the pending cut-point study. Test1-only P1 is now running with fresh L4 baselines and donor verification; no new result is established yet. [Experiment record](../2026/2026-10/week-2026-10-18/experiments/EXP-2026-10-22-07-early-prefix-grounding/record_ai.md).

## 2026-10-22T18:45:06+05:30 — interpret evidence-to-decision baseline before redesign

P1 uses12 recipient proposals from10 scenes, not72 independent examples. Frozen-prefix contradictions test sensitivity, not ordinary-input accuracy or proof that an early description was true. Keep the joint-image model as a comparison baseline; a future direct-answer versus concise checked-evidence+answer comparison on matched valid inputs could separate output-format value from explanation verbosity. Rationale truth and rejection/classification quality need separate evaluation. This is a proposal only, conditional on future approved data and training; no separate-LLM pipeline is presumed better. [Daily discussion](../2026/2026-10/week-2026-10-18/daily/2026-10-22_ai.md).

## 2026-10-22T18:52:45+05:30 — practical next SFT with limited manual review

### Minimal-supervision next-training proposal (not execution)

User lacks capacity to verify five sections per example and asks which text can be shortened. P1 did NOT separately ablate the five sections or measure their classification value; the4/12 versus1/12 result cannot rank section utility.

First proposed next run, once the user supplies the new other/background examples and training is authorized: standard LoRA SFT with class-only targets on reliable four-class labels, preserving the two-view input and a fixed starting checkpoint/adapter recipe. Both question and assistant target should request/contain only the class output; do not retain unverified ground-truth reasoning as an input prefix while calling the task answer-only. This removes any need to author five explanations per example. Keep image preprocessing and vision-encoder policy fixed initially to isolate the output/data question. Do not jump to GRPO or split-model generation based on P1.

Optional compact-evidence arm only where trusted existing text is available: remove Planning and duplicate Synthesis, avoid long forced class-elimination paragraphs, retain a few checked visual observations and at most one context observation when justified; permit unresolved attributes. Target roughly30–60 explanation tokens is a design budget, not a measured optimum. A class-only arm does not teach faithful explanations; compact rationale targets remain a separate capability with their own verification burden.

Compare arms on the same scene-disjoint development examples, including genuine non-target support; report per-class precision/recall, false acceptance, termination, output tokens and latency. Use the same training examples/start/seed/optimization and state whether exposure or compute is matched. Existing R1 is a reference; if the new data changes, an R1-versus-new score cannot isolate shortening as the cause. A same-data comparison requires trusted alternative targets; do not invent five-section negatives to construct a control. Test2 stays report-only and out of iterative tuning.

Output shortening should reduce generation work; training/prefill savings will be smaller because image tokens remain. No performance boost is established until measured. Supporting background: [Lanham et al., Measuring Faithfulness in Chain-of-Thought Reasoning](https://arxiv.org/abs/2307.13702) studies task-dependent CoT influence in language models; it does not validate this VLM or promise shorter targets will perform better.


## Next experiment brief — class-only four-way SFT

Status: dataset-preparation proposal, not authorization to start training. Model remains Qwen3-VL-8B-Instruct with the existing text+merger LoRA recipe and frozen vision blocks; two-view input stays fixed. Train the model to emit only `<answer>CLASS</answer>`; no Planning, Visual evidence, Grounding, Discrimination or Synthesis target is required. This is a classification baseline, not evidence of faithful reasoning.

For each example supply: unique neutral ID; source scene/site ID; close and context images showing the SAME clearly marked candidate; one accepted answer among radar/missile/other/background. Minimal metadata example: `{"id":"sample_001","site":"scene_A","images":["images/sample_001_det.jpg","images/sample_001_ctx.jpg"],"answer":"other"}`. The builder can create the prompt/messages; no manual question or rationale authoring needed. Both views use neutral markings without target-class text. Preserve existing explanations only as optional provenance.

For preparation, distinguish identifiable non-target objects (other) from empty ground/texture/clutter with no identifiable foreground object (background); flag uncertain cases separately instead of forcing a rejection label. Provide reliable unique examples from varied scenes rather than repeated overlapping crops to inflate counts. No mandatory quota was set. Keep source scene IDs so training/development remain disjoint; existing held-out Test1/Test2 sources must not enter training. Next generalization reports require non-target support; positive-only scores cannot assess rejection.

Once data is supplied and training approved, inspect final pixels/prompts as the standing preflight, construct class-only targets and compare the new model against frozen R1 on identical suitable held-out inputs: per-class precision/recall, non-target acceptance rate, output length and latency. Keep Test2 out of iterative selection. Because the data also changes, this comparison does not isolate output shortening as the cause of any gain. No data or model changes were executed for this brief.

Recorded 2026-10-22T19:07:17+05:30; task RN-20261022-next-sft-design.
