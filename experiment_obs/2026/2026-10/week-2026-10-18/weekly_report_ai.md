# Weekly report — radar/missile verifier (VLM), week of 18 Oct 2026 — AI-authored draft

Author: AI agent (Claude), 2026-10-22, from the researcher's notes ([plan](plan.md), [20 Oct](daily/2026-10-20.md), [21 Oct](daily/2026-10-21.md),
[22 Oct](daily/2026-10-22.md), [Paper1](Paper1.md)) and the experiment reports. Human companion: [weekly_report.md](weekly_report.md).

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
