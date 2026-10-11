# sqa-qc-checklists

Quality-criteria (QC) checklists used by TirSystem to review project
documents and source code. Each checklist is one Markdown file, `qc-<type>.md`,
with an ID such as `QC-BC-001`. The checklists of documents are in `artifacts/`;
those of source code, scripts and automation are in `code/`. Every criterion is tagged with an
ISO/IEC 25010:2023 quality characteristic.

## Contents

- Business and analysis: Business Case, Stakeholder Analysis, KPI, Business
  Model Canvas, BPMN, Governance, Milestones and gateways
- Requirements and design: Use Case Diagram, Use Case, User Story, Domain Model,
  SSD, Operation Contract, Sequence Diagram, DCD, ERD, ADR
- Cross-cutting: Language and Domain (applies to every artifact type written in
  the Product Owner's language), Domain Dictionary
- Source code and automation (`code/`): Python, C, C++, C#, shell, YAML files,
  CI workflows (Gitea Actions, GitHub Actions)

## Use

Review a document against the checklist for its type: tick each criterion,
record the outcome in a review record, and fix or justify every failed
criterion. Checklists link to each other through their `CrossReference` row,
for example a Use Case checklist points back to the Stakeholder Analysis one.

The programming checklists assume your team has written down its own coding
conventions for the language; they check that code follows them.

## Used as a submodule

```bash
git submodule add https://github.com/TirSystem/sqa-qc-checklists.git qc
```

## License

[CC BY-SA 4.0](LICENSE). You may share and adapt the checklists, including
commercially, if you credit TirSystem and release your adaptation under the
same license.

The canonical repository is on `git.tirsystem.com`; this GitHub repository is a
read-only mirror.
