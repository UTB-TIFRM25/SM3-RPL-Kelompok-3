# Product Backlog — Aplikasi Kos-kosan Online

**Status:** draft awal untuk refinement  
**Prioritas:** P0 = wajib untuk MVP, P1 = penting setelah alur inti, P2 = lanjutan  
**Estimasi:** story point belum diisi; tim perlu memperkirakan bersama. Urutan adalah usulan, bukan komitmen.

## Cara membaca backlog
Setiap item berisi ID, user story, prioritas, dependensi, dan acceptance criteria. Acceptance criteria menggunakan bahasa yang dapat diuji. Item dapat dipecah menjadi task teknis saat Sprint Planning.

## Epic dan backlog

### EPIC E01 — Akun dan akses

#### KOS-001 — Registrasi pengguna
- **Prioritas:** P0
- **Story:** Sebagai pengguna, saya ingin membuat akun agar dapat menggunakan fitur yang memerlukan identitas.
- **Acceptance criteria:**
  - Pengguna dapat mengisi field yang telah disepakati dan mengirim formulir.
  - Email/identitas unik yang sudah terdaftar ditolak dengan pesan yang jelas.
  - Input tidak valid menampilkan pesan validasi.
  - Password tidak disimpan dalam bentuk plaintext.
  - Setelah berhasil, pengguna menerima konfirmasi dan dapat login.
- **Dependensi:** keputusan field akun dan mekanisme verifikasi.

#### KOS-002 — Login dan logout
- **Prioritas:** P0
- **Story:** Sebagai pengguna terdaftar, saya ingin login dan logout dengan aman.
- **Acceptance criteria:**
  - Kredensial valid menghasilkan sesi/token yang valid.
  - Kredensial salah tidak mengungkap apakah akun tertentu terdaftar.
  - Pengguna dapat logout dan sesi/token terkait tidak lagi dapat digunakan sesuai mekanisme autentikasi.
  - Endpoint privat menolak request tanpa autentikasi.

#### KOS-003 — Role dan otorisasi
- **Prioritas:** P0
- **Story:** Sebagai sistem, saya ingin membatasi akses berdasarkan role pencari, pemilik, dan admin.
- **Acceptance criteria:**
  - Hak akses diperiksa di server, bukan hanya disembunyikan di UI.
  - Pemilik tidak dapat mengubah listing milik pemilik lain.
  - Admin memiliki akses moderasi sesuai kebijakan.
  - Akses yang ditolak menghasilkan respons yang sesuai dan tercatat bila relevan.

### EPIC E02 — Penemuan dan detail kos

#### KOS-004 — Daftar kos publik
- **Prioritas:** P0
- **Story:** Sebagai pencari kos, saya ingin melihat daftar kos yang tersedia agar dapat menemukan pilihan hunian.
- **Acceptance criteria:**
  - Hanya listing dengan status publik/disetujui yang muncul.
  - Setiap kartu menampilkan informasi ringkas yang telah disepakati.
  - Daftar mendukung pagination atau mekanisme pemuatan bertahap.
  - Empty state dan error state ditampilkan dengan jelas.

#### KOS-005 — Halaman detail kos
- **Prioritas:** P0
- **Story:** Sebagai pencari kos, saya ingin melihat detail kos sebelum menghubungi pemilik.
- **Acceptance criteria:**
  - Detail menampilkan nama, deskripsi, harga, fasilitas, lokasi, foto, status/ketersediaan, dan waktu pembaruan jika tersedia.
  - Listing yang tidak publik tidak dapat diakses melalui endpoint publik.
  - Data yang belum diisi ditampilkan secara wajar dan tidak merusak layout.

#### KOS-006 — Pencarian kata kunci
- **Prioritas:** P0
- **Story:** Sebagai pencari kos, saya ingin mencari kos menggunakan kata kunci.
- **Acceptance criteria:**
  - Pencarian menerima kata kunci yang ditentukan tim (mis. nama kos atau area).
  - Pencarian tanpa hasil menampilkan empty state.
  - Input dibatasi dan diproses aman; tidak membentuk query SQL mentah dari input pengguna.

#### KOS-007 — Filter harga, lokasi, fasilitas
- **Prioritas:** P0
- **Story:** Sebagai pencari kos, saya ingin mempersempit hasil berdasarkan harga, lokasi, dan fasilitas.
- **Acceptance criteria:**
  - Pengguna dapat menggabungkan filter yang didukung.
  - Rentang harga yang tidak valid ditolak atau dinormalisasi dengan aturan yang jelas.
  - Hasil sesuai dengan semua filter aktif.
  - Pengguna dapat menghapus filter dan kembali ke daftar awal.

### EPIC E03 — Pengelolaan listing oleh pemilik

#### KOS-008 — Dashboard pemilik
- **Prioritas:** P0
- **Story:** Sebagai pemilik, saya ingin melihat listing yang saya kelola beserta statusnya.
- **Acceptance criteria:**
  - Dashboard hanya menampilkan listing yang dimiliki akun tersebut.
  - Status draft, menunggu verifikasi, disetujui, ditolak/revisi terlihat jelas.
  - Pemilik dapat membuka form untuk membuat atau memperbarui listing.

#### KOS-009 — Buat dan ubah listing
- **Prioritas:** P0
- **Story:** Sebagai pemilik, saya ingin membuat dan memperbarui informasi kos.
- **Acceptance criteria:**
  - Form memvalidasi field wajib.
  - Listing baru masuk status draft atau menunggu verifikasi sesuai alur yang disepakati.
  - Perubahan pada listing yang sudah disetujui memicu aturan re-verifikasi jika diperlukan.
  - Pemilik tidak dapat mengubah listing milik orang lain.
  - Sistem menyimpan waktu pembuatan dan pembaruan.

#### KOS-010 — Unggah foto
- **Prioritas:** P0
- **Story:** Sebagai pemilik, saya ingin mengunggah foto agar calon penghuni dapat melihat kondisi kos.
- **Acceptance criteria:**
  - Tipe file dan ukuran maksimum dibatasi dan dikonfigurasi.
  - File disimpan pada storage yang sesuai, bukan sebagai file arbitrer di web root.
  - Foto dapat ditampilkan di halaman detail.
  - Penghapusan/perubahan foto hanya diizinkan kepada pemilik atau admin yang berwenang.

#### KOS-011 — Kelola kamar dan ketersediaan
- **Prioritas:** P0
- **Story:** Sebagai pemilik, saya ingin memperbarui jumlah kamar dan ketersediaannya.
- **Acceptance criteria:**
  - Pemilik dapat menambah/mengubah informasi kamar sesuai model yang disepakati.
  - Nilai jumlah kamar tidak boleh negatif.
  - Perubahan ketersediaan tersimpan dan tercermin pada detail publik setelah aturan publikasi terpenuhi.
  - Sistem mencatat waktu pembaruan.

### EPIC E04 — Moderasi admin

#### KOS-012 — Antrean verifikasi listing
- **Prioritas:** P0
- **Story:** Sebagai admin, saya ingin melihat listing yang menunggu verifikasi.
- **Acceptance criteria:**
  - Admin dapat memfilter listing berdasarkan status.
  - Detail yang diperlukan untuk moderasi dapat dilihat.
  - Pengguna non-admin tidak dapat mengakses antrean.

#### KOS-013 — Setujui, tolak, atau minta revisi
- **Prioritas:** P0
- **Story:** Sebagai admin, saya ingin mengambil keputusan atas listing agar informasi publik lebih tepercaya.
- **Acceptance criteria:**
  - Admin dapat memilih keputusan yang disepakati.
  - Penolakan/revisi wajib memiliki alasan.
  - Status, aktor, dan waktu keputusan tercatat.
  - Listing yang belum disetujui tidak tampil di daftar publik.

### EPIC E05 — Lokasi dan komunikasi

#### KOS-014 — Peta lokasi
- **Prioritas:** P1
- **Story:** Sebagai pencari kos, saya ingin melihat posisi kos di peta.
- **Acceptance criteria:**
  - Peta menampilkan koordinat yang tersimpan pada listing.
  - Jika koordinat belum ada, UI memberi informasi yang sesuai.
  - Provider peta, biaya, kuota, dan kebijakan privasi telah diputuskan sebelum rilis.

#### KOS-015 — Jarak ke kampus
- **Prioritas:** P1
- **Story:** Sebagai mahasiswa, saya ingin memperkirakan jarak kos ke kampus.
- **Acceptance criteria:**
  - Pengguna dapat memilih/menentukan kampus referensi jika fitur ini didukung.
  - Sistem menjelaskan apakah angka menunjukkan jarak garis lurus atau rute.
  - Hasil tidak ditampilkan jika data lokasi tidak memadai.

#### KOS-016 — Hubungi pemilik / chat
- **Prioritas:** P1
- **Story:** Sebagai pencari kos, saya ingin menghubungi pemilik untuk bertanya.
- **Acceptance criteria:**
  - Hanya kontak yang disetujui untuk ditampilkan yang tersedia.
  - Jika berupa chat internal, hanya pihak yang terlibat dapat membaca percakapan.
  - Jika berupa tautan/nomor kontak eksternal, pengguna diberi tahu bahwa komunikasi terjadi di luar aplikasi.
- **Catatan:** putuskan apakah MVP memakai kontak langsung sederhana atau chat internal.

### EPIC E06 — Ulasan dan rating

#### KOS-017 — Beri ulasan dan rating
- **Prioritas:** P1
- **Story:** Sebagai penghuni yang memenuhi syarat, saya ingin memberi ulasan agar pengguna lain mendapat gambaran pengalaman tinggal.
- **Acceptance criteria:**
  - Skala rating dan aturan panjang ulasan ditetapkan.
  - Pengguna hanya dapat mengulas sesuai kebijakan kelayakan yang disepakati.
  - Pengguna tidak dapat mengirim ulasan duplikat untuk pengalaman yang sama.
  - Ulasan dapat dimoderasi dan dilaporkan sesuai kebijakan.

#### KOS-018 — Tampilkan ulasan dan rating
- **Prioritas:** P1
- **Story:** Sebagai pencari kos, saya ingin membaca ulasan yang relevan sebelum memilih kos.
- **Acceptance criteria:**
  - Rating agregat dihitung konsisten.
  - Ulasan yang dihapus/disembunyikan sesuai kebijakan tidak tampil.
  - UI menampilkan kondisi jika belum ada ulasan.

### EPIC E07 — Fondasi produk dan operasional

#### KOS-019 — Validasi input dan penanganan error
- **Prioritas:** P0
- **Story:** Sebagai pengguna, saya ingin mendapat pesan error yang jelas ketika input atau permintaan gagal.
- **Acceptance criteria:** validasi sisi server tersedia; respons tidak membocorkan stack trace; error memiliki ID korelasi/log jika relevan.

#### KOS-020 — Audit perubahan penting
- **Prioritas:** P0
- **Story:** Sebagai admin/operator, saya ingin mengetahui siapa yang mengubah status listing.
- **Acceptance criteria:** perubahan status moderasi mencatat aktor, waktu, status lama/baru, dan alasan bila ada; log tidak menyimpan password/token.

#### KOS-021 — Logging, monitoring, dan backup dasar
- **Prioritas:** P0 sebelum pilot produksi
- **Story:** Sebagai operator, saya ingin mengetahui kondisi aplikasi dan memulihkan data jika terjadi kegagalan.
- **Acceptance criteria:** health check tersedia; error penting tercatat; backup database diuji pemulihannya; prosedur operasi dasar didokumentasikan.

#### KOS-022 — Responsif dan aksesibilitas dasar
- **Prioritas:** P0
- **Story:** Sebagai pengguna ponsel, saya ingin menggunakan alur utama tanpa kesulitan.
- **Acceptance criteria:** layout diuji pada viewport mobile dan desktop; form memiliki label; fokus keyboard terlihat; gambar memiliki alt text yang sesuai.

## Urutan prioritas rekomendasi
1. Fondasi akun, role, dan keamanan.
2. Daftar/detail/pencarian/filter.
3. Dashboard pemilik, listing, foto, kamar.
4. Verifikasi admin.
5. Observability, backup, hardening sebelum pilot.
6. Peta, chat, ulasan/rating setelah keputusan produk dan risiko jelas.

## Definition of Ready (DoR) — usulan
Sebuah item siap masuk sprint jika:
- Tujuan dan pengguna jelas.
- Acceptance criteria dapat diuji.
- Dependensi utama diketahui.
- Desain/API/data yang dibutuhkan cukup jelas.
- Tim memahami item dan sudah memberi estimasi.
- Item cukup kecil untuk selesai dalam satu sprint atau telah dipecah.

## Catatan
Backlog ini belum memiliki story point karena estimasi sebaiknya dilakukan oleh tim pelaksana. Product Owner dapat mengubah urutan prioritas berdasarkan hasil riset dan Sprint Review.
