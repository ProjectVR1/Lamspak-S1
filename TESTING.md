# Checklist Pengujian sebelum Go-Live

## Sudah diuji pada paket ini

1. Sintaks seluruh JavaScript utama.
2. Integritas 73 indikator dan 43 tabel.
3. Total bobot dan skor maksimum berbobot.
4. Pemisahan `scoreFloor`, `syaratUnggul`, dan `syaratAkreditasi`.
5. Kalkulator contoh untuk butir kuantitatif kritis.
6. Formula `AVERAGE` mengabaikan sel kosong.
7. Skor pecahan pada butir tracer study dapat disimpan dan ditampilkan.
8. Seluruh ID elemen yang direferensikan JavaScript tersedia di HTML.

## Disarankan diuji setelah deploy GitHub Pages

1. Isi 3–5 indikator, refresh halaman, pastikan `localStorage` memulihkan data.
2. Backup JSON → reset → restore JSON.
3. Unggah contoh FED `.docx` dan periksa bahwa hasil screening hanya berupa **saran**, tidak menimpa skor secara otomatis.
4. Isi salah satu dari 43 tabel dan bandingkan hasil formula dengan Excel sumber.
5. Ekspor PDF, Word `.docx`, dan Print/Save as PDF.
6. Uji di Chrome/Edge versi terbaru pada komputer tim akreditasi.
7. Lakukan peer review oleh minimal satu anggota tim penjaminan mutu yang tidak mengembangkan aplikasi.

## Kriteria penerimaan substantif

Aplikasi dinyatakan layak sebagai alat bantu internal bila (a) rubrik sama dengan instrumen yang berlaku, (b) hasil hitung sampel sama dengan perhitungan manual/Excel, (c) semua skor memiliki bukti terlacak, dan (d) rekomendasi dapat diturunkan menjadi PIC, tenggat, dan indikator keberhasilan. Status akreditasi tetap ditentukan melalui proses resmi LAMSPAK.
