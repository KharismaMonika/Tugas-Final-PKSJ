lPada lesson 9 kali ini, akan mensimulasikan tentang cara menggunakan SQL injection dengan menghasilkan output sebuah file hasil injection.

Mari ikuti langkah-langkah berikut:


1. masuk kedalam operating metasploit. ketik masuk kedalam mysql sebagai root. kemudian ketikkan perintah "show databases;" untuk melihat seluruh isi didalam database mysql metasploit. apabila terdapat database owasp10. gunakan database tersebut. kemudian tampilkan tabel yang terdapat didalamnya menggunakan perintah "show tables;"
![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/lesson_9/1.PNG "gambar1")

2. Kemudian kita lihat tabel account dan tabel credit_card dengan cara "desc (nama tabel)"
![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/lesson_9/2.PNG "gambar1")

3. kemudian kita coba untuk menggabungkan antara kolom account dengan kolom credit card menggunakan perintah union
![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/lesson_9/3.PNG "gambar1")

4. apabila sudah, kita akan membuat output file yang berisi hasil union dari kedua tabel diatas dalam bentuk csv menggunakan perintah sebagai berikut:
![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/lesson_9/4.PNG "gambar1")

5. jika sudah berhasil, saatnya untuk mengimplementasikannya didalam website. masuk kedalam halaman user info.
![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/lesson_9/5.PNG "gambar1")

6. pada kolom nama, klik kanan lalu pilih inspect element. ubah ukurannya menjadi 100
![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/lesson_9/6.PNG "gambar1")

7. kemudian masukkan text berikut kedalam kolom nama:
' union select ccid,ccnumber,ccv,expiration,null from credit_cards INTO OUTFILE '/var/www/mutillidae/CCN2.txt' FIELDS TERMINATED BY ',' OPTIONALLY ENCLOSED BY '"' LINES TERMINATED BY '\n' -- 
![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/lesson_9/9.PNG "gambar1")

8.apabila berhasil maka akan muncul halaman sebagai berikut:
![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/lesson_9/10.PNG "gambar1")

9. untuk mengecek keberhasilan dari progress diatas lakukan seperti pada gambar berikut:
![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/lesson_9/11.PNG "gambar1")

Selamat mencoba :)
