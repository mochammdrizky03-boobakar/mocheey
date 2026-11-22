# Mocheey PWA — Paket instalasi Android

Paket ini mengubah Mocheey menjadi Progressive Web App (PWA), sehingga dapat dipasang dari Chrome Android dan dibuka seperti aplikasi.

## Isi paket

- `index.html` — aplikasi Mocheey.
- `manifest.webmanifest` — nama, ikon, warna, dan mode aplikasi.
- `sw.js` — service worker untuk cache app shell dan akses offline setelah kunjungan pertama.
- `icons/` — ikon aplikasi ukuran 192px dan 512px.

## Cara hosting gratis dengan GitHub Pages

1. Buat akun atau masuk ke https://github.com/.
2. Buat repository baru, misalnya `mocheey`.
3. Upload **seluruh isi folder ini** ke root repository. Pastikan `index.html`, `manifest.webmanifest`, dan `sw.js` berada di root, bukan di dalam folder tambahan.
4. Buka **Settings → Pages**.
5. Pada **Build and deployment**, pilih **Deploy from a branch**.
6. Pilih branch `main` dan folder `/ (root)`, lalu tekan **Save**.
7. Tunggu proses deploy selesai. GitHub akan memberikan alamat HTTPS, biasanya `https://USERNAME.github.io/mocheey/`.
8. Buka alamat itu di Chrome Android.

## Cara install di HP Android

1. Buka URL GitHub Pages Mocheey menggunakan Chrome.
2. Tunggu halaman selesai dimuat dan pastikan koneksi internet aktif pada kunjungan pertama.
3. Buka menu titik tiga Chrome.
4. Pilih **Install app** atau **Tambahkan ke layar utama** (nama menu bisa berbeda menurut versi Chrome).
5. Konfirmasi pemasangan. Ikon Mocheey akan muncul di layar aplikasi/layar utama.

## Penting: pindahkan data lama

Versi HTML lokal dan versi PWA yang dihosting memiliki penyimpanan browser yang berbeda. Sebelum beralih:

1. Buka Mocheey versi lama di browser/perangkat tempat data tersimpan.
2. Tekan **Backup data** untuk mengunduh file JSON.
3. Buka Mocheey PWA dari URL HTTPS yang baru.
4. Tekan **Import backup**, pilih file JSON tadi, lalu konfirmasi.
5. Pastikan riwayat dan saldo sudah benar.

Simpan file backup di tempat aman dan buat backup berkala. Jangan mengandalkan satu salinan saja.

## Catatan offline dan privasi

- PWA dapat dibuka offline setelah berhasil dimuat setidaknya sekali secara online dan service worker selesai terpasang.
- Data transaksi tetap disimpan di `localStorage` pada browser/origin tersebut; tidak tersinkron otomatis antarperangkat.
- Jangan menghapus data situs Chrome tanpa backup.
- Jika mengubah kode aplikasi, naikkan nilai `CACHE_NAME` di `sw.js` (contoh `mocheey-pwa-v2`) agar browser mengambil cache versi baru.
- GitHub Pages bersifat publik untuk file aplikasi. Data keuangan tidak diunggah ke GitHub oleh aplikasi; data disimpan di browser pengguna. Jangan menambahkan data transaksi pribadi ke repository.
- Ini PWA berbasis penyimpanan lokal, bukan aplikasi native APK dan bukan layanan cloud.

## Troubleshooting

- **Tidak ada pilihan Install app:** pastikan memakai Chrome Android, URL HTTPS, manifest dan ikon ikut ter-upload, serta service worker berhasil dimuat.
- **Perubahan belum terlihat:** tutup lalu buka kembali aplikasi; jika masih versi lama, perbarui `CACHE_NAME` pada `sw.js`, commit, dan tunggu GitHub Pages selesai deploy.
- **Data lama tidak muncul:** lakukan backup dari versi lama dan import ke versi PWA. Penyimpanan tidak berpindah otomatis.
