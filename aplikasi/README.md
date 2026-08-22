# Aplikasi simulasi SIMPUL

Satu berkas HTML tanpa proses pemasangan dan tanpa peladen. Seluruh perhitungan dijalankan di
dalam peramban.

## Menjalankan

Buka `index.html` melalui peramban mana pun, atau kunjungi versi daring pada GitHub Pages.

## Yang dihitung di dalam peramban

Masalah alokasi pengadaan diselesaikan sebagai masalah transportasi dengan biaya bertingkat.
Karena seluruh sambungan pada satu tingkat memiliki biaya yang sama, penyelesaian dengan
mendahulukan tingkat termurah sudah menghasilkan penyelesaian optimal. Hasilnya identik
dengan pemrograman linear pada notebook, yang telah diperiksa pada tujuh nilai batas serapan.

Urutan tingkat biaya:

1. Pasokan dari kabupaten tempat dapur berada, tanpa biaya perpindahan
2. Antarkabupaten di dalam satu gugus geografis, sebesar tarif friksi hasil lapis pertama
3. Menyeberang antargugus, dua kali tarif tersebut
4. Pendatangan dari luar provinsi, tiga kali tarif ditambah selisih harga

## Bacaan otomatis

Setiap lembar menyediakan bacaan yang disusun dari nilai numerik hasil perhitungan dan aturan
ambang yang tertulis di dalam kode, bukan dari teks yang disiapkan lebih dahulu. Apabila
sebuah pengujian tidak menghasilkan bukti yang cukup, bacaan akan menyatakan hal itu secara
terbuka. Bacaan berubah dengan sendirinya setiap kali parameter digeser.

## Ketergantungan

Aplikasi memuat huruf dari Google Fonts. Apabila jaringan tidak tersedia, aplikasi tetap
berjalan dengan huruf cadangan bawaan sistem tanpa kehilangan fungsi.
