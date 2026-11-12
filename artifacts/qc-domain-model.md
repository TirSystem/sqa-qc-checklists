# Quality Criteria: Domain Model

## Metadata
| Key | Value |
| --- | --- |
| ID | QC-DM-001 |
| CrossReference | [QC-UC-001], [QC-UCD-001], [QC-SSD-001] |

## Version History
| Date | Status | Author | Reviewer | Change | Commit |
| --- | --- | --- | --- | --- | --- |
| 2026-11-08 | Deprecated | Jens Tirsvad Nielsen | S07 | Removed the obsolete DomainLanguages metadata row; the register is per artifact type in the project registry (issue 6); accepted by the author in chat as stand-in for S07, not independent | [ce06e14] |
| 2026-11-12 | Accepted | Jens Tirsvad Nielsen | S07 | Added criteria 9 to 11 (no technical solution names; no empty concept; a use case model matches and is added to the project Domain Model) and three common defects; accepted by the author in chat as stand-in for S07, not independent | [5596e86] |

---

## Purpose

The Domain Model captures the essential business vocabulary and concept relationships of the problem space, independent of any implementation. Its quality determines whether downstream design artifacts (SSDs, operation contracts, DCDs) are built on an accurate, shared understanding of the business.

## Quality Criteria Checklist

Level: **Mandatory** criteria are the baseline every instance must meet; **Optional** criteria are advanced and may be deferred.

| # | Criterion | Level | ISO/IEC 25010 Characteristic(s) | Notes |
| --- | --- | --- | --- | --- |
| 1 | Uses ubiquitous/business language throughout; no technical or implementation jargon (e.g. no "table", "class", "pointer") | Mandatory | Maintainability, Interaction Capability | Domain concepts must be recognizable to business stakeholders |
| 2 | Multiplicities on associations are correct and complete (e.g. `1..*`, `0..1`) | Mandatory | Functional Suitability | Missing or vague multiplicities are a common defect |
| 3 | No operation/method signatures shown — attributes and associations only | Mandatory | Maintainability | Domain Model is conceptual, not a design class diagram |
| 4 | Associations are named with an unambiguous reading direction | Optional | Interaction Capability, Maintainability | e.g. "Order — placed by — Customer" |
| 5 | Generalization/specialization used correctly, reflecting true "is-a" relationships, not misused for code reuse | Optional | Functional Suitability, Maintainability | Larman warns against inheritance abuse for implementation convenience |
| 6 | Every concept traces to a noun phrase found in the use cases or glossary | Mandatory | Functional Suitability | Prevents invented concepts with no requirement source |
| 7 | Attributes are simple domain data (no foreign-key-like references or object pointers modeled as attributes) | Mandatory | Maintainability | Relationships should be modeled as associations, not attribute references |
| 8 | The Purpose names the concerns (`CN-NNN`) the Domain Model answers and the stakeholders it serves, so its viewpoint is stated | Optional | Interaction Capability, Maintainability | Viewpoint of ISO/IEC/IEEE 42010; see `process/architecture-description.md` of the framework |
| 9 | No technical solution names: only conceptual classes of the Product Owner's world, never a file, an environment variable, a setting source, a database, a table, an API, a service, a cache or any other mechanism | Mandatory | Maintainability, Functional Suitability | Technical solutions first appear in the SD, DCD and ERD; a concept that exists only because of a technical choice does not belong |
| 10 | No empty concept: every concept has at least one attribute and at least one association | Mandatory | Maintainability, Functional Suitability | A concept with nothing to say is an attribute, an association name or not a concept |
| 11 | A Domain Model written for one use case reuses the concepts, attributes, associations and names of the project Domain Model, and its additions and changes are added to the project Domain Model | Mandatory | Maintainability, Functional Suitability | Not applicable to the project Domain Model itself; two models for the same thing, or a use case model never merged, make the project model drift |

## Common Defects

- Modeling database tables or classes instead of business concepts
- A concept named after a technical solution ("config from file", "environment variable", "cache")
- A concept with no attributes or no associations, drawn as an empty box
- A use case model that draws a concept the project Domain Model already has under another name, or whose additions never reach the project Domain Model
- Including operations/methods on domain concepts
- Missing or incorrect multiplicities on key associations
- Unnamed or ambiguously-directioned associations
- Overuse of generalization hierarchies for convenience rather than genuine taxonomy
- A Domain Model whose Purpose does not say which concerns it answers

## Traceability Rule

- Backward: Must trace to concepts and terminology introduced in the Use Case checklist ([QC-UC-001]) (and Use Case Diagram checklist [QC-UCD-001]/glossary)
- Forward: Feeds into the System Sequence Diagram checklist ([QC-SSD-001]), which references domain concepts as message parameters and return types

---

[QC-UC-001]: ./qc-use-case.md
[QC-UCD-001]: ./qc-use-case-diagram.md
[QC-SSD-001]: ./qc-ssd.md
[404f664]: https://git.tirsystem.com/TirSystem/SQA-QC-Checklists/commit/404f66454eb129463cf0982b425ad16707bd66a9
[f9409f9]: https://git.tirsystem.com/TirSystem/SQA-QC-Checklists/commit/f9409f9260b24321b8f9a11b8ce3c40698fae9ac
[ce06e14]: https://git.tirsystem.com/TirSystem/SQA-QC-Checklists/commit/ce06e14cbe173c007b78858bd8a5474d1668e9ab
[5596e86]: https://git.tirsystem.com/TirSystem/SQA-QC-Checklists/commit/5596e86f5ae01b9640b90b1e40764aba48e171d0
