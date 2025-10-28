# 📡 Competitor Data Automation & Network Benchmarking using Mobileum Studio64

## 🗭 Background

Proyek ini bertujuan untuk **mengotomatisasi pengumpulan data performa layanan operator kompetitor** (XL, Indosat, AXIS, Smartfren) menggunakan platform **Mobileum (SIGOS) Active Testing**.
Melalui automasi di **Studio64**, sistem mengeksekusi pengujian jaringan dan aplikasi operator secara paralel untuk mendapatkan data performa serta pengalaman pengguna (*Quality of Experience / QoE*) secara objektif.

🎯 **Tujuan utama:**

* Mendapatkan insight objektif mengenai *Quality of Experience (QoE)* antar operator.
* Membandingkan kecepatan, stabilitas, dan penawaran layanan kompetitor.
* Mengurangi waktu pengumpulan data manual melalui *automation pipeline*.

---

## ⚙️ Tools & Technology

| Komponen                         | Deskripsi                                                        |
| -------------------------------- | ---------------------------------------------------------------- |
| **Mobileum Test Center**         | Pengatur campaign & hasil eksekusi test                          |
| **Studio64**                     | IDE berbasis Eclipse untuk pembuatan & debugging automation test |
| **MTL (Mobileum Test Language)** | Bahasa scripting automation yang digunakan dalam Studio64        |
| **Probes Multi-SIM**             | Perangkat fisik berisi SIM operator berbeda                      |

---

## 🧪 Scope & Features

* Scraping data kuota, pulsa, dan promo dari aplikasi operator (MyTelkomsel, myXL, AXISnet, Smartfren).
* Capture tampilan hasil aplikasi (OCR-based verification).
* Menghitung *response time*, *latency*, dan *success rate*.
* Menjalankan eksekusi otomatis harian via Test Center.

---

## 🔁 Test Flow / Architecture (Based on Project Flow Diagram)

Diagram berikut menggambarkan alur otomasi pengumpulan data kompetitor dari dua kanal utama: **Mobile Apps** dan **UMB (USSD Menu)**.

![Flow Diagram](1a7378f0-897d-4cc8-8de9-4c9aaf0065a9.png)

| Flow  | Channel                                                  | Crawling                                                                                                                                                                                                                     | Parsing                                                                                                                           |
| ----- | -------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| **1** | **Mobile Apps** (IM3, XL, AXIS, mySF, Shopee)            | Data dikumpulkan otomatis dari aplikasi operator menggunakan **SIGOS Studio64**, dengan dukungan **RPA** dan *automation framework* seperti **Cetha / Katalon** untuk melakukan UI interaction (open app, capture, extract). | Hasil tangkapan dikirim ke server parser (**ISYANA**) untuk diekstraksi dan dikonversi ke data kuantitatif (pulsa, kuota, promo). |
| **2** | **UMB (USSD Menus)** (Indosat, AXIS, Smartfren, Tri, XL) | Eksekusi test otomatis dilakukan menggunakan **SIGOS Studio64** melalui *probe* fisik yang menjalankan kode USSD dan menunggu response.                                                                                      | Output text response diolah oleh **Cetha / ISYANA Parser** menjadi dataset yang bisa dibandingkan antar operator.                 |

📊 **Pipeline Summary:**

```
Mobile Apps → SIGOS Studio64 → Cetha / RPA → ISYANA Parser → Data KPI
UMB (USSD)  → SIGOS Probe → Text Extraction (Cetha) → ISYANA Parser → KPI Report
```

---

## 📸 Screenshots & Execution Proofs

### AXIS Automation Result

![AXIS Automation Result](af37fb2b-b63c-4543-a058-23b97d4d8ad8.png)

> Hasil capture otomatis aplikasi **AXISnet**, menampilkan informasi pulsa dan kuota aktif pengguna.

---

### XL Automation Result

![XL Automation Result](f8ee170e-1c95-4e04-942d-319507fe1e33.png)

> Eksekusi **Studio64** berhasil menyelesaikan test di aplikasi **myXL**.
> Terlihat flow node sequence (`Wait`, `Capture`, `Toggle Transaction`) berjalan sukses, dan hasil capture menampilkan halaman paket utama.

---

### Smartfren Automation Result

![Smartfren Automation Result](cd824ede-8636-45d4-aac5-611a9d4de7ed.png)

> Tampilan **Test Center** yang menampilkan device Smartfren di jaringan probe.
> Script menjalankan perintah *touch* dan *input otomatis* untuk masuk ke aplikasi serta memvalidasi halaman utama.

---

## 📊 Results & KPI Analysis

| Operator  | Avg Response Time (sec) | Success Rate (%) | Error Rate (%) |
| --------- | ----------------------- | ---------------- | -------------- |
| Telkomsel | 3.8                     | 99.1             | 0.9            |
| XL        | 3.2                     | 98.7             | 1.3            |
| AXIS      | 2.7                     | 99.3             | 0.7            |
| Smartfren | 3.4                     | 98.9             | 1.1            |

📈 **Insight:**
AXIS menunjukkan waktu respon aplikasi tercepat, sedangkan Telkomsel memiliki stabilitas tertinggi.
Hasil ini digunakan untuk membangun laporan **benchmark kompetitor** yang membantu tim internal dalam *strategic network improvement*.

---

## 🚀 Impact & Learning

✅ Pengumpulan data manual (±3 jam) disingkat menjadi **< 30 menit** via automation.
✅ Proses validasi UI dan *response time* kini otomatis melalui *capture & log parser*.
✅ Menyediakan *daily insight* kompetitor ke tim Network Operation & Strategy.
✅ Mendalami *event-driven scripting* dan *multi-probe orchestration* di sistem Mobileum.

---

## 🧳 Documentation & Artifacts

* 📸 Hasil screenshot automation tiap operator
* 🧹 Script `.mtl` automation workflow

---

