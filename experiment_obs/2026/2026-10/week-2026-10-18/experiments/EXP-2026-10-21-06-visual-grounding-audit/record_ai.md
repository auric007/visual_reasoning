# EXP-2026-10-21-06-visual-grounding-audit — Does R1 use image evidence or language momentum?

Author: AI agent (Codex). Human companion: [record.md](record.md).

## Request and design

User asked whether visual-evidence and grounding text produced by Qwen3-VL R1 reflects its paired images or is mainly autoregressive continuation from prior text. The study uses the stopped, saved Stage-1 R1 subset. It does not change training, data, or the frozen benchmark.

Two complementary probes are planned:

1. **Free-decoding visual interventions.** Hold prompt and decoding fixed while using original paired images, swapped candidate images, close-crop-only evidence, context-only evidence, and neutral visual input. Measure answer flips and save paired rationales for inspection.
2. **Fixed-rationale answer probe.** Hold the original generated CoT prefix fixed through `<answer>` while changing images, then compare class-token likelihoods. This distinguishes direct image influence on the final answer token from influence already encoded into the earlier generated text.

The audit is stratified by post-hoc gold class from saved Stage-1 predictions, uses a deterministic seed, and keeps all raw generations and per-condition scores. It can demonstrate sensitivity to visual input; it cannot prove a human-style causal explanation.

## Setup and execution

Status: **preparing**. Source predictions: `/sfs/vlm_qwen/experiments/2026-10-11/04_reviewed_reject_sft/eval/stage1_r1/preds_single.jsonl`. Model: completed `R1_reviewed_reject` adapter. Original full evaluation remains stopped by user and will not be resumed.

## Results and failures

Pending.

## Decision and next proposal

Report answer stability, rationale similarity, per-class intervention effects, and fixed-prefix class-token shifts before interpreting any generated visual cue as grounded.

## 2026-10-21 — implementation and execution

- Script: `/sfs/vlm_qwen/experiments/2026-10-21/06_visual_grounding_audit/scripts/visual_grounding_audit.py`.
- Run wrapper: `run.sh`, tmux session `vlm_r1_visual_audit`.
- Environment: `/sfs/envs/qwen_vl/bin/python3`; source model `/sfs/vlm_qwen/global_qwen/models/Qwen3-VL-8B-Instruct`; adapter `R1_reviewed_reject`.
- Inputs are frozen partial Stage-1 predictions (`preds_single.jsonl`) and their immutable input manifest. The full Stage-1 inference was not resumed.
- Passed `python -m py_compile`, `bash -n`, and `--prepare-only` (48 balanced rows) before launch. The run stores every completed image-condition output immediately and skips it on restart.
- Pending observed outcome: `eval/r1_stage1_visual_audit/SUMMARY.md` once all 240 interventions finish.
- At 2026-10-21T14:42:54+05:30 the process was alive after loading but before its first durable row, with Torch Inductor compile workers active. No outcome is yet available.
- Initial full launch then failed before the first record because manual concatenation invalidated Qwen's multimodal RoPE position tensors. The probe now rebuilds the assistant-prefix input with the processor. Syntax validation passed; a minimal GPU smoke test is running before the full audit is restarted.
- Repaired 4-row/16-token smoke completed in 6m19s. A one-row full-length timing calibration is now running; its result will determine whether the planned 240-condition audit needs a throughput optimization before restart.

## 2026-10-21T18:25:12+05:30 — full audit restarted

The initial full job had not been restarted after calibration. Fixed the probe to end at the OPEN answer prefix instead of the chat end marker; old calibration probabilities are invalid for this probe. All five processor input checks and syntax checks passed. The 240-intervention run was relaunched in `vlm_r1_visual_audit`; results remain pending. See today's daily note for exact changes and original evidence paths.

## 2026-10-21T19:10:06+05:30 — preliminary first-23 results

Five gold-radar originals all predicted missile. Real-image swap decisions stayed missile; gray-both changed 4/4 to other. The late-prefix top preference did not change. This is class-ordered, small, and confounded by radar-to-missile donor direction; no general grounding verdict. Snapshot: `/sfs/vlm_qwen/experiments/2026-10-21/06_visual_grounding_audit/reports/PRELIMINARY_FIRST23.md`. Full results pending.

### 2026-10-21T19:22:30+05:30 — RN-20261021-visual-grounding: user-corrected donor protocol

- User correctly identified a design failure: donors chosen by recipient gold class can share the model's existing prediction, making unchanged answers uninformative. Stopped only `vlm_r1_visual_audit` at 28 saved interventions; outputs are preserved and first-23 report marked superseded/exploratory. Earlier unchanged-answer observations do not establish image blindness.
- Built `scripts/contrastive_audit.py` and `run_contrastive.sh`. Frozen 48 recipients remain unchanged and are interleaved across classes. Donors are drawn from historical correct examples outside this subset (20 radar, 93 missile candidates), checked again on the same GPU, and must be from another scene with a class differing from the recipient's current prediction. Current donor coverage is radar/missile only; do not claim confidence calibration or correct other/background anchors.
- The free-decoding and fixed-current-rationale probes remain separate. Every new result stores donor gold, historical prediction, fresh verified prediction and image paths. Full paired swaps have donor expectations; mixed single-image swaps have no unique gold class. Summaries distinguish these and report section text changes without claiming factual grounding.
- Passed Python/shell syntax; donor-selection fixtures rejecting incorrect/same-prediction/same-scene donors; strict complete-answer parsing; section extraction; real-data prepare-only; identical prompts, 48 unique unchanged recipient IDs, interleaved order and existing input files.
- Launched corrected background run in tmux `vlm_r1_contrastive_audit` on idle V100. It is verifying donors before recipient interventions. Outputs `/sfs/vlm_qwen/experiments/2026-10-21/06_visual_grounding_audit/eval/contrastive_verified/`; logs `/sfs/vlm_qwen/experiments/2026-10-21/06_visual_grounding_audit/logs/contrastive.log`. No training or stopped full Stage-1 resume. The earlier ETA is superseded by this revised run; completion remains pending.

## 2026-10-21T19:38:23+05:30 — related training-data investigation

User requested other/background sampling and diversity analysis while image interventions continue. Confirmed class-bearing rendered IDs in rejection crops, one fixed answer per rejection class, class-biased other sampling and sorted-scene-biased background sampling. These are observed dataset construction issues; causal effects remain untested. See `/sfs/vlm_qwen/experiments/2026-10-11/04_reviewed_reject_sft/reports/REJECTION_SAMPLING_AUDIT.md` and today's daily note. No model/data modifications or additional training.

### 2026-10-21T20:26:11+05:30 — RN-20261021-visual-grounding: first six corrected recipients

- User requested conclusions from the six complete examples. Paired results across 30 interventions: all original answers missile; both-image replacements switch 6/6 to their verified radar donor; detail-only changes3/6, context-only changes3/6, gray-both changes6/6 to other. Only TWO unique radar donors are reused, so full-pair results are not six independent donor tests. Original gold is radar2/missile2/other1/background1; only missile→radar replacement direction is represented so far.
- Visual evidence and Grounding text changed for every altered condition (0/6 identical per section per condition). Example21DEC27025_0012 changes its claim about a raised element despite the same close view when only context changes. This shows contextual influence on candidate descriptions, not proof that either claim is correct.
- Under fixed original rationale, late first-token top class stays missile for every condition in all six examples. Supported interpretation: visual input affects free generation, while supplied conclusion-bearing prior text strongly constrains the late answer preference. Not proof that earlier reasoning ignored pixels or that rationale claims are faithful.
- Snapshot `/sfs/vlm_qwen/experiments/2026-10-21/06_visual_grounding_audit/reports/CONTRASTIVE_FIRST6.md`. Existing run unchanged; findings remain preliminary.

### 2026-10-22T01:39:00+05:30 — RN-20261021-visual-grounding: stopped by user; 40-example snapshot preserved

- User accepted 40 complete examples for analysis and is turning off the GPU. Stopped only tmux `vlm_r1_contrastive_audit`. The run was intentionally stopped at 200 saved interventions across 40 complete examples, not completed to the original 240 target. Gold composition: {'radar': 10, 'missile': 10, 'other': 10, 'background': 10}. Do not resume without a new request.
- Verified every retained example has all five distinct conditions and recipient/donor image references exist. Saved frozen `interventions_40_complete.jsonl` (raw outputs, section texts, pair metadata and late-prefix scores), `COMPLETE_EXAMPLES.json` (image paths and pair ledger), `SUMMARY_40_COMPLETE.md`, and `STOPPED_BY_USER.json` in `/sfs/vlm_qwen/experiments/2026-10-21/06_visual_grounding_audit/eval/contrastive_verified`. Original outputs, baselines, donor checks and logs remain preserved. Offline analysis requires no GPU.
- Snapshot SHA256: `fdf3378b08833f27c1b8b569439f75fe3073815c632a55464211ce2180e177ba`. No training, data changes or unrelated job termination.

### 2026-10-22T15:16:42+05:30 — RN-20261021-visual-grounding: all-40 offline analysis completed

- Completed CPU analysis of the accepted frozen snapshot:40 recipients/200 outputs,10 per gold class,18 recipient scenes,four unique verified donor pairs. No new inference, API use or training; stopped experiment remains stopped. Main evidence: `/sfs/vlm_qwen/experiments/2026-10-21/06_visual_grounding_audit/analysis_40/DEEP_ANALYSIS.md`; per-case review `CASE_REVIEWS.md`; image/text browser `review.html`; `decisions_40.png`; metrics, case CSV and validation JSON.
- Free generation: both-image replacements follow donor40/40 but produce only FOUR unique responses because the four donor pairs are reused. Close-only changes22/40, second-view-only25/40; overlap18 either-alone,4 close-only,7 context-only,11 both-needed. The wider image contains the candidate as well as surroundings, and mixed pairs violate the same-object premise; these are sensitivity results, not background-only or accuracy comparisons.
- Original predictions:34 missile/6 radar;12/40 correct in this balanced diagnostic subset. All20 other/background examples receive a target label. These are subset observations, not the complete benchmark.
- All altered Visual evidence and Grounding sections differ from original text. Original wording contains no-cabin-separation40/40 and no-raised-element36/40. Six second-view replacements reverse the raised-element claim while retaining the original close view. Fine-feature truth is mostly unresolved by the image scale, not scored as false merely because labels differ.
- Fixed-original-rationale next-class-token preference changes0/40 for every condition. All40 supplied Synthesis sections already name their final answer, so this is late label-continuation evidence, not a test of sections4–5 after an early prefix. The human-note mid-generation cut-point experiment is still NOT run and requires the requested separate go-ahead.
- Gray inputs yield one identical full response40/40. First four sections exactly match the background training template; Synthesis+answer match other. This is observed blank-input template recombination, not proof of the same mechanism on every real image.
- Reviewed all40 original close/context pairs and four donor pairs via ten contact sheets/four donor sheets, with nearest-neighbor target zooms for inspection only. Saved40 explicitly unblinded AI visual notes, not expert ground truth. One explicit own-class exclusion contradiction was detected (18MAY28024_0005), and one image-axis claim mismatches the rendered cyan target (141d9464_D_0002). No overall hallucination/faithfulness rate is claimed.
- Validation passed: frozen SHA256 unchanged; unique200 condition records; all40 complete condition sets; all complete tags/sections; verified contrasting/different-scene donors; image refs; overlap accounting; template comparisons;40 gallery cards and review entries; links. Hashed88 source image files. Reproducible scripts and `ANALYSIS_MANIFEST.json` saved outside notebook; no code Git is present at project root.
