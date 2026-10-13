# Huraian

🌐 [English](Description) · [Dansk](Description-da) · **Bahasa Melayu**

## Kandungan senarai semak

Setiap `qc-<jenis>.md` (dalam `artifacts/` untuk dokumen, dalam `code/` untuk kod sumber, skrip dan automasi) mempunyai bentuk yang sama:

| Bahagian | Kandungan |
| --- | --- |
| `## Metadata` | `ID` (cth. `QC-US-001`), `CrossReference` kepada senarai semak berkaitan, `DomainLanguages` |
| `## Version History` | Tarikh, status, penulis, penyemak, perubahan |
| `## Purpose` | Mengapa jenis artifak wujud dan apa yang dilindungi senarai semak |
| `## Quality Criteria Checklist` | Jadual kriteria bernombor |
| `## Common Defects` | Kesilapan yang sebenarnya ditemui penyemak |
| `## Traceability Rule` | Apa yang artifak mesti jejak *ke belakang* dan *ke hadapan* |

## Jadual kriteria

| # | Criterion | Level | ISO/IEC 25010 Characteristic(s) | Notes |
| --- | --- | --- | --- | --- |
| 2 | Written in "As a / I want / So that" form | Mandatory | Usability | |

- **Mandatory**: asas yang mesti dipenuhi setiap instans.
- **Optional**: lanjutan; boleh ditangguhkan dengan sebab.
- **Ciri ISO/IEC 25010**: ciri kualiti produk yang dilindungi kriteria
  (Functional Suitability, Reliability, Usability, Maintainability, Security,
  Compatibility, ...). Ia membolehkan penyemak melihat *jenis* kualiti yang
  terjejas apabila kriteria gagal, bukan sekadar bahawa ia gagal.

## ID dan versi

- ID senarai semak ialah `QC-` ditambah kod ringkas jenis artifak yang diliputinya: `QC-BC-001`, `QC-UC-001`, `QC-ERD-001`.
- Versi bebas daripada mana-mana dokumen yang disemak dan hanya bertambah apabila senarai semak itu sendiri disemak semula.
- Senarai semak `qc-language-domain.md` (`QC-LANG-001`) ialah **merentas**: ia terpakai, selain senarai semak jenisnya, kepada setiap dokumen yang ditulis dalam bahasa Product Owner.

## Kebolehjejakan

Senarai semak saling merujuk. *Traceability Rule* senarai semak user story
menunjuk ke belakang kepada senarai semak rajah use case, use case dan business
case, dan ke hadapan kepada ujian penerimaan. Penyemak menggunakannya untuk
memastikan dokumen tidak terapung bebas daripada dokumen yang menjadi
tanggungannya.

## Satu semakan, langkah demi langkah

1. Pilih senarai semak untuk jenis artifak (tambah `QC-LANG-001` jika bahasa terpakai).
2. Bagi setiap kriteria rekod `Pass`, `Fail` atau `N-A`, dengan bukti.
3. Beri keputusan: **Go**, **Go-with-conditions** atau **No-Go**.
4. Betulkan atau wajarkan setiap kriteria yang gagal, kemudian semak semula delta.
5. Penyemak tidak pernah penulisnya.

Format rekod (rekod semakan `RC-*`) ditakrifkan oleh
[rangka kerja](https://git.tirsystem.com/TirSystem/sqa-qc-framework); di luar
rangka kerja, mana-mana jadual dengan lajur yang sama boleh digunakan.

## Senarai semak kod sumber, YAML dan aliran kerja

Senarai semak `qc-programming-*` menganggap pasukan anda telah menulis
konvensyen pengekodan untuk bahasa itu. Ia menyemak kod **mengikutinya**; ia
tidak memaksakan gaya sendiri.

`qc-yaml` (`QC-YML-001`) terpakai pada mana-mana fail YAML dan `qc-workflow` (`QC-WF-001`)
pada aliran kerja Gitea Actions atau GitHub Actions; aliran kerja disemak terhadap
kedua-duanya. Antara lain, ia menyemak bahawa tiada rahsia ditulis dalam fail, setiap job
mempunyai kebenaran paling minimum, had masa dan actions yang dikunci, dan skrip yang
tertanam dalam YAML paling banyak lima baris (yang lebih panjang ialah fail yang boleh
dilint dan diuji).

## Lesen

CC BY-SA 4.0. Kongsi dan adaptasi, termasuk secara komersial, jika anda
mengkreditkan TirSystem dan menerbitkan adaptasi anda di bawah lesen yang sama.
