# Outline API Awal

Dokumen ini adalah daftar kontrak endpoint untuk diskusi. Ini **bukan** spesifikasi final; nama endpoint, autentikasi, payload, pagination, dan format error perlu diselaraskan dengan framework dan model data.

Base path usulan: `/api/v1`

## 1. Konvensi
- JSON untuk request/response kecuali upload file.
- Gunakan HTTP status yang sesuai: `200`, `201`, `204`, `400`, `401`, `403`, `404`, `409`, `422`, `429`, `500`.
- Format error konsisten, misalnya `code`, `message`, `details`, `request_id`.
- Endpoint privat harus memeriksa autentikasi, role, dan ownership.
- Pagination memakai konvensi yang dipilih tim (`page/limit` atau cursor).
- Filter hanya menerima parameter yang didukung; validasi batas harga dan input.

## 2. Akun
| Method | Endpoint | Akses | Tujuan |
|---|---|---|---|
| POST | `/auth/register` | Publik | Membuat akun |
| POST | `/auth/login` | Publik | Login |
| POST | `/auth/logout` | Pengguna login | Logout |
| GET | `/users/me` | Pengguna login | Profil pengguna saat ini |
| PATCH | `/users/me` | Pengguna login | Memperbarui profil yang diizinkan |

Jika menggunakan penyedia identitas eksternal, endpoint register/login lokal mungkin tidak diperlukan.

## 3. Pencarian dan listing publik
| Method | Endpoint | Akses | Tujuan |
|---|---|---|---|
| GET | `/properties` | Publik | Daftar listing yang disetujui |
| GET | `/properties/{propertyId}` | Publik | Detail listing yang disetujui |
| GET | `/facilities` | Publik | Katalog fasilitas filter |

Parameter pencarian usulan:
- `q`: kata kunci.
- `min_price`, `max_price`: rentang harga.
- `area`: lokasi/area.
- `facility_ids`: fasilitas yang harus tersedia.
- `page`, `limit`: pagination.
- `sort`: opsi sort yang diizinkan.

Jangan menerima nama kolom SQL mentah dari parameter `sort`.

## 4. Pemilik
| Method | Endpoint | Akses | Tujuan |
|---|---|---|---|
| GET | `/owner/properties` | Pemilik | Listing milik sendiri |
| POST | `/owner/properties` | Pemilik | Membuat listing |
| PATCH | `/owner/properties/{propertyId}` | Pemilik pemilik tersebut | Mengubah listing |
| POST | `/owner/properties/{propertyId}/photos` | Pemilik pemilik tersebut | Mengunggah foto |
| DELETE | `/owner/properties/{propertyId}/photos/{photoId}` | Pemilik pemilik tersebut | Menghapus foto |
| POST | `/owner/properties/{propertyId}/rooms` | Pemilik pemilik tersebut | Menambah kamar/tipe kamar |
| PATCH | `/owner/properties/{propertyId}/rooms/{roomId}` | Pemilik pemilik tersebut | Mengubah kamar/ketersediaan |
| POST | `/owner/properties/{propertyId}/submit-review` | Pemilik pemilik tersebut | Mengirim listing untuk verifikasi |

Server harus memeriksa bahwa listing dan kamar terkait benar-benar dimiliki pengguna.

## 5. Admin dan moderasi
| Method | Endpoint | Akses | Tujuan |
|---|---|---|---|
| GET | `/admin/properties?status=pending_review` | Admin | Antrean moderasi |
| POST | `/admin/properties/{propertyId}/approve` | Admin | Menyetujui listing |
| POST | `/admin/properties/{propertyId}/reject` | Admin | Menolak listing dengan alasan |
| POST | `/admin/properties/{propertyId}/request-revision` | Admin | Meminta perbaikan |

Semua keputusan harus mencatat aktor, waktu, status sebelumnya/baru, dan alasan bila relevan.

## 6. Fitur lanjutan
### Lokasi
- `GET /properties/{propertyId}/location`
- Integrasi peta/geocoding bergantung pada provider yang dipilih dan aturan biaya/privasi.

### Chat internal (opsional)
- `POST /conversations`
- `GET /conversations`
- `GET /conversations/{conversationId}/messages`
- `POST /conversations/{conversationId}/messages`

Setiap operasi wajib memastikan pengguna adalah anggota percakapan. Perlu pembatasan spam, moderasi, dan kebijakan retensi.

### Ulasan (opsional)
- `GET /properties/{propertyId}/reviews`
- `POST /properties/{propertyId}/reviews`
- `PATCH /reviews/{reviewId}` jika edit diizinkan.
- `POST /reviews/{reviewId}/report` jika pelaporan diimplementasikan.

## 7. Contoh respons daftar (ilustratif)
```json
{
  "data": [
    {
      "id": "property-id",
      "name": "Kos Melati",
      "price": {
        "amount": 1200000,
        "currency": "IDR",
        "period": "month"
      },
      "area": "Area contoh",
      "availableRooms": 2,
      "thumbnailUrl": "https://storage.example/photo.jpg"
    }
  ],
  "pagination": {
    "page": 1,
    "limit": 20,
    "total": 1
  }
}
```

## 8. Hal yang perlu diputuskan
- Session cookie atau bearer token.
- Format error baku.
- Pagination dan sorting.
- Batas request dan upload.
- Apakah API publik boleh diakses tanpa login.
- Apakah kontak pemilik berupa data publik, link eksternal, atau chat internal.
- Apakah endpoint admin menggunakan role internal atau identity provider.
