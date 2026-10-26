# Senarai Semak QC

🌐 [English](Home) · [Dansk](Home-da) · **Bahasa Melayu**

Senarai semak kriteria kualiti (QC) untuk menyemak dokumen projek dan kod
sumber. Satu fail Markdown bagi setiap jenis artifak, setiap kriteria ditandai
dengan ciri kualiti ISO/IEC 25010:2023. Dilesenkan
[CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/).

| Halaman | Baca apabila anda mahu |
| --- | --- |
| [Huraian](Description-ms) | Memahami cara senarai semak dibina, skema ID, tahap dan kebolehjejakan |
| [Pemasangan](Install-ms) | Menggunakan senarai semak secara bersendirian atau sebagai submodul |
| [Templat Prompt AI](AI-Prompt-Template-ms) | Meminta ejen AI menyemak dokumen atau kod terhadap senarai semak |
| [Lampiran](Appendix-Documentation-ms) | Pautan ke setiap dokumen di bawah `artifacts/`, `code/` |

## Senarai semak

Senarai semak dokumen berada dalam `artifacts/`; senarai semak untuk kod sumber, skrip dan automasi berada dalam `code/`.

| Kumpulan | Fail |
| --- | --- |
| Perniagaan dan analisis | `qc-business-case`, `qc-stakeholder-analysis`, `qc-kpi`, `qc-business-model-canvas`, `qc-bpmn`, `qc-governance`, `qc-milestones-gateways` |
| Keperluan | `qc-use-case-diagram`, `qc-use-case`, `qc-user-story` |
| Reka bentuk | `qc-domain-model`, `qc-ssd`, `qc-operation-contract`, `qc-sequence-diagram`, `qc-dcd`, `qc-erd`, `qc-architecture-description`, `qc-adr` |
| Perbendaharaan kata, bahasa, domain | `qc-dictionary`, `qc-language-domain` |
| Kod sumber (`code/`) | `qc-programming-python`, `-c`, `-cpp`, `-csharp`, `-shell` |
| YAML dan aliran kerja CI (`code/`) | `qc-yaml`, `qc-workflow` |

Senarai semak ini ialah pintu kualiti
[SQA and QC Framework](https://git.tirsystem.com/TirSystem/sqa-qc-framework),
yang memasang repositori ini di `framework/qc/`. Ia boleh digunakan tanpanya.
