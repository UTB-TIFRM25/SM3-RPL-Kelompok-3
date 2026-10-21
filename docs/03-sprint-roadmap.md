# Sprint Roadmap dan Panduan Scrum

## 1. Kerangka kerja
Materi proyek menetapkan Scrum dengan sprint 1–2 minggu, Daily Scrum 15 menit, Sprint Review, dan Sprint Retrospective. Rencana berikut mempertahankan empat sprint awal sebagai baseline, tetapi menambahkan pekerjaan kualitas/operasional agar MVP layak diuji.

## 2. Rencana empat sprint (draft)

### Sprint 1 — Fondasi dan alur penelusuran
**Tujuan sprint:** pengguna dapat masuk ke aplikasi dan melihat informasi kos dasar.

Kandidat backlog:
- KOS-001 Registrasi.
- KOS-002 Login/logout.
- KOS-003 Role/otorisasi versi awal.
- KOS-004 Daftar kos publik.
- KOS-005 Detail kos.
- Validasi dasar, struktur aplikasi, pipeline CI, environment dev/test.

**Demo yang diharapkan:** pengguna dapat login sesuai role dan membuka daftar serta detail kos contoh.

**Risiko/dependensi:** keputusan autentikasi, struktur data listing, desain UI dasar.

### Sprint 2 — Pencarian dan filter
**Tujuan sprint:** pencari dapat menemukan listing sesuai kriteria.

Kandidat backlog:
- KOS-006 Pencarian kata kunci.
- KOS-007 Filter harga/lokasi/fasilitas.
- Pagination/empty state.
- Uji integrasi query dan keamanan input.

**Demo yang diharapkan:** pencari mencari kos dan menggabungkan beberapa filter.

**Risiko/dependensi:** definisi harga (per bulan/per minggu/per hari), normalisasi lokasi, struktur fasilitas.

### Sprint 3 — Fitur pemilik
**Tujuan sprint:** pemilik dapat membuat dan mengelola listing serta ketersediaan.

Kandidat backlog:
- KOS-008 Dashboard pemilik.
- KOS-009 Buat/ubah listing.
- KOS-010 Unggah foto.
- KOS-011 Kelola kamar/ketersediaan.
- KOS-020 audit perubahan penting versi awal.

**Demo yang diharapkan:** pemilik membuat listing, mengunggah foto, dan memperbarui status kamar.

**Risiko/dependensi:** object storage, batas ukuran/jenis file, kebijakan listing yang telah disetujui.

### Sprint 4 — Moderasi dan fitur pelengkap terpilih
**Tujuan sprint:** listing dapat dimoderasi dan fitur pelengkap prioritas tinggi mulai tersedia.

Kandidat backlog inti:
- KOS-012 Antrean verifikasi admin.
- KOS-013 Keputusan verifikasi.
- KOS-021 Logging/monitoring/backup dasar.
- KOS-022 responsif dan aksesibilitas dasar.

Fitur lanjutan jika kapasitas dan keputusan produk memungkinkan:
- KOS-014 peta lokasi.
- KOS-016 kontak/chat sederhana.
- KOS-017 dan KOS-018 ulasan/rating.

**Demo yang diharapkan:** admin memverifikasi listing dan hanya listing yang disetujui muncul di publik.

**Catatan penting:** materi presentasi awal menempatkan peta, chat, ulasan/rating, dan verifikasi admin pada Sprint 4. Karena ruang lingkup tersebut berpotensi besar, rekomendasi ini memprioritaskan verifikasi dan kesiapan operasional; fitur lain dapat dipindahkan ke sprint berikutnya jika belum siap.

## 3. Ritme Scrum per sprint
- **Sprint Planning:** sepakati Sprint Goal, pilih item sesuai kapasitas, uraikan task, dan identifikasi dependensi.
- **Daily Scrum:** 15 menit untuk memeriksa progres menuju Sprint Goal dan menyesuaikan rencana kerja.
- **Backlog Refinement:** lakukan selama sprint agar item mendatang lebih jelas.
- **Sprint Review:** demo increment yang berjalan, kumpulkan feedback, dan perbarui backlog.
- **Sprint Retrospective:** pilih 1–3 perbaikan proses yang dapat ditindaklanjuti sprint berikutnya.

## 4. Contoh task breakdown
Untuk KOS-009 (buat dan ubah listing):
- UX: wireframe/form dan state validasi.
- Backend: model dan migration.
- Backend: endpoint create/update dan validasi server.
- Authorization: cek pemilik listing.
- Frontend: form create/edit dan error state.
- QA: test validasi, role, ownership, dan regresi.
- Documentation: perbarui API/data model bila berubah.

## 5. Artefak Scrum
- Product Goal: membantu pencari menemukan kos dan pemilik mengelola informasi secara tepercaya.
- Product Backlog: `02-product-backlog.md`.
- Sprint Backlog: dipilih dan dirinci setiap Sprint Planning.
- Increment: hasil terintegrasi yang memenuhi Definition of Done.
- Definition of Done: `07-quality-and-testing.md`.

## 6. Pengukuran
Gunakan data untuk perbaikan, bukan sebagai target yang memicu perilaku tidak sehat:
- item selesai vs direncanakan;
- jumlah bug terbuka berdasarkan severity;
- waktu penyelesaian review;
- feedback stakeholder;
- alasan item tidak selesai;
- lead time dari item siap hingga selesai.

Jangan membandingkan velocity antar tim secara langsung. Gunakan velocity sebagai alat perencanaan internal setelah beberapa sprint.
