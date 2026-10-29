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

Use the existing DevSecOps Project and a coherent example already present
there. The read-only reference repository is `D:\git\devsecops-platform`.
Select actual example links/commits while preparing the demo:
**`TODO_DEMO_SPEC`**, **`TODO_DEMO_TICKETS`**, **`TODO_DEMO_SESSIONS`**,
**`TODO_DEMO_REVIEW_MERGE`**. Do not fabricate a completed history.
Use completed, inspectable work rather than depending on a fresh long build
or a cloud change during the talk.

| Time | Demonstration cue | Human decision to point out |
|---|---|---|
| 09:15-09:20 | Open the existing Copilot Project. Show the starting intent and the resulting change. "Here is the result; now trace how we got it." | What outcome was worth pursuing? |
| 09:20-09:27 | Open `CONTEXT.md` and one relevant `docs/adr/` record, then the selected spec. Show a clarified ambiguity and acceptance criterion. | The agent asks; the human decides the intended behaviour. |
| 09:27-09:34 | Show the selected tickets and their dependencies. `AGENTS.md` points to `docs/agents/issue-tracker.md` and domain documentation. | Which work can start independently? Which must wait? |
| 09:34-09:44 | Show 2-3 real sessions, their assignments and distinct worktrees. Open a session question and its resulting scope correction. | The Project helps one person coordinate agents; it does not remove that person's decisions. |
| 09:44-09:54 | Show a real diff, local validation evidence and review feedback with its disposition, then the actual recorded merge result. | A convincing narrative is not evidence that the change works. |
| 09:54-10:00 | Ask participants to identify one reusable workflow and one decision they would keep. Preview exercise 3's local-only variant. | More simultaneous sessions are useful only when tasks can be reviewed and integrated. |

The reference repository uses domain terms from `CONTEXT.md`, relevant ADRs
and tracker instructions. Show those relationships without copying its
project-specific instructions into participants' assistants.

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

The local marketplace's `marketplace-install` skill documents `/plugin`
commands in app sessions. After resolving `TODO_MATT_POCOCK_PLUGIN`, use:

```text
/plugin marketplace add agel-data-and-ai-temp-poc/ai-dev-marketplace
/plugin marketplace browse ai-dev-marketplace
/plugin install TODO_MATT_POCOCK_PLUGIN@ai-dev-marketplace
/plugin install marketplace-maintenance@ai-dev-marketplace
```

Start a new session and inspect `/skills`. Confirm the actual vendored skills,
including the ones required by the app exercise, plus `marketplace-create-skill`
and `marketplace-submit-update` for sharing. Record the plugin versions.
If the catalogue does not contain the expected plugin, stop rather than
installing `ai-dev` as a substitute or adding upstream `mattpocock/skills`.

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
| 16:25-16:35 | Marketplace owner reviews/merges; after publication, others update `TODO_SHARED_PLUGIN`, open a new session and try the skill. | Another participant can invoke the published version. |
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
- Marketplace `README.md`,
  `plugins/marketplace-maintenance/skills/marketplace-install/SKILL.md` and
  `.github/plugin/marketplace.json`: app `/plugin` install/update, new-session
  availability, `ai-dev-marketplace` catalogue, versioned plugin publication.

The template instructions are aligned with
[msucharda/copilot-assistant-template#2](https://github.com/msucharda/copilot-assistant-template/pull/2):
`.agents/skills/` source, local commits, preview `gh skill install`,
`AGENTS.md` scope and the two marketplace-maintenance handoff skills.
The published app PR, pending Matt Pocock plugin and Friday's observations
still need integration. The app `/plugin` route is documented by the
marketplace reference, but has not yet been verified in the AGEL desktop-app
test. These notes are not a Friday checklist.
