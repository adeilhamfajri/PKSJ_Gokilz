# Tugas 2 - SQL Injection
##### *PKSJ Kelompok 8:*
- *Muhammad Faiez Ananda (5113100055)*
- *Ade Ilham Fajri (5113100058)*
- *Muhammad Divi Jaya N (5113100066)*

---

## Pendahuluan
Database merupakan tempat penyimpanan data penting yang dibutuhkan untuk menjamin kelancaran aktivitas suatu website. Data penting dan vital yang tersimpan pada database seringkali menjadi target empuk bagi para penyerang.

Salah satu teknik yang umum digunakan untuk menyerang database sebuah website adalah SQL injection atau dikenal juga dengan SQL insertion. SQL injection merupakan sebuah teknik yang digunakan untuk mengeksploitasi celah keamanan pada website dengan cara mengirim malicious SQL query ke database server untuk mengetahui informasi tentang struktur database dari website yang dieksploitasi, yang selanjutnya bisa digunakan untuk mendapatkan data dari database. Setelah data berhasil didapat, penyerang bisa dengan mudah memodifikasi atau bahkan menghapus isi database.

Pada kesempatan ini, kami akan mencoba untuk melakukan serangan SQL injection ke sebuah aplikasi web. Kami akan menyerang website yang menggunakan CMS (Content Management System) Wordpress dengan cara menyerang plugin-plugin WordPress yang vulnerable terhadap serangan SQL injection.

---

## Dasar Teori

### *Ubuntu Server*
Ubuntu Server adalah salah satu varian dari distro Ubuntu yang telah didesain khusus dengan kernel yang telah dikustomisasi untuk bekerja sebagai sistem operasi server. Ubuntu server menyediakan platform yang terintegrasi dengan baik yang akan memudahkan melakukan deploy server dengan fasilitas layanan internet standar seperti e-mail, web, DNS, file serving, hingga manajemen database. Sebagai turunan dari distro Debian, karakter alami Ubuntu server yang diwariskan dari Debian adalah faktor keamanan (security). Ubuntu server tidak membiarkan keberadaan port yang terbuka setelah proses instalasi, dan hanya akan memuat software-software yang esensial dan dibutuhkan untuk membangun sebuah sistem server yang aman.

### *Kali Linux*
Kali Linux adalah salah satu distro Linux tingkat lanjut untuk Penetration Testing dan audit keamanan. Kali Linux tersedia dalam versi 32 bit, 64 bit, dan ARM, serta sejumlah build khusus untuk berbagai macam platform hardware populer lainnya.

### *WordPress 4.6.1*
WordPress adalah sebuah aplikasi open source yang sangat populer digunakan sebagai blog engine. WordPress dibangun dengan bahasa pemrograman PHP dan database MySQL. Selain sebagai blog, WordPress juga mulai digunakan sebagai sebuah CMS (Content Management System) karena kemampuannya untuk dimodifikasi dan disesuaikan dengan kebutuhan penggunanya. WordPress adalah penerus resmi dari b2/cafelog yang dikembangkan oleh Michel Valdrighi. WordPress saat ini menjadi platform CMS bagi beberapa situs web ternama seperti CNN, Reuters, The New York Times, TechCrunch, dan lainnya. Versi terbaru WordPress adalah versi 4.6.1 (dirilis pada 7 September 2016).

### *Plugins*
*1. League Manager 3.9.11 (3.9.11)*

*2. Survey and Poll 1.1*

*3. -*

### *Tools*
*1. sqlmap*

*2. WPscan*

*3. jsql*

---

## Penjelasan Instalasi

### *Instalasi WordPress 4.6.1*
1. Sebelum melakukan instalasi WordPress, hal yang harus kita lakukan adalah melakukan beberapa langkah instal LAMP stack.
2. Pertama-tama kita akan mengisntal Apache Web Server. Masukkan perintah `sudo apt-get update`, kemudian ketik perintah `sudo apt-get install apache2 apache2-utils`.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%202%20-%20SQL%20Injection/Install%20Wordpress/1.PNG?raw=true)
</p>
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%202%20-%20SQL%20Injection/Install%20Wordpress/2.PNG?raw=true)
</p>
3. Tunggu hingga proses selesai dijalankan.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%202%20-%20SQL%20Injection/Install%20Wordpress/3.PNG?raw=true)
</p>
4. Untuk mengaktifkan Apache dapat kita lakukan dengan perintah `sudo systemctl enable apache2`, lalu selanjutnya `sudo systemctl start apache2`.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%202%20-%20SQL%20Injection/Install%20Wordpress/4.PNG?raw=true)
</p>
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%202%20-%20SQL%20Injection/Install%20Wordpress/5.PNG?raw=true)
</p>
5. Lakukan pengecekan Apache2 dengan memasukkan `service apache2 status`.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%202%20-%20SQL%20Injection/Install%20Wordpress/6.PNG?raw=true)
</p>
6. Jika Anda menggunakan Ubuntu Server dan ingin menginstal browser sedserhana, Anda dapat menginstal Lynx dengan cara `sudo apt-get install lynx`.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%202%20-%20SQL%20Injection/Install%20Wordpress/6-1.PNG?raw=true)
</p>
7. Buka Apache dengan Lynx melalui perintah `lynx localhost`. Maka akan muncul halaman seperti di bawah.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%202%20-%20SQL%20Injection/Install%20Wordpress/6-2.PNG?raw=true)
</p>
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%202%20-%20SQL%20Injection/Install%20Wordpress/6-3.PNG?raw=true)
</p>
8. Langkah selanjutnya yang harus dilakukan adalah dengan menginstal MySQL Database.
9. Ketikkan perintah `sudo apt-get install mysql-client mysql-server`.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%202%20-%20SQL%20Injection/Install%20Wordpress/7.PNG?raw=true)
</p>
10. Tunggu beberapa saat hingga instalasi selesai.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%202%20-%20SQL%20Injection/Install%20Wordpress/8.PNG?raw=true)
</p>
11. Saat muncul tampilan seperti di bawah, masukkan password untuk root dari MySQL database.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%202%20-%20SQL%20Injection/Install%20Wordpress/9.PNG?raw=true)
</p>
12. Masukkan ulang password.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%202%20-%20SQL%20Injection/Install%20Wordpress/10.PNG?raw=true)
</p>
13. Untuk memperkuat keamanan database server deployment dapat memasukkan perintah `sudo mysql_secure_installation`.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%202%20-%20SQL%20Injection/Install%20Wordpress/11.PNG?raw=true)
</p>
14 Untuk melihat status MySQL, dapat dilakukan dengan perintah `service mysql status`.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%202%20-%20SQL%20Injection/Install%20Wordpress/12.PNG?raw=true)
</p>
15. Langkah selanjutnya adalah install PHP dan modul-modulnya. Di contoh ini kami menginstall PHP 7.0
16. Masukka perintah `sudo apt-get install php7.0 php7.0-mysql libapache2-mod-php7.0 php7.0-cli php7.0-cgi php7.0-gd`.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%202%20-%20SQL%20Injection/Install%20Wordpress/13.PNG?raw=true)
</p>
17. Tunggulah hingga proses instalasi selesai dijalankan.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%202%20-%20SQL%20Injection/Install%20Wordpress/14.PNG?raw=true)
</p>
18. Buatlah file `info.php` dalam direktori `/var/www/html`.
19. Isilah data info.php seperti di bawah ini.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%202%20-%20SQL%20Injection/Install%20Wordpress/16.PNG?raw=true)
</p>
20. Sekarang buka info.php dengan menggunakan Lynx, masukkan perintah `lynx localhost/info.php`.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%202%20-%20SQL%20Injection/Install%20Wordpress/17.PNG?raw=true)
</p>
21. Maka akan muncul seperti di bawah ini.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%202%20-%20SQL%20Injection/Install%20Wordpress/18.PNG?raw=true)
</p>
22. Sekarang kita perlu mengunduh Wordpress dengan cara `sudo wget -c http://wordpress.org/latest.tar.gz`.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%202%20-%20SQL%20Injection/Install%20Wordpress/19.PNG?raw=true)
</p>
23. Kemudian ekstrak file ` sudo tar -xzvf latest.tar.gz`.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%202%20-%20SQL%20Injection/Install%20Wordpress/20.PNG?raw=true)
</p>
24. Pindahkan semua Wordpress file ke dalam apache root default direktori, `sudo rsync -av wordpress/* /var/www/html/`.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%202%20-%20SQL%20Injection/Install%20Wordpress/21.PNG?raw=true)
</p>
25. Sekarang ubah permission dari direktori website untuk memberikan kepemilikan Wordpress pada web server, `sudo chown -R www-data:www-data /var/www/html/`.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%202%20-%20SQL%20Injection/Install%20Wordpress/22.PNG?raw=true)
</p>
26. Lalu masukkan perintah `sudo chmod -R 755 /var/www/html/`.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%202%20-%20SQL%20Injection/Install%20Wordpress/23.PNG?raw=true)
</p>
27. Sekarang kita akan membuat Database Wordpress, masukkan `mysql -u root -p`.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%202%20-%20SQL%20Injection/Install%20Wordpress/24.PNG?raw=true)
</p>
28. Saat memasuki mysql shell commands, buatlah konfigurasi database yang diperlukan seperti pada contoh d bawah ini.
29. `CREATE DATABASE [nama_database];`
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%202%20-%20SQL%20Injection/Install%20Wordpress/25.PNG?raw=true)
</p>
30. `GRANT ALL PRIVILEGES ON [nama_database].* TO 'nama_user'@'localhost' IDENTIFIED BY 'password';`.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%202%20-%20SQL%20Injection/Install%20Wordpress/26.PNG?raw=true)
</p>
31. `FLUSH PRIVILEGES;`.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%202%20-%20SQL%20Injection/Install%20Wordpress/27.PNG?raw=true)
</p>
32. `EXIT`.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%202%20-%20SQL%20Injection/Install%20Wordpress/28.PNG?raw=true)
</p>
33. Sekarang masuklah ke direktori */var/www/html/* gantilah nama *wp-config-sample.php* menjadi *wp-config.php*.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%202%20-%20SQL%20Injection/Install%20Wordpress/29.PNG?raw=true)
</p>
34. Buka file *wp-config.php* dan ubah pengaturan sesuai yang telah dibuat sebelumnya.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%202%20-%20SQL%20Injection/Install%20Wordpress/30.PNG?raw=true)
</p>
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%202%20-%20SQL%20Injection/Install%20Wordpress/31.PNG?raw=true)
</p>
35. Sekarang restart apache2 dan mysql.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%202%20-%20SQL%20Injection/Install%20Wordpress/32.PNG?raw=true)
</p>
36. Cobalah buka website dengan browser standard di Windows (pastikan sefver tersambung ke jaringan melalui bridge).
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%202%20-%20SQL%20Injection/Install%20Wordpress/33.PNG?raw=true)
</p>

### *Instalasi League Manager 3.9.1.1 (3.9.11)*
1. Pertama-tama masuklah ke direktori */var/www/html/wp-content/plugins/*.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%202%20-%20SQL%20Injection/Install%20Plugin/League%20Manager%203.9.1.1/1.PNG?raw=true)
</p>
2. Setelah itu unduh file league manager versi 3.9.1.1 seperti di bawah ini.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%202%20-%20SQL%20Injection/Install%20Plugin/League%20Manager%203.9.1.1/2.PNG?raw=true)
</p>
3. Unzip file yang telah diunduh melalui perintah `sudo unzip leaguemanager.3.9.1.1.zip`.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%202%20-%20SQL%20Injection/Install%20Plugin/League%20Manager%203.9.1.1/3.PNG?raw=true)
</p>
4. Hapus file .zip agar tidak membebani storage, `sudo rm leaguemanager.3.9.1.1.zip`.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%202%20-%20SQL%20Injection/Install%20Plugin/League%20Manager%203.9.1.1/4.PNG?raw=true)
</p>
5. Untuk mengaktifkan plugin baru, masuklah ke antarmuka admin melalui browser.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%202%20-%20SQL%20Injection/Install%20Plugin/League%20Manager%203.9.1.1/5.PNG?raw=true)
</p>
6. Masuklah ke menu `Plugins` di sebelah kanan.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%202%20-%20SQL%20Injection/Install%20Plugin/League%20Manager%203.9.1.1/6.PNG?raw=true)
</p>
7. Akan tampak halaman seperti di bawah ini.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%202%20-%20SQL%20Injection/Install%20Plugin/League%20Manager%203.9.1.1/7.PNG?raw=true)
8. Aktifkan LeagueManager dengan memilih menu `Activate`.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%202%20-%20SQL%20Injection/Install%20Plugin/League%20Manager%203.9.1.1/8.PNG?raw=true)
</p>
9. Pada bagian atas, pilihlah kolom Activate untuk melihat apakah LeagueManager sudah aktif atau belum.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%202%20-%20SQL%20Injection/Install%20Plugin/League%20Manager%203.9.1.1/9.PNG?raw=true)
</p>
10. Jika sudah muncul seperti di bawah, maka Plugin baru telah aktif.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%202%20-%20SQL%20Injection/Install%20Plugin/League%20Manager%203.9.1.1/10.PNG?raw=true)
</p>

### *Instalasi belum*

### *Instalasi belum juga*

---

## Uji Penetrasi (SQL Injection)

### 1. Tools: WPscan,sqlmap <--> Plugins: League Manager 3.9.1.1 (3.9.11)

---

## Kesimpulan dan Saran

### *Kesimpulan*
- Banyak plugin pada wordpress yang dapat dijadikan sarana/jalur untuk meretas WordPress menggunakan metode SQL Injection.

### *Saran*
- Untuk melakukan penetrasi lebih disarankan menggunakan Kali Linux, karena di dalamnya sudah disertakan tool-tool untuk melakukan penetrasi.
- Pembuatan password untuk sebuah akun harus lebih diperhatikan, yaitu dengan menggunakan kombinasi dari karakter, angka, simbol, dan besar-kecil. Hal ini diperlukan untuk menghindari brute-force attack.
- Untuk menghindari serangan pada sistem lakukanlah update berkala pada sistem yang dimiliki baik itu PHP, MySQL, Apache, WordPress dan Plugin pada Wordpress. Update terbaru pada sistem memungkinkan diperbaikinya suatu celah yang sebelumnya ada pada versi lama.