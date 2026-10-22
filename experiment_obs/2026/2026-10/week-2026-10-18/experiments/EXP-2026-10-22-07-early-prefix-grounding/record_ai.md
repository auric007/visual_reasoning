# EXP-2026-10-22-07 — early-prefix grounding pilot

Author: Codex. Human companion: [record.md](record.md).

Task RN-20261022-p0p2-p1. Authorized 2026-10-22T17:20:12+05:30 by explicit user approval of P0/P2 offline then P1 on GPU. This supersedes the prior proposal-only execution restriction for these tasks only. Status: offline audit completed with unresolved expert questions; GPU smoke passed; full pilot about to launch (verify live outputs).

## Question and design
Do later generated sections remain sensitive to images when only early sections are supplied?12 Test1 recipients,3/gold class. Two cut points (after Visual evidence, after Grounding), three conditions (original, verified same-class pair, verified opposite-class pair):72 planned continuations. Donor reference class is the fresh original prediction, not recipient gold. Fresh L4 baselines/donor checks; old V100 outputs only inform selection. No class-bearing Synthesis or answer supplied; early class-word leakage logged. Same prefix reprocessed with each complete image pair, no image-conditioned KV-cache reuse.

## Setup and evidence
Original run: [/sfs/vlm_qwen/experiments/2026-10-19/07_early_prefix_grounding](/sfs/vlm_qwen/experiments/2026-10-19/07_early_prefix_grounding); [README](/sfs/vlm_qwen/experiments/2026-10-19/07_early_prefix_grounding/README.md); [manifest](/sfs/vlm_qwen/experiments/2026-10-19/07_early_prefix_grounding/eval/pilot_l4/manifest.json). R1 adapter frozen. Environment `/sfs/envs/qwen_vl/bin/python3`, torch/driver/GPU metadata saved per run. Model local; no dependencies changed. Project research code is unversioned; RUN_MANIFEST.json records script hashes and notebook revision separately. Decoding greedy, bf16, SDPA, max420 generated tokens.

## Offline observed results
P0:1960 training rows,490/class;1760 unique candidates. Radar290 unique; other/background490 each but one complete target template each. Zero missing training image references and literal scene-ID overlap with Test1/Stage1. Label-bearing rejection IDs confirmed from source renderer; causal use unknown. Ten radome/other cases require taxonomy adjudication; original corpus not changed.

P2:772 included reviewed-teacher records compared to exact source;128 records/188 selected fields changed (85 Visual evidence,41 Synthesis,31 Discrimination,18 Planning,13 Grounding). Absence/negation terms decreased in40 fields/increased in7: lexical screen, not expert truth.287 sentence units inventoried;12 paired sheets inspected by AI and19 fragments reviewed (8 supported coarse fragments,11 unresolvable). Other claims remain unreviewed; this is not a faithfulness error rate.

Links: [P0](/sfs/vlm_qwen/experiments/2026-10-19/07_early_prefix_grounding/offline/P0_INTEGRITY.md), [P2 changes](/sfs/vlm_qwen/experiments/2026-10-19/07_early_prefix_grounding/offline/P2_CORRECTIONS.md), [P2 pixel review](/sfs/vlm_qwen/experiments/2026-10-19/07_early_prefix_grounding/offline/P2_VISUAL_REVIEW.md). Historical40 cases include Test2-scene proposals; no new Test2 inference. New pilot recipients/donors restricted to split=Test1.

## Verification and limits
Seven CPU tests passed, including real-data cut boundaries and Test1-only selection. GPU smoke passed: image121/1024 tokens; open early prefix processed successfully at1365 input tokens. Frozen source hashes checked unchanged. These are diagnostic sensitivity comparisons, not population accuracy or an image-versus-language causal fraction. Test2 remains excluded from new model evaluation. No new training or original-data edits.

## Execution
Command: `bash /sfs/vlm_qwen/experiments/2026-10-19/07_early_prefix_grounding/run.sh`; detached session/log will be appended once launch is observed. No inference completion claimed yet.

### 2026-10-22T17:22:53+05:30 — detached P1 execution observed

Started tmux `vlm_p1_early_prefix` at17:20:31IST. Log: `/sfs/vlm_qwen/experiments/2026-10-19/07_early_prefix_grounding/logs/pilot_l4.log`. Live inspection confirmed session active, model loaded, free-generation smoke passed and early-prefix multimodal smoke passed. Donor verification/continuations are pending; no final result claimed. New run has its own outputs and does not resume the stopped40-case audit. Seven CPU tests passed again. Exit marker `EXIT.json` and completion marker `eval/pilot_l4/COMPLETE.json` distinguish failed versus fully complete execution.
