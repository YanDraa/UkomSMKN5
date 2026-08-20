<h1 align="center">🛒 Point of Sale (POS) — Sistem Kasir Berbasis Web</h1>

<p align="center">
  <img src="https://img.shields.io/badge/PHP-7.4%2B-777BB4?style=for-the-badge&logo=php&logoColor=white"/>
  <img src="https://img.shields.io/badge/MySQL-8.0-4479A1?style=for-the-badge&logo=mysql&logoColor=white"/>
  <img src="https://img.shields.io/badge/Bootstrap-4-563D7C?style=for-the-badge&logo=bootstrap&logoColor=white"/>
  <img src="https://img.shields.io/badge/License-MIT-green?style=for-the-badge"/>
</p>

<p align="center">
  Aplikasi Point of Sale (POS) sederhana berbasis web yang dibangun menggunakan <strong>PHP Native</strong> dan <strong>MySQL</strong>.
  Cocok digunakan untuk pengelolaan toko kecil hingga menengah, meliputi manajemen barang, kategori, penjualan, dan laporan.
</p>

---

## 📋 Daftar Isi

- [Fitur Utama](#-fitur-utama)
- [Teknologi yang Digunakan](#-teknologi-yang-digunakan)
- [Struktur Database](#-struktur-database)
- [Struktur Direktori](#-struktur-direktori)
- [Prasyarat](#-prasyarat)
- [Instalasi & Konfigurasi](#-instalasi--konfigurasi)
- [Cara Login](#-cara-login)
- [Cara Menjalankan](#-cara-menjalankan)
- [Kontribusi](#-kontribusi)
- [Lisensi](#-lisensi)

---

## ✨ Fitur Utama

| Fitur | Keterangan |
|-------|------------|
| 🔐 **Autentikasi** | Login sistem single-user dengan session PHP |
| 📦 **Manajemen Barang** | Tambah, ubah, hapus, dan lihat data barang beserta stok |
| 🏷️ **Manajemen Kategori** | Pengelompokan barang berdasarkan kategori |
| 🛍️ **Transaksi Penjualan** | Proses kasir & pembuatan nota transaksi |
| 📊 **Laporan** | Laporan penjualan harian/bulanan |
| 📄 **Export Excel** | Export data ke format Excel |
| 🖨️ **Cetak Nota** | Cetak nota / struk transaksi langsung dari browser |

---

## 🛠️ Teknologi yang Digunakan

- **Backend** : PHP 7.4+ (Native, tanpa framework)
- **Database** : MySQL 5.7+ / MariaDB
- **Frontend** : HTML5, CSS3, Bootstrap 4 (SB Admin Template)
- **Koneksi DB** : PDO (PHP Data Objects)
- **Server** : Apache (via Laragon / XAMPP / WAMP)

---

## 🗄️ Struktur Database

Database bernama **`db_toko`** terdiri dari tabel-tabel berikut:

```
db_toko
├── barang         → Data produk/barang yang dijual
├── kategori       → Kategori pengelompokan barang
├── login          → Data akun pengguna (ter-hash MD5)
├── member         → Data pelanggan / member toko
├── nota           → Nota / header transaksi
├── penjualan      → Detail item per transaksi
└── toko           → Informasi profil toko
```

> File SQL tersedia di [`db_toko.sql`](./db_toko.sql) — import file ini untuk mendapatkan struktur tabel beserta data sampel.

---

## 📁 Struktur Direktori

```
pos/
├── admin/
│   ├── module/
│   │   ├── barang/        → CRUD halaman barang
│   │   ├── jual/          → Halaman proses penjualan
│   │   ├── kategori/      → CRUD halaman kategori
│   │   └── laporan/       → Halaman laporan
│   └── template/          → Layout & komponen tampilan (sidebar, header, dsb.)
├── assets/                → File statis (CSS, JS, gambar)
├── fungsi/
│   ├── edit/              → Fungsi update data
│   ├── hapus/             → Fungsi delete data
│   ├── tambah/            → Fungsi insert data
│   └── view/              → Fungsi select/tampil data
├── sb-admin/              → Template SB Admin Bootstrap
├── .htaccess              → Konfigurasi Apache
├── config.php             → Konfigurasi koneksi database
├── db_toko.sql            → File dump database
├── excel.php              → Export data ke Excel
├── index.php              → Halaman utama (dashboard)
├── login.php              → Halaman login
├── logout.php             → Proses logout
└── print.php              → Cetak nota transaksi
```

---

## ✅ Prasyarat

Pastikan environment Anda sudah memiliki:

- [x] **PHP** versi 7.4 atau lebih baru
- [x] **MySQL** / MariaDB
- [x] **Apache** web server
- [x] **PDO** extension aktif di PHP

> Disarankan menggunakan [**Laragon**](https://laragon.org/) atau [**XAMPP**](https://www.apachefriends.org/) untuk kemudahan setup di lokal.

<details>
<summary>💡 <strong>Menggunakan Laragon? Klik untuk panduan khusus Laragon</strong></summary>

### Setup dengan Laragon

Laragon adalah local development environment yang ringan dan mudah digunakan untuk Windows. Berikut hal-hal yang perlu diketahui:

**Lokasi folder proyek:**
```
C:\laragon\www\pos\
```
Semua proyek diletakkan di dalam `C:\laragon\www\`. Laragon secara otomatis mendeteksi folder baru di sini.

**Mengakses aplikasi di browser:**
```
http://localhost/pos/
```
Atau jika fitur **Auto Virtual Host** aktif:
```
http://pos.test/
```
> Untuk mengaktifkan virtual host otomatis: buka Laragon → Menu → Preferences → centang *Auto create virtual hosts*.

**Mengakses phpMyAdmin:**
```
http://localhost/phpmyadmin
```
Atau lewat tray icon Laragon → klik kanan → **Database** → **phpMyAdmin**.

**Kredensial MySQL default Laragon:**
| Field    | Value  |
|----------|--------|
| Host     | `localhost` |
| Username | `root` |
| Password | `root` *(atau kosong, tergantung versi Laragon)* |

> Sesuaikan password MySQL Anda di `config.php` dengan kredensial di atas.

**Menjalankan / menghentikan server:**
- Klik **Start All** di jendela Laragon untuk menjalankan Apache & MySQL.
- Klik **Stop All** untuk menghentikan semua layanan.

</details>

---

## ⚙️ Instalasi & Konfigurasi

### 1. Clone atau salin proyek ke direktori web server

```bash
# Jika menggunakan Git
git clone https://github.com/YanDraa/UkomSMKN5.git

# Letakkan di dalam folder web server Anda, misalnya:
# Laragon : C:\laragon\www\pos\      ← akses via http://localhost/pos/
# XAMPP   : C:\xampp\htdocs\pos\     ← akses via http://localhost/pos/
```

> 💡 **Pengguna Laragon**: Clone langsung ke `C:\laragon\www\` agar Laragon otomatis mendeteksi proyek.

### 2. Import database

1. Buka **phpMyAdmin** di browser: `http://localhost/phpmyadmin`
2. Buat database baru dengan nama `db_toko`
3. Pilih database tersebut, klik tab **Import**
4. Pilih file [`db_toko.sql`](./db_toko.sql) lalu klik **Go**

### 3. Konfigurasi koneksi database

Buka file `config.php` dan sesuaikan dengan konfigurasi server Anda:

```php
$host   = 'localhost';   // Host server (biasanya localhost)
$user   = 'root';        // Username MySQL Anda
$pass   = '';            // Password MySQL Anda (kosongkan jika XAMPP default)
$dbname = 'db_toko';     // Nama database yang sudah dibuat
```

> ⚠️ **Jangan** menyertakan kredensial asli (username/password production) saat meng-upload ke repositori publik.

---

## 🔑 Cara Login

Gunakan kredensial default berikut untuk masuk ke sistem:

| Field    | Value   |
|----------|---------|
| Username | `admin` |
| Password | `123`   |

> ⚠️ **Catatan Keamanan**: Sistem ini menggunakan hash **MD5** untuk menyimpan password. Untuk penggunaan di lingkungan produksi, sangat disarankan mengganti metode hashing ke **bcrypt** atau **Argon2** demi keamanan yang lebih baik.

---

## ▶️ Cara Menjalankan

1. Pastikan **Apache** dan **MySQL** sudah berjalan (via Laragon / XAMPP).
2. Buka browser dan akses:

   ```
   http://localhost/pos/
   ```

3. Masuk menggunakan [kredensial default](#-cara-login) di atas.
4. Mulai kelola data toko Anda! 🎉

---

## 🤝 Kontribusi

Kontribusi sangat terbuka! Jika Anda ingin berkontribusi:

1. **Fork** repositori ini
2. Buat branch fitur baru: `git checkout -b fitur/nama-fitur`
3. Commit perubahan Anda: `git commit -m "feat: tambah fitur X"`
4. Push ke branch: `git push origin fitur/nama-fitur`
5. Buat **Pull Request** ke branch `main`

---

## 📄 Lisensi

Proyek ini dilisensikan di bawah **MIT License**.
Lihat file [`LICENSE`](./LICENSE) untuk informasi lebih lanjut.

---

<p align="center">
  Dibuat dengan ❤️ untuk keperluan belajar dan pengembangan.<br/>
  <em>Gunakan aplikasi ini dengan bijak. Selamat belajar!</em>
</p>
