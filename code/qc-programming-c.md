# Quality Criteria: C Source Code

## Metadata
| Key | Value |
| --- | --- |
| ID | QC-CL-001 |
| CrossReference | [QC-DCD-001], [QC-ADR-001] |
| DomainLanguages | IT Professional English |

## Version History
| Date | Status | Author | Reviewer | Change | Commit |
| --- | --- | --- | --- | --- | --- |
| 2026-10-09 | Accepted | Jens Tirsvad Nielsen | S02 | Accepted by the author as stand-in for S02 (Coding Standards Governance), through the pull request that merges this row; the delta re-review of the new criteria is a draft confirmed by the author as stand-in, not independently | [b5e5613] |
| 2026-10-14 | Proposed | Jens Tirsvad Nielsen | S02 | Added criteria 16 and 17 (layer folders; file and folder names) | pending |

---

## Purpose

C gives no safety net: memory, bounds and error handling are the programmer's job. This checklist confirms that C code follows the C coding conventions (naming with module prefixes, explicit ownership, checked errors), so that it is maintainable and free of the defects that cause crashes and vulnerabilities.

## Quality Criteria Checklist

Level: **Mandatory** criteria are the baseline every instance must meet; **Optional** criteria are advanced and may be deferred.

| # | Criterion | Level | ISO/IEC 25010 Characteristic(s) | Notes |
| --- | --- | --- | --- | --- |
| 1 | Functions and variables are `snake_case`; public symbols carry the module prefix; macros and enum constants are `UPPER_SNAKE` | Mandatory | Maintainability, Compatibility | |
| 2 | No reserved identifiers (leading underscore plus uppercase, double underscore) | Mandatory | Portability, Reliability | |
| 3 | Code compiles cleanly with the project's warning flags and the declared C standard | Mandatory | Reliability, Portability | |
| 4 | Code is produced by the project's formatter; braces are used on every control-flow body | Mandatory | Maintainability | |
| 5 | Every return value that can fail, including allocation, is checked | Mandatory | Reliability | |
| 6 | Every acquired resource (memory, file, lock) has one owner and is released on every exit path | Mandatory | Reliability, Performance Efficiency | |
| 7 | Every buffer is passed with its length; bounded functions (`snprintf`) are used, never `gets`, `sprintf` or `strcpy` | Mandatory | Security, Reliability | |
| 8 | No undefined behaviour: no signed overflow, use after free, out-of-bounds access or uninitialised reads | Mandatory | Reliability, Security | |
| 9 | Headers are self-contained, guarded, and expose only what callers need; internals are `static` | Mandatory | Maintainability, Compatibility | |
| 10 | Mutable global state is avoided, or is `static` and documented | Optional | Maintainability, Reliability | |
| 11 | Error reporting (status codes, `errno` use) is documented in the header | Optional | Usability, Reliability | |
| 12 | Tests cover new behaviour and run under address and undefined-behaviour sanitizers in at least one build | Optional | Reliability, Security | |
| 13 | Modules and functions trace to the Design Class Diagram or design artifact they implement | Mandatory | Functional Suitability, Maintainability | |
| 14 | Each piece of knowledge (a business rule, constant, format, validation or query) is defined in one place; code is merged only where it expresses the same knowledge, not where it merely looks alike | Mandatory | Maintainability | Modularity, Reusability. Rule: `coding-conventions` skill, “State each piece of knowledge once” |
| 15 | Includes point inward: business-rule modules include no I/O, platform or UI headers, the include graph has no cycles, and a module has one responsibility (rules are not mixed with I/O) | Mandatory | Maintainability, Portability | Modularity, Portability. Rule: `coding-conventions` skill, “Dependencies point inward” |
| 16 | Source is laid out in the layers and folders of the clean architecture folder structure (`domain/`, `application/`, `infrastructure/` and `presentation/` directories under `src/`, and `unit`, `integration` and `e2e` under `tests/`), in `snake_case`, and includes between the layers point inward | Mandatory | Maintainability, Portability | Structure: see the `clean-architecture` skill, "Folder structure". A merged layer is accepted when an ADR says why; `Domain` is never merged |
| 17 | File and folder names are English, contain no space and no character outside letters, digits, `-`, `_` and `.`, and follow the casing of the language for files | Mandatory | Usability, Maintainability, Portability | Names: rule 16 of `coding-conventions`; well-known names (`README.md`, `LICENSE`) and wiki page names are exceptions |

## Common Defects

- Unchecked `malloc` or `fopen` results
- Missing `free` or `close` on an early-return or error path
- Buffer sized without a length parameter; `strcpy` or `sprintf` on external input
- Public function or type without the module prefix, colliding across modules
- Macros doing the work of `static inline` functions or `enum`
- Identifiers starting with an underscore and an uppercase letter
- Undefined behaviour hidden by a build that happens to work
- The same rule, constant or table written in two modules
- A business-rule module that includes a platform, I/O or UI header, or modules that include each other
- A module that mixes business rules with file or device access
- Source files in one flat folder, or a layer that exists only by a naming habit and not as a project or directory
- File or folder names with a space, in a language other than English, or in another language's casing

## Traceability Rule

- Backward: Design Class Diagram checklist ([QC-DCD-001]) for the modules and operations being implemented; Architecture Decision Record checklist ([QC-ADR-001]) for the decisions that constrain the implementation
- Forward: none — source code is the end of the QC checklist chain

---

[QC-DCD-001]: ../artifacts/qc-dcd.md
[QC-ADR-001]: ../artifacts/qc-adr.md
[b5e5613]: https://git.tirsystem.com/TirSystem/SQA-QC-Checklists/commit/b5e5613a384527a18cd40594fc24cac4bdd11a31
