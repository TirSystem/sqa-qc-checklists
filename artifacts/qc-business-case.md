# Quality Criteria: Business Case

## Metadata
| Key | Value |
| --- | --- |
| ID | QC-BC-001 |
| CrossReference | [QC-SA-001], [QC-BMC-001], [QC-BPMN-001], [QC-KPI-001], [QC-UCD-001] |
| DomainLanguages | IT Professional English |

## Version History
| Date | Status | Author | Reviewer | Change | Commit |
| --- | --- | --- | --- | --- | --- |
| 2026-10-01 | Accepted | Jens Tirsvad Nielsen | S07 | First public release (1.0.0) | — |

---

## Purpose

A Business Case justifies why a project should proceed by articulating value, cost, risk, and scope. Its quality determines whether decision-makers can approve or reject the initiative on a sound, verifiable basis rather than assumptions.

## Quality Criteria Checklist

Level: **Mandatory** criteria are the baseline every instance must meet; **Optional** criteria are advanced and may be deferred.

| # | Criterion | Level | ISO/IEC 25010 Characteristic(s) | Notes |
| --- | --- | --- | --- | --- |
| 1 | ROI/Cost-Benefit analysis is quantitative, or where qualitative, is explicitly justified | Mandatory | Functional Suitability | |
| 2 | Risks are identified with documented impact and mitigation | Mandatory | Reliability | |
| 3 | Success criteria are measurable, stating explicit targets rather than vague aspirations | Mandatory | Functional Suitability | |
| 4 | Scope explicitly separates In Scope vs Out of Scope | Mandatory | Functional Suitability | |
| 5 | Stakeholders are cross-referenced to Stakeholder Analysis IDs rather than re-described inline | Mandatory | Maintainability | |
| 6 | Methodology and quality-standard foundation are stated explicitly (e.g. ISO/IEC 25010, Larman) | Optional | Compatibility | |
| 7 | Assumptions and constraints are explicit and clearly distinguished from one another | Mandatory | Functional Suitability | |
| 8 | Document supports executive decision-making with a clear, unambiguous recommendation | Mandatory | Usability | |

## Common Defects

- Reinventing stakeholder roles instead of cross-referencing Stakeholder Analysis stakeholder IDs
- Missing Metadata/Version History tables
- No CrossReference to related artifacts (e.g. Stakeholder Analysis)
- Success criteria stated as aspirations without measurable targets
- Risks listed without corresponding mitigations

## Traceability Rule

- Backward: Links to the Stakeholder Analysis checklist ([QC-SA-001]) for stakeholder interests and RACI-relevant IDs.
- Forward: Feeds into the KPI Definitions ([QC-KPI-001]), BPMN Process Model ([QC-BPMN-001]), Use Case Diagram ([QC-UCD-001]), and Business Model Canvas ([QC-BMC-001]) checklists.

---

[QC-SA-001]: ./qc-stakeholder-analysis.md
[QC-BMC-001]: ./qc-business-model-canvas.md
[QC-BPMN-001]: ./qc-bpmn.md
[QC-KPI-001]: ./qc-kpi.md
[QC-UCD-001]: ./qc-use-case-diagram.md
