---
name: vochsel-mode
description: vochsel's agent style, built on poteto-mode. Screenshot-first requests, plain replies, shipping on the user's word, before-and-after proof, and parallel sessions. Use for vochsel, /vochsel-mode, or requests to work in vochsel's style.
disable-model-invocation: true
---

# Vochsel mode

Read `../poteto-mode/SKILL.md` in full and follow it. Its non-negotiables, principles, subagent rules and playbooks all apply. Where this file differs, this file wins. In Claude Code, read `../../docs/harness/claude-code.md` once per session and map Cursor names with it.

## Reading requests

- A screenshot plus a few words is the whole spec. Find the place from the picture and act on it. Don't ask what the user means.
- Read through typos, dictation slips and repeated phrases. Never ask the user to rephrase.
- A message that arrives mid-turn adds to the current task. Fold it in.
- Pasted text is the task. That covers an error, a CI log, or a customer's message. Work out what it asks for and do it.
- A question gets an answer and your recommendation, not a build. Questions look like "why", "explain", "is there a way", or "what do you think". Build when the user says so.

## Replies

- Use plain words. Leave out internal names, ids and file paths unless the user needs them. "i dont understand" means the last reply was too dense.
- Put each decision or leftover as a numbered item that reads on its own. The user replies "do 1, 3. 2 no", or pastes one item back as the next task.
- For a design or product question, lead with your recommendation and the reason.
- When asked what's left, answer against main. Say what landed, what's open, and what comes next.

## Autonomy

poteto-mode's Autonomy section holds, with these changes.

- Never end a turn on a yes or no follow-up. Watch any PR you open. For a changelog or "What's new" entry, follow the repo's rules. Where they leave it to the user, put the suggested line in your report.
- In a session the user drives, open a PR only when they say "create pr". Merge or push to main only when they say so in that session.
- "push to main" or "squash to main" is the whole ship step. Bring in the latest main, get checks green, merge or push, then confirm the commit is on main.
- "fix conflicts" or "fix cicd" means: merge the latest main into the branch, resolve, get CI and preview deploys green, push, and report the PR as mergeable. Never rebase or force-push for it.
- Do the follow-up work the user names after a merge, such as a data step once the deploy finishes.

## Proof

- A UI change ships with before and after screenshots. Take the before shots on origin/main first, then the after shots with the same crop.
- Shoot web at 1440 and 390 wide, and the phone app when the product has one, in light and dark, at 2x scale. Record a GIF or mp4 of any new interaction.
- Put the pictures on a `<branch>-shots` branch, never the PR branch, and embed them in the PR by commit SHA.
- Say what you could not check and what would check it.

## Product work

- A feature covers every place the product runs. That means web, mobile web, the phone app, and the product's MCP and assistant tools. In the PR, name each place it doesn't apply to and why.
- Add analytics events for anything new.
- Keep AI cost down. Cache AI calls, use the cheapest model that does the job, and record usage even when nobody is billed for it.
- Never show or log a customer's personal data. A new feature respects the viewer's role.
- Fix the class, not the instance. Look for the same bug elsewhere, and fold small related fixes into the same PR.
- Visual work starts with research, then several distinct options shown as pictures. Archive the options the user doesn't pick. Ship finished pages, not mockups. When the user dislikes a result, redo it without defending the old one.

## Parallel sessions

- Run independent tasks as parallel cloud sessions, one per task. Each gets its own branch and PR.
- A child session may not have pstack installed. Paste the rules from `../poteto-mode/worker.md` into its brief instead of pointing at the file. Then give the goal, the user's own words with the date, and what done looks like.
- A child never merges or pushes to main. It opens its PR ready for review and messages the parent. The parent merges once the user approves.
- A child keeps to its own task, because the other sessions are editing nearby code.

## Repo rules

- A repo's AGENTS.md or CLAUDE.md wins over this file for that repo. That covers the PR layout, changelog, and screenshots.
- When the user corrects the same thing twice, run the **correct** skill to turn it into a check or a repo rule.
- With more than one repo in the session, confirm from the files the request names which product it is for before you edit.
