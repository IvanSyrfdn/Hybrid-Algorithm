# Hybrid Algorithm


# ☁️ Optimasi Penjadwalan Tugas Cloud: Analisis Komparatif PEFT-PSO vs. MA-NSGA-II pada CloudSim

![CloudSim](https://img.shields.io/badge/Simulator-CloudSim%203.0.3%2B-0ea5e9?style=for-the-badge&logo=java&logoColor=white)
![Frontend](https://img.shields.io/badge/Presentation-HTML5%20%7C%20CSS3%20%7C%20Vanilla%20JS-10b981?style=for-the-badge&logo=html5&logoColor=white)
![GitHub Pages](https://img.shields.io/badge/Hosted%20on-GitHub%20Pages-6366f1?style=for-the-badge&logo=github&logoColor=white)

Repositori ini berisi implementasi simulasi **CloudSim** dan **Presentasi Web Interaktif (*Cyber-Cloud Mission Control*)** untuk tugas mata kuliah **Strategi Komputasi Awan**. Proyek ini mengevaluasi performa dua algoritma penjadwalan *hybrid* berbasis jurnal ilmiah (**PEFT-PSO** dan **MA-NSGA-II**) menggunakan *workload* **Dataset Minggu 3**, serta membandingkannya terhadap tiga metode *baseline* tunggal yang telah diuji sebelumnya (**LJFP**, **DSOS**, dan **SMO**).

🔗 **Live Presentasi (GitHub Pages):** `https://<username-github-anda>.github.io/<nama-repositori>/`

---

## 📋 Daftar Isi
- [Latar Belakang & Kepatuhan Ketentuan](#-latar-belakang--kepatuhan-ketentuan)
- [Arsitektur & Algoritma yang Diuji](#-arsitektur--algoritma-yang-diuji)
- [Struktur Repositori](#-struktur-repositori)
- [Fitur Presentasi Web Interaktif](#-fitur-presentasi-web-interaktif)
- [Cara Menjalankan Simulasi CloudSim](#-cara-menjalankan-simulasi-cloudsim)
- [Panduan Deploy ke GitHub Pages](#-panduan-deploy-ke-github-pages)
- [Referensi Jurnal Ilmiah](#-referensi-jurnal-ilmiah)
- [Identitas Kelompok](#-identitas-kelompok)

---

## 🎯 Latar Belakang & Kepatuhan Ketentuan

1. **Pemilihan 2 Algoritma Hybrid (Pola B–E):**
   - **PEFT-PSO *(Pola B: Heuristik + Metaheuristik)*** — Memadukan prediksi *Optimistic Cost Table* (OCT) dari *Predict Earliest Finish Time* (PEFT) sebagai *seeding* deterministik bagi *Particle Swarm Optimization* (PSO).
   - **MA-NSGA-II *(Pola D: Memetic Algorithm)*** — Menggabungkan pencarian multi-objektif *Pareto* NSGA-II dengan *Critical-VM Local Search*.
2. **Keunggulan PEFT-PSO sebagai Hybrid Utama:**
   - Memangkas *makespan* secara signifikan sejak iterasi ke-0 melalui matriks *look-ahead* OCT tanpa penalti komputasi *non-dominated sorting* yang berat.
3. **Evaluasi Komparatif pada CloudSim:**
   - Diuji menggunakan skenario *Cloudlet* dan VM heterogen yang identik dengan **Dataset Minggu 3** melawan **LJFP**, **DSOS**, dan **SMO**.

---

## ⚙️ Arsitektur & Algoritma yang Diuji

| Algoritma | Kategori / Pola | Mekanisme Utama | Fokus Optimasi |
| :--- | :--- | :--- | :--- |
| **LJFP** *(Baseline 1)* | Heuristik Tunggal (Minggu 3) | Mengurutkan *task* berdasarkan ukuran MI terbesar (*Longest Job First*) dan memetakannya ke VM dengan *Earliest Finish Time* (EFT). | Waktu eksekusi awal (*greedy*) |
| **DSOS** *(Baseline 2)* | Metaheuristik (Minggu 3) | *Discrete Symbiotic Organisms Search* dengan fase *Mutualism*, *Commensalism*, dan *Parasitism* pada ruang diskrit. | Eksplorasi populasi global |
| **SMO** *(Baseline 3)* | Metaheuristik (Minggu 3) | *Spider Monkey Optimization* berbasis struktur sosial *fission-fusion* (*Local Leader* & *Global Leader*). | Keseimbangan eksplorasi-eksploitasi |
| **MA-NSGA-II** *(Hybrid 2)* | **Pola D** — Memetic Algorithm | Evolusi multi-objektif *Pareto Front* (NSGA-II) yang diperkuat *task-swapping local search* pada VM dengan beban kritis. | Kompromi *Makespan* vs. *Cost* |
| **PEFT-PSO** *(Hybrid Unggulan)* | **Pola B** — Heuristik + Metaheuristik | Menghitung *Optimistic Cost Table* (OCT) dari bawah ke atas, menyuntikkan jadwal `O_EFT` ke partikel-0 PSO, lalu mengoptimalkan pemetaan VM. | **Minimum Makespan Absolut** |

---

## 📂 Struktur Repositori

```text
├── index.html                        # Presentasi web interaktif 9 slide (self-contained, tanpa CDN eksternal)
└── README.md                         # Dokumentasi proyek

## Kelompok

| No. | Nama Mahasiswa | NRP |
| :---: | :--- | :---: |
| 1 | Ivan Syarifuddin | 5027241045 | 
| 2 | Reza Aziz Simatupang | 5027241051 | 
| 3 | Nisrina Bilqis | 5027241054 | 
| 4 | Ananda Widi Alrafi | 5027241067 | 
| 5 | Muhammad Khosyi Syehab | 5027241089 |