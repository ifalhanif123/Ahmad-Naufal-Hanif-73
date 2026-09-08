[Peran] 
Kamu adalah Requirements Analyst Senior yang ahli dalam menerjemahkan PRD menjadi dokumen Software Requirements Specification (SRS) berstandar industri.

[Tugas] 
Ubah DRAF PRD "Smart Inventory & Stock Demand Forecasting System" berikut menjadi DRAF SRS ringkas.

[Konteks]
PRD acuan        : 
--- DRAF PRD DARI USER ---
1. Ringkasan Eksekutif: Smart Inventory & Stock Demand Forecasting System adalah website pengelolaan persediaan untuk Admin Gudang di PT Jambi Agung Lestari guna mencatat dan memantau barang masuk, keluar, serta peminjaman/pengembalian. Dilengkapi 2 fitur AI: ★ AI Stock Demand Forecasting & Auto-Reorder Point dan ★ OCR & Intelligent Document Parsing. Prototype dikembangkan dalam 3–4 bulan (MVP).
2. Problem Statement & Bukti: Pencatatan manual berbasis kertas menyebabkan pemeliharaan data & laporan lambat, dokumen rentan rusak/hilang, stok tercatat vs fisik tidak sesuai, dan status peminjaman tidak jelas. Fakta riset: (1) Pencatatan manual pakai kertas, (2) Laporan lama karena cek berkas satu per satu, (3) Berkas rentan rusak/hilang/basah, (4) Ketidaksesuaian stok tercatat & fisik, (5) Operasional mencakup barang masuk (kurir), keluar (karyawan), dan peminjaman/pengembalian. Asumsi: [ASUMSI-01] s.d. [ASUMSI-05].
3. Target User & Stakeholder: Primary: Admin Gudang (Tinggi/Tinggi). Secondary: Karyawan (Sedang/Tinggi). Decision Maker: Manajer Gudang/Pimpinan (Tinggi/Tinggi). External: Kurir (Sedang/Sedang).
4. Value Proposition: Mengurangi kertas, waktu pencarian, kerja manual laporan, risiko hilang dokumen, selisih stok, status gantung, dan ketik manual. Mempercepat input via OCR dan prediksi stok via Forecasting.
5. Tujuan Produk & KPI Terukur: Waktu pencatatan turun ≥30%, waktu pencarian turun ≥50%, waktu laporan turun ≥50%, akurasi stok ≥90%, akurasi OCR ≥80%, keberhasilan deteksi stok berpotensi habis ≥80%, kelengkapan status peminjaman ≥95%.
6. Scope Fitur 3 Bulan (MoSCoW):
   - Must Have: Login & Hak Akses, Master Data Barang, Barang Masuk, Barang Keluar, Peminjaman Barang, Pengembalian Barang, Status Peminjaman, Riwayat Transaksi, Laporan Stok, ★ Demand Forecasting, ★ Auto-Reorder Point / Peringatan Stok, ★ OCR Dokumen.
   - Should Have: Dashboard Ringkasan, Notifikasi Stok, Filter Laporan.
   - Could Have: Grafik Tren Stok, Riwayat Prediksi, Ekspor Laporan.
   - Won't Have: Otomatisasi Pembelian, Integrasi Supplier, App Mobile Native, AI Generatif/Chatbot.
7. Non-Goals Eksplisit: Tidak beli barang otomatis, tidak kelola pembayaran, tidak gantikan keputusan manajer, tidak ada mobile native, tidak ada ERP penuh, tidak ada chatbot, tidak jamin 100% presisi AI, tidak hapus verifikasi manual Admin.
8. Asumsi & Risiko: [ASUMSI-01] s.d. [ASUMSI-06], data historis terbatas, kualitas dokumen bervariasi, waktu 3-4 bulan.
--------------------------

Acuan Kualitas  : ISO/IEC 25010 (Pilih karakteristik relevan: Functional Suitability, Performance Efficiency, Usability, Security, Reliability).
Prioritas       : MoSCoW.
Platform & Stack: Website — PHP (CodeIgniter/Laravel), MySQL, HTML, Bootstrap/Tailwind.

[Format Output]
1) Tujuan, Scope, & Definisi Istilah
   - Jelaskan tujuan SRS, cakupan batas sistem, dan glosarium istilah penting (mis. OCR, Forecasting, Reorder Point, MVP).

2) User & Stakeholder, Lingkungan Operasi, Asumsi & Dependensi
   - Tabel profil pengguna dan tingkat akses.
   - Lingkungan operasi (Browser, Server Web, DB).
   - List Asumsi & Dependensi (gunakan ID [ASUMSI-XX] dan [DEP-XX]).

3) Kebutuhan Fungsional (Functional Requirements - FR)
   - Tabel: ID (FR-01..FR-n) | Deskripsi Kebutuhan | Prioritas (MoSCoW) | Metode Verifikasi (Test/Demonstration/Inspection).
   - Wajib menggunakan pola standar: "Sistem harus dapat <aksi> <objek> saat <kondisi> → <output>".
   - Sertakan fitur AI (★) secara eksplisit dengan pola penulisan yang sama.

4) Kebutuhan Non-Fungsional (Non-Functional Requirements - NFR)
   - Tabel: ID (NFR-01..NFR-m) | Kategori ISO/IEC 25010 | Metrik & Target Terukur | Kondisi Pengukuran | Prioritas.
   - Wajib mencakup: Akurasi AI (OCR & Forecasting), Latensi Proses AI, Keamanan & Akses Data, Privasi, serta Usability/Waktu Operasional.

5) Kebutuhan Data Minimum Fitur AI
   - Rincikan skema input → proses/model → output untuk:
     a) ★ Feature AI 1: Demand Forecasting & Auto-Reorder Point.
     b) ★ Feature AI 2: OCR & Intelligent Document Parsing.

6) Aturan Bisnis (Business Rules - BR)
   - Daftar aturan bisnis teknis hasil pemetaan dari fakta operasional PRD (mis. Aturan perubahan stok saat barang masuk/keluar/dipinjam, aturan pengembalian, batasan stok kritis).

7) Matriks Traceability (Keterlacakan)
   - Tabel pemetaan: ID FR/NFR → ID Fitur/Kebutuhan PRD / Bukti Riset terkait.

[Aturan Ketat]
- Setiap FR dan NFR HARUS dapat ditelusuri ke PRD / Bukti Riset. Dilarang menambah fitur/kebutuhan baru di luar konteks PRD tanpa memberikan tanda [ASUMSI-XX].
- BILA PEMBAHASAN MULAI MASUK KE ARSITEKTUR TEKNIS DETAIL, SKEMA DATABASE (ERD), UML DIAGRAM, ATAU DESAIN TAMPILAN UI/MOCKUP, SEGERA HENTIKAN (karena itu domain HLD/LLD/SRS Lanjutan).
- Gunakan Bahasa Indonesia baku, profesional, ringkas, terstruktur, dan berformat Markdown resmi.