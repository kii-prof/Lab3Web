# Laporan Praktikum Lab3Web — CSS Dasar

| | |
|---|---|
| **Nama** | Rizky Fauzan Sobari |
| **NIM** | 312510342 |
| **Kelas** | I252A |
| **Mata Kuliah** | Pemrograman Web |
| **Kampus** | Universitas Pelita Bangsa |

## Tujuan Praktikum

Memahami tiga cara menerapkan CSS pada halaman HTML (inline, internal, dan eksternal) serta penggunaan selector dasar (tag, ID, class, dan descendant).

## Struktur Repository

```
Lab3Web/
├── README.md
├── lab2_css_dasar.html        # hasil akhir (inline + internal + eksternal)
├── style.css                  # CSS eksternal
├── steps/
│   ├── step1_tanpa_css.html
│   ├── step2_inline_css.html
│   └── step3_internal_css.html
└── screenshots/
    ├── 01_tanpa_css.png
    ├── 02_inline_css.png
    ├── 03_internal_css.png
    └── 04_eksternal_css.png
```

---

## Langkah 1 — Membuat Struktur HTML (Tanpa CSS)

Halaman dibuat dengan tag dasar HTML: `<header>` berisi judul `<h1>`, `<nav>` berisi tiga tautan `<a>`, dan `<div id="intro">` berisi judul, paragraf, serta tautan bergaya tombol (`class="button btn-primary"`).

Karena belum ada CSS, browser menampilkan gaya bawaan: teks hitam, tautan biru bergaris bawah, dan semua elemen tersusun ke bawah.

File: `steps/step1_tanpa_css.html`

![Tanpa CSS](screenshots/01_tanpa_css.png)

---

## Langkah 2 — Inline CSS

Inline CSS ditulis langsung pada atribut `style` di dalam tag. Pada paragraf ditambahkan:

```html
<p style="text-align: center; color: #ccd8e4;">...</p>
```

- `text-align: center` → teks paragraf rata tengah.
- `color: #ccd8e4` → warna teks abu-abu kebiruan muda.

Inline CSS hanya berlaku untuk satu elemen itu saja dan memiliki prioritas tertinggi dibanding internal maupun eksternal.

File: `steps/step2_inline_css.html`

![Inline CSS](screenshots/02_inline_css.png)

---

## Langkah 3 — Internal CSS

Internal CSS ditulis di dalam tag `<style>` pada bagian `<head>`, sehingga berlaku untuk seluruh halaman tersebut.

```html
<style>
    body   { font-family: 'Open Sans', sans-serif; }
    header { min-height: 80px; border-bottom: 1px solid #77CCEF; }
    h1     { font-size: 24px; color: #0F189F; text-align: center; padding: 20px 10px; }
    h1 i   { color: #6d6a6b; }
</style>
```

| Selector | Fungsi |
|---|---|
| `body` | Mengatur jenis huruf seluruh halaman |
| `header` | Tinggi minimal 80px dan garis bawah biru muda |
| `h1` | Ukuran 24px, warna biru tua, rata tengah, dengan padding |
| `h1 i` | Selector turunan: teks miring di dalam `h1` berwarna abu-abu |

Hasilnya, judul "CSS Internal dan _Inline CSS_" dan "Hello World" menjadi biru, rata tengah, dan kata _Inline CSS_ berwarna abu-abu.

File: `steps/step3_internal_css.html`

![Internal CSS](screenshots/03_internal_css.png)

---

## Langkah 4 — CSS Eksternal

CSS eksternal ditulis pada file terpisah (`style.css`) dan dihubungkan ke HTML lewat tag `<link>` di dalam `<head>`:

```html
<link rel="stylesheet" href="style.css" type="text/css">
```

Isi `style.css`:

```css
nav { background: #20A759; color: #fff; padding: 10px; }
nav a { color: #fff; text-decoration: none; padding: 10px 20px; }
nav .active, nav a:hover { background: #fff; color: #20A759; }

/* ID Selector */
#intro { background: #418fb1; border: 1px solid #099249; min-height: 100px; padding: 10px; }
#intro h1 { text-align: left; border: 0; color: #fff; }

/* Class Selector */
.button { padding: 15px 20px; background: #ec0606; color: #fdfcfc;
          display: inline-block; margin: 10px; text-decoration: none; }
```

Penjelasan:

- **`nav`, `nav a`** — menu navigasi berlatar hijau dengan tautan putih tanpa garis bawah. Saat kursor diarahkan (`:hover`), latar menjadi putih dan teks hijau.
- **`#intro` (ID selector)** — kotak biru dengan border hijau. `#intro h1` membuat judul di dalamnya rata kiri dan berwarna putih (menimpa gaya `h1` internal karena selector lebih spesifik).
- **`.button` (class selector)** — tautan "Informasi selengkapnya." tampil sebagai tombol merah.

File: `lab2_css_dasar.html` + `style.css`

![CSS Eksternal](screenshots/04_eksternal_css.png)

---

## Perbandingan Tiga Cara Penerapan CSS

| Cara | Lokasi | Cakupan | Prioritas |
|---|---|---|---|
| Inline | Atribut `style` pada tag | Satu elemen | Tertinggi |
| Internal | Tag `<style>` di `<head>` | Satu halaman | Menengah |
| Eksternal | File `.css` lewat `<link>` | Banyak halaman | Terendah (kecuali selector lebih spesifik) |

## Kesimpulan

Inline CSS cocok untuk perubahan kecil pada satu elemen, internal CSS untuk satu halaman, dan CSS eksternal paling efisien untuk dipakai bersama di banyak halaman karena gaya dipisahkan dari struktur HTML. Selector ID, class, dan turunan memungkinkan pengaturan tampilan yang lebih spesifik.
