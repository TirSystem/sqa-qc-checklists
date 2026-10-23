# Quality Criteria: Flutter (Dart) Source Code

## Metadata
| Key | Value |
| --- | --- |
| ID | QC-FL-001 |
| CrossReference | [QC-DCD-001], [QC-ADR-001] |
| DomainLanguages | IT Professional English |

## Version History
| Date | Status | Author | Reviewer | Change | Commit |
| --- | --- | --- | --- | --- | --- |
| 2026-10-18 | Proposed | Jens Tirsvad Nielsen | S02 | Created with the Flutter conventions of the `coding-conventions` skill | [772e160] |
| 2026-10-22 | Proposed | Jens Tirsvad Nielsen | S02 | Renamed the ISO/IEC 25010 tags to the 2023 names: Usability to Interaction Capability, Portability to Flexibility (RC-083) | pending |

---

## Purpose

A Flutter app mixes UI code, state and platform calls in one language, which makes it easy to put business rules in widgets and side effects in `build`. This checklist confirms that Flutter code follows the Flutter and Effective Dart conventions (naming, null safety, widget and state rules, formatting), so that it is correct, maintainable and consistent with the design it implements.

## Quality Criteria Checklist

Level: **Mandatory** criteria are the baseline every instance must meet; **Optional** criteria are advanced and may be deferred.

| # | Criterion | Level | ISO/IEC 25010 Characteristic(s) | Notes |
| --- | --- | --- | --- | --- |
| 1 | Types, widgets and extensions are `PascalCase`; functions, variables and constants `lowerCamelCase`; files, directories and packages `snake_case`; private members start with `_` | Mandatory | Maintainability, Interaction Capability | |
| 2 | Names state purpose in the domain's language; a widget file holds one public widget named after it; booleans read as a question | Mandatory | Maintainability, Interaction Capability | |
| 3 | `flutter analyze` is clean with the project's `analysis_options.yaml` (`flutter_lints` or stricter), or each ignore is justified; the Flutter version is pinned | Mandatory | Reliability, Flexibility | |
| 4 | Code is produced by `dart format` (the check passes); imports are ordered; generated files are not hand-edited | Mandatory | Maintainability | |
| 5 | Null safety is respected: no unexplained `!` or `late`; no `dynamic` in a public API; entity and state classes are immutable | Mandatory | Reliability, Maintainability | |
| 6 | `build` is pure: no network, file, timer, navigation or state change in it; side effects are in a view model, controller or event handler | Mandatory | Reliability, Performance Efficiency | |
| 7 | Large `build` methods are split into widget classes, not helper methods; `const` constructors are used wherever possible | Mandatory | Performance Efficiency, Maintainability | |
| 8 | Controllers, subscriptions and animations are disposed in `dispose()`; a `BuildContext` is not used after an `await` without a `mounted` check | Mandatory | Reliability | |
| 9 | Errors are handled by type (`on X catch`), never swallowed, never a thrown string; failures map to UI state (loading, data, error); uncaught errors reach `FlutterError.onError` | Mandatory | Reliability, Interaction Capability | |
| 10 | One state-management approach is used across the project; business rules are not in widgets | Mandatory | Maintainability | |
| 11 | User-visible text comes from localisation, styling from `Theme`, and non-text controls have `Semantics` labels | Optional | Interaction Capability, Flexibility | |
| 12 | Tests cover new behaviour (unit, widget, and integration for key flows), use fakes and no fixed delay, and GUI or end-to-end tests run in a container or sandbox, not on the host desktop | Optional | Reliability, Interaction Capability | |
| 13 | Classes and operations trace to the Design Class Diagram they implement; deviations are recorded | Mandatory | Functional Suitability, Maintainability | |
| 14 | Each piece of knowledge (a business rule, constant, format, validation or query) is defined in one place; code is merged only where it expresses the same knowledge, not where it merely looks alike | Mandatory | Maintainability | Modularity, Reusability. Rule: `coding-conventions` skill, “State each piece of knowledge once” |
| 15 | Dependencies point inward: `domain` and `application` import no `package:flutter` and no network, storage or platform package, and imports have no cycles | Mandatory | Maintainability, Flexibility | Modularity, Flexibility. Rule: `coding-conventions` skill, “Dependencies point inward” |
| 16 | SOLID holds: a class or widget has one reason to change; new behaviour is added by a new subtype, not by editing a type switch in several places; abstract ports are narrow; high-level code depends on an abstract repository and receives the implementation | Mandatory | Maintainability | Rule: `coding-conventions` skill, “SOLID” |
| 17 | Source is laid out in the layers and folders of the clean architecture folder structure (`domain/`, `application/`, `infrastructure/` and `presentation/` under `lib/`, features grouped under `presentation/`, tests mirroring `lib/`) | Mandatory | Maintainability, Flexibility | Structure: see the `clean-architecture` skill, "Folder structure". A merged layer is accepted when an ADR says why; `Domain` is never merged |
| 18 | File and folder names are English, contain no space and no character outside letters, digits, `-`, `_` and `.`, and follow the casing of the language for files | Mandatory | Interaction Capability, Maintainability, Flexibility | Names: rule 16 of `coding-conventions` |

## Common Defects

- Network calls, navigation or `setState` inside `build`
- Business rules in a widget's event handler
- Helper methods that return widgets instead of widget classes; missing `const`
- A controller, stream subscription or animation never disposed
- `BuildContext` used after an `await`
- `!` or `late` used to silence the analyzer
- `catch (e)` that swallows, or `throw 'text'`
- Hard-coded strings, colours and sizes
- `print` left in the code; `dart:io` in code that runs on the web
- A domain class that imports `package:flutter`
- The same rule, constant or validation written in two places
- File or folder names with a space, in a language other than English, or in another language's casing

## Traceability Rule

- Backward: Design Class Diagram checklist ([QC-DCD-001]) for the classes and operations being implemented; Architecture Decision Record checklist ([QC-ADR-001]) for the decisions that constrain the implementation
- Forward: none — source code is the end of the QC checklist chain

---

[QC-DCD-001]: ../artifacts/qc-dcd.md
[QC-ADR-001]: ../artifacts/qc-adr.md
[772e160]: https://git.tirsystem.com/TirSystem/SQA-QC-Checklists/commit/772e1604b9f2911fd6780b88ae2425e2e522ec68
