# Quality Criteria: KPI Definitions

## Metadata
| Key | Value |
| --- | --- |
| ID | QC-KPI-001 |
| CrossReference | [QC-BC-001] |
| DomainLanguages | IT Professional English |

## Version History
| Date | Status | Author | Reviewer | Change | Commit |
| --- | --- | --- | --- | --- | --- |
| 2026-10-01 | Deprecated | Jens Tirsvad Nielsen | S07 | First public release (1.0.0) | — |
| 2026-10-22 | Accepted | Jens Tirsvad Nielsen | S07 | Renamed the ISO/IEC 25010 tags to the 2023 names: Usability to Interaction Capability, Portability to Flexibility (RC-083); accepted by the author as stand-in for S07 on the user's instruction in chat on 2026-10-26, through the pull request that merges this row; not independent | [404f664] |

---

## Purpose

KPI definitions translate business objectives into measurable indicators, so their quality determines whether progress toward the Business Case's success criteria can be objectively tracked and acted upon.

## Quality Criteria Checklist

Level: **Mandatory** criteria are the baseline every instance must meet; **Optional** criteria are advanced and may be deferred.

| # | Criterion | Level | ISO/IEC 25010 Characteristic(s) | Notes |
| --- | --- | --- | --- | --- |
| 1 | KPI is defined in SMART format (Specific, Measurable, Achievable, Relevant, Time-bound) | Mandatory | Functional Suitability | Reject vague or non-quantifiable KPI statements. |
| 2 | Baseline and target values are both defined | Mandatory | Functional Suitability, Reliability | Without a baseline, progress cannot be measured. |
| 3 | KPI is aligned with a stated Business Case success criterion | Mandatory | Functional Suitability | Cross-check against Business Case Success Criteria table. |
| 4 | An owner/stakeholder is assigned for tracking the KPI | Mandatory | Interaction Capability, Maintainability | Ensures accountability for ongoing measurement. |
| 5 | Measurement frequency and method are explicitly stated | Mandatory | Reliability, Maintainability | E.g. "measured monthly via review-cycle audit logs." |
| 6 | Data source for the measurement is identified and accessible | Optional | Reliability, Flexibility | Prevents KPIs that cannot actually be measured in practice. |
| 7 | KPI thresholds distinguish acceptable, at-risk, and failing performance | Optional | Functional Suitability, Interaction Capability | Supports clear reporting and decision-making. |

## Common Defects

- KPI stated as a goal or activity rather than a measurable metric
- Missing baseline, making the target value meaningless
- No named owner responsible for tracking or reporting
- KPI not traceable to any Business Case success criterion
- Measurement method or frequency left unspecified

## Traceability Rule

- Backward: Must link to the Business Case checklist ([QC-BC-001]) Success Criteria that the KPI operationalizes.
- Forward: Feeds into SQA review metrics and governance reporting used to evaluate the framework's ongoing performance — outside the QC checklist chain.

---

[QC-BC-001]: ./qc-business-case.md
[404f664]: https://git.tirsystem.com/TirSystem/SQA-QC-Checklists/commit/404f66454eb129463cf0982b425ad16707bd66a9
