# Flashcard Mandarin

Aplikasi flash card Mandarin sederhana untuk belajar kosakata dan kalimat sehari-hari. Tanpa build, hanya HTML + JavaScript, dibuat untuk dipakai di HP (Chrome).

## Isi

- `index.html`: aplikasi Kartu Mandarin.
- `firebase-config.js`: tempat menaruh konfigurasi Firebase (login dan penyimpanan akun).
- `tes-suara.html`: halaman kecil untuk mengecek apakah suara Mandarin keluar di perangkat.

## Fitur

- Set kartu: Kata harian (50), Kalimat (20), dan tema Makanan, Keluarga, Belanja, Angka & waktu.
- Ketuk kartu untuk membalik. Suara pengucapan keluar otomatis, ada juga tombol Dengar dan Pelan.
- Penilaian Hafal / Belum hafal. Kartu yang belum hafal muncul lagi di sesi yang sama. Kartu yang hafal muncul lagi setelah 1, 3, 7, lalu 14 hari.
- Tombol **Kembali** membatalkan jawaban terakhir dan membuka lagi kartu sebelumnya (bisa berkali-kali dalam satu sesi).
- Satu sesi berisi 10 kartu (sekitar 10-15 menit per hari), streak harian, dan bar progres.
- Login email + kata sandi (Firebase). Tiap akun punya progres dan streak sendiri, bisa dibuka dari perangkat lain. Tanpa login, aplikasi jalan dalam mode tamu dan progres tersimpan hanya di browser.

## Memasang login Firebase (sekali saja)

1. Buka [Firebase Console](https://console.firebase.google.com), buat proyek baru (Google Analytics boleh dimatikan).
2. **Build > Authentication > Get started > Sign-in method**, aktifkan **Email/Password**.
3. **Authentication > Settings > Authorized domains**, tambahkan alamat tempat aplikasi ini dibuka (untuk GitHub Pages: `NAMAKAMU.github.io`).
4. **Build > Firestore Database > Create database** (mode production, pilih lokasi terdekat), lalu buka tab **Rules** dan tempel aturan ini:

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /users/{userId} {
      allow read, write: if request.auth != null && request.auth.uid == userId;
    }
  }
}
```

5. **Project settings > General > Your apps > Web (</>)**, daftarkan aplikasi web, lalu salin objek `firebaseConfig` ke `firebase-config.js` (ganti `null`).
6. Commit perubahan itu. Config web Firebase memang boleh publik; keamanan data dijaga oleh aturan di langkah 4.

Login tidak berfungsi bila file dibuka langsung dari penyimpanan HP (`file://`). Buka lewat alamat web (misalnya GitHub Pages).

## Target (metode Fire Spiral)

- Putaran 1: hafal ~50 kata dan 20 kalimat dalam 1 bulan; minimum 30 kata dan 10 kalimat dalam 2 minggu, nyaman dipakai di HP sampai mau dibuka tiap hari. Suara pengucapan sudah beres (jalur C: Go).
- Putaran 2: tombol Kembali, tema kata, dan login multi-pengguna (jalur B: Firebase).

### Gap Log

| Putaran | Jalur | Yang dicoba | Hasil nyata | Gap |
|---------|-------|-------------|-------------|-----|
| 1 | C (prototipe lama) | Flash card + suara + streak + animasi | Suara tidak keluar di HP | Pengucapan tidak berfungsi |
| 1 | C (file tes) | Bip dan 你好 di Chrome HP | Keduanya berbunyi | Tidak ada |
| 1 | C (aplikasi baru) | Kartu Mandarin, 50 kata + 20 kalimat | Suara semua keluar | Suara beres |
| 2 | B (Firebase) | Kembali + 4 tema + login | Diuji di browser desktop dengan Firebase tiruan; belum diuji dengan proyek Firebase asli | Menunggu config Firebase dan uji di HP |
