# Quality Criteria: Python Source Code

## Metadata
| Key | Value |
| --- | --- |
| ID | QC-PY-001 |
| CrossReference | [QC-DCD-001], [QC-ADR-001] |
| DomainLanguages | IT Professional English |

## Version History
| Date | Status | Author | Reviewer | Change | Commit |
| --- | --- | --- | --- | --- | --- |
| 2026-10-09 | Deprecated | Jens Tirsvad Nielsen | S02 | Added criteria 14 to 16 (DRY, dependency rule and SOLID) | [304ec77] |
| 2026-10-09 | Accepted | Jens Tirsvad Nielsen | S02 | Accepted by the author as stand-in for S02 (Coding Standards Governance), through the pull request that merges this row; the delta re-review of the new criteria is a draft confirmed by the author as stand-in, not independently | [b5e5613] |

---

## Purpose

Python source code is the implementation of the design. This checklist confirms that code follows the Python coding conventions (PEP 8 naming and layout, type hints, error handling), so that it is readable, maintainable and consistent with the design it implements.

## Quality Criteria Checklist

Level: **Mandatory** criteria are the baseline every instance must meet; **Optional** criteria are advanced and may be deferred.

| # | Criterion | Level | ISO/IEC 25010 Characteristic(s) | Notes |
| --- | --- | --- | --- | --- |
| 1 | Packages, modules, functions, variables, classes and constants follow PEP 8 casing (`snake_case`, `PascalCase`, `UPPER_SNAKE`) | Mandatory | Maintainability, Usability | |
| 2 | Names state purpose in the domain's language; no unexplained abbreviations, no single-letter names outside tiny scopes | Mandatory | Maintainability, Usability | |
| 3 | Code is produced by the project's formatter and passes its linter with no unexplained suppressions | Mandatory | Maintainability | |
| 4 | Every function and method signature is type-annotated, including `-> None` | Mandatory | Maintainability, Reliability | |
| 5 | No bare `except:`, no swallowed exceptions; specific exceptions are raised and the cause is kept (`raise ... from`) | Mandatory | Reliability | |
| 6 | No mutable default arguments and no shadowed builtins | Mandatory | Reliability, Maintainability | |
| 7 | Files, locks and connections are managed with context managers | Mandatory | Reliability, Performance Efficiency | |
| 8 | Public modules, classes and functions have docstrings that say what, not how | Optional | Usability, Maintainability | |
| 9 | Logging uses `logging`, not `print`; no secrets or personal data in log output | Mandatory | Security, Maintainability | |
| 10 | Classes and operations trace to the Design Class Diagram they implement; deviations are recorded | Mandatory | Functional Suitability, Maintainability | |
| 11 | Tests exist for new behaviour, are named for the behaviour, and do not depend on order or the network | Mandatory | Reliability, Maintainability | |
| 12 | Type checker runs in strict mode without errors; `Any` is justified in a comment | Optional | Reliability, Maintainability | |
| 13 | Dependencies are declared and pinned in the project's dependency file, none unused | Optional | Portability, Security | |
| 14 | Each piece of knowledge (a business rule, constant, format, validation or query) is defined in one place; code is merged only where it expresses the same knowledge, not where it merely looks alike | Mandatory | Maintainability | Modularity, Reusability. Rule: `coding-conventions` skill, “State each piece of knowledge once” |
| 15 | Imports point inward: business-rule modules import no framework, database, UI or delivery-mechanism code, and there are no import cycles | Mandatory | Maintainability, Portability | Modularity, Portability. Rule: `coding-conventions` skill, “Dependencies point inward” |
| 16 | SOLID holds: a class or module has one reason to change; new behaviour is added by extension, not by editing a type test in several places; subclasses honour the contract of their base; protocols are narrow; high-level code depends on protocols or abstract types and receives its implementations | Mandatory | Maintainability | Single responsibility is the most commonly violated. Rule: `coding-conventions` skill, “SOLID” |

## Common Defects

- Java- or C#-style casing (`getTotal`, `customerList` for functions and variables)
- Missing or partial type annotations
- Bare `except:` or `except Exception: pass`
- Mutable default arguments (`def f(x=[])`)
- `print` used for diagnostics; wildcard imports
- Code reformatted by hand, or an unrelated reformat mixed into a functional change
- Classes or methods that appear in no design artifact and have no stated reason
- The same rule, constant or validation written in two modules, or two functions merged because they look alike although they change for different reasons
- Business-rule modules importing the ORM, the web framework or a database driver
- A class with several unrelated responsibilities, or an `isinstance` chain repeated in several places

## Traceability Rule

- Backward: Design Class Diagram checklist ([QC-DCD-001]) for the classes and operations being implemented; Architecture Decision Record checklist ([QC-ADR-001]) for the decisions that constrain the implementation
- Forward: none — source code is the end of the QC checklist chain

---

[QC-DCD-001]: ../artifacts/qc-dcd.md
[QC-ADR-001]: ../artifacts/qc-adr.md
[304ec77]: https://git.tirsystem.com/TirSystem/SQA-QC-Checklists/commit/304ec7751bd39ff6d54862c2cd10958ef90123ff
[b5e5613]: https://git.tirsystem.com/TirSystem/SQA-QC-Checklists/commit/b5e5613a384527a18cd40594fc24cac4bdd11a31
