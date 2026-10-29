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
  `mattpocock-skills@mattpocock` plugin alongside it.
- Jira through the Atlassian Rovo Connector is optional. Every mandatory
  exercise must also work without Jira.

## Release status and unresolved integration values

**Draft for review, not the final preparation message.** Do not send the email
or run a command containing `TODO` or an unresolved `<placeholder>`.
The source inputs below are integrated for v0; publication and participant
results are not yet observed. The maintainer resolves the remaining values
after Friday's test. Do not substitute development copies for AGEL targets.

| Marker | Required value / evidence | Owner |
|---|---|---|
| `TODO_FRIDAY_RESULTS` | Results of Friday's rehearsal and resulting preparation changes | Coordinator |
| `TODO_PARTICIPANT_OS` | Participant operating systems and the observed wrapper/install procedures | Coordinator |
| `TODO_AGEL_ACCESS` | Published AGEL copies and participant account access | Coordinator |
| `TODO_DESKTOP_PLUGIN_TRIAL` | Actual desktop UI labels, install/update route, fresh-session discovery and manual-only slash invocation of plugin-provided skills | Lecturers |
| `TODO_VOLUNTEER` | One participant with marketplace branch/PR permission, Node.js 22+ and npm | Maintainer |
| `TODO_NPM_ACCESS` | That volunteer can complete `npm ci` using an approved npm registry route or cache | Volunteer / AGEL IT |

## Sample app

Participant repository:
[agel-data-and-ai-temp-poc/copilot-workshop-room-booking](https://github.com/agel-data-and-ai-temp-poc/copilot-workshop-room-booking).
The integrated source is pinned at
`316a0f6a2725c43bd70c6c7b721b1f5f7fb37e7b`, not yet evidence of an AGEL release.
It uses **Java 21 and Spring Boot 4.1.2**, Spring Data JPA, Flyway and local H2,
with a REST API, Swagger UI and HTTP Basic roles `EMPLOYEE`/`FACILITY_ADMIN`.
No Docker, database server or separate Maven installation is needed.

[Exercise 2](exercises/02-sample-app.md) contains the clone, wrapper build/run
commands, local-account cautions and the back-to-back bookings bug. Its larger
feature starts from `.scratch/recurring-bookings/idea.md` and stops at local
specification/ticket files. [Exercise 3](exercises/03-copilot-project.md) uses
the equipment-filter and CSV-export tasks, with facility documentation as an
optional third session. The availability-selection refactoring remains an
alternative supplied task, not a simultaneous second fix for the booking bug.

## Marketplace values

**This is the only place defining marketplace addresses and plugin names.**
The user confirmed this new marketplace for both installation and the whole
of exercise 4, including the `assistant-share` PR. Do not use the previous
marketplace. Confirmed configuration is not proof of publication, participant
access or a successful install; those live checks remain open.

| Setting | Value | Evidence needed |
|---|---|---|
| Marketplace repository (`owner/repo`) | [agel-data-and-ai-temp-poc/copilot-marketplace](https://github.com/agel-data-and-ai-temp-poc/copilot-marketplace) | Confirm participant access and permission to create a branch and PR here |
| Installed catalogue name | `copilot-marketplace` | Confirmed by the coordinator; verify the installed catalogue |
| Matt Pocock plugin | `matt-pocock-skills` | Source version **0.1.0**, 27 vendored skills |
| Sharing support plugin | `marketplace-maintenance` | Source version **0.3.0**; also the target for participant-authored contributions |
| Shared plugin version | `TODO_SHARED_VERSION` | Actual higher version of the sharing-support plugin after owner-approved merge/publication |
| Shared skill | `TODO_SHARED_SKILL` | Published name distinct from participants' personal example names |

Other materials refer to these settings rather than repeating their values.
Do not install an unrelated existing plugin as a substitute, or install the
upstream `mattpocock-skills@mattpocock` plugin alongside the vendored copy.
Marketplace source is pinned at `b7510db7dd83577844239674d5c4fbab31500b5d`.

### Marketplace installation and updates

**The desktop UI is the primary route.** The app has its own marketplace
registration, catalogue browsing, plugin installation and update management.
Exact UI labels and navigation remain unverified until Friday; the actions
below describe the procedure, not confirmed button names.

1. Open the app's marketplace/plugin management and add the Marketplace
   repository from the table above. Choose the AGEL GitHub account or approved
   system Git credentials when the app offers authentication.
2. Browse that catalogue and install the sharing-support and Matt Pocock
   plugins named above. Do not add the upstream duplicate.
3. Start a fresh desktop session. Inspect the installed versions and skills:
   `marketplace-install`, `marketplace-create-skill`, `marketplace-submit-update`,
   `/setup-matt-pocock-skills`, `/grill-with-docs`, `/to-spec`, `/to-tickets`,
   `diagnosing-bugs`, `tdd` and `code-review`. Listing is not invocation proof;
   apply the trial gate below.

After exercise 4's owner-approved merge/publication, refresh the catalogue
and update the changed sharing-support plugin **in the app UI**. Someone who
does not have it installed uses that UI's installation action. Record the
observed higher version, start a fresh session and invoke the shared skill.

### CLI fallback: separately installed only

If you already have a separately installed Copilot CLI, you may use its
plugin-management commands below as a fallback. Check `copilot --version`
first. Copilot CLI is not a participant prerequisite, and the coding/skill
exercises still run in the desktop app.

On the tested Windows app, the SDK-bundled `copilot.exe` is
not on the agent shell's PATH. Do not locate its private runtime or change
PATH to make these commands work. App and CLI share `installedPlugins` in
`~/.copilot/config.json`, so CLI-installed plugins are visible in the app;
do not edit that configuration by hand.

Do not treat the interactive CLI's `/plugin` or `/skills` as verified
desktop-app commands. This fallback is for **plugin management only**, not
skill invocation. CLI 1.0.105 fails user-only skill invocation in
both interactive TUI and non-interactive `-p` mode, even when its skill list
shows the skill enabled. Use the Matt Pocock workshop skills **only in the
desktop app**; do not treat CLI as a fallback for setup or planning.

```shell
copilot plugin marketplace add agel-data-and-ai-temp-poc/copilot-marketplace
copilot plugin marketplace browse copilot-marketplace
copilot plugin install marketplace-maintenance@copilot-marketplace
copilot plugin install matt-pocock-skills@copilot-marketplace
copilot plugin list
```

The fallback update after owner-approved publication is:

```shell
copilot plugin marketplace update copilot-marketplace
copilot plugin update marketplace-maintenance
```

Use its install command above for someone who has this CLI but not the plugin.
The source also documents `copilot plugin update matt-pocock-skills` for
changes to the vendored plugin; a participant skill must not modify that
vendored collection. Record the observed higher shared-plugin version,
start a fresh session and invoke the recorded shared skill.

### Skill invocation

Some skills are model-selected when their description matches the task.
Others declare `disable-model-invocation: true`: only the user invokes them
with a slash command. Naming such a skill in an ordinary prompt does not
let the model invoke it. Preserve the vendored frontmatter.

For exercise 2, the participant submits `/setup-matt-pocock-skills`,
then separately invokes `/grill-with-docs`, `/to-spec` and `/to-tickets`,
reviewing each result before the next command. Do not ask the model to
chain these user-only skills.

The desktop app supports explicit slash invocation with task text after the
name, for example `/grill-with-docs <task>`. The maintainer verified this with
a personal skill from `personal-agents`.
**Instructor note:** Friday must verify invocation of the plugin-provided
skills as well; the personal-skill result does not establish that.
Before clearing this trial, invoke all four setup/planning commands locally
in the app with task text, inspect their expected local outputs, and record
the working route in exercise 2. A picker listing alone does not pass this trial.
If a plugin skill cannot be invoked, use the exercise fallback and mark that
checkpoint incomplete. Do not switch participants to another client.

## Template alignment

The template interface is aligned with
[msucharda/copilot-assistant-template#2](https://github.com/msucharda/copilot-assistant-template/pull/2):
the participant clone URL is
`https://github.com/agel-data-and-ai-temp-poc/copilot-assistant-template.git`,
skills live in `.agents/skills/`, and personal installation uses `gh skill
install --from-local`. The published AGEL clone and desktop-app installation
still need Friday's live verification. The app bundles `gh`; do not add a
separate CLI prerequisite to the preparation message.
At template head `d873f8747d7c1cdf1b4b1e9fb254c038f471cc93`, both its README
and `assistant-share` use the confirmed marketplace destination above.
Recheck the published template version before the live exercise.

## Publication

This repository is the development copy. The coordinator publishes approved
milestones of `main` to the internal
`agel-data-and-ai-temp-poc/copilot-workshop` repository. These materials do
not perform that publication and do not include the Friday test-run checklist.

The Friday review milestone is 30 October at 10:00 CET for preparation and
exercise 1. Preparation is finalized after the 13:30 test and sent by the
maintainer around 16:00. Remaining materials are due Sunday 1 November at
18:00 CET.