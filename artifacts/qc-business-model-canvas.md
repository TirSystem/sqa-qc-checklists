# Quality Criteria: Business Model Canvas

## Metadata
| Key | Value |
| --- | --- |
| ID | QC-BMC-001 |
| CrossReference | [QC-BC-001], [QC-SA-001], [QC-BPMN-001], [QC-KPI-001] |
| DomainLanguages | IT Professional English |

## Version History
| Date | Status | Author | Reviewer | Change | Commit |
| --- | --- | --- | --- | --- | --- |
| 2026-10-01 | Accepted | Jens Tirsvad Nielsen | S07 | First public release (1.0.0) | — |

---

## Purpose

A Business Model Canvas summarizes how the project creates, delivers, and captures value in a single view. Its quality determines whether the operating model is complete, internally consistent, and grounded in real stakeholder needs rather than assumptions.

## Quality Criteria Checklist

Level: **Mandatory** criteria are the baseline every instance must meet; **Optional** criteria are advanced and may be deferred.

| # | Criterion | Level | ISO/IEC 25010 Characteristic(s) | Notes |
| --- | --- | --- | --- | --- |
| 1 | All 9 building blocks (Key Partners, Key Activities, Key Resources, Value Propositions, Customer Relationships, Channels, Customer Segments, Cost Structure, Revenue Streams) are populated, with no empty sections | Mandatory | Functional Suitability | |
| 2 | Value proposition aligns with stakeholder needs documented in the Stakeholder Analysis | Mandatory | Usability | |
| 3 | Assumptions underlying the canvas are explicit and testable | Mandatory | Reliability | |
| 4 | Revenue streams and cost structure are internally consistent with each other | Mandatory | Functional Suitability | |
| 5 | Customer segments and channels are consistent with stakeholder groups already identified | Optional | Compatibility | |
| 6 | Canvas cross-references the Business Case objectives it operationalizes, rather than restating them | Mandatory | Maintainability | |
| 7 | Canvas is reviewable as a single, concise overview (one-page) | Optional | Usability | |

## Common Defects

- Empty or placeholder building blocks left unfilled
- Value proposition disconnected from stakeholders documented in the Stakeholder Analysis
- Untestable or unstated assumptions
- Revenue/cost figures inconsistent with the Cost-Benefit Assessment in the Business Case
- Missing cross-reference to the Business Case or Stakeholder Analysis

## Traceability Rule

- Backward: Links to the Business Case checklist ([QC-BC-001]) for objectives and cost-benefit assessment, and the Stakeholder Analysis checklist ([QC-SA-001]) for customer segments and value-proposition alignment.
- Forward: Feeds into the BPMN Process Model ([QC-BPMN-001]) and KPI Definitions ([QC-KPI-001]) checklists that operationalize the canvas.

---

[QC-BC-001]: ./qc-business-case.md
[QC-SA-001]: ./qc-stakeholder-analysis.md
[QC-BPMN-001]: ./qc-bpmn.md
[QC-KPI-001]: ./qc-kpi.md
