# 🥋 Taekwondo Garuda Club Web App

Aplikasi web lengkap untuk Taekwondo Garuda Club. Menggabungkan situs informasi klub (Blog) dan sistem *E-commerce* sederhana untuk penjualan perlengkapan. Dibangun menggunakan **Flask (Python)**, **MongoDB (PyMongo)**, dan **UIkit 3** untuk *frontend*.

## ✨ Fitur Utama

  * **Sistem Admin (CMS):** Login, Dashboard, Manajemen Produk (CRUD), dan Manajemen Blog (CRUD).
  * **E-commerce:** Daftar produk, Halaman detail produk, Keranjang Belanja berbasis sesi, dan *Checkout* via WhatsApp.
  * **Sistem Ulasan (Review):** Pengguna dapat memberikan *rating* dan komentar pada produk.
  * **Kontak:** Form kontak dengan integrasi Flask-Mail.
  * **SEO:** Sitemap dinamis dan meta tag Open Graph untuk berbagi di media sosial.
  * **Desain Modern:** Menggunakan UIkit 3 dengan kustomisasi warna merah khas Taekwondo.

## 🛠️ Instalasi dan Setup Proyek

### 1\. Prasyarat

Pastikan Anda telah menginstal:

  * Python 3.8+
  * pip (Pengelola paket Python)
  * MongoDB Atlas Account (untuk `MONGO_URI`)
  * Cloudinary Account (untuk *storage* gambar)
  * Akun Gmail/Layanan SMTP lain (untuk `Flask-Mail`)

### 2\. Kloning Repositori

```bash
git clone https://github.com/IshikawaUta/taekwondo_garuda_club.git
cd taekwondo_garuda_club
```

### 3\. Setup Virtual Environment

```bash
# Untuk Linux/macOS
python3 -m venv venv
source venv/bin/activate

# Untuk Windows
python -m venv venv
venv\Scripts\activate
```

### 4\. Instalasi Dependensi

Instal semua pustaka Python yang diperlukan dari `requirements.txt`:

```bash
pip install -r requirements.txt
```

### 5\. Konfigurasi Lingkungan (`.env`)

Buat file bernama **`.env`** di root proyek dan isi dengan variabel lingkungan Anda. **Ganti semua nilai *placeholder* dengan kredensial Anda yang sebenarnya.**

> ⚠️ **CATATAN PENTING KEAMANAN:** Pastikan file `.env` ini ditambahkan ke `.gitignore` Anda dan **tidak pernah** di-*commit* ke repositori publik.

```ini
SECRET_KEY='[GANTI_DENGAN_KEY_ANDA]'
# MongoDB Atlas
MONGO_URI='mongodb+srv://[USER]:[PASSWORD]@cluster0.btmnj9t.mongodb.net/garuda_db?retryWrites=true&w=majority'
# WhatsApp (Gunakan kode negara, ex: 628...)
WHATSAPP_NUMBER='[NOMOR_WHATSAPP_ANDA]'
# Cloudinary
CLOUDINARY_CLOUD_NAME='[CLOUD_NAME_ANDA]'
CLOUDINARY_API_KEY='[API_KEY_ANDA]'
CLOUDINARY_API_SECRET='[API_SECRET_ANDA]'
# Flask-Mail (ex: Gmail SMTP)
MAIL_SERVER='smtp.gmail.com'
MAIL_PORT=587
MAIL_USE_TLS=True
MAIL_USERNAME='[EMAIL_ANDA]'
MAIL_PASSWORD='[PASSWORD_APLIKASI_EMAIL_ANDA]'
```

### 6\. Menjalankan Aplikasi

Aplikasi akan berjalan di `http://127.0.0.1:5000/`.

```bash
python app.py
```

## 📂 Struktur File Proyek

```
taekwondo-garuda-club/
├── .env                       # Variabel lingkungan (DIKECUALIKAN dari Git)
├── app.py                     # Logika utama Flask (Rute, Fungsi)
├── config.py                  # Memuat konfigurasi dari .env
├── requirements.txt           # Daftar dependensi Python
├── vercel.json                # Konfigurasi deployment Vercel
├── robots.txt                 # File standar untuk crawler
├── favicon.ico
├── static/                    # Aset statis
│   ├── css/
│   │   ├── style.css          # CSS Kustom (Warna Taekwondo)
│   │   └── uikit*.css         # File UIkit
│   ├── js/
│   │   └── uikit*.js          # File UIkit
│   └── images/                # (Asumsi) Tempat menyimpan banner, logo, dll.
└── templates/                 # Template HTML (Jinja2)
    ├── includes/
    │   ├── header.html        # Navbar & Offcanvas
    │   └── footer.html
    ├── admin/
    │   ├── login.html
    │   ├── dashboard.html
    │   ├── manage_products.html
    │   └── manage_blog.html
    ├── blog/
    │   ├── blog_list.html
    │   └── blog_post.html
    ├── product/
    │   ├── product_list.html
    │   ├── product_detail.html
    │   └── cart.html
    └── base.html              # Template dasar untuk semua halaman
    └── index.html             # Beranda
    └── about.html             # Tentang Kami
    └── contact.html           # Kontak
```

## 🚀 Deployment ke Vercel

Proyek ini telah dikonfigurasi untuk *deployment* mudah menggunakan **Vercel** dengan *build step* Python.

### 1\. Konfigurasi Vercel

File `vercel.json` sudah disiapkan untuk mengarahkan semua *traffic* ke `app.py`:

```json
{
  "version": 2,
  "builds": [
    {
      "src": "app.py",
      "use": "@vercel/python"
    }
  ],
  "routes": [
    {
      "src": "/(.*)",
      "dest": "app.py"
    }
  ]
}
```

### 2\. Langkah Deployment

1.  Commit dan *push* kode Anda ke GitHub/GitLab/Bitbucket.
2.  Buka Vercel Dashboard dan impor repositori Anda.
3.  Saat diminta, pastikan Anda menambahkan **semua variabel lingkungan** dari file `.env` ke **Environment Variables** di Pengaturan Proyek Vercel Anda.
      * Contoh: `SECRET_KEY`, `MONGO_URI`, `CLOUDINARY_API_SECRET`, dll.
4.  Vercel akan secara otomatis mendeteksi konfigurasi dan men-deploy aplikasi Flask Anda.

### 3\. Post-Deployment

Setelah *deployment* berhasil, pastikan untuk:

1.  Mengganti URL `Sitemap` di `robots.txt` dari `http://localost:5000/sitemap.xml` menjadi URL domain Anda yang sebenarnya (misalnya, `https://garudataekwondo.com/sitemap.xml`).
2.  Membuat pengguna Admin awal (jika belum otomatis dibuat oleh `app.py`).
