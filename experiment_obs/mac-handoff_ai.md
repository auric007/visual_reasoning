# Mac handoff — visual_reasoning

Author: AI agent (Codex). Human companion: [mac-handoff.md](mac-handoff.md).

Company repo: https://github.com/auric007/visual_reasoning.git, branch main.
Server notebook: `/sfs/vlm_qwen/experiment_obs`.
Recommended laptop destination:
`/Users/ashutosh.bharti/Documents/Obsidian Vault/Projects/visual_reasoning`.

For a NEW destination only, from the Mac Terminal:

```bash
git clone --filter=blob:none --no-checkout --branch main https://auric007@github.com/auric007/visual_reasoning.git "/Users/ashutosh.bharti/Documents/Obsidian Vault/Projects/visual_reasoning"
cd "/Users/ashutosh.bharti/Documents/Obsidian Vault/Projects/visual_reasoning"
git sparse-checkout set --no-cone '/experiment_obs/'
git checkout main
git config credential.useHttpPath true
git config user.name "Ashutosh Bharti"
git config user.email "ashutosh.bharti@auricai.in"
```

Use the company account credential on this Mac when prompted; never put a PAT
in a URL or tracked file. If the target already exists, inspect/preserve it first.
This keeps the whole notebook, including nested human and AI files, while excluding
research code from the visible checkout. Sparse checkout does not limit what an
incorrect push could publish; keep the existing guarded notebook sync workflow.

Open `experiment_obs/README_ai.md` in Obsidian. Human plans go in unsuffixed files;
agent responses go in their `_ai` counterparts. A pull command for this checkout is:

```bash
git -C "/Users/ashutosh.bharti/Documents/Obsidian Vault/Projects/visual_reasoning" pull --ff-only origin main
```

Add this checkout explicitly to the Mac's existing sync project list if desired.
The server cannot configure or verify the Mac scheduler from this session.
Server timing uses a 30-second wait after each completed cycle; simultaneous edits
may block safely and require review. Never force overwrite or execute a pulled plan.
Server boot integration still requires the provider startup hook or morning command.
