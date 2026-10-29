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
create a branch and PR in
`agel-data-and-ai-temp-poc/ai-dev-marketplace`. Do not create a personal
repository or use a fork as an unapproved substitute.

The personal assistant's source clone and `assistant-share` must be available.
The installed `marketplace-maintenance` plugin must supply
`marketplace-create-skill` and `marketplace-submit-update`; these perform
placement, validation, versioning and submission after `assistant-share`
prepares the candidate. Confirm all three skills before the volunteer starts.
The lecturer confirms the target plugin and its current version:
**`TODO_SHARED_PLUGIN`**. Do not treat the existing `ai-dev` or
`marketplace-maintenance` plugin as the target without confirmation.

## 1. Prepare a useful contribution (16:00-16:10, 10 minutes)

Each participant chooses the small skill created in exercise 1. Remove
personal examples, internal identifiers, credentials and machine-specific
paths. Confirm that it has an English trigger, required inputs, steps and
expected output. Try it once on a non-sensitive example.

Decide whether it applies to other people's work. A personal preference is
not automatically a useful shared skill. Everyone prepares locally, but only
the designated volunteer proceeds to publication.

## 2. Preview and create one live PR (16:10-16:25, 15 minutes)

The volunteer asks in their assistant session:

```text
Use assistant-share to prepare this reviewed skill for
agel-data-and-ai-temp-poc/ai-dev-marketplace.
Inspect the target plugin and its contribution instructions. Show me the
files, English description and version/catalog changes before publishing.
After I review the exact change, create one branch and one PR in that
marketplace repository. Do not create a participant repository or merge.
```

The volunteer reviews the proposed files and confirms the live branch/PR
step. Follow the skill's actual instructions; do not manually bypass a
reported permission or validation failure.

`assistant-share` preserves the personal original and prepares its candidate
in `sharing/<name>/`. The marketplace skills own the final shared name.
Choose a name distinct from participants' personal example skills and record
it as **`TODO_SHARED_SKILL`** until confirmed. This prevents a personal copy
from masking the plugin's skill during the update check.

Show the PR URL, diff and validation result. The marketplace owner reviews
the contribution, including the plugin/catalog version change, and decides
whether to merge. The participant and workshop agents do not assume authority
to merge on the owner's behalf.

**Checkpoint:** this is a real PR to the intended shared repository, created
using `assistant-share`, not a screenshot of a prepared draft.

## 3. Update after publication (16:25-16:35, 10 minutes)

Wait for the owner to confirm that the PR is merged and the new plugin
version is published. Record the actual plugin name and version in place of
`TODO_SHARED_PLUGIN`. In a Copilot app session, use:

```text
/plugin marketplace update ai-dev-marketplace
/plugin update TODO_SHARED_PLUGIN
```

Participants who do not already have that plugin use
`/plugin install TODO_SHARED_PLUGIN@ai-dev-marketplace` after the catalogue
update instead. Start a **new session**, inspect `/skills`, and invoke the
shared **`TODO_SHARED_SKILL`** on the same small example.

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
| `assistant-share` or network fails | Preserve the reviewed skill and contribution preview | A manually described PR is not the live `assistant-share` result |
| Owner has not merged by 16:25 | Walk through the real PR and show the update procedure without claiming a new version | Participant plugin update must wait for publication |
| Update succeeds but skill is missing | Start a new session and check the actual installed version/name | Do not report the shared skill available until it can be invoked |
| Rovo/Jira is unavailable | Skip only the optional segment | No mandatory outcome is affected |
