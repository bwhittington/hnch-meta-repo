# Skill: repo boundaries

- **`hnch`** — application code only (UI, calc engine, APIs, tests, deploy config).
- **`hnch-meta-repo`** — `AGENTS.md`, skills, durable docs, eval stubs, Excel/source pointers.
- Do not scaffold or land product features in the meta-repo.
- Do not park large prompts or model archaeology inside app PRs when they belong here.
- Cross-link the companion repo in PR descriptions when both sides matter.
