# Quality Criteria: Governance / ARB Workflow

## Metadata
| Key | Value |
| --- | --- |
| ID | QC-GOV-001 |
| CrossReference | [QC-BC-001], [QC-SA-001], [QC-BPMN-001] |
| DomainLanguages | IT Professional English |

## Version History
| Date | Status | Author | Reviewer | Change | Commit |
| --- | --- | --- | --- | --- | --- |
| 2026-10-01 | Accepted | Jens Tirsvad Nielsen | S07 | First public release (1.0.0) | — |

Allowed Status values: `Proposed`, `Accepted`, `Rejected`, `Deprecated`. The latest reviewed row is `Accepted`; the row before it is `Deprecated`.

---

## Purpose

A governance document defines who reviews what, who decides, and how disputes are settled. A gap in it (an unowned artifact type, a step with no actor, an unworkable independence rule) turns into unreviewed or contested artifacts. This checklist supports the decision to accept a governance or ARB workflow document as the basis for real reviews.

## Quality Criteria Checklist

Level: **Mandatory** criteria are the baseline every instance must meet; **Optional** criteria are advanced and may be deferred.

| # | Criterion | Level | ISO/IEC 25010 Characteristic(s) | Notes |
| --- | --- | --- | --- | --- |
| 1 | Purpose states what is governed and traces to the Business Case's governance and traceability objectives (a framework-level document that cannot cite project artifacts traces to the governance document it supports instead) | Mandatory | Functional Suitability, Maintainability | |
| 2 | Workflow steps are ordered, and every step names the role that performs it | Mandatory | Functional Suitability, Usability | A passive step with no actor is a defect |
| 3 | The RACI covers every in-scope artifact type, with exactly one Accountable per category | Mandatory | Functional Suitability, Reliability | Compare against the Business Case scope list |
| 4 | Roles are stakeholder IDs taken exactly from the Stakeholder Analysis; no invented role names | Mandatory | Maintainability | |
| 5 | Each verdict (Go, Go-with-conditions, No-Go) defines the resulting artifact status, using only allowed status values | Mandatory | Reliability, Maintainability | |
| 6 | Disputed or No-Go verdicts have an escalation path to a named stakeholder | Mandatory | Reliability | |
| 7 | The reviewer-independence rule can be applied: a named alternate exists when the reviewer is the author | Optional | Reliability | |
| 8 | Review cadence is stated for artifact instances and for the checklists themselves | Mandatory | Maintainability | |
| 9 | The document links the process artifacts it relies on (traceability matrix, review process, process model) | Optional | Maintainability, Usability | |
| 10 | Written without duplicated words or unexplained abbreviations | Optional | Usability | |

## Common Defects

- A workflow step written in the passive voice with no responsible role
- An in-scope artifact type that appears in no RACI category
- Two Accountable roles for one category, or none
- Status outcomes that use a value outside the allowed set, or leave a verdict's outcome undefined
- An independence rule with no one to reassign to
- Cadence stated for instances but not for the checklists

## Traceability Rule

- Backward: Business Case checklist ([QC-BC-001]) for the governance and traceability objectives; Stakeholder Analysis checklist ([QC-SA-001]) for the roles used in the RACI
- Forward: BPMN Process Model checklist ([QC-BPMN-001]) for the process model drawn from the workflow

---

[QC-BC-001]: ./qc-business-case.md
[QC-SA-001]: ./qc-stakeholder-analysis.md
[QC-BPMN-001]: ./qc-bpmn.md
