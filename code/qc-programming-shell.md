# Quality Criteria: Shell Script (bash)

## Metadata
| Key | Value |
| --- | --- |
| ID | QC-SH-001 |
| CrossReference | [QC-DCD-001], [QC-ADR-001], [QC-WF-001] |

## Version History
| Date | Status | Author | Reviewer | Change | Commit |
| --- | --- | --- | --- | --- | --- |
| 2026-10-11 | Proposed | Jens Tirsvad Nielsen | S07 | Cited QC-WF-001 as a backward checklist (RC-078) | [140bc3c] |
| 2026-10-22 | Proposed | Jens Tirsvad Nielsen | S07 | Renamed the ISO/IEC 25010 tags to the 2023 names: Usability to Interaction Capability, Portability to Flexibility (RC-083) | [404f664] |

---

## Purpose

Shell scripts automate steps that change files, repositories and remote systems, so a defect often does damage quietly. This checklist confirms that a bash script follows the shell conventions (strict mode, quoting, error handling, safe defaults), so that it is predictable, maintainable and safe to run.

## Quality Criteria Checklist

Level: **Mandatory** criteria are the baseline every instance must meet; **Optional** criteria are advanced and may be deferred.

| # | Criterion | Level | ISO/IEC 25010 Characteristic(s) | Notes |
| --- | --- | --- | --- | --- |
| 1 | Starts with `#!/usr/bin/env bash` and `set -euo pipefail` (or a comment explains the exception) | Mandatory | Reliability | |
| 2 | Every expansion is quoted; lists are arrays; tests use `[[ ]]` and `$(...)` | Mandatory | Reliability, Security | Unquoted expansions break on spaces and globs |
| 3 | Names follow the conventions: `kebab-case.sh` files, `snake_case` functions and variables, `UPPER_SNAKE` constants and environment variables | Mandatory | Maintainability, Interaction Capability | |
| 4 | Passes `shellcheck` and `bash -n` with no unexplained `disable` comments | Mandatory | Maintainability, Reliability | State the tool versions used |
| 5 | Errors go to standard error with an `error:` message and a non-zero exit code; bad or missing arguments print a usage line | Mandatory | Reliability, Interaction Capability | |
| 6 | Temporary files use `mktemp` with a `trap ... EXIT` cleanup; no fixed `/tmp` names | Mandatory | Security, Reliability | |
| 7 | No secret is written in the script, echoed, or put on a command line; secrets come from the environment or a gitignored file | Mandatory | Security | |
| 8 | A script that changes state outside its own directory defaults to a dry run or needs an explicit flag, and says so in its header | Mandatory | Reliability, Security | |
| 9 | A header comment states purpose, usage, options, environment variables and exit codes | Mandatory | Interaction Capability, Maintainability | |
| 10 | The script implements a task or design it cites; deviations are recorded | Mandatory | Functional Suitability, Maintainability | |
| 11 | Behaviour is tested for success, failure and any disabled or bypass path | Mandatory | Reliability | Tests may be a recorded manual run |
| 12 | Formatted with `shfmt` (or the project's formatter) | Optional | Maintainability | |
| 13 | Safe to re-run: a second run does not duplicate or corrupt what the first did | Optional | Reliability | |
| 14 | Bash version and external tools it needs are stated; GNU-only options are named | Optional | Flexibility | |
| 15 | A command sequence, constant, path or message used more than once is defined once (a function, a variable or a sourced helper); a helper is shared between scripts only where it expresses the same knowledge | Mandatory | Maintainability | Modularity, Reusability. Rule: `coding-conventions` skill, “State each piece of knowledge once” |

## Common Defects

- Unquoted `$var` that breaks on a space or an empty value
- Missing `set -euo pipefail`, or `|| true` hiding a real failure
- Parsing `ls` output instead of using globs or `find -print0`
- A script that deletes or overwrites by default with no dry run
- A token echoed to the terminal or kept in the script
- No usage message, so a wrong call fails with a cryptic error
- A script that implements nothing in any task or design
- The same path, option list or message pasted into several places in one script, or copied between scripts

## Traceability Rule

- Backward: Design Class Diagram checklist ([QC-DCD-001]) where the script implements a design; Architecture Decision Record checklist ([QC-ADR-001]) for the decisions that constrain it; CI workflow checklist ([QC-WF-001]) where a workflow calls the script
- Forward: none, source code is the end of the QC checklist chain

---

[QC-DCD-001]: ../artifacts/qc-dcd.md
[QC-ADR-001]: ../artifacts/qc-adr.md
[QC-WF-001]: ./qc-workflow.md
[140bc3c]: https://git.tirsystem.com/TirSystem/SQA-QC-Checklists/commit/140bc3c12df74238e332ff149243ef3e6255e208
[404f664]: https://git.tirsystem.com/TirSystem/SQA-QC-Checklists/commit/404f66454eb129463cf0982b425ad16707bd66a9
