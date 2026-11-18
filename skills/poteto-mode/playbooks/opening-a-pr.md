### Opening a PR

Invoked at the end of every other playbook. In a session the user drives, push the branch and open the PR when the user asks for it. Autonomous runs and workers open it as their brief says.

Work from a git worktree off trunk, and keep unrelated work out of it. Rebase into small, landable commits. Run `/deslop` from `cursor-team-kit` over the diff before commit.

When the repo has a PR template or an AGENTS.md layout for PRs, follow it instead of the title and body rules below.

A UI change carries before and after screenshots. Put them on a `<branch>-shots` branch, never the PR branch, and embed them in the body by commit SHA.

Title: `type(scope): subject`, naming a real symbol when one carries the change. Body: a one-minute briefing under 40 lines with these `##` headings in order, dropping empty ones: `## Why`, `## What changed`, `## Scope`, `## Tradeoffs` (only rejected alternatives a reviewer would otherwise ask about), `## Blast Radius`, `## Verification`.

Stack follow-ups by base branch. Open PRs ready, through the run's PR tool with `draft: false`. Without one, use `gh pr create` without `--draft`, or `origin pr create --status open` when Origin's CLI resolves the repository. Opening a PR does not start a babysit.
