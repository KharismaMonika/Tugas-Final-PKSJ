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
   #### Section 7 : Start Web Browser Session to Mutillidae
   1. IP/mutillidae
   #### Section 8 : Go To User Info Page
   1. OWASP Top 10 --> A1 - SQL Injection --> SQLi - Extract Data --> User Info
   
   #### Section 11: SQL Injection: Obtain Userlist (Method #1)
   1. Di page user info masukkan username: ' 1=1-- 
   2. Lihat URL yang dihasilkan. Url yang dihasilkan seperti berikut : http://192.168.149.101/mutillidae/index.php?page=user-info.php&username=%27+or+1%3D1--+&password=&user-info-php-submit-button=View+Account+Details
    Terlihat +or+1%3D1-- 
      Keterangan :
      + : space
      %3D : =
### Lesson 8
### Lesson 9
### Lesson 10
  #### Section 8: Navigate to the User Info Page
    1. Open Browser
    2. Open Mutillidae, dengan alamat http://IP/mutillidae
    3. Go to User Info : OWASP Top 10 --> A1 - SQL Injection --> SQLi - Extract Data --> User Info
    
  #### Section 9: Inject Backdoor into User Info Page
    1. Inspect element textbox name
    2. Mengganti ukuran textbox, dari 20 menjadi 100.
    3. Pada textbox tuliskan string berikut, 
    
    belum bisa
    
### Lesson 11

## Cuckoo
### Instalasi
### Konfigurasi
### Testing

## Snort
### Instalasi
### Konfigurasi
### Testing
