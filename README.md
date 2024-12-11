# Rangkuman-Jarkom-Lanjut
Nama 	: Hemiltin Adilah
Nim	: 20210801147
Prodi	: Teknik Informatika

Pengenalan WAN dan Router
•	Wide Area Network (WAN) adalah sebuah jaringan komunikasi data yang menghubungkan user-user yang ada di jaringan yang berada di suatu area geografik yang besar.
•	Router adalah perangkat jaringan yang digunakan untuk menghubungkan beberapa jaringan komputer, baik jaringan lokal (LAN) maupun jaringan yang lebih luas seperti WAN (Wide Area Network). Router bertugas mengatur lalu lintas data antara jaringan-jaringan tersebut sehingga informasi dapat dikirim dari satu perangkat ke perangkat lain dengan efisien.
Konfigurasi awal router
1.	Persiapan 
•	Sambungkan router ke sumber daya listrik.
•	 Hubungkan perangkat (PC/laptop) ke router melalui kabel Ethernet atau Wi-Fi. 
2.	Akses Router 
•	Buka browser dan masukkan alamat IP default router (biasanya 192.168.1.1 atau 192.168.0.1).
•	Login dengan username dan password default (tertera di perangkat atau manual).
3.	Pengaturan Dasar 
•	Atur alamat IP router untuk jaringan lokal (LAN). 
•	Konfigurasikan NAT jika diperlukan untuk akses internet. 
4.	Pengaturan Internet (WAN) 
•	Masukkan informasi koneksi internet (IP statis, DHCP, atau PPPoE) sesuai penyedia layanan. 
5.	Keamanan 
•	Ubah username dan password default. 
•	Aktifkan firewall dan enkripsi Wi-Fi (WPA2/WPA3). 
6.	Konfigurasi Wi-Fi 
•	Atur nama jaringan (SSID) dan kata sandi Wi-Fi. 
7.	Penyimpanan & Pengujian 
•	Simpan pengaturan dan restart router. 
•	Uji koneksi internet dan jaringan lokal.


Pengenalan Routing dan Routing statis
•	Routing adalah proses pengiriman data dari satu jaringan ke jaringan lain melalui router. 
•	Router menentukan jalur terbaik untuk mencapai tujuan berdasarkan tabel routing. 
-	Jenis Routing: Routing Statis: Dikonfigurasi secara manual. 
Routing Dinamis: Menggunakan protokol untuk pembaruan otomatis (OSPF, RIP, BGP).
•	Routing Statis Definisi: Jalur ditentukan secara manual oleh administrator jaringan.
•	Konfigurasi Routing Statis 
Static (Manual)
1.	Dalam WinBox → IP → Addresses
2.	Tambahkan IP Address baru → Contohnya 192.168.10.1/24 → Sesuaikan interface dengan ether dari sambungan kabel LAN → Apply → Ok
3.	Buka Control Panel untuk mengatur IP Laptop
Control Panel → Network and Internet → Network and Sharing Center → Ethernet → Properties
4.	Ubah IPv4 dengan double click → Use the following IP Address → Isi dengan 192.168.10.2 (2 karena 1 sudah digunakan MikroTik) → Tab untuk kolom yang lain → Ok
5.	Lakukan Ping terhadap IP Laptop dalam Terminal WinBox

DHCP (Otomatis)
1.	Dalam WinBox → IP → Addresses
2.	Tambahkan IP Address baru → Contohnya 192.168.10.1/24 → Sesuaikan interface dengan ether dari sambungan kabel LAN → Apply → Ok
3.	Buka Control Panel untuk mengatur IP Laptop
Control Panel → Network and Internet → Network and Sharing Center → Ethernet → Properties
4.	Ubah IPv4 dengan double click → Obtain an IP Address automatically → Ok
5.	Dalam WinBox → IP → DHCP Server
6.	Tambahkan DHCP dengan DHCP Setup → Sesuaikan interface dengan ether yang digunakan → Klik Next sampai selesai
7.	Buka bagian Leases dalam DHCP Server → Lihat IP dalam bagian Active Addresses
8.	Lakukan Ping terhadap IP Address yang ada dalam Leases di Terminal WinBox

Bridge
1.	Dalam WinBox → Bridge
2.	Tambahkan Bridge baru → Apply → Ok
3.	Tambahkan Bridge Port → Sesuaikan interface dengan ether yang digunakan → Sesuaikan Bridge dengan Bridge yang sudah dibuat → Apply → Ok
4.	Tambahkan IP Address → Ubah interface dengan Bridge yang sudah dibuat → Apply → Ok
5.	Tambahkan DHCP dengan DHCP Setup → Sesuaikan interface dengan Bridge yang sudah dibuat → Klik Next → Pada bagian DNS Servers ubah menjadi 8.8.8.8 → Klik Next sampai selesai
6.	Buka Command Prompt → ipconfig → Lihat IPv4 Address → Lakukan Ping terhadap sesama Laptop (Laptop A melakukan Ping terhadap IP Laptop B dan sebaliknya)
7.	Buka XAMPP dan nyalakan → Salin IP Address Laptop satu sama lain untuk melihat web XAMPP jika sudah tersambung.




#Ip clas A -> 10 
	B -> 172 
	C -> 192 -> 256 -> total ip 
#Subnet /24 -> 256 -> 255.255.255.0
	/25 -> 128
	/26 -> 64
	/27 -> 32
	/28 -> 16 
	/29 -> 8
	/30 -> 4
	/31 -> 2
	/32 -> 1
Naik (X 2) Turun (:2) / start dari /24)
Ip host -> mulaI dari 0 
255.255.255.128 ( :2 )
255.255.128. 0 (x2)
IPV 4 -> maksimalnya 32 bit 
Protocol : 6 (tcp)
Dst rost : 80
Multiarea OSPF membutuhkan desain jaringan hirarkis dan area utama disebut backbone area, atau area 0, dan semua area lainnya harus terhubung ke backbone area. router-router yang menghubungkan area-area lain ke backbone di dalam sebuah AS disebut Area Border Routers (ABRs)
Multiarea OSPF diimplementasikan dalam hierarki area dua lapis: 
1.	Backbone Area (transit) 
• Area yang fungsi utamanya adalah pergerakan paket IP yang cepat dan efisien. • Berinterkoneksi dengan tipe area OSPF lainnya. • Disebut OSPF area 0, yang menghubungkan semua area lainnya secara langsung.
2.	Area reguler (Non-Backbone) 
• Menghubungkan pengguna dan sumber daya. • Area reguler tidak mengizinkan lalu lintas dari area lain menggunakan linknya untuk menjangkau area lain.
#Konfigurasi Multiarea OSPF
 Konfigurasi mendasar dari OSPF tidak sesederhana RIP, IGRP, dan EIGRP, dan konfigurasi ini bias menjadi benar-benar rumit ketika banyak opsi yang diperbolehkan di OSPF, ikut diperhitungkan. Bagian berikut menggambarkan bagaimana mengkonfigurasi OSPF area tunggal. Contoh berikut menampilkan konfigurasi OSPF multiarea: 
• R1 (config) # router ospf 10 • R1 (config-router) # router-id 1.1.1.1 • R1 (config-router) # network 10.1.1.1 0.0.0.0 area 1 • R1 (config-router) # network 10.1.2.1 0.0.0.0 area 1 • R1 (config-router) # network 192.168.10.1 0.0.0.0 area 0
