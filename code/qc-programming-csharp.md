# Quality Criteria: C# Source Code

## Metadata
| Key | Value |
| --- | --- |
| ID | QC-CS-001 |
| CrossReference | [QC-DCD-001], [QC-ADR-001] |
| DomainLanguages | IT Professional English |

## Version History
| Date | Status | Author | Reviewer | Change | Commit |
| --- | --- | --- | --- | --- | --- |
| 2026-10-09 | Accepted | Jens Tirsvad Nielsen | S02 | Accepted by the author as stand-in for S02 (Coding Standards Governance), through the pull request that merges this row; the delta re-review of the new criteria is a draft confirmed by the author as stand-in, not independently | [b5e5613] |
| 2026-10-14 | Proposed | Jens Tirsvad Nielsen | S02 | Added criteria 17 and 18 (layer folders; file and folder names) | pending |

---

## Purpose

C# code carries the design into a managed runtime where naming, nullability, disposal and async usage decide whether it stays maintainable and correct. This checklist confirms that C# code follows the C# coding conventions (Microsoft naming and design guidelines), so that it is consistent with .NET practice and with the design it implements.

## Quality Criteria Checklist

Level: **Mandatory** criteria are the baseline every instance must meet; **Optional** criteria are advanced and may be deferred.

| # | Criterion | Level | ISO/IEC 25010 Characteristic(s) | Notes |
| --- | --- | --- | --- | --- |
| 1 | Types, methods, properties and constants are `PascalCase`; parameters and locals `camelCase`; private fields `_camelCase`; interfaces start with `I` | Mandatory | Maintainability, Usability | |
| 2 | Async methods end in `Async`; exceptions end in `Exception`; one top-level type per file, named after the file | Mandatory | Maintainability, Usability | |
| 3 | Code is formatted per the project's `.editorconfig` and builds with no unexplained analyzer suppressions | Mandatory | Maintainability | |
| 4 | Nullable reference types are enabled; the null-forgiving operator (`!`) is justified in a comment | Mandatory | Reliability | |
| 5 | `IDisposable` objects are disposed with `using`; no resource leaks on exception paths | Mandatory | Reliability, Performance Efficiency | |
| 6 | Async code uses `await` throughout: no `.Result` or `.Wait()` and no `async void` outside event handlers | Mandatory | Reliability, Performance Efficiency | |
| 7 | Specific exceptions are thrown; arguments are validated at public boundaries; rethrow uses `throw;`; no empty `catch` | Mandatory | Reliability, Security | |
| 8 | Public types and members have XML documentation comments | Optional | Usability, Maintainability | |
| 9 | State is exposed through properties, not public fields; immutability (`readonly`, `init`, `record`) is preferred where it fits | Optional | Maintainability, Reliability | |
| 10 | Money uses `decimal`; points in time use `DateTimeOffset` | Mandatory | Functional Suitability, Reliability | |
| 11 | Public async APIs accept and pass a `CancellationToken` where the operation can be cancelled | Optional | Performance Efficiency, Reliability | |
| 12 | Tests cover new behaviour, are named `Method_Condition_Expected`, and do not depend on order, time or the network | Mandatory | Reliability, Maintainability | |
| 13 | Classes and members trace to the Design Class Diagram they implement; deviations are recorded | Mandatory | Functional Suitability, Maintainability | |
| 14 | Each piece of knowledge (a business rule, constant, format, validation or query) is defined in one place; code is merged only where it expresses the same knowledge, not where it merely looks alike | Mandatory | Maintainability | Modularity, Reusability. Rule: `coding-conventions` skill, “State each piece of knowledge once” |
| 15 | Namespace and project references point inward: business-rule code references no framework, database, UI or delivery-mechanism code, and there are no reference cycles | Mandatory | Maintainability, Portability | Modularity, Portability. Rule: `coding-conventions` skill, “Dependencies point inward” |
| 16 | SOLID holds: a class has one reason to change; new behaviour is added by extension, not by editing a type test in several places; subtypes honour the contract of their base; interfaces are narrow; high-level code depends on interfaces and receives its implementations by injection | Mandatory | Maintainability | Single responsibility is the most commonly violated. Rule: `coding-conventions` skill, “SOLID” |
| 17 | Source is laid out in the layers and folders of the clean architecture folder structure (the projects `<App>.Domain`, `<App>.Application`, `<App>.Infrastructure` and `<App>.Presentation` under `src/`, and `unit`, `integration` and `e2e` under `tests/`), in `PascalCase`, and project references between the layers point inward | Mandatory | Maintainability, Portability | Structure: see the `clean-architecture` skill, "Folder structure". A merged layer is accepted when an ADR says why; `Domain` is never merged |
| 18 | File and folder names are English, contain no space and no character outside letters, digits, `-`, `_` and `.`, and follow the casing of the language for files | Mandatory | Usability, Maintainability, Portability | Names: rule 16 of `coding-conventions`; well-known names (`README.md`, `LICENSE`) and wiki page names are exceptions |

## Common Defects

- camelCase methods or snake_case members carried over from another language
- Nullable warnings silenced with `!` or pragmas
- `Task.Result` or `.Wait()` on the request path (deadlocks and thread starvation)
- `throw ex;` destroying the stack trace; empty `catch` blocks
- Undisposed `HttpClient`, streams or database connections
- `DateTime` used for instants, or `double` for money
- Several public types in one file, or a file name that differs from its type
- The same rule, constant or validation written in two places, or two methods merged because they look alike although they change for different reasons
- Business-rule code that references the ORM, the web framework or a database driver
- A class with several unrelated responsibilities, or `is`/`switch` type tests repeated in several places
- Source files in one flat folder, or a layer that exists only by a naming habit and not as a project or directory
- File or folder names with a space, in a language other than English, or in another language's casing

## Traceability Rule

- Backward: Design Class Diagram checklist ([QC-DCD-001]) for the classes and members being implemented; Architecture Decision Record checklist ([QC-ADR-001]) for the decisions that constrain the implementation
- Forward: none — source code is the end of the QC checklist chain

---

[QC-DCD-001]: ../artifacts/qc-dcd.md
[QC-ADR-001]: ../artifacts/qc-adr.md
[b5e5613]: https://git.tirsystem.com/TirSystem/SQA-QC-Checklists/commit/b5e5613a384527a18cd40594fc24cac4bdd11a31
