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

### Exploit : php_cgi_arg_injection, Post Exploitation :

### Exploit : usermap_script, Post Exploitation :

### Exploit : vsftpd_234_backdoor, Post Exploitation : 


## Kesimpulan dan Saran

### *Kesimpulan*
1. Exploit yang paling populer untuk melakukan penetrasi adalah metode Reverse Proxy (Reverse TCP).
2. Malicious code sering disipkan dalam sebuah file untuk melakukan eksploitasi komputer target.

### *Saran*
1. Disarankan untuk menggunakan Kali Linux karena di dalamnya telah tersedia tools untuk melakukan exploit seperti Metasploit, Armitage dll.
2. Disarankan untuk lebih berhati-hati jika akan membuka file yang mencurigakan, karena dalam file-file tersebut sering terdapat malicious code yang dapat membuka celah keamanan komputer.