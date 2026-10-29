# AGEL Copilot workshop

**Monday 2 November 2026, 09:00-17:00 CET.** Svätoplukova 2A,
Bratislava, with remote participation through Teams. Participants work
individually in the **GitHub Copilot desktop app**.

Build a personal coding assistant that you can maintain, use skills to turn
intent into verifiable work, and coordinate several local coding sessions
through a Copilot Project. Git knowledge is assumed; skills and Projects are
introduced from the beginning.

## Materials

| Material | Audience | When to use it |
|---|---|---|
| [Preparation instructions](docs/preparation.md) | Participants, Microsoft, AGEL | Before Monday; draft pending Friday's test results |
| [Preparation email](docs/preparation-email.md) | Workshop maintainer | Send after Friday's test, around 16:00 CET |
| [Facilitator script](docs/facilitator-script.md) | Lecturers | Full-day timings, demo cues, checkpoints and fallbacks |
| [Theory slides](slides/agentic-workshop.html) | Everyone | Open the file in a browser; 12 slides, no server needed |
| [Exercise 1: personal assistant](exercises/01-personal-assistant.md) | Participants | 10:45-12:00 |
| [Exercise 2: from bug to feature tickets](exercises/02-sample-app.md) | Participants | 13:00-14:30 |
| [Exercise 3: your Copilot Project](exercises/03-copilot-project.md) | Participants | 14:45-16:00 |
| [Exercise 4: share a skill](exercises/04-share-a-skill.md) | Participants | 16:00-16:40 |

The slides support only the theory block. The remaining blocks are live
demonstrations or individual exercises, guided by the facilitator script.
Use the slide navigation buttons, Left/Right arrows, Home/End, or a direct
`#slide-1` through `#slide-12` link. Printing shows all slides.
Use **Fullscreen** for presenting; on desktop the deck keeps a 16:9 slide
inside the available viewport.

## Day plan

| Time (CET) | Block |
|---|---|
| 09:00-09:15 | Goals, preparation check |
| 09:15-10:00 | DevSecOps Project demo: intent -> spec -> tickets -> sessions -> review -> merge |
| 10:00-10:30 | Agentic approach, knowledge layers, skills and marketplace installation |
| 10:30-10:45 | Break |
| 10:45-12:00 | Exercise 1: personal assistant and personal installation |
| 12:00-13:00 | Lunch |
| 13:00-14:30 | Exercise 2: sample app, bug fix, larger feature up to tickets |
| 14:30-14:45 | Break |
| 14:45-16:00 | Exercise 3: own Project, 2-3 worktree sessions, local merge |
| 16:00-16:40 | Exercise 4: one live marketplace PR, plugin update; optional Jira |
| 16:40-17:00 | Maintaining the assistant and questions |

## Working agreement

- Write prompts, documentation, skills and other workshop output in English.
- Work alone on local clones. Do not create a participant repository on GitHub.
- Exercise 3 uses local merges to `main`, not PRs or GitHub Copilot review.
- Exercise 4 is the single exception: one designated participant creates a
  branch and live PR in the shared marketplace, with the required permission.
- Install the AGEL vendored Matt Pocock plugin, not the upstream
  `mattpocock/skills` plugin alongside it.
- Jira through the Atlassian Rovo Connector is optional. Every mandatory
  exercise must also work without Jira.

## Release status and unresolved integration values

**Draft for review, not the final preparation message.** Do not send the email
or run a command containing `TODO` or an unresolved `<placeholder>`.
The maintainer replaces the following
values after checking the sibling repositories and Friday's test results.
Development repositories below are references, not participant clone targets.

| Marker | Required value / evidence | Owner |
|---|---|---|
| `TODO_SAMPLE_APP_URL` | Published workshop Java app clone URL; source: [sample app](https://github.com/msucharda/copilot-workshop-room-booking) | Coordinator |
| `TODO_APP_VERIFY_COMMAND` | JDK 21 build/test command from the sample app README | Sample app session |
| `TODO_APP_RUN_COMMAND` | Local run command and expected result from the sample app README | Sample app session |
| `TODO_BUG_TASK` | Existing `.scratch/` bug task filename and baseline symptom | Sample app session |
| `TODO_FEATURE_TASK` | Existing `.scratch/` larger-feature brief, ending at tickets | Sample app session |
| `TODO_PROJECT_TASK_A`, `TODO_PROJECT_TASK_B`, `TODO_PROJECT_TASK_C` | Two required and one optional existing `.scratch/` tasks with compatible acceptance criteria | Sample app session |

## Marketplace values

**This is the only place defining marketplace addresses and plugin names.**
The maintainer is preparing a new marketplace; its address and the vendored
Matt Pocock plugin name are not confirmed. The sharing destination also
awaits confirmation. No participant should check permission against a guessed
repository or submit a PR until the coordinator confirms these values.

| Setting | Value | Evidence needed |
|---|---|---|
| Marketplace repository (`owner/repo`) | `TODO_MARKETPLACE_REPOSITORY` | Coordinator-confirmed address and sharing destination |
| Installed catalogue name | `TODO_MARKETPLACE_NAME` | Name reported by the confirmed marketplace catalogue |
| Matt Pocock plugin | `TODO_MATT_POCOCK_PLUGIN` | Published plugin containing all his vendored skills |
| Sharing support plugin | `TODO_SHARING_SUPPORT_PLUGIN` | Provides `marketplace-create-skill` and `marketplace-submit-update` for the confirmed destination |
| Shared plugin and version | `TODO_SHARED_PLUGIN` | Name/version published after the exercise-4 PR is reviewed and merged |
| Shared skill | `TODO_SHARED_SKILL` | Published name distinct from participants' personal example names |

Other materials refer to these settings rather than repeating their values.
Do not install an unrelated existing plugin as a substitute, or install the
upstream `mattpocock/skills` plugin alongside the vendored copy.

### Marketplace commands

In a Copilot app session, replace each bracketed field with its confirmed
setting above. These are command shapes, **not executable final commands**.
Verify them against the new marketplace's README before the workshop.

```text
/plugin marketplace add <marketplace-repository>
/plugin marketplace browse <catalogue-name>
/plugin install <matt-pocock-plugin>@<catalogue-name>
/plugin install <sharing-support-plugin>@<catalogue-name>
```

After exercise 4's owner-approved merge and publication:

```text
/plugin marketplace update <catalogue-name>
/plugin update <shared-plugin>
```

For someone who has not installed the shared plugin yet, use
`/plugin install <shared-plugin>@<catalogue-name>` after refreshing the
catalogue. Start a new session and check `/skills`.

## Template alignment

The template interface is aligned with
[msucharda/copilot-assistant-template#2](https://github.com/msucharda/copilot-assistant-template/pull/2):
the participant clone URL is
`https://github.com/agel-data-and-ai-temp-poc/copilot-assistant-template.git`,
skills live in `.agents/skills/`, and personal installation uses `gh skill
install --from-local`. The published AGEL clone and desktop-app installation
still need Friday's live verification. The app bundles `gh`; do not add a
separate CLI prerequisite to the preparation message.
Its sharing instructions must also match the confirmed marketplace
destination; do not follow a stale hard-coded target from a template version.

## Publication

This repository is the development copy. The coordinator publishes approved
milestones of `main` to the internal
`agel-data-and-ai-temp-poc/copilot-workshop` repository. These materials do
not perform that publication and do not include the Friday test-run checklist.

The Friday review milestone is 30 October at 10:00 CET for preparation and
exercise 1. Preparation is finalized after the 13:30 test and sent by the
maintainer around 16:00. Remaining materials are due Sunday 1 November at
18:00 CET.