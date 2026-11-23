---
name: estimation-domain
description: >-
  Domain-aware helper for HNCH estimation: load project context, model
  overview, fidelity rules, and naysayer when implementing or reviewing.
---

# estimation-domain

## Mission

Help implement and review HNCH estimation software while staying faithful to the Excel model.

## Always load

1. `AGENTS.md`
2. `docs/agents-skills.md` (and skill `using-agents-skills` when implementing tickets)
3. `docs/project-context.md`
4. `docs/estimation-model-overview.md`
5. skill `estimation-fidelity`
6. skill `repo-boundaries`
7. skill `naysayer` (when reviewing or opening a PR)

## Companion app

Code changes go in https://github.com/bwhittington/hnch only.

## Local model file

If the workbook is available locally, see `docs/source-model.md`. Do not commit secrets or customer-specific rate sheets.

## Output expectations

- Prefer precise phase codes and mode names from the model overview.
- Call out when a proposed change would diverge from the workbook.
- Keep meta-repo edits to `AGENTS.md`, `docs/`, `skills/`, `.cursor/skills/`, `evals/` — not app scaffolding.
