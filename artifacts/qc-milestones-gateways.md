# Quality Criteria: Milestones / Gateways

## Metadata
| Key | Value |
| --- | --- |
| ID | QC-MIL-001 |
| CrossReference | [QC-BC-001], [QC-KPI-001] |
| DomainLanguages | IT Professional English |

## Version History
| Date | Status | Author | Reviewer | Change | Commit |
| --- | --- | --- | --- | --- | --- |
| 2026-10-01 | Accepted | Jens Tirsvad Nielsen | S07 | First public release (1.0.0) | — |

---

## Purpose

Milestones and gateways define the checkpoints at which project progress and quality are formally evaluated, so their quality determines whether governance decisions to proceed, rework, or stop are made on objective, well-scoped grounds.

## Quality Criteria Checklist

Level: **Mandatory** criteria are the baseline every instance must meet; **Optional** criteria are advanced and may be deferred.

| # | Criterion | Level | ISO/IEC 25010 Characteristic(s) | Notes |
| --- | --- | --- | --- | --- |
| 1 | A concrete deliverable is defined for every gate | Mandatory | Functional Suitability | Reject gates with no tangible output to evaluate. |
| 2 | Explicit Go/No-Go criteria are stated for each gate | Mandatory | Functional Suitability, Reliability | Criteria must be objectively checkable, not subjective. |
| 3 | Dependencies on other milestones are explicitly mapped | Optional | Functional Suitability, Maintainability | Prevents scheduling conflicts and hidden ordering assumptions. |
| 4 | Each milestone is traceable to a Business Case objective or KPI | Mandatory | Functional Suitability | Cross-check against Business Case Objectives/Success Criteria. |
| 5 | Milestone owner and approving reviewer are identified | Mandatory | Usability, Maintainability | Ensures accountability for the Go/No-Go decision. |
| 6 | Milestone has a defined target date consistent with project constraints | Mandatory | Reliability | Cross-check against Business Case Constraints (e.g. 12-week duration). |

## Common Defects

- Gate with no defined deliverable, only a date
- Go/No-Go criteria left implicit or subjective
- Milestone dependencies omitted, causing sequencing conflicts
- Milestone with no link to any Business Case objective or KPI
- No named owner or reviewer accountable for the gate decision

## Traceability Rule

- Backward: Must link to the Business Case checklist ([QC-BC-001]) scope/objectives and the KPI Definitions checklist ([QC-KPI-001]) for relevant KPIs that justify the milestone.
- Forward: Feeds into governance sign-off gates and SQA review scheduling that enforce the Go/No-Go decision — outside the QC checklist chain.

---

[QC-BC-001]: ./qc-business-case.md
[QC-KPI-001]: ./qc-kpi.md
