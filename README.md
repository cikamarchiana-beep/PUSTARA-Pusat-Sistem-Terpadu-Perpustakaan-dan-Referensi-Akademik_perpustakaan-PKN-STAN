> **VERSI PERBAIKAN TERBARU (8 Oktober 2026):** Dark mode & kontras diperbaiki di seluruh role, katalog tidak menumpuk, mobile sidebar dan form filter diperbaiki. Lihat `docs/PERBAIKAN_TERBARU.md`. Untuk memperbarui situs Vercel yang sudah ada, **replace isi repository lama dengan isi ZIP ini, lalu push commit** (atau jalankan `npx vercel --prod` dari root folder). Jangan menghapus konfigurasi domain proyek.

# PUSTARA — Paket Siap Deploy ke Vercel

Paket ini mempertahankan UI PUSTARA dari satu file HTML asli. Semua maskot, sticker, achievement, dan gambar utama **sudah tertanam langsung dalam `index.html`**. Folder `assets/` hanya untuk favicon, ikon web, dan logo tambahan. Tidak ada build dependency atau framework yang perlu diinstal.

## Isi ZIP

- `index.html` — aplikasi utama (HTML, CSS, JavaScript, aset visual tertanam).
- `vercel.json` — konfigurasi proyek statis Vercel dan header dasar.
- `assets/` — favicon, ikon 192px/512px, dan logo PUSTARA.
- `site.webmanifest` — metadata ikon situs, tanpa service worker atau cache offline yang berisiko kedaluwarsa.
- `docs/QA-CHECKLIST.md` — pemeriksaan manual setelah deploy.
- `docs/PRODUCTION-READINESS.md` — batasan teknis dan langkah menuju aplikasi sungguhan.

## Cara deploy melalui GitHub dan Vercel

1. **Ekstrak ZIP** di komputer. Pastikan `index.html` dan `vercel.json` berada di root folder proyek.
2. Buat repository GitHub, unggah **isi folder** `PUSTARA_Vercel_Ready/` ke root repository.
3. Buka Vercel → **Add New Project** → impor repository tersebut.
4. Pilih framework **Other** / no framework. Root Directory: `./`. Tidak perlu build command atau install command.
5. Deploy, lalu akses domain yang diberikan Vercel. Halaman utama berada di `/`.

Alternatif via Vercel CLI (sudah login):

```bash
cd PUSTARA_Vercel_Ready
npx vercel --prod
```

**Catatan:** file ZIP biasanya tidak diimpor langsung sebagai project melalui dashboard Vercel. Ekstrak lalu deploy folder/repository. Jangan unggah screenshot QA atau file sumber lain dari luar folder proyek.

## Menjalankan di komputer

```bash
python -m http.server 8080
```

Buka `http://localhost:8080/`. Periksa Light/Dark, navigasi role/login, grafik, dan pembayaran.

## Tentang alur pembayaran

- Bagian status & bukti memiliki efek animasi struk keluar dari printer.
- **Menunggu verifikasi** menampilkan *bukti pengajuan*, bukan receipt lunas.
- Setelah petugas verifikasi, cetak menghasilkan **2 receipt + 1 bukti pembayaran**.
- QRIS dan rekening contoh **tidak aktif**, dan pembayaran belum dihubungkan ke gateway/bank asli.

## Kesiapan produksi penting

**Deployable ≠ production-ready untuk layanan nyata.** Deployment ini menayangkan prototype front-end, tetapi autentikasi, data transaksi, verifikasi pembayaran, audit, dan notifikasi pada beberapa alur masih berjalan melalui state/localStorage browser. Artinya, petugas di laptop lain tidak otomatis menerima pengajuan dari pengguna lain. **Jangan gunakan untuk menerima pembayaran nyata atau menyimpan data pribadi mahasiswa sungguhan** sampai backend, database, autentikasi aman, dan integrasi finansial selesai. Lihat `docs/PRODUCTION-READINESS.md`.

Bila akan dipakai sebagai pratinjau internal, amankan URL dengan Vercel Deployment Protection atau kontrol akses setara.
