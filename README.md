# 🧩 **FLOW DIAGRAM LENGKAP APLIKASI SHOPEE**

### (High-Level + Detail Alur Pembelian, Pembayaran, Pengiriman, Chat, ShopeePay, SPayLater, dan Seller)

---

# **1. MAIN SYSTEM FLOW (HIGH LEVEL)**

```
 ┌──────────┐
 │ Splash   │
 └────┬─────┘
      ▼
 ┌──────────┐
 │ Login /  │───► Daftar Akun
 │ Register │
 └────┬─────┘
      ▼
 ┌──────────┐
 │   Home   │
 └────┬─────┬─────────────┬───────────┬─────────────┐
      ▼     ▼             ▼           ▼             ▼
  Search  Kategori    Notifikasi   ShopeePay     SPayLater
      │                                  │
      │                                  ▼
      ▼                         Topup / Transfer / Bayar
 ┌──────────┐
 │ Product  │
 │  Detail  │
 └────┬─────┘
      ▼
 ┌──────────┐
 │ Keranjang│
 └────┬─────┘
      ▼
 ┌──────────┐
 │ Checkout │
 └────┬─────┘
      ▼
 ┌──────────┐
 │ Payment  │
 └────┬─────┘
      ▼
 ┌──────────┐
 │ Tracking │
 └────┬─────┘
      ▼
 ┌──────────┐
 │ Complete │
 └──────────┘
```

---

# **2. FLOW: PEMBELIAN PRODUK**

```
Home
   ▼
Search / Kategori
   ▼
Product Detail
   ├── Lihat foto & deskripsi
   ├── Lihat ulasan
   ├── Pilih variasi
   └── Tambah ke Keranjang / Beli Sekarang
         ▼
      Keranjang
         ▼
      Checkout
         ├── Pilih alamat
         ├── Pilih ekspedisi
         ├── Gunakan voucher
         └── Pilih metode pembayaran
                 ▼
              Payment
                 ▼
        Status: Menunggu Pembayaran
                 ▼
        Status: Dikemas Penjual
                 ▼
        Status: Dikirim (tracking paket)
                 ▼
        Status: Pesanan Tiba
                 ▼
           Selesai & Review
```

---

# **3. FLOW: SISTEM PEMBAYARAN**

## 3.1 ShopeePay

```
Checkout
   ▼
Pilih Pembayaran: ShopeePay
   ▼
Masukkan PIN
   ▼
Pembayaran Berhasil → Konfirmasi Pesanan
```

## 3.2 Virtual Account (VA)

```
Checkout
   ▼
Pilih VA (BCA/BRI/Mandiri)
   ▼
Tampilan nomor VA
   ▼
User bayar via ATM/Mbanking
   ▼
Sistem update otomatis
   ▼
Pesanan Diproses
```

## 3.3 SPayLater

```
Checkout
   ▼
Pilih SPayLater
   ▼
Pilih tenor
   ▼
Konfirmasi → Pembayaran berhasil
   ▼
Tambahkan ke tagihan bulan berjalan
```

## 3.4 COD

```
Checkout
   ▼
Pilih COD
   ▼
Pesanan Diproses
   ▼
Bayar saat barang diterima
```

---

# **4. FLOW: TRACKING PESANAN**

```
Pesanan Dibuat
   ▼
Pending Payment
   ▼ (Pembayaran berhasil)
Dikemas Penjual
   ▼
Kurir Menjemput
   ▼
Dikirim
   ▼
Dalam Perjalanan
   ▼
Sampai di tujuan
   ▼
Pesanan Diterima
   ▼
Rating & Review
```

---

# **5. FLOW: SHOPEE CHAT (Pembeli ↔ Penjual)**

```
Product Detail ──► Chat Penjual
   ▼
Chat Window
   ├── Tanya Stok
   ├── Nego harga (opsi penjual)
   ├── Kirim variasi
   ├── Kirim foto
   └── Checkout dari Chat
```

---

# **6. FLOW: SHOPEEPAY**

```
ShopeePay
   ├── Saldo
   ├── Top Up
   │      ├── Transfer Bank
   │      ├── Alfamart/Indomaret
   │      └── e-Wallet lain
   ├── Transfer ke Teman
   ├── Scan QR
   └── Riwayat Transaksi
```

---

# **7. FLOW: SPayLater**

```
SPayLater
   ▼
Ajukan Aktivasi
   ├── Verifikasi KTP
   ├── Selfie
   └── Approval Sistem
   ▼
Limit diberikan
   ▼
Gunakan saat Checkout
   ▼
Tambah ke tagihan bulanan
   ▼
Pembayaran tagihan
```

---

# **8. FLOW: SELLER / PENJUAL**

```
Dashboard Penjual
   ├── Kelola Produk
   │      ├── Tambah Produk
   │      ├── Edit Produk
   │      └── Stok & Variasi
   │
   ├── Pesanan Masuk
   │      ├── Packing
   │      ├── Cetak Resi
   │      └── Pickup / Drop-off
   │
   ├── Chat Pembeli
   ├── Statistik Toko
   └── Penarikan Dana
```
