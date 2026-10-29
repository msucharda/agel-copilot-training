# Exercise 2: from a bug to feature tickets

**13:00-14:30 CET, 90 minutes.** Work alone on the local Java room-booking
sample app in the Copilot desktop app.

**Result:** one reproduced and fixed bug with evidence, plus a reviewed
specification and tickets for a larger feature. Stop the larger feature at
tickets; do not implement it in this block.

**App only:** invoke the Matt Pocock skills in the desktop app. CLI 1.0.105
cannot invoke the user-only skills in either interactive TUI or non-interactive
mode, even if they appear enabled. The optional CLI plugin-management
procedure is not a fallback for this exercise.

## Before you start

Use **JDK 21** and the Maven wrapper shipped with the app. The integrated
source uses Spring Boot **4.1.2**. The lecturer must confirm that the AGEL copy
contains the [reviewed baseline](../README.md#sample-app).
**Linux only:** the wrapper also needs `unzip` and either `sha256sum` or
`shasum`; complete the conditional [preparation check](../docs/preparation.md#checks)
before running it. These utilities are not Windows prerequisites.

| Input | File in the app clone |
|---|---|
| Bug | `.scratch/back-to-back-bookings/issues/01-fix-boundary-conflict.md` |
| Larger feature | `.scratch/recurring-bookings/idea.md` |

The AGEL vendored Matt Pocock plugin must be installed from the morning
theory block. Do not also install the upstream `mattpocock-skills@mattpocock` plugin.

Use the desktop app's explicit slash invocation with task text after the name.
**Instructor note:** the maintainer verified that route with a personal skill;
Friday must still verify the plugin-provided skills used here. If a plugin
skill cannot be invoked, use the fallback and mark that checkpoint incomplete.
Do not ask the model to load a user-only skill or switch to another client.

## 1. Establish the baseline (13:00-13:15, 15 minutes)

If you do not already have the sample clone, use the AGEL copy:

```shell
git clone https://github.com/agel-data-and-ai-temp-poc/copilot-workshop-room-booking.git agel-room-booking
cd agel-room-booking
git status --short
```

Add this existing local directory as a repository in the Copilot app and
start a session. Read the app README, including its local accounts and CSRF
procedure. Run the wrapper from the app root:

| Action | Windows PowerShell | Unix shell |
|---|---|---|
| Verify baseline and formatting | `.\mvnw.cmd verify` | `./mvnw verify` |
| Run locally | `.\mvnw.cmd spring-boot:run` | `./mvnw spring-boot:run` |

If Java 21 is not selected, use your actual JDK installation path for
`JAVA_HOME` and put its `bin` first on `PATH`, as the app README describes.
Do not copy another machine's JDK path.

The app binds to `127.0.0.1:8080`. Open
<http://localhost:8080/actuator/health> and
<http://localhost:8080/swagger-ui.html>. All `/api/**` routes require HTTP Basic:

| Local development account | Public local-only password | Role |
|---|---|---|
| `alice` | `alice-local-only` | `EMPLOYEE` |
| `bob` | `bob-local-only` | `EMPLOYEE` |
| `facilities` | `facilities-local-only` | `FACILITY_ADMIN`, `EMPLOYEE` |

These are intentional development examples, not company credentials.
Do not expose the service or enter real company data. Writes need the token
from `GET /api/csrf`, its session cookie and the returned token header;
follow the app README rather than disabling CSRF to make a request work.

Data persists in `.data/room-booking.mv.db`; tests use in-memory H2.
Do not delete the database as a routine reset. Stop the manual server with
`Ctrl+C` before changing/rebuilding it, then restart to observe the new code.
Record baseline results before making changes. An initially green `verify`
does not prove that the intentional boundary bug is absent.
Do not create a GitHub repository, fork, PR or remote branch.

## 2. Set up the coding workflow (13:15-13:25, 10 minutes)

Invoke the setup skill yourself in the sample-app session:

```text
/setup-matt-pocock-skills Set up this repository.
Read its current
instructions and README first. Explain the proposed changes, then configure
the repository to use the AGEL vendored Matt Pocock skills.
Choose LOCAL MARKDOWN as the issue tracker, not GitHub or Jira even though
origin points at GitHub. Configure docs/agents/issue-tracker.md and
docs/agents/domain.md. Specs belong in .scratch/<feature>/spec.md and each
ticket in .scratch/<feature>/issues/<NN>-<slug>.md.
When a skill says "publish to the issue tracker", it means these local files.
Do not install the upstream plugin, create remote issues, publish a
repository or start unrelated work.
```

Inspect the diff and verify the resulting instructions in a new session.
Inspect the session's available skills: `diagnosing-bugs`, `tdd`,
`/grill-with-docs`, `/to-spec`, `/to-tickets` and `code-review`. The local-tracker
template is supported by the installed setup skill; do not use its GitHub
tracker template for this exercise.

**Checkpoint:** identify what changed in the repository and what comes from
the installed plugin. A skill name in a document is not proof that the skill
is installed.

## 3. Reproduce and fix one bug (13:25-14:00, 35 minutes)

Open `.scratch/back-to-back-bookings/issues/01-fix-boundary-conflict.md`.
Its symptom is **HTTP 409 instead of 201** when a booking starts exactly
when another ends. Follow its reproduction, including authentication and CSRF.
Ask:

```text
Read .scratch/back-to-back-bookings/issues/01-fix-boundary-conflict.md.
Use diagnosing-bugs and tdd. Reproduce the exact boundary-conflict symptom
through the public API, then add a failing regression before fixing it.
Preserve real-overlap conflicts, cancelled-booking behavior, ownership and
room locking. Make availability and creation agree. Run the task's targeted
tests and full verify, then show the reproduction and passing evidence.
Stay local; do not create tracker issues, open a PR or push.
```

Read the reproduction before accepting a fix. A test that was already green
does not establish that the bug existed. Review the final diff and save a
local commit using your normal Git workflow.

**Checkpoint:** show the reproduction, the changed behaviour and the relevant
passing check. If the baseline failed for an environment reason, keep that
separate from the bug result.
The red result must expose the expected 201 versus actual 409, not merely
a missing test class, authentication failure or malformed request.

After adding the regression, the task's PowerShell checks are:

```powershell
.\mvnw.cmd '-Dtest=BookingBoundaryIntegrationTest,BookingApiIntegrationTest,AvailabilityApiIntegrationTest' test
.\mvnw.cmd verify
```

On Unix, replace `.\mvnw.cmd` with `./mvnw`. Restart the manual server if
you also check the changed behavior interactively.

## 4. Shape a larger feature, stopping at tickets (14:00-14:25, 25 minutes)

Read `.scratch/recurring-bookings/idea.md`. It is only an idea: weekly
meetings, changes/cancellation and visible conflicts. A specification and
tickets do not exist yet. Each block below is a separate participant invocation.
Do not ask the model to invoke or chain these user-only skills.

**First, invoke clarification and answer its questions:**

```text
/grill-with-docs Clarify .scratch/recurring-bookings/idea.md.
Read our local issue-tracker docs.
Clarify recurrence, timezone/DST, limits, conflicts, edits/cancellation and
ownership without inventing decisions. Keep work local; do not implement.
```

**After clarification, invoke specification:**

```text
/to-spec Write .scratch/recurring-bookings/spec.md.
Read our agreed recurring-bookings decisions and local issue-tracker docs.
Use bounded, observable acceptance criteria.
"Publish" means this local Markdown file, not a remote issue.
Stop after the specification; do not implement.
```

**Review the specification before invoking ticket creation:**

```text
/to-tickets Split the approved .scratch/recurring-bookings/spec.md.
Read our local tracker docs.
Write one file per ticket in
.scratch/recurring-bookings/issues/<NN>-<slug>.md with explicit dependencies
and completion checks. Use only local Markdown. Do not create remote tracker
issues, implement the feature, start sessions or push.
```

Review at least one ambiguous case and one dependency. If the agent proposes
more work than you can review in five minutes, reduce the scope.
Inspect both the local spec and separate ticket files; a combined prose list
alone is not the documented `/to-tickets` output. Do not create GitHub or Jira
tickets for this exercise.

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
| Marketplace/plugin is unavailable | Inspect the available skill sources and draft a spec using ordinary prompts | Installation and `/setup-matt-pocock-skills` verification remain pending |
| Desktop app does not recognize a slash command | Draft the local spec/tickets with ordinary prompts and inspect the skill contract with the lecturer | User-only skill invocation is unverified; do not claim that skill ran |
| AGEL copy lacks the pinned tasks | Report the publication mismatch and inspect the supplied brief with the lecturer | Do not clone a development copy or invent a replacement bug |

No mandatory step uses Jira or the Atlassian Rovo Connector.
