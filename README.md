# HNCH meta-repo

AI assets and agent context for the **HNCH estimation software**.

This repository does **not** hold application code. Product code lives in:

- **App:** [bwhittington/hnch](https://github.com/bwhittington/hnch)
- **This repo (meta):** [bwhittington/hnch-meta-repo](https://github.com/bwhittington/hnch-meta-repo)
- **Build/ops harness:** [skyfox675/agents-skills](https://github.com/skyfox675/agents-skills) — install in Cursor; do not vendor here. See [docs/agents-skills.md](./docs/agents-skills.md).

## Layout

```
AGENTS.md   Always-on rules: repo boundaries, Excel fidelity, toolkit pointer
docs/       Durable domain truth + agents-skills adoption notes
skills/     Thin HNCH task playbooks (incl. using-agents-skills)
evals/      Stub for golden Excel scenario checks (later)
```

## How to use

1. Install **agents-skills** in Cursor (marketplace plugin `agents-skills`, or point Cursor at the git repo). Details: [docs/agents-skills.md](./docs/agents-skills.md).
2. Read `AGENTS.md`.
3. Load domain facts from `docs/` (`project-context.md`, `estimation-model-overview.md`).
4. Open the relevant playbook under `skills/` (start with `using-agents-skills.md` for ticket work).
5. Implement product changes only in `hnch`.

## Source model

Behavior should stay faithful to `Estimation_Model_1702.xlsx` unless Brett says otherwise. How to attach the workbook without committing secrets: `docs/source-model.md`. The Anthropic **`xlsx`** helper (via agents-skills quickstart) helps with Excel fidelity work.

## Local sibling checkout (typical)

```
repos/hnch
repos/hnch-meta-repo
```
