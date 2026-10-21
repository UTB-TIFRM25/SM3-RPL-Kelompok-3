# Keputusan, Asumsi, Risiko, dan Pertanyaan Terbuka

Dokumen ini mencegah asumsi teknis/bisnis dianggap sebagai keputusan final.

## 1. Asumsi sementara
| ID | Asumsi | Status |
|---|---|---|
| A-01 | Produk pertama berupa web responsif | Perlu konfirmasi |
| A-02 | Listing yang tampil publik harus disetujui admin | Usulan berdasarkan kebutuhan verifikasi |
| A-03 | Harga ditampilkan dalam IDR | Perlu konfirmasi |
| A-04 | Database relasional digunakan untuk data inti | Rekomendasi teknis |
| A-05 | Foto disimpan di object storage | Rekomendasi teknis |
| A-06 | Empat sprint adalah rencana awal, durasi 1–2 minggu | Berdasarkan materi awal; kapasitas perlu validasi |
| A-07 | Pembayaran sewa tidak termasuk MVP | Usulan pembatasan ruang lingkup |
| A-08 | Chat internal, peta, dan rating dapat dipindah ke sprint lanjutan | Rekomendasi pengendalian scope |

## 2. Pertanyaan produk — perlu jawaban sebelum implementasi terkait
1. Siapa target pasar awal: mahasiswa, pekerja, atau keduanya?
2. Area peluncuran pertama di kota/daerah mana?
3. Apakah pengguna dapat melihat listing tanpa login?
4. Apakah akun pemilik harus diverifikasi? Jika ya, dengan cara apa?
5. Informasi harga ditetapkan per bulan, minggu, hari, atau dapat bervariasi?
6. Apakah listing mewakili satu properti kos atau per kamar?
7. Bagaimana status kamar didefinisikan dan seberapa sering pemilik wajib memperbarui?
8. Apa checklist admin untuk menyetujui listing?
9. Apakah perubahan listing yang sudah disetujui memerlukan verifikasi ulang?
10. Bagaimana pencari dapat menghubungi pemilik pada MVP: nomor/tautan kontak atau chat internal?
11. Apakah ulasan hanya boleh dibuat oleh penghuni terverifikasi?
12. Apakah ada fitur pelaporan listing dan proses penanganannya?
13. Apakah ada pembayaran/booking di fase berikutnya?
14. Apakah produk memiliki biaya listing atau model bisnis lain?

## 3. Pertanyaan teknis
1. Stack frontend/backend apa yang dikuasai tim?
2. Hosting target dan anggaran awal?
3. Apakah autentikasi dibuat di aplikasi atau memakai identity provider?
4. Database apa yang akan digunakan dan siapa yang mengelolanya?
5. Object storage/provider foto apa yang dipilih?
6. Provider peta dan kebijakan API key/biayanya?
7. Target performa dan jumlah pengguna bersamaan?
8. Target availability, RPO, dan RTO?
9. Apakah perlu email/WhatsApp notification?
10. Apakah aplikasi harus memenuhi ketentuan privasi atau regulasi tertentu yang berlaku?

## 4. Decision log
Tambahkan keputusan baru di atas baris terbaru.

| ID | Tanggal | Keputusan | Alasan | Pemutus | Dampak |
|---|---|---|---|---|---|
| DEC-001 | 2026-10-21 | Dokumen awal menggunakan PRD, Product Backlog, dan empat sprint sebagai baseline | Menyelaraskan dokumentasi dengan materi proyek | Belum ditetapkan | Perlu validasi sebelum implementasi |

## 5. Risk register
| ID | Risiko | Kemungkinan | Dampak | Mitigasi / tindakan |
|---|---|---|---|---|
| R-01 | Ruang lingkup Sprint 4 terlalu besar | Sedang | Tinggi | Prioritaskan verifikasi dan kesiapan operasional; fitur lain dapat ditunda |
| R-02 | Data ketersediaan kedaluwarsa | Tinggi | Tinggi | Tampilkan waktu pembaruan, pengingat pemilik, mekanisme pelaporan |
| R-03 | Listing palsu | Sedang | Tinggi | Moderasi, audit trail, laporan pengguna |
| R-04 | Ulasan tidak autentik | Sedang | Sedang | Tentukan bukti kelayakan dan moderasi |
| R-05 | Upload foto berisiko atau mahal | Sedang | Sedang | Batas ukuran/jenis, validasi konten, kompresi, lifecycle storage |
| R-06 | Kebutuhan hosting/teknologi belum jelas | Sedang | Sedang | Spike teknis singkat sebelum komitmen implementasi |

## 6. Langkah berikutnya yang direkomendasikan
1. Review PRD bersama calon pengguna dan pemilik kos.
2. Tetapkan Product Owner dan pihak yang berwenang mengambil keputusan.
3. Jawab pertanyaan produk yang memengaruhi data model dan MVP.
4. Pilih stack dan target hosting setelah menilai kemampuan tim.
5. Buat wireframe untuk pencarian/detail, dashboard pemilik, dan moderasi admin.
6. Lakukan backlog refinement dan estimasi tim.
7. Jalankan Sprint 1 dengan Sprint Goal yang realistis.
