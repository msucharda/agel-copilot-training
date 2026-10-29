# Exercise 2: from a bug to feature tickets

**13:00-14:30 CET, 90 minutes.** Work alone on the local Java room-booking
sample app in the Copilot desktop app.

**Result:** one reproduced and fixed bug with evidence, plus a reviewed
specification and tickets for a larger feature. Stop the larger feature at
tickets; do not implement it in this block.

## Before you start

Use JDK 21. Obtain the actual values below from the sample app README and the
lecturer; do not run the placeholders or invent task files.

| Value | Integration status |
|---|---|
| Published clone URL | `TODO_SAMPLE_APP_URL` |
| Build and test command | `TODO_APP_VERIFY_COMMAND` |
| Local run command and observable result | `TODO_APP_RUN_COMMAND` |
| Bug brief in `.scratch/` | `TODO_BUG_TASK` |
| Larger-feature brief in `.scratch/` | `TODO_FEATURE_TASK` |

The AGEL vendored Matt Pocock plugin must be installed from the morning
theory block. Do not install `mattpocock/skills` separately.

## 1. Establish the baseline (13:00-13:15, 15 minutes)

If you do not already have the sample clone, use the published URL:

```shell
git clone TODO_SAMPLE_APP_URL agel-room-booking
cd agel-room-booking
git status --short
```

Add this existing local directory as a repository in the Copilot app and
start a session. Read the app README. Run its verified build/test command,
`TODO_APP_VERIFY_COMMAND`, and its local run command,
`TODO_APP_RUN_COMMAND`. Record what succeeded or failed before making changes.
Do not create a GitHub repository, fork, PR or remote branch.

## 2. Set up the coding workflow (13:15-13:25, 10 minutes)

Ask in the sample-app session:

```text
Use setup-matt-pocock-skills for this repository. Read its current
instructions and README first. Explain the proposed changes, then configure
the repository to use the AGEL vendored Matt Pocock skills. Do not install
the upstream plugin, publish a repository or start unrelated work.
```

Inspect the diff and verify the resulting instructions in a new session.
Use `/skills` to confirm that the relevant workflow skills are available.

**Checkpoint:** identify what changed in the repository and what comes from
the installed plugin. A skill name in a document is not proof that the skill
is installed.

## 3. Reproduce and fix one bug (13:25-14:00, 35 minutes)

Open `.scratch/TODO_BUG_TASK` only after the actual filename has been supplied.
Ask:

```text
Read the selected .scratch bug brief. First reproduce its exact symptom and
record the expected versus actual behaviour. Use the installed diagnosis and
test-first workflow skills where applicable. Make the smallest complete fix,
run the relevant tests and show evidence that the original symptom is gone.
Stay local; do not open a PR or push.
```

Read the reproduction before accepting a fix. A test that was already green
does not establish that the bug existed. Review the final diff and save a
local commit using your normal Git workflow.

**Checkpoint:** show the reproduction, the changed behaviour and the relevant
passing check. If the baseline failed for an environment reason, keep that
separate from the bug result.

## 4. Shape a larger feature, stopping at tickets (14:00-14:25, 25 minutes)

Read `.scratch/TODO_FEATURE_TASK`, using its actual filename. Ask:

```text
Use the installed planning skills to clarify the selected larger-feature
brief. Ask about ambiguous behaviour, write a bounded specification with
observable acceptance criteria, then split it into independently verifiable
local tickets with explicit dependencies. Keep all output local. Do not
create tracker issues, implement the feature, start sessions or push.
```

Review at least one ambiguous case and one dependency. If the agent proposes
more work than you can review in five minutes, reduce the scope.
Keep the tickets in the local location chosen by the app's documented
workflow; do not create GitHub or Jira tickets for this exercise.

## 5. Inspect the handoff (14:25-14:30, 5 minutes)

Show the lecturer the bug result, the feature acceptance criteria and the
local ticket list. Label each ticket with an observable completion condition.
The feature remains unimplemented.

Exercise 3 uses the lecturer's selected tasks already supplied in `.scratch/`.
Do not substitute your new feature tickets for that set unless the lecturer
has checked that they are independent and fit the next block.

## If something is unavailable

| Problem | Continue with | What is not complete |
|---|---|---|
| JDK, Maven download or sample app fails | Inspect the supplied task and follow the lecturer's demonstrated baseline; write the local feature spec | You have not verified a working local app or bug fix |
| Marketplace/plugin is unavailable | Inspect the available skill sources and draft a spec using ordinary prompts | Installation and `setup-matt-pocock-skills` verification remain pending |
| Sample tasks are not published | Use the lecturer's approved brief when supplied; otherwise observe and draft questions | Do not invent a bug and claim to have fixed the required task |

No mandatory step uses Jira or the Atlassian Rovo Connector.
