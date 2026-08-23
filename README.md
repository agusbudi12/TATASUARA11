# TATA SUARA SMK NEGERI 1 TANON — Sistem Ujian + Rekap Satu Sesi

Paket ini siap di-upload ke GitHub Pages atau hosting biasa.

## Isi
- `index.html` — halaman siswa
- `rekap.html` — halaman guru untuk melihat rekap
- `firebase-config.js` — konfigurasi Firebase (WAJIB diisi)
- `firestore.rules` — aturan keamanan database
- `.nojekyll` — dukungan GitHub Pages

## Fitur
- 15 soal Tebak Jack & Tebak Pasangan
- Soal diacak
- Timer TOTAL 2 menit untuk seluruh 15 soal
- Android, iPhone, PC/laptop
- Nama + nomor absen
- Kode sesi untuk mengelompokkan hasil
- Nilai otomatis dikirim ke Firebase Firestore
- Halaman guru untuk melihat, mencari, mengurutkan, mencetak, dan mengunduh CSV

## A. Buat Firebase
1. Buka https://console.firebase.google.com/
2. Buat project baru, misalnya `tata-suara-smk-tanon`.
3. Tambahkan Web App (`</>`).
4. Salin konfigurasi Firebase ke `firebase-config.js`.
5. Authentication → Sign-in method → aktifkan:
   - Anonymous
   - Email/Password
6. Firestore Database → Create database.
7. Buat akun guru pada Authentication → Users → Add user.
8. Catat email guru tersebut.
9. Isi `window.TEACHER_EMAIL` dengan email guru.
10. Pada `firestore.rules`, ganti `GANTI_EMAIL_GURU` dengan email guru yang sama.
11. Publish rules tersebut di Firestore → Rules.

## B. Upload ke GitHub Pages
1. Upload semua file di folder ini ke repository.
2. Pastikan `index.html` berada di root repository.
3. Settings → Pages → Deploy from a branch → `main` → `/ (root)` → Save.
4. Halaman siswa: `https://USERNAME.github.io/REPOSITORY/`
5. Halaman guru: `https://USERNAME.github.io/REPOSITORY/rekap.html`

## C. Cara menjalankan satu sesi
Guru menentukan kode, misalnya:
`TATA-SUARA-001`

Semua siswa memasukkan kode sesi yang sama.

Setelah mengerjakan, nilai otomatis masuk ke Firestore. Guru membuka `rekap.html`, login dengan akun guru, lalu memilih kode sesi.

## Catatan keamanan
Jangan menghapus `firestore.rules`. Aturan tersebut membuat siswa hanya bisa menambahkan hasil sebagai pengguna anonim, sedangkan pembacaan hasil dibatasi ke email guru yang ditentukan.
