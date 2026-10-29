# Exercise 1: build your personal coding assistant

**10:45-12:00 CET, 75 minutes.** Work individually in the Copilot desktop app.
Use the assistant clone from preparation; do not create a repository on GitHub.
Write your assistant's output in English.

**Result:** a local assistant repository that captures your preferences,
contains one reusable skill, and has a verified personal installation.

## Before you start

- Complete the [preparation checks](../docs/preparation.md).
- Have the template clone open. If you did not clone it, use the AGEL URL in
  the finalized [preparation instructions](../docs/preparation.md), not a
  development URL.
- Add the existing local assistant directory as a repository in the app and
  start a session there. This is not yet the Project exercise.
- Read the clone's README. Confirm that `assistant-setup`, `assistant-learn`
  and `assistant-skill` are available in that session. Use `/skills` to inspect
  available skills; if a skill is missing, ask the lecturer before continuing.

The four maintenance skills come from `.agents/skills/` in this clone.
`assistant-setup` fills `AGENTS.md` and creates a local commit after approval;
`assistant-learn` also commits confirmed changes. Inspect those commits
rather than assuming every change remains uncommitted.

## 1. Set up the assistant (10:45-11:00, 15 minutes)

In the assistant session, ask:

```text
Use assistant-setup to help me configure this local personal coding assistant.
Ask about my coding workflow and the kinds of help I want. Keep my decisions
separate from your suggestions. Write the resulting repository content in
English. Do not create a GitHub repository or push anything.
```

Answer with a real, non-sensitive preference, for example: "When a change
affects behaviour, explain its expected result before showing the diff."
Read the proposed changes before accepting them. Inspect the local Git diff.

**Checkpoint:** explain which part of `AGENTS.md` holds the durable preference
and which part is merely a suggestion. The setup must reflect your answers,
not a generic biography invented by the agent. This repository's `AGENTS.md`
is not automatically loaded into unrelated code repositories.

## 2. Teach one durable lesson (11:00-11:15, 15 minutes)

Use the learning skill:

```text
Use assistant-learn. I want a reusable preference for future coding work:
when reporting a failed command, include the command and its first relevant
error. Check for an existing equivalent, ask if scope is unclear, and propose
only the smallest useful update. Write it in English.
```

Review the change. Invoke `assistant-learn` again with the same lesson.
Compare the diff before and after the second invocation.

**Checkpoint:** the preference appears once. Explain why this rule should
survive the current chat, and why a temporary task status should not.

## 3. Create and try a skill (11:15-11:40, 25 minutes)

Choose a repeatable task such as preparing a bug report from supplied
reproduction notes. Use an English name such as `bug-report-notes`, not the
template-reserved `assistant-*` prefix. Ask:

```text
Use assistant-skill to create a small English skill for turning supplied
bug notes into a reproducible report. Include when to use it, required
inputs, steps and the expected output. Do not invent missing observations;
ask for them or mark them unknown. Show the proposed skill before saving.
```

Try it with:

```text
Use the bug-report skill we just created.
Notes: the room search returns an error when the requested end time equals
the start time. I have not recorded the app version or the exact error text.
```

Then try a non-trigger: "What is a Git branch?" The bug-report workflow
should not take over that unrelated conversation.

**Checkpoint:** the report distinguishes supplied observations from missing
facts. You can point to the skill's trigger and describe the output it
promises. If the trigger is too broad, narrow it and try again.
Your editable source is `.agents/skills/bug-report-notes/SKILL.md` if you
chose that name. `assistant-skill` installs the current source and commits
source changes locally; inspect its reported command and result.

## 4. Install personally and verify scope (11:40-11:55, 15 minutes)

Confirm the installation performed by `assistant-skill`. The reviewed
template procedure, run from the assistant repository root, is:

```shell
gh skill install --from-local . bug-report-notes --agent github-copilot --scope user --allow-hidden-dirs --force
```

Replace `bug-report-notes` if you chose another name. The app bundles `gh`;
the template uses its preview `skill` command. The source copy goes to
`~/.copilot/skills/<name>/`; `--force` replaces an installed copy.
Inspect the installed skill, not just the command's completion message.
Do not install another copy under a different name.

Start a **new session outside the assistant repository**, in another local
repository or a general chat as supported by the template's installation
procedure. Check the installed skills and invoke the skill you created.
Do not rely only on a session that already loaded the template-local skills.

**Checkpoint:** the skill is available in the new context. Explain the
difference between editing your source clone and updating its personal
installation. Re-run the same install command after every source change;
`gh skill update` skips these local installations and is not the refresh
procedure. The personal profile in `AGENTS.md` is not copied globally by this
skill installation.

## 5. Save and explain (11:55-12:00, 5 minutes)

Review `git status`, `git diff` and the local commits created by the skills.
Commit any remaining intended source changes using your normal Git workflow.
Keep `origin` pointing to the shared template and do not push personal commits.
Keep personal edits in `AGENTS.md` and your own skill directories, not in the
four shared `assistant-*` skills.

For later template updates, preserve your work and follow the template README:
setup configures this clone to merge template updates with `git pull`.
Resolve any conflict without discarding personal content, then reinstall
personal skills whose source changed. Local-only commits are not a backup.

Show the lecturer:

- The preference recorded once and the file that contains it.
- The new skill, a useful run and a deliberately unrelated prompt.
- The skill available outside the template clone after personal installation.

## If something is unavailable

| Problem | Continue with | What is not complete |
|---|---|---|
| Template download or app access fails | Follow the lecturer's walkthrough and draft your preference and skill in a local text file | Assistant setup and installed-skill verification |
| A required skill is missing | Compare the actual README and `/skills` output with the lecturer; inspect its source if available | Do not pretend that an ordinary prompt invoked that skill |
| Personal installation fails | Preserve the local source and demonstrate the repository-local skill | Personal installation remains pending; local availability is not proof of personal scope |

Jira and the Connector are not needed. Keep useful local work if a dependency
fails, and explicitly record the incomplete checkpoint.
