# SIMPUL Sulawesi Tenggara

Repositori ini memuat bahan pengolahan dan dua aplikasi simulasi untuk naskah opini ilmiah
**"Diagnosis Friksi Pasar dan Strategi Optimalisasi Penyerapan Permintaan untuk Stabilitas Pangan
dan Hilirisasi Perikanan Sulawesi Tenggara"**, yang disusun untuk Kompetisi Opini Ilmiah
FORKESTRA 2026 yang diselenggarakan Kantor Perwakilan Bank Indonesia Provinsi Sulawesi Tenggara.

SIMPUL (Sistem Intelijen Mitra Pangan Unggul Lokal) terdiri atas dua modul yang saling menyambung.

| Modul | Pertanyaan yang dijawab | Tautan |
|---|---|---|
| Halaman depan | Hubungan kedua modul | https://barata90.github.io/simpul-sultra/ |
| Modul 1 SIMPUL Pasar | Dari mana friksi harga pangan berasal, dan bagaimana permintaan Program Makan Bergizi Gratis dipenuhi dari dalam provinsi | https://barata90.github.io/simpul-sultra/aplikasi/ |
| Modul 2 SIMPUL Inflasi | Berapa dampaknya terhadap inflasi dan penduduk miskin, dan kombinasi kebijakan apa yang membawa inflasi ke rentang sasaran | https://barata90.github.io/simpul-sultra/inflasi/ |

Modul 1 adalah isi naskah. Modul 2 adalah pengembangan setelah naskah dikirim, yang meneruskan
temuan Modul 1 menjadi instrumen kebijakan dan isian data bulanan.

---

## Versi

| Versi | Tanggal | Isi |
|---|---|---|
| `naskah-forkestra-2026` | 22 Agustus 2026 | Notebook 01 sampai 03 dan aplikasi Modul 1 sebagaimana dirujuk naskah awal |
| Koreksi data Baubau | 23 September 2026 | Perbaikan penulisan nama wilayah pada notebook 03, angka naskah terkoreksi, nilai awal Modul 1 disesuaikan |
| Modul 2 dan halaman depan | 23 September 2026 | Notebook pengembangan 1 sampai 5, aplikasi SIMPUL Inflasi, navigasi antarmodul |

---

## Temuan pokok Modul 1 (angka terkoreksi)

| Temuan | Nilai |
|---|---|
| Sebaran harga produsen antarkabupaten, simpangan baku logaritma | 0,2977 |
| Sebaran harga eceran antarkota, ukuran yang sama | 0,0989 |
| Perbandingan keduanya | 3,01 kali lebih lebar di tingkat produsen |
| Rasio harga tertinggi terhadap terendah, jenis ikan sama | 2,69 kali |
| Kebutuhan ikan program terhadap produksi tangkap 2024 (272.457 ton) | 1,91 persen |
| Batas serapan terkecil agar seluruh kebutuhan terpenuhi dari dalam provinsi | 1,91 persen (baris 2,0 persen pada Tabel 3) |
| Perpindahan antarkabupaten pada batas serapan 2,0 persen | 1.547 ton per tahun, 29,8 persen pasokan setempat |
| Indeks ketidaksesuaian ruang | 0,3125 |
| Wilayah kepulauan yang surplus | 8 dari 9, uji Mann-Whitney satu arah nilai p 0,018 |
| Nilai yang sampai ke produsen | Rp136,3 miliar per tahun |

---

## Catatan koreksi 23 September 2026

Pada notebook `03_pemutakhiran_data.ipynb`, fungsi `samakan()` mengganti penulisan "Bau Bau"
sebelum huruf diseragamkan. Nama wilayah pada berkas KKP tertulis dengan huruf kapital, sehingga
penggantian tidak terjadi dan produksi Kota Baubau sebesar 18.705,5 ton tercatat nol pada tabel
sebaran ruang dan pemrograman linear. Fungsi tersebut telah diperbaiki.

| Butir | Naskah awal | Setelah koreksi |
|---|---|---|
| Penyebut produksi | 253.751 ton | 272.457 ton |
| Kebutuhan ikan program terhadap produksi | 2,05 persen | 1,91 persen |
| Batas serapan pada titik jenuh | 2,5 persen | 2,0 persen |
| Perpindahan antarkabupaten pada titik jenuh | 1.595 ton (30,7 persen) | 1.547 ton (29,8 persen) |
| Perpindahan pada batas serapan 5 persen | 18,2 persen | 12,2 persen |
| Indeks ketidaksesuaian ruang | 0,3503 | 0,3125 |
| Wilayah kepulauan surplus | 7 dari 9 (nilai p 0,057) | 8 dari 9 (nilai p 0,018) |
| Kebutuhan tertinggi pada kisi kepekaan | 6,10 persen (penyebut data 2018) | 4,58 persen |
| Nilai yang sampai ke produsen | Rp136,3 miliar | Rp136,3 miliar |

Kesimpulan naskah tidak berubah: kapasitas pasokan bukan kendala yang mengikat, dan yang
mengikat adalah penjadwalan perpindahan dari gugus kepulauan ke kabupaten daratan. Aplikasi
Modul 1 sejak awal memuat data Baubau yang benar, sehingga yang disesuaikan hanya nilai awal
batas serapan (dari 2,5 menjadi 2,0 persen) dan harga produsen (Rp26.239 per kilogram,
tertimbang volume tangkapan laut, sama dengan notebook).

---

## Isi repositori

```
simpul-sultra/
├── index.html                                    Halaman depan dua modul
├── aplikasi/
│   └── index.html                                Modul 1 SIMPUL Pasar
├── inflasi/
│   └── index.html                                Modul 2 SIMPUL Inflasi
├── notebook/
│   ├── 01_pengolahan_utama.ipynb                 Naskah: lapis 1, 2, dan 3 serta tangga nilai perikanan
│   ├── 02_kalibrasi_parameter.ipynb              Naskah: penggantian asumsi dengan angka resmi dan kepekaan
│   ├── 03_pemutakhiran_data.ipynb                Naskah: data produksi 2024, sebaran harga produsen, alokasi
│   ├── 1.Analisis_Forkestra2026_Sultra (olah).ipynb                   Pengembangan: friksi, penyerapan, kerangka simulasi
│   ├── 2.Simulasi_Inflasi_Kemiskinan_SADDSO_Sultra (olah).ipynb       Pengembangan: nowcast, arahan harga, perencana kemiskinan
│   ├── 3.Satelit_GEE_Forkestra2026_Sultra (olah).ipynb                Pengembangan: indikator citra satelit
│   ├── 4.Analisis_Kabkota_Forkestra2026_Sultra (olah).ipynb           Pengembangan: dampak per kabupaten dan kota
│   └── 5.Diagram_Sistem_Dinamis_Forkestra2026_Sultra (olah).ipynb     Pengembangan: diagram sebab-akibat
├── LICENSE
└── README.md
```

Angka pada naskah bersumber dari notebook 01 sampai 03. Notebook 1 sampai 5 adalah pengembangan
untuk Modul 2 dan dapat memakai asumsi yang berbeda. Contohnya, notebook 1 menghitung kebutuhan
ikan program 4.899 ton per tahun karena memakai protein hewani 17,5 gram per porsi (sekitar 94
gram ikan utuh), sedangkan naskah memakai 100 gram ikan utuh (5.196 ton). Kedua nilai berada di
dalam rentang standar gizi 81 sampai 108 gram yang diuji pada kisi kepekaan naskah.

---

## Dari temuan Modul 1 ke instrumen Modul 2

| Temuan atau rekomendasi Modul 1 | Dipakai di Modul 2 |
|---|---|
| Friksi struktural setara 5,29 persen harga eceran, bersumber dari biaya angkut | Menu Pasar ikan: penurunan margin distribusi melalui logistik dan rantai dingin |
| Permintaan terjamin Program Makan Bergizi Gratis dapat dipenuhi dari dalam provinsi | Menu Pasar ikan: tambahan penyerapan permintaan |
| Keterbukaan harga produsen antarkabupaten | Menu Input data: harga 18 jenis ikan per kota IHK dan di tingkat nelayan |
| Nilai Rp136,3 miliar per tahun dapat tertahan pada produsen | Dampak pada nilai tukar nelayan dan penduduk miskin per kabupaten dan kota |
| Ketahanan kesimpulan diuji melalui kisi kepekaan | Menu Uji ketahanan: akurasi nowcast, uji mundur, penapisan Morris, kalibrasi kemiskinan |

---

## Cara menjalankan

Notebook disusun untuk Google Colab. Notebook 01 sampai 03 dijalankan berurutan, dan setiap
tahap membaca arsip keluaran tahap sebelumnya. Notebook 1 sampai 5 juga dijalankan berurutan;
notebook 3 memerlukan akun Google Earth Engine.

Kedua aplikasi berupa satu berkas HTML tanpa pemasangan dan seluruh perhitungannya dijalankan
di dalam browser. Modul 2 menyimpan isian data bulanan di browser pengguna, sehingga tanggal,
proyeksi, dan uji ketahanan ikut diperbarui setiap kali data resmi bulan baru diisi.

---

## Sumber data

| Sumber | Dipakai untuk |
|---|---|
| Kementerian Kelautan dan Perikanan, Portal Data Kelautan dan Perikanan | Produksi, nilai, dan harga produsen perikanan tangkap 2024 menurut jenis ikan dan kabupaten |
| Dinas Kelautan dan Perikanan Sulawesi Tenggara, Satu Data provinsi | Pemeriksaan silang produksi perikanan tangkap (selisih total 0,45 persen) |
| Bank Indonesia, Pusat Informasi Harga Pangan Strategis | Harga eceran bulanan komoditas pangan |
| Badan Pusat Statistik dan BPS Provinsi Sulawesi Tenggara | Indeks harga konsumen, inflasi, nilai tukar petani dan nelayan, kemiskinan, perdagangan luar negeri, proyeksi penduduk |
| Badan Gizi Nasional | Struktur biaya dan standar gizi Program Makan Bergizi Gratis |
| Kementerian Keuangan | Sasaran inflasi 2025 sampai 2027 (PMK Nomor 31 Tahun 2024) |
| OCHA melalui Humanitarian Data Exchange | Batas administrasi kabupaten dan kota |

---

## Lisensi

Kode pengolahan dan aplikasi tersedia di bawah lisensi MIT. Data mentah tetap tunduk pada
ketentuan lembaga penerbitnya masing-masing.
