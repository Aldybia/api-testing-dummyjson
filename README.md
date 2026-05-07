# 🧪 API Testing – DummyJSON E-Commerce

![API Testing](https://img.shields.io/badge/API%20Testing-Postman-orange?style=for-the-badge&logo=postman)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen?style=for-the-badge)
![Pass Rate](https://img.shields.io/badge/Pass%20Rate-100%25-success?style=for-the-badge)
![Platform](https://img.shields.io/badge/Platform-DummyJSON-blue?style=for-the-badge)

> Dokumentasi hasil pengujian API pada platform demo e-commerce **DummyJSON**, mencakup validasi alur **Login**, **Get Products**, dan **Checkout (Cart)** menggunakan Postman.

---

## 📋 Daftar Isi

- [Tentang Project](#-tentang-project)
- [Tools & Teknologi](#-tools--teknologi)
- [Struktur Repository](#-struktur-repository)
- [Skenario Pengujian](#-skenario-pengujian)
- [Hasil Pengujian](#-hasil-pengujian)
- [Cara Menggunakan Collection](#-cara-menggunakan-collection)
- [Environment Variables](#-environment-variables)

---

## 📖 Tentang Project

Project ini merupakan studi kasus **API Testing** pada platform demo e-commerce [DummyJSON](https://dummyjson.com). Pengujian difokuskan pada tiga alur utama:

1. **Autentikasi** – Login pengguna dan validasi JWT token
2. **Produk** – Pengambilan daftar produk
3. **Cart/Checkout** – Simulasi penambahan produk ke keranjang belanja

Pengujian mencakup **Positive Test Cases** (alur normal) dan **Negative Test Cases** (validasi error handling).

---

## 🛠 Tools & Teknologi

| Tool | Kegunaan |
|------|----------|
| [Postman](https://www.postman.com/) | API Testing & Automation |
| [DummyJSON](https://dummyjson.com/) | Platform demo e-commerce (API publik) |
| JWT (JSON Web Token) | Mekanisme autentikasi |
| Environment Variables | Manajemen token otomatis |

---

## 📁 Struktur Repository

```
api-testing-dummyjson/
├── 📄 README.md
├── 📦 API_dummyJSON.postman_collection.json   # Postman Collection
└── 📊 Laporan_API_Testing_DummyJSON.pdf       # Laporan hasil pengujian
```

---

## 🗂 Skenario Pengujian

### ✅ Positive Test Cases

| No | Test Case | Method | Endpoint | Expected |
|----|-----------|--------|----------|----------|
| TC-01 | Login dengan kredensial valid | `POST` | `/auth/login` | 200 OK + Token |
| TC-02 | Ambil daftar produk | `GET` | `/products` | 200 OK + Data produk |
| TC-03 | Tambahkan produk ke cart | `POST` | `/carts/add` | 201 Created |

### ❌ Negative Test Cases

| No | Test Case | Method | Endpoint | Expected |
|----|-----------|--------|----------|----------|
| TC-04 | Login dengan password salah | `POST` | `/auth/login` | 400 Bad Request |
| TC-05 | Add cart dengan user ID tidak valid | `POST` | `/carts/add` | 404 Not Found |

---

## 📊 Hasil Pengujian

| Test Case | Tipe | Status Code | Hasil |
|-----------|------|-------------|-------|
| TC-01 – Login Valid | Positive | `200 OK` | ✅ PASS |
| TC-02 – Get Products | Positive | `200 OK` | ✅ PASS |
| TC-03 – Add to Cart | Positive | `201 Created` | ✅ PASS |
| TC-04 – Login Invalid Password | Negative | `400 Bad Request` | ✅ PASS |
| TC-05 – Add Cart Invalid User | Negative | `404 Not Found` | ✅ PASS |

```
Total Test Cases : 5
PASS             : 5
FAIL             : 0
Pass Rate        : 100%
```

---

## 🚀 Cara Menggunakan Collection

### 1. Import Collection ke Postman
1. Buka **Postman**
2. Klik **Import** → pilih file `API_dummyJSON.postman_collection.json`
3. Collection **"API dummyJSON"** akan muncul di sidebar

### 2. Setup Environment
1. Klik **Environments** → **Import** atau buat manual
2. Buat environment baru bernama `dummyJSON-env`
3. Tambahkan variable berikut:

| Variable | Initial Value |
|----------|--------------|
| `base_url` | `https://dummyjson.com` |
| `token` | *(kosongkan, akan terisi otomatis)* |

### 3. Jalankan Request
1. Pilih environment **dummyJSON-env**
2. Jalankan **Login User** terlebih dahulu → token akan tersimpan otomatis
3. Jalankan request lainnya sesuai urutan

---

## 🔐 Environment Variables

Token disimpan otomatis menggunakan **Postman Scripts** pada request Login:

```javascript
let response = pm.response.json();
pm.environment.set("token", response.accessToken);
```

Token kemudian digunakan di header request berikutnya:

```
Authorization: Bearer {{token}}
```

---

## 📄 Laporan

Laporan lengkap hasil pengujian tersedia di file:
📊 [`Laporan_API_Testing_DummyJSON.pdf`](./Laporan_API_Testing_DummyJSON.pdf)

---

*Dibuat untuk keperluan pembelajaran API Testing | DummyJSON | Postman | 2026*
