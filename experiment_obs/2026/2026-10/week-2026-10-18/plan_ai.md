# Week of 2026-10-18 — documentation plan

Author: AI agent (Codex). Human companion: [plan.md](plan.md).

Week runs Sunday October 18 through Saturday October 24 in Asia/Kolkata.
Establish notebook instructions, plans/state, knowledge, templates and guarded company
GitHub transport; verify routing and publication boundaries. Research work requires
its own explicit task. Add actual outcomes to daily AI notes.


## 2026-10-22 — experiment priorities for analysis

Task: **RN-20261022-experiment-priorities**. Author: Codex. Status: **proposed order only; no new experiment launched or authorized by this plan**.

Sources: [human weekly plan](plan.md), [Paper1 reading notes](Paper1.md), [October21 ideas](daily/2026-10-21.md), [October22 questions](daily/2026-10-22.md), and [completed 40-example analysis](/sfs/vlm_qwen/experiments/2026-10-21/06_visual_grounding_audit/analysis_40/DEEP_ANALYSIS.md). Paper notes motivate hypotheses; this task did not independently review or validate the papers.

### Recommendation

**First CPU work: establish trustworthy labels/overlays and review visual claims. First new GPU experiment: the early-prefix intervention (P1).** Then diagnose rejection and GT-versus-detector behavior before another training sweep. Test simpler data/target changes before changing the architecture or loss. Do not rerun the completed 40-example experiment or restart the stopped full Stage1 evaluation.

Priorities order information gained and interpretability, not an assumed accuracy improvement. P0 is a prerequisite, and P2 can proceed alongside P1. The later training ranks are provisional: revise them when those diagnostic results arrive.

| Priority | Experiment or preparation | Main question / reason for order | Cost type / dependency |
|---|---|---|---|
| P0 | Audit label mapping, neutral overlays, and evaluation coverage | Could supervision or label-bearing image text confound the next comparison? Known construction defects should not be carried into new training. | CPU + human adjudication; prerequisite for new data/training |
| P1 | Freeze early text, change image pair, regenerate later sections | Do Discrimination/Synthesis still respond to visual input before a class-bearing conclusion has been supplied? This is the user's central unanswered question. | Small GPU inference pilot; no retraining |
| P2 | Visual-claim review + analyst-correction audit | Are generated cues actually visible, contradicted, or unresolvable? Image sensitivity alone cannot establish truth. | Offline review, preferably analyst-labelled; parallel with P1 |
| P3 | Rejection/failure decomposition and train-only hard-negative proposal | Why does GT-box performance coexist with poor detector-box precision? Separate proposal misses, classification errors, and rejection errors. | Reuse saved outputs first; limited matched inference only if later approved |
| P4 | Short target versus existing five-section target | Can we remove routine wording, reduce latency, and preserve useful discrimination? Establish a cheap output baseline before more elaborate reasoning designs. | Controlled SFT; after P0 and a fixed diagnostic protocol |
| P5 | Same 1,000 images: repetitive versus varied faithful explanations | Does linguistic variety help when the image/class mix is identical? Avoid confusing better sampling with better text. | Two matched SFT arms; curated text prerequisite |
| P6 | Matched close/context visual-token budget | Does changing resolution allocation help? A large token count is not evidence of greater causal influence. | Matched preprocessing pilot, then training/inference consistency if retrained |
| P7 | Separate image/section generation, then combine | Does explicit view assignment improve factual evidence? This is a larger pipeline change with attribution and error-propagation risks. | Inference prototype first; after P1/P2/P6 |
| P8 | Concept-selective / weighted loss | Can selective supervision help beyond a concise-target baseline? Predicting vocabulary is not itself visual grounding. | Training + train-only concept dictionary; after simpler baselines |
| P9 | Apply validated audit to all trained VLMs | Which findings generalize across checkpoints? Broad comparisons are useful only after the measurement is sound. | Inference expansion; after P1/P2 protocol validated |

### P0 — integrity and evaluation contract

Observed, not hypothesized: rejection crops visibly encode `other_####`/`background_####`; each rejection class has one complete explanation template; other examples are dominated by vehicle/smallvehicle; ten raw radomes were assigned other. See [construction audit](/sfs/vlm_qwen/experiments/2026-10-11/04_reviewed_reject_sft/reports/REJECTION_SAMPLING_AUDIT.md).

Before any new training: decide whether radomes belong to radar under the intended task, make IDs neutral in a **new version**, and inventory scene/class/subtype coverage. Preserve the original training corpus and frozen intervention images as evidence. Neutral IDs cannot retroactively repair R1. A later same-image ID-removal/replacement test could measure shortcut sensitivity; an audit on seen training images would not be a held-out capability score.

Freeze a development diagnostic manifest covering all four classes, scene groups, and GT versus predicted boxes; preserve an independent generalization holdout. Report target P/R and rejection errors, not only positive-only accuracy. Zero other/background predictions mean zero recall on supported negatives; precision for an unpredicted class is undefined. No random crop is guaranteed background solely by non-overlap with annotations. Do not spend Test2 on iterative troubleshooting.

### P1 — early-prefix intervention: first new GPU study

Start with a small **8–12-case feasibility pilot**, covering both original prediction directions and correct/incorrect/rejection cases where available. This is a proposed pilot size, not a running job or population study.

1. Freeze the original generated text after Planning + Visual evidence; separately test a cut after Grounding. Do **not** include Discrimination/Synthesis or an already-written answer.
2. For each identical prefix, regenerate the remaining sections under original images versus a verified contrasting donor pair. Add a same-class donor control and free-generation controls. Record donor correctness, scene independence and reuse. Prefer more than four independent donors if available.
3. Rebuild the entire multimodal prefix for each image pair; do not reuse a cache carrying the original image representations. Keep model, GPU, prompt, decoding and limits fixed.
4. Log whether the supplied early text already names/implies a class. Report that subset separately; do not silently rewrite the prefix and call it the same experiment.
5. Compare semantic visual claims, treatment of conflicts, and final classes. If outputs change with fixed early text, later generation is image-sensitive under that intervention. If they do not, textual evidence might already suffice, or images may not overcome it; neither result yields a percentage of reasoning that is visually grounded.

Use whole-pair replacement first. Different-object close/context mixtures are attribution stress tests with no unique correct class, not ordinary evaluation images. A late prefix containing Synthesis already names the class in all40 saved cases, so the completed late-answer probe does not answer this question.

### P2 — claims and corrected-CoT review: parallel offline work

Use the saved40 cases and existing analyst edits before collecting another large run. Label atomic claims about shape, antenna, cabin, shadow and placement as **supported / contradicted / unresolvable**, identifying which image and marked object supports each claim. Keep expert judgements separate from AI impressions; blind condition/model identity when feasible.

Compare teacher versus analyst-corrected text and catalogue recurring corrections, especially false absence claims and unjustified class exclusions. Include the six fixed-close/context-swap raised-element reversals as attribution examples; these mixtures do not establish hallucination on valid same-object pairs. Measure claim correctness where adjudicable and explicitly report unresolved claims. Lexical differences and plausible wording are insufficient.

### P3 — rejection and GT-versus-Stage1 gap

Reuse saved Stage1 outputs; select a manageable scene-stratified diagnostic subset rather than restarting all6,983 proposals. Include the user's missile→vehicle cases where identifiable from the saved records. Match GT and detector-box views for the **same physical objects**, and separately inspect background/other proposals. The October5 paired-box result belongs to an older checkpoint; do not treat it as an R1 paired result.

Separate: (a) objects Stage1 never proposes, (b) wrong class even under a GT box, (c) errors introduced by proposal geometry/context, and (d) non-target proposals accepted as targets. Report confusion matrices, support, per-scene results and object-level matching; do not treat repeated overlapping crops as independent objects.

For a future rebuild, mine genuine false positives from **training scenes only**, including relevant non-target subtypes and varied background settings. Inspect for unlabelled targets and use instance-specific checked explanations or concise labels. Previously evaluated scenes must not be silently reassigned to training; reserve new scenes/candidates if overlap makes a clean split impossible. This priority proposes an auditable data repair, not evidence that it will solve rejection.

### P4–P5 — isolate output length from text diversity

P4 compares existing five-section supervision with concise factual evidence + decision on the same images/labels. Include a class-only reference if compute permits. Track per-class P/R, rejection errors, judged cue quality, generated-token count, termination and measured latency. Document whether comparisons match sample exposure or compute; do not conflate them.

P5 uses the **same** candidate set, class/scene composition, section structure, length distribution, seed and training recipe in each arm; vary only repetitive versus varied wording that expresses the same checked facts. Target1,000 unique examples per arm only if the curated corpus supports it. Paraphrase diversity must not invent visual evidence. A third instance-specific-facts arm is a separate question from surface paraphrasing. This directly addresses the user's 1,000-versus-1,000 proposal without changing sampling simultaneously.

### P6–P7 — visual allocation before pipeline redesign

For P6, count actual post-processor visual tokens rather than nominal pixels. Compare current resolution allocation with a smaller context view while retaining the close image; record any loss of visible detail. The existing 22/40 versus25/40 single-view flips do not establish context dominance. Earlier ctx512 results exist for older training; inspect those first and do not label the hypothesis untested across the whole project. A fresh R1 inference-only resize diagnoses sensitivity, not a train-matched recipe improvement.

For P7, prototype close-only Visual evidence and wider-view Grounding with explicit image identity, then combine their generated outputs using the **same model first**. Evaluate contradictory/unresolved claims and propagation into the final class. Only then introduce a separate small text LLM; changing view routing and classifier model together prevents attribution. The wider image also contains the target; it is not pure environmental context.

### P8–P9 — loss and broader model comparisons last

Read the two papers in the human plan as targeted background, not a dependency blocking P1. Treat selective-loss claims as hypotheses until checked against the actual paper. Build any concept dictionary from training answers only; compare whole-answer, concise/class-only, and concept-weighted supervision with explicit masking. Assess visual-claim truth and image interventions alongside class accuracy; rewarding domain words does not tell us their evidence source.

Once the protocol works on R1, apply it to selected older checkpoints and the base model on a common scene-disjoint subset. Reconcile different class vocabularies/prompts/overlays before comparing. Do not immediately multiply a flawed measurement across every trained model.

### What is already complete versus pending

- **Complete:** R1 rejection sampling audit; accepted40-example image audit and offline review. The stopped full Stage1 run remains partial, and older28-output exploratory interventions are not pooled with the corrected200 outputs.
- **Still open:** expert truth labels for most fine-feature claims; early-prefix continuation; causes of poor rejection; new data/target/loss/pipeline training comparisons.
- **First execution proposal:** P0/P2 offline preparation, then P1 pilot after a separate user go-ahead. This document does not launch jobs, edit datasets, or alter existing test seals.

### Execution update 2026-10-22T17:22:53+05:30

The user approved P0/P2 offline then P1. Offline checks are completed as documented, with unresolved analyst adjudications retained. P1 is now running as [EXP-2026-10-22-07](experiments/EXP-2026-10-22-07-early-prefix-grounding/record_ai.md); P3–P9 remain proposals. This supersedes the earlier proposal-only wording for P0/P2/P1.
