# Blogger Post Grid with Auto-Labels & Enclosure

Sistem tampilan *grid* modern untuk Blogger yang dirancang khusus untuk situs portal tema, download file, atau katalog produk. Menggunakan sistem **Vanilla CSS Grid** untuk tata letak yang responsif dan logika **Blogger Data Tags** untuk menangani label secara dinamis tanpa memerlukan JavaScript sama sekali.

## Fitur Utama
- **3-Column Grid:** Tata letak responsif (3 kolom di desktop, 2 di tablet, 1 di mobile).
- **Auto-Label Parsing:** Deteksi otomatis label untuk badge "Version", harga (Rp), dan status (Premium/Gratis).
- **Dynamic Enclosure:** Tombol "Demo" yang terintegrasi langsung dengan fitur *Enclosure* bawaan Blogger.
- **No-Image Fallback:** Menampilkan placeholder otomatis jika postingan tidak memiliki gambar utama.
- **Pure CSS:** Performa sangat cepat karena tidak memuat *script* tambahan.

---

## Cara Pemakaian Label
Sistem ini membaca label yang Anda masukkan pada setiap postingan untuk menentukan tampilan data. Pastikan Anda memberikan label dengan format berikut:

Berikut adalah panduan cara menggunakan label yang benar:

---

## 1. Menampilkan Harga & Diskon
Kode ini mencari label yang mengandung karakter **"Rp"**.
* **Harga Normal:** Buat label dengan format `Rp100.000` (tanpa kata Promo).
* **Harga Diskon:** Anda harus menambahkan **dua label** sekaligus pada satu postingan:
    1.  Label harga asli: `Rp200.000`
    2.  Label harga promo: `Rp100.000 Promo` (wajib mengandung kata **Promo**).
    * *Hasilnya:* Harga Rp200.000 akan dicoret, dan Rp100.000 akan tampil sebagai harga utama yang berwarna hijau.

## 2. Menampilkan Versi Produk
Gunakan label yang mengandung kata **"Version"**.
* **Contoh:** `Version 1.0.0` atau `v2.0 Build Version`.
* *Posisi:* Akan muncul sebagai badge putih di pojok kiri atas gambar produk.

## 3. Menampilkan Ikon Teknologi (Bahasa Pemrograman)
Kode tersebut sudah di-hardcode untuk mengenali nama label spesifik. Anda harus menulisnya **persis** (case sensitive) seperti berikut agar ikonnya muncul:

| Nama Label | Output Visual |
| :--- | :--- |
| `Tailwind CSS` | Badge biru muda dengan ikon Tailwind |
| `HTML` | Badge oranye dengan angka 5 |
| `CSS` | Badge biru standar |
| `Javascript` | Badge kuning dengan inisial "JS" |
| `Blogger` | Badge oranye dengan ikon Blogger |
| `Laravel` | Badge merah dengan ikon Play/Laravel |
| `MySQL` | Badge biru tua dengan ikon Database |
| `PHP` / `Wordpress` / `XML` | Badge sesuai warna brand masing-masing |

## 4. Status Lisensi (Premium vs Gratis)
Kode menggunakan logika pengecekan label bernama **"Premium"**.
* **Premium:** Tambahkan label `Premium`. Maka badge kuning "PREMIUM" akan muncul.
* **Gratis:** Jika Anda **tidak** menambahkan label `Premium`, secara otomatis sistem akan menampilkan badge "GRATIS".

## 5. Tombol Demo (Enclosure)
Khusus untuk tombol **Demo**, ini tidak menggunakan Label, melainkan **Tautan Lampiran (Enclosure)**:
1.  Saat menulis postingan, buka setelan **Tautan Lampiran** di sisi kanan editor.
2.  Masukkan URL demo Anda.
3.  Pada kolom **Mime Type**, tuliskan: `Demo/html`.
    * *Catatan:* Jika Mime Type tidak diisi `Demo/html`, tombol Demo tidak akan muncul.

---

### Contoh Kombinasi Label dalam Satu Postingan:
Jika Anda menjual template landing page, isi kolom label seperti ini:
> `Rp150.000`, `Rp99.000 Promo`, `Tailwind CSS`, `Javascript`, `Version 2.1`, `Premium`

Dengan kombinasi di atas, kartu produk akan menampilkan harga coret, badge versi, ikon teknologi, dan status premium secara otomatis. 

---

## Instalasi

### 1. Menambahkan Kode Widget
Buka **Theme** > **Edit HTML** di Blogger Anda. Cari bagian `b:includable` untuk post body (biasanya bernama `postBodySnippet`) dan ganti kodenya dengan kode XML yang telah disediakan di file proyek ini.

### 2. Mengatur Parent Container
Pastikan Anda membungkus daftar postingan di dalam file `index.html` atau *template* utama dengan *container* berikut agar grid berfungsi:

```html
<div class='post-grid-container'>
  <b:loop values='data:posts' var='post'>
    <b:include data='post' name='postBodySnippet'/>
  </b:loop>
</div>
```

### 3. Menambahkan CSS
Salin kode CSS dari file `style.css` dan letakkan di dalam tag `<style>` atau file `.css` eksternal tema Anda (di bawah kode `]]></b:skin>`).

### 4. Pengaturan Enclosure (Demo Button)
Untuk menampilkan tombol **Demo**, pastikan saat Anda membuat postingan baru di Blogger:
1.  Klik menu **Enclosure** (di bagian kanan editor post).
2.  Masukkan URL demo Anda.
3.  Pada kolom **MIME Type**, isi dengan kata: `Demo`

---

## Lisensi
Proyek ini bersifat *Open Source*. Silakan modifikasi sesuai kebutuhan tema Blogger Anda. 

*Dibuat untuk memudahkan manajemen konten katalog di platform Blogger.*
