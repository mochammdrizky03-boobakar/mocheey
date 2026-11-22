# Mocheey — Master Guide & Product Prompt

## 1. Identitas aplikasi

- **Nama:** Mocheey
- **Jenis:** aplikasi pencatatan dan pemantauan keuangan pribadi
- **Format:** satu file HTML mandiri
- **Bahasa:** Indonesia
- **Gaya visual:** minimalis, rapi, elegan, dominan ungu
- **Tujuan:** membantu pemilik mencatat arus kas, memantau kewajiban, mengelola anggaran, dan menjaga riwayat keuangan dalam jangka panjang.

## 2. File

- `mocheey.html` — aplikasi utama. Buka langsung menggunakan browser modern.
- `MASTER.md` — dokumentasi dan prompt pengembangan.

## 3. Fitur yang tersedia

1. **Pemasukan dan pengeluaran** — catat keterangan, nominal, tanggal, kategori, dan status.
2. **Saldo tersedia** — pemasukan lunas dikurangi pengeluaran lunas pada bulan yang dipilih.
3. **Piutang dan hutang terpisah** — pemasukan belum lunas ditampilkan sebagai piutang; pengeluaran belum lunas sebagai hutang.
4. **Ringkasan keseluruhan** — total pemasukan, pengeluaran, jumlah transaksi tertunda, dan saldo bersih tercatat.
5. **Grafik tren bulanan** — visualisasi pemasukan dan pengeluaran lunas per hari dalam bulan yang dipilih.
6. **Filter dan pencarian** — filter jenis/status serta cari keterangan atau kategori.
7. **Edit dan hapus transaksi** — koreksi catatan yang sudah dibuat.
8. **Anggaran bulanan** — tetapkan batas pengeluaran untuk setiap bulan dan pantau pemakaiannya.
9. **Export CSV** — unduh catatan transaksi dalam format CSV yang dapat dibuka dengan Microsoft Excel, Google Sheets, dan aplikasi spreadsheet lain.
10. **Cetak / PDF** — gunakan dialog cetak browser dan pilih “Save as PDF”.
11. **Backup dan restore JSON** — simpan salinan transaksi dan anggaran, lalu pulihkan saat pindah perangkat atau browser.

## 4. Cara memulai

1. Unduh `mocheey.html`.
2. Buka file menggunakan Chrome, Firefox, Edge, atau browser modern lain.
3. Untuk transaksi masuk, pilih **Pemasukan**; untuk uang keluar, pilih **Pengeluaran**.
4. Isi keterangan, nominal, tanggal, kategori, dan status.
5. Klik **Simpan transaksi**.
6. Pilih bulan pada bagian **Tren keuangan** untuk melihat ringkasan bulan tersebut.
7. Atur anggaran bulanan pada panel **Anggaran bulanan**.
8. Gunakan tombol **Edit** atau **Hapus** di riwayat untuk mengelola transaksi.

## 5. Makna status dan perhitungan

- **Lunas:** uang sudah diterima (pemasukan) atau sudah dibayarkan (pengeluaran).
- **Belum lunas:** pemasukan yang belum diterima adalah **piutang**; pengeluaran yang belum dibayarkan adalah **hutang**.
- **Saldo tersedia bulan terpilih** = pemasukan lunas bulan tersebut − pengeluaran lunas bulan tersebut.
- **Saldo bersih tercatat** = seluruh pemasukan lunas − seluruh pengeluaran lunas sejak awal data.
- Transaksi belum lunas tidak mengubah saldo tersedia.
- Anggaran membandingkan batas yang ditentukan dengan total pengeluaran lunas pada bulan terpilih.

## 6. Ekspor, cetak, dan backup

### Excel / spreadsheet
Klik **Export Excel/CSV**. File CSV dapat dibuka di Excel atau Google Sheets. Jika perlu, gunakan “Save As” di Excel untuk menyimpan sebagai `.xlsx`.

### PDF
Klik **Cetak / PDF**, lalu pilih printer **Save as PDF** pada dialog browser. Tampilan cetak menyembunyikan tombol dan kontrol yang tidak dibutuhkan.

### Backup data
Klik **Backup data** secara berkala. Simpan file JSON di tempat aman (misalnya folder cloud pribadi atau penyimpanan eksternal). Untuk memulihkan, buka Mocheey lalu klik **Import backup** dan pilih file JSON. Import mengganti transaksi dan anggaran yang sedang ada, jadi buat backup terbaru sebelum memulihkan.

## 7. Penyimpanan dan batasan

- Data disimpan secara lokal di browser melalui `localStorage`; tidak ada akun, server, atau sinkronisasi otomatis.
- File yang dibuka pada perangkat/browser lain tidak otomatis memiliki data yang sama.
- Jangan menghapus data situs/browser sebelum membuat backup.
- Untuk pemakaian jangka panjang, ekspor backup JSON secara rutin dan simpan di lebih dari satu tempat yang aman.
- CSV merupakan format spreadsheet yang kompatibel dengan Excel, bukan file `.xlsx` native.
- Fitur PDF menggunakan fasilitas cetak browser.
- Aplikasi ini adalah pencatat pribadi, bukan layanan bank, bukan sistem akuntansi resmi, dan tidak melakukan sinkronisasi rekening.

## 8. Prompt utama untuk pengembangan Mocheey

Salin prompt berikut ketika ingin meminta AI mengembangkan aplikasi ini lebih lanjut:

> Bertindaklah sebagai senior frontend engineer sekaligus product designer. Kembangkan aplikasi bernama **Mocheey**, sebuah personal finance tracker untuk penggunaan pribadi jangka panjang. Pertahankan aplikasi sebagai satu file HTML mandiri yang bisa dibuka langsung di browser tanpa instalasi, backend, atau koneksi internet. Gunakan HTML, CSS, dan JavaScript vanilla.
>
> **Identitas visual:** minimalis, elegan, bersih, mudah dipahami, dominan ungu dengan kontras teks yang nyaman. Desain harus responsif untuk HP dan desktop. Hindari tampilan yang ramai dan jangan mengorbankan keterbacaan demi dekorasi.
>
> **Fitur wajib:** pencatatan pemasukan dan pengeluaran; nominal, tanggal, kategori, keterangan, serta status lunas/belum lunas; saldo tersedia; pemisahan piutang (pemasukan belum diterima) dan hutang (pengeluaran belum dibayar); ringkasan keseluruhan; riwayat transaksi; pencarian dan filter; edit dan hapus transaksi; grafik tren bulanan; anggaran per bulan; export CSV yang kompatibel dengan Excel; cetak laporan ke PDF melalui browser; backup dan restore JSON.
>
> **Kebutuhan jangka panjang:** data harus konsisten, perhitungan saldo tidak boleh menghitung transaksi belum lunas sebagai uang yang sudah diterima/dibayarkan, validasi nominal dan tanggal harus jelas, serta pengguna harus dapat membuat backup dan memulihkan data. Jangan menghapus atau mengubah struktur data lama tanpa migrasi yang aman. Berikan konfirmasi sebelum tindakan destruktif seperti menghapus transaksi atau mengganti seluruh data saat restore.
>
> **Kualitas teknis:** gunakan kode yang terstruktur dan mudah dirawat, nama fungsi/variabel yang jelas, aksesibilitas label form, penanganan localStorage yang aman, serta empty state dan pesan sukses/gagal yang informatif. Jangan mengarang klaim keamanan atau sinkronisasi cloud. Jika menambahkan fitur baru, jelaskan dampaknya pada penyimpanan dan kompatibilitas data.
>
> Sebelum menyelesaikan, uji alur tambah, edit, hapus, filter, perhitungan saldo, anggaran, export CSV, cetak, backup, dan restore. Berikan file HTML lengkap serta dokumentasi MASTER.md yang menjelaskan fitur, cara pakai, rumus, backup, dan batasan.

## 9. Ide pengembangan berikutnya

- Transaksi berulang untuk gaji, sewa, langganan, dan tagihan.
- Target tabungan dengan progres.
- Anggaran per kategori, bukan hanya total bulanan.
- Perbandingan bulan ke bulan dan laporan tahunan.
- Pengelolaan beberapa dompet atau rekening.
- Penguncian aplikasi dengan PIN lokal (perlu penjelasan batas keamanan karena tetap berjalan di browser lokal).

**Prioritas yang disarankan:** backup yang rutin, target tabungan, transaksi berulang, lalu laporan tahunan. Pertahankan pengalaman sederhana sebagai prinsip utama Mocheey.


## 10. Instalasi sebagai PWA di Android

Paket `mocheey-pwa` berisi versi PWA siap-hosting: `index.html`, `manifest.webmanifest`, `sw.js`, dan ikon 192/512px. Upload seluruh isi folder ke root repository GitHub, aktifkan GitHub Pages dari branch `main` dan folder `/root`, lalu buka URL HTTPS hasil deploy di Chrome Android dan pilih **Install app** atau **Tambahkan ke layar utama**.

Lihat `README-PWA.md` di paket PWA untuk langkah lengkap, termasuk pemindahan data lama melalui Backup data dan Import backup. Penyimpanan versi lokal dan PWA terpisah, sehingga backup lalu restore diperlukan saat migrasi.
