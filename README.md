# HNCH meta-repo

AI assets, agent context, and durable product notes for the **HNCH estimation software**.

This repository does **not** hold application code. Product code lives in the companion app repo:

- **App:** [bwhittington/hnch](https://github.com/bwhittington/hnch)
- **This repo (meta):** [bwhittington/hnch-meta-repo](https://github.com/bwhittington/hnch-meta-repo)

## Why two repos?

| Repo | Owns |
|------|------|
| `hnch` | Estimation app (UI, calc engine, APIs, tests) |
| `hnch-meta-repo` | Prompts, agent instructions, model notes, product context agents should load |

Keep prompts and source-model notes here so app PRs stay focused on product code, and agents have a stable place for estimation-domain context.

## Layout

```
docs/           Durable product & agent context (modes, phases, vocabulary)
prompts/        Reusable prompt snippets for agents and workflows
agents/         Agent role briefs / skill-style instructions
context/        Local source notes (Excel model pointers — not secrets)
```

## How agents should use this repo

1. Read `docs/project-context.md` for goals, constraints, and companion-repo links.
2. Read `docs/estimation-model-overview.md` for Excel-faithful domain facts (modes, phases, staffing/pricing).
3. Load prompts from `prompts/` and role briefs from `agents/` when running estimation-related tasks.
4. Treat `context/` as optional local notes. Prefer documented pointers over committing large binaries or anything sensitive.
5. Implement product changes only in `hnch`, using this repo as the source of domain intent.

## Source model

Behavior should stay faithful to the Excel estimation workbook (`Estimation_Model_1702.xlsx`) unless Brett says otherwise. The workbook may live in a Cursor Project store or a local path — see `context/excel-model/README.md` for how to attach it without dumping secrets into git.

## Local sibling checkout (typical)

On Brett’s machine these often sit side by side:

```
repos/hnch
repos/hnch-meta-repo
```

Clone both if you need app + AI context together.
