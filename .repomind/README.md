# RepoMind on this repository

This repo has [RepoMind](https://github.com/repomind) — an autonomous CI
auto-fix agent — installed.

## What does it do?

When a GitHub Actions workflow on this repo **fails**, RepoMind:

1. Downloads the failure logs.
2. Runs a multi-agent LLM pipeline to triage the failure.
3. Proposes a fix.
4. Either posts the fix as a comment (`dry_run`) or opens a PR (`auto_fix`).
5. Waits for **a human to review and approve** before any merge.

## How is it configured?

This repo's `.repomind.yml` (in the repo root) controls the agent's behaviour
**for this repo specifically**. You don't need to email anyone to change it —
just edit the YAML and merge.

### Three modes

| Mode | What happens |
|------|--------------|
| `disabled` | RepoMind ignores this repo entirely. |
| `dry_run`  | RepoMind posts comments with proposed fixes. **Never opens PRs.** ← default |
| `auto_fix` | RepoMind opens fix PRs automatically. **Still requires human merge.** |

### Human-in-the-loop

`hitl_required: true` (the default) means RepoMind will **never auto-merge**
a PR. You always get the final say.

## Removing RepoMind

Delete `.repomind.yml`, or set `mode: disabled`, or uninstall the GitHub App
from this repo. There's nothing to clean up.

## Questions?

See the [onboarding guide](https://github.com/repomind/repomind/blob/main/projectdocs/ONBOARDING.md).
