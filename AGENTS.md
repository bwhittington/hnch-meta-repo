# Agent rules (always on)

Rules for any agent working on HNCH estimation. Load task playbooks from `skills/` as needed; durable domain facts live in `docs/`.

**Builders should have [skyfox675/agents-skills](https://github.com/skyfox675/agents-skills) available** (Cursor plugin or git). See [docs/agents-skills.md](./docs/agents-skills.md) and [skills/using-agents-skills.md](./skills/using-agents-skills.md). That harness is shared tooling — not vendored into this repo.

## Repo boundaries

| Repo | Owns |
|------|------|
| [bwhittington/hnch](https://github.com/bwhittington/hnch) | Application code only (UI, calc engine, APIs, tests, deploy) |
| [bwhittington/hnch-meta-repo](https://github.com/bwhittington/hnch-meta-repo) (this repo) | Agent rules, thin skills, durable domain docs, eval stubs, source-model pointers |
| [skyfox675/agents-skills](https://github.com/skyfox675/agents-skills) | Shared build/ops commands, agents, and skills (install separately) |

- Do not scaffold or land product features in this meta-repo.
- Do not park large prompts or model archaeology inside app PRs when they belong here.
- Do not copy the full agents-skills tree into git here unless Brett asks.
- Cross-link the companion repo in PR descriptions when both sides matter.

## Excel fidelity

- Behavioral source of truth: workbook `Estimation_Model_1702.xlsx`, summarized in `docs/estimation-model-overview.md`.
- Preserve Inventory / Task / Hybrid modes, phase codes (PL…WA), staffing vs unstaffed, Additional Costs, and Fixed-Fee vs T&M semantics unless Brett explicitly overrides.
- Do not simplify away PERT/Avg statistics, Setup ratios, or test phase splits (TCP/TCE/TBF) without asking.
- Broken / peripheral sheets (`Staffing w Built In CO`, `Agile` `#REF!`, unwired `Task Breakdown`) are not required product scope by default.
- Prefer the Anthropic **`xlsx`** helper skill (via agents-skills quickstart) when inspecting the workbook.

## Ticket flow (agents-skills)

Prefer: `/gh-issue` → `/gh-issue-groom` → `/gh-issue-recon` → `/dispatch` (and `/rescue` when stuck). Details: `docs/agents-skills.md`.

## What belongs where

| Path | Use |
|------|-----|
| `AGENTS.md` | Always-on rules (this file) |
| `docs/` | Durable domain truth + toolkit pointer (`agents-skills.md`) |
| `skills/` | Thin HNCH task playbooks |
| `evals/` | Future golden Excel scenario checks (stub for now) |

Do not commit secrets, customer rate books, or the Excel binary. See `docs/source-model.md` for attach guidance.
