# Quality Criteria: C++ Source Code

## Metadata
| Key | Value |
| --- | --- |
| ID | QC-CPP-001 |
| CrossReference | [QC-DCD-001], [QC-ADR-001] |
| DomainLanguages | IT Professional English |

## Version History
| Date | Status | Author | Reviewer | Change | Commit |
| --- | --- | --- | --- | --- | --- |
| 2026-10-14 | Accepted | Jens Tirsvad Nielsen | S02 | Added criteria 17 and 18 (layer folders; file and folder names); accepted by the author as stand-in for S02 (Coding Standards Governance), through the pull request that merges this row; not independent of the author | [f65bb81] |
| 2026-10-22 | Proposed | Jens Tirsvad Nielsen | S02 | Renamed the ISO/IEC 25010 tags to the 2023 names: Usability to Interaction Capability, Portability to Flexibility (RC-083) | [404f664] |

---

## Purpose

C++ offers automatic resource management when used as designed and the same hazards as C when not. This checklist confirms that C++ code follows the C++ coding conventions (naming, RAII, C++ Core Guidelines), so that it is safe, maintainable and consistent with the design it implements.

## Quality Criteria Checklist

Level: **Mandatory** criteria are the baseline every instance must meet; **Optional** criteria are advanced and may be deferred.

| # | Criterion | Level | ISO/IEC 25010 Characteristic(s) | Notes |
| --- | --- | --- | --- | --- |
| 1 | Types are `PascalCase`; functions and variables `snake_case`; private members end in `_`; constants use `k` + `PascalCase`; namespaces are lowercase | Mandatory | Maintainability, Interaction Capability | |
| 2 | Names state purpose in the domain's language; no unexplained abbreviations | Mandatory | Maintainability, Interaction Capability | |
| 3 | Code compiles cleanly with the project's warning flags and the declared C++ standard | Mandatory | Reliability, Flexibility | |
| 4 | Code is produced by the project's formatter; includes are ordered and self-contained headers | Mandatory | Maintainability | |
| 5 | No owning raw pointers and no naked `new`/`delete`; resources are held by RAII types (`unique_ptr`, containers, guards) | Mandatory | Reliability, Security | |
| 6 | Special member functions follow the rule of zero, or all five are defined or deleted | Mandatory | Reliability, Maintainability | |
| 7 | `const`, `constexpr`, `explicit`, `override` and `[[nodiscard]]` are used where they apply | Mandatory | Reliability, Maintainability | |
| 8 | No C-style casts, no `using namespace` in headers, no macros where a function, `constexpr` or `enum class` works | Mandatory | Maintainability, Reliability | |
| 9 | Error handling uses one strategy per project (exceptions or error codes); destructors do not throw; no silent `catch (...)` | Mandatory | Reliability | |
| 10 | Non-owning parameters use views (`std::span`, `std::string_view`) or `const&`; no dangling references to temporaries | Optional | Performance Efficiency, Reliability | |
| 11 | Static analysis with the Core Guidelines checks is clean, or each suppression is justified | Optional | Reliability, Maintainability | |
| 12 | Tests cover new behaviour and run under address and undefined-behaviour sanitizers in at least one build | Optional | Reliability, Security | |
| 13 | Classes and operations trace to the Design Class Diagram they implement; deviations are recorded | Mandatory | Functional Suitability, Maintainability | |
| 14 | Each piece of knowledge (a business rule, constant, format, validation or query) is defined in one place; code is merged only where it expresses the same knowledge, not where it merely looks alike | Mandatory | Maintainability | Modularity, Reusability. Rule: `coding-conventions` skill, “State each piece of knowledge once” |
| 15 | Includes and link dependencies point inward: business-rule code includes no I/O, platform, UI or framework headers, and the include graph has no cycles | Mandatory | Maintainability, Flexibility | Modularity, Flexibility. Rule: `coding-conventions` skill, “Dependencies point inward” |
| 16 | SOLID holds: a class has one reason to change; new behaviour is added by a new derived type, not by editing a type switch in several places; derived classes honour the contract of their base (`override`); abstract interfaces are narrow; high-level code depends on abstract types and receives its implementations | Mandatory | Maintainability | Single responsibility is the most commonly violated. Rule: `coding-conventions` skill, “SOLID” |
| 17 | Source is laid out in the layers and folders of the clean architecture folder structure (`domain/`, `application/`, `infrastructure/` and `presentation/` directories with a `snake_case` namespace each, and `unit`, `integration` and `e2e` under `tests/`), and includes and link dependencies between the layers point inward | Mandatory | Maintainability, Flexibility | Structure: see the `clean-architecture` skill, "Folder structure". A merged layer is accepted when an ADR says why; `Domain` is never merged |
| 18 | File and folder names are English, contain no space and no character outside letters, digits, `-`, `_` and `.`, and follow the casing of the language for files | Mandatory | Interaction Capability, Maintainability, Flexibility | Names: rule 16 of `coding-conventions`; well-known names (`README.md`, `LICENSE`) and wiki page names are exceptions |

## Common Defects

- `new` and `delete` in application code, or a raw owning pointer member
- Destructor, copy or move operations defined inconsistently (only some of the five)
- Missing `override` or `explicit`; ignored return values of `[[nodiscard]]` functions
- `using namespace std;` in a header
- Macros for constants or small functions
- Returning a reference or view to a local or temporary
- Exceptions and error codes mixed in the same module without a stated rule
- The same rule, constant or validation written in two places, or two functions merged because they look alike although they change for different reasons
- Business-rule code that includes a framework, platform or database header
- A class with several unrelated responsibilities, or a `switch` on a type code repeated in several places
- Source files in one flat folder, or a layer that exists only by a naming habit and not as a project or directory
- File or folder names with a space, in a language other than English, or in another language's casing

## Traceability Rule

- Backward: Design Class Diagram checklist ([QC-DCD-001]) for the classes and operations being implemented; Architecture Decision Record checklist ([QC-ADR-001]) for the decisions that constrain the implementation
- Forward: none — source code is the end of the QC checklist chain

---

[QC-DCD-001]: ../artifacts/qc-dcd.md
[QC-ADR-001]: ../artifacts/qc-adr.md
[f65bb81]: https://git.tirsystem.com/TirSystem/SQA-QC-Checklists/commit/f65bb81af825478f73e0f65463c69c32fe8b45c9
[404f664]: https://git.tirsystem.com/TirSystem/SQA-QC-Checklists/commit/404f66454eb129463cf0982b425ad16707bd66a9
