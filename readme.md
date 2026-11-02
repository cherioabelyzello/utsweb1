# 📚 Web Application - Toko Buku Pustaka

Dokumentasi proyek aplikasi web sistem manajemen toko buku berbasis HTML, CSS, dan JavaScript modular untuk tugas mata kuliah **Pemrograman Web**.

## 👨‍🎓 Identitas Mahasiswa

* **Nama Lengkap**: Cheerio Abelyzello Martines
* **NIM**: 312510241
* **Mata Kuliah**: Pemrograman Web
* **Program Studi**: Teknik Informatika
* **Perguruan Tinggi**: Universitas Pelita Bangsa (UPB)

---

## 📌 Deskripsi Proyek

Aplikasi **Toko Buku Pustaka** adalah sistem informasi berbasis web yang dirancang menggunakan struktur **modular dengan file HTML terpisah**. Pendekatan ini membuat aplikasi ringan, terstruktur dengan jelas, dan mudah dikembangkan tanpa terjadi pembentrokan alur kerja (*display conflicts*).

Aplikasi ini dilengkapi dengan:

* **Form Login & Autentikasi**: Antarmuka login bersih dengan dukungan penanganan modal **Lupa Password** dan **Daftar**.
* **Validasi Login Autentik**: Memeriksa kesesuaian email dan password secara dinamis menggunakan array `dataPengguna` pada JavaScript.
* **Notifikasi Alert Interaktif**: Menampilkan pop-up konfirmasi selamat datang dinamis saat login sukses.
* **Fitur Modal Interaktif**: Pop-up window interaktif untuk pemulihan akun dan pendaftaran pengguna baru.
* **Dashboard Dinamis & Sapaan Waktu**: Fitur greeting berbasis jam lokal serta penanganan logout pengguna.
* **Informasi Stok & Katalog Buku (`stok.html`)**: Tabel lengkap daftar buku, penulis, kategori, harga, dan stok yang tersedia.
* **Modul Tracking Pengiriman (`tracking.html`)**: Fitur pencarian status pengiriman berdasarkan Nomor Resi / Kode Pesanan.
* **Laporan Pemesanan Buku (`laporan.html`)**: Tabel rekapitulasi data pesanan buku yang mencakup nama pemesan, judul buku, jumlah, dan status transaksi.
* **History Transaksi (`history.html`)**: Catatan riwayat transaksi pengguna yang menampilkan ID transaksi, rincian buku, total harga, dan status pembayaran.
* **Form Pemesanan / Checkout (`checkout.html`)**: Form input interaktif untuk pemesanan buku baru dengan pilihan metode pembayaran.
* **Struktur Navigasi Terpisah**: Menghubungkan ke fitur Informasi Stok, Tracking Pengiriman, Laporan Pemesanan, History Transaksi, dan Checkout.
* **Master Data Terpusat (`data.js`)**: Menyimpan data array katalog buku dan data kredensial pengguna untuk autentikasi.

---

## 📂 Struktur Berkas (File Structure)

```
├── index.html          # Halaman Utama / Form Login & Modal Interaktif
├── dashboard.html      # Halaman Dashboard Utama & Menu Navigasi
├── stok.html           # Halaman Informasi Stok & Katalog Buku
├── tracking.html       # Halaman Tracking Pengiriman Buku
├── laporan.html        # Halaman Laporan Pemesanan Buku (Tabel Data)
├── history.html        # Halaman History / Riwayat Transaksi
├── checkout.html       # Halaman Form Pemesanan / Checkout Buku
├── css/
│   └── style.css       # File Styling & Tata Letak Aplikasi
└── js/
    ├── data.js         # Master Data Array (Katalog Buku & Data Pengguna)
    └── script.js       # Logika Autentikasi, Modal, Greeting & Navigasi
```

---

## 📸 Dokumentasi Antarmuka & Kode Program

### 1. Antarmuka Login (`index.html`)

* Halaman awal aplikasi berupa form autentikasi email dan password.
* Terdapat tautan interaktif **Lupa Password** dan **Daftar** di bagian bawah.

### 2. Notifikasi Pop-up Alert Login Berhasil

* Saat input validasi sesuai dengan data di `data.js`, sistem memicu pop-up *Alert* pesan selamat datang sebelum meredirect pengguna ke `dashboard.html`.

### 3. Antarmuka Dashboard (`dashboard.html`)

* Halaman pusat navigasi yang menampilkan ucapan selamat datang dinamis dan tombol akses cepat ke seluruh fitur aplikasi serta fungsi **Logout**.

### 4. Informasi Stok & Katalog Buku (`stok.html`)

* Menampilkan daftar koleksi buku dalam tabel teratur yang mencakup Kode Buku, Judul, Penulis, Kategori, Harga, dan Jumlah Stok.

### 5. Antarmuka Tracking Pengiriman (`tracking.html`)

* Tampilan antarmuka modul tracking pengiriman pesanan di mana pengguna dapat memasukkan nomor resi atau kode pesanan untuk mengecek status terkini.

### 6. Laporan Pemesanan Buku (`laporan.html`)

* Halaman laporan yang menyajikan data rekapitulasi pesanan buku pelanggan, seperti pesanan atas nama **Cheerio Abelyzello** (Status: Diproses) dan **Budi Santoso** (Status: Selesai).

### 7. History Transaksi (`history.html`)

* Menampilkan kartu rincian riwayat transaksi yang pernah dilakukan pengguna (seperti ID Transaksi **#TRX-93821**, judul buku, total harga, dan status keberhasilan transaksi).

### 8. Form Pemesanan & Checkout Buku (`checkout.html`)

![Form Pemesanan & Laporan Buku](image_2feac7.png)

* Halaman input transaksi pemesanan yang berisi form nama pemesan, alamat pengiriman, pilihan daftar buku, jumlah beli, serta pilihan metode pembayaran (seperti Transfer Bank).

### 9. Source Code Modul Tracking Pengiriman (`tracking.html`)

```html
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <title>Tracking Pengiriman - Toko Buku Pustaka</title>
    <link rel="stylesheet" href="css/style.css">
</head>
<body>
    <div class="tracking-container">
        <h2>Tracking Pengiriman Pesanan</h2>
        <p><a href="dashboard.html" class="link-kembali">&larr; Kembali ke Dashboard</a></p>

        <div style="margin-top: 15px;">
            <label>Masukkan Nomor Resi / Kode Pesanan:</label>
            <input type="text" id="input-resi" placeholder="Contoh: RESI001" style="margin-top: 5px;">
            <button type="button" id="btn-tracking">Cek Status</button>
        </div>

        <div id="hasil-tracking" style="margin-top: 20px; padding: 10px; background: #f9f9f9;">
            <!-- Hasil tracking akan muncul di sini -->
        </div>
    </div>

    <script src="js/script.js"></script>
</body>
</html>
```

### 10. Master Data Terpusat (`js/data.js`)

```javascript
// js/data.js
const dataKatalogBuku = [
    { kode: "BK001", judul: "Pemrograman Web Dasar", penulis: "Andi Wijaya", kategori: "Teknologi" },
    { kode: "BK002", judul: "JavaScript untuk Pemula", penulis: "Rina Kartika", kategori: "Teknologi" }
];

const dataPengguna = [
    { nama: "Mahasiswa Demo", email: "mahasiswa@email.com", password: "123456" }
];
```

### 11. Logika Validasi Login (`js/script.js`)

```javascript
// ==========================================
// 2. Validasi Login
// ==========================================
const formLogin = document.getElementById("form-login");

if (formLogin) {
    formLogin.addEventListener("submit", function (e) {
        e.preventDefault();
        const email = document.getElementById("login-email").value.trim();
        const password = document.getElementById("login-password").value.trim();

        // Cek dari dataPengguna
        const user = dataPengguna.find(u => u.email === email && u.password === password);

        if (user) {
            alert("Login Berhasil! Selamat datang, " + user.nama);
            window.location.href = "dashboard.html";
        } else {
            alert("email/password yang anda masukkan salah");
        }
    });
}
```

### 12. Logika Modal Lupa Password & Daftar (`js/script.js`)

```javascript
// ==========================================
// 3. Logika Modal Lupa Password & Daftar
// ==========================================
const modalLupa = document.getElementById("modal-lupa");
const modalDaftar = document.getElementById("modal-daftar");

const btnLupa = document.getElementById("btn-lupa");
const btnDaftar = document.getElementById("btn-daftar");

if (btnLupa) btnLupa.onclick = () => modalLupa.style.display = "block";
if (btnDaftar) btnDaftar.onclick = () => modalDaftar.style.display = "block";

const closeLupa = document.getElementById("close-lupa");
const closeDaftar = document.getElementById("close-daftar");

if (closeLupa) closeLupa.onclick = () => modalLupa.style.display = "none";
if (closeDaftar) closeDaftar.onclick = () => modalDaftar.style.display = "none";

window.onclick = function(event) {
    if (event.target === modalLupa) modalLupa.style.display = "none";
    if (event.target === modalDaftar) modalDaftar.style.display = "none";
};
```

### 13. Logika Dashboard Greeting & Logout (`js/script.js`)

```javascript
// ==========================================
// 4. Script Dashboard (Greeting & Logout)
// ==========================================
const greetingEl = document.getElementById("greeting");
if (greetingEl) {
    const jam = new Date().getHours();
    let waktu = "Pagi";
    if (jam >= 11 && jam < 15) waktu = "Siang";
    else if (jam >= 15 && jam < 18) waktu = "Sore";
    else if (jam >= 18) waktu = "Malam";

    greetingEl.textContent = `Selamat datang ditoko buku pustaka!`;
}

const btnLogout = document.getElementById("btn-logout");
if (btnLogout) {
    btnLogout.onclick = function() {
        alert("Berhasil logout!");
        window.location.href = "index.html";
    };
}
```

---

## 🚀 Alur Navigasi Aplikasi

1. **Halaman Login (`index.html`)**:
   * Pengguna mengisikan email (`mahasiswa@email.com`) dan password (`123456`).
   * Tombol **Lupa Password** dan **Daftar** membuka modal interaktif tanpa beralih halaman.
   * Menekan tombol **Login** akan memvalidasi data ke `js/data.js`, menayangkan pop-up *alert* sukses, lalu mengarahkan ke `dashboard.html`.

2. **Halaman Dashboard (`dashboard.html`)**:
   * Menampilkan ucapan selamat datang via `script.js`.
   * Menampilkan tombol navigasi menuju `stok.html`, `tracking.html`, `laporan.html`, `history.html`, dan `checkout.html`.
   * Tombol **Logout** menampilkan alert notifikasi lalu mengarahkan kembali ke `index.html`.

3. **Halaman Fitur (Modul Terpisah)**:
   * **`stok.html`**: Tabel daftar lengkap stok buku dan katalog.
   * **`tracking.html`**: Form pencarian status pengiriman pesanan.
   * **`laporan.html`**: Tabel rincian pemesanan buku beserta statusnya.
   * **`history.html`**: Kartu riwayat transaksi pembelian buku.
   * **`checkout.html`**: Form pengisian pesanan pembelian buku.
   * Setiap modul menyediakan link **`← Kembali ke Dashboard`** untuk kemudahan alur pemakaian.

---

## 💻 Teknologi yang Digunakan

* **HTML5**: Struktur halaman web statis modular.
* **CSS3**: Penataan layout responsif, form, dan styling tabel.
* **JavaScript (ES6)**: Manipulasi DOM, validasi login, logika modal, greeting dinamis, serta pengelolaan array data.