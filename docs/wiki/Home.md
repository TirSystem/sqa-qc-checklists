# QC Checklists

🌐 **English** · [Dansk](Home-da) · [Bahasa Melayu](Home-ms)

Quality-criteria (QC) checklists for reviewing project documents and source
code. One Markdown file per artifact type, each criterion tagged with an
ISO/IEC 25010:2023 quality characteristic. Licensed
[CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/).

| Page | Read it when you want to |
| --- | --- |
| [Description](Description) | Understand how a checklist is built, the ID scheme, levels and traceability |
| [Install](Install) | Use the checklists on their own or as a submodule |
| [AI Prompt Template](AI-Prompt-Template) | Ask an AI agent to review a document or code against a checklist |
| [Appendix](Appendix-Documentation) | Links to every document under `artifacts/`, `code/` |

## Checklists

The checklists of documents are in `artifacts/`; those of source code, scripts and automation are in `code/`.

| Group | Files |
| --- | --- |
| Business and analysis | `qc-business-case`, `qc-stakeholder-analysis`, `qc-kpi`, `qc-business-model-canvas`, `qc-bpmn`, `qc-governance`, `qc-milestones-gateways` |
| Requirements | `qc-use-case-diagram`, `qc-use-case`, `qc-user-story` |
| Design | `qc-domain-model`, `qc-ssd`, `qc-operation-contract`, `qc-sequence-diagram`, `qc-dcd`, `qc-erd`, `qc-adr` |
| Vocabulary, language, domain | `qc-dictionary`, `qc-language-domain` |
| Source code (`code/`) | `qc-programming-python`, `-c`, `-cpp`, `-csharp`, `-shell` |
| YAML and CI workflows (`code/`) | `qc-yaml`, `qc-workflow` |

These checklists are the quality gate of the
[SQA and QC Framework](https://git.tirsystem.com/TirSystem/sqa-qc-framework),
which mounts this repository at `framework/qc/`. They are usable without it.
