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
1. Pilih bahasa yang anda inginkan
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/Instalasi%20Kali%20Linux/1.JPG?raw=true)


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
1. Pasikanlah server telah diupdate paling baru, jika belum ketikkan perintah 'apt-get update'.
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/SSH%20Server/1.PNG?raw=true)
2. Setelah itu untuk melakukan instalasi SSHGuard, dapat dilakukan dengan perintah 'apt-get install sshguard'.
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/Konfigurasi%20SSHGuard/2.PNG?raw=true)
3. Tunggulah beberapa saat hingga proses instalasi selesai.
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/Konfigurasi%20SSHGuard/3.PNG?raw=true)
4. Lakukan konfigurasi SSHGuard (SSHGuard tidak memiliki file konfigurasi, sehingga harus menggunakan iptables untuk mengatur mekanisme pemblokiran.
5. Masukkan perintah 'iptables -N sshguard'.
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/Konfigurasi%20SSHGuard/4.PNG?raw=true)
6. Kemudian masukkan perintah 'iptables -A INPUT -j sshguard'.
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/Konfigurasi%20SSHGuard/5.PNG?raw=true)
7. Untuk melakukan pemblokiran port (SSH, FTP, IMAP, POP dll) dapat dilakukan dengan memasukkan perintah 'iptables -A INPUT -m multiport -p tcp --destination-ports 21,22,110,143 -j sshguard'.
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/Konfigurasi%20SSHGuard/6.PNG?raw=true)
8. Masukkan perintah 'iptables -F'.
9. Masukkan perintah 'iptables -X'.
10. Masukkan perintah 'iptables -P'.
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/Konfigurasi%20SSHGuard/7.PNG?raw=true)
11. Masukkan juga perintah 'iptables -P INPUT ACCEPT'.
12. Lalu masukkan 'iptables -P FORWARD ACCEPT'.
13. Dan juga perintah 'iptables -P OUTPUT ACCEPT'.
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/Konfigurasi%20SSHGuard/8.PNG?raw=true)
14. Dua perintah terakhir adalah 'iptables -N sshguard'.
15. Dan perintah 'iptables -A INPUT -j sshguard'.
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/Konfigurasi%20SSHGuard/9.PNG?raw=true)
16. SSHGuard berhasil terinstal ddalam server, untuk melakukan pengecekan status SSHGuard, masukkan 'service sshguard status'. Maka akan muncul status SSHGuard (di bawah ini SSHGuard sedang aktif).
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/Konfigurasi%20SSHGuard/10.PNG?raw=true)

### *Konfigurasi SSH Server*
1. Setelah di topik sebelumnya SSH Server telah terinstall di server, sekarang saatnya untuk melakukan konfigurasi pada SSH Server.
2. Pertama-tama bukalah file konfigurasi dengan perintah 'nano /etc/ssh/sshd_config'.
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/Konfigurasi%20SSH%20Server/1.PNG?raw=true)
3. Maka akan tampak isi file sshd_config seperti di bawah ini.
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/Konfigurasi%20SSH%20Server/2.PNG?raw=true)
4. Yang akan kita lakukan adalah melakukan sedikit konfigurasi pada bagian port agar port untuk ssh tidak 22 melainkan 354. Cara yang dapat dilakukan adalah mengcomment port 22 dan menambahkan port 354, seperti pada contoh.
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/Konfigurasi%20SSH%20Server/3.PNG?raw=true)
5. Setelah port berubah, kita harus menjalankan ulang ssh server dengan perintah '/etc/init.d/ssh restart'.
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/Konfigurasi%20SSH%20Server/4.PNG?raw=true)
6. Untuk melakukan percobaan dapat kita lakukan dengan perintah 'ssh root@localhost'.
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/Konfigurasi%20SSH%20Server/5.PNG?raw=true)
7. Jika muncul report seperti di bawah ini, maka port ssh berhasil dialhkan.
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/Konfigurasi%20SSH%20Server/6.PNG?raw=true)
8. Untuk dapat tersambung dapat dilakukan dengan memasukkan 'ssh root@localhost -p 354'.
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/Konfigurasi%20SSH%20Server/7.PNG?raw=true)
9. Dengan memasukkan perintah 'service ssh status', kita dapat melihat keadaan ssh yang ada pada server kita. Tanda 'Active (running)' menandakan bahwa ssh sedang berjalan.
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/Konfigurasi%20SSH%20Server/8.PNG?raw=true)

### *Medusa*
1. Sebelum menggunakan Medusa, pastikan dahulu melakukan 'apt-get update'. Kemudian instal Medusa dengan perintah 'apt-get install medusa'. Ternyata Kali Linux juga telah menyediakan Medusa sebagai brute-force penetration tool.
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/Medusa%20-%20Penetrasi%202/1.PNG?raw=true)
2. Langkah selanjutnya adalah melakukan penetrasi ke Ubuntu Server dengan perintah 'medusa -h [IP_ADDRESS] -u [USERNAME] -P [FILE] -M ssh'. Contohnya seperti di bawah ini.
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/Medusa%20-%20Penetrasi%202/2.PNG?raw=true)
3. Hasil yang didapat adalah 'failed to connect', hal ini dikarenakan konfigurasi SSH Server telah kita ubah port defaulnya menjadi 354.
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/Medusa%20-%20Penetrasi%202/3.PNG?raw=true)
4. Sekarang kita kembalikan konfigurasi port menjadi 22 dan pastikan SSHGuard telah berjalan.
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/Medusa%20-%20Penetrasi%202/4.PNG?raw=true)
5. Masukkan perintah penetrasi seperti dibawah.
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/Medusa%20-%20Penetrasi%202/5.PNG?raw=true)
6. Hasil yang kita dapat adalah brute-force attack yang kita lakukan hanya berjalan beberapa iterasi sebelum kemudian SSHGuard pada server memblokir akses yang kita lakukan.
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/Medusa%20-%20Penetrasi%202/6%20kedua.PNG?raw=true)

### *THC-Hydra*
1. Sekarang akan kita coba lakukan kembali penetrasi pada Ubuntu Server menggunakan THC-Hydra.
2. Kita siapkan dahulu sebuah file yang berisi daftar password yang akan di brute-force, disini kami menamai filenya pass.txt.
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/Hydra%20-%20Penetrasi%202/100.PNG?raw=truerue)
3. Penetrasi dapat dilakukan dengan perintah 'hydra -l [username] -P [FILE] IP_DESTINATION ssh'. Contohnya seperti: 'hydra -l pksjserver -P pass.txt 10.151.43.177 ssh'.
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/Hydra%20-%20Penetrasi%202/1.PNG?raw=true)
4. Koneksi ke Ubuntu Server di refused karena port ssh 22 (dafault) telah berganti menjadi 354.
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/Hydra%20-%20Penetrasi%202/2.PNG?raw=true)
5. Sekarang konfigurasi port telah kita kembalikan menjadi 22 (default). Kita coba lakukan lagi penetrasi. Hasilnya adalah koneksi Timeout (koneksi ke server memakan waktu yang terlalu lama karena IP kita diblok oleh server).
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/Hydra%20-%20Penetrasi%202/3.PNG?raw=true)
6. Sekarang mari kita coba lihat log file di sisi Ubuntu Server dengan memasukkan perintah 'nano /var/log/auth.log'.
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/Hydra%20-%20Penetrasi%202/4.PNG?raw=true)
7. Berikut ini salah satu baris yang menunjukkan bahwa IP Kali Linux sedang terblokir dalam waktu 945 detik.
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%201%20-%20Uji%20Penetrasi/Hydra%20-%20Penetrasi%202/5.PNG?raw=true)

## Kesimpulan dan Saran

### *Kesimpulan*

### *Saran*