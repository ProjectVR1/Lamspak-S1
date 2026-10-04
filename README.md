# Muhasabbah FED LAMSPAK Sarjana - IAPS 2.0 (v3.0)

Aplikasi statis siap **GitHub Pages** untuk evaluasi diri Program Sarjana/S1 berdasarkan paket instrumen yang diberikan pengguna:

- `14_Matriks Penilaian Unggul_Sarjana.pdf` - 73 indikator, rubrik skor 0/1/2, bobot.
- `FED_Unggul_Sarjana.docx` - struktur narasi dan 43 tabel data kinerja.
- `Alat Bantu Penghitungan Tabel.xlsx` - struktur tabel dan formula bantu.

## Perbaikan metodologis utama

1. **Memisahkan batas skor dari syarat perlu Unggul.** Butir dengan teks “tidak ada nilai kurang dari 1” tidak lagi otomatis disebut kritis. “SYARAT PERLU UNGGUL” hanya ditandai jika frasa tersebut eksplisit pada kolom keterangan matriks.
2. **Indeks kesiapan bukan keputusan akreditasi.** Rumus internal: `Σ(skor × bobot) / 282 × 100`.
3. **Kematangan bukti dihitung terpisah** dari skor rubrik, sehingga kualitas dokumentasi tidak mengubah deskriptor resmi.
4. **Kalkulator deterministik** tersedia pada indikator kuantitatif utama. Saran kalkulator hanya diterapkan jika pengguna menekan tombol `Gunakan skor terukur`.
5. **Screening dokumen konservatif.** Analisis DOCX/PDF tidak menganggap “tidak ditemukan teks” sebagai skor 0 dan tidak menimpa skor evaluator otomatis.
6. **Narasi hasil per item** dibuat dari skor, bobot, pengukuran, status bukti, dan gap ke skor 2.
7. **Rencana tindak lanjut** memuat prioritas, tindakan, PIC, tenggat, indikator keberhasilan, dan status.
8. **Ekspor PDF dan Word (.docx)** serta cetak browser/Save as PDF.

## Instalasi GitHub Pages

1. Buat repository baru.
2. Unggah seluruh isi folder ini ke root repository.
3. `Settings` → `Pages` → `Deploy from a branch`.
4. Pilih branch `main` dan folder `/(root)`, lalu `Save`.
5. Buka URL GitHub Pages yang diberikan.

Tidak diperlukan Node.js, build step, database, atau server. Data pengguna tersimpan di `localStorage` browser; gunakan **Backup JSON** secara berkala.

## Ketergantungan CDN

Aplikasi menggunakan Mammoth (DOCX reader), PDF.js, jsPDF + AutoTable, dan docx.js untuk ekspor Word. Pada GitHub Pages, pustaka ini dimuat melalui CDN. Data FED tetap diproses di browser. Jika pustaka PDF tidak termuat, tombol PDF mengalihkan ke dialog cetak browser/Save as PDF. Jika docx.js tidak termuat, ekspor Word otomatis menggunakan fallback `.doc` berbasis HTML sehingga laporan tetap dapat dibuka di Microsoft Word/LibreOffice.

## Catatan validasi sumber

Beberapa teks sumber memiliki ketidakkonsistenan yang sengaja **tidak disembunyikan**:

- Butir 15 menulis persentase responden `PJ = (NL/NJ) × 100%`; kalkulator meminta `PJ` langsung agar tidak mengoreksi sumber secara diam-diam.
- Butir 56 menulis pertidaksamaan skor 1 secara tidak konsisten; nilai <25% tidak dipetakan otomatis.
- Butir 64 menyebut `DPD` pada deskriptor skor 1, sementara indikator menggunakan `DPkMD`; aplikasi mengikuti variabel indikator dan memberikan peringatan.

Lihat halaman **Metodologi** di dalam aplikasi untuk rumus, klasifikasi, dan batas interpretasi.

## Struktur berkas

- `index.html` - UI utama.
- `styles.css` - tampilan dan print CSS.
- `lamspak-data.js` - matriks dan 43 tabel.
- `app.js` - penilaian, kalkulator, tabel, laporan, ekspor.
- `analysis.js` - screening dokumen FED.
- `.nojekyll` - kompatibilitas GitHub Pages.

## Prinsip penggunaan

Aplikasi adalah alat bantu **evaluasi diri dan audit internal**, bukan mesin keputusan akreditasi. Skor akhir dan status akreditasi harus mengikuti asesmen resmi LAMSPAK serta instrumen yang berlaku pada saat pengajuan.


## Verifikasi eksternal instrumen

Per 30 September 2026, halaman **Instrumen** resmi LAMSPAK masih mencantumkan **Paket IAPS 2.0 Unggul Sarjana**. Tautan rujukan: `https://www.lamspak.id/akreditasi/instrumen/`. Paket aplikasi ini tetap menggunakan berkas instrumen yang disediakan pengguna sebagai sumber data operasional; sebelum pengajuan resmi, cocokkan kembali dengan versi instrumen LAMSPAK yang berlaku.
