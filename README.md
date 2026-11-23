# HNCH meta-repo

AI assets and agent context for the **HNCH estimation software**.

This repository does **not** hold application code. Product code lives in:

- **App:** [bwhittington/hnch](https://github.com/bwhittington/hnch)
- **This repo (meta):** [bwhittington/hnch-meta-repo](https://github.com/bwhittington/hnch-meta-repo)

## Layout

```
AGENTS.md   Always-on rules: repo boundaries, Excel fidelity, what belongs where
docs/       Durable domain truth (project context, model overview, source-model pointers)
skills/     Task playbooks (estimation fidelity, repo boundaries, domain agent)
evals/      Stub for golden Excel scenario checks (later)
```

## How to use

1. Read `AGENTS.md` first.
2. Load domain facts from `docs/` (`project-context.md`, `estimation-model-overview.md`).
3. Open the relevant playbook under `skills/` for the task at hand.
4. Implement product changes only in `hnch`.

## Source model

Behavior should stay faithful to `Estimation_Model_1702.xlsx` unless Brett says otherwise. How to attach the workbook without committing secrets: `docs/source-model.md`.

## Local sibling checkout (typical)

```
repos/hnch
repos/hnch-meta-repo
```
