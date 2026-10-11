# Quality Criteria: Operation Contract

## Metadata
| Key | Value |
| --- | --- |
| ID | QC-OC-001 |
| CrossReference | [QC-SSD-001], [QC-DM-001], [QC-SD-001] |
| DomainLanguages | IT Professional English |

## Version History
| Date | Status | Author | Reviewer | Change | Commit |
| --- | --- | --- | --- | --- | --- |
| 2026-10-01 | Accepted | Jens Tirsvad Nielsen | S07 | First public release (1.0.0) | — |

---

## Purpose

An Operation Contract precisely specifies the effect of a single system operation (identified on an SSD) in terms of preconditions and postconditions on the Domain Model, without prescribing implementation. Its quality is essential for unambiguous, testable behavioral specifications that bridge analysis and design.

## Quality Criteria Checklist

Level: **Mandatory** criteria are the baseline every instance must meet; **Optional** criteria are advanced and may be deferred.

| # | Criterion | Level | ISO/IEC 25010 Characteristic(s) | Notes |
| --- | --- | --- | --- | --- |
| 1 | Method signature is complete: operation name, parameter types, and return type | Mandatory | Functional Suitability | Signature must match the corresponding SSD message |
| 2 | Preconditions explicitly list required state before execution | Mandatory | Functional Suitability, Reliability | Must reference Domain Model concepts, not implementation state |
| 3 | Postconditions explicitly describe resulting state using Larman's "instance created/associated/attribute modified" style | Mandatory | Functional Suitability | Avoid describing algorithmic steps; describe state deltas only |
| 4 | Exceptions and error conditions are documented, including the triggering precondition failure | Mandatory | Reliability, Security | Ensures error handling is designed, not assumed |
| 5 | Operation is explicitly traceable to a single SSD message | Mandatory | Maintainability | One contract per system operation |
| 6 | Contract avoids specifying implementation/algorithmic details (declarative, not procedural) | Optional | Maintainability | Contracts describe "what", not "how" |
| 7 | Cross-references the Domain Model classes/associations affected by pre/postconditions | Optional | Maintainability | Keeps contract consistent with the Domain Model |

## Common Defects

- Missing or vague postconditions (e.g. "system processes the request")
- Describing implementation logic instead of state changes
- Preconditions that don't match the actual guard conditions needed
- No traceability reference back to the originating SSD message
- Omitting exception/error conditions entirely

## Traceability Rule

- Backward: Must trace to a specific System Sequence Diagram checklist ([QC-SSD-001]) message and the Domain Model checklist ([QC-DM-001]) concepts referenced in pre/postconditions
- Forward: Feeds into the design-level Sequence Diagram checklist ([QC-SD-001]) that realizes the operation's postconditions through object collaborations

---

[QC-SSD-001]: ./qc-ssd.md
[QC-DM-001]: ./qc-domain-model.md
[QC-SD-001]: ./qc-sequence-diagram.md
