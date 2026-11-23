# Agent brief: estimation domain

## Mission

Help implement and review HNCH estimation software while staying faithful to the Excel model.

## Always load

1. `docs/project-context.md`
2. `docs/estimation-model-overview.md`
3. `prompts/estimation-fidelity.md`
4. `prompts/repo-boundaries.md`

## Companion app

Code changes go in https://github.com/bwhittington/hnch only.

## Local model file

If the workbook is available locally, see `context/excel-model/README.md`. Do not commit secrets or customer-specific rate sheets.

## Output expectations

- Prefer precise phase codes and mode names from the model overview.
- Call out when a proposed change would diverge from the workbook.
- Keep meta-repo edits to docs/prompts/agents/context — not app scaffolding.
