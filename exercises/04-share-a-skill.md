# Exercise 4: share a skill through the marketplace

**16:00-16:40 CET, 40 minutes.** Everyone prepares a shareable skill.
**One designated participant** creates the live PR; the others update the
published plugin afterwards. This is the only participant GitHub PR in the
workshop.

**Result:** one real marketplace PR created with `assistant-share`, followed
by an observed plugin update after the marketplace owner reviews and merges
the change. An unmerged PR alone is not an available plugin update.

## Before the live step

The lecturer names the volunteer and confirms that their AGEL account may
create a branch and PR in the **confirmed workshop marketplace**. Its address
and plugin names are defined only in the
[marketplace values](../README.md#marketplace-values). The whole exercise,
including this PR, uses that new marketplace. Access is still a live
prerequisite; do not create a personal repository or use a fork or previous
marketplace as a substitute.

The personal assistant's source clone and `assistant-share` must be available.
The installed sharing-support plugin must supply
`marketplace-create-skill` and `marketplace-submit-update`; these perform
placement, validation, versioning and submission after `assistant-share`
prepares the candidate. Confirm all three skills before the volunteer starts.
Participant-authored skills go into the **sharing-support plugin** named in
that same README, not into the vendored Matt Pocock collection. The final
shared skill and higher published version are recorded there when known.
The template's `assistant-share` instructions must point at this confirmed
destination too; stop if they still name an old repository.

Only the volunteer needs **Node.js 22+, npm and Git** for contribution checks.
`npm ci` installs a locked npm dependency, so confirm an approved registry
route or cache as well as branch/PR permission. Do not install tools or assume
network approval on another participant's behalf.

## 1. Prepare a useful contribution (16:00-16:10, 10 minutes)

Each participant chooses the small skill created in exercise 1. Remove
personal examples, internal identifiers, credentials and machine-specific
paths. Confirm that it has an English trigger, required inputs, steps and
expected output. Try it once on a non-sensitive example.

Decide whether it applies to other people's work. A personal preference is
not automatically a useful shared skill. Everyone prepares locally, but only
the designated volunteer proceeds to publication.

## 2. Preview and create one live PR (16:10-16:25, 15 minutes)

The volunteer copies the **Marketplace repository** value from the workshop
README into `<confirmed-destination>` below. Confirm two distinct absolute paths:
`<assistant-root>` for the personal assistant clone and `<marketplace-root>`
for the marketplace checkout. Clone the confirmed marketplace into its own
local folder if necessary; this does not create a GitHub repository.
Replace both path placeholders before sending the prompt in the assistant
session. Do not send it while the destination is still `TODO`.
The assistant repository's own README is not the workshop settings source.

```text
Use assistant-share to prepare this reviewed skill for <confirmed-destination>.
Assistant clone: <assistant-root>
Marketplace clone: <marketplace-root>
This is the destination confirmed in the workshop README.
Compare it with the template's sharing instructions and stop if they differ.
Confirm the exact destination with me before acting.
Before any marketplace edit, verify its checkout and record its base with:
git -C "<marketplace-root>" rev-parse --show-toplevel
git -C "<marketplace-root>" rev-parse HEAD
Use that marketplace base, never the assistant clone's HEAD.
Retain the absolute candidate path, both roots, confirmed destination, recorded
base, approved shared name, behavior, version changes and stop point across
confirmation turns.
Inspect the target plugin and its contribution instructions. Show me the
files, English description and version/catalog changes before publishing.
Invoke marketplace-create-skill with this handoff, targeting the prescribed
participant-contribution plugin, not the vendored collection. Invoke
marketplace-submit-update with the same root and recorded base; if the
creation skill already invoked submission, continue it instead of submitting
twice. Reading a skill file or implementing it inline is not invocation.
Set the marketplace checkout as the working directory in every shell call
that runs npm or the validator. Await each command and stop on a failed check.
Run its npm tests and validators, comparing versions against the recorded base.
After I review the exact change, create one branch and one PR in that
marketplace repository. Do not create a participant repository or merge.
```

The volunteer reviews the proposed files and confirms the live branch/PR
step. Follow the skill's actual instructions; do not manually bypass a
reported permission or validation failure. The first Git command must return
the confirmed marketplace root; the second supplies its base commit before
any marketplace edit. Keep the candidate in the assistant clone, not the
marketplace checkout.

`assistant-share` preserves the personal original and prepares its candidate
in `sharing/<name>/`. The marketplace skills place the approved candidate at
`plugins/<sharing-support-plugin>/skills/<shared-skill>/SKILL.md`.
Those fields refer to the central README setting and approved skill name.
Use English kebab-case and matching directory/YAML `name`, with a `description`;
do not use reserved `assistant-*` maintenance names or alter vendored files.
Choose a name distinct from participants' personal example skills and record
it in the README's Shared skill setting when confirmed. This prevents a personal copy
from masking the plugin's skill during the update check.

The create/submit skills own the marketplace clone and checks, not the
personal assistant clone. Use `git -C "<marketplace-root>"` for marketplace
Git commands. For **every separate shell call**, set its working directory
to that verified root before running one of the commands below. In Windows
PowerShell, start each call with
`Set-Location -LiteralPath "<marketplace-root>" -ErrorAction Stop`;
in a Unix shell, use `cd "<marketplace-root>" &&`.
A previous call's directory change does not carry into the next call.
Record the base **before edits**, then follow the documented commands:

```shell
npm ci
npm test
npm run validate
node scripts/validate.mjs --base <recorded-base-commit-sha>
```

Await each command to completion before starting the next. If it fails,
report its command, working directory and error before correcting the cause;
do not skip the check or invent package files after an install failure.
Replace the last field with the recorded marketplace SHA; do not compare a
change with itself. Validation is offline only **after** dependency installation.
Use the documented SemVer rule: fixes patch, new capabilities minor,
incompatible changes major. Update the changed plugin's
`.github/plugin/plugin.json` and its matching catalogue entry together.
Derive the new version from the actual contribution base, not an assumed
workshop version.

Show the single PR against marketplace `main`, its diff, validation and
green contribution CI. Follow its PR template. The marketplace owner reviews
and decides whether to merge; the participant and workshop agents stop at
the reviewable PR and do not assume that authority.

**Checkpoint:** this is a real PR to the intended shared repository, created
using `assistant-share`, not a screenshot of a prepared draft.

## 3. Update after publication (16:25-16:35, 10 minutes)

Wait for the owner to confirm that the PR is merged and the new plugin
version is published. Record its actual version in the README's Shared
plugin version setting. Follow the
[marketplace installation and update procedure](../README.md#marketplace-installation-and-updates),
using that single source for the catalogue and plugin names. Use the
**desktop app UI** to refresh the catalogue and update the plugin; exact UI
labels remain part of Friday's trial. CLI commands are a fallback only for
someone with a separately installed Copilot CLI, not an assumed app PATH tool.
Participants without the plugin use the app UI's installation action.
Start a **new session**, inspect its available skills, and invoke the recorded
shared skill on the same small example.

**Checkpoint:** someone other than the author can load and use the published
version. An old session or a local copy of the author's skill is not evidence
that the marketplace update worked.

## 4. Optional Jira via Atlassian Rovo (16:35-16:40, 5 minutes)

Only if time, account access and the Connector are available: use the
**Atlassian Rovo Connector** to read an existing permitted Jira item and
identify its intent and acceptance criteria. Do not create or change Jira
items as part of this optional demonstration.

If the Connector is absent, skip this segment. Refer to the local feature
brief from exercise 2 to discuss the same intent-to-spec transition.
The mandatory sharing exercise does not depend on Jira.

## If something is unavailable

| Problem | Continue with | What is not complete |
|---|---|---|
| Volunteer lacks marketplace branch/PR permission | Keep the local share preview; show the intended contribution to the owner | The live PR criterion is pending; do not switch to a personal repository |
| Volunteer lacks Node/npm or dependency access | Keep the local candidate and arrange the missing prerequisite | Do not skip contribution checks or claim a validated PR |
| `assistant-share` or network fails | Preserve the reviewed skill and contribution preview | A manually described PR is not the live `assistant-share` result |
| Owner has not merged by 16:25 | Walk through the real PR and show the update procedure without claiming a new version | Participant plugin update must wait for publication |
| Update succeeds but skill is missing | Start a new session and check the actual installed version/name | Do not report the shared skill available until it can be invoked |
| Rovo/Jira is unavailable | Skip only the optional segment | No mandatory outcome is affected |
