# Agent rules (always on)

Rules for any agent working on HNCH estimation. Load Agent Skills from `skills/*/SKILL.md` (Cursor auto-loads `.cursor/skills/`); durable domain facts live in `docs/`.

**Builders should have [skyfox675/agents-skills](https://github.com/skyfox675/agents-skills) available.** Install via copy-paste steps in [docs/agents-skills.md](./docs/agents-skills.md) (git/fallback first — do not block on marketplace). Harness is shared tooling — not vendored into this repo.

## naysayer (required on every PR)

**Every PR** on `hnch` and `hnch-meta-repo` must get a **naysayer** pass before merge. See [skills/naysayer/SKILL.md](./skills/naysayer/SKILL.md).

- naysayer = adversarial, skeptical reviewer (assume wrong until proven).
- Project coordinator / `/dispatch` should spawn naysayer on PR open.
- Related to agents-skills `reviewer`, but the HNCH gate keeps the name **naysayer**.
- **Repo enforcement:** GitHub Action `naysayer-gate` + PR template — see [docs/naysayer-enforcement.md](./docs/naysayer-enforcement.md). Branch protection “required check” needs Brett’s admin UI (documented there).
- **Always fix** naysayer findings without waiting; escalate to Brett only what needs him.
- No merge without an explicit naysayer recommendation (`request-changes` resolved, or `approve-with-risks`).

## Repo boundaries

| Repo | Owns |
|------|------|
| [bwhittington/hnch](https://github.com/bwhittington/hnch) | Application code only (UI, calc engine, APIs, tests, deploy) |
| [bwhittington/hnch-meta-repo](https://github.com/bwhittington/hnch-meta-repo) (this repo) | Agent rules, Agent Skills, durable domain docs, eval stubs, source-model pointers |
| [skyfox675/agents-skills](https://github.com/skyfox675/agents-skills) | Shared build/ops commands, agents, and skills (install separately) |

- Do not scaffold or land product features in this meta-repo.
- Do not park large prompts or model archaeology inside app PRs when they belong here.
- Do not copy the full agents-skills tree into git here unless Brett asks.
- Cross-link the companion repo in PR descriptions when both sides matter.

## Excel fidelity

- Behavioral source of truth: workbook `Estimation_Model_1702.xlsx`, summarized in `docs/estimation-model-overview.md` (read the provenance banner).
- Preserve Inventory / Task / Hybrid modes, phase codes (PL…WA), staffing vs unstaffed, Additional Costs, and Fixed-Fee vs T&M semantics unless Brett explicitly overrides.
- Do not simplify away PERT/Avg statistics, Setup ratios, or test phase splits (TCP/TCE/TBF) without asking.
- Broken / peripheral sheets (`Staffing w Built In CO`, `Agile` `#REF!`, unwired `Task Breakdown`) are not required product scope by default.
- Prefer the Anthropic **`xlsx`** helper skill when inspecting the workbook.

## Ticket flow (agents-skills)

Prefer: `/gh-issue` → `/gh-issue-groom` → `/gh-issue-recon` → `/dispatch` → **naysayer** (and `/rescue` when stuck). Details: `docs/agents-skills.md`.

## What belongs where

| Path | Use |
|------|-----|
| `AGENTS.md` | Always-on rules (this file) |
| `docs/` | Durable domain truth + toolkit / enforcement docs |
| `skills/<name>/SKILL.md` | HNCH Agent Skills (canonical) |
| `.cursor/skills/<name>/SKILL.md` | Same skills for Cursor project auto-load (keep in sync) |
| `evals/` | Future golden Excel scenario checks (stub for now) |

Do not commit secrets, customer rate books, or the Excel binary. See `docs/source-model.md` for attach guidance.
