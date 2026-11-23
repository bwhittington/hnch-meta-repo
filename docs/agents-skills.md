# agents-skills (build / ops toolkit)

HNCH adopts **[skyfox675/agents-skills](https://github.com/skyfox675/agents-skills)** as the shared build/ops harness: slash commands, specialized agents, and skills for ticket → PR work.

We **do not** vendor that repository into `hnch-meta-repo` (license churn and maintenance). Install it in Cursor (or your other coding agent) and keep this meta-repo for domain docs plus HNCH Agent Skills under `skills/*/SKILL.md` (Cursor loads the mirror in `.cursor/skills/`).

## Ownership split

| Layer | Where |
|-------|--------|
| Product code | [bwhittington/hnch](https://github.com/bwhittington/hnch) only |
| Domain docs + HNCH skills | This repo (`docs/`, `skills/*/SKILL.md`, `.cursor/skills/`, `AGENTS.md`) |
| Shared commands / agents / skills harness | Upstream **agents-skills** (install separately), not copied here |

## Install (Cursor) — copy-paste

**Do not block on marketplace.** Use Path A or B first; marketplace is optional sugar.

### Path A — point Cursor at the git repo (reliable)

1. Clone (once per machine):

```powershell
git clone https://github.com/skyfox675/agents-skills.git C:\Users\brett\repos\agents-skills
```

2. In Cursor: open **Settings → Plugins / Features → add marketplace or project from git** and add  
   `https://github.com/skyfox675/agents-skills`  
   (upstream ships `.cursor-plugin/marketplace.json`).  
   If the UI label differs: use “Add plugin from GitHub” / “Install from repository” and paste that URL.

3. Confirm slash commands: in chat type `/` — you should see `/gh-issue`, `/dispatch`, etc.

### Path B — copy Cursor folders into a working project (offline fallback)

If plugins UI is unavailable, copy harness folders into the **app** repo you are coding in (usually `hnch`), not necessarily this meta-repo:

```powershell
$src = "C:\Users\brett\repos\agents-skills"   # after Path A clone
$dst = "C:\Users\brett\repos\hnch"            # product checkout
git -C $src pull --ff-only
Copy-Item -Recurse -Force "$src\.cursor\*" "$dst\.cursor\"
Copy-Item -Recurse -Force "$src\.claude\skills" "$dst\.claude\skills"
```

Then reopen the `hnch` folder in Cursor and type `/`.

### Path C — marketplace (optional)

If Cursor’s plugin marketplace lists **`agents-skills`**, install it. Treat this as best-effort; if the listing is missing, use Path A or B.

### Helper skills (incl. `xlsx`)

Paste into Cursor chat (from upstream quickstart, adapted):

```text
Install these skills into .cursor/skills/ (or ~/.cursor/skills/ for every project):
1. Anthropic skills (docx, pdf, pptx, xlsx, skill-creator, doc-coauthoring, mcp-builder): copy each skills/<name>/ folder from github.com/anthropics/skills
2. caveman: run its official installer from github.com/JuliusBrussee/caveman
3. humanizer: git clone github.com/blader/humanizer
Then tell me what you installed.
```

### GitHub CLI (required for gh-issue / dispatch / rescue)

```powershell
gh auth status
# if not logged in:
gh auth login
```

**Do not** add a git submodule of agents-skills to this meta-repo unless Brett explicitly asks.

## Intended HNCH ticket flow

1. `/gh-issue` — capture / file the work  
2. `/gh-issue-groom` — groom acceptance and scope  
3. `/gh-issue-recon` — recon the codebase against the issue  
4. `/dispatch` — implement (opens PR via implementer agents)  
5. **naysayer** — adversarial PR review (required before merge; spawn on PR open)  
6. `/rescue` — unstick a stuck PR or red CI when needed  

### naysayer vs agents-skills `reviewer`

Upstream includes a `reviewer` agent. HNCH keeps **naysayer** (`skills/naysayer/SKILL.md`) as the merge gate. CI: `docs/naysayer-enforcement.md`.

## Excel / `xlsx` helper

For workbook fidelity work against `Estimation_Model_1702.xlsx`, the Anthropic **`xlsx`** helper skill is especially useful. Pair with `docs/source-model.md` and `docs/estimation-model-overview.md`.

## Related in this repo

- Always-on rules: `AGENTS.md`
- HNCH skills: `skills/*/SKILL.md` (Cursor: `.cursor/skills/`)
- Enforcement: `docs/naysayer-enforcement.md`
- Domain overview: `docs/estimation-model-overview.md`
