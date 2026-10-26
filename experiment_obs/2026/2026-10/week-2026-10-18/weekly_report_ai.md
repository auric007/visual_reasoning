# Weekly report — radar/missile verifier (VLM), week of 18 Oct 2026 — AI-authored draft

> **26 October update:** the earlier AI draft below was written on 22 October. Read the [review of your conclusions](#review-of-your-conclusions) appended at the end for the completed results and qualifications to causal claims. Your human-authored report is unchanged.


Author: AI agent (Claude), 2026-10-22, from the researcher's notes ([plan](plan.md), [20 Oct](daily/2026-10-20.md), [21 Oct](daily/2026-10-21.md),
[22 Oct](daily/2026-10-22.md), [Paper1](Paper1.md)) and the experiment reports. Human companion: [weekly_report.md](Projects/vlm/experiment_obs/2026/2026-10/week-2026-10-18/weekly_report.md).

---

## Why I worked on this
Our detector finds candidate objects in satellite images but often confuses radars and missiles with trucks and raises many
false alarms. I am building a **verifier**: a vision-language model (Qwen3-VL) that looks at each candidate twice — a close-up
and a wider view — and answers **radar, missile, other, or background**, with a short step-by-step explanation an analyst can
read. The previous version could only say "radar" or "missile", so it could not reject anything: on 6,983 detector boxes it
called 6,982 radar or missile.

## What I did and found
1. **Retrained on analyst-corrected explanations.** On clean radar/missile examples, the overall score rose from 0.66 to
   **0.73** (radar 0.51 → 0.61). Analyst review of the training text clearly helps.
2. **Trained the four-way verifier** (adds "other" and "background", 490 examples each; 27 h on two GPUs). On clean examples it
   is precise on radar (84%) and finds almost all missiles (96%), but still misses more than half of radars.
3. **Tested it on real detector boxes — the main problem.** In the first 2,473 boxes it **rejected nothing**: all 2,312 boxes
   that are not radar/missile were still called radar or missile. I stopped the run to find out why.
4. **Found the cause in the training data for the two rejection classes:**
   - the class name was **printed inside the training image** (e.g. "background_0397") — the answer was visible to the model;
   - **every background example had the identical explanation**, and every "other" example another fixed one, so the model
     learned a template, not what a vehicle or empty ground looks like;
   - "other" was 84% vehicles with no tanks or artillery, and radomes were counted as "other";
   - "background" was random empty ground, not the kind of false alarms the detector actually makes;
   - the wide view gives the model ~10× more image detail than the close-up (≈1,000 vs ≈110 image tokens).
5. **Checked whether the model really looks at the image** (40 examples, 200 runs with images swapped):
   - changing only the close-up changed the answer in 22/40 cases, only the wide view in 25/40 → it uses both views;
   - but changing the wide view also changed the description of the *unchanged* object (6 cases switched to "raised antenna");
   - with blank gray images it reproduced the memorised rejection text word for word, even describing a marker that wasn't there.
6. **Checked whether the final reasoning reads the image or just continues its own earlier text** (small pilot, 12 cases):
   after the model had written its visual description, swapping in an image of a different class changed the answer in only
   **4/12** cases (1/12 after the surroundings section; 0/12 with a same-class swap). Once the description is written, the
   conclusion mostly follows the text.
7. **Read a related paper** (key-concept training for medical VLMs): it weights important domain words in training — useful for
   cutting time spent on routine wording, but it does not by itself make the model look at the right place.

## Conclusion
The idea of a rejecting verifier is not disproved — **the rejection training examples were weak and leaked the answer.** The
explanations are partly a learned template, and the final answer is anchored on what the model writes first. So the next model
needs better rejection data, and each part of the explanation must be tied to what is actually in the image.

## Next steps
1. **Rebuild rejection data** (I am preparing it): real detector false alarms from training scenes, a varied "other" class
   (tanks, artillery, camouflage, radomes decided explicitly), no labels or IDs drawn in the images, and either varied
   explanations or class-only answers.
2. **Check for leakage before every training run** — inspect the final images and prompt, not just file names.
3. **Balance the two views** (resize the wide view to a similar size as the close-up) and **shorten the explanation** to cut
   training/testing time.
4. **Make every section image-based:** test generating each section from its own image/question, with a small model
   combining them into the final class.
5. **Small learning test:** 1,000 examples with uniform wording vs 1,000 diverse examples — which teaches the model better.
6. **Re-run the detector-box test** after retraining. Success = most false alarms rejected while radar/missile recall is kept.
7. **Audit analyst corrections** to list the recurring mistakes of the model that wrote the training explanations, so they don't recur.

<a id="review-of-your-conclusions"></a>

## Review of your conclusions — 26 October 2026, 16:11 IST

Author: Codex. Task: `RN-20261026-weekly-conclusion-review`. Source: your [weekly_report.md](Projects/vlm/experiment_obs/2026/2026-10/week-2026-10-18/weekly_report.md). Your note is unchanged.

**Verdict:** the sequence of work, motivation for class-only SFT, confusion matrix and proposed next steps are consistent with the saved evidence. The main corrections concern causal certainty and which examples were evaluated.

### Claim-by-claim check

| Your conclusion | Assessment | More precise wording |
|---|---|---|
| The old four-class VLM failed because other/background descriptions were repeated. | The repeated templates are confirmed; the causal explanation is not isolated. | Each rejection class used one repeated full answer: one template for other and a separate template for background. This was an observed data defect and a plausible contributor to failure. |
| The model overfitted. | Reasonable hypothesis, not an established single cause. | Blank-image interventions reproduced rejection-template text, showing template-driven behavior in that condition. This does not prove that every real-image answer ignored the pixels. |
| It answered radar or missile for all Stage1 boxes. | True for every saved answer in the stopped run; not verified for the entire available benchmark. | All 2,473 processed proposals in the stopped R1 run were labeled radar or missile. The remaining boxes were not evaluated by that run. |
| You replaced the long CoT targets with class-only SFT. | Correct. | C1 was trained to emit `<answer>CLASS</answer>`, followed by EOS. It does not require a manually written five-section explanation for each training example. |
| The class-only model still had poor precision and recall. | Fair description of remaining limitations, but incomplete as a summary of progress. | Rejection improved in the matched diagnostic, but target precision remained low on the full proposal population. |
| The confusion matrix shown is last week's result. | Every cell is correct. Its cohort needs a label. | It is C1 on 4,231 frozen Stage1 proposals from the clean 67-scene subset, pooled across Test1 and Test2, at Stage1 confidence ≥0.50 and matching polygon IoU ≥0.50. |
| Comparing the VLM with the eight-class YOLO detector is the next task. | Correct as a research objective, not a completed result. | Compare the same annotated instances and compatible class/matching rules before drawing conclusions about agreement or possible integration. |
| Cleaning the data and trying better training are next priorities. | Consistent with the evidence. | Keep them as hypotheses and planned work; their benefit has not yet been measured. |

### What I recommend adding

**1. Repeated wording was not the only observed data issue.**

The old rejection images also contained class-bearing IDs such as `other_0170` and `background_0397`. The old other pool was dominated by vehicle/smallvehicle examples and had no literal tank or artillery examples. Background candidates were random low-annotation-overlap regions rather than a sample of the detector's actual false alarms. These are documented defects or coverage limitations. Their individual causal effects have not been measured.

The neutral-ID class-only dataset changed these inputs as well as the output format. C1 used 1,764 unique examples, balanced to 1,968 rows per epoch. It started from the base Qwen model with fresh text-and-merger LoRA; it was not simply R1 with the explanation removed at inference. We therefore cannot conclude that removing CoT alone caused the improvement or that CoT is inherently worse.

**2. The class-only model did learn some rejection.**

On the same balanced 256-proposal diagnostic, R1 rejected **0 of 128** non-target proposals, while C1 rejected **95 of 128**. Macro-F1 rose from **0.202 to 0.553**. This is an observed matched-input result, not a controlled isolation of the training-data and target-format changes.

On the full clean 67-scene population, C1 rejected **3,406 of 3,941 non-target proposals (86.4%)**. The remaining **535 non-target proposals** were accepted as radar or missile. Those false alarms, together with radar/missile cross-confusions, kept target precision low.

Confusing other with background is a four-class error, but both answers still reject the candidate as a target. It is useful to report exact four-class accuracy and binary target rejection separately.

**3. Label the confusion matrix and distinguish two recall denominators.**

Your matrix is a correct **proposal-classification** matrix. Its 95 radar and 195 missile rows include only objects Stage1 found. It does not contain the 57 radar and 40 missile GT instances that Stage1 missed in those scenes.

For that clean subset:

- Radar proposal recall is **54/95 = 56.8%**; end-to-end recall is **54/152 = 35.5%**.
- Missile proposal recall is **114/195 = 58.5%**; end-to-end recall is **114/235 = 48.5%**.

The all-80 audit was completed later in the same week and should be identified as a separate scope:

| Scope | Class | Precision | End-to-end recall | F1 | TP | FP | FN |
|---|---|---:|---:|---:|---:|---:|---:|
| Clean 67 scenes | radar | 19.6% | 35.5% | 25.3% | 54 | 221 | 98 |
| Clean 67 scenes | missile | 24.9% | 48.5% | 32.9% | 114 | 344 | 121 |
| All 80, as provided | radar | 19.8% | 31.1% | 24.2% | 64 | 259 | 142 |
| All 80, as provided | missile | 27.0% | 48.2% | 34.6% | 148 | 401 | 159 |

The all-80 diagnostic includes 12 scenes used for background training. One additional scene has an image/label coordinate mismatch and no Stage1 proposals; its radar annotation is counted mechanically as a miss in the as-provided score. The 79-scene geometry-valid radar recall is **64/205 = 31.2%** instead. The clean 67-scene result remains the held-out reference.

**4. Treat the YOLO comparison as a test of complementarity.**

The planned comparison should report objects both models get right, objects both miss, and objects only one gets right. Match permanent GT IDs, coordinate spaces, class definitions and IoU settings. A separate analysis is needed for false positives that do not match any annotated instance.

Stage2's draft P04 changes some GT classes, while the VLM benchmark uses the original classes. Do not compare those headline scores directly. The comparison may show useful complementarity, but combining the models has not yet been shown to improve performance. Class-only SFT also does not establish faithful reasoning or explanation quality.

### Suggested wording you can adopt

> The previous four-class VLM showed severe rejection failure: every one of the 2,473 processed Stage1 proposals in the stopped evaluation was assigned radar or missile. The data audit found one repeated explanation per rejection class, class-bearing IDs rendered in rejection images, and limited rejection-example coverage. These were plausible contributors, but their individual effects were not isolated.
>
> We then trained a class-only SFT model using revised data and neutral image IDs. This avoided the need to author five-section CoT targets for other and background examples. Rejection improved in a matched diagnostic, but precision remained low on the full clean proposal population. Because both the dataset and the target format changed, this does not isolate the effect of removing CoT.
>
> The confusion matrix below covers 4,231 Stage1 proposals from 67 clean scenes. It measures classification of proposed boxes, not the objects Stage1 missed. The next study will compare the VLM and Stage2 YOLO on aligned GT instances to identify shared errors and complementary successes. Dataset cleanup, class definitions and a better-defined training experiment remain the next priorities.

### Evidence and checks

- [Old rejection-data audit](/sfs/vlm_qwen/experiments/2026-10-11/04_reviewed_reject_sft/reports/REJECTION_SAMPLING_AUDIT.md): repeated templates, class-bearing IDs and sampling limitations.
- [P0 integrity audit](/sfs/vlm_qwen/experiments/2026-10-19/07_early_prefix_grounding/offline/P0_INTEGRITY.md): one full target text per rejection class; source coverage.
- [Saved stopped R1 outputs](/sfs/vlm_qwen/experiments/2026-10-11/04_reviewed_reject_sft/eval/stage1_r1/preds_single.jsonl): 2,473 rows; 604 radar and 1,869 missile predictions.
- [40-example visual audit](/sfs/vlm_qwen/experiments/2026-10-21/06_visual_grounding_audit/analysis_40/DEEP_ANALYSIS.md): template recombination on blank inputs and limits of the grounding conclusions.
- [Class-only recipe](/sfs/vlm_qwen/experiments/2026-10-19/08_class_only_fourway_sft/README.md) and [matched diagnostic](/sfs/vlm_qwen/experiments/2026-10-19/08_class_only_fourway_sft/reports/COMPARISON.md).
- [Clean 67-scene metrics](/sfs/vlm_qwen/experiments/2026-10-19/09_c1_full_stage1_eval/eval/METRICS.json) and [all-80 audit](/sfs/vlm_qwen/experiments/2026-10-19/10_all80_inclusive_eval/reports/FULL_METRICS.md).

Verification: parsed all 16 numeric cells of your matrix and checked them against the clean saved confusion counts; counted every row and prediction in the stopped R1 run; checked the diagnostic rejection counts and current precision/recall values. No model inference or new experiment was run. Your original report's SHA256 remains `22fdaf7aa33cbd6109316ff8571e7f0ecb47853ea40f52e73dc6522725b761e4`.
