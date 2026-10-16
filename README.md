# 🚀 API Automation Testing Portfolio - Kelas Otomesyen

Proyek ini berisi pengujian otomatisasi API (*API Automation Testing*) berbasis Postman yang mencakup pengujian fungsionalitas **Authentication** dan **E2E Product CRUD Lifecycle**.

---

## 📌 Target API & Environment
* **Base URL**: `https://api-test.kelasotomesyen.com`
* **Environment**: Staging
* **Authentication Method**: Bearer Token

---

## 🧪 Skenario Pengujian

### 1. Auth Module (`01 - Auth`)
* **`POST /api/login` (Login Success)**: Validasi login berhasil dan menyimpan Bearer Token ke *Environment Variable* secara otomatis.
* **`POST /api/login` (Login Invalid)**: Validasi penanganan kredensial tidak valid (Status `400` / `401`).
* **`POST /api/logout` (Logout Success)**: Validasi logout dengan Bearer Token valid (Status `200` / `204`).
* **`POST /api/logout` (Logout Unauthorized)**: Validasi akses logout tanpa menyertakan token (Status `401`).

### 2. Products Module (`02 - Products`)
* **`GET /api/products` (Get All Products)**: Validasi daftar produk dan pencatatan ID produk secara dinamis.
* **`POST /api/products` (Create Product)**: Pembuatan produk baru dengan *pre-request script* tanggal otomatis (`today`) dan penyimpanan `created_product_id`.
* **`GET /api/products/:id` (Get Product Detail)**: Validasi detail produk berdasarkan `created_product_id`.
* **`PATCH /api/products/:id` (Update Product)**: Pembaruan data atribut harga dan stok produk.
* **`DELETE /api/products/:id` (Delete Product)**: Penghapusan produk & pembersihan (*cleanup/unset*) variabel environment secara otomatis.

---

## 🛠️ Fitur Otomatisasi Utama
* **Dynamic Variable Chaining**: Pemanfaatan *Post-response script* untuk meneruskan parameter *token* dan *product ID* antar-request secara otomatis.
* **Pre-request Date Generator**: Penanganan *payload* dinamis berbasis tanggal hari ini dengan format `YYYY-MM-DD`.
* **Environment Cleanup**: Menghapus variabel sementara (`unset`) setelah proses `DELETE` berhasil dieksekusi.
* **Assertions & Validations**: Pemeriksaan HTTP Status Code, Response Time, dan JSON Response structure.

---

## 📊 Hasil Eksekusi Test Runner
 Seluruh **17 test assertions** berhasil lulus (**100% PASS**) pada pengujian Collection Runner.
