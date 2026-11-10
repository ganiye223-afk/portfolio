# Portfolio

Website portfolio berbahasa Indonesia dengan halaman publik, detail studi kasus, formulir kontak yang tersimpan di MySQL, serta panel admin untuk mengelola proyek dan membaca pesan.

## Teknologi

- Laravel 13 dan PHP 8.3+
- MySQL (Laragon)
- Blade, Vite, dan CSS responsif

## Menjalankan di Laragon

1. Nyalakan **Apache** dan **MySQL** dari Laragon.
2. Buat database MySQL bernama `portofolio` melalui HeidiSQL atau Laragon.
3. Pastikan pengaturan `DB_*` di `.env` sesuai dengan MySQL lokal Anda. Laragon biasanya memakai `root` tanpa kata sandi.
4. Isi identitas situs (`PORTFOLIO_*`) dan atur `ADMIN_EMAIL` serta `ADMIN_PASSWORD` dengan kata sandi kuat di `.env`. Tidak ada password admin bawaan.
5. Jalankan perintah berikut dari folder proyek:

   ```powershell
   composer install
   Copy-Item .env.example .env
   php artisan key:generate
   npm.cmd install
   php artisan migrate --seed
   npm.cmd run build
   php artisan serve
   ```

   Jika `.env` sudah tersedia, jangan salin ulang `.env.example` agar kunci aplikasi yang ada tidak tertimpa.
6. Buka URL yang ditampilkan `php artisan serve` (biasanya `http://127.0.0.1:8000`) atau arahkan virtual host Laragon ke folder `public`.
7. Masuk ke `/admin/login` menggunakan email dan password admin dari `.env`.

Seeder membuat beberapa proyek contoh dan akun admin **hanya jika** `ADMIN_EMAIL` dan `ADMIN_PASSWORD` sudah diatur. Ganti atau hapus konten contoh melalui panel admin.

## Fitur

- Portfolio responsif dengan bagian karya, profil, dan kontak.
- Detail karya publik dan pilihan untuk menyimpan karya sebagai draft.
- Panel admin terproteksi untuk membuat, mengedit, mengurutkan, memublikasikan, dan menghapus karya.
- Pesan kontak tervalidasi, dibatasi laju pengiriman, disimpan di database, dan bisa ditandai sudah dibaca.
- Autentikasi admin memakai sesi Laravel; password di-hash, formulir memakai CSRF, dan akun non-admin tidak dapat mengakses panel.

## Validasi

```powershell
php artisan test
npm.cmd run build
```
