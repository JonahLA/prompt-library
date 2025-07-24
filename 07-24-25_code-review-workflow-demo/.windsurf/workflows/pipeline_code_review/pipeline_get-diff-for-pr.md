---
description: Gets the file diff between stage and the head of a PR for the current repo
---

INTERFACE:

 - IN
   - branchName (name of branch associated with PR)
 - OUT
   - diff (diff between base branch and head of PR)

NOTES:

 - MUST be run in "Write" mode, not "Chat" mode


STEPS:

A. Get latest updates for base branch
 - `git fetch origin stage`

B. Generate diff
 - `git diff origin/stage...origin/{branchName}`
 - OUT -> {diff}