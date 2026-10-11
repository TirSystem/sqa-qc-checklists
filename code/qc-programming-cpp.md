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
| 2026-10-09 | Deprecated | Jens Tirsvad Nielsen | S02 | Added criteria 14 to 16 (DRY, dependency rule and SOLID) | [304ec77] |
| 2026-10-09 | Accepted | Jens Tirsvad Nielsen | S02 | Accepted by the author as stand-in for S02 (Coding Standards Governance), through the pull request that merges this row; the delta re-review of the new criteria is a draft confirmed by the author as stand-in, not independently | [b5e5613] |

---

## Purpose

C++ offers automatic resource management when used as designed and the same hazards as C when not. This checklist confirms that C++ code follows the C++ coding conventions (naming, RAII, C++ Core Guidelines), so that it is safe, maintainable and consistent with the design it implements.

## Quality Criteria Checklist

Level: **Mandatory** criteria are the baseline every instance must meet; **Optional** criteria are advanced and may be deferred.

| # | Criterion | Level | ISO/IEC 25010 Characteristic(s) | Notes |
| --- | --- | --- | --- | --- |
| 1 | Types are `PascalCase`; functions and variables `snake_case`; private members end in `_`; constants use `k` + `PascalCase`; namespaces are lowercase | Mandatory | Maintainability, Usability | |
| 2 | Names state purpose in the domain's language; no unexplained abbreviations | Mandatory | Maintainability, Usability | |
| 3 | Code compiles cleanly with the project's warning flags and the declared C++ standard | Mandatory | Reliability, Portability | |
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
| 15 | Includes and link dependencies point inward: business-rule code includes no I/O, platform, UI or framework headers, and the include graph has no cycles | Mandatory | Maintainability, Portability | Modularity, Portability. Rule: `coding-conventions` skill, “Dependencies point inward” |
| 16 | SOLID holds: a class has one reason to change; new behaviour is added by a new derived type, not by editing a type switch in several places; derived classes honour the contract of their base (`override`); abstract interfaces are narrow; high-level code depends on abstract types and receives its implementations | Mandatory | Maintainability | Single responsibility is the most commonly violated. Rule: `coding-conventions` skill, “SOLID” |

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

## Traceability Rule

- Backward: Design Class Diagram checklist ([QC-DCD-001]) for the classes and operations being implemented; Architecture Decision Record checklist ([QC-ADR-001]) for the decisions that constrain the implementation
- Forward: none — source code is the end of the QC checklist chain

---

[QC-DCD-001]: ../artifacts/qc-dcd.md
[QC-ADR-001]: ../artifacts/qc-adr.md
[304ec77]: https://git.tirsystem.com/TirSystem/SQA-QC-Checklists/commit/304ec7751bd39ff6d54862c2cd10958ef90123ff
[b5e5613]: https://git.tirsystem.com/TirSystem/SQA-QC-Checklists/commit/b5e5613a384527a18cd40594fc24cac4bdd11a31
