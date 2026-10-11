# Quality Criteria: Use Case Diagram

## Metadata
| Key | Value |
| --- | --- |
| ID | QC-UCD-001 |
| CrossReference | [QC-SA-001], [QC-BC-001], [QC-US-001], [QC-UC-001] |
| DomainLanguages | IT Professional English |

## Version History
| Date | Status | Author | Reviewer | Change | Commit |
| --- | --- | --- | --- | --- | --- |
| 2026-10-01 | Accepted | Jens Tirsvad Nielsen | S07 | First public release (1.0.0) | — |

---

## Purpose

Use case diagrams define the system boundary and the actors that interact with it, establishing shared scope agreement before detailed behavior is specified. They anchor traceability between stakeholder needs and the more detailed use case and user story artifacts that follow.

## Quality Criteria Checklist

Level: **Mandatory** criteria are the baseline every instance must meet; **Optional** criteria are advanced and may be deferred.

| # | Criterion | Level | ISO/IEC 25010 Characteristic(s) | Notes |
| --- | --- | --- | --- | --- |
| 1 | Actors are defined with correct UML stereotypes (e.g. `<<System>>`, `<<Actor>>`) | Mandatory | Functional Suitability, Maintainability | |
| 2 | System boundary is clearly drawn and labeled | Mandatory | Functional Suitability | |
| 3 | Include/extend relationships are used correctly per UML 2.5.1, not as generic "uses" arrows | Mandatory | Functional Suitability, Maintainability | |
| 4 | Every actor participates in at least one use case (no orphan actors) | Mandatory | Functional Suitability | |
| 5 | Diagram is traceable to a documented stakeholder need | Mandatory | Functional Suitability, Maintainability | |
| 6 | Use case names are verb phrases describing actor goals, not internal system operations | Mandatory | Usability, Maintainability | |
| 7 | Diagram is free of implementation detail (e.g. UI widgets, database tables) | Optional | Maintainability, Portability | |
| 8 | Actor and use case naming is consistent with corresponding Use Case and User Story documents | Optional | Compatibility, Maintainability | |

## Common Defects

- Actors modeled as use cases, or use cases modeled as actors
- Overuse of `<<include>>`/`<<extend>>` to represent what is really normal sequential flow
- Missing or ambiguous system boundary
- Orphan actors with no connected use case
- Use case names phrased as system functions (e.g. "Validate Input") rather than user goals (e.g. "Place Order")

## Traceability Rule

- Backward: Stakeholder Analysis checklist ([QC-SA-001]), Business Case checklist ([QC-BC-001])
- Forward: User Story checklist ([QC-US-001]), Use Case checklist ([QC-UC-001]) (Brief, Casual, Fully Dressed)

---

[QC-SA-001]: ./qc-stakeholder-analysis.md
[QC-BC-001]: ./qc-business-case.md
[QC-US-001]: ./qc-user-story.md
[QC-UC-001]: ./qc-use-case.md
