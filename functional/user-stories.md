Berikut **DRAF User Stories / Agile Product Backlog** yang diturunkan langsung dari SRS yang kamu berikan. Saya hanya memasukkan fitur **Must Have** dan **Should Have**, serta memastikan setiap story memiliki keterlacakan ke FR dan, bila relevan, NFR/BR.

# DRAF USER STORIES

## Smart Inventory & Stock Demand Forecasting System

---

# Epik 1 — Manajemen Otentikasi & Hak Akses

### US-01 — Login Pengguna

* **ID Story:** US-01
* **User Story:** Sebagai **pengguna**, saya ingin melakukan login ke sistem, sehingga saya dapat mengakses fitur sesuai akun saya.
* **Prioritas:** Must Have
* **Keterlacakan:**

  * Diturunkan dari: **FR-01**
  * Didukung oleh: **NFR-08, NFR-10**
* **Kriteria Penerimaan:**

  * **Given** pengguna memiliki akun yang valid, **When** pengguna memasukkan kredensial yang benar, **Then** sistem memberikan akses ke sistem.
  * **Given** kredensial tidak valid, **When** pengguna mencoba login, **Then** sistem menolak akses.
  * **Given** pengguna berhasil login, **When** sistem memberikan akses, **Then** akses disesuaikan dengan peran pengguna.

### US-02 — Hak Akses Berdasarkan Peran

* **ID Story:** US-02
* **User Story:** Sebagai **pengguna**, saya ingin sistem membatasi akses berdasarkan peran, sehingga saya hanya dapat menggunakan fungsi yang sesuai dengan kewenangan saya.
* **Prioritas:** Must Have
* **Keterlacakan:**

  * Diturunkan dari: **FR-02**
  * Didukung oleh: **NFR-08, NFR-09**
* **Kriteria Penerimaan:**

  * **Given** pengguna telah login, **When** pengguna mengakses sistem, **Then** sistem menerapkan hak akses sesuai perannya.
  * Pengguna tidak dapat mengakses fungsi yang berada di luar kewenangannya.
  * Data transaksi tidak dapat diakses oleh pengguna tanpa hak akses.

---

# Epik 2 — Pengelolaan Master Data Barang & Inventori

### US-03 — Mengelola Data Barang

* **ID Story:** US-03
* **User Story:** Sebagai **Admin Gudang**, saya ingin mengelola data barang, sehingga data inventori dapat digunakan dalam transaksi gudang.
* **Prioritas:** Must Have
* **Keterlacakan:**

  * Diturunkan dari: **FR-03**
  * Didukung oleh: **NFR-03**
* **Kriteria Penerimaan:**

  * **Given** Admin memiliki hak akses, **When** Admin menambahkan data barang, **Then** data barang tersimpan dalam sistem.
  * Admin dapat memperbarui data barang yang tersedia.
  * Data barang yang tersimpan dapat digunakan pada transaksi inventori.

### US-04 — Menjaga Ketepatan Data Stok

* **ID Story:** US-04
* **User Story:** Sebagai **Admin Gudang**, saya ingin data stok diperbarui berdasarkan transaksi, sehingga jumlah stok dalam sistem dapat sesuai dengan kondisi operasional.
* **Prioritas:** Must Have
* **Keterlacakan:**

  * Diturunkan dari: **FR-03, FR-09**
  * Didukung oleh: **NFR-03, NFR-15, BR-08**
* **Kriteria Penerimaan:**

  * Setiap perubahan stok berasal dari transaksi yang tercatat.
  * Sistem mempertahankan data transaksi setelah berhasil disimpan.
  * Data stok dapat ditelusuri melalui riwayat transaksi.

---

# Epik 3 — Transaksi Operasional Barang

### US-05 — Mencatat Barang Masuk

* **ID Story:** US-05
* **User Story:** Sebagai **Admin Gudang**, saya ingin mencatat barang yang diterima dari kurir, sehingga stok barang masuk tercatat dalam sistem.
* **Prioritas:** Must Have
* **Keterlacakan:**

  * Diturunkan dari: **FR-04**
  * Didukung oleh: **BR-01, BR-02**
* **Kriteria Penerimaan:**

  * **Given** barang diterima dari kurir, **When** Admin mencatat transaksi barang masuk, **Then** transaksi tersimpan.
  * Stok bertambah sesuai jumlah barang yang diterima.
  * Transaksi barang masuk tercatat dalam riwayat.

### US-06 — Mencatat Barang Keluar

* **ID Story:** US-06
* **User Story:** Sebagai **Admin Gudang**, saya ingin mencatat barang yang diberikan kepada karyawan, sehingga pengurangan stok dapat tercatat dengan benar.
* **Prioritas:** Must Have
* **Keterlacakan:**

  * Diturunkan dari: **FR-05**
  * Didukung oleh: **BR-03, BR-14**
* **Kriteria Penerimaan:**

  * **Given** barang akan diberikan kepada karyawan, **When** Admin mencatat barang keluar, **Then** transaksi tersimpan.
  * Stok berkurang sesuai jumlah barang yang dikeluarkan.
  * Jika jumlah pengeluaran melebihi stok tersedia, transaksi ditolak atau Admin diminta melakukan koreksi.

### US-07 — Riwayat Transaksi Barang

* **ID Story:** US-07
* **User Story:** Sebagai **Admin Gudang**, saya ingin melihat riwayat transaksi barang, sehingga aktivitas stok dapat ditelusuri kembali.
* **Prioritas:** Must Have
* **Keterlacakan:**

  * Diturunkan dari: **FR-09**
  * Didukung oleh: **NFR-05, BR-08**
* **Kriteria Penerimaan:**

  * Setiap transaksi yang berhasil dicatat muncul dalam riwayat.
  * Riwayat dapat digunakan untuk menelusuri transaksi barang.
  * Data transaksi yang tersimpan dapat ditampilkan kembali.

---

# Epik 4 — Pemantauan Peminjaman & Pengembalian Barang

### US-08 — Mencatat Peminjaman

* **ID Story:** US-08
* **User Story:** Sebagai **Karyawan**, saya ingin melakukan peminjaman barang, sehingga penggunaan barang operasional dapat tercatat dan ditelusuri.
* **Prioritas:** Must Have
* **Keterlacakan:**

  * Diturunkan dari: **FR-06**
  * Didukung oleh: **BR-04**
* **Kriteria Penerimaan:**

  * **Given** barang tersedia untuk dipinjam, **When** peminjaman dilakukan, **Then** transaksi peminjaman tersimpan.
  * Transaksi memiliki status peminjaman.
  * Peminjaman masuk ke dalam riwayat transaksi.

### US-09 — Mencatat Pengembalian

* **ID Story:** US-09
* **User Story:** Sebagai **Admin Gudang**, saya ingin mencatat pengembalian barang, sehingga status barang yang dipinjam dapat diperbarui.
* **Prioritas:** Must Have
* **Keterlacakan:**

  * Diturunkan dari: **FR-07**
  * Didukung oleh: **BR-06, BR-07**
* **Kriteria Penerimaan:**

  * **Given** terdapat barang yang sedang dipinjam, **When** barang dikembalikan, **Then** transaksi pengembalian tersimpan.
  * Status peminjaman berubah menjadi telah dikembalikan.
  * Pengembalian dapat ditelusuri melalui riwayat transaksi.

### US-10 — Memantau Status Peminjaman

* **ID Story:** US-10
* **User Story:** Sebagai **Admin Gudang**, saya ingin melihat status peminjaman barang, sehingga saya dapat mengetahui barang yang masih dipinjam dan yang telah dikembalikan.
* **Prioritas:** Must Have
* **Keterlacakan:**

  * Diturunkan dari: **FR-08**
  * Didukung oleh: **NFR-14, BR-05, BR-07**
* **Kriteria Penerimaan:**

  * Sistem menampilkan status barang yang masih dipinjam.
  * Sistem menampilkan status barang yang telah dikembalikan.
  * Minimal **95% transaksi peminjaman** memiliki status yang jelas.

---

# Epik 5 — Pelaporan & Informasi Dashboard

### US-11 — Melihat Laporan Stok

* **ID Story:** US-11
* **User Story:** Sebagai **Admin Gudang**, saya ingin melihat laporan stok, sehingga saya dapat mengetahui kondisi inventori berdasarkan transaksi yang tercatat.
* **Prioritas:** Must Have
* **Keterlacakan:**

  * Diturunkan dari: **FR-10**
  * Didukung oleh: **NFR-06**
* **Kriteria Penerimaan:**

  * **Given** data transaksi tersedia, **When** Admin meminta laporan stok, **Then** sistem menampilkan laporan berdasarkan data transaksi.
  * Informasi stok dapat digunakan untuk pemantauan inventori.
  * Waktu pembuatan laporan berkurang dibandingkan proses manual sesuai target KPI.

### US-12 — Melihat Ringkasan Dashboard

* **ID Story:** US-12
* **User Story:** Sebagai **Manajer Gudang/Pimpinan**, saya ingin melihat ringkasan kondisi stok dan transaksi, sehingga saya dapat memantau kondisi inventori dengan lebih cepat.
* **Prioritas:** Should Have
* **Keterlacakan:**

  * Diturunkan dari: **FR-17**
* **Kriteria Penerimaan:**

  * Sistem menampilkan ringkasan informasi stok.
  * Sistem menampilkan informasi transaksi yang tersedia.
  * Informasi dapat diakses oleh pengguna yang memiliki kewenangan.

### US-13 — Memfilter Laporan

* **ID Story:** US-13
* **User Story:** Sebagai **Admin Gudang**, saya ingin memfilter laporan berdasarkan kriteria tertentu, sehingga saya dapat menemukan informasi yang dibutuhkan dengan lebih cepat.
* **Prioritas:** Should Have
* **Keterlacakan:**

  * Diturunkan dari: **FR-19**
  * Didukung oleh: **NFR-05, NFR-06**
* **Kriteria Penerimaan:**

  * Admin dapat menentukan kriteria laporan.
  * Sistem hanya menampilkan data yang sesuai dengan kriteria.
  * Waktu pencarian informasi lebih cepat dibandingkan pencarian manual.

### US-14 — Menerima Notifikasi Stok

* **ID Story:** US-14
* **User Story:** Sebagai **Admin Gudang**, saya ingin menerima peringatan ketika stok berpotensi kritis, sehingga saya dapat segera memperhatikan barang tersebut.
* **Prioritas:** Should Have
* **Keterlacakan:**

  * Diturunkan dari: **FR-18**
  * Didukung oleh: **FR-12, BR-09**
* **Kriteria Penerimaan:**

  * **Given** sistem mendeteksi indikasi stok kritis, **When** kondisi tersebut terpenuhi, **Then** sistem memberikan peringatan.
  * Peringatan mengidentifikasi barang yang perlu diperhatikan.
  * Peringatan tidak secara otomatis melakukan pembelian barang.

---

# Epik 6 — Fitur Cerdas AI: OCR & Intelligent Document Parsing ★

### US-15 — Membaca Dokumen dengan OCR ★

* **ID Story:** US-15
* **User Story:** Sebagai **Admin Gudang**, saya ingin sistem membaca nota, tanda terima, atau bukti peminjaman menggunakan OCR, sehingga saya tidak perlu mengetik seluruh informasi secara manual.
* **Prioritas:** Must Have
* **Keterlacakan:**

  * Diturunkan dari: **FR-14**
  * Didukung oleh: **NFR-01, NFR-07, BR-12**
* **Kriteria Penerimaan:**

  * **Given** Admin memasukkan dokumen yang dapat dibaca, **When** proses OCR dijalankan, **Then** sistem menghasilkan teks dari dokumen.
  * Proses OCR menghasilkan informasi yang dapat digunakan untuk tahap ekstraksi.
  * Akurasi OCR mencapai minimal **80%** pada data pengujian.

### US-16 — Mengekstraksi Informasi Dokumen ★

* **ID Story:** US-16
* **User Story:** Sebagai **Admin Gudang**, saya ingin sistem mengekstraksi informasi relevan dari dokumen, sehingga data dapat digunakan untuk membantu pencatatan transaksi.
* **Prioritas:** Must Have
* **Keterlacakan:**

  * Diturunkan dari: **FR-15**
  * Didukung oleh: **NFR-01, BR-12**
* **Kriteria Penerimaan:**

  * **Given** teks dokumen berhasil dibaca, **When** proses parsing dilakukan, **Then** sistem menghasilkan data terstruktur.
  * Data hasil ekstraksi dapat diperiksa oleh Admin.
  * Informasi yang tidak berhasil dibaca tidak boleh dianggap otomatis benar.

### US-17 — Memvalidasi Hasil OCR ★

* **ID Story:** US-17
* **User Story:** Sebagai **Admin Gudang**, saya ingin memeriksa dan mengoreksi hasil OCR, sehingga data yang digunakan dalam transaksi tetap valid.
* **Prioritas:** Must Have
* **Keterlacakan:**

  * Diturunkan dari: **FR-16**
  * Didukung oleh: **NFR-01, NFR-03, BR-12, BR-13**
* **Kriteria Penerimaan:**

  * **Given** hasil OCR telah tersedia, **When** Admin memeriksanya, **Then** Admin dapat memvalidasi hasil.
  * Admin dapat melakukan koreksi terhadap informasi yang salah.
  * Data hanya digunakan setelah proses validasi Admin.

---

# Epik 7 — Fitur Cerdas AI: Forecasting & Auto-Reorder Point ★

### US-18 — Memprediksi Kebutuhan Stok ★

* **ID Story:** US-18
* **User Story:** Sebagai **Admin Gudang**, saya ingin sistem memprediksi kebutuhan barang berdasarkan riwayat pengeluaran dan peminjaman, sehingga saya dapat mengetahui barang yang berpotensi mengalami kekurangan stok.
* **Prioritas:** Must Have
* **Keterlacakan:**

  * Diturunkan dari: **FR-11**
  * Didukung oleh: **NFR-02, NFR-07, BR-11**
* **Kriteria Penerimaan:**

  * **Given** data historis tersedia, **When** forecasting dijalankan, **Then** sistem menghasilkan prediksi kebutuhan barang.
  * Hasil prediksi dapat digunakan untuk mengidentifikasi potensi kekurangan stok.
  * Proses AI memiliki latensi maksimal sesuai target **≤10 detik/proses**.

### US-19 — Mendeteksi Potensi Stok Habis ★

* **ID Story:** US-19
* **User Story:** Sebagai **Admin Gudang**, saya ingin sistem mengidentifikasi barang yang berpotensi habis, sehingga saya dapat melakukan tindakan sebelum stok benar-benar habis.
* **Prioritas:** Must Have
* **Keterlacakan:**

  * Diturunkan dari: **FR-12**
  * Didukung oleh: **NFR-02, BR-09, BR-11**
* **Kriteria Penerimaan:**

  * **Given** hasil forecasting menunjukkan risiko kekurangan stok, **When** sistem mengevaluasi hasil tersebut, **Then** barang ditandai sebagai berpotensi kritis.
  * Sistem memberikan informasi/peringatan terhadap barang tersebut.
  * Keberhasilan deteksi mencapai minimal **80% pada data pengujian**.

### US-20 — Menentukan Reorder Point ★

* **ID Story:** US-20
* **User Story:** Sebagai **Admin Gudang**, saya ingin sistem memberikan indikator reorder point berdasarkan penggunaan dan forecasting, sehingga saya dapat mengetahui kapan stok perlu mendapatkan perhatian.
* **Prioritas:** Must Have
* **Keterlacakan:**

  * Diturunkan dari: **FR-13**
  * Didukung oleh: **BR-09, BR-10, BR-11**
* **Kriteria Penerimaan:**

  * **Given** data penggunaan dan forecasting tersedia, **When** sistem menentukan indikator reorder point, **Then** sistem menghasilkan batas/peringatan stok.
  * Barang yang mencapai kondisi indikator mendapatkan peringatan.
  * Reorder point hanya menjadi **informasi pendukung**, bukan perintah pembelian otomatis.

---

# Ringkasan Product Backlog

| Epik                                 |               Story |  Must  | Should |
| ------------------------------------ | ------------------: | :----: | :----: |
| **1. Otentikasi & Hak Akses**        |    US-01 s.d. US-02 |    2   |    —   |
| **2. Master Data & Inventori**       |    US-03 s.d. US-04 |    2   |    —   |
| **3. Transaksi Operasional**         |    US-05 s.d. US-07 |    3   |    —   |
| **4. Peminjaman & Pengembalian**     |    US-08 s.d. US-10 |    3   |    —   |
| **5. Pelaporan & Dashboard**         |    US-11 s.d. US-14 |    1   |    3   |
| **6. OCR & Parsing ★**               |    US-15 s.d. US-17 |    3   |    —   |
| **7. Forecasting & Reorder Point ★** |    US-18 s.d. US-20 |    3   |    —   |
| **Total**                            | **20 User Stories** | **17** |  **3** |

### Prioritas MVP

**Must Have — 17 story**

> Login → Hak Akses → Master Barang → Barang Masuk/Keluar → Peminjaman/Pengembalian → Status → Riwayat → Laporan → ★ OCR → ★ Forecasting → ★ Reorder Point.

**Should Have — 3 story**

> Dashboard → Filter Laporan → Notifikasi Stok.

Dengan struktur ini, **setiap User Story dapat ditelusuri kembali ke minimal satu FR pada SRS**, sedangkan NFR dan BR digunakan sebagai pendukung acceptance criteria dan batas kualitas/perilaku sistem.
