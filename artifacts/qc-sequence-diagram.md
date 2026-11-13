# Quality Criteria: Sequence Diagram (Design)

## Metadata
| Key | Value |
| --- | --- |
| ID | QC-SD-001 |
| CrossReference | [QC-OC-001], [QC-DCD-001] |

## Version History
| Date | Status | Author | Reviewer | Change | Commit |
| --- | --- | --- | --- | --- | --- |
| 2026-10-26 | Deprecated | Jens Tirsvad Nielsen | S07 | Added criterion 9 (the Purpose names the concerns the view answers); accepted by the author as stand-in for S07 on the user's instruction in chat on 2026-10-26, through the pull request that merges this row; not independent | [f9409f9] |
| 2026-11-08 | Deprecated | Jens Tirsvad Nielsen | S07 | Removed the obsolete DomainLanguages metadata row; the register is per artifact type in the project registry (issue 6); accepted by the author in chat as stand-in for S07, not independent | [ce06e14] |
| 2026-11-13 | Deprecated | Jens Tirsvad Nielsen | S07 | Added criterion 10 (a layered architecture shows its layers in the diagram) | [c855322] |
| 2026-11-13 | Accepted | Jens Tirsvad Nielsen | S07 | Added criterion 11 (each layer in its fixed pastel colour); accepted by the author in chat as stand-in for S07, not independent | — |

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
| 9 | The Purpose names the concerns (`CN-NNN`) the Sequence Diagram answers and the stakeholders it serves, so its viewpoint is stated | Optional | Interaction Capability, Maintainability | Viewpoint of ISO/IEC/IEEE 42010; see `process/architecture-description.md` of the framework |
| 10 | When the design uses a layered architecture (Clean, Hexagonal, Onion or similar), the lifelines are grouped by layer and calls across a layer boundary go through the inner layer's interface | Mandatory | Maintainability, Flexibility | Applies only if the architecture is layered; the layer names match the packages of the Design Class Diagram |
| 11 | When the design uses a layered architecture, each layer is drawn in its fixed pastel colour: Delivery `#FADADD`, Application `#FFF3B0`, Domain `#CDEFD3`, Infrastructure `#D4E4F7` | Optional | Interaction Capability, Maintainability | The same colours in every Sequence Diagram and Design Class Diagram, so a layer is recognised by its colour; a layer name from another architecture (Use Cases, Entities, Frameworks and Drivers) takes the colour of the layer it matches |

## Common Defects

- Arrow types inconsistent with UML (e.g. using sync arrows for async calls)
- No annotation of applied design patterns, leaving intent implicit
- A single "god" controller object receiving and handling all responsibilities
- Missing creation/destruction notation for transient objects
- Diagram does not actually satisfy the referenced Operation Contract's postconditions
- An error condition of the Operation Contract that never appears in the diagram, or an error drawn as a fragment that does not stop the flow
- A Sequence Diagram whose Purpose does not say which concerns it answers
- A layered design whose Sequence Diagram does not show the layers, or an inner-layer object that calls an outer-layer concrete object
- A layered design whose layers are drawn in other colours than the fixed ones, or in no colour

## Traceability Rule

- Backward: Must trace to a specific Operation Contract checklist ([QC-OC-001]) whose postconditions the collaboration fulfills
- Forward: Feeds into the Design Class Diagram checklist ([QC-DCD-001]), where participating objects become classes with the operations/messages shown here

---

[QC-OC-001]: ./qc-operation-contract.md
[QC-DCD-001]: ./qc-dcd.md
[f9409f9]: https://git.tirsystem.com/TirSystem/SQA-QC-Checklists/commit/f9409f9260b24321b8f9a11b8ce3c40698fae9ac
[ce06e14]: https://git.tirsystem.com/TirSystem/SQA-QC-Checklists/commit/ce06e14cbe173c007b78858bd8a5474d1668e9ab
[c855322]: https://git.tirsystem.com/TirSystem/SQA-QC-Checklists/commit/c855322ae37d637b7a6dd141d7d1f22283bdc1ec
