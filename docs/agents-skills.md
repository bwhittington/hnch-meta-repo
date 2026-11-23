# agents-skills (build / ops toolkit)

HNCH adopts **[skyfox675/agents-skills](https://github.com/skyfox675/agents-skills)** as the shared build/ops harness: slash commands, specialized agents, and skills for ticket → PR work.

We **do not** vendor that repository into `hnch-meta-repo` (license churn and maintenance). Install it in Cursor (or your other coding agent) and keep this meta-repo for domain docs plus thin HNCH skills.

## Ownership split

| Layer | Where |
|-------|--------|
| Product code | [bwhittington/hnch](https://github.com/bwhittington/hnch) only |
| Domain docs + thin HNCH skills | This repo (`docs/`, `skills/`, `AGENTS.md`) |
| Shared commands / agents / skills harness | Upstream **agents-skills** (plugin or git), not copied here |

## Preferred install (Cursor)

From the upstream README:

1. **Plugin (preferred):** install **`agents-skills`** from Cursor’s plugin marketplace.  
   — or —  
   **Point Cursor at the git repo** `https://github.com/skyfox675/agents-skills` (it ships `.cursor-plugin/marketplace.json`, so Cursor can source the plugin from git).
2. **Helper skills (quickstart):** install Anthropic document skills (includes **`xlsx`**), plus any other helpers the upstream quickstart lists (e.g. caveman, humanizer). Paste the Cursor install prompt from the [agents-skills README](https://github.com/skyfox675/agents-skills) Cursor section if you want the assistant to do the copies.
3. **GitHub CLI:** `gh` authenticated (`gh auth login`) — required for the `gh-issue-*`, `/dispatch`, and `/rescue` flows.

Release zips also exist on upstream GitHub Releases if you prefer a manual plugin install; marketplace/git is the short path.

**Do not** add a git submodule of agents-skills to this meta-repo unless Brett explicitly asks.

## Intended HNCH ticket flow

Use the upstream GitHub command chain:

1. `/gh-issue` — capture / file the work  
2. `/gh-issue-groom` — groom acceptance and scope  
3. `/gh-issue-recon` — recon the codebase against the issue  
4. `/dispatch` — implement (opens PR via implementer agents)  
5. **naysayer** — adversarial PR review (required before merge; spawn on PR open)  
6. `/rescue` — unstick a stuck PR or red CI when needed  

Type `/` in Cursor chat to list commands once the plugin is installed. Try a smoke issue after install (upstream example pattern: `/gh-issue …`).

### naysayer vs agents-skills `reviewer`

Upstream agents-skills includes a `reviewer` agent (severity-tagged adversarial diff review). HNCH keeps a named role **naysayer** (`skills/naysayer.md`) as the **merge gate** for every PR on `hnch` and `hnch-meta-repo`. Use the same skeptical style; do not skip naysayer because a generic reviewer already ran. Project coordinator / dispatch should spawn naysayer when a PR opens.

Domain fidelity for estimation still comes from this meta-repo (`docs/estimation-model-overview.md`, `skills/estimation-fidelity.md`, etc.). Product edits land only in `hnch`.

## Excel / `xlsx` helper

For workbook fidelity work against `Estimation_Model_1702.xlsx`, the Anthropic **`xlsx`** helper skill (via the agents-skills quickstart / Anthropic skills install) is especially useful: read and inspect sheet structure without inventing calc behavior. Pair it with `docs/source-model.md` and `docs/estimation-model-overview.md`.

## Related in this repo

- Always-on rules: `AGENTS.md`
- Thin playbook: `skills/using-agents-skills.md`
- Adversarial PR gate: `skills/naysayer.md`
- Domain overview: `docs/estimation-model-overview.md`
