# 📡 Competitor Data Automation & Network Benchmarking using Mobileum Studio64

## 🧭 Background

Proyek ini bertujuan untuk **mengotomatisasi pengumpulan data performa layanan operator kompetitor** (Telkomsel, XL, Indosat, Tri) menggunakan platform **Mobileum (SIGOS) Active Testing**.  
Melalui automasi yang dikembangkan di **Studio64**, sistem dapat mengeksekusi tes jaringan, menjalankan USSD, dan mengambil tangkapan layar aplikasi operator untuk mendapatkan data kuantitatif terkait performa jaringan.

🎯 **Tujuan utama:**  
- Mendapatkan insight objektif mengenai *Quality of Experience (QoE)* antar operator.  
- Membandingkan kecepatan, stabilitas, dan penawaran layanan kompetitor.  
- Mengurangi waktu pengumpulan data manual melalui automation pipeline.

---


## ⚙️ Tools & Technology

| Komponen | Deskripsi |
|-----------|------------|
| **Mobileum Test Center** | Pengatur campaign & hasil eksekusi test |
| **Studio64** | IDE berbasis Eclipse untuk pembuatan & debugging automation test |
| **MTL (Mobileum Test Language)** | Bahasa scripting automation yang digunakan dalam Studio64 |
| **Probes Multi-SIM** | Perangkat fisik dengan SIM operator berbeda |
| **Report Manager / CSV Parser** | Ekstraksi hasil & visualisasi data KPI |

---

## 🧪 Scope & Features

- Scraping data kuota, pulsa, dan promo dari aplikasi operator (MyTelkomsel, MyXL, Bima+)
- Menjalankan USSD otomatis (`*123#`, `*888#`, `*111#`)
- Capture screenshot hasil tampilan UI (OCR-based verification)
- Menghitung response time, latency, dan success rate
- Jadwal eksekusi otomatis via Test Center (harian/mingguan)
- Ekspor hasil ke CSV dan analisis otomatis dengan Excel / Grafana

---

## 🔁 Test Flow / Architecture

📸 Screenshots & Execution Proofs
AXIS Automation Result

Contoh hasil capture otomatis aplikasi AXISnet, menunjukkan informasi pulsa dan kuota aktif pengguna.

XL Automation Result

Eksekusi Studio64 berhasil menyelesaikan test pada aplikasi myXL.
Terlihat flow node sequence (Wait, Capture, Toggle Transaction) berjalan sukses dan hasil capture menampilkan halaman paket utama.

Smartfren Automation Result

Tampilan Test Center yang menampilkan device Smartfren di jaringan probe.
Script menjalankan perintah touch & input otomatis untuk masuk ke aplikasi dan validasi halaman utama.

📊 Results & KPI Analysis
Operator	Avg Response Time (sec)	Success Rate (%)	Error Rate (%)
Telkomsel	3.8	99.1	0.9
XL	3.2	98.7	1.3
AXIS	2.7	99.3	0.7
Smartfren	3.4	98.9	1.1

📈 Insight:
AXIS menunjukkan waktu respon aplikasi tercepat, sedangkan Telkomsel memiliki stabilitas tertinggi.
Hasil digunakan untuk membangun laporan benchmark kompetitor yang dipakai tim internal dalam strategic network improvement.

🚀 Impact & Learning

✅ Pengumpulan data manual (±3 jam) disingkat jadi < 30 menit via automation.
✅ Proses validasi UI dan response time kini otomatis via capture & log parser.
✅ Menyediakan insight harian kompetitor ke tim Network Operation & Strategy.
✅ Mendalami event-driven scripting dan multi-probe orchestration pada sistem Mobileum.

🧾 Documentation & Artifacts

📸 Hasil screenshot automation tiap operator

📂 Export report CSV hasil test campaign

🧩 Script .mtl automation workflow

📊 Dashboard KPI summary (daily/weekly auto-report)

🧠 Takeaways

Pengalaman ini memperkuat kemampuan saya dalam:

Telecommunication QA Automation & Competitive Benchmarking

Data Scraping yang Etis dan Terstruktur

Integrasi automation test ke reporting system

Analisis KPI berbasis Mobileum & real device probe

Dengan Mobileum Studio64, saya membangun sistem automasi yang mampu mengumpulkan data kompetitor secara sah, efisien, dan siap digunakan untuk pengambilan keputusan berbasis data.
