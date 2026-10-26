# Quality Criteria: BPMN Business Process Model

## Metadata
| Key | Value |
| --- | --- |
| ID | QC-BPMN-001 |
| CrossReference | [QC-BC-001], [QC-SA-001], [QC-UCD-001] |
| DomainLanguages | IT Professional English |

## Version History
| Date | Status | Author | Reviewer | Change | Commit |
| --- | --- | --- | --- | --- | --- |
| 2026-10-22 | Deprecated | Jens Tirsvad Nielsen | S07 | Renamed the ISO/IEC 25010 tags to the 2023 names: Usability to Interaction Capability, Portability to Flexibility (RC-083) | [404f664] |
| 2026-10-26 | Accepted | Jens Tirsvad Nielsen | S07 | Added criterion 8 (the Purpose names the concerns the view answers); accepted by the author as stand-in for S07 on the user's instruction in chat on 2026-10-26, through the pull request that merges this row; not independent | [f9409f9] |

---

## Purpose

BPMN process models describe how business goals are actually carried out across participants, so their quality directly determines whether downstream use cases and requirements are grounded in a correct, unambiguous understanding of the process.

## Quality Criteria Checklist

Level: **Mandatory** criteria are the baseline every instance must meet; **Optional** criteria are advanced and may be deferred.

| # | Criterion | Level | ISO/IEC 25010 Characteristic(s) | Notes |
| --- | --- | --- | --- | --- |
| 1 | Diagram uses valid BPMN 2.0 syntax (events, gateways, activities, sequence/message flows) | Mandatory | Functional Suitability, Compatibility | Verify element types and notation conform to the BPMN 2.0 specification. |
| 2 | Swimlanes/pools are clearly defined for each participant | Mandatory | Interaction Capability, Functional Suitability | Every actor/role involved in the process has its own lane or pool. |
| 3 | No dead-end flows; every path reaches a defined end event | Mandatory | Functional Suitability, Reliability | Trace each branch from start to end event. |
| 4 | Gateway split/join logic is consistent (matching AND/XOR pairs) | Mandatory | Functional Suitability, Reliability | A gateway that splits a flow must be closed by a matching gateway type. |
| 5 | Process maps to a stated business goal from the Business Case | Mandatory | Functional Suitability | Cross-check against Business Case objectives/scope. |
| 6 | Message flows correctly cross pool boundaries and internal sequence flows do not | Mandatory | Functional Suitability, Compatibility | Common notation error to check explicitly. |
| 7 | Diagram is readable without excessive flow crossings or ambiguous labeling | Optional | Interaction Capability, Maintainability | Supports faster, less error-prone reviews and maintenance. |
| 8 | The Purpose names the concerns (`CN-NNN`) the BPMN process model answers and the stakeholders it serves, so its viewpoint is stated | Optional | Interaction Capability, Maintainability | Viewpoint of ISO/IEC/IEEE 42010; see `process/architecture-description.md` of the framework |

## Common Defects

- Sequence flows drawn across pool boundaries instead of message flows
- Unlabeled or ambiguously labeled gateways, making split logic unclear
- Missing end events, leaving process paths open-ended
- Activities assigned to no lane, or to the wrong participant
- Process diagram with no traceable link to a Business Case objective
- A process model whose Purpose does not say which concerns it answers

## Traceability Rule

- Backward: Must link to the Business Case checklist ([QC-BC-001]) for objectives/scope and the Stakeholder Analysis checklist ([QC-SA-001]) for relevant needs that justify the process.
- Forward: Feeds into the Use Case Diagram checklist ([QC-UCD-001]) that formalizes system-supported steps of the process.

---

[QC-BC-001]: ./qc-business-case.md
[QC-SA-001]: ./qc-stakeholder-analysis.md
[QC-UCD-001]: ./qc-use-case-diagram.md
[404f664]: https://git.tirsystem.com/TirSystem/SQA-QC-Checklists/commit/404f66454eb129463cf0982b425ad16707bd66a9
[f9409f9]: https://git.tirsystem.com/TirSystem/SQA-QC-Checklists/commit/f9409f9260b24321b8f9a11b8ce3c40698fae9ac
