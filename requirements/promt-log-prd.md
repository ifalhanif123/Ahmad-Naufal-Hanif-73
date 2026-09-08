[Peran] 
Kamu adalah Product Manager Senior untuk produk Website berfitur AI (Smart Inventory Management System).

[Tugas] 
Susun DRAF PRD ringkas untuk "Smart Inventory & Stock Demand Forecasting System" berdasarkan data kasus nyata pada studi literatur PT Jambi Agung Lestari berikut.

[Konteks]
Problem statement : PT Jambi Agung Lestari menghadapi masalah pada sistem pencatatan stok gudang yang masih manual menggunakan kertas. Hal ini menyebabkan proses pemeliharaan data dan pembuatan laporan memakan waktu lama, data tidak relevan, laporan tidak akurat, serta berkas fisik rentan rusak atau hilang. Selain itu, sering terjadi ketidakcocokan antara stok tercatat dengan stok fisik, serta ketidakjelasan status peminjaman barang.

Target user        : Admin Gudang (staf operasional pencatatan keluar/masuk dan peminjaman barang) dan Karyawan (peminjam/penerima barang).

Stakeholder lain    : Manajer Gudang / Pimpinan Perusahaan (pengambil keputusan & pengawas) dan Kurir (pengirim barang).

Persona ringkas     : Admin Gudang yang memproses transaksi harian barang masuk/keluar/peminjaman, sering terhambat pencatatan kertas dan pencarian data manual saat merekap laporan.

Bukti riset         : 
1. Pencatatan stok barang masih manual menggunakan kertas oleh admin gudang.
2. Pembuatan laporan memakan waktu lama dan tidak relevan karena harus mengecek berkas satu per satu.
3. Berkas fisik rentan rusak, hilang, basah, atau terselip.
4. Sering terjadi ketidakcocokan antara pencatatan stok dan stok fisik gudang.
5. Proses operasional harian mencakup: penerimaan barang masuk dari kurir via tanda terima, pengeluaran barang untuk karyawan, serta peminjaman/pengembalian barang operasional proyek/kantor.

Platform & stack    : Website — PHP, MySQL, HTML (Framework CodeIgniter/Laravel), Bootstrap, Tailwind.

Fitur AI inti       : 
1. AI Stock Demand Forecasting & Auto-Reorder Point (Memprediksi barang mana yang akan habis berdasarkan riwayat peminjaman/pengeluaran barang dan memberikan peringatan otomatis).
2. OCR & Intelligent Document Parsing (Membaca dan memasukkan data nota/tanda terima dari kurir atau bukti peminjaman secara otomatis ke sistem tanpa ketik manual).

Konstrain           : Prototype dikembangkan dalam kurun waktu 1 semester (3-4 bulan); anggaran dan resource data AI terbatas.

[Format output]
1) Ringkasan eksekutif
2) Problem statement & bukti (pisahkan fakta riset vs asumsi)
3) Target user & stakeholder (buat tabel: Peran – Kebutuhan – Tingkat Pengaruh/Kepentingan)
4) Value proposition: Pain yang dikurangi, Gain yang diciptakan, dan Justifikasi mengapa fitur AI bukan gimmick (harus memecahkan bottleneck)
5) Tujuan produk & KPI terukur (cantumkan metric utama + cara mengukurnya)
6) Scope fitur 3 bulan: Tabel MoSCoW (fitur AI wajib diberi tanda ★)
7) Non-goals eksplisit
8) Asumsi, risiko utama, & strategi mitigasi

[Aturan]
- Hanya gunakan data pada [Konteks]; bila informasi kurang, tulis [ASUMSI-XX] lalu lanjutkan penalaran secara logis.
- Jangan menulis solusi teknis detail/arsitektur sistem/ERD/UML (itu bagian dari dokumen SRS/HLD/LLD).
- Gunakan Bahasa Indonesia baku, profesional, serta format Markdown yang rapi dan terstruktur.