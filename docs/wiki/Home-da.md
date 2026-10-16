# QC-tjeklister

🌐 [English](Home) · **Dansk** · [Bahasa Melayu](Home-ms)

Kvalitetskriterier (QC-tjeklister) til review af projektdokumenter og
kildekode. Én Markdown-fil pr. artefakttype, hvert kriterium mærket med en
ISO/IEC 25010:2023-kvalitetsegenskab. Licens:
[CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/).

| Side | Læs den, når du vil |
| --- | --- |
| [Beskrivelse](Description-da) | Forstå hvordan en tjekliste er bygget, ID-skemaet, niveauer og sporbarhed |
| [Installation](Install-da) | Bruge tjeklisterne alene eller som submodul |
| [AI-promptskabelon](AI-Prompt-Template-da) | Bede en AI-agent reviewe et dokument eller kode mod en tjekliste |
| [Appendiks](Appendix-Documentation-da) | Links til alle dokumenter under `artifacts/`, `code/` |

## Tjeklister

Dokumenternes tjeklister ligger i `artifacts/`; tjeklisterne for kildekode, scripts og automatisering ligger i `code/`.

| Gruppe | Filer |
| --- | --- |
| Forretning og analyse | `qc-business-case`, `qc-stakeholder-analysis`, `qc-kpi`, `qc-business-model-canvas`, `qc-bpmn`, `qc-governance`, `qc-milestones-gateways` |
| Krav | `qc-use-case-diagram`, `qc-use-case`, `qc-user-story` |
| Design | `qc-domain-model`, `qc-ssd`, `qc-operation-contract`, `qc-sequence-diagram`, `qc-dcd`, `qc-erd`, `qc-adr` |
| Ordforråd, sprog, domæne | `qc-dictionary`, `qc-language-domain` |
| Kildekode (`code/`) | `qc-programming-python`, `-c`, `-cpp`, `-csharp`, `-shell` |
| YAML og CI-workflows (`code/`) | `qc-yaml`, `qc-workflow` |

Tjeklisterne er kvalitetsporten i
[SQA and QC Framework](https://git.tirsystem.com/TirSystem/sqa-qc-framework),
som monterer dette repository i `framework/qc/`. De kan bruges uden det.
