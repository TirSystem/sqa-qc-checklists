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
| 2026-10-15 | Accepted | Jens Tirsvad Nielsen | S07 | Added criteria 8 and 9 (split into use cases; MoSCoW priority with a reason); accepted by the author as stand-in for S07, through the pull request that merges this row; not independent of the author | [b818ee7] |
| 2026-10-22 | Proposed | Jens Tirsvad Nielsen | S07 | Renamed the ISO/IEC 25010 tags to the 2023 names: Usability to Interaction Capability, Portability to Flexibility (RC-083) | [404f664] |

---

## Purpose

User stories capture user-valued increments of functionality in a lightweight, negotiable format that drives backlog prioritization, estimation, and iterative delivery planning.

## Quality Criteria Checklist

Level: **Mandatory** criteria are the baseline every instance must meet; **Optional** criteria are advanced and may be deferred.

| # | Criterion | Level | ISO/IEC 25010 Characteristic(s) | Notes |
| --- | --- | --- | --- | --- |
| 1 | Follows INVEST criteria (Independent, Negotiable, Valuable, Estimable, Small, Testable) | Mandatory | Functional Suitability, Maintainability | |
| 2 | Written in "As a / I want / So that" form | Mandatory | Interaction Capability | |
| 3 | Clear, testable acceptance criteria are included | Mandatory | Functional Suitability, Reliability | |
| 4 | Traceable to a use case or epic | Mandatory | Maintainability | |
| 5 | Story is sized to fit within a single iteration | Optional | Maintainability | |
| 6 | Story statement avoids technical implementation detail | Optional | Interaction Capability, Maintainability | |
| 7 | Role named in the story matches an actor defined in the Use Case Diagram | Mandatory | Compatibility | |
| 8 | A story with more than one actor goal is split into use cases, one per actor goal, and each use case names the story it comes from | Optional | Maintainability, Functional Suitability | Candidate stories are proposed, then accepted, merged or dropped by the user |
| 9 | The story has a priority (MoSCoW: Must, Should, Could, Won't now) with the reason beside it | Optional | Maintainability | The reason cites value, risk or a dependency |

## Common Defects

- Compound stories bundling multiple unrelated goals ("As a... I want X and Y and Z")
- Missing, vague, or unverifiable acceptance criteria
- Role that does not match any actor defined elsewhere
- Stories phrased as implementation tasks rather than user-valued outcomes
- A priority without a reason, or every story marked Must

## Traceability Rule

- Backward: Use Case Diagram checklist ([QC-UCD-001]), Use Case checklist ([QC-UC-001]) (Brief/Casual), Business Case checklist ([QC-BC-001])
- Forward: Iteration/Sprint backlog, Fully Dressed Use Cases ([QC-UC-001]), acceptance tests — the backlog/tests are outside the QC checklist chain

---

[QC-UCD-001]: ./qc-use-case-diagram.md
[QC-UC-001]: ./qc-use-case.md
[QC-BC-001]: ./qc-business-case.md
[b818ee7]: https://git.tirsystem.com/TirSystem/SQA-QC-Checklists/commit/b818ee7f007b69282461bc616a48dd5871cedad6
[404f664]: https://git.tirsystem.com/TirSystem/SQA-QC-Checklists/commit/404f66454eb129463cf0982b425ad16707bd66a9
