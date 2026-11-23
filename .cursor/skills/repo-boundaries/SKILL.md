---
name: repo-boundaries
description: >-
  Keep product code in bwhittington/hnch and AI/domain assets in
  bwhittington/hnch-meta-repo; do not mix scaffolding across repos.
---

# repo-boundaries

- **`hnch`** — application code only (UI, calc engine, APIs, tests, deploy config).
- **`hnch-meta-repo`** — `AGENTS.md`, Agent Skills under `skills/*/SKILL.md` (mirrored for Cursor under `.cursor/skills/`), durable docs, eval stubs, Excel/source pointers.
- **`skyfox675/agents-skills`** — shared build/ops harness (install separately; do not vendor).
- Do not scaffold or land product features in the meta-repo.
- Do not park large prompts or model archaeology inside app PRs when they belong here.
- Cross-link the companion repo in PR descriptions when both sides matter.
