# Quality Criteria: Use Case (Brief / Casual / Fully Dressed)

## Metadata
| Key | Value |
| --- | --- |
| ID | QC-UC-001 |
| CrossReference | [QC-UCD-001], [QC-US-001], [QC-SA-001], [QC-DM-001], [QC-SSD-001] |
| DomainLanguages | IT Professional English |

## Version History
| Date | Status | Author | Reviewer | Change | Commit |
| --- | --- | --- | --- | --- | --- |
| 2026-10-01 | Accepted | Jens Tirsvad Nielsen | S07 | First public release (1.0.0) | — |

---

## Purpose

Use cases describe actor-goal-driven system behavior at three levels of formality (Brief, Casual, Fully Dressed, per Larman's *Applying UML and Patterns*), providing the functional detail that bridges stakeholder intent and downstream design artifacts such as the Domain Model and System Sequence Diagrams.

## Quality Criteria Checklist

Level: **Mandatory** criteria are the baseline every instance must meet; **Optional** criteria are advanced and may be deferred.

| # | Criterion | Level | Format | ISO/IEC 25010 Characteristic(s) | Notes |
| --- | --- | --- | --- | --- | --- |
| 1 | Consists of a single, concise paragraph summarizing only the primary success scenario | Mandatory | Brief | Functional Suitability | |
| 2 | Written as an informal multi-paragraph narrative; may mention some alternate flows without formal structure | Mandatory | Casual | Functional Suitability | |
| 3 | All standard sections are present: actors, preconditions, postconditions, main success scenario, alternative/exception flows | Mandatory | Fully Dressed | Functional Suitability, Maintainability | |
| 4 | Preconditions and postconditions are explicitly defined | Mandatory | All | Functional Suitability | |
| 5 | Primary actor is explicitly stated | Mandatory | All | Functional Suitability | |
| 6 | Stakeholders and their interests are stated | Mandatory | Fully Dressed | Functional Suitability | |
| 7 | Main success scenario is written as clear, numbered steps | Mandatory | Fully Dressed | Usability, Maintainability | |
| 8 | Alternative/exception flows correctly reference `<<include>>`/`<<extend>>` use cases where relevant, per UML 2.5.1 | Mandatory | Fully Dressed | Functional Suitability, Maintainability | |
| 9 | Explicit business rules are captured per step where applicable, rather than embedded loosely in narrative text | Optional | Fully Dressed | Functional Suitability, Reliability | |
| 10 | Naming of actors and use case title is consistent with the corresponding Use Case Diagram and User Stories | Mandatory | All | Compatibility, Maintainability | |
| 11 | Scope/level (e.g. summary, user-goal, subfunction) is explicitly stated | Optional | All | Usability, Maintainability | |
| 12 | Use case is written from the actor's goal perspective, free of UI or implementation detail | Mandatory | All | Usability, Portability | |

## Common Defects

- Fully Dressed use case missing postconditions or exception/alternative flows
- Brief use case bloated with step-by-step detail that belongs in the Fully Dressed format
- Casual use case omitting the primary actor or the actor's goal
- Business rules embedded loosely in narrative text instead of stated explicitly per step
- Inconsistent actor or use case naming versus the corresponding Use Case Diagram

## Traceability Rule

- Backward: Use Case Diagram checklist ([QC-UCD-001]), User Story checklist ([QC-US-001]), Stakeholder Analysis checklist ([QC-SA-001])
- Forward: Domain Model checklist ([QC-DM-001]), System Sequence Diagram checklist ([QC-SSD-001])

---

[QC-UCD-001]: ./qc-use-case-diagram.md
[QC-US-001]: ./qc-user-story.md
[QC-SA-001]: ./qc-stakeholder-analysis.md
[QC-DM-001]: ./qc-domain-model.md
[QC-SSD-001]: ./qc-ssd.md
