# Quality Criteria: Stakeholder Analysis

## Metadata
| Key | Value |
| --- | --- |
| ID | QC-SA-001 |
| CrossReference | [QC-BC-001] |
| DomainLanguages | IT Professional English |

## Version History
| Date | Status | Author | Reviewer | Change | Commit |
| --- | --- | --- | --- | --- | --- |
| 2026-10-01 | Accepted | Jens Tirsvad Nielsen | S07 | First public release (1.0.0) | — |

---

## Purpose

A Stakeholder Analysis is the foundational artifact that identifies who has influence over, or interest in, the project. Its quality determines whether later artifacts (Business Case, Business Model Canvas, requirements, RACI assignments) engage the right people with the right level of attention.

## Quality Criteria Checklist

Level: **Mandatory** criteria are the baseline every instance must meet; **Optional** criteria are advanced and may be deferred.

| # | Criterion | Level | ISO/IEC 25010 Characteristic(s) | Notes |
| --- | --- | --- | --- | --- |
| 1 | Power/Interest grid is filled for every stakeholder, with no gaps or unclassified entries | Mandatory | Functional Suitability | |
| 2 | Each stakeholder is assigned a unique, stable ID (e.g. S01-S11 style) reusable for RACI assignments in other artifacts | Mandatory | Maintainability | |
| 3 | Roles and organizational context are defined with explicit Power and Interest levels, not just narrative description | Mandatory | Functional Suitability | |
| 4 | Communication needs (channel, frequency, deliverable type) are mapped to project phases or milestones | Optional | Usability | |
| 5 | Conflicting stakeholder interests are identified with documented mitigation or resolution strategies | Mandatory | Reliability | |
| 6 | Stakeholder concerns are explicitly traced to Business Case objectives | Mandatory | Maintainability | |
| 7 | Primary concerns are expressed in both business language and a recognized quality-attribute mapping (e.g. FURPS+) | Optional | Functional Suitability | |
| 8 | Document is understandable and navigable by non-technical stakeholders reviewing their own entry | Optional | Usability | |

## Common Defects

- Stakeholders described only qualitatively, without a stable ID that other artifacts can reuse for RACI
- Power/Interest quadrant missing, or inconsistent with the surrounding rationale narrative
- Communication plan omitted, or not tied to any project phase/milestone
- Conflicts of interest glossed over or left undocumented
- No traceability linkage from stakeholder concerns back to Business Case objectives

## Traceability Rule

- Backward: None — Stakeholder Analysis is foundational and has no prerequisite artifact.
- Forward: Feeds into the Business Case checklist ([QC-BC-001]) stakeholder cross-references, and transitively into the Business Model Canvas ([QC-BMC-001]), KPI Definitions ([QC-KPI-001]), and RACI assignments in downstream artifacts.

---

[QC-BC-001]: ./qc-business-case.md
[QC-BMC-001]: ./qc-business-model-canvas.md
[QC-KPI-001]: ./qc-kpi.md
