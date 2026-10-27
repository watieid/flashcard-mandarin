# Flashcard Mandarin

Aplikasi flash card Mandarin sederhana untuk belajar kosakata dan kalimat sehari-hari. Satu file HTML, tanpa instalasi, dibuat untuk dipakai sendiri di HP (Chrome).

## Isi

- `index.html`: aplikasi Kartu Mandarin.
- `tes-suara.html`: halaman kecil untuk mengecek apakah suara Mandarin keluar di perangkat.

## Fitur

- 50 kata dan 20 kalimat sehari-hari, lengkap dengan hanzi, pinyin, dan arti dalam bahasa Indonesia.
- Ketuk kartu untuk membalik. Suara pengucapan keluar otomatis, ada juga tombol Dengar dan Dengar pelan.
- Penilaian Hafal / Belum hafal. Kartu yang belum hafal muncul lagi di sesi yang sama. Kartu yang hafal muncul lagi setelah 1, 3, 7, lalu 14 hari.
- Satu sesi berisi 10 kartu (sekitar 10-15 menit per hari).
- Streak harian dan bar progres dengan penanda minimum (30 kata, 10 kalimat).
- Progres tersimpan di browser (localStorage). Menghapus data Chrome akan mengulang progres dari nol.

## Cara pakai

1. Unduh `index.html`.
2. Buka di Chrome (di HP: lewat Files / Downloads, pilih Chrome).
3. Naikkan volume media, lalu ketuk kartu.

Suara memakai Web Speech API bawaan browser (`zh-CN`). Kalau suara tidak keluar, buka `tes-suara.html` untuk mendiagnosisnya.

## Target (metode Fire Spiral)

- Target: dalam 1 bulan hafal sekitar 50 kata dan 20 kalimat sehari-hari.
- Minimum success: dalam 2 minggu hafal 30 kata dan 10 kalimat, dan nyaman dipakai di HP sampai mau dibuka tiap hari.

### Gap Log putaran 1

| Jalur | Yang dicoba | Hasil nyata | Gap terhadap target |
|-------|-------------|-------------|---------------------|
| C (prototipe lama) | Flash card + suara + streak + animasi | Suara tidak keluar di HP | Pengucapan tidak berfungsi |
| C (file tes) | Bip dan 你好 di Chrome HP | Keduanya berbunyi | Tidak ada |
| C (aplikasi baru) | Kartu Mandarin, 50 kata + 20 kalimat | Suara semua keluar | Suara beres; kenyamanan harian belum dinilai |

Keputusan: jalur C **Go**. Putaran berikutnya layak dibuka bila ada bagian layar HP yang kurang nyaman, kosakata ingin ditambah (tema makanan, belanja, keluarga), atau progres perlu dicadangkan.
