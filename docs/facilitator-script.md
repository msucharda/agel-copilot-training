# Facilitator script

**Monday 2 November 2026, 09:00-17:00 CET, AGEL, Bratislava + Teams.**
Use live app demonstrations except for the 10:00 theory block.
Participants work individually; no team assignment is scheduled.

The learning arc is: **see a complete Project -> understand the mechanisms ->
build a personal assistant -> use it on an app -> coordinate agents -> share
and maintain a skill**. Demonstrate outcomes and human decisions, not a race
to produce the most code.

## Status and operating notes

- This is a draft. Resolve the [integration values](../README.md#release-status-and-unresolved-integration-values)
  before presenting the dependent steps. Never type a `TODO` command live.
- The Java app and its six `.scratch/` tasks are being developed separately.
  Their exact commands and filenames must come from the reviewed app README.
- Use the GitHub Copilot desktop app, including its session terminal when
  needed. Do not silently substitute VS Code, browser chat or standalone CLI.
- Share the app window in Teams, enlarge text, read task prompts aloud and
  repeat spoken questions for remote participants. Check remote audio at
  the introduction and after lunch.
- Do not create GitHub repositories for participants. Exercise 3 stays local;
  exercise 4 has exactly one participant PR to the shared marketplace.
- All written output is English. Jira uses Atlassian **Rovo**, and is optional.
- A fallback preserves learning, not completion status. Mark any unverified
  checkpoint explicitly; do not present a walkthrough as a successful install.

This script is for Monday. The Friday test-run checklist is deliberately
not included.

## 09:00-09:15 | Introduction and preparation check

**Goal:** everyone knows the destination, the client and where to ask for help.

| Time | Say / do | Observe |
|---|---|---|
| 09:00-09:05 | "Today you will build an assistant you own and maintain, then use a Project to get help from several agents." Introduce lecturers and remote audio route. | Remote participants hear and see the app. |
| 09:05-09:10 | Show the [day plan](../README.md#day-plan). Explain individual local work and the single marketplace PR exception. | Participants do not start creating GitHub repos. |
| 09:10-09:15 | Ask participants to open the desktop app with their AGEL account and their template clone. Check Git and JDK results from [preparation](preparation.md). | Licence, sign-in or install failures are identified before exercise 1. |

Microsoft supplies licences through
`github-agl-aiworkshop-copilot-users`, materials and lecturers.
AGEL supplies JDK installation permission, GitHub/Maven Central network
access and optional Jira access.

**Fallback:** if accounts, licence or network fail, direct the affected person
to the supporting lecturer while they observe the demo and retain local notes.
If Teams fails, use the invitation's agreed support route; do not assume remote
participants can follow an inaudible room conversation. Connector and
marketplace availability do not block this introduction.

## 09:15-10:00 | DevSecOps Copilot Project demonstration

**Goal:** show one person directing intent -> spec -> tickets -> sessions ->
review -> merge, before explaining the mechanics.

Use **the local-CI performance story, 27-28 October 2026**, in the existing
Project for [msucharda/devsecops-platform](https://github.com/msucharda/devsecops-platform).
The read-only local reference is `D:\git\devsecops-platform`.
Show completed work and its recorded evidence; do not start a fresh overnight
run or make a cloud change during the talk.

### Main story: from a slow feedback loop to three integrated changes

**All times in this main story are CET (UTC+1).** The maintainer supplied the
Project/session timeline. Issue creation and PR creation/merge timestamps
were cross-checked against GitHub.

| Date and time | Open / explain |
|---|---|
| 27 Oct, 20:19 | User intent in the Project, English translation: "Once the current work finishes, we must focus on local CI speed. It cannot continue like this." |
| 27 Oct, 20:35 | Analysis session: "Local CI speed: analysis and proposal" (English translation of its title). |
| 27 Oct, 21:28 | The maintainer delegates autonomous work and goes offline. This is a scope decision, not evidence that every later question has already been answered. |
| 27 Oct, 21:29 | New specification in [msucharda/devsecops-platform#134](https://github.com/msucharda/devsecops-platform/issues/134), alongside existing [msucharda/devsecops-platform#107](https://github.com/msucharda/devsecops-platform/issues/107). |
| 27 Oct, 21:31 | Three parallel sessions: the local gate, mutation-runtime work, and action pins with Dependabot. |
| 27 Oct, 21:54 / 22:00 / 23:50 | PRs open: action pins [msucharda/devsecops-platform#135](https://github.com/msucharda/devsecops-platform/pull/135), mutation runtime [msucharda/devsecops-platform#137](https://github.com/msucharda/devsecops-platform/pull/137), local gate [msucharda/devsecops-platform#138](https://github.com/msucharda/devsecops-platform/pull/138), respectively. |
| Overnight | Sessions surface TDD interface confirmations and align the shared `LOCAL_CI_WORKER_BUDGET` contract. The maintainer reports that a `security-checkpoint` review found a High finding in the action-pins PR. Show the actual question/review and its disposition; do not treat a question or finding as resolved merely because work continued. |
| 28 Oct, 08:54 / 09:08 / 09:28 | Merges, respectively: mutation runtime [msucharda/devsecops-platform#137](https://github.com/msucharda/devsecops-platform/pull/137), action pins [msucharda/devsecops-platform#135](https://github.com/msucharda/devsecops-platform/pull/135), local gate [msucharda/devsecops-platform#138](https://github.com/msucharda/devsecops-platform/pull/138). |

The intent becomes observable requirements in the local-gate issue: broad
Windows pre-push runs had taken 90-95 minutes; the requested local-feedback
target is five minutes p95. **That target is not a measured result.** Open
the PR's actual measurements before claiming a speed-up.

Keep the lanes distinct: the local-gate issue leads to the local-gate PR;
the existing mutation issue leads to the mutation-runtime PR; action pins
are the third session. Show how a shared worker-budget contract crosses
session boundaries without turning the sessions into a team exercise.

| Time | Demonstration cue | Human decision to point out |
|---|---|---|
| 09:15-09:20 | Show the three merged PRs, then return to the 20:19 intent. "Here is the result; now trace how we got it." | What outcome was worth pursuing? |
| 09:20-09:27 | Open `CONTEXT.md`, a relevant ADR and the local-gate issue. Contrast a speed complaint with the five-minute p95 acceptance target. | The agent analyses; the human chooses the intended outcome. |
| 09:27-09:34 | Open the existing mutation issue and the three task/PR lanes above. Show dependencies rather than implying all three solve the same issue. | Which work can start independently? Which contract must be shared? |
| 09:34-09:44 | Show the three real sessions and their worktrees. Inspect a TDD confirmation and the `LOCAL_CI_WORKER_BUDGET` agreement. | Autonomy still produces questions; distinguish answered, pending and completed work. |
| 09:44-09:54 | Show the review's High finding and disposition, a real diff, validation evidence and the next-morning merges. Stay on how agents help, not implementation details of the controls. | A review can change the work; a completed narrative is not proof of correctness. |
| 09:54-09:57 | Use the retrospective supplement below to show agents improving the workflow itself. | Hypotheses become useful only after evidence and a bounded change. |
| 09:57-10:00 | Ask for one reusable workflow and one retained human decision; preview exercise 3's local-only variant. | More sessions help only if their results can be reviewed and integrated. |

The reference repository uses domain terms from `CONTEXT.md`, relevant ADRs
and tracker instructions. Show those relationships without copying its
project-specific instructions into participants' assistants.

### Supplement for agenda point 3: agents improve the way you work

Use this as the three-minute morning supplement and recall it briefly at
14:45. **These events are on 22-23 October and use CEST (UTC+2), not CET.**

| Date and time | Evidence / teaching cue |
|---|---|
| 22 Oct, 16:39 | The maintainer asks for a deep retrospective across sessions. Parallel subagents produce hypotheses H4 and H7. A hypothesis is not yet a verified finding. |
| 22 Oct, before 19:16 | Experiments turn the hypotheses into bounded specifications. Ask what observation would support or reject a proposed workflow change. |
| 22 Oct, 19:16 | Resulting issues: local-CI workflow [msucharda/devsecops-platform#84](https://github.com/msucharda/devsecops-platform/issues/84) and merge workflow [msucharda/devsecops-platform#85](https://github.com/msucharda/devsecops-platform/issues/85). |
| 23 Oct, 11:10 | Local-CI workflow PR [msucharda/devsecops-platform#93](https://github.com/msucharda/devsecops-platform/pull/93) merges. |
| 23 Oct, 11:52 | Merge-workflow PR [msucharda/devsecops-platform#90](https://github.com/msucharda/devsecops-platform/pull/90) merges. |
| Same retrospective | The maintainer reports that `issue-kickoff` and `security-checkpoint` also emerged as reusable skills. Show their purpose, not a separate implementation lecture. |

The Project/session sequence and skill origins above are maintainer-provided;
GitHub verifies the issue/PR references and timestamps. Do not assign H4 or
H7 to an individual issue without the retrospective evidence. The lesson is
one person using agents to analyse friction, test a hypothesis, specify a
change and retain a useful procedure.

**Fallback:** if the live Project or network is unavailable, walk through a
previously saved, approved view of the same spec, tickets, session assignments,
diff and review/merge evidence. If that evidence has not been prepared, label
the flow as a schematic, not an observed successful run. Marketplace and
Connector failures do not require installing anything for this demo.

## 10:00-10:30 | Theory and marketplace

**Goal:** participants distinguish intent, instructions, skill, plugin,
marketplace, Connector and Project before using them.

Open [the 12-slide deck](../slides/agentic-workshop.html).

| Time | Slides / action | Key statement |
|---|---|---|
| 10:00-10:05 | 1-3: outcome, intent loop, human decisions | "Name the outcome and the evidence, not just the coding activity." |
| 10:05-10:10 | 4-6: knowledge layers and packaging | "A skill is a repeatable workflow; a plugin distributes skills; a marketplace lists plugins." |
| 10:10-10:15 | 7-9: Connector, skill contract, lifecycle | "A Connector supplies permitted external information; it is not the workflow itself." |
| 10:15-10:18 | 10-12: Project worktrees, sharing, day map | "Create your own Project later; first build the assistant." |
| 10:18-10:30 | Install the AGEL marketplace and vendored Matt Pocock plugin; open a new session and check skills. | "Install the AGEL copy only, not the upstream plugin as well." |

Use the single [marketplace values and commands](../README.md#marketplace-values)
section. The address, catalogue and plugin names are confirmed there.
Do not reuse a previous marketplace address or execute command shapes before
substituting the settings. Check the new marketplace's README and verify the
app installation route before the workshop; publication/access remain untested.

Start a new session and inspect `/skills`. Confirm the actual vendored skills,
including the ones required by the app exercise, plus `marketplace-create-skill`
and `marketplace-submit-update` for sharing. Record the plugin versions.
If the catalogue does not contain the expected plugin, stop rather than
installing another plugin as a substitute or adding upstream
`mattpocock-skills@mattpocock`.

**Fallback:** the deck is self-contained and opens offline. If marketplace
registration or installation fails, show the reviewed local skill source and
its expected trigger; retain the installation as incomplete. Do not spend the
break debugging every account. Jira/Connector availability has no bearing on
the installation checkpoint.

## 10:30-10:45 | Break

Put the return time on screen and leave the exercise 1 link visible.
The supporting lecturer may help with preparation failures without changing
the group schedule.

**Fallback:** if the network is down, keep the locally saved exercise visible;
the break and return time do not depend on marketplace or Connector access.

## 10:45-12:00 | Exercise 1: personal assistant

Open [exercise 1](../exercises/01-personal-assistant.md).

| Time | Facilitation cue | Checkpoint |
|---|---|---|
| 10:45-11:00 | Use `assistant-setup`; demonstrate how to answer one setup question. | A reviewed local preference, not invented personal facts. |
| 11:00-11:15 | Use `assistant-learn` and repeat the same lesson. | No duplicate durable rule. |
| 11:15-11:40 | Use `assistant-skill`, test the resulting workflow and an unrelated prompt. | A specific trigger and honest handling of missing input. |
| 11:40-11:55 | Verify `assistant-skill` installed with `gh skill install --from-local . NAME --agent github-copilot --scope user --allow-hidden-dirs --force`. Start a new session outside the clone. | Personal skill availability, not automatic global loading of `AGENTS.md`. |
| 11:55-12:00 | Ask participants to review and save a local commit. | They can explain source clone versus installed copy and how to refresh it. |

At 11:35, ask who has reached the skill test; help participants finish one
small skill rather than starting several. Do not require personal or company
secrets as assistant-learning examples.

**Fallback:** if template skills or personal installation are unavailable,
preserve the local preference and skill draft, use the source walkthrough and
mark the relevant checkpoint incomplete. Marketplace/network failure does
not justify claiming a prompt used a skill it never loaded. Jira is unused.

## 12:00-13:00 | Lunch

Announce 13:00 restart and exercise 2's app/JDK requirement.

**Fallback:** display the return time locally; no Connector, marketplace or
network action is required during lunch.

## 13:00-14:30 | Exercise 2: sample app

Open [exercise 2](../exercises/02-sample-app.md), check Teams audio again and
use the reviewed Java app's README. Do not improvise its build command.

| Time | Facilitation cue | Checkpoint |
|---|---|---|
| 13:00-13:15 | Clone `TODO_SAMPLE_APP_URL`; run `TODO_APP_VERIFY_COMMAND` and `TODO_APP_RUN_COMMAND`. | Observed baseline and JDK 21. |
| 13:15-13:25 | Run `setup-matt-pocock-skills`; inspect its changes and the available installed skills. | Repository setup versus plugin installation are distinct. |
| 13:25-14:00 | Work on `.scratch/TODO_BUG_TASK`: reproduce, test, fix, verify, review diff. | Original symptom reproduced and gone after the fix. |
| 14:00-14:25 | Clarify `.scratch/TODO_FEATURE_TASK`, write a spec and local tickets with dependencies. | Stop at tickets: no feature implementation or tracker writes. |
| 14:25-14:30 | Inspect one bug result and one ticket's acceptance criteria. | Participants can describe the evidence and the remaining work. |

**Fallback:** if Java/Maven or network fails, use the lecturer's observed
baseline and task text to draft the spec and reproduction plan. If the
marketplace is down, inspect reviewed skill sources and use plain prompts
without calling that a completed skill installation. If the app tasks remain
unpublished, label the exercise blocked rather than inventing acceptance
criteria. Jira/Connector failures do not change this block.

## 14:30-14:45 | Break

Ask participants to preserve exercise 2 work and return ready to create a
Project. Leave exercise 3 visible.

**Fallback:** use the saved instruction file if the network is unavailable;
neither marketplace nor Connector is needed for the break.

## 14:45-16:00 | Exercise 3: own Copilot Project

Open [exercise 3](../exercises/03-copilot-project.md).
This block covers how one person gets help from agents, not team roles.
Recall the morning retrospective: the agent can help identify friction in
your own workflow as well as implement a task. Keep the exercise's 75-minute
schedule unchanged.

| Time | Facilitation cue | Checkpoint |
|---|---|---|
| 14:45-14:55 | Preserve exercise 2 work, add the existing local app clone, create a Project based on local `main`. | No remote repository creation. |
| 14:55-15:05 | Have the Project start two sessions for `TODO_PROJECT_TASK_A/B`; add `TODO_PROJECT_TASK_C` only if useful. | Each session has a bounded `.scratch/` task and its own worktree. |
| 15:05-15:35 | Read questions and diffs; require `code-review` and a disposition for every finding in each session. | Local skill review, not GitHub Copilot PR review. |
| 15:35-15:55 | Merge ready results one at a time into local `main`; rerun the documented app checks on the combination. | No PR, push or GitHub review. |
| 15:55-16:00 | Ask each participant to identify one human coordination decision. | A Project with 2-3 reviewed sessions and a verified local result. |

At 15:25, discourage starting more work. At 15:35, freeze new assignments
and integrate only verified changes. A shared file conflict is a reason to
inspect task intent, not to discard one session's work.

**Fallback:** if Projects or sessions are unavailable, show the lecturer's
prepared Project and record the missing participant checkpoint. If a skill
review cannot run, preserve the diff but do not integrate it as reviewed.
If only one session finishes, show the honest partial result. Network,
marketplace or Connector problems do not authorize a substitute GitHub PR.

## 16:00-16:40 | Exercise 4: sharing and optional Jira

Open [exercise 4](../exercises/04-share-a-skill.md).
This is the single live participant PR, not a new repository exercise.

| Time | Facilitation cue | Checkpoint |
|---|---|---|
| 16:00-16:10 | Everyone prepares a general-purpose skill; designate one volunteer with marketplace branch/PR permission. | Reviewed English content and an identified target plugin. |
| 16:10-16:25 | Volunteer invokes `assistant-share`, inspects the preview, confirms publication and creates one real PR. | Actual marketplace URL, validation and version/catalog changes. |
| 16:25-16:35 | Marketplace owner reviews/merges; after publication, others update the shared plugin recorded in the README, open a new session and try the skill. | Another participant can invoke the published version. |
| 16:35-16:40 | Optional read-only Jira example through Atlassian Rovo, only if available. | Identify intent and acceptance criteria; no mandatory dependency. |

The marketplace owner decides whether to merge. Do not present an unmerged
PR as a published plugin. Use the actual updated version to distinguish the
marketplace result from an existing personal/local skill copy.

**Fallback:** without branch/PR permission or network, preserve the local
share preview and mark the live PR pending; do not publish to a different
repository. Without a reviewed merge, defer plugin verification. If Rovo or
Jira is unavailable, skip only the last five minutes and use the local feature
brief to discuss the same information flow.

## 16:40-17:00 | Maintenance and questions

| Time | Facilitation cue | Takeaway |
|---|---|---|
| 16:40-16:48 | Return to the assistant source clone. Show `assistant-learn`, `assistant-skill`, `assistant-share`, then the README's `git pull` template-update procedure after preserving local work. | Personal files and shared `assistant-*` paths have different owners. Reinstall personal skills after source changes; `gh skill update` skips local installs. |
| 16:48-16:55 | Describe the next maintenance cycle: try a real task, capture one useful lesson, test its trigger and output, commit locally, update personal installation, share only if useful. | Do not accumulate duplicate or obsolete instructions. |
| 16:55-17:00 | Questions. Ask: "Which task will you try first, and what result would show the assistant helped?" | A bounded next task and observable evidence. |

**Fallback:** if marketplace/network is unavailable, show the local source and
write down the actual refresh/share step for later; do not claim publication.
Connector failure is irrelevant. Preserve an explicit list of incomplete
individual checkpoints for follow-up rather than extending the workshop.

## Source alignment notes

Verified against the maintainer's read-only local references:

- DevSecOps `AGENTS.md`, `CONTEXT.md`, `docs/agents/domain.md` and
  `docs/agents/issue-tracker.md`: domain vocabulary/ADRs before exploration,
  GitHub issues and explicit tracker conventions.
- Legacy marketplace reference `README.md`,
  `plugins/marketplace-maintenance/skills/marketplace-install/SKILL.md` and
  `.github/plugin/marketplace.json`: app `/plugin` install/update, new-session
  availability and versioned plugin publication. This is prior reference
  evidence, not the confirmed workshop marketplace's address or an installation
  target.

The template instructions are aligned with
[msucharda/copilot-assistant-template#2](https://github.com/msucharda/copilot-assistant-template/pull/2):
`.agents/skills/` source, local commits, preview `gh skill install`,
`AGENTS.md` scope and the two marketplace-maintenance handoff skills.
The published app PR, new marketplace implementation and Friday's observations
still need integration. The template's sharing target is verified against
the confirmed settings at the source head recorded in the workshop README.
Recheck the published AGEL copy before live use. The app `/plugin` route is documented by the
legacy reference, but the new marketplace and AGEL desktop-app test remain
unverified. These notes are not a Friday checklist.
