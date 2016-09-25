# Tugas 1 - Uji Penetrasi
##### *PKSJ Kelompok 8:*
- *Muhammad Faiez Ananda (5113100055)*
- *Ade Ilham Fajri (5113100058)*
- *Muhammad Divi Jaya N (5113100066)*

## Pendahuluan
Dalam dunia komunikasi data dan perkembangan teknologi informasi yang senantiasa berubah, keamanan sistem dan jaringan merupakan suatu isu yang sangat penting. Perlu kita sadari bahwa untuk mencapai suatu keamanan itu adalah suatu hal yang sangat mustahil. Namun kita bisa melakukan pencagahan untuk mengurangi gangguan tersebut.

Salah satu metode pengamanan sistem yang umum diketahui banyak orang adalah password. Tanpa disadari password mempunyai peranan penting dalam mengamankan informasi-informasi yang sifatnya pribadi (confidential). Tetapi banyak dari para pengguna password yang membuat password secara sembarangan tanpa mengetahui kebijakan pengamanan (password policy) dan bagaimana membuat password yang kuat (strong password). Mereka tidak sadar dengan bahayanya para ‘penyerang’ (attacker) yang dapat mencuri atau mengacak-acak informasi tersebut.

Oleh karena itu, disini kami akan mencoba untuk melakukan penetrasi ke server menggunakan teknik brute force untuk mendapatkan password. Dan kami juga mencontohkan couter measure dari serangan brute force tersebut.

## Dasar Teori

### *Ubuntu Server*
	Ubuntu Server adalah salah satu varian dari distro Ubuntu yang telah didesain khusus dengan kernel yang telah dikustomisasi untuk bekerja sebagai sistem operasi server. Ubuntu server menyediakan platform yang terintegrasi dengan baik yang akan memudahkan melakukan deploy server dengan fasilitas layanan internet standar seperti e-mail, web, DNS, file serving, hingga manajemen database. Sebagai turunan dari distro Debian, karakter alami Ubuntu server yang diwariskan dari Debian adalah faktor keamanan (security). Ubuntu server tidak membiarkan keberadaan port yang terbuka setelah proses instalasi, dan hanya akan memuat software-software yang esensial dan dibutuhkan untuk membangun sebuah sistem server yang aman.

### *Kali Linux*
	Kali Linux adalah salah satu distro Linux tingkat lanjut untuk Penetration Testing dan audit keamanan. Kali Linux tersedia dalam versi 32 bit, 64 bit, dan ARM, serta sejumlah build khusus untuk berbagai macam platform hardware populer lainnya.

### *THC-Hydra*
	THC Hydra adalah sebuah password cracking tools yang dapat melakukan dictionary attack terhadap lebih dari lima puluh protokol jaringan dengan sangat cepat, lebih cepat bila dibandingkan dengan password cracking tools yang lain. Menambahkan modul dan penambahan fitur dapat dengan mudah dilakukan. THC Hydra tersedia untuk Windows, Linux, Free BSD, Solaris, dan OS X.

### *Medusa*
	Medusa juga merupakan sebuah password cracking tools seperti THC Hydra. Attacker bisa memilih secara fleksibel apakah akan melakukan cracking terhadap password, host, atau username dan password sekaligus ketika melakukan attack. Medusa juga bisa melakukan parallel attack. Parallel attack dapat dilakukan dengan menyediakan daftar username bersamaan dengan daftar password.

### *SSHGuard*
	SSHGuard adalah sebuah program yang memonitor layanan yang sedang berjalan dari file-file log. SSHGuard melindungi host dari serangan brute force terhadap SSH dan layanan lainnya. Ketika pada file log sistem terdeteksi bahwa seseorang melakukan serangan brute force, SSHGuard memblokir alamat IP dari orang tersebut menggunakan salah satu dari beberapa backend firewall, termasuk iptables, ipwf, dan pf.

## Uji Penetrasi 1

### *Instalasi Ubuntu Server*
1. Buka Virtual Box atau software virtualisasi sejenis, disini kami menggunakan Virtual Box.
2. Setelah halaman utama Virtual Box terbuka, pilih menu "Baru" di pojok kiri atas (icon menu adalah lingkaran biru bergerigi).
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/Ubuntu%20Server/1.PNG?raw=true)
3. Pada langkah selanjutnya, masukkan nama untuk mesin virtual Anda (disini kami memberikan nama XenialServer, yang mengacu pada versi ubuntu 16.04 Xenial Xerus).
4. Pilihlah tipe Sistem Operasi yang akan dibuat (kami menggunakan Linux) dan pilihlah versi dari Sistem Operasi (kami menggunakan Ubuntu 64-bit).
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/Ubuntu%20Server/2.PNG?raw=true)
5. Alokasikan memori (RAM) yang akan digunakan untuk mesin virtual yang akan dibuat (kami mengalokasikan 2048 MB).
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/Ubuntu%20Server/3.PNG?raw=true)
6. Lanjut ke langkah selanjutnya, jika Anda belum pernah mengalokasikan harddisk untuk mesin virtual sebelumnya, pilihlah pilihan "Buat hard disk virtual untuk mesin baru".
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/Ubuntu%20Server/4.PNG?raw=true)
7. Pilihlah VDI (VirtualBox Disk Image) dan pilih lanjut.
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/Ubuntu%20Server/5.PNG?raw=true)
8. Pilihlah sifat alokasinya antara tetap atau dinamik (kami memilih alokasi dinamik untuk mempercepat waktu instalasi).
9. Alokasikan ukuran hard disk virtual (kami memilih default atau tidak melakukan perubahan), kemudian pilih perintah "Buat".
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/Ubuntu%20Server/6.PNG?raw=true)
10. Masuk ke menu Pengaturan.
11. Pilih menu Penyimpanan di bagian kiri.
12. Lakukan setting CD dengan memilih ikon bergambar disk dengan tanda plus, lalu pilihlah file .ISO dari Ubuntu Server.
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/Ubuntu%20Server/1000.PNG?raw=true)
13. Pilihlah menu Sistem, pastikan Urutan Boot Optik berada pada urutan teratas.
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/Ubuntu%20Server/1001.PNG?raw=true)
14. Jalankan UbuntuServer dan ikuti langkah-langkah berikutnya sesuai dengan pengaturan default yang sudah ada.
15. Pilih English.
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/Ubuntu%20Server/7.PNG?raw=true)
16. Pilih 'Install Ubuntu Server'.
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/Ubuntu%20Server/8.PNG?raw=true)
17. Pilihan bahasa pilihlah English.
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/Ubuntu%20Server/9.PNG?raw=true)
18. Zona waktu pilihlah 'Singapore' sesuai waktu di Indonesia.
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/Ubuntu%20Server/10.PNG?raw=true)
19. Untuk keyboard layout pilihlah 'No'.
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/Ubuntu%20Server/11.PNG?raw=true)
20. Kemudian pilihlah 'English (US)'.
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/Ubuntu%20Server/11-5.PNG?raw=true)
21. Masukkan Full Name, username dan password pada kolom-kolom yang muncul berikutnya.
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/Ubuntu%20Server/13.PNG?raw=true)
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/Ubuntu%20Server/14.PNG?raw=true)
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/Ubuntu%20Server/15.PNG?raw=true)
22. Pilih 'Yes' untuk konfirmasi Zona waktu yang telah dipilih.
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/Ubuntu%20Server/17.PNG?raw=true)
23. Pilihlah 'Guided - use entire disk and set up LVM'.
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/Ubuntu%20Server/18.PNG?raw=true)
24. Pilihlah sesuai pilihan disk partition yang muncul di layar.
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/Ubuntu%20Server/19.PNG?raw=true)
25. Pilihlah 'Yes' untuk konfirmasi.
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/Ubuntu%20Server/20.PNG?raw=true)
26. Pilih 'Continue'.
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/Ubuntu%20Server/21.PNG?raw=true)
27. Pilih 'Yes' untuk melanjutkan.
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/Ubuntu%20Server/22.PNG?raw=true)
28. Tunggulah proses yang sedang berjalan.
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/Ubuntu%20Server/23.PNG?raw=true)
29. Jika Anda tidak menggunakan pengaturan proxy, kosongkan dan pilihlah 'Continue'.
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/Ubuntu%20Server/24.PNG?raw=true)
30. Pilihlah 'No automatic updates'.
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/Ubuntu%20Server/25.PNG?raw=true)
31. Pilihlah 'Continue'.
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/Ubuntu%20Server/26.PNG?raw=true)
32. Pilih 'Yes' untuk instalasi GRUB loader.
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/Ubuntu%20Server/27.PNG?raw=true)
33. Pilih 'Continue'.
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/Ubuntu%20Server/28.PNG?raw=true)
34. Setelah semua proses selesai, Anda akan masuk ke dalam Ubuntu Server. Masukkan username dan password untuk dapat menjalankan Ubuntu Server.
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/Ubuntu%20Server/29.PNG?raw=true)

### *Instalasi OS Penetrasi (Kali Linux)*

### *Instalasi SSH Server*
1. Pastikan Anda telah masuk ke dalam Ubuntu Server
2. Masukkan perintah untuk update OS terlebih dahulu dengan mengetikkan 'sudo apt-get update'
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/SSH%20Server/1.PNG?raw=true)
3. Untuk melakukan install SSH Server tuliskan perintah 'sudo apt-get install ssh'.
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/SSH%20Server/2.PNG?raw=true)
4. Tunggulah beberapa saat hingga proses instalasi selesai dilakukan.
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/SSH%20Server/101.PNG?raw=true)
5. Jalankan SSH Server dengan mengetikkan perintah 'sudo service ssh start'.
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/SSH%20Server/3.PNG?raw=true)
6. Untuk melakukan pengecekan apakah SSH Server telah berjalan, ketikkan perintah 'sudo service ssh status'.
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/SSH%20Server/4.PNG?raw=true)
7. Jika Anda menginginkan SSH Server berjalan otomatis setelah reboot, masukkan perintah 'sudo systemctl enable ssh'.
8. SSH Server selesai di install.

### *Medusa*

### *THC-Hydra*

## Uji Penetrasi 2

### *Konfigurasi SSHGuard*

### *Konfigurasi SSH Server*

### *Medusa*

### *THC-Hydra*

## Kesimpulan dan Saran

### *Kesimpulan*

### *Saran*