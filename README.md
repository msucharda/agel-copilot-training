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
| `TODO_DESKTOP_PLUGIN_TRIAL` | Actual desktop Customize controls, install/update route and fresh-session skill discovery | Lecturers |
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

### Marketplace commands

In the **desktop app**, inspect **Customize** for marketplace/plugin controls.
Their exact route and behavior remain part of the desktop-plugin trial above; a terminal
command being documented is not evidence that the desktop controls work.
Do not treat the interactive CLI's `/plugin` or `/skills` as verified
desktop-app commands, or switch participants to another client.

These are the new marketplace's documented **terminal** commands, for the
lecturer to verify through the app's session terminal before live use.
They do not add a standalone CLI installation to participant preparation.
If the tool is unavailable there, report the installation checkpoint blocked.

```shell
copilot plugin marketplace add agel-data-and-ai-temp-poc/copilot-marketplace
copilot plugin marketplace browse copilot-marketplace
copilot plugin install marketplace-maintenance@copilot-marketplace
copilot plugin install matt-pocock-skills@copilot-marketplace
copilot plugin list
```

Start a fresh desktop session. Inspect its available skills and confirm
`marketplace-install`, `marketplace-create-skill`, `marketplace-submit-update`,
`setup-matt-pocock-skills`, `grill-with-docs`, `to-spec`, `to-tickets`,
`diagnosing-bugs`, `tdd` and `code-review`. Inspect the actual plugin versions;
a name in these notes does not prove installation.

After exercise 4's owner-approved merge/publication, refresh the catalogue
and update the changed sharing-support plugin:

```shell
copilot plugin marketplace update copilot-marketplace
copilot plugin update marketplace-maintenance
```

Use its install command above for someone who has not installed it yet.
The source also documents `copilot plugin update matt-pocock-skills` for
changes to the vendored plugin; a participant skill must not modify that
vendored collection. Record the observed higher shared-plugin version,
start a fresh session and invoke the recorded shared skill.

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