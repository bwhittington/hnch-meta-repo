# naysayer merge-gate enforcement

## What runs automatically (this repo)

| Mechanism | Behavior |
|-----------|----------|
| `.github/workflows/naysayer-gate.yml` | PR check **fails** unless a PR review or issue comment contains `## naysayer review` |
| `.github/PULL_REQUEST_TEMPLATE.md` | Required checklist for authors |

Marker format is defined in `skills/naysayer/SKILL.md`.

### Local / agent check (`gh`)

```powershell
# From a clone; set PR number
$pr = 1
gh api "repos/bwhittington/hnch-meta-repo/pulls/$pr/reviews" --jq '.[].body' | Select-String -Pattern '##\s*naysayer\s+review'
gh api "repos/bwhittington/hnch-meta-repo/issues/$pr/comments" --jq '.[].body' | Select-String -Pattern '##\s*naysayer\s+review'
```

If neither matches, spawn naysayer before merge.

## Policy

- **Every PR** on `hnch-meta-repo` and `hnch` needs a naysayer pass.
- This repo’s Action enforces the marker on **hnch-meta-repo** PRs.
- Mirror the same workflow into `hnch` when app work starts (see `hnch` `AGENTS.md` pointer).
- **Always fix** naysayer findings without waiting; escalate to Brett only what needs him.

## Branch protection (Brett admin UI — escalate)

GitHub Actions alone do not block merge until the check is **required**. Brett (repo admin) should:

1. Open https://github.com/bwhittington/hnch-meta-repo/settings/branches
2. Under **Branch protection rules**, edit or add a rule for `main`
3. Enable **Require status checks to pass before merging**
4. Search/select the status check named **`naysayer-required`** (job from workflow `naysayer-gate`) — after the workflow has run at least once it appears in the list
5. Enable **Require a pull request before merging** (recommended)
6. Save changes

Repeat for `bwhittington/hnch` once that repo has the same workflow.

Until that UI step is done, the Action still runs and shows red/green on the PR, but a human can merge past it.
