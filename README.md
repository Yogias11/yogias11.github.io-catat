# Catat Pengeluaran — PWA + Google Sheets

Aplikasi pencatat pengeluaran harian untuk iPhone, terhubung langsung ke Google Sheets.

---

## File yang disertakan

| File | Fungsi |
|------|--------|
| `index.html` | Aplikasi utama (PWA) |
| `sw.js` | Service worker (offline support) |
| `manifest.json` | Metadata PWA untuk iPhone |
| `Code.gs` | Google Apps Script (API backend) |

---

## LANGKAH 1 — Setup Google Apps Script

1. Buka file **Google Sheets keuangan** Anda
2. Klik menu **Extensions → Apps Script**
3. Hapus semua kode yang ada di editor
4. Buka file `Code.gs` dari paket ini, **copy semua isinya**, paste ke editor Apps Script
5. Klik **Save** (ikon disket atau Ctrl+S)
6. Klik **Deploy → New Deployment**
7. Klik ikon ⚙️ di samping "Select type" → pilih **Web app**
8. Isi pengaturan:
   - Description: `Catat Pengeluaran API`
   - Execute as: **Me**
   - Who has access: **Anyone**
9. Klik **Deploy**
10. Klik **Authorize access** jika diminta (pilih akun Google Anda)
11. Copy **URL** yang muncul — formatnya:
    `https://script.google.com/macros/s/AKfycb.../exec`

> ⚠️ Simpan URL ini baik-baik, dibutuhkan di langkah berikutnya.

---

## LANGKAH 2 — Hosting Aplikasi (GitHub Pages, GRATIS)

### Cara paling mudah:

1. Buat akun di [github.com](https://github.com) jika belum punya
2. Klik **New repository**, beri nama misalnya `catat-pengeluaran`
3. Centang "Add a README file", klik **Create repository**
4. Upload semua file (`index.html`, `sw.js`, `manifest.json`) ke repository:
   - Klik **Add file → Upload files**
   - Drag & drop ketiga file
   - Klik **Commit changes**
5. Klik **Settings → Pages**
6. Source: pilih **Deploy from a branch**
7. Branch: pilih **main**, folder: **/ (root)**
8. Klik **Save**
9. Tunggu 1-2 menit, URL aplikasi Anda akan muncul:
   `https://username.github.io/catat-pengeluaran/`

### Alternatif hosting lain:
- **Netlify** — drag & drop folder ke [netlify.com/drop](https://app.netlify.com/drop)
- **Vercel** — upload via [vercel.com](https://vercel.com)

---

## LANGKAH 3 — Install di iPhone (Add to Home Screen)

1. Buka Safari di iPhone (wajib Safari, bukan Chrome)
2. Kunjungi URL aplikasi Anda (dari GitHub Pages)
3. Tap ikon **Share** (kotak dengan panah ke atas) di bawah layar
4. Scroll ke bawah, tap **"Add to Home Screen"**
5. Beri nama "Catat", tap **Add**
6. Aplikasi kini muncul di home screen seperti app biasa!

---

## LANGKAH 4 — Hubungkan ke Google Sheets

1. Buka aplikasi dari home screen iPhone
2. Tap tab **Pengaturan** (ikon gear, paling kanan)
3. Paste URL Apps Script dari Langkah 1 ke kolom URL
4. Tap **Simpan URL**
5. Status akan berubah menjadi ✅ **Terhubung**

---

## Cara Pakai Sehari-hari

1. Buka aplikasi dari home screen
2. Ketuk angka di numpad → jumlah muncul besar di atas
3. Pilih **kategori** (chip di bawah numpad)
4. Isi keterangan (opsional)
5. Pastikan tanggal sudah benar
6. Pilih dibayar oleh siapa (Suami / Istri / Bersama)
7. Tap **Simpan ke Google Sheets**
8. Data langsung muncul di sheet "Catatan Pengeluaran"!

---

## Fitur Offline

Jika tidak ada internet saat mencatat:
- Data tersimpan di antrian lokal di HP
- Saat internet kembali, antrian otomatis terkirim
- Bisa juga kirim manual via **Pengaturan → Kirim Ulang Antrian**

---

## Troubleshooting

| Masalah | Solusi |
|---------|--------|
| Status "Gagal terhubung" | Pastikan URL Apps Script sudah benar dan akses "Anyone" |
| Data tidak masuk sheet | Cek nama sheet harus persis `Catatan Pengeluaran` |
| Tombol Add to Home Screen tidak muncul | Pastikan pakai Safari, bukan Chrome atau browser lain |
| URL Apps Script expired | Re-deploy di Apps Script → New Deployment |

---

## Catatan Keamanan

- URL Apps Script bersifat semi-privat (hanya yang punya URL bisa akses)
- Data dikirim langsung ke Google Sheet milik Anda
- Tidak ada server pihak ketiga yang menyimpan data Anda
