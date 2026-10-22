# Decisions

Author: AI agent (Codex). Human companion: [decisions.md](decisions.md).

## D-20261019-01 — Add this project's notebook

User explicitly requested experiment_obs and documentation, selected company repo
auric007/visual_reasoning, and approved public access. Use the existing shared policy,
Sunday notebook weeks and recursive human/AI filename separation. Preserve original
research paths and use independent notebook Git metadata. Only notebook files are
eligible for transport; no model work is authorized by a note or its synchronization.

Evidence: [setup task](../2026/2026-10/week-2026-10-18/daily/2026-10-19_ai.md).
Revisit transport if repository ownership, visibility or publication requirements change.

## D-20261022-01 — user supplies next rejection examples; preflight visual label leakage

Recorded 2026-10-22T18:06:52+05:30; task RN-20261022-p0p2-p1. The user will prepare the next other/background examples personally and supply them later. Defer remediation of the old P0 corpus; this decision does not request any data generation or training now.

Before the next authorized run using those inputs, verify actual final image pixels (both close and context) and prompt text contain no class-revealing IDs or labels. Neutral marks are acceptable. Paths used only to load images are not supplied as text, but visible text embedded in pixels remains model-readable. Record inspected examples and outcome before training. This future check is a standing requirement, not a claim that the new dataset already exists or has passed it.

Persisted in project CLAUDE.md for future sessions. [Daily evidence](../2026/2026-10/week-2026-10-18/daily/2026-10-22_ai.md).
