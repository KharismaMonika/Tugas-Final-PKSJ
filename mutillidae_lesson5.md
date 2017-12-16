### LESSON 5
1. Membuka halaman mutillidae dengan memasukan URL sebagai berikut [IP_metasploitable]/mutillidae seperti pada gambar
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_5/home.png "Mutillidae Homepage") 
pada gambar 192.168.56.101/mutillidae

2. Pilih halaman login dengan menekan tulisan login di sebelah kiri atas dari halaman mutillidae
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_5/login.png "Mutillidae Login page")

3. Isikan (') / petik satu / single_quote pada kolom name seperti pada gambar
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_5/single_quote_test.png "Mutillidae single quote test")
Lalu tekan enter

4. Dapat dilihat dibagian atas muncul error log yang memberikan indikasi mengenai format dari dari perintah SQL untuk login
yaitu SELECT * FROM accounts WHERE username=''' AND password=''
dimana (') menyebabkan error pada eksekusi command sql.
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_5/single_quote_test_report.png "Mutillidae single quote test report")

5. Dengan demikian maka dapat dilakukan login dengan mem-bypass password menggunakan sql injection dengan mengetikan perintah
sebagai berikut "'or 1=1-- " (petik 2 tidak perlu diketik juga)
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_5/bypass_password_username_test.png "Mutillidae bypass login")
Perhatikan untuk memberikan spasi di akhir dari tanda (-- ).
Lalu tekan enter.

6. Hasilnya
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_5/bypass_password_username_test_report.png "Mutillidae login as admin")
Perhatikan frasa logged in as Admin:admin

7. Selanjutnya mencoba injeksi sql pada kolom password. Masukan samurai pada kolom nama, kemudian tanda (') pada kolom password
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_5/9.1.png "Injeksi pada kolom password")

8. Untuk menampilkan isi password, klik kanan pada kolom pengisian password, pilih inspect element. Ubah type=password menjadi type=text seperti pada gambar
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_5/9.2.png "Menampilkan isi password")

9. Setelah di tekan login kita dapat melihat hasilnya adalah sebagai berikut, yang menyatakan bahwa (') terdaftar sebagai simbol yang digunakan dalam perintah sql yang "dapat merusak" sebuah query pada web yang rentan terhadap sql injection
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_5/9.3.png "error report single quotes on password")

10. Selanjutnya mencoba injeksi sql pada kolom password untuk login kembali. Masukan samurai pada kolom nama, kemudian tanda "'or 1=1-- " (petik 2 tidak perlu diketik juga) pada kolom password. (jangan lupa spasi setelah '-- ' )
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_5/10.1.png "Injeksi pada kolom password")

11. Untuk menampilkan isi password, klik kanan pada kolom pengisian password, pilih inspect element. Ubah type=password menjadi type=text seperti pada gambar
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_5/10.2.png "Menampilkan isi password")

12. Setelah di tekan login kita dapat melihat hasilnya adalah sebagai berikut
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_5/10.3.png "success login as admin")
Meskipun name yang dimasukan adalah samurai, tetapi karena struktur query yang ada, maka dengan menginjeksikan "'or 1=1-- " / selalu benar, maka record yang diambil adalah yang paling atas yaitu record admin.
Setelah itu lakukan logout

13. Selanjutnya mencoba injeksi sql pada kolom password untuk login kembali untuk masuk sebagai user samurai. Masukan samurai pada kolom nama, kemudian klik kanan, pilih inspect element, ubay maxlength=20 menjadi maxlength=50 dan type=password menjadi type text
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_5/11.1.png "Inspect element")

  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_5/11.2.png "Mengubah maxlength dan type")

14. Masukan "' or (1=1 and username='samurai')-- " pada kolom password, perhatikan untuk memberikan spasi di akhir dari tanda '-- '
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_5/11.3.png "Perintah sql injection")

15. Setelah di tekan login kita dapat melihat hasilnya adalah sebagai berikut
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_5/11.4.png "success login as samurai")

16. Selanjutnya kita akan mencoba perintah sql pada terminal. Jalankan perintah berikut pada terminal di metasploitable.
Ketikan perintah sudo mysql atau mysql -u [nama_user] -p [password]
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_5/12.1.png "success login as root in mysql")
Lalu tekan enter.

17. Ketikan 'show databases;' kemudian tekan enter. Perintah berikut adalah untuk menampilkan semua database yang ada.
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_5/12.2.png "show database")

18. Ketikan perintah 'use owasp10' untuk memilih database yang akan diakses / active database. (tidak perlu memberikan tanda (;) pada akhir perintah.
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_5/12.3.png "change database")

19. Masukan perintah 'show tables;' untuk menampilkan list tabel yang ada pada database aktif
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_5/12.5.png "show table")

20. Masukan perintah 'desc accounts;' untuk menampilkan format dan struktur dari tabel accounts
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_5/12.6.png "desc accounts")

21. Masukan perintah 'select * from accounts;' untuk menampilkan isi dari tabel accounts
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_5/12.7.png "query seluruh tabel")

22. Masukan perintah (select * from accounts where username='' and password='';) untuk menampilkan record dengan username='' dan password=''. 
Kemudian perintah (select * from accounts where username='samurai' and password='samurai';) untuk menampilkan record dengan username=samurai dan password=samurai.
Kemudian perintah (select * from accounts where username='samurai' and password='wrongpassword';) untuk menampilkan record dengan username=samurai dan password=wrongpassword.
Kemudian perintah (select * from accounts where username='samurai';-- and password='samurai';) untuk menampilkan record dengan username=samurai dan mengcomment / mengabaikan perintah selanjutnya. Untuk lebih jelas dapat dilihat pada gambar berikut ini.
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_5/12.8.png "query 4 macam")

23. Mencoba hasil single quote test / memasukan (') pada kolom username. Dapat dilihat bahwa input (') merusak query sehingga tida menghasilkan apapun kecuali ditambahkan dengan (';)
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_5/12.9.png "hasil query (')")

24. Mencoba hasil query (select * from accounts where username = '' or 1=1; --   and password = '';). Dapat dilihat bahwa input ini mengembalikan hasil seluruh record pada tabel karena perintah always true.
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_5/12.10.png "hasil query always true")

25. Mencoba hasil query (select * from accounts where username = 'samurai' and password = '' or 1=1; -- ';). Dapat dilihat bahwa input ini mengembalikan hasil seluruh record pada tabel karena perintah always true dan struktur perintah dari mutilidae.
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_5/12.11.png "hasil query always true")

26. Mencoba hasil query (select * from accounts where username = 'samurai' and password = '' or (1=1 and username = 'samurai'); -- ';).Dapat dilihat bahwa input ini mengembalikan hasil berupa record dengan username adalah samurai tanpa perlu mengetahui password.
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_5/12.12.png "hasil query user samurai")


