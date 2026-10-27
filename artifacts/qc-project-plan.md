# Quality Criteria: Project Plan

## Metadata
| Key | Value |
| --- | --- |
| ID | QC-PP-001 |
| CrossReference | [QC-BC-001], [QC-SA-001], [QC-MIL-001], [QC-GOV-001] |
| DomainLanguages | IT Professional English |

## Version History
| Date | Status | Author | Reviewer | Change | Commit |
| --- | --- | --- | --- | --- | --- |
| 2026-10-27 | Proposed | Jens Tirsvad Nielsen | S07 | First draft of the Project Plan checklist | pending |

---

## Purpose

The Project Plan schedules the project's milestones and gateways inside the Business Case's constraints, so its quality determines whether the work is delivered in a feasible order, whether every in-scope item has a home, and whether a No-Go is absorbed or breaks the schedule.

## Quality Criteria Checklist

Level: **Mandatory** criteria are the baseline every instance must meet; **Optional** criteria are advanced and may be deferred.

| # | Criterion | Level | ISO/IEC 25010 Characteristic(s) | Notes |
| --- | --- | --- | --- | --- |
| 1 | The plan states its start date, end date and the constraint it must fit | Mandatory | Reliability, Functional Suitability | Cross-check against Business Case Constraints (e.g. the 12-week duration). |
| 2 | Every milestone or gateway is listed once with its document, decision date and owner | Mandatory | Functional Suitability, Maintainability | Each row links to its `MIL-*` document; no gateway exists only in the plan or only in a `MIL-*`. |
| 3 | Every decision date lies inside the plan's window and is consistent with the dates in the linked `MIL-*` document | Mandatory | Reliability | Reject a date that differs between the plan and its milestone, or falls after the end date. |
| 4 | Every in-scope item of the Business Case is delivered at a named gateway (scope coverage) | Mandatory | Functional Suitability | Reject an in-scope item with no gateway, and a gateway with no Business Case item or recorded change. |
| 5 | Dependencies between gateways are stated, acyclic and consistent with the schedule order | Mandatory | Functional Suitability, Reliability | A gateway may not be decided before a predecessor it depends on. |
| 6 | The plan states what happens to later gateways and to the end date when a gateway is No-Go | Mandatory | Reliability | Name who decides a move of the end date. |
| 7 | Owners, reviewers and escalation roles use Stakeholder Analysis IDs and match the governance RACI | Mandatory | Interaction Capability, Maintainability | No invented role names; cross-check against the governance checklist. |
| 8 | Planning assumptions are listed with their source, and a changed baseline is recorded with its reason | Mandatory | Reliability, Maintainability | For example a re-baselined date, a dropped cadence or an agreed minimum quality baseline. |
| 9 | Plan risks are listed with impact and a mitigation, and trace to Business Case risks where they come from there | Mandatory | Reliability, Security | A risk with no mitigation is an open issue, not a risk. |
| 10 | Open issues are listed, and none contradicts a statement elsewhere in the plan | Mandatory | Maintainability | Remove an open issue once closed; do not leave stale entries. |
| 11 | Each gateway's main deliverable is stated and matches the deliverable of its `MIL-*` document | Mandatory | Functional Suitability | Reject a deliverable that only the plan names. |
| 12 | Gateways that deliver user stories name them, and those that do not say why | Optional | Functional Suitability, Maintainability | For example "none (technical tasks)". |
| 13 | The schedule view (table, Gantt) and the dependency view agree with each other | Optional | Maintainability, Interaction Capability | Check bar dates against the table, and the chain against the dependency list. |
| 14 | Each gateway is linked to its issue-tracker milestone, or marked as not yet synced | Optional | Maintainability | Keeps plan and tracker in step after a sync. |
| 15 | The plan is a singleton: one Project Plan per project, changes recorded in Version History | Mandatory | Maintainability | Version History keeps the two latest rows, with the commit of each change. |

## Common Defects

- Gateway dates in the plan that differ from the dates in the `MIL-*` documents
- Business Case scope items with no gateway, or gateways added after the baseline with no scope entry
- Dependency chain that disagrees with the schedule order
- A No-Go with no rule for moving later gateways or the end date
- Assumptions that were changed (re-baselined dates) without a recorded reason
- Open issues that were closed long ago, or contradict the rest of the plan
- Role names instead of Stakeholder Analysis IDs
- Gantt chart out of step with the schedule table

## Traceability Rule

- Backward: Must link to the Business Case checklist ([QC-BC-001]) for scope, constraints and risks; to the Stakeholder Analysis checklist ([QC-SA-001]) for owners and reviewers; to the Governance checklist ([QC-GOV-001]) for the Go/No-Go roles.
- Forward: Schedules the Milestones / Gateways ([QC-MIL-001]), whose decision dates and deliverables it must match.

---

[QC-BC-001]: ./qc-business-case.md
[QC-SA-001]: ./qc-stakeholder-analysis.md
[QC-MIL-001]: ./qc-milestones-gateways.md
[QC-GOV-001]: ./qc-governance.md
