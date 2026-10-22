# Product Requirements Document (PRD)
## Aplikasi Kostara

- **Status:** Draft untuk validasi
- **Versi:** 0.1
- **Pemilik produk:** belum ditetapkan
- **Stakeholder utama:** pencari kos, pemilik kos, admin
- **Metode pengembangan:** Scrum dengan sprint awal 1–2 minggu

## 1. Ringkasan produk
Aplikasi Kostara adalah platform yang membantu pencari kos menemukan hunian berdasarkan informasi harga, lokasi, fasilitas, foto, dan ketersediaan kamar. Pemilik kos dapat mengelola informasi kos dan kamar, sedangkan admin memverifikasi data kos agar informasi yang tampil lebih dapat dipercaya.

## 2. Latar belakang masalah
Materi awal mengidentifikasi masalah berikut:
- Pencari kos masih perlu berkeliling atau mengandalkan rekomendasi dari mulut ke mulut.
- Harga, fasilitas, dan ketersediaan kamar tidak selalu jelas atau sudah kedaluwarsa.
- Pemilik kos kesulitan menjangkau calon penghuni.

## 3. Visi dan tujuan
**Visi:** mempermudah pencari kos menemukan tempat tinggal dan membantu pemilik menjangkau calon penghuni melalui informasi yang terstruktur.

**Tujuan produk:**
1. Menyediakan informasi kos yang lengkap dan relatif terkini.
2. Memudahkan pencarian kos berdasarkan harga, lokasi, dan fasilitas.
3. Menampilkan detail kos, foto, lokasi, dan ketersediaan kamar.
4. Memberikan kanal komunikasi langsung antara pencari dan pemilik.
5. Memungkinkan pemilik mengelola listing dan kamar.
6. Memungkinkan admin memverifikasi listing.

## 4. Pengguna dan kebutuhan

### 4.1 Pencari kos
- Mencari kos berdasarkan kriteria tertentu.
- Membandingkan harga, fasilitas, dan lokasi.
- Melihat foto dan informasi kamar tersedia.
- Menghubungi pemilik.
- Memberikan ulasan/rating sesuai kebijakan yang akan ditetapkan.

### 4.2 Pemilik kos
- Membuat dan memperbarui profil/listing kos.
- Mengunggah foto.
- Mengelola informasi kamar dan ketersediaannya.
- Menanggapi pertanyaan calon penghuni.

### 4.3 Admin
- Meninjau listing yang diajukan.
- Menyetujui, menolak, atau meminta perbaikan data.
- Menangani laporan listing yang tidak akurat atau melanggar kebijakan (fitur ini perlu disepakati lebih lanjut).

## 5. Ruang lingkup

### 5.1 Fitur inti untuk MVP
- Registrasi dan login.
- Daftar kos dan halaman detail.
- Pencarian dan filter harga, lokasi, serta fasilitas.
- Dashboard pemilik untuk mengelola listing.
- Unggah foto kos.
- Informasi jumlah/ketersediaan kamar.
- Verifikasi listing oleh admin.

### 5.2 Fitur lanjutan dalam rencana awal
- Peta lokasi dan informasi jarak ke kampus.
- Chat dengan pemilik.
- Ulasan dan rating dari penghuni sebelumnya.

Presentasi awal membagi fitur ke empat sprint. Pembagian ini adalah baseline awal; prioritas dan kapasitas harus divalidasi sebelum komitmen sprint.

### 5.3 Di luar ruang lingkup MVP (usulan)
- Pembayaran sewa di dalam aplikasi.
- Penandatanganan kontrak digital.
- Pemeriksaan identitas otomatis.
- Rekomendasi berbasis machine learning.
- Aplikasi native Android/iOS terpisah.
- Integrasi pihak ketiga untuk pembayaran atau pemetaan berbayar.

Item di atas bukan kebutuhan yang dikonfirmasi dan tidak boleh dikerjakan tanpa keputusan Product Owner.

## 6. Alur pengguna utama

### 6.1 Pencari kos
1. Membuka aplikasi.
2. Melihat daftar kos yang sudah dipublikasikan dan disetujui.
3. Mengisi kata kunci/filter.
4. Membuka detail kos.
5. Melihat foto, harga, fasilitas, lokasi, dan ketersediaan.
6. Menghubungi pemilik melalui kanal yang tersedia.
7. Jika memenuhi syarat, memberi ulasan setelah tinggal (aturan verifikasi perlu ditentukan).

### 6.2 Pemilik kos
1. Mendaftar dan login.
2. Membuka dashboard pemilik.
3. Membuat listing kos dan melengkapi informasi.
4. Mengunggah foto dan memasukkan data kamar.
5. Mengirim listing untuk verifikasi.
6. Memperbaiki data jika ditolak/diminta revisi.
7. Memperbarui ketersediaan kamar secara berkala.

### 6.3 Admin
1. Login dengan akun admin.
2. Melihat antrean listing yang menunggu verifikasi.
3. Meninjau kelengkapan dan kepatuhan data.
4. Menyetujui, menolak, atau meminta perbaikan.
5. Sistem mencatat status dan waktu perubahan.

## 7. Kebutuhan fungsional

| ID | Kebutuhan | Prioritas awal |
|---|---|---|
| FR-01 | Pengguna dapat registrasi dan login | Must |
| FR-02 | Pengunjung dapat melihat daftar kos yang dipublikasikan | Must |
| FR-03 | Pengunjung dapat membuka detail kos | Must |
| FR-04 | Pengunjung dapat mencari dan memfilter kos menurut harga, lokasi, fasilitas | Must |
| FR-05 | Pemilik dapat membuat, mengubah, dan mengarsipkan listing miliknya | Must |
| FR-06 | Pemilik dapat mengunggah foto kos | Must |
| FR-07 | Pemilik dapat mengelola informasi dan ketersediaan kamar | Must |
| FR-08 | Admin dapat menyetujui/menolak/meminta revisi listing | Must |
| FR-09 | Pencari dapat melihat lokasi kos di peta dan jarak ke kampus | Should |
| FR-10 | Pencari dan pemilik dapat berkomunikasi melalui chat | Should |
| FR-11 | Pengguna yang memenuhi syarat dapat memberi ulasan dan rating | Should |
| FR-12 | Sistem menampilkan status verifikasi listing | Must |

## 8. Kebutuhan nonfungsional awal
Angka target di bawah adalah **usulan untuk dibahas**, bukan SLA yang sudah disepakati.

- **Keamanan:** password disimpan dengan hashing yang aman; endpoint privat memerlukan autentikasi; role dan kepemilikan data diperiksa di sisi server.
- **Privasi:** jangan menampilkan data pribadi yang tidak dibutuhkan; tentukan persetujuan dan retensi data.
- **Performa:** usulan p95 API baca utama ≤ 800 ms pada beban uji yang disepakati, tidak termasuk layanan pihak ketiga.
- **Ketersediaan:** target awal MVP ditentukan setelah pilihan hosting dan kebutuhan bisnis disepakati.
- **Usability:** form memberi pesan validasi yang jelas; halaman detail dapat digunakan dari layar ponsel.
- **Aksesibilitas:** navigasi dasar dapat dilakukan dengan keyboard dan komponen memiliki label yang jelas.
- **Maintainability:** source code menggunakan review, test otomatis, dan konfigurasi per environment.
- **Observability:** log terstruktur untuk error penting; metrik untuk latency, error rate, dan status layanan.
- **Backup/recovery:** tentukan frekuensi backup dan target RPO/RTO sebelum produksi.

## 9. Aturan bisnis awal
1. Listing hanya tampil publik setelah disetujui admin.
2. Pemilik hanya dapat mengubah listing yang menjadi miliknya.
3. Listing minimal memiliki nama, alamat/lokasi, harga, fasilitas, dan deskripsi.
4. Status ketersediaan harus memiliki definisi yang jelas, misalnya tersedia, penuh, atau tidak aktif.
5. Ulasan tidak boleh dibuat berkali-kali untuk transaksi/pengalaman yang sama; mekanisme verifikasi perlu disepakati.
6. Penolakan listing harus memiliki alasan agar pemilik dapat memperbaiki data.

Aturan 1–6 perlu dikonfirmasi oleh Product Owner dan stakeholder.

## 10. Metrik keberhasilan awal
Tetapkan baseline dan target numerik setelah pilot. Metrik yang disarankan:
- Jumlah listing aktif yang sudah diverifikasi.
- Persentase listing dengan data wajib lengkap.
- Persentase listing yang diperbarui dalam periode yang ditetapkan.
- Jumlah pencarian yang menghasilkan pembukaan halaman detail.
- Jumlah kontak antara pencari dan pemilik.
- Waktu median dari pengajuan listing hingga keputusan admin.
- Jumlah laporan terkait informasi tidak akurat.

## 11. Risiko dan mitigasi
| Risiko | Dampak | Mitigasi awal |
|---|---|---|
| Informasi ketersediaan tidak diperbarui | Pengguna kecewa | Tampilkan waktu pembaruan terakhir dan ingatkan pemilik |
| Listing palsu/tidak akurat | Kepercayaan turun | Moderasi admin, pelaporan, audit perubahan |
| Ruang lingkup melebar | MVP terlambat | Prioritaskan backlog dan gunakan change review |
| Data foto besar | Performa/biaya meningkat | Batasi ukuran, kompresi, object storage |
| Chat menjadi kompleks | Jadwal dan keamanan bertambah | Putuskan MVP chat sederhana vs tautan kontak |
| Ulasan palsu | Rating tidak tepercaya | Tetapkan aturan kelayakan ulasan sebelum implementasi |

## 12. Kriteria penerimaan produk
MVP dapat dipertimbangkan siap pilot ketika:
- Alur pencari melihat, mencari, memfilter, dan membuka detail kos berjalan.
- Pemilik dapat mengelola listing, foto, dan ketersediaan.
- Admin dapat memoderasi listing.
- Kontrol akses diuji untuk tiap role.
- Tidak ada bug blocker/critical yang diketahui.
- Backup, monitoring, dan prosedur penanganan insiden dasar tersedia.
- Stakeholder menerima hasil Sprint Review/UAT dan menyetujui batasan MVP.

## 13. Referensi dan catatan
Dokumen ini diturunkan dari materi presentasi “Aplikasi Kostara — Metode Scrum”. Detail nonfungsional, aturan bisnis, dan metrik yang tidak ada di materi ditandai sebagai usulan untuk divalidasi.
