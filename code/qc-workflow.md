# Quality Criteria: CI Workflow (Gitea Actions / GitHub Actions)

## Metadata
| Key | Value |
| --- | --- |
| ID | QC-WF-001 |
| CrossReference | [QC-YML-001], [QC-SH-001], [QC-PY-001], [QC-ADR-001] |

## Version History
| Date | Status | Author | Reviewer | Change | Commit |
| --- | --- | --- | --- | --- | --- |
| 2026-10-11 | Proposed | Jens Tirsvad Nielsen | — | Initial version: criteria for a workflow file under `.gitea/workflows/` or `.github/workflows/` | [4af4688] |

---

## Purpose

A workflow runs unattended, with a token and often with write access, on events anyone with push or pull-request rights can cause. A defect therefore costs more than in an ordinary script: a leaked secret, an unpinned action that changes under you, a release published by accident, a run that hangs a runner. This checklist confirms that a workflow is valid, runs with the least privilege, is reproducible, keeps its logic in files that can be tested, and works on the host that runs it (Gitea Actions) without breaking on the host it may move to (GitHub Actions).

Apply it together with the YAML checklist ([QC-YML-001]); a script the workflow calls is reviewed with its own language checklist ([QC-SH-001], [QC-PY-001]).

## Quality Criteria Checklist

Level: **Mandatory** criteria are the baseline every instance must meet; **Optional** criteria are advanced and may be deferred.

### Structure

| # | Criterion | Level | ISO/IEC 25010 Characteristic(s) | Notes |
| --- | --- | --- | --- | --- |
| 1 | The file meets the YAML checklist ([QC-YML-001]) | Mandatory | Maintainability, Reliability | |
| 2 | The file is in `.gitea/workflows/` or `.github/workflows/` with the extension `.yml` or `.yaml`, and the same workflow does not exist in both directories | Mandatory | Reliability, Compatibility | A host may read only one of the two directories; a copy drifts |
| 3 | The file declares `name`, `on` and `jobs`; `on` lists explicit events and, where it matters, `branches` or `paths` | Mandatory | Functional Suitability | |
| 4 | A header comment states the purpose, the triggers, the inputs, the secrets it needs, what it changes outside the repository, and the decision or milestone it implements | Mandatory | Usability, Maintainability | |
| 5 | Every job and step has a descriptive `name`, unique within its job | Mandatory | Usability, Maintainability | The default name is the first line of the command |
| 6 | The file passes `actionlint` (or the project's workflow validation test) and the tool version is stated | Mandatory | Reliability, Maintainability | A host-only context such as `gitea.*` may need the linter's configuration |

### Security

| # | Criterion | Level | ISO/IEC 25010 Characteristic(s) | Notes |
| --- | --- | --- | --- | --- |
| 7 | Every job declares `permissions` explicitly with the least access that works (`contents: read` or none by default); write access only on the job that needs it | Mandatory | Security | A workflow-level default of none, raised per job, is acceptable |
| 8 | Every action used is pinned to a full commit SHA or an exact release tag, never to a branch; a moving major tag (`@v1`) is accepted only for an action published by the same organisation under a stated release policy | Mandatory | Security, Reliability | A floating reference changes the code that runs with your token |
| 9 | No secret is written in the file; a secret is read as `secrets.NAME`, passed to a step through `env:`, never placed on a command line or echoed | Mandatory | Security | A secret name must also be one the host accepts (for example, not starting with `GITEA_` or `GITHUB_`) |
| 10 | Untrusted text (`inputs.*`, event fields such as a title, branch name or label, step outputs derived from them) is never interpolated into a `run:` script; it is passed through `env:` and used as a quoted variable | Mandatory | Security | `${{ ... }}` inside `run:` is text substitution before the shell runs |
| 11 | A trigger that gives a run secrets or a write token on code from a fork or an untrusted branch (`pull_request_target`, `workflow_run`) does not check out or execute that code | Mandatory | Security | |
| 12 | A workflow that changes state outside the repository (release, tag, publish, sync, deploy) is started by hand or by a protected branch, and a manual run defaults to a dry run with an explicit input to apply | Mandatory | Reliability, Security | Same rule as a script that changes state, [QC-SH-001] |
| 13 | The token the workflow uses has only the scope the job needs, and where the host's built-in token is enough it is used instead of a personal token | Optional | Security | |

### Reliability and performance

| # | Criterion | Level | ISO/IEC 25010 Characteristic(s) | Notes |
| --- | --- | --- | --- | --- |
| 14 | Every job sets `runs-on` to an explicit label and `timeout-minutes` | Mandatory | Reliability, Performance Efficiency | A hung step must not hold a runner for the host's default limit |
| 15 | `concurrency` is set where two runs would conflict: a check cancels the older run (`cancel-in-progress: true`); a publishing job queues (`cancel-in-progress: false`) | Mandatory | Reliability, Performance Efficiency | |
| 16 | Triggers are filtered (`branches`, `paths`, `types`) so the workflow runs only for the changes it concerns | Mandatory | Performance Efficiency | |
| 17 | Tools and dependencies are installed at pinned versions; a version is a workflow input with a default or a value in one place | Mandatory | Reliability, Maintainability | |
| 18 | A dependency cache is used where the install is slow enough to matter | Optional | Performance Efficiency | |
| 19 | A failing step names the tool, the file and the reason in its log (annotation or `::error::` line) | Optional | Usability, Reliability | |

### Maintainability and portability

| # | Criterion | Level | ISO/IEC 25010 Characteristic(s) | Notes |
| --- | --- | --- | --- | --- |
| 20 | A `run:` block is at most five lines; a longer script is a file (`tools/`, or a shared repository fetched at a pinned ref) that the step calls with one command, and the workflow passes its settings through `env:` | Mandatory | Maintainability, Reliability | A script file can be linted, formatted and tested; one inside YAML cannot. The script meets its language checklist |
| 21 | Logic used by more than one workflow or repository is a reusable workflow (`workflow_call`) or a composite action; each input has a `description`, a `type` and a `default` where one is sensible | Mandatory | Maintainability | Modularity, Reusability. Rule: `coding-conventions` skill, “State each piece of knowledge once” |
| 22 | Every workflow feature used is verified on the instance that runs it, and the host and version are recorded; a feature the target hosts differ on is noted in the header | Mandatory | Portability, Compatibility | State the Gitea version; `gitea.*` and `github.*` contexts are both read, so the workflow stays portable if only one is used consistently |
| 23 | A reusable workflow states, in its header, how a caller pins it and the script it fetches, so the workflow and its script are the same release | Optional | Reliability, Maintainability | |
| 24 | A static test of the repository's workflows exists and runs on every pull request: valid YAML, required keys, explicit permissions and runner, no inline script above the limit | Optional | Reliability | |

## Common Defects

- Missing `permissions`, so a job runs with the host's broad default token
- An action referenced as `@main`, or a third-party action on a moving tag
- `${{ github.event.pull_request.title }}` or an input written straight into a `run:` script
- A secret echoed, put on a command line, or written in the file
- `pull_request_target` that checks out and runs the pull request's code
- A release or publish workflow that applies on its first run with no dry-run input
- A 30-line shell or Python script inside `run: |` that no linter or test ever sees
- No `timeout-minutes`, so a hung step holds a runner
- No `concurrency` on a publishing job, so two merges race
- The same workflow copied into several repositories instead of called as a reusable workflow
- A feature that works on one host but was never tried on the instance that runs it
- Steps named `Run a command` or left unnamed

## Traceability Rule

- Backward: YAML file checklist ([QC-YML-001]); Architecture Decision Record checklist ([QC-ADR-001]) for the decisions that constrain the workflow
- Forward: the script checklists ([QC-SH-001], [QC-PY-001]) for each script the workflow calls; the workflow is otherwise the end of the QC checklist chain

---

[QC-YML-001]: ./qc-yaml.md
[QC-SH-001]: ./qc-programming-shell.md
[QC-PY-001]: ./qc-programming-python.md
[QC-ADR-001]: ../artifacts/qc-adr.md
[4af4688]: https://git.tirsystem.com/TirSystem/SQA-QC-Checklists/commit/4af4688c52dc2aef15cd69de91952b66d283dfca
