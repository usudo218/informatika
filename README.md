# Portal Siswa - Kelas Informatika SMAN 1 Muncar

Ini adalah repositori kode sumber untuk **Portal Siswa Kelas Informatika SMAN 1 Muncar**. Portal ini di-hosting menggunakan GitHub Pages dan berfungsi sebagai pusat informasi, materi, dan administrasi tugas untuk siswa.

**➡️ Link Portal Live: `https://usudo218.github.io/informatika/`**
---

## Fitur Utama

Portal ini terdiri dari beberapa halaman utama yang saling terhubung:

1.  **Portal Utama (`index.html`)**
    * Halaman selamat datang yang berfungsi sebagai dashboard navigasi utama.
    * Mengarahkan siswa ke halaman "Repositori Materi" atau "Pengumpulan Tugas".

2.  **Repositori Materi (`repository.html`)**
    * Menampilkan daftar materi pelajaran (modul, video, zip) dalam bentuk kartu yang rapi.
    * Menyediakan tombol "Lihat" dan "Unduh" yang terhubung langsung ke file di Google Drive.
    * Menampilkan kartu khusus untuk "Tugas & Ulangan" yang mengarah ke halaman login.

3.  **Halaman Login Tugas (`dashboard.html`)**
    * Sistem login aman menggunakan **Username** dan **Password** yang unik untuk setiap siswa.
    * Mencegah siswa melihat soal sebelum login.

4.  **Halaman Tugas/Ulangan (`tugas.html`)**
    * Halaman pribadi yang hanya bisa diakses setelah login berhasil.
    * Menampilkan detail siswa (Nama, Kelas, Absen) yang sedang login.
    * Secara otomatis menampilkan **soal yang berbeda-beda** untuk setiap siswa berdasarkan nomor absen mereka.
    * Memiliki fitur "Download Soal (PDF)" untuk dikerjakan secara offline.

5.  **Pengumpulan Tugas (`upload.html`)**
    * Formulir sederhana bagi siswa untuk mengunggah file tugas mereka.
    * Terintegrasi dengan **Google Apps Script** sebagai backend, sehingga file yang diunggah otomatis tersimpan di folder Google Drive guru.

---

## Teknologi yang Digunakan

* **Frontend:** HTML5, CSS3 (Flexbox/Grid), dan Vanilla JavaScript (ES6+).
* **Hosting:** GitHub Pages.
* **Backend (Upload):** Google Apps Script (dideploy sebagai Web App).
* **Lain-lain:** `jspdf.js` (untuk generate PDF di sisi klien).

---

## Cara Mengelola Konten (Untuk Guru)

Untuk mempermudah pembaruan, semua data telah dipisahkan dari file HTML. Anda hanya perlu mengedit file `.js` berikut untuk mengelola konten:

* **Untuk Mengelola Login Siswa:**
    Buka dan edit file `database-siswa.js`.

* **Untuk Mengelola Soal Ulangan/Tugas:**
    Buka dan edit file `database-soal.js`.

* **Untuk Mengelola Materi Repositori:**
    Buka dan edit file `database-materi.js`.

### Catatan Penting Saat Update (Cache)

Setelah Anda mengedit salah satu file `.js` di atas, siswa mungkin tidak akan langsung melihat perubahan karena **cache browser**.

Untuk memaksa browser siswa mengunduh file versi baru, Anda harus mengubah nomor versi di file `.html` yang memanggilnya.

**Contoh di `repository.html`:**
* **Sebelum update:** `<script src="database-materi.js?v=1"></script>`
* **Setelah update:** `<script src="database-materi.js?v=2"></script>`

Lakukan hal yang sama di `dashboard.html` (untuk `database-siswa.js`) dan `tugas.html` (untuk `database-soal.js`).
