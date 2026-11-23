# HNCH estimation software — project context

## Goal

Build project estimation software based on the Excel model `Estimation_Model_1702.xlsx`.

## Repositories

- **App code:** https://github.com/bwhittington/hnch
- **AI assets / context (this repo):** https://github.com/bwhittington/hnch-meta-repo

## Constraints

- Keep product code in `hnch`; keep agent rules, skills, and durable domain docs in `hnch-meta-repo`.
- Prefer fidelity to the Excel estimation model’s inputs, calculations, and outputs unless Brett asks otherwise.

## Source model

- Workbook: `Estimation_Model_1702.xlsx` — attach guidance in [source-model.md](./source-model.md).
- Domain overview: [estimation-model-overview.md](./estimation-model-overview.md).

## Agent entry points

- Always-on rules: `AGENTS.md`
- Build/ops harness: [agents-skills.md](./agents-skills.md) (skyfox675/agents-skills — install, don’t vendor)
- Task playbooks: `skills/` (incl. `using-agents-skills.md`, **`naysayer.md`**)
- **Merge gate:** every PR on `hnch` and `hnch-meta-repo` needs a naysayer pass before merge
- Future golden checks: `evals/`
