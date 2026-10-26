# Quality Criteria: React (TypeScript) Source Code

## Metadata
| Key | Value |
| --- | --- |
| ID | QC-RX-001 |
| CrossReference | [QC-DCD-001], [QC-ADR-001] |
| DomainLanguages | IT Professional English |

## Version History
| Date | Status | Author | Reviewer | Change | Commit |
| --- | --- | --- | --- | --- | --- |
| 2026-10-18 | Deprecated | Jens Tirsvad Nielsen | S02 | Created with the React conventions of the `coding-conventions` skill | [772e160] |
| 2026-10-22 | Accepted | Jens Tirsvad Nielsen | S02 | Renamed the ISO/IEC 25010 tags to the 2023 names: Usability to Interaction Capability, Portability to Flexibility (RC-083); accepted by the author as stand-in for S02 on the user's instruction in chat on 2026-10-26, through the pull request that merges this row; not independent | [404f664] |

---

## Purpose

React code stays correct only when components and hooks are pure and effects are used to synchronise with the outside world. TypeScript removes a class of defects only in `strict` mode and without `any`. This checklist confirms that React code follows the React and TypeScript conventions (naming, the Rules of React, state and effects, accessibility, formatting), so that it is correct, accessible, maintainable and consistent with the design it implements.

## Quality Criteria Checklist

Level: **Mandatory** criteria are the baseline every instance must meet; **Optional** criteria are advanced and may be deferred.

| # | Criterion | Level | ISO/IEC 25010 Characteristic(s) | Notes |
| --- | --- | --- | --- | --- |
| 1 | Components and types are `PascalCase`; functions and variables `camelCase`; hooks start with `use`; module-level constants `UPPER_SNAKE`; component files `PascalCase.tsx`, other files and folders `kebab-case` | Mandatory | Maintainability, Interaction Capability | |
| 2 | Names state purpose in the domain's language; props types are named `<Component>Props`; booleans read as a question; handlers are `on…` (props) and `handle…` (implementations) | Mandatory | Maintainability, Interaction Capability | |
| 3 | `tsc --noEmit` passes in `strict` mode; ESLint (with `typescript-eslint`, `react-hooks` and `jsx-a11y`) is clean, or each disable is justified | Mandatory | Reliability, Flexibility | |
| 4 | Code is produced by `prettier` (the check passes); imports are ordered; no unused import; lock file and configuration are committed | Mandatory | Maintainability | |
| 5 | Components and hooks are pure: render does no fetch, timer, subscription or DOM write; hooks are called only at the top level; state is never mutated | Mandatory | Reliability | Rules of React |
| 6 | State is minimal: derived values are computed in render, not stored; remote data is held by one server-state library, not copied into local state | Mandatory | Maintainability, Performance Efficiency | |
| 7 | Effects only synchronise with something outside React; every dependency is listed; every subscription, timer and request has a cleanup | Mandatory | Reliability | |
| 8 | No `any`, and no `!` or `as` cast without a comment; props are typed; alternatives are discriminated unions; data from the network is validated at the boundary | Mandatory | Reliability, Security | |
| 9 | Lists use a stable unique `key`, not the array index of a reorderable list | Mandatory | Reliability | |
| 10 | Errors are handled at a boundary that can act (`try`/`catch`, error boundary), never an empty `catch`; no floating promise; no stack trace or secret reaches the user | Mandatory | Reliability, Security | |
| 11 | Semantic elements are used (not a clickable `div`); inputs have labels, images have `alt`, and the UI works by keyboard | Mandatory | Interaction Capability | Accessibility |
| 12 | No `dangerouslySetInnerHTML` with unsanitised input and no secret in the client bundle; `memo`, `useMemo` and `useCallback` appear only where a measurement or an identity requirement justifies them | Optional | Security, Performance Efficiency | |
| 13 | Components and operations trace to the Design Class Diagram they implement; deviations are recorded | Mandatory | Functional Suitability, Maintainability | |
| 14 | Each piece of knowledge (a business rule, constant, format, validation or query) is defined in one place; code is merged only where it expresses the same knowledge, not where it merely looks alike | Mandatory | Maintainability | Modularity, Reusability. Rule: `coding-conventions` skill, “State each piece of knowledge once” |
| 15 | Dependencies point inward: `domain` and `application` import no `react`, DOM or network code, are imported through a layer's `index.ts`, and the import graph has no cycles | Mandatory | Maintainability, Flexibility | Modularity, Flexibility. Rule: `coding-conventions` skill, “Dependencies point inward” |
| 16 | SOLID holds: a component or module has one reason to change; new behaviour is added by composition or a new type, not by editing a flag or type switch in several places; interfaces and props are narrow; high-level code depends on a port it owns and receives the implementation | Mandatory | Maintainability | Rule: `coding-conventions` skill, “SOLID” |
| 17 | Source is laid out in the layers and folders of the clean architecture folder structure (`domain/`, `application/`, `infrastructure/` and `presentation/` under `src/`, features grouped under `presentation/`, and unit, integration and end-to-end tests separated) | Mandatory | Maintainability, Flexibility | Structure: see the `clean-architecture` skill, "Folder structure". A merged layer is accepted when an ADR says why; `Domain` is never merged |
| 18 | File and folder names are English, contain no space and no character outside letters, digits, `-`, `_` and `.`, and follow the casing of the language for files | Mandatory | Interaction Capability, Maintainability, Flexibility | Names: rule 16 of `coding-conventions` |
| 19 | Tests cover new behaviour, query by role, label or text, use fake timers and a fake network, and end-to-end tests run in a container or sandbox, not on the host desktop | Optional | Reliability, Interaction Capability | |

## Common Defects

- Fetching or mutating inside render, or hooks called in a condition or loop
- State that mirrors a prop, or state mutated in place
- An effect used to compute a value or to react to a user event; missing dependencies or cleanup
- `any`, `!` or `as` used to silence the compiler
- Array index as `key` in a list that reorders
- A clickable `div`, an input without a label, an image without `alt`
- Business rules inside components
- `memo`/`useMemo`/`useCallback` everywhere without a measurement
- An empty `catch` or a floating promise
- `dangerouslySetInnerHTML` with user data; a secret in the bundle
- The same rule, constant or validation written in two places
- File or folder names with a space, in a language other than English, or in another language's casing

## Traceability Rule

- Backward: Design Class Diagram checklist ([QC-DCD-001]) for the components and operations being implemented; Architecture Decision Record checklist ([QC-ADR-001]) for the decisions that constrain the implementation
- Forward: none — source code is the end of the QC checklist chain

---

[QC-DCD-001]: ../artifacts/qc-dcd.md
[QC-ADR-001]: ../artifacts/qc-adr.md
[772e160]: https://git.tirsystem.com/TirSystem/SQA-QC-Checklists/commit/772e1604b9f2911fd6780b88ae2425e2e522ec68
[404f664]: https://git.tirsystem.com/TirSystem/SQA-QC-Checklists/commit/404f66454eb129463cf0982b425ad16707bd66a9
