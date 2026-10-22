# EXP-2026-10-22-08 — class-only four-way SFT

Author: Codex. Human companion: [record.md](record.md).

Task RN-20261022-class-only-sft-train. Explicit user authorization 2026-10-22T20:42:56+05:30: start recommended training in background and estimate duration on current GPU. Original run [/sfs/vlm_qwen/experiments/2026-10-19/08_class_only_fourway_sft](/sfs/vlm_qwen/experiments/2026-10-19/08_class_only_fourway_sft); all code/data/weights remain outside notebook. No Test2 evaluation or old full-Stage1 restart authorized.

## Recipe and controls
Fresh Qwen3-VL-8B-Instruct + language/merger LoRA r8/alpha16, bf16, frozen vision blocks, same paired images. Source1764 unique records; class-balanced experiment-local manifest1968 rows/epoch (492/class). Two epochs, batch1×accum8,492 optimizer steps, AdamW LR1e-4 cosine/warmup.03,seed20261022,maxlen2048,checkpoint100steps. Class-only answer/EOS loss. Only necessary LM-head suffix logits computed; random-tensor full-loss and gradient equivalence tests passed. No quantization or input resizing introduced.

## Preflight
All3528 source JPEG references verified and SHA256 recorded; source train manifest hash matched. Exact class+EOS loss masks passed for every class and mixed-length padded batches (8–9 supervised tokens vs1195–1338 total in checked examples). Two loss/gradient tests passed. Final paired sample inspected: neutral n-hash IDs, same candidate marks in each view; pre-existing AI48-sheet review remains non-expert semantic evidence. Some source border/overlay limitations are retained, not silently repaired.

## Evaluation boundary
New background training draws from12 previously-held-out scenes explicitly embargoed by source preparation. Unfiltered historical Test1/Test2 are no longer clean benchmarks for this model. Frozen experiment-local diagnostic256 proposals (64/class,34 remaining Test1 scenes) excludes all242 source-training scenes and all12 embargo scenes. Training uses all1764 unique source rows. No new Test2 evaluation. Counts/selection hashed in [PREFLIGHT](/sfs/vlm_qwen/experiments/2026-10-19/08_class_only_fourway_sft/reports/PREFLIGHT.json). Diagnostic class balance is not deployment prevalence; underlying geometric proposal gold is not proof of annotation completeness.

## Status
Preflight complete; launching on idle NVIDIA L4 (23034MiB). No completed optimizer steps or ETA claimed until observed. [Training log](/sfs/vlm_qwen/experiments/2026-10-19/08_class_only_fourway_sft/logs/train.log), [progress](/sfs/vlm_qwen/experiments/2026-10-19/08_class_only_fourway_sft/progress.json), [config](/sfs/vlm_qwen/experiments/2026-10-19/08_class_only_fourway_sft/config.json). Actual code root unversioned; source-file hashes will be logged separately from notebook revision.

### 2026-10-22T20:54:26+05:30 — training verified; measured ETA

- Live tmux confirmed; optimizer41/492,median16.45s/update,peak allocated GPU18.08GiB. Estimated remaining training2.06h,finish around22:57IST before save overhead. Allow roughly2.25–2.5h total training,not including comparison. Finite nonzero gradients and nonzero learning rate observed after warmup; no OOM/quantization fallback.
- Trainable22,396,928 parameters:21,823,488 language +573,440 merger,zero vision-block trainables. All1764 exact processor grid budgets checked; largest1394 visual tokens plus conservative150 text tokens fits2048. Exact class/EOS masking,padded batches,CE/full-gradient equivalence and comparator parser/undefined-precision edge checks passed. An auxiliary header check initially used system Python without PIL,then the installed processor helper without its required options dict; corrected to the documented Qwen interpreter and explicit dict. Training was unaffected.
- Queued deterministic post-training workflow: save adapter,record train metrics,then evaluate final C1 and frozen R1 on the same256-proposal clean-Test1 diagnostic. No Test2,no old full-Stage1 restart,no new training sweep. R1 gets420 tokens to avoid truncation,C1 gets32;questions/pixels/GPU/greedy decoding otherwise identical. Logs/eval.log and reports/COMPARISON.md save the comparison; normal-exit hook appends outcomes to actual-date daily and this record.
- Source JSONL hash remains unchanged. Research code is unversioned; script/shared-trainer hashes and notebook revision recorded separately in CODE_MANIFEST.json.

### 2026-10-22T22:58:35+05:30 — RN-20261022-class-only-sft-train

Training completed and adapter saved. Measured train runtime8125.1753 seconds. Adapter `/sfs/vlm_qwen/experiments/2026-10-19/08_class_only_fourway_sft/runs/C1_class_only`. Starting only the frozen256-proposal Test1-clean diagnostic against R1; all training/embargo scenes excluded. No Test2 evaluation.
