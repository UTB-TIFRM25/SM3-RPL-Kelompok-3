# Dokumentasi Pengembangan — Kostara

Dokumentasi awal untuk pengembangan **Aplikasi Kostara** menggunakan pendekatan Scrum. Dokumen ini menjadi acuan bersama Product Owner, Scrum Master, developer, QA, UI/UX, dan stakeholder.

## Tujuan produk

Mempertemukan pencari kos dan pemilik kos melalui informasi kos yang lengkap dan terkini, pencarian yang mudah, serta sarana pengelolaan data kos dan kamar.

## Paket dokumen

| Dokumen                                                                 | Kegunaan                                                                 |
| ----------------------------------------------------------------------- | ------------------------------------------------------------------------ |
| [01-product-requirements.md](01-product-requirements.md)                 | PRD: tujuan, pengguna, ruang lingkup, kebutuhan, dan metrik keberhasilan |
| [02-product-backlog.md](02-product-backlog.md)                           | Product Backlog terurut dengan user story dan acceptance criteria        |
| [03-sprint-roadmap.md](03-sprint-roadmap.md)                             | Rencana awal empat sprint dan aktivitas Scrum                            |
| [04-architecture-overview.md](04-architecture-overview.md)               | Gambaran arsitektur awal dan pertimbangan teknis                         |
| [05-data-model.md](05-data-model.md)                                     | Entitas data dan relasi awal                                             |
| [06-api-outline.md](06-api-outline.md)                                   | Kontrak API awal untuk diskusi tim                                       |
| [07-quality-and-testing.md](07-quality-and-testing.md)                   | Quality plan, strategi pengujian, dan Definition of Done                 |
| [08-decisions-and-open-questions.md](08-decisions-and-open-questions.md) | Asumsi, keputusan yang perlu disepakati, risiko, dan pertanyaan terbuka  |

## Cara menggunakan

1. Product Owner dan stakeholder meninjau PRD serta pertanyaan terbuka.
2. Tim memperkirakan dan memprioritaskan backlog saat refinement.
3. Pada Sprint Planning, pilih item yang memenuhi kriteria kesiapan dan sesuai kapasitas tim.
4. Acceptance criteria menjadi dasar implementasi dan pengujian.
5. Setelah Sprint Review, perbarui backlog dan dokumen jika ada perubahan yang disepakati.

## Status dokumen

- Status: **Draft awal — perlu validasi stakeholder**
- Versi: 0.1
- Tanggal: 2026-10-21
- Dasar: materi presentasi “Aplikasi Kos-kosan Online — Metode Scrum”.
- Catatan: detail teknis, kebijakan bisnis, dan angka target yang tidak disebutkan dalam presentasi ditulis sebagai usulan/asumsi, bukan keputusan final.

## Prinsip pengelolaan dokumen

- Perubahan ruang lingkup harus tercermin pada PRD dan Product Backlog.
- Jangan menganggap estimasi sprint sebagai komitmen tanggal rilis sebelum kapasitas dan dependensi divalidasi.
- Keputusan penting dicatat di `08-decisions-and-open-questions.md`.
