Berikut saya pilih **Pilihan A — Fitur Cerdas OCR & Parsing Nota/Bukti Transaksi**, karena fitur ini memiliki alur yang jelas dari **dokumen → OCR → ekstraksi → verifikasi Admin → transaksi**, serta dapat diuji secara konkret berdasarkan target akurasi ≥80% dan latensi ≤10 detik.

# USE CASE DETAIL

## Smart Inventory & Stock Demand Forecasting System

### 1. Dokumen Use Case Detail

| Elemen                | Spesifikasi                                                                                                                                                                                                                                                                                                                     |
| --------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Use Case ID**       | **UC-01**                                                                                                                                                                                                                                                                                                                       |
| **Nama Use Case**     | **Fitur Cerdas OCR & Intelligent Document Parsing Nota/Bukti Transaksi**                                                                                                                                                                                                                                                        |
| **Aktor Utama**       | **Admin Gudang**                                                                                                                                                                                                                                                                                                                |
| **Deskripsi Ringkas** | Use case ini memungkinkan Admin Gudang memasukkan dokumen nota, tanda terima, atau bukti peminjaman ke sistem. Sistem membaca dokumen menggunakan OCR, mengekstraksi informasi relevan menjadi data terstruktur, kemudian memberikan hasil kepada Admin untuk diperiksa dan dikoreksi sebelum digunakan sebagai data transaksi. |
| **FR Terkait**        | FR-14, FR-15, FR-16                                                                                                                                                                                                                                                                                                             |
| **NFR Terkait**       | NFR-01, NFR-03, NFR-07                                                                                                                                                                                                                                                                                                          |
| **BR Terkait**        | BR-12, BR-13                                                                                                                                                                                                                                                                                                                    |
| **Prioritas**         | **Must Have ★**                                                                                                                                                                                                                                                                                                                 |

### Pre-kondisi

1. Admin Gudang telah berhasil login ke sistem.
2. Admin memiliki hak akses untuk melakukan pencatatan transaksi.
3. Admin memiliki dokumen nota, tanda terima, atau bukti peminjaman yang akan diproses.
4. Dokumen memiliki informasi yang relevan untuk pencatatan transaksi.
5. **[ASUMSI-16]** Dokumen tersedia dalam bentuk yang dapat dimasukkan ke sistem.

### Post-kondisi

Jika proses berhasil:

1. Sistem menghasilkan teks dari dokumen menggunakan OCR.
2. Sistem mengekstraksi informasi relevan menjadi data terstruktur.
3. Admin dapat memeriksa hasil ekstraksi.
4. Admin dapat mengoreksi informasi yang salah.
5. Data yang telah diverifikasi dapat digunakan untuk pencatatan transaksi.
6. Hasil AI tidak dianggap sebagai data transaksi final sebelum diverifikasi Admin.

---

## Skenario Utama — Happy Flow

1. **Aktor:** Admin Gudang memilih proses input dokumen transaksi.
2. **Aktor:** Admin memasukkan nota, tanda terima, atau bukti peminjaman ke sistem.
3. **Sistem:** Sistem menerima dokumen dan melakukan pemeriksaan awal terhadap keterbacaan dokumen.
4. **Sistem:** Sistem menjalankan proses OCR terhadap dokumen.
5. **Sistem:** Sistem menghasilkan teks berdasarkan informasi yang berhasil dibaca.
6. **Sistem:** Sistem melakukan parsing terhadap teks hasil OCR.
7. **Sistem:** Sistem menghasilkan data terstruktur yang relevan untuk transaksi, misalnya nama barang, jumlah barang, dan nomor nota.
8. **Sistem:** Sistem menampilkan hasil ekstraksi kepada Admin untuk diverifikasi.
9. **Aktor:** Admin memeriksa hasil ekstraksi dengan dokumen sumber.
10. **Aktor:** Jika terdapat kesalahan, Admin mengoreksi data tersebut.
11. **Aktor:** Admin melakukan konfirmasi bahwa data telah sesuai.
12. **Sistem:** Sistem menggunakan data yang telah diverifikasi sebagai data transaksi.
13. **Sistem:** Sistem mencatat data transaksi dan mempertahankan hasilnya dalam riwayat transaksi.

---

## Skenario Alternatif / Pengecualian

### AF-01 — Dokumen Buram atau Tidak Terbaca

1. Admin memasukkan dokumen ke sistem.
2. Sistem mencoba membaca dokumen menggunakan OCR.
3. Sistem mendeteksi bahwa informasi dokumen tidak dapat dibaca dengan memadai.
4. Sistem tidak menganggap hasil OCR sebagai data yang valid.
5. Sistem memberikan informasi kepada Admin bahwa dokumen perlu diperiksa.
6. Admin dapat memperbaiki atau memasukkan informasi secara manual.
7. Admin memverifikasi data sebelum data digunakan sebagai transaksi.

### AF-02 — Confidence/Hasil OCR di Bawah Ambang

1. Sistem selesai melakukan OCR dan parsing.
2. Hasil pembacaan memiliki tingkat confidence **<80%**.
3. Sistem menandai hasil tersebut sebagai hasil yang memerlukan verifikasi.
4. Sistem memberikan kesempatan kepada Admin untuk memeriksa dan mengoreksi data.
5. Admin memperbaiki informasi yang tidak sesuai.
6. Data baru dapat digunakan sebagai transaksi setelah Admin melakukan verifikasi.

### AF-03 — Data Dokumen Tidak Lengkap

1. Sistem berhasil membaca sebagian informasi dokumen.
2. Sistem mendeteksi bahwa informasi yang diperlukan belum lengkap.
3. Sistem tidak langsung menyimpan hasil tersebut sebagai transaksi final.
4. Admin melengkapi atau memperbaiki data yang kurang.
5. Admin melakukan verifikasi.
6. Sistem menyimpan data setelah data dinyatakan sesuai.

### AF-04 — Admin Mengoreksi Hasil OCR

1. Sistem menampilkan hasil ekstraksi.
2. Admin menemukan informasi yang berbeda dengan dokumen sumber.
3. Admin mengubah informasi yang salah.
4. Sistem menerima perubahan tersebut.
5. Admin melakukan konfirmasi.
6. Sistem menggunakan data hasil koreksi sebagai data transaksi.

### AF-05 — Proses AI Melebihi Batas Waktu

1. Admin memasukkan dokumen untuk diproses.
2. Sistem menjalankan OCR dan parsing.
3. Proses AI belum menghasilkan hasil setelah **10 detik**.
4. Sistem memberikan informasi bahwa proses AI belum berhasil memenuhi batas waktu.
5. Admin diberikan opsi untuk melakukan pemeriksaan dan pengisian data secara manual.
6. Sistem tidak menyimpan hasil AI yang belum diverifikasi sebagai transaksi final.

---

# 2. Acceptance Criteria

## Skenario 1 — OCR Berhasil dan Memenuhi Quality Gate

**Given**

* Admin Gudang telah login.
* Admin memasukkan dokumen tanda terima yang dapat dibaca.
* Dokumen mengandung informasi transaksi yang relevan.
* Hasil OCR memiliki akurasi/confidence minimal **80%**.

**When**

* Admin menjalankan proses OCR dan Intelligent Document Parsing.

**Then**

* Sistem menghasilkan teks dari dokumen.
* Sistem menghasilkan data terstruktur yang relevan untuk transaksi.
* Proses AI selesai dalam waktu **≤10 detik**.
* Hasil ekstraksi ditampilkan kepada Admin untuk diverifikasi.
* Data belum dianggap sebagai transaksi final sebelum Admin melakukan verifikasi.

**Status yang diharapkan:** **PASS**

---

## Skenario 2 — OCR Gagal / Confidence di Bawah 80%

**Given**

* Admin Gudang telah login.
* Admin memasukkan dokumen yang buram atau sulit dibaca.
* Hasil OCR memiliki confidence **<80%** atau informasi penting tidak berhasil diekstraksi.

**When**

* Admin menjalankan proses OCR dan Intelligent Document Parsing.

**Then**

* Sistem menandai hasil sebagai perlu verifikasi.
* Sistem tidak menganggap hasil OCR sebagai data yang benar secara otomatis.
* Sistem memberikan kesempatan kepada Admin untuk mengoreksi atau melengkapi data secara manual.
* Data transaksi hanya dapat digunakan setelah Admin melakukan verifikasi.
* Sistem tidak melakukan penyimpanan transaksi final berdasarkan hasil OCR yang belum diverifikasi.

**Status yang diharapkan:** **PASS**

---

## Quality Gate Use Case

| Parameter                 |                                 Target | Hasil yang Dinyatakan Lulus                                         |
| ------------------------- | -------------------------------------: | ------------------------------------------------------------------- |
| **Akurasi OCR/ekstraksi** |                                   ≥80% | Hasil mencapai minimal 80% pada data pengujian                      |
| **Latensi AI**            |                              ≤10 detik | Hasil diproses maksimal 10 detik                                    |
| **Verifikasi Admin**      |                                  Wajib | Admin dapat memeriksa hasil sebelum transaksi final                 |
| **Koreksi manual**        |                         Wajib tersedia | Admin dapat memperbaiki hasil OCR                                   |
| **Dokumen gagal dibaca**  | Tidak boleh menjadi transaksi otomatis | Sistem mengarahkan ke verifikasi/koreksi manual                     |
| **Confidence <80%**       |                       Perlu verifikasi | Sistem tidak menganggap hasil sebagai data final                    |
| **Integritas transaksi**  |                     Data terverifikasi | Hanya data yang telah diverifikasi yang digunakan sebagai transaksi |

### Traceability

**US-15 → FR-14 → NFR-01 & NFR-07 → UC-01**

**US-16 → FR-15 → NFR-01 → UC-01**

**US-17 → FR-16 → NFR-03 → BR-12 & BR-13 → UC-01**

Dengan demikian, **UC-01 mencakup seluruh alur tiga User Story AI OCR (US-15, US-16, US-17)** tanpa masuk ke ranah arsitektur teknis, database, UML, maupun desain UI.

Kalau dokumen ini akan kamu masukkan ke laporan skripsi, struktur di atas sudah bisa dijadikan **Use Case Detail/Spesifikasi Use Case**, sedangkan bagian **Acceptance Criteria + Quality Gate** bisa kamu gunakan sebagai dasar **test case pengujian fitur AI**.
