# Quality Criteria: User Story

## Metadata
| Key | Value |
| --- | --- |
| ID | QC-US-001 |
| CrossReference | [QC-UCD-001], [QC-UC-001], [QC-BC-001] |
| DomainLanguages | IT Professional English |

## Version History
| Date | Status | Author | Reviewer | Change | Commit |
| --- | --- | --- | --- | --- | --- |
| 2026-10-01 | Accepted | Jens Tirsvad Nielsen | S07 | First public release (1.0.0) | — |

---

## Purpose

User stories capture user-valued increments of functionality in a lightweight, negotiable format that drives backlog prioritization, estimation, and iterative delivery planning.

## Quality Criteria Checklist

Level: **Mandatory** criteria are the baseline every instance must meet; **Optional** criteria are advanced and may be deferred.

| # | Criterion | Level | ISO/IEC 25010 Characteristic(s) | Notes |
| --- | --- | --- | --- | --- |
| 1 | Follows INVEST criteria (Independent, Negotiable, Valuable, Estimable, Small, Testable) | Mandatory | Functional Suitability, Maintainability | |
| 2 | Written in "As a / I want / So that" form | Mandatory | Usability | |
| 3 | Clear, testable acceptance criteria are included | Mandatory | Functional Suitability, Reliability | |
| 4 | Traceable to a use case or epic | Mandatory | Maintainability | |
| 5 | Story is sized to fit within a single iteration | Optional | Maintainability | |
| 6 | Story statement avoids technical implementation detail | Optional | Usability, Maintainability | |
| 7 | Role named in the story matches an actor defined in the Use Case Diagram | Mandatory | Compatibility | |

## Common Defects

- Compound stories bundling multiple unrelated goals ("As a... I want X and Y and Z")
- Missing, vague, or unverifiable acceptance criteria
- Role that does not match any actor defined elsewhere
- Stories phrased as implementation tasks rather than user-valued outcomes

## Traceability Rule

- Backward: Use Case Diagram checklist ([QC-UCD-001]), Use Case checklist ([QC-UC-001]) (Brief/Casual), Business Case checklist ([QC-BC-001])
- Forward: Iteration/Sprint backlog, Fully Dressed Use Cases ([QC-UC-001]), acceptance tests — the backlog/tests are outside the QC checklist chain

---

[QC-UCD-001]: ./qc-use-case-diagram.md
[QC-UC-001]: ./qc-use-case.md
[QC-BC-001]: ./qc-business-case.md
