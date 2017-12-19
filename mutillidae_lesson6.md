Pada lesson 6 kali ini, akan menjelaskan tentang:
A. cara mengetahui isi dari suatu paket (POST) menggunakan burpsuite dan curl
B. cara masuk sebagai user / pengguna tertentu tanpa melakukan login menggunakan cookies.

A. cara mengetahui isi dari suatu paket (POST) menggunakan burpsuite dan curl

1. Buka burpsuite didalam kali linux. kemudian pilih tab proxy -> option . pastikan port 8080 atau localhost pada kolom running tercentang

2. Lalu pada bagian proxy -> interception, pastikan intercept dalam kondisi off.

3. Buka browser, lalu masukkan alamat ip mutillidae: 192.168.56.101/mutillidae. kemudian pilih menu login/register

4. pada kolom nama, masukkan perintah sebagai berikut: "' or 1=1-- " (yang terdapat didalam dua petik. pastikan pada akhir -- terdapat spasi. maksud dari perintah tersebut apabila diterjemahkan dalam bahasa sql adalah sebagai berikut: SELECT * FROM accounts WHERE username='' or 1=1-- ' AND password=''

5. kemudian klik login. setelah itu, kembali pada bupsuite dan masuk kebagian proxy -> history. didalam nya akan terdapat hasil proses login yang telah dilakukan tadi.

6. kemudian kembali ke browser. logout user tadi. apabila sudah logout, buka terminal. kemudian jalankan perintah sebagai berikut: curl -b crack_cookies.txt -c crack_cookies.txt --user-agent "Mozilla/4.0 (compatible; MSIE 5.01; Windows NT 5.0)" --data "username=%27+or+1%3D1--+&password=&login-php-submit-button=Login" --location "http://192.168.56.101/mutillidae/index.php?page=login.php" > login1.txt . Apabila sudah, jalankan perintah grep "Logged In" login1.txt kemudian cat crack_cookies.txt. semua perintah diatas bertujuan untuk mengetahui user yang sedang login pada session sebelumnya.
