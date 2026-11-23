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
- Domain overview (with provenance): [estimation-model-overview.md](./estimation-model-overview.md).

## Agent entry points

- Always-on rules: `AGENTS.md`
- Build/ops harness: [agents-skills.md](./agents-skills.md) (install, don’t vendor)
- Agent Skills: `skills/*/SKILL.md` (Cursor: `.cursor/skills/`)
- **Merge gate:** naysayer on every PR — [naysayer-enforcement.md](./naysayer-enforcement.md)
- Future golden checks: `evals/`
