***

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

1.  **Versi:** Gunakan kata "Version" di awal nama label.
    *   *Contoh:* `Version v1` atau `Version v3.1`
2.  **Harga:** Gunakan kata "Rp" untuk menampilkan nominal harga.
    *   *Contoh:* `Rp 175.000`
3.  **Premium/Gratis:**
    *   Jika postingan memiliki label **"Premium"**, maka badge status akan otomatis berubah menjadi "PREMIUM".
    *   Jika tidak ada label "Premium", maka otomatis tertulis "Gratis".

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
