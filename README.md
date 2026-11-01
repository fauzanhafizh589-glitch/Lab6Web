# Laporan Praktikum 6: JavaScript DOM dan Event Handling
---

## Cara Menjalankan Program
1. Pastikan seluruh file (`index.html`, `style.css`, dan `script.js`) berada di dalam satu folder direktori yang sama.
2. Buka file **`index.html`** menggunakan *browser* modern (seperti Google Chrome, Mozilla Firefox, atau Microsoft Edge).
3. Uji setiap fitur interaktif mulai dari perubahan teks, *event* tombol, penghitung karakter, validasi *form*, hingga *to-do list* dan mini project langsung di *browser*.
---

## Tujuan dan Fungsi Program

### **A. Tujuan Program**
Program ini dibuat dengan tujuan utama sebagai sarana pembelajaran praktik untuk:
1. **Memahami Konsep DOM (*Document Object Model*):** Mengenal bagaimana struktur dokumen HTML dapat diakses, dibaca, dan dimodifikasi secara dinamis menggunakan bahasa pemrograman JavaScript.
2. **Menerapkan *Event Handling*:** Mempelajari cara merespons berbagai tindakan atau aksi yang dilakukan oleh pengguna pada halaman web (seperti klik tombol, ketikan teks, perubahan input, hingga pengiriman formulir) menggunakan metode `addEventListener()`.
3. **Melakukan Validasi Sisi Klien (*Client-Side Validation*):** Menguasai teknik pemeriksaan kelayakan data pada formulir sebelum data tersebut diproses atau dikirim ke server.
4. **Membangun Komponen Interaktif:** Mengembangkan keterampilan membuat aplikasi web fungsional berukuran kecil, mulai dari pengubah gaya CSS, penghitung karakter *real-time*, aplikasi daftar tugas (*to-do list*), hingga pembuatan form pendaftaran workshop.

### **B. Fungsi dari Setiap Komponen Program**
Secara arsitektur, program ini dibagi menjadi tiga bagian file utama yang saling terintegrasi untuk menjalankan fungsi-fungsi berikut:
1. **`index.html` (Struktur dan Kerangka Tampilan):** Membangun tata letak halaman web secara terstruktur dan menyediakan elemen-elemen antarmuka seperti tajuk, paragraf, tombol, kotak teks, daftar terstruktur, dan formulir pendaftaran.
2. **`style.css` (Penataan Gaya Visual):** Memperindah tampilan estetika halaman web serta menyediakan kelas utilitas khusus (`.highlight`, `.teks-besar`, dan `.selesai`) yang dirancang agar dapat dipasang atau dilepas secara dinamis oleh JavaScript.
3. **`script.js` (Logika Pemrograman & Interaktivitas):**
   * **Manipulasi Teks & Elemen (`Latihan 1` & `Latihan 2`):** Mencari elemen HTML berdasarkan ID dan mengubah teks di dalamnya secara otomatis, serta mencatat waktu saat tombol diklik oleh pengguna.
   * **Pengubahan Gaya Dinamis (`Latihan 3`):** Mengubah tampilan elemen secara interaktif menggunakan fungsi `classList.toggle()` guna mengaktifkan atau menonaktifkan gaya CSS tertentu.
   * **Penghitung Karakter (*Real-Time Character Counter*) (`Latihan 4`):** Memantau ketikan pengguna pada kolom input secara langsung dan memperbarui jumlah karakter yang diketik pada layar.
   * **Validasi Formulir (`Latihan 5` & *Mini Project*):** Menahan aksi bawaan *browser* (`event.preventDefault()`) saat tombol *submit* ditekan, lalu memeriksa apakah masukan nama, format email, pilihan sesi, dan rentang usia telah sesuai dengan aturan yang ditentukan sebelum data dinyatakan valid.
   * **Aplikasi Daftar Tugas (*To-Do List*) (`Latihan 6`):** Membuat elemen HTML baru secara dinamis (`document.createElement()`) guna menambahkan daftar tugas baru serta mengubah status tugas menjadi selesai menggunakan efek coret garis (*line-through*).



### 1. Apa yang dimaksud dengan DOM dan apa manfaatnya?
* **Jawaban:** DOM (*Document Object Model*) adalah representasi terstruktur dari dokumen HTML dalam bentuk objek yang dapat diakses dan dimanipulasi oleh bahasa pemrograman seperti JavaScript. Manfaatnya adalah memungkinkan pengembang web untuk mengubah konten teks, atribut, struktur elemen, serta merespons interaksi pengguna secara dinamis tanpa harus memuat ulang (*reload*) halaman.

### 2. Apa perbedaan getElementById(), querySelector(), dan querySelectorAll()?
* **Jawaban:** 
  * `getElementById(id)`: Memilih **satu** elemen secara spesifik berdasarkan atribut `id`-nya.
  * `querySelector(selector)`: Memilih **elemen pertama** yang cocok dengan pemilih CSS tertentu (bisa berupa ID `#`, kelas `.`, atau nama tag).
  * `querySelectorAll(selector)`: Memilih **seluruh elemen** yang cocok dengan pemilih CSS tertentu dan mengembalikannya dalam bentuk NodeList.

### 3. Apa fungsi addEventListener() dan sebutkan tiga contoh event?
* **Jawaban:** `addEventListener()` berfungsi untuk mendaftarkan fungsi penanganan (*event handler*) pada suatu elemen agar mendengarkan dan merespons kejadian (*event*) tertentu. Tiga contoh *event* meliputi:
  1. `"click"` (terjadi ketika elemen diklik).
  2. `"input"` (terjadi saat nilai pada *input* atau *textarea* berubah/diketik).
  3. `"submit"` (terjadi saat sebuah *form* dikirimkan).

### 4. Mengapa event.preventDefault() digunakan pada event submit form?
* **Jawaban:** `event.preventDefault()` digunakan untuk mencegah perilaku bawaan *browser* yang langsung melakukan *reload* halaman saat sebuah *form* disubmit. Hal ini penting agar proses validasi data JavaScript dapat berjalan terlebih dahulu di sisi klien.

### 5. Apa perbedaan textContent dan innerHTML dari sisi penggunaan dan keamanan?
* **Jawaban:** 
  * `textContent` hanya memproses dan mengatur teks biasa (*plain text*), sehingga lebih aman dari celah keamanan.
  * `innerHTML` dapat membaca dan memasukkan tag markup HTML. Namun, penggunaan `innerHTML` untuk data yang bersumber dari pengguna sangat tidak disarankan karena rentan terhadap serangan keamanan seperti XSS (*Cross-Site Scripting*).

### 6. Bagaimana classList.toggle() membantu mengubah tampilan elemen?
* **Jawaban:** `classList.toggle()` berfungsi untuk memeriksa keberadaan suatu kelas CSS pada elemen; jika kelas tersebut belum ada maka akan ditambahkan, dan jika sudah ada maka akan dihapus secara otomatis. Hal ini sangat membantu dalam membuat efek interaktif seperti tombol *toggle* (aktif/non-aktif) dengan lebih ringkas.

### 7. Sebutkan minimal tiga skenario pengujian validasi form.
* **Jawaban:** Tiga skenario pengujian validasi form meliputi:
  1. **Skenario Form Kosong:** Menguji apakah pesan kesalahan muncul ketika semua kolom form dibiarkan kosong.
  2. **Skenario Format Input Salah:** Menguji respons form saat memasukkan format email yang tidak valid (misal tanpa simbol `@`).
  3. **Skenario Nilai Di Luar Ketentuan:** Menguji input angka usia di bawah batas minimum (misal di bawah 17 tahun).

---