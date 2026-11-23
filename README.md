# HNCH meta-repo

AI assets and agent context for the **HNCH estimation software**.

This repository does **not** hold application code. Product code lives in:

- **App:** [bwhittington/hnch](https://github.com/bwhittington/hnch)
- **This repo (meta):** [bwhittington/hnch-meta-repo](https://github.com/bwhittington/hnch-meta-repo)
- **Build/ops harness:** [skyfox675/agents-skills](https://github.com/skyfox675/agents-skills) — install via [docs/agents-skills.md](./docs/agents-skills.md) (git/fallback first).

## Layout

```
AGENTS.md                 Always-on rules + naysayer gate
docs/                     Domain truth, agents-skills install, naysayer enforcement
skills/<name>/SKILL.md    HNCH Agent Skills (canonical)
.cursor/skills/           Cursor auto-load mirror of those skills
evals/                    Stub for golden Excel scenario checks
.github/workflows/        naysayer-gate CI
```

## How to use

1. Install **agents-skills** using [docs/agents-skills.md](./docs/agents-skills.md) Path A or B (do not wait on marketplace).
2. Open this repo in Cursor so `.cursor/skills/` loads (naysayer, estimation-fidelity, …).
3. Read `AGENTS.md` and domain docs under `docs/`.
4. Implement product changes only in `hnch`.

## naysayer (merge gate)

**Every PR** on `hnch` and `hnch-meta-repo` requires a **naysayer** review (`## naysayer review` marker).  
CI: `.github/workflows/naysayer-gate.yml`. Details: [docs/naysayer-enforcement.md](./docs/naysayer-enforcement.md).  
**Always fix** naysayer findings; escalate to Brett only what needs him (e.g. branch-protection UI).

## Source model

Behavior should stay faithful to `Estimation_Model_1702.xlsx` unless Brett says otherwise.  
Overview + provenance: `docs/estimation-model-overview.md`. Attach guidance: `docs/source-model.md`.

## Local sibling checkout (typical)

```
repos/hnch
repos/hnch-meta-repo
repos/agents-skills   # optional local clone for Path A/B install
```
