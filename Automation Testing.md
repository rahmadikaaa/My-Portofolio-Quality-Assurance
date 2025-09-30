# 📊 Portofolio Proyek: Crawling Data Harga Paket USSD/UMB Multi-Kota

## 🎯 Tujuan
Mengembangkan sistem **Otomatisasi USSD Terdistribusi** untuk crawling data harga paket internet dari berbagai operator seluler (Telkomsel, XL, Indosat, Tri, Smartfren) secara **multi-geografis**.  
Sistem ini memungkinkan pengumpulan harga yang akurat sesuai lokasi pelanggan, mendukung analisis variasi tarif regional (*De-Averaging*).

---

## 🧭 Fase I – Penentuan Lingkup Strategis & KPI
**Fokus:** Apa yang diuji dan bagaimana menilai keberhasilan.  

- **Lingkup:** Data harga paket internet dari 5 operator di 6 kota besar (Jakarta, Bandung, Surabaya, Bali, Medan, Makassar).  
- **KPI Utama:**
  - Latensi menu USSD < 5 detik.  
  - Tingkat keberhasilan navigasi end-to-end > 95%.  
  - Integritas data harga (tidak ada teks terpotong/salah parsing).  

---

## 🛠️ Fase II – Konfigurasi Lingkungan & Desain Skenario Uji
**Fokus:** Siapkan probe, skenario, dan skrip crawling.  


- **Arsitektur:**
  - **Probe Terdistribusi:** SIM fisik ditempatkan di kota target, dijalankan dengan perangkat uji (contoh: Mobileum/SIGOS probe).  
  - **Pusat Kontrol:** SITE (Integrated Test Environment) untuk orkestrasi eksekusi.  

📷 **Contoh Dasar Lingkup Uji**  
Sebagai bagian dari penentuan lingkup, berikut setup awal pada **SIGOS Vendor Heavy Desktop**.  
Konfigurasi ini mendefinisikan node lokasi (*Palembang*), operator (*XL/Excelcom*), serta nomor uji yang akan digunakan.  
Hal ini memastikan KPI nantinya bisa diukur sesuai target lingkup pengujian.  

![Setup Lingkup Pengujian](./images/isat_pale.png)  


- **Desain Skenario:**
  1. Dial kode akses (contoh: `*363#` untuk Telkomsel).  
  2. Navigasi menu otomatis (misal pilih `1 → 2 → 3`).  
  3. Ekstraksi teks dari layar USSD (paket, kuota, harga).  

- **Teknis:**
  - Skrip dibuat via *scripting studio* atau Python.  
  - Parsing hasil USSD → format JSON.  
  - Contoh hasil parsing:
    ```json
    {
      "paket": "Freedom Harian",
      "kuota": "1GB",
      "harga": "Rp23rb"
    }
    ```

---

## ⚙️ Fase III – Eksekusi Otomatis & Pemantauan Real-Time
**Fokus:** Jalankan crawling di semua kota secara simultan.  

- **Eksekusi Paralel:** Probe di setiap kota menjalankan skenario pada jam terjadwal (contoh: setiap hari pukul 03.00 WIB).  
- **Pengumpulan Data Terpusat:** Semua hasil ekstraksi dikirim ke pusat (SITE DB).  
- **Monitoring:**
  - Dashboard real-time (Grafana/Power BI).  
  - Alert otomatis jika probe gagal navigasi atau parsing.  

---

## 📈 Fase IV – Analitik Tingkat Lanjut & Optimalisasi Berkelanjutan
**Fokus:** Mengubah data harga menjadi insight.  

- **Analisis Harga Regional:**
  - Bandingkan harga paket antar kota.  
  - Identifikasi variasi tarif (contoh: Paket A Rp50.000 di Jakarta, Rp60.000 di Bandung).  

- **Integritas Data:**
  - Validasi parsing 100% (tidak ada teks terpotong karena batas 182 karakter).  

- **Insight Bisnis:**
  - Laporan tren harga & anomali tarif.  
  - Rekomendasi optimasi channel USSD.  

---

## ✅ Hasil & Dampak
- Sistem crawling otomatis menghasilkan **database harga paket real-time** multi-kota.  
- Latensi rata-rata tercatat **< 4 detik** per layer, sesuai KPI.  
- Data harga digunakan untuk **analisis kompetitor** dan **penyesuaian strategi produk**.  

---

## 💡 Peran Saya
- Mendesain metodologi crawling multi-geografis.  
- Membuat skenario navigasi USSD & parsing hasil menu.  
- Membangun pipeline eksekusi otomatis & integrasi data ke dashboard.  
- Menyusun laporan analisis variasi tarif untuk stakeholder.  
