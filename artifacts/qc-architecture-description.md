# Quality Criteria: Architecture Description

## Metadata
| Key | Value |
| --- | --- |
| ID | QC-AD-001 |
| CrossReference | [QC-BC-001], [QC-SA-001], [QC-DM-001], [QC-DCD-001], [QC-ERD-001], [QC-ADR-001], [QC-TP-001] |
| DomainLanguages | IT Professional English |

## Version History
| Date | Status | Author | Reviewer | Change | Commit |
| --- | --- | --- | --- | --- | --- |
| 2026-10-26 | Proposed | Jens Tirsvad Nielsen | S02 | Created | [f9409f9] |

---

## Purpose

An Architecture Description indexes the architecture of one system in one place: the views, the viewpoint of each view, the stakeholder concerns they answer, the correspondences between views and the decisions behind them. It follows the concepts of ISO/IEC/IEEE 42010 and does not repeat what the views and the decision records already say. Its quality decides whether a stakeholder can find out which part of the design answers their concern, and whether the views stay consistent with each other.

## Quality Criteria Checklist

Level: **Mandatory** criteria are the baseline every instance must meet; **Optional** criteria are advanced and may be deferred.

| # | Criterion | Level | ISO/IEC 25010 Characteristic(s) | Notes |
| --- | --- | --- | --- | --- |
| 1 | Every architectural view of the system is listed with its type and a link to the instance; no view is described only here | Mandatory | Maintainability, Functional Suitability | The index points to the views; it does not copy them |
| 2 | Every view names its viewpoint: the stakeholders it serves and the concerns it frames | Mandatory | Interaction Capability, Maintainability | Viewpoint of ISO/IEC/IEEE 42010 |
| 3 | Every concern (`CN-NNN`) of the concern register is answered by at least one view, or is listed as a gap with an owner | Mandatory | Functional Suitability, Reliability | A concern without a view is a gap to decide, not a silent omission |
| 4 | The correspondences between views are stated, by the terms of the Domain Dictionary (for example a Domain Model concept, its Design Class Diagram class and its Entity Relationship Diagram entity) | Mandatory | Maintainability, Compatibility | A correspondence is the rule that keeps two views consistent |
| 5 | The list of open inconsistencies between views is current; each entry names the views, the review record that found it, its status and, when closed, where it was resolved | Mandatory | Reliability, Maintainability | A closed entry stays for the record |
| 6 | The architecturally significant decisions are listed with a link to their Architecture Decision Record; none is justified only in this document | Mandatory | Maintainability | Rationale lives in the ADR |
| 7 | The quality characteristics (ISO/IEC 25010:2023) that matter to the system are listed with a measurable target, and each target links to the decision that serves it and to a test or check | Optional | Performance Efficiency, Reliability, Security, Safety | Characteristics that do not matter are named and left out on purpose |
| 8 | Every link resolves: each listed view, record, decision and test exists | Mandatory | Reliability | |
| 9 | The document is in IT Professional English and uses the IT terms of the Domain Dictionary | Mandatory | Interaction Capability, Maintainability | |

## Common Defects

- A view described in the Architecture Description and nowhere else
- A viewpoint with no named stakeholder, or a stakeholder with no concern
- A concern with no view and no entry in the gaps
- Correspondences written with the Product Owner's terms in a design view
- An inconsistency found in a review that is not on the list
- A decision whose reason is only in this document
- A quality target with no decision and no test behind it

## Traceability Rule

- Backward: Business Case ([QC-BC-001]) for the goals and quality targets; Stakeholder Analysis ([QC-SA-001]) for the stakeholders and the concern register; the view checklists ([QC-DM-001], [QC-DCD-001], [QC-ERD-001]) and the Architecture Decision Record checklist ([QC-ADR-001]) for the views and decisions it indexes
- Forward: Test Plan ([QC-TP-001]) for the checks of the quality targets

---

[QC-BC-001]: ./qc-business-case.md
[QC-SA-001]: ./qc-stakeholder-analysis.md
[QC-DM-001]: ./qc-domain-model.md
[QC-DCD-001]: ./qc-dcd.md
[QC-ERD-001]: ./qc-erd.md
[QC-ADR-001]: ./qc-adr.md
[QC-TP-001]: ./qc-test-plan.md
[f9409f9]: https://git.tirsystem.com/TirSystem/SQA-QC-Checklists/commit/f9409f9260b24321b8f9a11b8ce3c40698fae9ac
