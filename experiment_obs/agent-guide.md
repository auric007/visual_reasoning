# vlm_qwen notebook instructions

Read the project-root AGENTS.md and CLAUDE.md and the shared server policy at
`/sfs/research-notebook/logging-policy.md` with its `projects.json` registry.
The canonical project root is `/sfs/vlm_qwen`; this notebook belongs only to it.

## Read and document each substantive task

Read the human and AI root plan/state, relevant knowledge, current month/week
plan/state, recent daily entries and available previous period reviews. Follow
links to original evidence; missing history is unknown, not proof of inactivity.
At start, append concise intent, cwd, authorization, stable task ID and actual
Asia/Kolkata timestamp. At milestones/end, append actual changed paths, executed
commands, tests/results, failures, uncertainty and proposed next steps. Reuse task
IDs for follow-ups. Update weekly state and other summaries when materially changed.
Never log secrets, hidden reasoning or conversations this agent cannot observe.
Honor explicit read-only requests. Report saved/committed/pushed separately.

## Human and AI files

Unsuffixed files are human-editable sources: preserve their contents. All new
agent-authored notebook content uses one lowercase `_ai` suffix before the final
extension, recursively: `plan_ai.md`, `state_ai.md`, `review_ai.md`,
`record_ai.md`, `metrics_ai.json`, `plot_ai.png`. Create an empty unsuffixed
companion only when absent; begin each AI note with authorship and a link to it.
`agent-guide.md`, AGENTS.md and CLAUDE.md are fixed-name instruction exceptions.
Read both lanes and existing mixed-author history. Do not bulk-rename old evidence.
Use [templates](templates/daily_ai.md) and the shared passive append helper.

## Calendar and actual experiments

Sunday 00:00 starts each notebook week in Asia/Kolkata; file under that Sunday's
month/year. Daily AI paths are `YYYY/YYYY-MM/week-YYYY-MM-DD/daily/YYYY-MM-DD_ai.md`.
An actual authorized experiment may use
`YYYY/YYYY-MM/week-YYYY-MM-DD/experiments/EXP-YYYY-MM-DD-NN-slug/record_ai.md`.
Allocate IDs across both lanes and all existing records; planning creates no
fictitious experiment. Keep ongoing records in their original folders.
Use the [experiment template](templates/experiment_ai.md). Record the question,
baseline/success criterion, actual code Git root/SHA/dirty state (or unversioned),
notebook revision separately, environment, data/model/config versions, seeds,
commands/times, measured units/denominators, evidence, failures and uncertainty.
Preserve the lab's test seals, split rules and existing experiment conventions.
Original research runs remain under `/sfs/vlm_qwen/experiments`; link rather than
relocate them. Never copy checkpoints, datasets, model snapshots or large outputs.

## Synthesis and execution

Put evidence-backed findings in knowledge/findings_ai.md, untested proposals in
ideas_ai.md, and decisions with reasons in decisions_ai.md. Append superseding
entries with links instead of erasing prior outcomes. Weekly/monthly reviews
compare plans with observed outcomes, failures, coverage gaps and proposed next
work; do not average incompatible metrics or count one result twice. Check closed
period reviews at the next active session without inventing missing history.

This guide is instruction, not a background recorder. Start an agent in the
project directory or explicitly ask it to load the instructions. Reading a plan
does not authorize executing experiments. No research runner is installed here.

## Transport

Notebook metadata: `/sfs/markdown-sync/git/vlm_qwen`; research code Git is separate
and currently absent at the project root. Approved company destination is
auric007/visual_reasoning, main, with public notes approved on 2026-10-19.
The dedicated wrapper uses the shared engine and project-private credentials;
the service waits 30 seconds after each cycle. The project is explicitly enrolled
in the global launcher. Check actual success timestamps and messages before
claiming delivery. Sync must publish only reviewed ordinary files inside
experiment_obs, retain the existing
credential/size/conflict/history/deletion guards, and preserve both filename lanes.

## Result-table preservation — user preference, 2026-10-23

For every experiment and small diagnostic/pilot actually performed, preserve the
small result tables shown in chat as readable Markdown in the actual day's daily
`_ai.md` and the corresponding experiment `record_ai.md`, not only dense numeric
prose or external report links. Include experiment/model/data identity, split,
measured units/denominators, confidence/IoU when relevant, TP/FP/FN and P/R/F1 where
available, recipe changes, interpretation/limits and source links. Distinguish
proposal-classification from end-to-end metrics and partial from final results.
Large per-instance/per-scene outputs may stay linked to source artifacts or an
AI-suffixed notebook report; keep a compact result table inline. Capture observed
failures and small experiments too; do not invent missing historical tables or
count multiple summaries of the same run as new experiments. Preserve human notes.
