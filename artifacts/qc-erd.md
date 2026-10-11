# Quality Criteria: Entity Relationship Diagram (ERD)

## Metadata
| Key | Value |
| --- | --- |
| ID | QC-ERD-001 |
| CrossReference | [QC-DCD-001] |
| DomainLanguages | IT Professional English |

## Version History
| Date | Status | Author | Reviewer | Change | Commit |
| --- | --- | --- | --- | --- | --- |
| 2026-10-01 | Accepted | Jens Tirsvad Nielsen | S07 | First public release (1.0.0) | — |

---

## Purpose

The Entity Relationship Diagram specifies the persistent data structure that will back the system's Design Class Diagram, defining entities, keys, and relationships for storage. Its quality determines data integrity, query performance, and consistency between the design and the persisted data model.

## Quality Criteria Checklist

Level: **Mandatory** criteria are the baseline every instance must meet; **Optional** criteria are advanced and may be deferred.

| # | Criterion | Level | ISO/IEC 25010 Characteristic(s) | Notes |
| --- | --- | --- | --- | --- |
| 1 | Primary keys (PK) identified for every entity | Mandatory | Functional Suitability, Reliability | Every entity must have a unique identifier |
| 2 | Foreign keys (FK) identified for every relationship requiring referential integrity | Mandatory | Functional Suitability, Reliability | Prevents orphaned or ambiguous references |
| 3 | Schema normalized to at least 3NF unless denormalization is explicitly justified for performance | Optional | Maintainability, Performance Efficiency | Justification must be documented in Notes when denormalized |
| 4 | Relationship cardinalities specified (1:1, 1:N, N:M) for every relationship | Mandatory | Functional Suitability | Missing cardinality is a common review-blocking defect |
| 5 | Data types consistent with corresponding Operation Contract/DCD attribute types | Mandatory | Compatibility, Maintainability | Prevents silent type mismatches between design and storage |
| 6 | N:M relationships resolved via explicit junction/associative entities | Mandatory | Functional Suitability | Required for correct relational representation |
| 7 | Naming conventions for entities/attributes are consistent and free of implementation-specific abbreviations | Optional | Usability, Maintainability | Improves readability and long-term maintainability |

## Common Defects

- Entities without a defined primary key
- Missing foreign keys on relationships that require referential integrity
- Unresolved N:M relationships without a junction entity
- Data types inconsistent with the DCD/Operation Contracts they implement
- Denormalization applied without documented performance justification

## Traceability Rule

- Backward: Must trace to the Design Class Diagram checklist ([QC-DCD-001]), particularly persistent classes and their attributes/associations
- Forward: Feeds into physical database implementation (schema creation, migrations) — outside this project's scope and outside the QC checklist chain, but must remain consistent with it

---

[QC-DCD-001]: ./qc-dcd.md
