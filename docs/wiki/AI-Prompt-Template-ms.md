# Templat Prompt AI

🌐 [English](AI-Prompt-Template) · [Dansk](AI-Prompt-Template-da) · **Bahasa Melayu**

Prompt untuk menyemak dengan ejen AI. Jalankan semakan dalam **sesi baharu**
jika ejen yang sama menulis dokumen: penyemak tidak boleh penulisnya.

## Semak dokumen

```text
Semak <laluan/ke/dokumen.md> terhadap senarai semak <laluan/ke/qc-jenis.md>.
Bagi setiap kriteria bernombor beri Pass, Fail atau N-A dengan bukti (petik
baris dalam dokumen). Kemudian senaraikan kriteria Mandatory yang gagal
dahulu, beri keputusan (Go, Go-with-conditions, No-Go) dan perubahan terkecil
yang akan menjadikan setiap kriteria yang gagal lulus. Jangan sunting dokumen.
```

## Semak kod

```text
Semak perubahan dalam <laluan atau diff> terhadap <laluan/ke/qc-programming-bahasa.md>
dan konvensyen pengekodan kami di <laluan>. Laporkan setiap kriteria sebagai
Pass, Fail atau N-A dengan fail dan baris. Jangan betulkan apa-apa; senaraikan
dapatan mengikut keterukan.
```

## Semak bahasa dan domain

```text
Semak <dokumen> terhadap qc-language-domain.md. Bahasa Product Owner ialah
<bahasa> dan domainnya <domain>. Semak bahawa setiap istilah PO yang digunakan
dalam dokumen terdapat dalam kamus <laluan> dan tiada istilah IT yang meresap
ke bahagian untuk PO. Senaraikan setiap ketidakpadanan dengan barisnya.
```

## Semak semula selepas pembetulan

```text
Semak semula hanya kriteria yang gagal dalam <rekod semakan terdahulu>. Bagi
setiap satu, nyatakan sama ada <dokumen> baharu kini lulus dan petik buktinya.
```

## Petua

- Beri ejen **satu** senarai semak bagi setiap semakan.
- Minta bukti bagi setiap kriteria; "Pass" sahaja bukan semakan.
- Anggap keputusan ejen sebagai input. Penyemak yang memutuskan.
