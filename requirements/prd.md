# DRAF PRD — Smart Inventory & Stock Demand Forecasting System

## 1. Ringkasan Eksekutif

**Smart Inventory & Stock Demand Forecasting System** adalah website pengelolaan persediaan yang ditujukan untuk membantu **Admin Gudang** mencatat dan memantau barang masuk, barang keluar, serta peminjaman dan pengembalian barang secara lebih terstruktur.

Produk ini dikembangkan untuk mengatasi pencatatan manual berbasis kertas di **PT Jambi Agung Lestari**, yang menyebabkan proses pencarian data dan pembuatan laporan lambat, risiko kehilangan dokumen, serta ketidaksesuaian antara stok tercatat dan stok fisik.

Selain digitalisasi pencatatan, produk memiliki dua fitur AI utama:

* **★ AI Stock Demand Forecasting & Auto-Reorder Point** — memprediksi barang yang berpotensi habis berdasarkan riwayat pengeluaran/peminjaman dan memberikan peringatan.
* **★ OCR & Intelligent Document Parsing** — membantu membaca nota, tanda terima, atau bukti peminjaman sehingga data dapat dimasukkan tanpa seluruhnya diketik manual.

Karena prototype hanya dikembangkan selama **3–4 bulan dengan sumber daya data AI terbatas**, fokus produk adalah membangun **MVP yang mampu membuktikan pengurangan pekerjaan manual dan membantu pengambilan keputusan stok**, bukan sistem AI berskala produksi penuh.

---

# 2. Problem Statement & Bukti

## Problem Statement

PT Jambi Agung Lestari menghadapi kendala dalam pengelolaan stok gudang karena pencatatan masih dilakukan menggunakan kertas. Kondisi tersebut menyebabkan pemeliharaan data dan pembuatan laporan membutuhkan waktu lama, data sulit ditelusuri, dokumen berisiko rusak atau hilang, serta terdapat ketidaksesuaian antara stok yang tercatat dan stok fisik.

Selain itu, proses peminjaman dan pengembalian barang belum memiliki pencatatan status yang jelas sehingga menyulitkan pemantauan barang yang sedang dipinjam.

### Fakta Riset

| No. | Fakta                                                                                                                       |
| --- | --------------------------------------------------------------------------------------------------------------------------- |
| 1   | Pencatatan stok masih dilakukan secara manual menggunakan kertas.                                                           |
| 2   | Pembuatan laporan membutuhkan waktu lama karena harus memeriksa berkas satu per satu.                                       |
| 3   | Berkas fisik rentan rusak, hilang, basah, atau terselip.                                                                    |
| 4   | Sering terjadi ketidaksesuaian antara stok tercatat dan stok fisik.                                                         |
| 5   | Operasional mencakup penerimaan barang dari kurir, pengeluaran barang untuk karyawan, serta peminjaman/pengembalian barang. |

### Asumsi

| ID          | Asumsi                                                                                                                                |
| ----------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| [ASUMSI-01] | Admin Gudang menjadi pengguna utama sistem dan bertanggung jawab terhadap validasi transaksi stok.                                    |
| [ASUMSI-02] | Tersedia riwayat pengeluaran/peminjaman yang cukup untuk prototype forecasting, meskipun jumlah dan kualitas datanya belum diketahui. |
| [ASUMSI-03] | Dokumen nota/tanda terima memiliki informasi yang cukup terbaca untuk diproses oleh OCR.                                              |
| [ASUMSI-04] | Manajer/Pimpinan membutuhkan informasi stok dan peringatan barang yang berpotensi habis untuk membantu pengambilan keputusan.         |
| [ASUMSI-05] | Prototype tidak ditujukan untuk menggantikan seluruh proses operasional gudang secara otomatis.                                       |

---

# 3. Target User & Stakeholder

| Peran                         | Kebutuhan                                                                                              | Tingkat Pengaruh/Kepentingan |
| ----------------------------- | ------------------------------------------------------------------------------------------------------ | ---------------------------- |
| **Admin Gudang**              | Mencatat barang masuk/keluar, peminjaman, pengembalian, mencari data, dan membuat laporan dengan cepat | **Tinggi / Tinggi**          |
| **Karyawan**                  | Mengajukan/melakukan peminjaman dan mengetahui status barang yang dipinjam                             | **Sedang / Tinggi**          |
| **Manajer Gudang / Pimpinan** | Memantau kondisi stok, laporan, dan mendapatkan peringatan barang yang berpotensi habis                | **Tinggi / Tinggi**          |
| **Kurir**                     | Menyerahkan barang dan tanda terima sebagai bukti barang masuk                                         | **Sedang / Sedang**          |

### Prioritas pengguna

**Primary user:** Admin Gudang
**Secondary user:** Karyawan
**Decision maker:** Manajer Gudang / Pimpinan
**External operational stakeholder:** Kurir

---

# 4. Value Proposition

## A. Pain yang Dikurangi

1. Mengurangi pencatatan stok menggunakan kertas.
2. Mengurangi waktu pencarian data transaksi.
3. Mengurangi pekerjaan manual ketika membuat laporan.
4. Mengurangi risiko dokumen rusak atau hilang.
5. Membantu mengurangi ketidaksesuaian antara stok tercatat dan kondisi fisik.
6. Mengurangi ketidakjelasan status barang yang sedang dipinjam.
7. Mengurangi pekerjaan mengetik ulang informasi dari dokumen.

## B. Gain yang Diciptakan

1. **Data stok lebih mudah ditelusuri** melalui pencatatan digital.
2. **Laporan lebih cepat dibuat** berdasarkan data transaksi yang telah tersimpan.
3. **Status peminjaman lebih jelas**, termasuk barang yang masih dipinjam atau telah dikembalikan.
4. **Peringatan dini stok** membantu Admin Gudang mengetahui barang yang berpotensi habis.
5. **Input dokumen lebih cepat** dengan bantuan OCR.
6. **Pengambilan keputusan lebih proaktif** karena sistem tidak hanya menunjukkan stok saat ini tetapi juga memberikan indikasi kebutuhan stok berikutnya.

## C. Mengapa AI Bukan Gimmick?

AI digunakan untuk mengatasi **dua bottleneck nyata** dalam proses gudang:

### ★ Demand Forecasting

Masalah utama bukan hanya mengetahui **berapa stok saat ini**, tetapi mengetahui **barang mana yang kemungkinan akan habis**.

AI memanfaatkan riwayat pengeluaran/peminjaman untuk menghasilkan prediksi dan peringatan. Dengan demikian, Admin Gudang dapat melakukan tindakan sebelum stok benar-benar habis.

**Bottleneck yang diselesaikan:** keterlambatan mengetahui kebutuhan stok.

### ★ OCR & Intelligent Document Parsing

Pencatatan manual menyebabkan Admin harus memasukkan data dari dokumen secara berulang.

OCR digunakan untuk membantu membaca informasi dari nota, tanda terima, atau bukti peminjaman sehingga Admin tidak perlu mengetik seluruh informasi dari awal.

**Bottleneck yang diselesaikan:** input data manual dari dokumen.

> Dengan demikian, AI ditempatkan pada aktivitas yang memang membutuhkan **prediksi** dan **ekstraksi informasi**, bukan sekadar ditambahkan sebagai fitur tambahan.

---

# 5. Tujuan Produk & KPI Terukur

## Tujuan Produk

1. Mendigitalisasi proses pencatatan stok dan transaksi gudang.
2. Mempercepat pencarian data dan pembuatan laporan.
3. Meningkatkan keterlacakan peminjaman dan pengembalian barang.
4. Membantu Admin mendeteksi potensi kekurangan stok lebih awal.
5. Mengurangi pekerjaan input data dokumen secara manual.
6. Membuktikan kelayakan penggunaan AI pada proses operasional gudang.

## KPI

| Metric Utama                                   |               Target Prototype | Cara Mengukur                                                              |
| ---------------------------------------------- | -----------------------------: | -------------------------------------------------------------------------- |
| **Waktu pencatatan transaksi**                 |                     Turun ≥30% | Bandingkan waktu pencatatan manual dengan pencatatan melalui prototype     |
| **Waktu pencarian data**                       |                     Turun ≥50% | Ukur waktu menemukan transaksi/barang tertentu sebelum dan sesudah sistem  |
| **Waktu pembuatan laporan**                    |                     Turun ≥50% | Bandingkan waktu pembuatan laporan manual dengan laporan dari sistem       |
| **Akurasi pencatatan stok**                    |  ≥90% pada pengujian prototype | Bandingkan stok sistem dengan hasil pengecekan stok fisik                  |
| **Akurasi OCR**                                |     ≥80% pada field yang diuji | Bandingkan hasil OCR dengan data dokumen yang benar                        |
| **Keberhasilan deteksi stok berpotensi habis** |             ≥80% pada data uji | Bandingkan peringatan sistem dengan kondisi yang muncul pada data historis |
| **Kelengkapan status peminjaman**              | ≥95% transaksi memiliki status | Periksa transaksi peminjaman yang memiliki status jelas                    |

**Catatan:** Target KPI di atas merupakan **[ASUMSI-06]** karena data baseline aktual dari PT Jambi Agung Lestari belum tersedia dalam konteks.

---

# 6. Scope Fitur 3 Bulan — MoSCoW

| Prioritas       | Fitur                                  | Deskripsi                                                              | Status                  |
| --------------- | -------------------------------------- | ---------------------------------------------------------------------- | ----------------------- |
| **Must Have**   | Login & hak akses pengguna             | Akses berdasarkan peran Admin, Karyawan, dan pihak terkait             | Wajib                   |
| **Must Have**   | Master data barang                     | Pengelolaan data barang dan informasi stok                             | Wajib                   |
| **Must Have**   | Barang masuk                           | Pencatatan penerimaan barang dari kurir berdasarkan tanda terima       | Wajib                   |
| **Must Have**   | Barang keluar                          | Pencatatan barang yang diberikan kepada karyawan                       | Wajib                   |
| **Must Have**   | Peminjaman barang                      | Pencatatan transaksi peminjaman                                        | Wajib                   |
| **Must Have**   | Pengembalian barang                    | Pencatatan barang yang telah dikembalikan                              | Wajib                   |
| **Must Have**   | Status peminjaman                      | Menampilkan status barang: dipinjam/dikembalikan                       | Wajib                   |
| **Must Have**   | Riwayat transaksi                      | Melihat histori barang masuk, keluar, dan peminjaman                   | Wajib                   |
| **Must Have**   | Laporan stok                           | Menampilkan informasi stok dan transaksi                               | Wajib                   |
| **Must Have**   | ★ Demand Forecasting                   | Memprediksi barang yang berpotensi habis berdasarkan riwayat transaksi | **AI Wajib**            |
| **Must Have**   | ★ Auto-Reorder Point / peringatan stok | Memberikan peringatan ketika stok diprediksi mendekati kondisi kritis  | **AI Wajib**            |
| **Must Have**   | ★ OCR dokumen                          | Membaca informasi dari nota/tanda terima/bukti peminjaman              | **AI Wajib**            |
| **Should Have** | Dashboard ringkasan                    | Menampilkan ringkasan stok, transaksi, dan peringatan                  | Prioritas kedua         |
| **Should Have** | Notifikasi stok                        | Memberikan informasi ketika terdapat barang yang perlu diperhatikan    | Prioritas kedua         |
| **Should Have** | Filter laporan                         | Memudahkan pencarian berdasarkan periode/barang/transaksi              | Prioritas kedua         |
| **Could Have**  | Grafik tren stok                       | Visualisasi perkembangan penggunaan barang                             | Jika waktu memungkinkan |
| **Could Have**  | Riwayat prediksi                       | Menampilkan hasil prediksi sebelumnya                                  | Jika waktu memungkinkan |
| **Could Have**  | Ekspor laporan                         | Ekspor laporan ke format tertentu                                      | Jika waktu memungkinkan |
| **Won't Have**  | Otomatisasi pembelian barang           | Sistem tidak melakukan pemesanan barang secara otomatis                | Di luar scope           |
| **Won't Have**  | Integrasi supplier                     | Tidak membangun integrasi langsung dengan pemasok                      | Di luar scope           |
| **Won't Have**  | Aplikasi mobile native                 | Prototype hanya berfokus pada website                                  | Di luar scope           |
| **Won't Have**  | AI generatif/chatbot kompleks          | Tidak membangun chatbot umum karena bukan bottleneck utama             | Di luar scope           |

### Prioritas 3 Bulan

**Bulan 1 — Fondasi**

* Master data barang
* Pengguna dan hak akses
* Barang masuk/keluar
* Peminjaman/pengembalian
* Riwayat transaksi

**Bulan 2 — Digitalisasi & AI**

* Laporan stok
* ★ OCR & Intelligent Document Parsing
* ★ Pengembangan awal demand forecasting
* Data historis untuk pengujian prediksi

**Bulan 3 — Integrasi & Validasi**

* ★ Auto-Reorder Point/peringatan
* Dashboard
* Pengujian akurasi AI
* Pengujian KPI
* Perbaikan berdasarkan hasil pengujian

---

# 7. Non-Goals Eksplisit

Hal-hal berikut **tidak menjadi tujuan produk dalam prototype 3 bulan**:

1. Sistem tidak melakukan **pemesanan barang secara otomatis** kepada supplier.
2. Sistem tidak mengelola proses pembelian dan pembayaran.
3. Sistem tidak menggantikan keputusan Manajer/Pimpinan dalam menentukan pembelian barang.
4. Sistem tidak membangun aplikasi mobile native.
5. Sistem tidak ditujukan untuk menjadi ERP perusahaan secara keseluruhan.
6. Sistem tidak membuat chatbot AI umum.
7. Sistem tidak menjamin prediksi stok selalu benar 100%.
8. Sistem tidak melakukan pengelolaan logistik kurir secara menyeluruh.
9. Sistem tidak membangun arsitektur AI berskala besar karena keterbatasan waktu, data, dan resource.
10. Sistem tidak menghilangkan kebutuhan **verifikasi Admin terhadap hasil OCR maupun prediksi AI**.

---

# 8. Asumsi, Risiko Utama & Strategi Mitigasi

| Asumsi/Risiko                                | Dampak                                                     | Strategi Mitigasi                                                                         |
| -------------------------------------------- | ---------------------------------------------------------- | ----------------------------------------------------------------------------------------- |
| **[ASUMSI-01]** Admin menjadi pengguna utama | Fitur dapat tidak sesuai kebutuhan jika alur kerja berbeda | Validasi alur dengan skenario operasional yang tersedia                                   |
| **[ASUMSI-02]** Data historis tersedia       | Forecasting sulit bekerja jika data terlalu sedikit        | Gunakan forecasting sebagai prototype dan tampilkan keterbatasan hasil prediksi           |
| Data transaksi historis terbatas             | Akurasi prediksi rendah                                    | Fokus pada indikator/peringatan sederhana dan evaluasi menggunakan data uji yang tersedia |
| Kualitas dokumen berbeda-beda                | OCR dapat salah membaca data                               | Hasil OCR wajib dapat diperiksa dan dikoreksi Admin                                       |
| **[ASUMSI-03]** Dokumen dapat dibaca OCR     | Data tidak dapat diekstraksi jika dokumen terlalu buruk    | Batasi prototype pada jenis dokumen yang memenuhi kualitas minimum                        |
| Ketidaksesuaian stok fisik                   | Forecasting menggunakan data yang tidak akurat             | Sediakan pencatatan/verifikasi stok fisik secara berkala                                  |
| Waktu pengembangan hanya 3–4 bulan           | Fitur terlalu banyak dapat mengganggu fitur inti           | Terapkan prioritas MoSCoW dan fokus pada MVP                                              |
| Resource AI terbatas                         | Tidak memungkinkan model AI kompleks                       | Gunakan pendekatan AI yang sederhana dan sesuai dengan jumlah data                        |
| Pengguna terlalu bergantung pada AI          | Kesalahan prediksi dapat menyebabkan keputusan stok keliru | AI bersifat **decision support**, bukan pengambil keputusan otomatis                      |
| Perubahan kebutuhan stakeholder              | Scope dapat melebar                                        | Tetapkan Must Have sebagai baseline dan dokumentasikan perubahan kebutuhan                |

---

## Kesimpulan PRD

**Smart Inventory & Stock Demand Forecasting System** berfokus pada satu tujuan utama: **mengubah pengelolaan stok yang sebelumnya manual menjadi proses digital yang lebih cepat, terukur, dan proaktif.**

Nilai utama produk bukan sekadar digitalisasi pencatatan, tetapi mengatasi dua bottleneck yang paling relevan:

> **Digitalisasi + AI OCR → mengurangi pekerjaan input manual.**
> **AI Forecasting → membantu mengetahui potensi kekurangan stok sebelum terjadi.**

Dengan keterbatasan waktu **3–4 bulan**, MVP sebaiknya memprioritaskan **pencatatan stok, peminjaman/pengembalian, laporan, ★ OCR, dan ★ demand forecasting/peringatan stok**, sementara fitur di luar kebutuhan inti ditunda.
