# HNCH estimation software — project context

## Goal

Build project estimation software based on the Excel model `Estimation_Model_1702.xlsx`.

## Repositories

- **App code:** https://github.com/bwhittington/hnch
- **AI assets / context (this repo):** https://github.com/bwhittington/hnch-meta-repo

## Constraints

- Keep product code in `hnch`; keep prompts, agent context, and AI assets in `hnch-meta-repo`.
- Prefer fidelity to the Excel estimation model’s inputs, calculations, and outputs unless Brett asks otherwise.

## Source model

- Workbook: `Estimation_Model_1702.xlsx` (see `context/excel-model/` for attach guidance).
- Domain overview for agents: [estimation-model-overview.md](./estimation-model-overview.md).

## Agent entry points in this repo

- Prompts: `prompts/`
- Role briefs: `agents/`
- Local/source notes: `context/`
