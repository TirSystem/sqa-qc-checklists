# Pemasangan

🌐 [English](Install) · [Dansk](Install-da) · **Bahasa Melayu**

## Gunakan fail terus

Tiada apa-apa untuk dipasang. Klon dan buka senarai semak yang anda perlukan.

Repositori ini awam, jadi HTTPS berfungsi tanpa akaun:

```bash
git clone https://git.tirsystem.com/TirSystem/sqa-qc-checklists.git
# atau cermin GitHub baca sahaja
git clone https://github.com/TirSystem/sqa-qc-checklists.git
```

SSH turut berfungsi, jika anda mempunyai akses ke `git.tirsystem.com`:

```bash
git clone ssh://git@git.tirsystem.com:10022/TirSystem/sqa-qc-checklists.git
```

Repositori kanonik berada di `git.tirsystem.com`; repositori GitHub ialah
cermin baca sahaja.

## Sebagai submodul projek anda

```bash
git submodule add https://github.com/TirSystem/sqa-qc-checklists.git qc
git submodule update --init
```

Kunci commit atau tag supaya semakan anda boleh diulang; kemas kini dengan
commit yang disengajakan.

## Dengan SQA and QC Framework

Anda tidak memasang repositori ini secara berasingan. Rangka kerja memasangnya
di `framework/qc/` sebagai submodul bersarang:

```bash
git submodule update --init --recursive
```

Jika `framework/qc/` kosong, tiada semakan boleh bermula. Lihat
[halaman Pemasangan wiki rangka kerja](https://git.tirsystem.com/TirSystem/sqa-qc-framework/wiki/Install-ms).

## Menyumbang perubahan

Kriteria baharu atau yang diubah ialah item keluaran. Ubah senarai semak,
tambah baris Version History, dan pastikan setiap kriteria ditandai dengan ciri
ISO/IEC 25010 dan tahap.
