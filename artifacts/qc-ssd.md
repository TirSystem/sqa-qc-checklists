# Quality Criteria: System Sequence Diagram (SSD)

## Metadata
| Key | Value |
| --- | --- |
| ID | QC-SSD-001 |
| CrossReference | [QC-UC-001], [QC-DM-001], [QC-OC-001] |
| DomainLanguages | IT Professional English |

## Version History
| Date | Status | Author | Reviewer | Change | Commit |
| --- | --- | --- | --- | --- | --- |
| 2026-10-01 | Accepted | Jens Tirsvad Nielsen | S07 | First public release (1.0.0) | — |

---

## Purpose

The System Sequence Diagram illustrates the interaction between an actor and the system as a black box, for one use case scenario. Its quality ensures that the boundary between external actors and internal system behavior is captured accurately before internal design begins.

## Quality Criteria Checklist

Level: **Mandatory** criteria are the baseline every instance must meet; **Optional** criteria are advanced and may be deferred.

| # | Criterion | Level | ISO/IEC 25010 Characteristic(s) | Notes |
| --- | --- | --- | --- | --- |
| 1 | Input/output messages match the corresponding Use Case's main success scenario step-for-step | Mandatory | Functional Suitability | The primary purpose of an SSD; deviations must be justified |
| 2 | Actor and System are treated strictly as black boxes (system shown as `:System`) | Mandatory | Maintainability, Compatibility | No internal object interactions may appear on an SSD |
| 3 | Object creation/destruction of the System instance handled explicitly where relevant | Optional | Functional Suitability | Applies mainly to session/transaction-scoped interactions |
| 4 | Return values are shown for operations that produce one, using dashed return arrows | Mandatory | Functional Suitability | Missing return arrows hide important system responses |
| 5 | Alternate/exceptional flows are represented separately (or explicitly out of scope noted) | Mandatory | Reliability | Prevents conflating happy-path and error-path in a single diagram |
| 6 | Message names are verb phrases consistent with the use case's system responsibilities | Optional | Usability, Maintainability | Improves traceability to Operation Contracts |
| 7 | Diagram references the specific Use Case (name and ID) it depicts | Mandatory | Maintainability | Required for backward traceability |

## Common Defects

- Showing internal objects or classes instead of a single `:System` lifeline
- Message sequence not matching the use case's main success scenario
- Missing return values for queries or commands that report a result
- Mixing multiple use case scenarios into a single SSD without separation
- No reference to the source Use Case

## Traceability Rule

- Backward: Must trace to a specific Use Case checklist ([QC-UC-001]) main success scenario and the Domain Model checklist ([QC-DM-001]) concepts used as message parameters/return types
- Forward: Feeds into the Operation Contract checklist ([QC-OC-001]), one per system operation (message) shown on the SSD

---

[QC-UC-001]: ./qc-use-case.md
[QC-DM-001]: ./qc-domain-model.md
[QC-OC-001]: ./qc-operation-contract.md
