# Prepare for the AGEL Copilot workshop

**Draft: await the maintainer's final message after Friday's test.**
The workshop is Monday 2 November 2026, 09:00-17:00 CET, at
Svätoplukova 2A, Bratislava, and remotely through Teams.

Complete the checks below before Monday. Use your **AGEL GitHub account**.
You do not need to create a repository on GitHub. All coding exercises use
individual local clones in the GitHub Copilot desktop app.

## Who provides what

| Owner | Provides |
|---|---|
| You | Installed Copilot desktop app, AGEL GitHub sign-in, Git, JDK 21, a successful test clone of the assistant template |
| Microsoft | Copilot licences through enterprise team `github-agl-aiworkshop-copilot-users`, materials and lecturers |
| AGEL | Permission to install JDK 21, network access to `github.com` and Maven Central, optional Jira access |

If installation requires administrator permission, ask AGEL IT before Monday.
Do not wait until the workshop to request access or a licence.

## Checks

| Prerequisite | One check | Passing result |
|---|---|---|
| Copilot desktop app | Open the GitHub Copilot desktop app | The app opens; a browser chat or editor extension is not the workshop client |
| AGEL account | Open the app's account/profile view | The signed-in identity is your AGEL GitHub account |
| Copilot entitlement | Send `Reply with READY.` in a new app chat | Copilot responds; there is no licence or sign-in error |
| Git | Run `git --version` in a terminal | A Git version is printed |
| App-bundled GitHub CLI | In an app chat, ask `Run gh --version in this session's shell and show its first output line.` | Actual output reports `gh` version **2.102.1 or higher** |
| JDK 21, not only a JRE | Run `java -version; javac -version` in PowerShell | Both commands report major version `21` |
| Linux only: wrapper utilities | Run `command -v unzip && (command -v sha256sum || command -v shasum)` in a Linux shell | Paths are printed for `unzip` and at least one supported checksum tool |
| Template access and GitHub connectivity | Run the test clone below | Clone completes without an authentication or network error |
| Maven Central connectivity | Open <https://repo.maven.apache.org/maven2/> on the workshop network | The Maven repository index is reachable, not blocked by a proxy page |
| Marketplace contribution permission | Ask the maintainer to confirm that your AGEL account can create a branch and PR in the [workshop marketplace](../README.md#marketplace-values) | The marketplace owner confirms the required permission; only one volunteer uses it live |
| Hybrid participation | Open the workshop invitation in your calendar and check its Teams joining instructions and your audio | You can join and hear the presenter; use the calendar invitation, not a meeting link in this repository |

The JDK check above uses PowerShell command separators. On another shell,
run `java -version` and `javac -version` as separate commands. Report a
different major version instead of assuming that it is sufficient.
The tested Windows desktop app puts its bundled Git and `gh` on the agent
shell's PATH. Check `gh` inside the app, not an unrelated terminal.
Do not install `gh` separately; report a missing/older bundled version to
the lecturer. Linux participants must also pass the conditional utilities
check above; Windows participants do not need those Linux tools.

The Maven Central browser check verifies reachability, not a successful app
build; the sample app build is checked in exercise 2. That app uses Java 21
and its bundled Maven wrapper; do not install Maven or a database server
separately. The [sample-app instructions](../exercises/02-sample-app.md)
contain the actual AGEL clone and Windows/Unix wrapper commands.
Python is not required.

### Test clone

The URL below is the workshop target documented by the assistant template.
The maintainer must confirm publication and AGEL account access after Friday's
test before sending this page.

Choose a writable local parent directory in a terminal, then run:

```shell
git clone https://github.com/agel-data-and-ai-temp-poc/copilot-assistant-template.git agel-assistant
cd agel-assistant
git status --short
```

Success means the clone exists and `git status --short` prints no changes.
Keep this clone: exercise 1 uses it. If that directory already exists, inspect
it and use the existing workshop clone rather than overwriting your work.
Do not fork the template or create a remote participant repository.

## Skills and marketplace

We install the AGEL marketplace and the vendored Matt Pocock plugin together
at 10:00 using the **desktop app's marketplace/plugin UI**. Its exact labels
and navigation await Friday's trial. No standalone Copilot CLI installation
is required; the SDK runtime bundled in the app is not a `copilot` command
on the tested agent shell's PATH.
Do not install the upstream `mattpocock-skills@mattpocock` plugin in addition:
it would duplicate skill names. You do not need to learn skills or Copilot
Projects in advance.

For exercise 4, participants need permission to create a branch and PR in
the workshop marketplace. Its address and plugin names live only in the
[marketplace values](../README.md#marketplace-values). The destination is
confirmed; participant access remains to be verified. One volunteer performs
the single live PR there.

Only the designated contribution volunteer needs **Node.js 22+ and npm**
for the marketplace's validation commands. The maintainer confirms that
participant and their tools before the live exercise. This is not an
additional installation requirement for everyone. If you volunteer, check
`node --version; npm --version` in PowerShell and report missing tools;
do not assume permission to install software. The marketplace's `npm ci`
also needs its npm dependency download or an approved cache; confirm that
route with the maintainer/AGEL IT. GitHub and Maven reachability alone do not
establish it. Other participants only install/update the published plugin.

## Optional Jira

Jira uses the **Atlassian Rovo Connector**. If your organisation makes that
Connector and Jira access available, you may use them in the optional final
segment. They are not prerequisites for exercises 1-4. No mandatory task
requires Jira sign-in or a working Connector.

## If a check fails

Send the failed check, the error text and whether you used the AGEL network
to **Martin Sucharda** at
[martin.sucharda@microsoft.com](mailto:martin.sucharda@microsoft.com)
before Monday. Never include a password, token
or authentication code. For a licence error, mention the AGEL account and
team `github-agl-aiworkshop-copilot-users` through the agreed support route.
For blocked GitHub or Maven access or JDK installation, AGEL IT owns the fix.

Bring the laptop on which you completed these checks. Keep your local clone
and your normal Git tooling available. The exercises do not need a GitHub
participant repository or prior Jira integration.
