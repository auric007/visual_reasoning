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
