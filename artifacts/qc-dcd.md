# Quality Criteria: Design Class Diagram (DCD)

## Metadata
| Key | Value |
| --- | --- |
| ID | QC-DCD-001 |
| CrossReference | [QC-DM-001], [QC-SD-001], [QC-ERD-001], [QC-PY-001], [QC-CL-001], [QC-CPP-001], [QC-CS-001] |
| DomainLanguages | IT Professional English |

## Version History
| Date | Status | Author | Reviewer | Change | Commit |
| --- | --- | --- | --- | --- | --- |
| 2026-10-22 | Proposed | Jens Tirsvad Nielsen | S02 | Renamed the ISO/IEC 25010 tags to the 2023 names: Usability to Interaction Capability, Portability to Flexibility (RC-083) | [404f664] |
| 2026-10-26 | Proposed | Jens Tirsvad Nielsen | S02 | Added criterion 10 (the Purpose names the concerns the view answers) | [f9409f9] |

---

## Purpose

The Design Class Diagram specifies the concrete classes, attributes, operations, and relationships that will be implemented, refining the Domain Model with design decisions from the Sequence Diagrams. Its quality directly determines the maintainability and correctness of the resulting implementation.

## Quality Criteria Checklist

Level: **Mandatory** criteria are the baseline every instance must meet; **Optional** criteria are advanced and may be deferred.

| # | Criterion | Level | ISO/IEC 25010 Characteristic(s) | Notes |
| --- | --- | --- | --- | --- |
| 1 | SOLID principles applied; no god classes with excessive responsibilities | Mandatory | Maintainability | Single Responsibility Principle is the most commonly violated |
| 2 | Visibility markers correct and consistent (`+` public, `-` private, `#` protected) | Mandatory | Maintainability | Encapsulation must be explicit, not assumed |
| 3 | Relationships correctly distinguished: Association vs Aggregation vs Composition vs Dependency | Mandatory | Functional Suitability, Maintainability | Diamond notation must match actual ownership semantics |
| 4 | Multiplicities and navigability specified on all associations | Mandatory | Functional Suitability | Unspecified navigability leads to ambiguous implementation |
| 5 | Applied design patterns are annotated explicitly (e.g. Singleton, Factory, Strategy) | Optional | Maintainability | Pattern intent should be discoverable from the diagram |
| 6 | Method signatures are traceable to Operation Contracts and/or design Sequence Diagrams | Mandatory | Functional Suitability, Maintainability | Prevents drift between design layers |
| 7 | Class names and structure remain consistent with the Domain Model concepts they refine | Mandatory | Maintainability, Compatibility | Design classes should not silently rename or drop domain concepts |
| 8 | No circular dependencies between classes/packages unless explicitly justified | Optional | Maintainability, Reliability | Circular coupling harms testability and portability |
| 9 | Dependencies between classes and packages point inward: domain classes do not depend on infrastructure, delivery or framework classes | Mandatory | Maintainability, Flexibility | Business rules must be buildable and testable without the outer layers; cycles are criterion 8 |
| 10 | The Purpose names the concerns (`CN-NNN`) the Design Class Diagram answers and the stakeholders it serves, so its viewpoint is stated | Optional | Interaction Capability, Maintainability | Viewpoint of ISO/IEC/IEEE 42010; see `process/architecture-description.md` of the framework |

## Common Defects

- God classes accumulating unrelated responsibilities
- Missing or incorrect visibility markers
- Composition used where the parts do not share the whole's lifecycle (or vice versa)
- Method signatures that don't match any Operation Contract or Sequence Diagram message
- Unannotated or inconsistently applied design patterns
- Domain classes that depend on persistence, user-interface or framework classes
- A Design Class Diagram whose Purpose does not say which concerns it answers

## Traceability Rule

- Backward: Must trace to the Domain Model checklist ([QC-DM-001]) (concept origin) and the design Sequence Diagram checklist ([QC-SD-001]) (object collaborations and method signatures)
- Forward: Feeds into the Entity Relationship Diagram checklist ([QC-ERD-001]) for persistent classes, and into the language code checklists ([QC-PY-001], [QC-CL-001], [QC-CPP-001], [QC-CS-001]) for the implementation of the classes

---

[QC-DM-001]: ./qc-domain-model.md
[QC-SD-001]: ./qc-sequence-diagram.md
[QC-ERD-001]: ./qc-erd.md
[QC-PY-001]: ../code/qc-programming-python.md
[QC-CL-001]: ../code/qc-programming-c.md
[QC-CPP-001]: ../code/qc-programming-cpp.md
[QC-CS-001]: ../code/qc-programming-csharp.md
[b5e5613]: https://git.tirsystem.com/TirSystem/SQA-QC-Checklists/commit/b5e5613a384527a18cd40594fc24cac4bdd11a31
[404f664]: https://git.tirsystem.com/TirSystem/SQA-QC-Checklists/commit/404f66454eb129463cf0982b425ad16707bd66a9
[f9409f9]: https://git.tirsystem.com/TirSystem/SQA-QC-Checklists/commit/f9409f9260b24321b8f9a11b8ce3c40698fae9ac
