---
name: using-agents-skills
description: >-
  Use skyfox675/agents-skills as the HNCH build/ops harness for GitHub ticket
  flow (gh-issue, groom, recon, dispatch, rescue) without vendoring upstream.
---

# using-agents-skills

## When

Any HNCH implementation ticket, grooming, recon, dispatch, stuck-PR rescue, or toolkit setup.

## Do

1. Confirm **agents-skills** is available. Prefer the copy-paste steps in `docs/agents-skills.md` (**git/fallback first**, marketplace optional). If missing, stop and tell Brett to install — do not vendor the upstream tree into git.
2. Prefer the adopted flow: `/gh-issue` → `/gh-issue-groom` → `/gh-issue-recon` → `/dispatch` → **naysayer** on PR open (and `/rescue` when stuck).
3. Load HNCH domain context from this meta-repo (`AGENTS.md`, `docs/`, other project skills) before changing estimation behavior.
4. For Excel model inspection, use the Anthropic **`xlsx`** helper skill when available; stay faithful to `docs/estimation-model-overview.md`.
5. Implement product code only in https://github.com/bwhittington/hnch. Keep domain docs and thin skills here.
6. Do not merge without a **naysayer** pass (`skills/naysayer/SKILL.md`) on both `hnch` and `hnch-meta-repo` PRs.

## Do not

- Copy or submodule the full skyfox675/agents-skills tree into `hnch-meta-repo` or `hnch` unless Brett explicitly asks.
- Bypass groom/recon for non-trivial tickets when the toolkit is installed.
- Treat upstream agents-skills docs as a substitute for HNCH Excel domain truth.

## Pointer

Install and flow details: `docs/agents-skills.md`.
