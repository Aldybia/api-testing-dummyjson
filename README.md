# 🧪 API Testing - DummyJSON

![Postman](https://img.shields.io/badge/Postman-FF6C37?style=for-the-badge&logo=postman&logoColor=white)
![Newman](https://img.shields.io/badge/Newman-6.2.2-brightgreen?style=for-the-badge)
![Assertions](https://img.shields.io/badge/Assertions-8%2F8%20Passed-success?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Completed-blue?style=for-the-badge)

> Implementasi pengujian API menggunakan **Postman** dan **Newman CLI** terhadap endpoint [DummyJSON](https://dummyjson.com) — mencakup positive test cases, negative test cases, dan automated report generation.

---

## 📋 Daftar Isi

- [Tentang Proyek](#tentang-proyek)
- [Tools & Teknologi](#tools--teknologi)
- [Struktur File](#struktur-file)
- [Test Cases](#test-cases)
- [Hasil Pengujian](#hasil-pengujian)
- [Cara Menjalankan](#cara-menjalankan)
- [Laporan Newman](#laporan-newman)

---

## 📖 Tentang Proyek

Proyek ini merupakan implementasi **pengujian API (API Testing)** yang bertujuan untuk memvalidasi fungsionalitas endpoint REST API dari DummyJSON. Pengujian dilakukan secara manual menggunakan Postman dan otomatis menggunakan Newman CLI, mencakup skenario positif dan negatif.

**Base URL:** `https://dummyjson.com`

---

## 🛠️ Tools & Teknologi

| Tool | Versi | Fungsi |
|------|-------|--------|
| [Postman](https://www.postman.com/) | v12.9.4 | Membuat & menjalankan request API |
| [Newman](https://www.npmjs.com/package/newman) | v6.2.2 | Menjalankan collection via CLI |
| [newman-reporter-html](https://www.npmjs.com/package/newman-reporter-html) | Latest | Generate laporan HTML |
| Node.js | v11.14.0 | Runtime untuk Newman |

---

## 📁 Struktur File

```
api-testing-dummyjson/
├── 📄 API dummyJSON.postman_collection2.json   # Postman Collection
├── 📄 dummyJSON-env.environment.json           # Environment Variables
├── 📄 newman-report.html                       # Laporan Hasil Pengujian
└── 📄 README.md                                # Dokumentasi
```

---

## ✅ Test Cases

### 🟢 Positive Test Cases

| # | Nama Test | Method | Endpoint | Expected Status | Assertions |
|---|-----------|--------|----------|----------------|------------|
| 1 | Login User | POST | `/auth/login` | 200 OK | Status 200 ✅, Access token present ✅ |
| 2 | Get Product | GET | `/products` | 200 OK | Status 200 ✅, Min 2 items ✅ |
| 3 | Add Product to Cart | POST | `/carts/add` | 201 Created | Status 201 ✅, Product valid ✅ |

### 🔴 Negative Test Cases

| # | Nama Test | Method | Endpoint | Expected Status | Assertions |
|---|-----------|--------|----------|----------------|------------|
| 1 | Login dengan Password Salah | POST | `/auth/login` | 400 Bad Request | Status 400 ✅ |
| 2 | Add Cart dengan User ID Tidak Valid | POST | `/carts/add` | 404 Not Found | Status 404 ✅ |

---

## 📊 Hasil Pengujian

### Ringkasan

| Metric | Nilai |
|--------|-------|
| **Total Iterations** | 1 |
| **Total Requests** | 9 |
| **Total Assertions** | 8 |
| **Assertions Passed** | ✅ 8/8 (100%) |
| **Total Duration** | 4.6 detik |
| **Total Data Received** | 44.67 KB |
| **Rata-rata Response Time** | 426ms |

### Detail Hasil per Test Case

```
✅ Positive Test Cases
   ├── Login User          → 200 OK     | Status 200 ✓ | Access token present ✓
   ├── Get Product         → 200 OK     | Status 200 ✓ | Min 2 items ✓
   └── Add Product to Cart → 201 Created| Status 201 ✓ | Product valid ✓

✅ Negative Test Cases
   ├── Login Invalid Password    → 400 Bad Request | Status 400 ✓
   └── Add Cart Invalid User ID  → 404 Not Found   | Status 404 ✓
```

---

## 🚀 Cara Menjalankan

### Prasyarat

Pastikan sudah terinstall:
- [Node.js](https://nodejs.org/) (v10 ke atas)
- Newman

```bash
# Install Newman
npm install -g newman

# Install HTML Reporter
npm install -g newman-reporter-html
```

### Jalankan Collection

```bash
# Basic run
newman run "API dummyJSON.postman_collection2.json" --env-var "base_url=https://dummyjson.com"

# Run dengan environment file
newman run "API dummyJSON.postman_collection2.json" -e "dummyJSON-env.environment.json"
```

### Generate Laporan HTML

```bash
newman run "API dummyJSON.postman_collection2.json" \
  --env-var "base_url=https://dummyjson.com" \
  --reporters html \
  --reporter-html-export newman-report.html
```

---

## 📈 Laporan Newman

Laporan hasil pengujian tersedia dalam format HTML di file `newman-report.html`.

Buka file tersebut di browser untuk melihat:
- Ringkasan eksekusi
- Detail setiap request
- Status assertion per test case
- Daftar failures (jika ada)

---


## 📝 Catatan

> Folder **REQRES** dalam collection menggunakan variable `{{reqres_url}}` yang tidak dikonfigurasi dalam pengujian ini, sehingga request pada folder tersebut tidak dapat dieksekusi. Fokus pengujian adalah pada endpoint **DummyJSON**.
