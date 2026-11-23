# Skill: using agents-skills

## When

Any HNCH implementation ticket, grooming, recon, dispatch, or stuck-PR rescue.

## Do

1. Confirm the **agents-skills** toolkit is available in this Cursor session (plugin marketplace `agents-skills`, or Cursor pointed at https://github.com/skyfox675/agents-skills). If missing, stop and tell Brett to install it — do not vendor the upstream tree into git.
2. Prefer the adopted flow for GitHub work: `/gh-issue` → `/gh-issue-groom` → `/gh-issue-recon` → `/dispatch` (and `/rescue` when stuck). Follow those command/agent patterns instead of inventing a parallel process.
3. Load HNCH domain context from this meta-repo (`AGENTS.md`, `docs/`, other `skills/`) before changing estimation behavior.
4. For Excel model inspection, use the Anthropic **`xlsx`** helper skill when available; stay faithful to `docs/estimation-model-overview.md`.
5. Implement product code only in https://github.com/bwhittington/hnch. Keep domain docs and thin skills here.

## Do not

- Copy or submodule the full skyfox675/agents-skills tree into `hnch-meta-repo` or `hnch` unless Brett explicitly asks.
- Bypass groom/recon for non-trivial tickets when the toolkit is installed.
- Treat upstream agents-skills docs as a substitute for HNCH Excel domain truth.

## Pointer

Install and flow details: `docs/agents-skills.md`.
