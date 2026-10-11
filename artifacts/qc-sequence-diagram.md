# Quality Criteria: Sequence Diagram (Design)

## Metadata
| Key | Value |
| --- | --- |
| ID | QC-SD-001 |
| CrossReference | [QC-OC-001], [QC-DCD-001] |
| DomainLanguages | IT Professional English |

## Version History
| Date | Status | Author | Reviewer | Change | Commit |
| --- | --- | --- | --- | --- | --- |
| 2026-10-01 | Accepted | Jens Tirsvad Nielsen | S07 | First public release (1.0.0) | — |

---

## Purpose

A design-level Sequence Diagram shows how internal design objects collaborate to fulfill an Operation Contract's postconditions, applying GRASP/GoF patterns for responsibility assignment. Its quality determines whether the resulting object interactions are correct, maintainable, and implementable as specified.

## Quality Criteria Checklist

Level: **Mandatory** criteria are the baseline every instance must meet; **Optional** criteria are advanced and may be deferred.

| # | Criterion | Level | ISO/IEC 25010 Characteristic(s) | Notes |
| --- | --- | --- | --- | --- |
| 1 | Message passing strictly follows UML sync/async/return arrow syntax | Mandatory | Functional Suitability, Maintainability | Solid filled-arrow for sync calls, open arrow for async, dashed for returns |
| 2 | GRASP/GoF patterns applied and explicitly annotated where used (e.g. Controller, Observer, Mediator, Factory) | Optional | Maintainability | Pattern usage must be labeled, not implicit |
| 3 | Lifelines show activation bars matching actual processing time/call nesting | Optional | Performance Efficiency, Maintainability | Nested activations must reflect the true call stack |
| 4 | Object creation and destruction shown with correct UML notation (`create`/`destroy` messages, X on lifeline) | Mandatory | Functional Suitability | Missing creation messages hide important object lifecycle |
| 5 | Diagram realizes the postconditions of a specific Operation Contract | Mandatory | Functional Suitability | Every postcondition must be satisfiable by the shown collaboration |
| 6 | Responsibility assignment favors low coupling/high cohesion (no god-object receiving all messages) | Optional | Maintainability | Reviewer should check GRASP Controller isn't overloaded |
| 7 | Loop, alt, and opt combined fragments used correctly for conditional/repeated behavior | Mandatory | Functional Suitability | Avoids ambiguous or missing control flow |
| 8 | Each exception of the realized Operation Contract is shown as an `alt` or `opt` fragment, or its absence is justified | Optional | Reliability, Functional Suitability | Keeps the design consistent with the contract's error conditions |

## Common Defects

- Arrow types inconsistent with UML (e.g. using sync arrows for async calls)
- No annotation of applied design patterns, leaving intent implicit
- A single "god" controller object receiving and handling all responsibilities
- Missing creation/destruction notation for transient objects
- Diagram does not actually satisfy the referenced Operation Contract's postconditions
- An error condition of the Operation Contract that never appears in the diagram, or an error drawn as a fragment that does not stop the flow

## Traceability Rule

- Backward: Must trace to a specific Operation Contract checklist ([QC-OC-001]) whose postconditions the collaboration fulfills
- Forward: Feeds into the Design Class Diagram checklist ([QC-DCD-001]), where participating objects become classes with the operations/messages shown here

---

[QC-OC-001]: ./qc-operation-contract.md
[QC-DCD-001]: ./qc-dcd.md
