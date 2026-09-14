Ini prompt lanjutan untuk app LumiPOS yang sudah kamu bangun di thread ini. Kerjakan sebagai perubahan bertahap pada app yang sudah ada, bukan membangun ulang dari nol.

# 0. ATURAN UTAMA

Jangan hapus layar mana pun yang sudah ada. Jangan mengubah tata letak atau isi layar yang sudah jadi kecuali diminta eksplisit di prompt ini.

Kalau sebuah instruksi di bawah menuntut penyesuaian pada layar lama, sebutkan dulu layar mana dan apa yang berubah, lalu kerjakan. Jangan diam-diam menyesuaikan.

Satu pengecualian yang memang diizinkan: penyeragaman warna, ukuran teks, radius, dan spasi ke design token di Bagian 2. Itu memang harus diterapkan ke SEMUA layar, termasuk yang sudah jadi.

# 1. STRUKTUR HALAMAN

LumiPOS terdiri dari TIGA aplikasi terpisah. Masing-masing harus punya halaman atau route sendiri, tidak dicampur dalam satu halaman panjang:

- **Kasir** (route `/kasir`) - dipakai staf, tablet landscape dan desktop
- **Back-office** (route `/backoffice`) - dipakai pemilik usaha, desktop
- **Lumi-Order** (route `/order`) - dipakai pelanggan, mobile portrait

Ketiganya berbagi design token yang sama, tapi tidak berbagi navigasi. Kasir tidak punya menu ke Back-office, dan sebaliknya. Perpindahan antar app hanya lewat App Switcher di Bagian 4, yang merupakan alat bantu mockup, bukan bagian dari produk.

# 2. DESIGN TOKENS (sumber kebenaran tunggal)

Terapkan token ini ke SELURUH app, termasuk layar yang sudah jadi. Kalau ada nilai di layar lama yang berbeda dari daftar ini, samakan ke daftar ini.

## Warna inti
- Aksen (satu-satunya warna aksen di seluruh app): #14706B
- Aksen hover: #0F5B57
- Aksen lembut (latar badge ikon, chip terpilih): #D9EDF0
- Latar halaman: #F0F6F7
- Latar kartu: #FFFFFF
- Latar sekunder (baris berselang, panel dalam kartu): #F7FAFB
- Teks utama: #16282C
- Teks sekunder: #5E747A
- Teks di atas aksen: #FFFFFF
- Garis pemisah dan outline: #E3ECEE

## Warna status (HANYA untuk keadaan nyata, bukan dekorasi)
- Berhasil / Selesai / selisih kas lebih: latar #DFF3E4, teks #2C6B3F
- Info / Berjalan / Berikutnya: latar #D6EAF5, teks #1F5A7A
- Menunggu / netral: latar #EDF2F3, teks #5E747A
- Peringatan / stok menipis: latar #FBF0D9, teks #8A6520
- Galat / Batal / selisih kas kurang: latar #F9E1E1, teks #9A3535

## Tipografi: TEPAT 4 ukuran, tidak boleh ada yang kelima
- Display: 32px, line-height 1.15, weight 700 - total belanja, kembalian, angka besar
- Judul: 20px, line-height 1.3, weight 600 - judul layar, judul kartu
- Badan: 15px, line-height 1.5, weight 400 - teks normal, label tombol, isi tabel
- Kecil: 13px, line-height 1.4, weight 400 - label sekunder, keterangan, timestamp

Kalau sebuah layar terasa butuh ukuran kelima, perbaiki dengan bobot atau warna, jangan tambah ukuran.

Font: sans-serif ramah dan sedikit membulat. Bukan Inter. Bukan serif.
Monospace HANYA di preview struk termal. Di luar itu tidak ada monospace.

## Radius
- Kartu, panel, modal: 12px
- Tombol, input, select: 10px
- Badge status, chip kategori: pill penuh
- Kotak ikon kecil: 10px

## Target sentuh
- Minimum untuk semua elemen yang bisa ditekan: 44px
- Aksi utama di layar kasir (kartu produk, tombol bayar, keypad, stepper qty): 56px

## Spasi
Kelipatan 4: 4, 8, 12, 16, 24, 32.

## Bayangan
Diberi rona teal tipis, bukan hitam murni:
- Kartu: 0 1px 2px rgba(22,40,44,0.04), 0 2px 8px rgba(22,40,44,0.04)
- Terangkat: 0 4px 16px rgba(22,40,44,0.08)

# 3. AUDIT DAN PERBAIKI LAYAR YANG HILANG

Periksa satu per satu apakah layar berikut sudah ada di app, dan apakah sudah berada di halaman yang benar. Laporkan hasilnya sebagai daftar sebelum memperbaiki.

Untuk setiap layar yang HILANG, buat ulang mengikuti design token di Bagian 2.
Untuk setiap layar yang ADA tapi berada di halaman yang salah, pindahkan ke halaman yang benar.
Untuk setiap layar yang sudah ada dan sudah benar tempatnya, biarkan apa adanya kecuali penyeragaman token.

## Halaman /kasir
1. Login PIN, dengan state galat PIN salah yang tampil inline
2. Buka Shift (pilih cash drawer, saldo awal, nama staf)
3. Layar Kasir utama, katalog campuran: sebagian bergambar, sebagian belum difoto, dua gambar gagal dimuat
4. Layar Kasir, keadaan keranjang kosong
5. Layar Kasir, keadaan katalog kosong
6. Layar Kasir, keadaan mode offline
7. Popup Edit Item (stepper qty, ubah harga sementara, diskon per item, catatan, hapus)
8. Kartu Pembayaran (satu kartu, toggle metode, QRIS di dalam kartu yang sama)
9. Transaksi Berhasil (kembalian ukuran display, cetak, WhatsApp, email)
10. Preview Struk Termal 58mm dan 80mm
11. Riwayat Transaksi, termasuk keadaan kosong
12. Void dan Refund, dengan konfirmasi dan alasan wajib
13. Operasional Laci Kas (kas masuk, kas keluar, riwayat shift berjalan)
14. Tutup Kas dan Laporan Shift (selisih lebih hijau, kurang merah, nol netral)

## Halaman /backoffice
15. Dashboard (metrik hari ini, grafik tren 7 hari)
16. Katalog Produk, termasuk keadaan kosong
17. Edit Produk, dengan unggah gambar dan tiga keadaan galat berbeda
18. Manajemen Staf (PIN, hak akses berkelompok)
19. Laporan (filter rentang tanggal, per hari, per produk, per metode, per staf)
20. Pengaturan (profil usaha, struk, printer, pajak, metode pembayaran)

## Halaman /order
21. Masuk via QR (nama usaha, nomor meja terdeteksi)
22. Daftar Menu (kategori, kartu menu, item habis ditandai)
23. Detail Item (varian, add-on, catatan, stepper qty)
24. Keranjang
25. Pembayaran QRIS (memuat, siap dipindai, berhasil, kedaluwarsa)
26. Status Pesanan (diterima, disiapkan, siap)

# 4. APP SWITCHER (komponen baru)

Tambahkan kontrol untuk berpindah antar tiga app. Ini ALAT BANTU MOCKUP, bukan bagian dari produk yang akan dikirim ke pengguna.

Karena itu penampilannya harus jelas berbeda dari UI produk, supaya tidak pernah tertukar sebagai fitur:
- Bar tipis menempel di tepi atas layar, latar gelap netral (bukan teal, bukan warna produk)
- Tinggi maksimum 44px
- Tiga tombol segmented: Kasir, Back-office, Lumi-Order. Yang aktif ditandai jelas.
- Di sebelah kanan bar, tampilkan label kecil "Mockup preview" supaya statusnya eksplisit
- Bar ini melayang di atas konten, tidak mendorong layout app di bawahnya
- Bar ini muncul di ketiga halaman, posisinya sama persis

Tambahkan juga di dalam bar itu sebuah dropdown atau daftar untuk melompat ke layar tertentu di app yang sedang aktif, memakai penomoran dari Bagian 3. Ini supaya layar seperti keadaan kosong atau keadaan galat bisa dibuka langsung tanpa harus mensimulasikan alurnya.

# 5. ATURAN YANG BERLAKU DI SEMUA LAYAR

Beberapa di antaranya sudah dijaga test di repo produksi, jadi mockup yang melanggarnya akan bentrok dengan kode yang sudah ada.

1. Kartu produk TANPA gambar tidak menampilkan kotak abu-abu placeholder. Kartu langsung menampilkan nama dan harga saja.
2. Kartu produk yang gambarnya GAGAL DIMUAT menampilkan keadaan bernama: bingkai putus-putus, ikon, dan kata. Harus bisa dibedakan dari "belum difoto".
3. Grid katalog di layar kasir muat minimal 12 kartu tanpa scroll di tablet landscape.
4. Kartu Pembayaran adalah SATU kartu dengan toggle. Ganti metode tidak memindahkan halaman.
5. Nol karakter em-dash di seluruh teks yang terlihat pengguna. Pakai tanda hubung biasa atau titik.
6. Label ada di atas input, teks galat di bawah input. Placeholder tidak pernah menggantikan label.
7. Label tombol maksimum 3 kata, tidak boleh wrap ke baris kedua.
8. Setiap komponen interaktif punya state lengkap: default, hover, active, disabled, loading, galat.
9. Tidak ada titik berwarna dekoratif di depan item nav atau baris daftar.
10. Nama produk dan nama orang realistis Indonesia, bukan placeholder generik.

# 6. LAPORKAN SETELAH SELESAI

Sebutkan secara ringkas:
- Layar mana yang tadinya hilang dan sudah dibuat
- Layar mana yang dipindahkan antar halaman
- Layar lama mana saja yang warnanya atau ukuran teksnya berubah karena penyeragaman token
- Kalau ada instruksi di prompt ini yang tidak bisa dikerjakan, sebutkan mana dan kenapa