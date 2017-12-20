## Snort
Pada tugas ini menggunakan sistem operasi windows
### Instalasi
 1. Snort dapat diunduh di [www.snort.org](https://www.snort.org/)
 2. Download file .exe snort dan rules.
 3. Install snort dari file .exe, lakukan seperti penginstalan aplikasi pada umumnya.
 4. Install snort ini sudah termasuk winPcap
 5. Mengecek versi snort, dapat dilakukan menggunakan CMD, membuka direktory dimana snort diinstal.
 ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Screenshoot%20Snort/install%20done.PNG "Install Snort Berhasil")
 6. Ekstrak rules dan masukkan pada folder rules snort
 7. Ekstrak preprocessor rules dan masukkan pada folder preprocessor rules snort
 
 
### Konfigurasi
Konfigurasi dapat dilakukan dengan mengedit file konfigurasi snort yang bernama snort.conf. File tersebut terdapat pada folder etc.
Konfigurasi ini dilakukan untuk packet capture.
Terdapat beberapa hal yang diperlu disetting dalam file konfigurasi ini, antara lain:
 1. Set the network variables.
 	Dalam hal ini perlu mendefinisikan alamat yang dilindungi, alamat dapat berupa IP address atau subnet. Selain itu perlu mendefinisikan yang termasuk IP eksternal, path rule, preprocessor path, membuat white list dan black list.
 2. Configure the decoder
 	Dalam step ini disetting path dari log directory
 3. Configure the base detection engine
 	Tahap ini dibiarkan saja, settingan defaultnya.
 4. Configure dynamic loaded libraries
 	Tahap ini dilakukan mendefinisikan path dinamic pre processor dan path dinamic engine
 5. Configure preprocessors
 	Tahap ini melakukan comment terhadap konfigurasi preprocessor, uncomment terhadap  port yang akan dideteksi, mengubah nama file white list dan black list serta membuat file white list dan black list
 6. Configure output plugins
 	Tahap ini dibiarkan saja, settingan defaultnya.
 7. Customize your rule set
 	Tahap ini mengubah slash menjadi backslash, karena backslash lebih baik untuk windows.
 8. Customize preprocessor and decoder rule set
 	Tahap ini perlu dilakukan uncomment include.
 9. Customize shared object rule set
 	Tahap ini dibiarkan saja, settingan defaultnya.

Setelah konfigurasi perlu dilakukan validasi konfigurasi dengan perintah, snort -c -C:\Snort\etc\snort.conf -T, perintah ini dijalankan pada CMD sebagai administrator.
### Testing
Tahap ini bertujuan untuk membaca file pcap.
 1. Download file pcap
 2. Buka CMD, buka direktori C:\Snort\bin
 3. Jalankan perintah snort -r directory\file.pcap
 4. Dokumentasi testing :

 