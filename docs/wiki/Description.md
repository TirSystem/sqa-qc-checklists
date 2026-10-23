# Description

🌐 **English** · [Dansk](Description-da) · [Bahasa Melayu](Description-ms)

## What a checklist contains

Every `qc-<type>.md` (in `artifacts/` for documents, in `code/` for source code, scripts and automation) has the same shape:

| Section | Content |
| --- | --- |
| `## Metadata` | `ID` (e.g. `QC-US-001`), `CrossReference` to related checklists, `DomainLanguages` |
| `## Version History` | Date, status, author, reviewer, change |
| `## Purpose` | Why the artifact type exists and what the checklist protects |
| `## Quality Criteria Checklist` | The numbered criteria table |
| `## Common Defects` | The mistakes reviewers actually find |
| `## Traceability Rule` | What the artifact must trace *back* to and *forward* to |

## The criteria table

| # | Criterion | Level | ISO/IEC 25010 Characteristic(s) | Notes |
| --- | --- | --- | --- | --- |
| 2 | Written in "As a / I want / So that" form | Mandatory | Interaction Capability | |

- **Mandatory**: the baseline every instance must meet.
- **Optional**: advanced; may be deferred, with a reason.
- **ISO/IEC 25010 characteristic**: which product-quality characteristic the
  criterion protects (Functional Suitability, Reliability, Interaction Capability,
  Maintainability, Security, Compatibility, ...). It lets a reviewer see
  *what kind* of quality a failed criterion puts at risk, not only that it failed.

## IDs and versions

- A checklist ID is `QC-` plus the short code of the artifact type it covers: `QC-BC-001`, `QC-UC-001`, `QC-ERD-001`.
- The version is independent of any reviewed document and increments only when the checklist itself is revised.
- The `qc-language-domain.md` checklist (`QC-LANG-001`) is **cross-cutting**: it applies in addition to the type's own checklist to every document written in the Product Owner's language.

## Traceability

Checklists link to each other. The *Traceability Rule* of a user-story
checklist points back to use case diagram, use case and business case checklists
and forward to acceptance tests. A reviewer uses this to check that a document
does not float free of the ones it depends on.

## A review, step by step

1. Pick the checklist for the artifact type (plus `QC-LANG-001` if the language applies).
2. For every criterion record `Pass`, `Fail` or `N-A`, with evidence.
3. Give a verdict: **Go**, **Go-with-conditions** or **No-Go**.
4. Fix or justify every failed criterion, then re-review the delta.
5. The reviewer is never the author.

The record format (an `RC-*` review record) is defined by the
[framework](https://git.tirsystem.com/TirSystem/sqa-qc-framework); outside the
framework any table with the same columns works.

## Source-code, YAML and workflow checklists

The `qc-programming-*` checklists assume your team has written down its coding
conventions for the language. They check that code **follows them**; they do
not impose a style of their own.

`qc-yaml` (`QC-YML-001`) applies to any YAML file and `qc-workflow` (`QC-WF-001`) to a Gitea
Actions or GitHub Actions workflow; a workflow is reviewed against both. They check, among
other things, that no secret is written in the file, that every job has least-privilege
permissions, a timeout and pinned actions, and that a script embedded in YAML is at most
five lines (a longer one is a file that can be linted and tested).

## Licence

CC BY-SA 4.0. Share and adapt, including commercially, if you credit TirSystem
and release your adaptation under the same licence.
