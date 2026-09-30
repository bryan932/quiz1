# Laporan Kuis 1 Pemrograman Web

| | |
|---|---|
| Nama | Bryan Darrick Pangedo |
| NRP | 5025251198 |
| Departemen | Teknik Informatika, ITS |
| Website | https://bryan932.github.io/quiz1 |

Website portofolio mahasiswa bertema **Kota Medan**, berisi perkenalan diri, kota asal, kuliner khas, dan tempat wisata.

---

## 1. Konsep Desain dan Struktur Website

### 1.1 Konsep Desain

Desainnya saya buat bersih, ringan, dan konsisten. Semua halaman memakai kerangka yang sama supaya pengunjung tidak bingung saat berpindah halaman:

- **Navbar** di atas dengan menu Home, Profil, Kota Asal, Kuliner Khas, dan Wisata. Menu halaman yang sedang dibuka dibuat lebih tebal sebagai penanda posisi.
- **Konten utama** di tengah, disusun dengan kartu (card) dan grid.
- **Footer** berisi nama, NRP, dan tautan singkat.

Warna dasarnya putih dengan aksen biru untuk tombol, label, dan ikon. Teks utama berwarna gelap dan teks deskripsi abu-abu supaya hierarkinya jelas. Halaman dengan banyak item (kuliner dan wisata) memakai tiga kartu sejajar, sedangkan Profile dan Hometown memakai satu kartu besar di tengah karena isinya lebih fokus.

### 1.2 Struktur Halaman dan Route

| Halaman | URL | File |
|---|---|---|
| Homepage | `/quiz1` | `index.html` |
| Profile | `/quiz1/profile` | `profile/index.html` |
| Hometown | `/quiz1/hometown` | `hometown/index.html` |
| Local Food | `/quiz1/food` | `food/index.html` |
| Tourist Places | `/quiz1/tourist` | `tourist/index.html` |

### 1.3 Struktur Folder

```
quiz1/
├── index.html
├── style.css
├── img/
├── profile/index.html
├── hometown/index.html
├── food/index.html
└── tourist/index.html
```

### 1.4 Isi Tiap Halaman

- **Homepage**: sapaan, empat tombol cepat, dan empat kartu ringkasan menuju halaman lain.
- **Profile**: foto, nama, NRP, label kampus dan jurusan, biodata singkat, dan empat kotak informasi.
- **Hometown**: foto Kota Medan, deskripsi kota, dan tiga fakta menarik (iklim, pendidikan, heritage).
- **Local Food**: tiga kuliner khas Medan, yaitu Soto Medan, Bika Ambon, dan Lontong Medan.
- **Tourist Places**: tiga destinasi, yaitu Danau Toba, Kesawan City Walk, dan Istana Maimun.

---

## 2. Screenshot Halaman Final

### Homepage

<img width="1440" height="784" alt="Screenshot 2026-09-30 at 15 57 09" src="https://github.com/user-attachments/assets/99a0b5d1-76a7-4979-ba91-3b580dfcf527" />

### Profile

<img width="1440" height="900" alt="Screenshot 2026-09-30 at 15 57 37" src="https://github.com/user-attachments/assets/ed5eef51-8fde-4932-a7ab-0bbb902bd524" />

### Hometown

<img width="1440" height="900" alt="Screenshot 2026-09-30 at 15 57 49" src="https://github.com/user-attachments/assets/81a84a81-ed60-4b64-8624-15ea6c94b991" />

### Local Food
<img width="1440" height="900" alt="Screenshot 2026-09-30 at 15 57 53" src="https://github.com/user-attachments/assets/7202ff42-e5ab-490d-b280-d7bd1e562b75" />


### Tourist Places

![Uploading Screenshot 2026-09-30 at 15.57.56.png…]()

---

## 3. Penjelasan Kode dan Pilihan Implementasi

### 3.1 Bootstrap 5 lewat CDN

```html
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet">
<link href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.11.3/font/bootstrap-icons.css" rel="stylesheet">
<link href="/quiz1/style.css" rel="stylesheet">
```

Saya memakai Bootstrap karena tampilan yang dirancang (navbar, kartu, grid tiga kolom, tombol outline) sudah tersedia sebagai komponen, jadi kodenya lebih pendek dan responsif tanpa menulis banyak CSS. Bootstrap Icons dipakai untuk ikon menu dan tombol. `style.css` dimuat terakhir supaya bisa menambah atau menimpa gaya bawaan Bootstrap.

### 3.2 Routing dengan folder `index.html`

Setiap halaman ada di foldernya sendiri dengan nama `index.html`. Saat server menerima `/quiz1/profile`, ia otomatis membuka `profile/index.html`, jadi URL sesuai ketentuan soal tanpa ekstensi `.html`. Semua link memakai path absolut:

```html
<a class="nav-link" href="/quiz1/profile/">Profil</a>
```

Path absolut membuat link yang sama tetap benar dari halaman mana pun, karena tidak bergantung pada posisi file yang sedang dibuka.

### 3.3 Navbar dan penanda menu aktif

```html
<nav class="navbar navbar-expand-md bg-white shadow-sm">
  ...
  <a class="nav-link active" aria-current="page" href="/quiz1/hometown/">Kota Asal</a>
</nav>
```

`navbar-expand-md` membuat menu tampil mendatar di layar besar dan berubah jadi tombol hamburger di layar kecil. Class `active` hanya diberikan ke menu halaman yang sedang dibuka, dan `style.css` mengubahnya menjadi teks hitam tebal.

### 3.4 Grid dan kartu

```html
<div class="row g-4">
  <div class="col-lg-4">
    <div class="card-x overflow-hidden h-100 position-relative">...</div>
  </div>
</div>
```

`row` dengan `col-lg-4` menghasilkan tiga kolom sejajar di layar lebar yang otomatis turun jadi satu kolom di layar kecil. `g-4` memberi jarak antarkartu dan `h-100` menyamakan tinggi kartu. Kartu memakai class buatan sendiri, `card-x`, yang berisi border tipis dan sudut membulat.

### 3.5 Gambar

```html
<img src="/quiz1/img/Soto.jpg" alt="Soto Medan" class="w-100 object-fit-cover" style="height:250px">
```

`w-100` membuat gambar selalu selebar kartu, sedangkan `object-fit-cover` menjaga foto tidak gepeng walau rasio aslinya berbeda-beda. Ukuran tinggi dibuat tetap supaya semua kartu rapi. Atribut `alt` diisi agar gambar tetap bermakna bagi pembaca layar. Foto dikonversi ke JPG dan dikecilkan resolusinya supaya halaman cepat dimuat.

### 3.6 CSS tambahan (`style.css`)

| Class | Fungsi |
|---|---|
| `.card-x` | border tipis dan sudut membulat untuk kartu |
| `.badge-top` | label kategori yang menempel di pojok kanan atas foto |
| `.info-box` | kotak abu-abu berisi data pada halaman Profile |
| `.pill` | label kecil berbentuk kapsul untuk kampus dan jurusan |
| `.tag` | label biru di atas judul halaman |
| `.nav-link.active` | penanda menu yang sedang dibuka |

Class ini dipisah ke `style.css` supaya bisa dipakai ulang di semua halaman dan perubahan gaya cukup dilakukan di satu tempat.

### 3.7 Pilihan lain

- **Tanpa JavaScript buatan sendiri.** Semua konten statis, jadi tidak perlu logika tambahan. Satu-satunya JavaScript adalah bundle Bootstrap yang membuat menu hamburger bisa dibuka.
- **Satu file CSS bersama** untuk semua halaman, bukan CSS di tiap file.
- **Hosting GitHub Pages**, karena gratis dan langsung menyajikan struktur folder sebagai route.

---

## 4. Analisis dan Evaluasi

**Kelebihan**

- Tampilan konsisten di semua halaman karena kerangka dan gaya yang sama.
- Responsif: layout menyesuaikan layar HP, tablet, dan desktop lewat grid Bootstrap.
- Ringan dan cepat dimuat karena hanya HTML statis, satu file CSS, dan gambar yang sudah dikecilkan.
- Route sesuai ketentuan soal dan mudah diingat.
- Kode mudah dibaca dan dirawat karena setiap halaman berdiri sendiri.

---

## 5. Kesimpulan

Website portofolio lima halaman bertema Kota Medan berhasil dibuat dengan tampilan yang konsisten, responsif, dan route sesuai ketentuan soal, lalu dipublikasikan lewat GitHub Pages. Pemakaian Bootstrap mempercepat pembuatan layout, sedangkan struktur folder `index.html` membuat URL menjadi rapi tanpa ekstensi. Dari tugas ini saya jadi lebih paham hubungan antara struktur folder, path, dan alamat web, serta cara menyusun halaman yang mudah dirawat.
