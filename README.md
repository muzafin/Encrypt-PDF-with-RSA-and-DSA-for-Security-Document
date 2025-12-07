🔒 Encrypt PDF with RSA and DSA for Security Document
Sistem Enkripsi Asimetris (RSA) dan Tanda Tangan Digital (DSA) untuk Dokumen Rahasia
Proyek ini adalah aplikasi desktop berbasis Python menggunakan library Tkinter untuk antarmuka grafis dan PyCryptodome untuk operasi kriptografi. Tujuannya adalah menyediakan mekanisme keamanan ganda pada dokumen (khususnya PDF):

Kerahasiaan Data (Confidentiality) melalui Enkripsi Hybrid (RSA + AES).

Keaslian & Integritas Data (Authenticity & Integrity) melalui Tanda Tangan Digital DSA.

🚀 Fitur Utama Aplikasi
Aplikasi dibagi menjadi tiga tab fungsional untuk memudahkan alur kerja kriptografi:

1. Buat Kunci (RSA & DSA)
Generasi Kunci Ganda: Membuat pasangan kunci RSA-2048 (Privat/Publik) dan DSA-2048 (Privat/Publik) secara bersamaan untuk satu pengguna.

Penggunaan Kunci:

RSA Privat: Untuk Dekripsi data (Penerima).

RSA Publik: Untuk Enkripsi data (Pengirim).

DSA Privat: Untuk Menandatangani (Signing) dokumen (Pengirim).

DSA Publik: Untuk Verifikasi tanda tangan (Penerima).

2. Kirim (Encrypt RSA & Sign DSA)
Ini adalah alur kerja Pengirim. Dokumen akan diproses dalam dua langkah:

Tanda Tangan Digital (DSA): Dokumen di-hash menggunakan SHA256, lalu di-sign menggunakan DSA Private Key milik Pengirim.

Enkripsi Hybrid (RSA + AES):

Dokumen dienkripsi menggunakan session key AES-128 (Mode EAX).

Session key AES dienkripsi menggunakan RSA Public Key milik Penerima.

Output: Menghasilkan 3 file terpisah untuk dikirim: File Terenkripsi (enc_...), File Kunci Sesi (key_...), dan File Tanda Tangan (sig_...).

3. Terima (Decrypt RSA & Verify DSA)
Ini adalah alur kerja Penerima. Dokumen akan diproses dalam dua langkah terbalik:

Dekripsi Hybrid (RSA + AES):

RSA Private Key Penerima digunakan untuk mendekripsi session key AES yang terenkripsi.

Session key AES digunakan untuk mendekripsi dokumen terenkripsi.

Verifikasi Tanda Tangan (DSA):

Dokumen hasil dekripsi di-hash ulang dengan SHA256.

DSA Public Key milik Pengirim digunakan untuk memverifikasi tanda tangan terhadap hash baru.

Status: Memberikan notifikasi visual (Hijau/Merah) untuk menunjukkan apakah dokumen Valid dan Terdekripsi atau Tanda Tangan Tidak Valid/Rusak.

🛠️ Persyaratan dan Instalasi
Proyek ini membutuhkan Python 3.x dan beberapa library eksternal:

Persyaratan
- Python 3.x
- Tkinter (Umumnya sudah terinstal dengan Python)
- PyCryptodome
