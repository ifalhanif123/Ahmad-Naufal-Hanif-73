# DRAF SRS — Smart Inventory & Stock Demand Forecasting System

**Versi:** 0.1 (Draft)
**Status:** Draft
**Platform:** Website
**Target Implementasi:** MVP 3–4 bulan
**Acuan Kualitas:** ISO/IEC 25010 — Functional Suitability, Performance Efficiency, Usability, Security, Reliability
**Prioritas:** MoSCoW

---

# 1. Tujuan, Scope, & Definisi Istilah

## 1.1 Tujuan SRS

Software Requirements Specification (SRS) ini mendefinisikan kebutuhan sistem **Smart Inventory & Stock Demand Forecasting System** berdasarkan PRD, sehingga menjadi acuan dalam pengembangan, pengujian, dan validasi prototype.

Sistem ditujukan untuk mendigitalisasi pencatatan persediaan PT Jambi Agung Lestari yang sebelumnya dilakukan menggunakan kertas serta memberikan dukungan AI untuk prediksi kebutuhan stok dan ekstraksi data dokumen.

## 1.2 Scope Sistem

### In Scope

Sistem mencakup:

* Login dan hak akses pengguna.
* Pengelolaan data barang.
* Pencatatan barang masuk.
* Pencatatan barang keluar.
* Pencatatan peminjaman dan pengembalian barang.
* Pemantauan status peminjaman.
* Riwayat transaksi.
* Laporan stok.
* ★ Demand Forecasting.
* ★ Auto-Reorder Point/peringatan stok.
* ★ OCR & Intelligent Document Parsing.
* Dashboard, notifikasi stok, dan filter laporan sebagai fitur **Should Have**.

### Out of Scope

* Pembelian barang secara otomatis.
* Integrasi dengan supplier.
* Pengelolaan pembayaran.
* Aplikasi mobile native.
* ERP perusahaan secara keseluruhan.
* Chatbot/AI generatif.
* Keputusan pembelian otomatis oleh AI.

---

## 1.3 Definisi Istilah

| Istilah                          | Definisi                                                                                                              |
| -------------------------------- | --------------------------------------------------------------------------------------------------------------------- |
| **SRS**                          | Dokumen yang mendefinisikan kebutuhan perangkat lunak yang harus dipenuhi sistem.                                     |
| **MVP**                          | Minimum Viable Product, yaitu versi minimum sistem untuk membuktikan fungsi dan nilai utama produk.                   |
| **OCR**                          | Optical Character Recognition, teknologi untuk mengenali teks dari dokumen/gambar.                                    |
| **Intelligent Document Parsing** | Proses mengekstraksi informasi relevan dari dokumen agar dapat digunakan sebagai data sistem.                         |
| **Forecasting**                  | Proses memprediksi kebutuhan/penggunaan stok berdasarkan data historis.                                               |
| **Demand Forecasting**           | Prediksi kebutuhan suatu barang pada periode mendatang berdasarkan riwayat penggunaan/pengeluaran.                    |
| **Reorder Point**                | Batas kondisi stok yang digunakan sebagai indikator bahwa barang perlu mendapatkan perhatian untuk pengadaan kembali. |
| **Auto-Reorder Point**           | Penentuan/penyesuaian batas peringatan stok berdasarkan hasil pengolahan data penggunaan/prediksi.                    |
| **Stok**                         | Jumlah barang yang tercatat tersedia dalam sistem.                                                                    |
| **Barang Masuk**                 | Barang yang diterima gudang dari kurir.                                                                               |
| **Barang Keluar**                | Barang yang dikeluarkan untuk karyawan.                                                                               |
| **Peminjaman**                   | Transaksi ketika barang operasional diberikan kepada karyawan untuk digunakan sementara.                              |
| **Pengembalian**                 | Transaksi ketika barang yang dipinjam dikembalikan.                                                                   |

---

# 2. User & Stakeholder, Lingkungan Operasi, Asumsi & Dependensi

## 2.1 Profil Pengguna

| Pengguna                    | Kebutuhan Utama                                             | Tingkat Akses |
| --------------------------- | ----------------------------------------------------------- | ------------- |
| **Admin Gudang**            | Mengelola transaksi, stok, peminjaman, dokumen, dan laporan | **Tinggi**    |
| **Karyawan**                | Melakukan/memantau peminjaman barang                        | **Sedang**    |
| **Manajer Gudang/Pimpinan** | Memantau kondisi stok dan informasi laporan/prediksi        | **Tinggi**    |
| **Kurir**                   | Menyerahkan barang dan tanda terima                         | **Terbatas**  |

> **[ASUMSI-07]** Detail hak akses setiap peran belum ditentukan dalam PRD. Oleh karena itu, tingkat akses di atas merupakan batas konseptual dan perlu divalidasi pada tahap lanjutan.

## 2.2 Lingkungan Operasi

| Komponen   | Kebutuhan                                                                   |
| ---------- | --------------------------------------------------------------------------- |
| Platform   | Website                                                                     |
| Browser    | Browser web modern                                                          |
| Web Server | Server yang mendukung PHP                                                   |
| Backend    | PHP dengan CodeIgniter atau Laravel                                         |
| Database   | MySQL                                                                       |
| Frontend   | HTML dengan Bootstrap atau Tailwind                                         |
| Koneksi    | **[ASUMSI-08]** Sistem membutuhkan koneksi jaringan untuk mengakses website |

Detail spesifikasi server dan browser minimum **belum ditentukan dalam PRD**.

## 2.3 Asumsi

| ID          | Asumsi                                                                                     |
| ----------- | ------------------------------------------------------------------------------------------ |
| [ASUMSI-01] | Admin Gudang merupakan pengguna utama sistem.                                              |
| [ASUMSI-02] | Tersedia data historis pengeluaran/peminjaman untuk kebutuhan forecasting.                 |
| [ASUMSI-03] | Nota/tanda terima/bukti peminjaman memiliki kualitas yang cukup untuk diproses OCR.        |
| [ASUMSI-04] | Manajer/Pimpinan membutuhkan informasi kondisi stok dan peringatan stok.                   |
| [ASUMSI-05] | Sistem tidak menggantikan keputusan manusia dalam pengadaan barang.                        |
| [ASUMSI-06] | Target KPI pada PRD merupakan target awal prototype karena baseline aktual belum tersedia. |
| [ASUMSI-07] | Hak akses setiap peran perlu divalidasi lebih lanjut.                                      |
| [ASUMSI-08] | Pengguna mengakses sistem melalui jaringan yang tersedia.                                  |

## 2.4 Dependensi

| ID       | Dependensi                                                                   |
| -------- | ---------------------------------------------------------------------------- |
| [DEP-01] | Ketersediaan data historis stok/pengeluaran/peminjaman untuk forecasting.    |
| [DEP-02] | Ketersediaan dokumen nota/tanda terima/bukti peminjaman untuk pengujian OCR. |
| [DEP-03] | Ketersediaan PHP dan framework CodeIgniter/Laravel.                          |
| [DEP-04] | Ketersediaan MySQL untuk penyimpanan data.                                   |
| [DEP-05] | Ketersediaan browser web untuk mengakses sistem.                             |

---

# 3. Kebutuhan Fungsional (FR)

**Metode verifikasi:**

* **Test:** diuji berdasarkan skenario dan hasil yang diharapkan.
* **Demonstration:** diperlihatkan melalui prototype.
* **Inspection:** diperiksa keberadaan dan kesesuaiannya.

| ID        | Deskripsi Kebutuhan                                                                                                                                                                       | Prioritas  | Verifikasi    |
| --------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- | ------------- |
| **FR-01** | Sistem harus dapat melakukan autentikasi pengguna saat pengguna mengakses sistem → sistem memberikan akses sesuai akun pengguna.                                                          | Must       | Test          |
| **FR-02** | Sistem harus dapat menerapkan hak akses pengguna saat pengguna berhasil masuk → pengguna hanya memperoleh akses sesuai perannya.                                                          | Must       | Test          |
| **FR-03** | Sistem harus dapat mengelola data barang saat Admin Gudang melakukan pemeliharaan data → data barang tersimpan dan dapat digunakan dalam transaksi.                                       | Must       | Test          |
| **FR-04** | Sistem harus dapat mencatat barang masuk saat barang diterima dari kurir → jumlah stok tercatat sebagai barang masuk.                                                                     | Must       | Test          |
| **FR-05** | Sistem harus dapat mencatat barang keluar saat barang diberikan kepada karyawan → jumlah stok tercatat sebagai barang keluar.                                                             | Must       | Test          |
| **FR-06** | Sistem harus dapat mencatat peminjaman barang saat karyawan melakukan peminjaman → transaksi peminjaman tersimpan dengan status peminjaman.                                               | Must       | Test          |
| **FR-07** | Sistem harus dapat mencatat pengembalian barang saat barang yang dipinjam dikembalikan → transaksi pengembalian tersimpan dan status peminjaman diperbarui.                               | Must       | Test          |
| **FR-08** | Sistem harus dapat menampilkan status peminjaman saat Admin Gudang atau pihak berwenang melihat transaksi → sistem menampilkan status barang yang masih dipinjam atau telah dikembalikan. | Must       | Test          |
| **FR-09** | Sistem harus dapat mencatat riwayat transaksi saat transaksi stok dilakukan → histori transaksi dapat ditelusuri.                                                                         | Must       | Test          |
| **FR-10** | Sistem harus dapat menampilkan laporan stok saat pengguna berwenang meminta informasi stok → sistem menghasilkan informasi stok berdasarkan data transaksi.                               | Must       | Demonstration |
| **FR-11** | Sistem harus dapat memproses data historis pengeluaran/peminjaman saat data forecasting tersedia → sistem menghasilkan prediksi kebutuhan barang.                                         | **★ Must** | Test          |
| **FR-12** | Sistem harus dapat mengidentifikasi barang yang berpotensi habis saat hasil forecasting menunjukkan risiko kekurangan stok → sistem menghasilkan peringatan stok.                         | **★ Must** | Test          |
| **FR-13** | Sistem harus dapat menentukan indikator reorder point saat data penggunaan dan hasil forecasting tersedia → sistem menghasilkan batas/peringatan kebutuhan stok.                          | **★ Must** | Test          |
| **FR-14** | Sistem harus dapat membaca dokumen saat Admin Gudang memasukkan nota/tanda terima/bukti peminjaman → sistem menghasilkan teks hasil OCR.                                                  | **★ Must** | Test          |
| **FR-15** | Sistem harus dapat mengekstraksi informasi relevan saat dokumen berhasil dibaca → sistem menghasilkan data terstruktur yang dapat diperiksa Admin.                                        | **★ Must** | Test          |
| **FR-16** | Sistem harus dapat memungkinkan Admin Gudang memeriksa hasil OCR saat data dokumen telah diekstraksi → Admin dapat memvalidasi hasil sebelum digunakan.                                   | **★ Must** | Demonstration |
| **FR-17** | Sistem harus dapat menampilkan ringkasan informasi stok saat pengguna berwenang membuka dashboard → sistem menampilkan informasi ringkas yang tersedia.                                   | Should     | Demonstration |
| **FR-18** | Sistem harus dapat memberikan notifikasi saat terdapat indikasi stok yang perlu diperhatikan → pengguna menerima informasi/peringatan stok.                                               | Should     | Test          |
| **FR-19** | Sistem harus dapat memfilter laporan saat pengguna menentukan kriteria laporan → sistem menampilkan data sesuai kriteria.                                                                 | Should     | Test          |
| **FR-20** | Sistem harus dapat menampilkan grafik tren stok saat data transaksi tersedia → sistem menampilkan tren penggunaan/stok.                                                                   | Could      | Demonstration |
| **FR-21** | Sistem harus dapat menampilkan riwayat hasil prediksi saat hasil forecasting tersedia → sistem menampilkan hasil prediksi sebelumnya.                                                     | Could      | Demonstration |
| **FR-22** | Sistem harus dapat menyediakan ekspor laporan saat pengguna meminta laporan dalam format yang didukung → sistem menghasilkan file laporan.                                                | Could      | Demonstration |

---

# 4. Kebutuhan Non-Fungsional (NFR)

> Target berikut mengacu pada KPI PRD. Spesifikasi yang tidak tersedia secara eksplisit ditandai sebagai **[ASUMSI]**.

| ID         | Kategori ISO/IEC 25010 | Metrik & Target Terukur                                                                          | Kondisi Pengukuran                                          | Prioritas |
| ---------- | ---------------------- | ------------------------------------------------------------------------------------------------ | ----------------------------------------------------------- | --------- |
| **NFR-01** | Functional Suitability | Akurasi OCR ≥ **80%**                                                                            | Diuji pada dokumen uji yang tersedia                        | Must      |
| **NFR-02** | Functional Suitability | Keberhasilan deteksi stok berpotensi habis ≥ **80%**                                             | Dibandingkan dengan kondisi pada data pengujian             | Must      |
| **NFR-03** | Functional Suitability | Akurasi pencatatan stok ≥ **90%**                                                                | Dibandingkan dengan hasil pengecekan stok fisik             | Must      |
| **NFR-04** | Performance Efficiency | Waktu pencatatan transaksi turun ≥ **30%**                                                       | Dibandingkan proses manual dengan proses menggunakan sistem | Must      |
| **NFR-05** | Performance Efficiency | Waktu pencarian data turun ≥ **50%**                                                             | Dibandingkan waktu pencarian manual                         | Must      |
| **NFR-06** | Performance Efficiency | Waktu pembuatan laporan turun ≥ **50%**                                                          | Dibandingkan proses manual                                  | Must      |
| **NFR-07** | Performance Efficiency | Latensi proses AI **[ASUMSI-09] ≤10 detik/transaksi dokumen atau prediksi**                      | Diukur dari permintaan proses AI hingga hasil ditampilkan   | Should    |
| **NFR-08** | Security               | Pengguna hanya dapat mengakses fungsi sesuai hak aksesnya                                        | Pengujian menggunakan beberapa peran pengguna               | Must      |
| **NFR-09** | Security               | Data transaksi tidak dapat diakses oleh pengguna tanpa hak akses                                 | Pengujian akses terhadap data pengguna lain                 | Must      |
| **NFR-10** | Security               | Data autentikasi harus terlindungi dari akses pengguna yang tidak berwenang                      | Inspection/Test                                             | Must      |
| **NFR-11** | Security / Privacy     | Data dokumen yang diproses hanya digunakan untuk kebutuhan pengelolaan inventori **[ASUMSI-10]** | Pemeriksaan alur penggunaan data                            | Must      |
| **NFR-12** | Usability              | ≥ **90%** pengguna uji dapat menyelesaikan skenario transaksi utama **[ASUMSI-11]**              | Pengujian tugas kepada pengguna uji                         | Should    |
| **NFR-13** | Usability              | Waktu operasional pencatatan dan pencarian mengikuti target pengurangan waktu pada KPI           | Pengujian skenario operasional utama                        | Must      |
| **NFR-14** | Reliability            | ≥ **95%** transaksi peminjaman memiliki status yang jelas                                        | Pemeriksaan data transaksi                                  | Must      |
| **NFR-15** | Reliability            | Sistem mempertahankan data transaksi setelah proses penyimpanan berhasil                         | Pengujian penyimpanan dan pengambilan kembali data          | Must      |

### Catatan NFR AI

Target **latensi ≤10 detik** dan **usability ≥90%** diberi tanda **[ASUMSI-09]** dan **[ASUMSI-11]** karena PRD tidak menentukan angka tersebut. Angka dapat disesuaikan setelah pengujian awal prototype.

---

# 5. Kebutuhan Data Minimum Fitur AI

## 5.1 ★ Feature AI 1 — Demand Forecasting & Auto-Reorder Point

### Input → Proses → Output

| Tahap            | Kebutuhan                                                                                                                         |
| ---------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| **Input**        | Identitas barang, riwayat pengeluaran, riwayat peminjaman, dan informasi stok yang tersedia.                                      |
| **Proses/Model** | Sistem menganalisis pola penggunaan historis untuk menghasilkan estimasi kebutuhan barang.                                        |
| **Analisis**     | Hasil prediksi dibandingkan dengan kondisi stok untuk mengidentifikasi barang yang berpotensi mencapai kondisi kritis.            |
| **Output**       | Prediksi kebutuhan barang, indikator risiko stok habis, dan peringatan/reorder point.                                             |
| **Validasi**     | Admin Gudang dapat menggunakan hasil tersebut sebagai informasi pendukung dan tetap melakukan keputusan/verifikasi secara manual. |

**Data minimum:**

1. ID/nama barang.
2. Riwayat jumlah barang keluar.
3. Riwayat jumlah barang dipinjam.
4. Informasi stok.
5. Periode/tanggal transaksi.

> **[ASUMSI-12]** Minimal diperlukan riwayat transaksi yang memiliki tanggal/periode dan jumlah penggunaan agar pola penggunaan dapat dianalisis.

---

## 5.2 ★ Feature AI 2 — OCR & Intelligent Document Parsing

### Input → Proses → Output

| Tahap        | Kebutuhan                                                                      |
| ------------ | ------------------------------------------------------------------------------ |
| **Input**    | Foto/scan nota, tanda terima, atau bukti peminjaman.                           |
| **Proses**   | Sistem membaca teks dokumen menggunakan OCR.                                   |
| **Parsing**  | Sistem mengidentifikasi informasi yang relevan dari teks hasil OCR.            |
| **Output**   | Data hasil ekstraksi yang dapat diperiksa oleh Admin Gudang.                   |
| **Validasi** | Admin memeriksa dan mengoreksi hasil sebelum data digunakan sebagai transaksi. |

**Data minimum:**

* Dokumen sumber.
* Teks hasil OCR.
* Informasi relevan yang berhasil diekstraksi.
* Hasil validasi/koreksi Admin.

> **[ASUMSI-13]** Field dokumen yang diekstraksi minimal berupa informasi yang diperlukan untuk mencatat transaksi, sedangkan daftar field spesifik belum ditentukan dalam PRD.

---

# 6. Aturan Bisnis (Business Rules — BR)

| ID        | Aturan Bisnis                                                                                                                                             |
| --------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **BR-01** | Setiap barang masuk harus dicatat sebagai transaksi sebelum perubahan stok dianggap sebagai transaksi resmi.                                              |
| **BR-02** | Barang masuk menyebabkan jumlah stok bertambah sesuai jumlah barang yang diterima.                                                                        |
| **BR-03** | Barang keluar menyebabkan jumlah stok berkurang sesuai jumlah barang yang dikeluarkan.                                                                    |
| **BR-04** | Peminjaman barang harus dicatat agar keberadaan barang dapat ditelusuri.                                                                                  |
| **BR-05** | Barang yang sedang dipinjam harus memiliki status peminjaman yang menunjukkan bahwa barang belum dikembalikan.                                            |
| **BR-06** | Pengembalian barang harus mengacu pada transaksi peminjaman yang bersangkutan.                                                                            |
| **BR-07** | Setelah barang dikembalikan, status peminjaman harus diperbarui menjadi telah dikembalikan.                                                               |
| **BR-08** | Setiap transaksi stok harus masuk ke dalam riwayat transaksi agar dapat digunakan untuk pelaporan dan analisis.                                           |
| **BR-09** | Sistem harus memberikan peringatan ketika hasil forecasting menunjukkan bahwa suatu barang berpotensi mencapai kondisi stok kritis.                       |
| **BR-10** | Reorder point digunakan sebagai indikator kebutuhan perhatian/pengadaan kembali dan bukan sebagai perintah pembelian otomatis.                            |
| **BR-11** | Hasil forecasting merupakan informasi pendukung dan tidak menggantikan keputusan Admin Gudang atau Manajer/Pimpinan.                                      |
| **BR-12** | Hasil OCR harus dapat diverifikasi Admin sebelum digunakan sebagai data transaksi.                                                                        |
| **BR-13** | Sistem tidak boleh menganggap hasil OCR selalu benar 100%.                                                                                                |
| **BR-14** | **[ASUMSI-14]** Transaksi yang jumlahnya melebihi stok tersedia harus ditolak atau meminta koreksi Admin untuk mencegah pencatatan stok yang tidak valid. |
| **BR-15** | **[ASUMSI-15]** Stok kritis ditentukan berdasarkan indikator reorder point yang dihasilkan/ditetapkan sistem.                                             |

---

# 7. Matriks Traceability

| ID Requirement | PRD / Fitur Acuan              | Bukti Riset Terkait                                    |
| -------------- | ------------------------------ | ------------------------------------------------------ |
| FR-01          | Login & Hak Akses              | Mendukung pengelolaan sistem digital                   |
| FR-02          | Login & Hak Akses              | Pengelolaan pengguna sistem                            |
| FR-03          | Master Data Barang             | Fakta 1 — pencatatan stok masih manual                 |
| FR-04          | Barang Masuk                   | Fakta 5 — penerimaan barang dari kurir                 |
| FR-05          | Barang Keluar                  | Fakta 5 — pengeluaran barang untuk karyawan            |
| FR-06          | Peminjaman Barang              | Fakta 5 — proses peminjaman barang                     |
| FR-07          | Pengembalian Barang            | Fakta 5 — proses pengembalian barang                   |
| FR-08          | Status Peminjaman              | Problem — status peminjaman tidak jelas                |
| FR-09          | Riwayat Transaksi              | Fakta 2 — pencarian/rekap data manual memakan waktu    |
| FR-10          | Laporan Stok                   | Fakta 2 — pembuatan laporan lama                       |
| ★ FR-11        | ★ Demand Forecasting           | Value Proposition — prediksi kebutuhan stok            |
| ★ FR-12        | ★ Auto-Reorder Point           | Value Proposition — peringatan barang berpotensi habis |
| ★ FR-13        | ★ Auto-Reorder Point           | Tujuan AI — mendeteksi potensi kekurangan stok         |
| ★ FR-14        | ★ OCR                          | Fakta 1 & Value Proposition — mengurangi input manual  |
| ★ FR-15        | ★ Intelligent Document Parsing | Value Proposition — mengurangi ketik manual            |
| ★ FR-16        | ★ OCR                          | Non-goal — Admin tetap melakukan verifikasi            |
| FR-17          | Dashboard                      | Scope — Should Have                                    |
| FR-18          | Notifikasi Stok                | Scope — Should Have                                    |
| FR-19          | Filter Laporan                 | Scope — Should Have                                    |
| FR-20          | Grafik Tren Stok               | Scope — Could Have                                     |
| FR-21          | Riwayat Prediksi               | Scope — Could Have                                     |
| FR-22          | Ekspor Laporan                 | Scope — Could Have                                     |
| NFR-01         | ★ OCR                          | KPI — akurasi OCR ≥80%                                 |
| NFR-02         | ★ Forecasting                  | KPI — keberhasilan deteksi ≥80%                        |
| NFR-03         | Pengelolaan Stok               | KPI — akurasi stok ≥90%                                |
| NFR-04         | Efisiensi operasional          | KPI — waktu pencatatan turun ≥30%                      |
| NFR-05         | Pencarian data                 | KPI — waktu pencarian turun ≥50%                       |
| NFR-06         | Laporan                        | KPI — waktu laporan turun ≥50%                         |
| NFR-07         | ★ AI                           | **[ASUMSI-09]** target latensi prototype               |
| NFR-08         | Hak Akses                      | PRD — Login & Hak Akses                                |
| NFR-09         | Hak Akses                      | PRD — Login & Hak Akses                                |
| NFR-10         | Hak Akses                      | PRD — Login & Hak Akses                                |
| NFR-11         | **[ASUMSI-10]** Privasi        | **[ASUMSI-10]**                                        |
| NFR-12         | Usability                      | KPI efisiensi operasional + **[ASUMSI-11]**            |
| NFR-13         | Usability                      | KPI waktu pencatatan/pencarian/laporan                 |
| NFR-14         | Status Peminjaman              | KPI — kelengkapan status ≥95%                          |
| NFR-15         | Reliability                    | Fakta 3 — risiko kehilangan/kerusakan berkas fisik     |

---

## Ringkasan Batasan SRS

SRS ini **tidak mencakup** desain arsitektur, struktur database/ERD, UML, desain UI/mockup, pemilihan algoritma forecasting secara detail, maupun implementasi kode. Dokumen hanya mendefinisikan **apa yang harus dilakukan sistem dan kualitas yang harus dicapai**, sesuai batasan PRD.

Dengan demikian, kebutuhan inti MVP adalah:

**Pencatatan stok → barang masuk/keluar → peminjaman/pengembalian → laporan → ★ OCR → ★ Forecasting → ★ Peringatan/Reorder Point.**
