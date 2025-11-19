
## Ringkasan Profesional

Profesional Quality Assurance yang berorientasi detail dengan pengalaman komprehensif dalam pengujian manual dan dasar-dasar automasi.
Terampil dalam merancang test case, mengeksekusi pengujian fungsional & API, serta melakukan bug tracking.
Mampu memanfaatkan SQL untuk validasi data di sisi backend dan memahami alur kerja SDLC agar produk memenuhi standar kualitas.
Memiliki pengetahuan dalam pemanfaatan AI dan automasi untuk meningkatkan efisiensi serta akurasi pengujian.

---

## Daftar Proyek Portofolio

1. [Proyek 1: Dokumentasi skenario pengujian Positive & Negative Testing pada modul Customer, Prospek, Quotation, Approval, dan Sales Order di CRM/ERP.](#proyek-1-dokumentasi-skenario-pengujian)
2. [Proyek 2: Validasi Data Pricelist Produk dengan SQL Query.](#proyek-2-validasi-data-pricelist-dengan-sql-query)
3. [Proyek 3: Analisis Alur & Hak Akses Pengguna (Flowchart RBAC).](#proyek-3-analisis-alur-kerja--hak-akses-pengguna)

---

## Proyek 1: Dokumentasi Skenario Pengujian

Proyek ini menunjukkan kemampuan saya membuat **positive & negative test case** yang terstruktur pada modul **Customer, Prospek, Quotation, Approval, dan Sales Order** di sistem CRM/ERP.

### A. Test Case Positif

| ID Tes     | Prioritas | Modul    | Judul Skenario                            | Prasyarat                                | Langkah-langkah                                                           | Data Uji     | Hasil yang Diharapkan      |
| ---------- | --------- | -------- | ----------------------------------------- | ---------------------------------------- | ------------------------------------------------------------------------- | ------------ | -------------------------- |
| TC-CUST-01 | High      | Customer | Membuat Customer baru dengan data minimal | User 'Sales' sudah login.                | Isi data tanpa NPWP, Sage Code, Email, HP → pilih tipe customer → simpan. | Sales, Fleet | Customer baru tersimpan.   |
| TC-CUST-02 | Medium    | Customer | Menambahkan "Unit Owned"                  | Customer sudah ada.                      | Buka data customer → tab Unit Owned → tambah unit → simpan.               | ALUMINDO     | Data unit tersimpan.       |
| TC-CUST-03 | Medium    | Customer | Menambahkan "Contact & Delivery Address"  | Customer sudah ada.                      | Buka customer → create contact → isi alamat → simpan.                     | ALUMINDO     | Kontak & alamat tersimpan. |
| TC-PROS-01 | High      | Prospek  | Membuat Prospek baru                      | Sales login, customer & produk tersedia. | Buka prospek → pilih customer → tambah produk → simpan.                   | Produk MH    | Prospek baru tersimpan.    |
| TC-PROS-02 | Medium    | Prospek  | Verifikasi tombol info stok produk        | Prospek dengan line produk sudah ada.    | Buka prospek → klik tombol info.                                          | -            | Pop-up stok produk tampil. |

### B. Test Case Negatif

| ID Tes       | Prioritas | Modul       | Judul Skenario                  | Prasyarat                                 | Langkah-langkah                         | Data Uji         | Hasil yang Diharapkan                         |
| ------------ | --------- | ----------- | ------------------------------- | ----------------------------------------- | --------------------------------------- | ---------------- | --------------------------------------------- |
| TC-CUST-04-N | High      | Customer    | Membuat Customer tanpa nama     | Sales login                               | Create customer tanpa nama → simpan.    | Nama kosong      | Error: *Nama Customer wajib diisi*.           |
| TC-CUST-05-N | Medium    | Customer    | Unit Owned format salah         | Customer ada                              | Isi field angka dengan teks → simpan.   | Tahun: "duaribu" | Error: *Tahun harus berupa angka*.            |
| TC-PROS-04-N | High      | Prospek     | Prospek tanpa produk            | Sales login, pilih customer               | Create prospek tanpa produk → simpan.   | -                | Error: *Minimal 1 produk harus ditambahkan*.  |
| TC-QUO-05-N  | High      | Quotation   | Diskon melebihi wewenang        | Sales login, Quotation ada                | Input diskon > limit → simpan.          | Sales, 50%       | Error: *Diskon melebihi batas wewenang*.      |
| TC-QUO-06-N  | High      | Quotation   | Quotation tanpa Pricelist       | Customer X tanpa Pricelist                | Buat prospek → buat quotation → simpan. | Customer X       | Error: *Pricelist tidak ditemukan*.           |
| TC-APP-04-N  | High      | Approval    | Approve diri sendiri            | Sales login, Quotation butuh approval     | Buka Quotation → klik Approve           | Sales            | Tombol Approve hidden/disabled.               |
| TC-APP-05-N  | Medium    | Approval    | BM yang salah approve           | BM B login, Quotation butuh approval BM A | Buka Quotation → klik Approve           | BM_B             | Error: *Anda tidak memiliki wewenang*.        |
| TC-SO-04-N   | High      | Sales Order | SO dari Quotation belum approve | PM login, Quotation waiting approval      | Buka Quotation → Create SO              | PM               | Tombol Create SO disabled.                    |
| TC-SO-05-N   | High      | Sales Order | SO dari Quotation bobot < 70    | PM login, Quotation approved bobot 50     | Buka Quotation → Create SO              | Bobot 50         | Error: *Bobot Prospek ≥ 70 untuk membuat SO*. |

---

## Proyek 2: Validasi Data Pricelist dengan SQL Query

Proyek ini mendemonstrasikan penggunaan **SQL Query** untuk validasi data di modul *Product Pricelist*.

### A. Query Update Data

```sql
UPDATE product_pricelist 
SET ktg_business_category_id = NULL, 
    ktg_is_pricelist_spss = TRUE 
WHERE id = 123;
```

**Tujuan:**

1. Mengosongkan kategori bisnis (set NULL).
2. Mengaktifkan flag `is_pricelist_spss`.
3. Berlaku hanya pada record dengan `id=123`.

---

### B. Query Validasi Data

```sql
SELECT name->>'en_US' AS name, * 
FROM product_pricelist 
WHERE name->>'en_US' LIKE '%Sparepart%';
```

**Tujuan:**

1. Menampilkan semua pricelist dengan nama mengandung kata *Sparepart*.
2. Mengubah kolom JSON `name` menjadi teks biasa agar mudah dibaca.

---

## Proyek 3: Analisis Alur Kerja & Hak Akses Pengguna
![Flowchart](./images/flowchart.png)  
📌 [Link Flowchart](https://drive.google.com/file/d/1lBxgUyG-dKvn67-CVGJuSbCVPKOl09aD/view?usp=sharing)

### A. Ringkasan Alur

Flowchart menggambarkan **Role-Based Access Control (RBAC)** untuk modul Customer:

* **Branch Manager** → Lihat semua customer di cabang + tambah customer baru.
* **Sales** → Tambah customer baru + lihat hanya data miliknya sendiri.
* **Admin Sales** → Lihat semua customer (read-only).

### B. Analisis Kekuatan

* **Pemisahan Tugas**: Wewenang antara BM, Sales, dan Admin jelas.
* **Least Privilege**: Role hanya punya hak minimum yang dibutuhkan.
* **Kontrol Kualitas**: Adanya validasi data di level BM & Sales.

### C. Rekomendasi QA

1. **Edit & Hapus Data** → perlu diuji siapa yang berhak melakukan update/delete.
2. **Transfer Customer** → jika Sales resign, BM harus bisa reassignment customer.
3. **Kolaborasi Tim** → skenario berbagi akses customer antar Sales perlu diuji.

---
