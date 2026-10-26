# Quality Criteria: YAML File

## Metadata
| Key | Value |
| --- | --- |
| ID | QC-YML-001 |
| CrossReference | [QC-WF-001], [QC-ADR-001] |

## Version History
| Date | Status | Author | Reviewer | Change | Commit |
| --- | --- | --- | --- | --- | --- |
| 2026-10-11 | Deprecated | Jens Tirsvad Nielsen | S02 | Accepted by S02 on 2026-10-11 (confirmed in chat, relayed by the author), through the pull request that merges this row; the first review is confirmed by S07 and its conditions are closed; no criterion changes | [a686ac1] |
| 2026-10-22 | Accepted | Jens Tirsvad Nielsen | S02 | Renamed the ISO/IEC 25010 tags to the 2023 names: Usability to Interaction Capability, Portability to Flexibility (RC-083); accepted by the author as stand-in for S02 on the user's instruction in chat on 2026-10-26, through the pull request that merges this row; not independent | [404f664] |

---

## Purpose

YAML carries configuration that other tools act on: pipelines, deployments, linters, data. It is easy to write and easy to get wrong silently: a wrong indent changes the meaning, an unquoted `no` becomes a boolean, a duplicate key drops a value. This checklist confirms that a YAML file parses to what its author meant, is formatted the same way as its neighbours, holds no secret, and keeps embedded program text out of strings, so that the consuming tool and the next reader both get the same result.

A file with a defined purpose has a second checklist that applies in addition to this one (for a CI workflow, the workflow checklist, [QC-WF-001]).

## Quality Criteria Checklist

Level: **Mandatory** criteria are the baseline every instance must meet; **Optional** criteria are advanced and may be deferred.

| # | Criterion | Level | ISO/IEC 25010 Characteristic(s) | Notes |
| --- | --- | --- | --- | --- |
| 1 | The file parses with a safe YAML loader and has no duplicate keys in any mapping | Mandatory | Reliability | A duplicate key silently keeps one value; state the loader used |
| 2 | Indentation is 2 spaces everywhere, never tabs; lines end with LF; the file ends with one newline and has no trailing spaces | Mandatory | Maintainability | |
| 3 | Passes `yamllint` (or the project's YAML linter) with its configuration committed next to the code and no unexplained `disable` comments | Mandatory | Maintainability, Reliability | State the tool version |
| 4 | A scalar that YAML would coerce to another type is quoted: `yes`, `no`, `on`, `off`, `null`, `~`, numbers with a leading zero, versions such as `1.10`, and values that contain `: ` or ` #` | Mandatory | Reliability | The `on` and `1.10` cases are the usual ones; quote versions and country codes |
| 5 | Only safe, plain types are used: no language-specific tags (`!!python/object`, `!ruby/object`) and no `!include`-style extension unless the consuming tool documents it | Mandatory | Security, Flexibility | Unsafe tags allow code execution in some loaders |
| 6 | No secret is written in the file: no password, token, key or private connection string; a secret is referenced by name and supplied by the consuming tool | Mandatory | Security | |
| 7 | Embedded program text (shell, Python, SQL, `jq`, and so on) in a value is at most five lines; a longer one is moved to a file of its own, in its own language, and the YAML calls it | Mandatory | Maintainability, Reliability | Only a separate file can be linted, formatted and unit tested. The limit is defined in the `coding-conventions` skill (`references/yaml.md`, language rules, "Embedded program text"); this criterion is its check, and criterion 20 of [QC-WF-001] applies it to a workflow |
| 8 | A block of keys or values repeated in the file or across files is defined once (an anchor, a template, an include or a reusable unit the consumer supports) | Mandatory | Maintainability | Modularity, Reusability. Rule: `coding-conventions` skill, “State each piece of knowledge once” |
| 9 | Anchors, aliases and merge keys (`&`, `*`, `<<`) are used only where the consuming tool is known to support them | Mandatory | Flexibility, Compatibility | A tool that does not expand them reads the literal text |
| 10 | The file validates against the schema of the consuming tool where one exists, and the schema or tool version is stated | Optional | Reliability, Compatibility | |
| 11 | A header comment states what the file is for, which tool reads it, and where its decision or design is recorded | Mandatory | Interaction Capability, Maintainability | Comments say why, not what |
| 12 | Key names follow the convention of the consuming tool; one case style is used within the file (kebab-case or snake_case, never mixed) | Mandatory | Maintainability, Interaction Capability | |
| 13 | Multi-line strings use a block scalar (`\|` or `>`) and state the chomping indicator (`\|-`, `\|+`) where the trailing newline matters | Optional | Reliability | |
| 14 | The file name is lowercase kebab-case with one extension style (`.yml` or `.yaml`) used throughout the repository | Optional | Maintainability | |
| 15 | A change is exercised by a check that runs without the real target: a parse and schema test, or a dry run of the consuming tool | Optional | Reliability | |

## Common Defects

- Tabs, or a mix of 2 and 4 space indents, that make a key land in the wrong parent
- `on:` read as the boolean `true`, a version `3.10` read as `3.1`, a country code `NO` read as `false`
- Two keys with the same name in one mapping, the first silently lost
- A token, password or connection string pasted into the file
- A 20-line shell or Python script inside a `|` block that no linter or test ever sees
- The same block copied into five files, so one fix is applied four times
- An anchor or merge key the consuming tool does not expand
- A file with no comment saying which tool reads it
- A YAML file that no linter has ever run on, or a linter configuration full of unexplained `disable` comments
- A language-specific or extension tag (`!!python/object`, `!include`) in a file that another tool reads
- Keys in `camelCase` and `kebab-case` mixed in one file, against the convention of the tool that reads it
- A file never validated against the schema of the tool that reads it
- A multi-line value whose trailing newline changes the result and no chomping indicator says which
- `.yml` and `.yaml` mixed in one repository, or a file name that is not kebab-case
- A change that is only ever tried on the real target, with no parse, schema or dry-run check before it

## Traceability Rule

- Backward: Architecture Decision Record checklist ([QC-ADR-001]) for the decisions that constrain the file
- Forward: workflow checklist ([QC-WF-001]) when the file is a CI workflow; none otherwise, the file is the end of the QC checklist chain

---

[QC-WF-001]: ./qc-workflow.md
[QC-ADR-001]: ../artifacts/qc-adr.md
[a686ac1]: https://git.tirsystem.com/TirSystem/SQA-QC-Checklists/commit/a686ac140157cf6c607bef8d96959cd4ce8d0468
[404f664]: https://git.tirsystem.com/TirSystem/SQA-QC-Checklists/commit/404f66454eb129463cf0982b425ad16707bd66a9
