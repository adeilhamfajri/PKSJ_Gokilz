# Tugas 2 - SQL Injection
##### *PKSJ Kelompok 8:*
- *Muhammad Faiez Ananda (5113100055)*
- *Ade Ilham Fajri (5113100058)*
- *Muhammad Divi Jaya N (5113100066)*

---

## Pendahuluan

---

## Dasar Teori

### *Ubuntu Server*
Ubuntu Server adalah salah satu varian dari distro Ubuntu yang telah didesain khusus dengan kernel yang telah dikustomisasi untuk bekerja sebagai sistem operasi server. Ubuntu server menyediakan platform yang terintegrasi dengan baik yang akan memudahkan melakukan deploy server dengan fasilitas layanan internet standar seperti e-mail, web, DNS, file serving, hingga manajemen database. Sebagai turunan dari distro Debian, karakter alami Ubuntu server yang diwariskan dari Debian adalah faktor keamanan (security). Ubuntu server tidak membiarkan keberadaan port yang terbuka setelah proses instalasi, dan hanya akan memuat software-software yang esensial dan dibutuhkan untuk membangun sebuah sistem server yang aman.

### *Kali Linux*
Kali Linux adalah salah satu distro Linux tingkat lanjut untuk Penetration Testing dan audit keamanan. Kali Linux tersedia dalam versi 32 bit, 64 bit, dan ARM, serta sejumlah build khusus untuk berbagai macam platform hardware populer lainnya.

### *Wordpress 4.6.1*

### *Plugins*
*1. League Manager 3.9.11 (3.9.11)*

*2. -*

*3. -*

### *Tools*
*1. sqlmap*

*2. WPscan*

*3. -*

---

## Penjelasan Instalasi

### *Instalasi Wordpress 4.6.1*
1. Buka Virtual Box atau software virtualisasi sejenis, disini kami menggunakan Virtual Box.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/Ubuntu%20Server/1.PNG?raw=true)
</p>

### *Instalasi League Manager 3.9.1.1 (3.9.11)*

### *Instalasi belum*

### *Instalasi belum juga*

---

## Uji Penetrasi (SQL Injection)

### 1. Tools: WPscan,sqlmap <--> Plugins: League Manager 3.9.1.1 (3.9.11)

---

## Kesimpulan dan Saran

### *Kesimpulan*
- Banyak plugin pada wordpress yang dapat dijadikan sarana/jalur untuk meretas wordpress menggunakan metode SQL Injection.

### *Saran*
- Untuk melakukan penetrasi lebih disarankan menggunakan Kali Linux, karena di dalamnya sudah disertakan tool-tool untuk melakukan penetrasi.
- Pembuatan password untuk sebuah akun harus lebih diperhatikan, yaitu dengan menggunakan kombinasi dari karakter, angka, simbol, dan besar-kecil. Hal ini diperlukan untuk menghindari brute-force attack.
- Untuk menghindari serangan pada sistem lakukanlah update berkala pada sistem yang dimiliki baik itu PHP, MySQL, Apache, Wordpress dan Plugin pada Wordpress. Update terbaru pada sistem memungkinkan diperbaikinya suatu celah yang sebelumnya ada pada versi lama.