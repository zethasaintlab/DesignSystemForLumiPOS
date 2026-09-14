# LumiPOS Design Tokens

**Status: DRAFT, butuh verifikasi.** Nilai hex di bawah diperkirakan secara visual dari screenshot Lovable, bukan diambil sampel piksel. Sebelum file ini dikunci sebagai acuan, ambil nilai aslinya lewat panel Inspect di Figma (lihat tutorial yang menyertai file ini) dan koreksi angka yang meleset.

Sekali diverifikasi, file ini jadi satu-satunya sumber kebenaran untuk warna, tipografi, dan spasi di seluruh LumiPOS. Kasir app, back-office, dan Lumi-Order semuanya menurunkan nilai dari sini.

---

## KONFLIK YANG HARUS DIPUTUSKAN DULU

Kartu "Design system" di mockup menulis deskripsinya sebagai **"Teal hangat di atas kertas kopi"**, tapi latar yang benar-benar dirender terlihat **putih kebiruan pucat**, bukan krem kertas kopi.

Dua kemungkinan:
- Deskripsinya yang benar, dan rendering-nya meleset. Berarti latar harus diganti ke krem hangat.
- Rendering-nya yang benar, dan deskripsinya sisa dari arah desain lama. Berarti deskripsinya yang harus diperbarui.

Token di bawah ditulis mengikuti **apa yang benar-benar terlihat** (putih kebiruan), karena itu yang bisa saya amati. Kalau ternyata kamu memang mau krem, ganti `--surface-page` dan turunannya.

---

## Warna

### Inti

| Token | Perkiraan hex | Dipakai untuk |
|---|---|---|
| `--accent` | `#14706B` | Satu-satunya warna aksen. Tombol utama, ikon aktif, state terpilih. |
| `--accent-hover` | `#0F5B57` | Hover pada elemen beraksen. |
| `--accent-subtle` | `#D9EDF0` | Latar badge ikon, chip terpilih, highlight lembut. |
| `--surface-page` | `#F0F6F7` | Latar halaman. |
| `--surface-card` | `#FFFFFF` | Latar kartu dan panel. |
| `--surface-raised` | `#F7FAFB` | Baris berselang-seling, latar sekunder di dalam kartu. |
| `--text-primary` | `#16282C` | Judul, angka, teks utama. |
| `--text-secondary` | `#5E747A` | Label, keterangan, teks pendukung. |
| `--text-on-accent` | `#FFFFFF` | Teks di atas `--accent`. |
| `--border` | `#E3ECEE` | Garis pemisah, outline input, batas kartu. |

### Status

Dipakai HANYA untuk menyampaikan keadaan nyata. Tidak untuk dekorasi.

| Token | Perkiraan hex | Teks di atasnya | Dipakai untuk |
|---|---|---|---|
| `--status-success-bg` | `#DFF3E4` | `#2C6B3F` | Selesai, berhasil, selisih kas lebih. |
| `--status-info-bg` | `#D6EAF5` | `#1F5A7A` | Berikutnya, sedang berjalan, informasi. |
| `--status-pending-bg` | `#EDF2F3` | `#5E747A` | Menunggu, belum mulai, netral. |
| `--status-warning-bg` | `#FBF0D9` | `#8A6520` | Perlu perhatian, stok menipis. |
| `--status-danger-bg` | `#F9E1E1` | `#9A3535` | Galat, batal, selisih kas kurang. |

**Aturan kontras:** setiap pasangan latar dan teks di tabel status wajib lolos WCAG AA (4.5:1). Verifikasi ulang setelah hex final ditetapkan, jangan diasumsikan.

---

## Tipografi

**Tepat 4 ukuran. Tidak boleh ada yang kelima.**

Kalau sebuah layar terasa butuh ukuran kelima, itu tanda hierarkinya yang salah, bukan skalanya yang kurang. Perbaiki dengan bobot (weight) atau warna, bukan dengan menambah ukuran.

| Token | Perkiraan ukuran | Bobot | Dipakai untuk |
|---|---|---|---|
| `--text-display` | 32px / line-height 1.15 | 700 | Total belanja, kembalian, angka besar yang dibaca sekilas. |
| `--text-title` | 20px / line-height 1.3 | 600 | Judul layar, judul kartu. |
| `--text-body` | 15px / line-height 1.5 | 400 | Teks normal, label tombol, isi tabel. |
| `--text-small` | 13px / line-height 1.4 | 400 | Label sekunder, keterangan, timestamp. |

**Keluarga font:** sans-serif yang ramah dan sedikit membulat. Bukan Inter. Bukan serif.

**Pengecualian monospace:** HANYA di preview struk termal, karena mensimulasikan cetakan printer asli. Di luar itu tidak ada monospace di mana pun.

> **Perlu dicek:** di screenshot, judul hero terlihat lebih besar daripada judul kartu. Kalau benar keduanya ukuran berbeda, berarti sudah ada 5 ukuran, bukan 4. Konfirmasi lewat Inspect, lalu putuskan mana yang digabung.

---

## Bentuk dan Radius

Satu sistem, dipakai konsisten. Jangan campur.

| Token | Nilai | Dipakai untuk |
|---|---|---|
| `--radius-card` | 12px | Kartu, panel, modal. |
| `--radius-control` | 10px | Tombol, input, select. |
| `--radius-pill` | 999px | Badge status, chip kategori. |
| `--radius-icon-badge` | 10px | Kotak ikon kecil di kartu. |

---

## Target Sentuh

Ini bukan preferensi estetika. Kasir menekan sambil terburu-buru di depan pelanggan.

| Token | Nilai | Dipakai untuk |
|---|---|---|
| `--touch-min` | 44px | Semua elemen yang bisa ditekan, minimum absolut. |
| `--touch-primary` | 56px | Aksi utama di layar kasir: kartu produk, tombol bayar, keypad angka, stepper qty. |

---

## Spasi

Skala kelipatan 4.

| Token | Nilai |
|---|---|
| `--space-1` | 4px |
| `--space-2` | 8px |
| `--space-3` | 12px |
| `--space-4` | 16px |
| `--space-6` | 24px |
| `--space-8` | 32px |

---

## Bayangan

Diberi rona teal tipis, bukan hitam murni. Kartu hanya diberi bayangan kalau elevasinya menyampaikan hierarki nyata, bukan sebagai dekorasi default.

| Token | Nilai perkiraan |
|---|---|
| `--shadow-card` | `0 1px 2px rgba(22, 40, 44, 0.04), 0 2px 8px rgba(22, 40, 44, 0.04)` |
| `--shadow-raised` | `0 4px 16px rgba(22, 40, 44, 0.08)` |

---

## Aturan Global

Aturan ini berlaku di seluruh LumiPOS, dan beberapa di antaranya sudah dijaga test di repo.

1. **Satu warna aksen saja.** Teal dipakai di seluruh aplikasi. Tidak ada tombol biru di satu layar dan teal di layar lain.
2. **Kartu produk tanpa gambar TIDAK menampilkan kotak abu-abu placeholder.** Ketiadaan cabang render itulah aturannya. Ini sudah dijaga `tests/kasir/gambar-kartu.test.js`.
3. **Kartu produk gambar gagal dimuat menampilkan keadaan bernama** (bingkai putus-putus, ikon, kata), supaya bisa dibedakan dari "belum difoto".
4. **Nol karakter em-dash** di mana pun teks yang terlihat pengguna.
5. **Warna status hanya untuk keadaan nyata**, tidak untuk dekorasi. Tidak ada titik berwarna di depan item nav atau baris daftar.
6. **Label ada di atas input**, teks galat di bawah input. Placeholder tidak pernah menggantikan label.
7. **Setiap komponen interaktif punya state lengkap**: default, hover, active, disabled, loading, galat. Bukan cuma state berhasil.

---

## Cara File Ini Dipakai

Simpan di repo sebagai `docs/design-tokens.md`. Claude Code membaca file ini, bukan screenshot. Setiap kali ada pertanyaan "warnanya apa" atau "ukuran teksnya berapa" saat implementasi, jawabannya diambil dari sini, bukan diperkirakan ulang dari mockup.

Kalau token berubah, ubah di sini dulu, baru implementasinya menyusul. Jangan sebaliknya.
