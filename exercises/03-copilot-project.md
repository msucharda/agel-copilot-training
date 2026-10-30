# Exercise 3: coordinate your own Copilot Project

**14:45-16:00 CET, 75 minutes.** Work individually on the sample app.
One person gets help from several agents; this is not a team exercise.

**Result:** a Copilot Project with 2-3 reviewed worktree sessions and their
changes merged **locally into `main`**. Do not open PRs, request GitHub
Copilot review or push these changes.

## Task selection

Use these existing files in the app clone. The lecturer checks the
[integrated baseline](../README.md#sample-app) before starting.

| Session | Task | Use |
|---|---|---|
| A | `.scratch/room-equipment-filter/issues/01-filter-room-equipment.md` | Required: all-of equipment filter on the room catalogue |
| B | `.scratch/booking-csv-export/issues/01-export-own-bookings.md` | Required: private paginated CSV export |
| C | `.scratch/facility-api-guide/issues/01-document-facility-operations.md` | Optional: facility operations guide |

Read each task's acceptance criteria. Choose two independent tasks; use a
third only if it can finish and be reviewed within this block. Do not start
several sessions on the same file without an explicit coordination decision.
These task scopes separate `room/`, new `booking/export/` files and
`docs/api-usage.md`, with distinct tests. Do not edit shared helpers or the
shared README from those sessions.
`.scratch/availability-selection/issues/01-clarify-selection-pipeline.md`
is an alternative refactoring task, not another boundary-bug implementation.

## 1. Prepare the local base (14:45-14:55, 10 minutes)

Inspect the app clone with your normal Git tools. Commit the work you want to
keep from exercise 2, ensure the working tree is clean, and select local
`main` as the Project base. If the clone is not on `main`, ask the lecturer to
help preserve the current work before switching branches.
Keep the local Markdown tracker configuration from exercise 2, including
`docs/agents/issue-tracker.md` and `docs/agents/domain.md`.

Add the **existing local sample-app clone** as a repository in the Copilot
desktop app if it is not already registered. Create your own Copilot Project
for this repository. Set its goal and local-only working agreement.

Do not choose a remote repository creation or publishing flow.

## 2. Give the Project a bounded assignment (14:55-15:05, 10 minutes)

Use the selected task filenames directly:

```text
This is my individual local workshop Project for the sample app.
Read its README and the selected .scratch tasks before acting.
Our tracker is local Markdown: no GitHub/Jira issue writes.
Create two coding sessions for:
A: .scratch/room-equipment-filter/issues/01-filter-room-equipment.md
B: .scratch/booking-csv-export/issues/01-export-own-bookings.md
Optionally create C for
.scratch/facility-api-guide/issues/01-document-facility-operations.md
only if independent and time permits.
Each session must use its own worktree, implement only its assigned task,
capture its base commit before editing, verify acceptance criteria, run
code-review against that base and the local task file, resolve findings,
and report its branch and commit. Stay within each task's file scope.
Run the app's targeted tests and wrapper verify. Do not run competing
manual app servers on port 8080. Do not create PRs, request GitHub Copilot
review, push, or merge until I inspect the results.
```

Ask the Project to name each session's scope and dependency before it starts.

**Checkpoint:** two sessions exist, each has a different worktree/branch,
and you can identify the task assigned to each.

## 3. Supervise and review (15:05-15:35, 30 minutes)

Read a session's question before answering. If a task is blocked by another,
have the Project sequence the dependent work instead of making both sessions
guess. Do not add a third session merely to increase the count.

For each completed session, inspect:

- The assigned task and the resulting diff.
- Evidence for its acceptance criteria and relevant tests.
- Its `code-review` result and the disposition of every finding.
- The exact local branch and commit offered for integration.

For A, check all-of matching, omitted/duplicate/unknown equipment and
combination with existing filters. For B, check owner isolation, pagination,
CSV quoting and spreadsheet-formula neutralization. For C, check the
documented PowerShell/CSRF workflow and its expected 403/400 examples.
Use the complete task criteria, not just these reminders.

If the session skipped the review, ask it to run `code-review` before
integration. This is a local skill review, not GitHub Copilot PR review.

## 4. Merge locally and check the combination (15:35-15:55, 20 minutes)

Inspect the app's merge target and confirm that it is **local `main`**.
Merge one ready session at a time using the app's local merge action, or
your usual Git workflow in the base clone:

```shell
git switch main
git merge --no-edit SESSION_A_BRANCH
git merge --no-edit SESSION_B_BRANCH
```

Replace branch placeholders with the actual reported local branch names.
If you started session C, integrate it only after its review has finished.
Do not click a GitHub PR or remote merge action.

If a merge reports a conflict, stop integration, inspect both task intents,
resolve the actual conflict and rerun the affected checks before continuing.
Do not discard another session's changes to obtain a clean merge.

Run the full check from the app root on combined local `main`:

```powershell
.\mvnw.cmd verify
```

On Unix, use `./mvnw verify`. Inspect both tasks' observable results. Passing checks inside
separate worktrees do not prove that the combination works.
Tests use in-memory H2; manual app instances use per-worktree database files
but share the default port. Stop any previous manual server before running
one instance to inspect the combined result. Do not delete another worktree's data.

## 5. Explain the result (15:55-16:00, 5 minutes)

Show the Project, the 2-3 worktree sessions, their reviews and the local
`main` result. Explain one decision you made as the human coordinator.
Keep the local commits; there is no GitHub participant repository to show.

## If something is unavailable

| Problem | Continue with | What is not complete |
|---|---|---|
| Project/session creation is unavailable | Follow the lecturer's Project walkthrough; record task boundaries and dependency order locally | Manual chats alone do not satisfy the Project checkpoint |
| Plugin or network fails | Inspect existing diffs and prepare review questions; resume the named review when available | Do not label an unrun review complete |
| A session is unfinished at 15:35 | Integrate only reviewed, verified work; keep the other session's worktree | Report the missing session instead of claiming the 2-session result |
| No local app baseline | Observe the lecturer's integration and preserve your task plan | Your local integrated app remains unverified |

Jira and the Connector do not affect this exercise.
