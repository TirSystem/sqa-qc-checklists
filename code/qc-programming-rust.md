# Quality Criteria: Rust Source Code

## Metadata
| Key | Value |
| --- | --- |
| ID | QC-RS-001 |
| CrossReference | [QC-DCD-001], [QC-ADR-001] |
| DomainLanguages | IT Professional English |

## Version History
| Date | Status | Author | Reviewer | Change | Commit |
| --- | --- | --- | --- | --- | --- |
| 2026-10-18 | Proposed | Jens Tirsvad Nielsen | S02 | Created with the Rust conventions of the `coding-conventions` skill | [772e160] |
| 2026-10-22 | Proposed | Jens Tirsvad Nielsen | S02 | Renamed the ISO/IEC 25010 tags to the 2023 names: Usability to Interaction Capability, Portability to Flexibility (RC-083) | [404f664] |

---

## Purpose

Rust removes whole classes of memory and data-race defects when its safe subset is used as designed, and loses that guarantee through `unsafe`, `unwrap` and unchecked assumptions. This checklist confirms that Rust code follows the Rust conventions (naming, ownership, error handling, formatting), so that it is safe, maintainable and consistent with the design it implements.

## Quality Criteria Checklist

Level: **Mandatory** criteria are the baseline every instance must meet; **Optional** criteria are advanced and may be deferred.

| # | Criterion | Level | ISO/IEC 25010 Characteristic(s) | Notes |
| --- | --- | --- | --- | --- |
| 1 | Types and traits are `PascalCase`; functions, variables, modules and files `snake_case`; constants `UPPER_SNAKE`; acronyms are one word (`HttpClient`) | Mandatory | Maintainability, Interaction Capability | |
| 2 | Names state purpose in the domain's language; getters have no `get_` prefix; conversions use `as_`, `to_` and `into_` by cost; booleans read as a question | Mandatory | Maintainability, Interaction Capability | |
| 3 | Code builds on the pinned stable toolchain and edition with no warning, and `cargo clippy -- -D warnings` is clean or each `allow` is justified | Mandatory | Reliability, Flexibility | |
| 4 | Code is produced by `rustfmt` (`cargo fmt --check` passes); `Cargo.lock` is committed for a binary | Mandatory | Maintainability | |
| 5 | Parameters borrow (`&str`, `&[T]`) unless the function stores or consumes the value; no `clone()` that only silences the borrow checker | Mandatory | Performance Efficiency, Maintainability | |
| 6 | `unsafe` is forbidden or confined to one small module; every `unsafe` block has a `// SAFETY:` comment stating its invariant and is wrapped in a safe API | Mandatory | Security, Reliability | |
| 7 | No `unwrap`, `expect` (without a proven-invariant message), `panic!`, `todo!` or unchecked indexing in library or production code | Mandatory | Reliability | Allowed in tests |
| 8 | Errors are `Result` values propagated with `?`; a library has a typed error `enum` that keeps the source error; no `Result` is discarded without a comment; panics are reserved for broken invariants | Mandatory | Reliability, Maintainability | |
| 9 | Invalid states are unrepresentable: alternatives are `enum`s, validated values are newtypes, `match` on an own enum has no `_` arm | Mandatory | Reliability, Maintainability | |
| 10 | Shared state uses channels or the smallest `Mutex`/`RwLock` critical section; no lock is held across an `.await`; `Send`/`Sync` bounds are stated | Optional | Reliability, Performance Efficiency | |
| 11 | Public items have `///` documentation with `# Errors`, `# Panics` and `# Safety` sections where they apply; examples are doctests | Optional | Interaction Capability, Maintainability | |
| 12 | Tests cover new behaviour (unit tests in the module, integration tests in `tests/`), use no fixed sleep, and `cargo miri test` runs on code that contains `unsafe` | Optional | Reliability, Security | |
| 13 | Types and operations trace to the Design Class Diagram they implement; deviations are recorded | Mandatory | Functional Suitability, Maintainability | |
| 14 | Each piece of knowledge (a business rule, constant, format, validation or query) is defined in one place; code is merged only where it expresses the same knowledge, not where it merely looks alike | Mandatory | Maintainability | Modularity, Reusability. Rule: `coding-conventions` skill, “State each piece of knowledge once” |
| 15 | Dependencies point inward: the `domain` crate (or module) has no workspace dependency and no I/O, framework or database crate, and the crate graph has no cycles | Mandatory | Maintainability, Flexibility | Modularity, Flexibility. Rule: `coding-conventions` skill, “Dependencies point inward” |
| 16 | SOLID holds: a type or module has one reason to change; new behaviour is added by a new trait implementation, not by editing a `match` repeated in several places; traits are narrow; high-level code depends on a trait it owns and receives the implementation | Mandatory | Maintainability | Rule: `coding-conventions` skill, “SOLID” |
| 17 | Source is laid out in the layers and folders of the clean architecture folder structure (`domain`, `application`, `infrastructure` and `presentation` as crates or modules in a workspace, and unit, integration and end-to-end tests separated) | Mandatory | Maintainability, Flexibility | Structure: see the `clean-architecture` skill, "Folder structure". A merged layer is accepted when an ADR says why; `Domain` is never merged |
| 18 | File and folder names are English, contain no space and no character outside letters, digits, `-`, `_` and `.`, and follow the casing of the language for files | Mandatory | Interaction Capability, Maintainability, Flexibility | Names: rule 16 of `coding-conventions` |

## Common Defects

- `unwrap()` or `expect()` on input or I/O in production code
- `clone()` added to make the borrow checker pass
- `unsafe` without a `// SAFETY:` comment, or spread across the code base
- `Result` ignored with `let _ =`, or the same error logged and returned
- `&String` or `&Vec<T>` parameters; `Box<dyn Error>` leaking out of a library
- A `_ =>` arm that hides a new enum variant
- A lock held across an `.await`
- The same rule, constant or validation written in two places
- A domain crate that depends on a database, HTTP or runtime crate
- File or folder names with a space, in a language other than English, or in another language's casing

## Traceability Rule

- Backward: Design Class Diagram checklist ([QC-DCD-001]) for the types and operations being implemented; Architecture Decision Record checklist ([QC-ADR-001]) for the decisions that constrain the implementation
- Forward: none — source code is the end of the QC checklist chain

---

[QC-DCD-001]: ../artifacts/qc-dcd.md
[QC-ADR-001]: ../artifacts/qc-adr.md
[772e160]: https://git.tirsystem.com/TirSystem/SQA-QC-Checklists/commit/772e1604b9f2911fd6780b88ae2425e2e522ec68
[404f664]: https://git.tirsystem.com/TirSystem/SQA-QC-Checklists/commit/404f66454eb129463cf0982b425ad16707bd66a9
