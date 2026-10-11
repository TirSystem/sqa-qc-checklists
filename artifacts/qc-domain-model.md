# Quality Criteria: Domain Model

## Metadata
| Key | Value |
| --- | --- |
| ID | QC-DM-001 |
| CrossReference | [QC-UC-001], [QC-UCD-001], [QC-SSD-001] |
| DomainLanguages | IT Professional English |

## Version History
| Date | Status | Author | Reviewer | Change | Commit |
| --- | --- | --- | --- | --- | --- |
| 2026-10-01 | Accepted | Jens Tirsvad Nielsen | S07 | First public release (1.0.0) | — |

---

## Purpose

The Domain Model captures the essential business vocabulary and concept relationships of the problem space, independent of any implementation. Its quality determines whether downstream design artifacts (SSDs, operation contracts, DCDs) are built on an accurate, shared understanding of the business.

## Quality Criteria Checklist

Level: **Mandatory** criteria are the baseline every instance must meet; **Optional** criteria are advanced and may be deferred.

| # | Criterion | Level | ISO/IEC 25010 Characteristic(s) | Notes |
| --- | --- | --- | --- | --- |
| 1 | Uses ubiquitous/business language throughout; no technical or implementation jargon (e.g. no "table", "class", "pointer") | Mandatory | Maintainability, Usability | Domain concepts must be recognizable to business stakeholders |
| 2 | Multiplicities on associations are correct and complete (e.g. `1..*`, `0..1`) | Mandatory | Functional Suitability | Missing or vague multiplicities are a common defect |
| 3 | No operation/method signatures shown — attributes and associations only | Mandatory | Maintainability | Domain Model is conceptual, not a design class diagram |
| 4 | Associations are named with an unambiguous reading direction | Optional | Usability, Maintainability | e.g. "Order — placed by — Customer" |
| 5 | Generalization/specialization used correctly, reflecting true "is-a" relationships, not misused for code reuse | Optional | Functional Suitability, Maintainability | Larman warns against inheritance abuse for implementation convenience |
| 6 | Every concept traces to a noun phrase found in the use cases or glossary | Mandatory | Functional Suitability | Prevents invented concepts with no requirement source |
| 7 | Attributes are simple domain data (no foreign-key-like references or object pointers modeled as attributes) | Mandatory | Maintainability | Relationships should be modeled as associations, not attribute references |

## Common Defects

- Modeling database tables or classes instead of business concepts
- Including operations/methods on domain concepts
- Missing or incorrect multiplicities on key associations
- Unnamed or ambiguously-directioned associations
- Overuse of generalization hierarchies for convenience rather than genuine taxonomy

## Traceability Rule

- Backward: Must trace to concepts and terminology introduced in the Use Case checklist ([QC-UC-001]) (and Use Case Diagram checklist [QC-UCD-001]/glossary)
- Forward: Feeds into the System Sequence Diagram checklist ([QC-SSD-001]), which references domain concepts as message parameters and return types

---

[QC-UC-001]: ./qc-use-case.md
[QC-UCD-001]: ./qc-use-case-diagram.md
[QC-SSD-001]: ./qc-ssd.md
