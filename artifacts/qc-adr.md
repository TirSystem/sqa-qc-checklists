# Quality Criteria: Architecture Decision Record

## Metadata
| Key | Value |
| --- | --- |
| ID | QC-ADR-001 |
| CrossReference | [QC-BC-001], [QC-DCD-001], [QC-ERD-001], [QC-PY-001], [QC-CL-001], [QC-CPP-001], [QC-CS-001], [QC-YML-001] |
| DomainLanguages | IT Professional English |

## Version History
| Date | Status | Author | Reviewer | Change | Commit |
| --- | --- | --- | --- | --- | --- |
| 2026-10-11 | Proposed | Jens Tirsvad Nielsen | S07 | Cited QC-YML-001 as a forward checklist (RC-077) | [140bc3c] |
| 2026-10-22 | Proposed | Jens Tirsvad Nielsen | S07 | Renamed the ISO/IEC 25010 tags to the 2023 names: Usability to Interaction Capability, Portability to Flexibility (RC-083) | pending |

---

## Purpose

An Architecture Decision Record captures one significant decision, the options weighed and its consequences, so that the reasoning survives the people who made it. It supports the decision to accept, reject or supersede a design or architecture choice.

## Quality Criteria Checklist

Level: **Mandatory** criteria are the baseline every instance must meet; **Optional** criteria are advanced and may be deferred.

| # | Criterion | Level | ISO/IEC 25010 Characteristic(s) | Notes |
| --- | --- | --- | --- | --- |
| 1 | The ID (`ADR-NNNN`, 4-digit) matches the filename number and is unique and sequential | Mandatory | Maintainability | |
| 2 | Context states the problem, the forces (cost, risk, constraints) and the options evaluated | Mandatory | Functional Suitability, Maintainability | |
| 3 | At least two options were considered, or the absence of alternatives is justified | Mandatory | Functional Suitability | |
| 4 | Decision is stated in one or two unhedged sentences and matches one of the evaluated options | Mandatory | Functional Suitability, Interaction Capability | |
| 5 | Consequences list both Positive and Negative outcomes | Mandatory | Maintainability, Reliability | |
| 6 | Quality-attribute impacts (performance, security, portability, etc.) are named where the decision affects them | Optional | Performance Efficiency, Security, Flexibility, Compatibility | |
| 7 | Affected Artifacts are listed as links, and each is also in CrossReference | Mandatory | Maintainability | |
| 8 | Status changes are recorded as new Version History rows with a Change summary and Commit link; retained rows are never rewritten | Mandatory | Reliability, Maintainability | |
| 9 | A superseded or deprecated ADR names its successor, and the successor links back | Optional | Maintainability | |
| 10 | Written in business or technical language of the domain, with no unexplained abbreviations | Optional | Interaction Capability | |
| 11 | Status is one of `Proposed`, `Accepted`, `Rejected`, `Deprecated` or `Superseded by ADR-NNNN`, and every Version History row uses only these | Mandatory | Reliability, Maintainability | `Approved` is not an ADR status |

## Common Defects

- Decision described only as the chosen technology, with no problem or rationale
- Only one option listed, presented as if it were a comparison
- Consequences that list only benefits
- Decision text hedged ("we might", "probably") or split across several unrelated decisions
- Status outside the allowed set (for example `Approved`, `Final`, `Draft`)
- Rewritten history: the status or decision changed in place instead of a new row or a superseding ADR
- Affected Artifacts missing, so the impact of the decision cannot be traced

## Traceability Rule

- Backward: Business Case checklist ([QC-BC-001]) for the objectives and constraints that force the decision
- Forward: Design Class Diagram checklist ([QC-DCD-001]) and Entity Relationship Diagram checklist ([QC-ERD-001]) for the design and data structures the decision shapes, and the language code checklists ([QC-PY-001], [QC-CL-001], [QC-CPP-001], [QC-CS-001]) for the implementation it constrains; the YAML file checklist ([QC-YML-001]) for the configuration files a decision constrains

---

[QC-BC-001]: ./qc-business-case.md
[QC-DCD-001]: ./qc-dcd.md
[QC-ERD-001]: ./qc-erd.md
[QC-PY-001]: ../code/qc-programming-python.md
[QC-CL-001]: ../code/qc-programming-c.md
[QC-CPP-001]: ../code/qc-programming-cpp.md
[QC-CS-001]: ../code/qc-programming-csharp.md
[QC-YML-001]: ../code/qc-yaml.md
[140bc3c]: https://git.tirsystem.com/TirSystem/SQA-QC-Checklists/commit/140bc3c12df74238e332ff149243ef3e6255e208
