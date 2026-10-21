# Quality Plan, Testing, dan Definition of Done

## 1. Tujuan
Memastikan fitur sesuai acceptance criteria, data terlindungi, dan increment dapat didemokan tanpa menyembunyikan masalah penting.

## 2. Tingkat pengujian
- **Unit test:** validasi harga, aturan status listing, role/ownership, kalkulasi rating bila ada.
- **Integration test:** API dengan database, upload/storage, alur moderasi.
- **API contract test:** format request/response, status code, dan skema error.
- **End-to-end test:** alur pencari, pemilik, dan admin dari UI.
- **Security test:** autentikasi, otorisasi, IDOR, validasi upload, rate limiting, input injection, kebocoran rahasia.
- **Performance test:** pencarian/daftar/detail menggunakan dataset dan beban yang disepakati.
- **Usability test:** pengguna mencoba alur inti dari ponsel dan desktop.
- **Recovery test:** verifikasi backup dapat dipulihkan.

## 3. Skenario smoke test minimum
1. Pengunjung membuka daftar kos.
2. Pengunjung membuka detail listing yang disetujui.
3. Listing pending/rejected tidak tampil secara publik.
4. Pengguna membuat akun dan login.
5. Pemilik membuat listing dengan field wajib.
6. Pemilik mencoba mengubah listing milik akun lain — harus ditolak.
7. Pemilik mengunggah file valid; file tidak valid ditolak.
8. Admin melihat antrean dan menyetujui listing.
9. Listing yang disetujui muncul pada daftar publik.
10. Admin menolak listing dengan alasan; listing tidak tampil publik.
11. Filter harga/lokasi/fasilitas menghasilkan hasil yang sesuai.
12. Error server tidak mengungkap stack trace atau rahasia.
13. Health check dan logging dasar bekerja.
14. Backup database dapat dipulihkan ke lingkungan uji.

## 4. Definition of Ready (DoR)
Item siap diambil jika tujuan, acceptance criteria, dependensi, rancangan yang dibutuhkan, dan estimasi cukup jelas; item dapat diselesaikan atau telah dipecah sesuai kapasitas sprint.

## 5. Definition of Done (DoD)
Sebuah item dianggap selesai bila:
- Acceptance criteria terpenuhi.
- Code review dilakukan sesuai kebijakan tim.
- Unit/integration test relevan lulus.
- Tidak ada bug blocker/critical yang belum diselesaikan.
- Validasi dan otorisasi sisi server diterapkan.
- UI memiliki loading, empty, success, dan error state yang relevan.
- Dokumentasi API/data model diperbarui bila berubah.
- Tidak ada secret atau data sensitif yang masuk repository/log.
- Perubahan terintegrasi dan dapat diuji di lingkungan yang ditentukan.
- Demo atau bukti pengujian tersedia untuk Sprint Review.

## 6. Severity bug
- **Blocker:** fitur utama tidak dapat digunakan atau data/keamanan sangat terancam.
- **Critical:** kerusakan besar, kehilangan data, atau kontrol akses gagal.
- **Major:** fungsi penting rusak tanpa workaround yang layak.
- **Minor:** gangguan kecil dengan workaround.
- **Trivial:** perbaikan kosmetik.

Tim perlu menyepakati waktu respons dan aturan release berdasarkan severity.

## 7. Checklist sebelum pilot
- [ ] Semua alur MVP berhasil pada staging.
- [ ] Hak akses pencari/pemilik/admin diuji.
- [ ] Kebijakan listing publik dan moderasi diterapkan.
- [ ] Backup dan restore diuji.
- [ ] HTTPS dan konfigurasi rahasia benar.
- [ ] Log tidak berisi password, token, atau data sensitif.
- [ ] Alert dan kontak penanggung jawab tersedia.
- [ ] Prosedur rollback tersedia.
- [ ] Terms/privacy notice dan aturan penggunaan ditinjau pihak terkait.
- [ ] Stakeholder melakukan UAT dan menyetujui batasan MVP.
