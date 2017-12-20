## Cuckoo
### Instalasi
1. Penulis menggunakan WSL (Windows Subsystem Linux dalam melakukan penginstallan cuckoo) Untuk melakukan pengaktifan WSL lakukan langkah berikut

Ketikan perintah (Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux) pada windows shell dengan run as administrator
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Screenshot_Cuckoo/Windows/1.png "Enable WSL") 

Kemudian perlu mengaktifkan developer mode, dengan membuka windows setting
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Screenshot_Cuckoo/Windows/2.png "Windows setting") 

lalu memilih update and security, lalu for developers, aktifkan developer mode.
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Screenshot_Cuckoo/Windows/3.png "For developer") 

Jika ada perintaan untuk restart silahkan restart

2. Setelah itu, pilih Run / Ctrl + R, ketikan cmd untuk membuka command prompt 
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Screenshot_Cuckoo/Windows/4.png "open command prompt")

3. Ketikan (bash) untuk memulai WSL
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Screenshot_Cuckoo/Windows/5.png "start bash") 
 
Ikuti perintah yang diminta, seperti memasukan user, password

4. Ketikan perintah (sudo apt-get update)
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Screenshot_Cuckoo/Windows/5.png "apt-get update") 

5. Ketikan perintah (sudo apt-get upgrade)
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Screenshot_Cuckoo/Windows/6.png "apt-get upgrade") 

6. Untuk menjalankan cuckoo dibutuhkan beberapa modul yaitu
mongodb, web server (penulis menggunakan xampp di windows), dan mysql sebagai database local.
Modul : - lamp-server^
	   - mysql-server
	   - mongodb
Gunakan perintah (sudo apt-get install <<Nama-Modul?>>)

  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Screenshot_Cuckoo/Windows/8.png "install mongodb") 

7. Jalankan Apache, Mongodb dan mysql dengan perintah (service <<Nama-Service>> start)
Service : - mysql
		- apache2
		- mongodb

8. Selanjutnya buka command prompt yang baru dan masuk ke directory instalasi dari python C:\Python27\Script lalu ketikan perintah (pip install cuckoo)
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Screenshot_Cuckoo/Windows/11.png "install cuckoo") 

9. Selanjutnya ketikan perintah sebagai berikut
(pip install distorm3),(pip install pycrypto), (pip install volatility)
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Screenshot_Cuckoo/Windows/7.png "install pycrypto,distorm,volatility") 

10. Setelah itu ketikan (cuckoo init) untuk memulai. Cuckoo init akan membuat CWD (Cuckoo Working Directory)
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Screenshot_Cuckoo/Windows/12.png "cuckoo init") 

11. CWD dari cuckoo adalah %USERPROFILE%\.cuckoo (C:\Users\<username>\.cuckoo)
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Screenshot_Cuckoo/Windows/13.png "CWD")

12. Kemudian lakukan perubahan pada bebeberapa file pada direktori CWD\conf 
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Screenshot_Cuckoo/Windows/14.png "CWD\conf")

13. Ubah file 

cuckoo.conf
[database]
connection = mysql://<Username>:<password>@127.0.0.1/<database>
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Screenshot_Cuckoo/Windows/15.png "cuckoo.conf")
NOTE: user yang digunakan adalah root , password tidak ada, dan database tujuan adalah cuckoo.

auxillary.conf
[sniffer]
enabled = yes
tcpdump = <PATH to TCPDUMP>
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Screenshot_Cuckoo/Windows/16.png "auxilary")
NOTE: lokasi dari tcpdump dalam gambar adalah di tcpdump = C:\tools\WinDump.exe

virtualbox.conf
[virtualbox]
path = C:\Program Files\Oracle\VirtualBox\VBoxManage.exe
interface = VirtualBox Host-Only Network (Isikan nama INTERFACE)
machines = cuckoo1
[cuckoo1]
label = windows1 (NAMA VIRTUAL MACHINE)
platform = windows
ip = 192.168.56.91 (IP dari VM)
snapshot = snapshot (NAMA SNAPSHOT)

  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Screenshot_Cuckoo/Windows/17.png "vbox.conf")

reporting.conf
[mongodb]
enabled = yes
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Screenshot_Cuckoo/Windows/18.png "reporting")

14. Install Sebuah Virtual Machine baru dengan nama sesuai dengan settingan pada virtualbox.conf, interface Host-Only dan NAT network, matikan dhcp server untuk host only network. Lalu isikan IP secara manual. Dalam hal ini ip dari windows xp yang diinstall adalah 192.168.56.91
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Screenshot_Cuckoo/Windows/19.png "win name")
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Screenshot_Cuckoo/Windows/20.png "adapter 1")
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Screenshot_Cuckoo/Windows/21.png "adapter 2")
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Screenshot_Cuckoo/Windows/22.png "sharefile")
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Screenshot_Cuckoo/Windows/23.png "network")

15. Jalankan virtual machine windows
- Matikan windows Firewall
- Matikan windows update
- konfigurasi IP menjadi statis
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Screenshot_Cuckoo/Windows/24.png "firewall")
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Screenshot_Cuckoo/Windows/25.png "static ip")

16. Install beberapa program seperti, Adobe reader, microsoft word, winrar, serta python pada virtual box windows xp

17. Copykan agent.py dari directory (CWD\agent) pada windows (host) ke virtual machine
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Screenshot_Cuckoo/Windows/26.png "copy agent")

18. Jalankan agent.py yang telah dicopy pada virtual machine. dengan perintah (python agent.py) atau double klik.
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Screenshot_Cuckoo/Windows/27.png "run agent")

19. Pada host machine (windows 10) jalankan perintah (cuckoo web) pada command prompt

### Konfigurasi
### Testing

1. Untuk melakukan testing, malware didownload dari website (https://blog.didierstevens.com/2015/08/28/test-file-pdf-with-embedded-doc-dropping-eicar/) berupa file pdf.

2. Setelah malware didownload. Buka dengan browser (localhost:8000) yang adalah cuckoo web interface dari cuckoo sandbox.
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Screenshot_Cuckoo/Windows/29.png "run agent")

3. Pilih Submit a file, cari file malware yang akan dianalisa.
lalu jalankan. Hasilnya adalah sebagai berikut
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Screenshot_Cuckoo/Windows/28.png "hasil")

4. Hasil analisa menujukan bahwa file pdf tersebut berindikasi malware dengan nilai 1.8
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Screenshot_Cuckoo/Windows/30.png "run agent")
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Screenshot_Cuckoo/Windows/31.png "run agent")
  ![alt text](https://github.com/KharismaMonika/Tugas-Final-PKSJ/blob/master/Screenshot_Cuckoo/Windows/32.png "run agent")
