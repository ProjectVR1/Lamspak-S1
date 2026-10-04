# Catatan Validasi dan Jejak Perubahan

## Verifikasi struktur sumber

- Matriks penilaian: 73 indikator, 11 standar, total bobot 141, maksimum berbobot 282.
- FED/alat bantu: 43 tabel data kinerja.
- Skor rubrik: 0, 1, 2; pada 27 butir kolom skor 0 menyatakan “tidak ada nilai kurang dari 1”, sehingga dropdown skor 0 dinonaktifkan pada butir tersebut.
- Butir yang secara eksplisit memuat “SYARAT PERLU UNGGUL” pada keterangan matriks: 9, 16, 55, 56, 60.
- Butir 44 dan 45 memiliki catatan eksplisit mengenai kondisi yang “TIDAK MEMENUHI syarat terakreditasi”.

## Koreksi terhadap aplikasi lama

Aplikasi lama menggunakan field `mandatory` untuk seluruh butir dengan skor minimum 1. Ini mencampur dua konsep: “skor rubrik tidak boleh 0” dan “syarat perlu Unggul”. Versi 3 memisahkan:

- `scoreFloor` - batas bawah skor berdasarkan kolom skor 0;
- `syaratUnggul` - hanya jika kolom keterangan menyebut frasa tersebut;
- `syaratAkreditasi` - jika matriks secara eksplisit menyatakan kondisi tidak memenuhi syarat terakreditasi.

## Prinsip validitas

1. Tidak ada status “Unggul” otomatis.
2. Indeks 0-100 diberi nama **Indeks Kesiapan Internal**, bukan nilai akreditasi.
3. Screening teks tidak boleh menghasilkan skor 0 hanya karena bukti tidak ditemukan.
4. Saran otomatis tidak menimpa skor manual tanpa tindakan eksplisit pengguna.
5. Evidence maturity merupakan indikator audit internal yang terpisah dari skor rubrik.
6. Ketidakkonsistenan teks sumber ditampilkan kepada pengguna, bukan “diperbaiki” diam-diam.


## Uji teknis paket v3

- Pemeriksaan sintaks JavaScript (`node --check`) untuk `app.js`, `analysis.js`, dan `lamspak-data.js`: **lulus**.
- Integritas data: 73 indikator, 11 standar, total bobot 141, maksimum berbobot 282, 43 tabel: **lulus**.
- Formula tabel yang dipreservasi dari alat bantu: 166 formula (`SUM`, `AVERAGE`, `IF`): terdeteksi dan dimuat.
- Uji ambang butir 9: RIPK 3,25 → skor 2: **lulus**.
- Uji butir 15: penyesuaian skor berbasis Prmin menghasilkan skor pecahan tanpa dipaksa menjadi bilangan bulat: **lulus**.
- Uji butir 44: NDPRPS < 5 → skor 0 dan peringatan syarat terakreditasi: **lulus**.
- Uji butir 56: nilai <25% tidak dipaksakan ke skor 0 karena ketidakjelasan teks sumber: **lulus**.
- Uji `AVERAGE` tabel: sel kosong diabaikan seperti Excel: **lulus**.
- Uji 5 butir eksplisit “SYARAT PERLU UNGGUL” (9, 16, 55, 56, 60): **lulus**.

### Batas uji

Uji di atas memvalidasi integritas data dan logika perangkat lunak, bukan mengesahkan aplikasi sebagai instrumen resmi LAMSPAK. Keputusan skor substantif tetap membutuhkan telaah evaluator terhadap dokumen, tabel, bukti sahih, dan ketentuan yang berlaku. Integrasi pustaka pihak ketiga dimuat dari CDN pada saat aplikasi dijalankan; mekanisme fallback disediakan untuk PDF/Word.
