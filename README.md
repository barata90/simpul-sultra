# SIMPUL — Diagnosis Friksi Pasar Pangan Sulawesi Tenggara

Repositori ini memuat seluruh bahan pengolahan, data, dan aplikasi simulasi untuk naskah
opini ilmiah **"Diagnosis Friksi Pasar dan Rancangan Pencocokan Permintaan Terjamin untuk
Stabilitas Pangan dan Hilirisasi Perikanan Sulawesi Tenggara"**, yang disusun untuk Kompetisi
Opini Ilmiah FORKESTRA 2026 yang diselenggarakan Kantor Perwakilan Bank Indonesia Provinsi
Sulawesi Tenggara.

**Aplikasi simulasi:** https://barata90.github.io/simpul-sultra/aplikasi/

---

## Pertanyaan yang dijawab

Provinsi Sulawesi Tenggara menghasilkan 272.457 ton perikanan tangkap senilai Rp7,16 triliun
pada 2024, namun pangan tetap menjadi penyumbang inflasi dan pendapatan nelayan tertinggal.
Diagnosis yang lazim menempatkan keterbatasan pembiayaan sebagai penyebab. Naskah ini
mengajukan bahwa persoalannya terletak pada pencocokan antara produksi yang tersebar dan
permintaan yang sudah tersedia.

Tiga pertanyaan yang dijawab:

1. Dari sumber apa friksi harga pangan antarwilayah berasal, dan apakah sumber tersebut
   menuntut penanganan yang sama.
2. Seberapa lebar sebaran harga yang dihadapi produsen dibandingkan yang dihadapi konsumen.
3. Bagaimana permintaan terjamin Program Makan Bergizi Gratis dapat dialokasikan sehingga
   sebanyak mungkin nilainya tertahan di dalam provinsi.

---

## Temuan pokok

| Temuan | Nilai |
|---|---|
| Sebaran harga produsen antarkabupaten, simpangan baku logaritma | 0,2977 |
| Sebaran harga eceran antarkota, ukuran yang sama | 0,0989 |
| Perbandingan keduanya | 3,01 kali lebih lebar di tingkat produsen |
| Rasio harga tertinggi terhadap terendah, jenis ikan sama | 2,69 kali |
| Kebutuhan ikan program terhadap produksi provinsi | 1,91 persen |
| Beban perpindahan antarkabupaten pada titik jenuh | 1.547 ton per tahun |
| Nilai yang sampai ke produsen | Rp136,5 miliar per tahun |

Friksi harga eceran terbagi menjadi dua jenis yang menuntut kebijakan berlawanan. Komoditas
yang didatangkan dari luar provinsi (gula pasir, beras, daging sapi, minyak goreng)
menghadapi selisih harga yang menetap dan bersumber dari biaya angkut. Komoditas yang
diproduksi setempat (cabai, bawang merah, telur, daging ayam) menghadapi selisih yang
bergejolak tanpa pusat yang menetap dan bersumber dari kegagalan koordinasi.

Temuan utama terletak pada tingkat produsen. Barang jadi bergerak antarkota sehingga harga
eceran saling mendekat, sedangkan hasil tangkapan tidak bergerak antarkabupaten sehingga
harga yang diterima nelayan tetap terpisah-pisah. Persoalan integrasi pasar di provinsi ini
terletak di hulu, bukan di hilir.

---

## Isi repositori

```
simpul-sultra/
├── notebook/
│   ├── 01_pengolahan_utama.ipynb        Lapis 1, 2, dan 3 serta tangga nilai perikanan
│   ├── 02_kalibrasi_parameter.ipynb     Penggantian asumsi dengan angka resmi dan kepekaan
│   └── 03_pemutakhiran_data.ipynb       Data produksi 2024 dan sebaran harga produsen
├── data/                                 Berkas sumber dari lembaga resmi
├── aplikasi/
│   └── index.html                        Aplikasi simulasi, satu berkas tanpa pemasangan
├── naskah/
│   └── Opini_Ilmiah_Forkestra2026_SIMPUL.docx
└── README.md
```

---

## Cara menjalankan notebook

Ketiga notebook disusun untuk Google Colab dan dijalankan berurutan. Setiap tahap membaca
arsip keluaran tahap sebelumnya, sehingga perhitungan yang tidak berubah tidak diulang.

1. Buka `notebook/01_pengolahan_utama.ipynb` di Google Colab.
2. Jalankan seluruh sel. Notebook akan memasang pustaka, membuat folder di Google Drive,
   meminta unggahan berkas dari folder `data/`, lalu mengunduh arsip hasil secara otomatis.
3. Buka `notebook/02_kalibrasi_parameter.ipynb`, unggah arsip hasil tahap pertama, jalankan.
4. Buka `notebook/03_pemutakhiran_data.ipynb`, unggah arsip tahap pertama dan kedua beserta
   `data/produksi_perikanan.xlsx`, jalankan.

Keluaran setiap tahap berupa tabel dalam format CSV, gambar beresolusi 300 titik per inci,
berkas interpretasi otomatis, dan catatan teknis yang merekam seluruh parameter serta asumsi.

Notebook ketiga menarik data produksi langsung dari antarmuka pemrograman Satu Data Provinsi
Sulawesi Tenggara. Apabila penarikan gagal, notebook beralih ke salinan tercatat yang
disertai tanggal penarikan, dan peralihan itu diumumkan pada keluaran.

---

## Cara menjalankan aplikasi simulasi

Aplikasi berupa satu berkas HTML tanpa proses pemasangan. Buka
`aplikasi/index.html` melalui peramban, atau kunjungi tautan GitHub Pages di bagian atas
halaman ini.

Seluruh perhitungan dijalankan di dalam peramban. Masalah alokasi pengadaan diselesaikan
sebagai masalah transportasi dengan biaya bertingkat, dan hasilnya identik dengan pemrograman
linear pada notebook. Setiap kali parameter digeser, seluruh angka, gambar, dan bacaan
otomatis dihitung ulang.

Lima lembar yang tersedia:

- **Ringkasan** — kedudukan kebutuhan program terhadap kapasitas provinsi
- **Friksi eceran** — taksonomi friksi dengan ambang yang dapat digeser
- **Harga produsen** — sebaran harga antarkabupaten menurut jenis ikan
- **Pencocokan** — alokasi optimal dan beban perpindahan antarkabupaten
- **Kepekaan** — kisi dua dimensi terhadap frekuensi menu dan berat porsi

---

## Metode

**Lapis pertama.** Selisih logaritma harga antarkota diuraikan menjadi komponen permanen dan
komponen sementara melalui model *unobserved components* (komponen tak teramati) bentuk taraf
lokal, diduga dengan kemungkinan maksimum melalui saringan Kalman. Pangsa ragam permanen
memisahkan friksi logistik dari kegagalan koordinasi. Pemeriksaan silang dilakukan dengan uji
akar unit Dickey dan Fuller yang diperluas serta uji kestasioneran Kwiatkowski dan rekan.

**Lapis kedua.** Penjalaran guncangan harga diukur dengan *generalized forecast error variance
decomposition* (dekomposisi varians galat ramalan tergeneralisasi) pada vektor autoregresi
berdimensi tinggi yang diduga persamaan demi persamaan dengan penyusutan kuadrat terkecil
terpilih.

**Lapis ketiga.** Sebaran harga produsen antarkabupaten diukur untuk jenis ikan yang sama,
lalu diuji terhadap dua penjelasan tandingan melalui simulasi pembulatan dan regresi dengan
efek tetap. Alokasi pengadaan dirumuskan sebagai pemrograman linear yang parameter biayanya
diturunkan dari hasil lapis pertama.

---

## Sumber data

| Sumber | Dipakai untuk |
|---|---|
| Kementerian Kelautan dan Perikanan, Portal Data Kelautan dan Perikanan | Produksi, nilai, dan harga produsen perikanan tangkap 2024 menurut jenis ikan dan kabupaten |
| Dinas Kelautan dan Perikanan Sulawesi Tenggara, Satu Data provinsi | Pemeriksaan silang produksi perikanan tangkap |
| Bank Indonesia, Pusat Informasi Harga Pangan Strategis | Harga eceran bulanan sepuluh komoditas pangan |
| Badan Pusat Statistik dan BPS Provinsi Sulawesi Tenggara | Indeks harga konsumen, perdagangan luar negeri, proyeksi penduduk |
| Badan Gizi Nasional | Struktur biaya program melalui Juknis Kepka 401.1 Tahun 2025 dan Siaran Pers SIPERS-98/BGN/02/2026 |
| Kementerian Kesehatan | Tabel Komposisi Pangan Indonesia |

Kedua sumber produksi disusun lembaga yang berbeda dan diperiksa silang dengan selisih total
0,45 persen, sehingga keduanya dirujuk bersama sebagai penguat satu sama lain.

---

## Keterbatasan

Empat keterbatasan disampaikan terbuka karena memengaruhi cara membaca hasil.

1. Sebagian besar harga pada berkas sumber tercatat dalam angka bulat, sehingga harga per
   pengamatan tidak presisi. Sebarannya telah diuji nyata melalui simulasi tiga ribu ulangan
   yang menunjukkan sebaran teramati 14,2 kali melampaui yang dapat dijelaskan pembulatan.
2. Perbedaan mutu dan ukuran ikan antarkabupaten tidak dapat dikendalikan dengan data yang
   tersedia, sehingga sebagian sebaran harga mungkin mencerminkan perbedaan mutu.
3. Sebaran eceran berasal dari dua kota sedangkan sebaran produsen berasal dari belasan
   kabupaten, sehingga perbandingan keduanya belum sepenuhnya setara.
4. Matriks jarak antarkabupaten tidak tersedia, sehingga biaya perpindahan disusun bertingkat
   menurut gugus geografis.

---

## Dugaan yang diuji dan gugur

Pencatatan ini disampaikan agar pembaca dapat menilai bahwa kesimpulan yang tersisa telah
melalui penyaringan.

| Dugaan | Alasan gugur |
|---|---|
| Kendari sebagai kota pusat penyalur guncangan harga | Rasio dominasi hanya 1,048 sehingga arus antarkota hampir setara |
| Program menaikkan inflasi pangan secara terukur | Sumbangan terhadap inflasi jauh di bawah angka inflasi teramati |
| Marjin rantai pasok sebesar 47,3 persen | Diturunkan dari dua asumsi yang saling bertentangan |
| Berat ikan lima puluh gram per porsi | Standar protein hewani menuntut 81 sampai 108 gram ikan utuh |
| Data produksi 2018 sebagai acuan sebaran ruang | Korelasi peringkat terhadap data 2024 hanya 0,449 |
| Kekuatan tawar pembeli sebagai sebab utama sebaran harga | Hanya menjelaskan 4,08 persen ragam harga di dalam jenis ikan yang sama |

---

## Lisensi

Kode pengolahan dan aplikasi tersedia di bawah lisensi MIT. Data mentah tetap tunduk pada
ketentuan lembaga penerbitnya masing-masing dan dicantumkan di sini untuk keperluan
penelusuran ulang perhitungan.
