# Quality Criteria: Test Plan

## Metadata
| Key | Value |
| --- | --- |
| ID | QC-TP-001 |
| CrossReference | [QC-UC-001], [QC-OC-001], [QC-MIL-001] |
| DomainLanguages | IT Professional English |

## Version History
| Date | Status | Author | Reviewer | Change | Commit |
| --- | --- | --- | --- | --- | --- |
| 2026-10-20 | Proposed | Jens Tirsvad Nielsen | S02 | Created | [671993f] |
| 2026-10-22 | Proposed | Jens Tirsvad Nielsen | S02 | Renamed the ISO/IEC 25010 tags to the 2023 names: Usability to Interaction Capability, Portability to Flexibility (RC-083) | pending |

---

## Purpose

A Test Plan states what will be tested, with which kinds of test, at which level and in which environment, and which kinds do not apply and why. It turns the use cases, operation contracts and risks into checkable evidence, so that a milestone's Go/No-Go can rest on test results and not on opinion.

## Quality Criteria Checklist

Level: **Mandatory** criteria are the baseline every instance must meet; **Optional** criteria are advanced and may be deferred.

| # | Criterion | Level | ISO/IEC 25010 Characteristic(s) | Notes |
| --- | --- | --- | --- | --- |
| 1 | Scope names what is tested and what is out of scope, and each unit of behaviour under test traces to a use case, an operation contract, a quality requirement or a plain technical task | Mandatory | Functional Suitability, Maintainability | |
| 2 | A coverage matrix has one row per unit of behaviour and one column per test kind of `coding-conventions` rule 17 (positive, negative, boundary value, edge case, equivalence partitioning, state transition, concurrency, race condition, asynchronous, timeout and retry, error handling, integration, regression, exploratory) | Mandatory | Functional Suitability, Reliability | |
| 3 | Every cell of the matrix lists test case IDs, or `N/A` with a reason; no cell is empty | Mandatory | Functional Suitability, Reliability | A reason such as "no shared state" is checkable; "not needed" is not |
| 4 | Each test case has an ID, the behaviour it proves, input or setup, and the expected result stated so a pass or fail is unambiguous | Mandatory | Functional Suitability | |
| 5 | Each postcondition and each exception of an operation contract in scope is covered by at least one test case | Mandatory | Functional Suitability, Reliability | |
| 6 | Boundary-value cases list the limits of each input range and test at, just below and just above each limit | Mandatory | Reliability | |
| 7 | Levels are stated (unit, integration, end-to-end) with the tool and the folder under `tests/` for each, and unit tests use fakes with no network and no fixed sleep | Mandatory | Maintainability, Reliability | |
| 8 | Test environments and test data are stated; a GUI or end-to-end test names its environment (Docker container or Windows Sandbox), never the host desktop | Mandatory | Reliability, Flexibility | `process/gui-testing.md` |
| 9 | Entry and exit criteria are objectively checkable and feed the Go/No-Go of the milestone that depends on the plan | Mandatory | Maintainability | |
| 10 | The risks in the Risk Analysis that testing mitigates are listed, each with the test cases that address it | Optional | Reliability, Security | |
| 11 | Non-functional tests (performance, security, accessibility, portability) are planned where a quality requirement exists, each with a measurable threshold | Optional | Performance Efficiency, Security, Interaction Capability, Flexibility | A size or speed goal is a number, not a word |
| 12 | The exploratory kind has a charter and a time box, and each defect it finds becomes a scripted regression test | Optional | Reliability | |
| 13 | Defect handling is stated: where defects are recorded, how severity is set, and that every fixed defect gets a regression test | Optional | Maintainability | |

## Common Defects

- A matrix with empty cells, or `N/A` with no reason
- Test cases that say "works correctly" instead of an observable result
- Only positive cases; boundaries and failures missing
- A use case or operation contract with no test case that traces to it
- Concurrency or timeout behaviour in the design but no test of it
- Unit tests that call the network or sleep for a fixed time
- A GUI test planned on the host desktop
- Exit criteria that are words ("good enough") and not numbers or checks
- Test cases that restate the code instead of the specification

## Traceability Rule

- Backward: Use Case checklist ([QC-UC-001]) and Operation Contract checklist ([QC-OC-001]) for the behaviour under test; Milestone checklist ([QC-MIL-001]) for the gate the plan supports
- Forward: the test code under `tests/`, which is reviewed against the language's `qc-programming-*` checklist

---

[QC-UC-001]: ./qc-use-case.md
[QC-OC-001]: ./qc-operation-contract.md
[QC-MIL-001]: ./qc-milestones-gateways.md
[671993f]: https://git.tirsystem.com/TirSystem/SQA-QC-Checklists/commit/671993fe2def9f17df72db99ab58bdd26581be00
