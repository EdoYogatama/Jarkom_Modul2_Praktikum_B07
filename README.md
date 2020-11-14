# Jarkom_Modul2_Praktikum_B07

## Kelompok
* 05111840000060 Edo Dwi Yogatama 
* 05111840000091 Vincentius Tanubrata

#### 1. Kalian diminta untuk membuat sebuah website utama dengan alamat **http://semeruyyy.pw**
#### 2. yang memiliki alias **http://www.semeruyyy.pw**
#### 3. dan subdomain **http://penanjakan.semeruyyy.pw** yang diatur DNS-nya pada **MALANG** dan mengarah ke IP Server **PROBOLINGGO**
#### 4. serta dibuatkan reverse domain untuk domain utama.
#### 5. Untuk mengantisipasi server dicuri/rusak, Bibah minta dibuatkan DNS Server Slave pada **MOJOKERTO** agar Bibah tidak terganggu menikmati keindahan Semeru pada Website.
#### 6. Selain website utama Bibah juga meminta dibuatkan subdomain dengan alamat **http://gunung.semeruyyy.pw** yang didelegasikan pada server **MOJOKERTO** dan mengarah ke IP Server **PROBOLINGGO**.
#### 7. Bibah juga ingin memberi petunjuk mendaki gunung semeru kepada anggota komunitas sehingga dia meminta dibuatkan subdomain dengan nama **http://naik.gunung.semeruyyy.pw**, domain ini diarahkan ke IP Server **PROBOLINGGO**. 
#### 8. Setelah selesai membuat keseluruhan domain, kamu diminta untuk segera mengatur web server. Domain **http://semeruyyy.pw** memiliki _DocumentRoot_ pada **/var/www/semeruyyy.pw**
* Pada UML PROBOLINGGO menginstall apache2 dan php5 dengan command :
```
apt-get update
apt-get install apache2
apt-get install php
```
* Setelah itu mendowndload dan _unzip_ folder website yang telah tersedia (Install unzip apabila belum terinstall di UML PROBOLINGGO)
* Pindah direktori ke **/etc/apache2/sites-available**
* Mengcopy file konfigurasi **default** dengan nama **semerub07.pw** setelah itu buka file dan mengganti konfigurasi seperti dibawah
```
cd /etc/apache2/sites-available
cp default semerub07.pw
nano semerub07.pw
```
![Isi /etc/apache2/sites-available/semerub07.pw](images/8.jpg)
* Pindah direktori ke **/var/www/**, setelah itu move folder yang sudah diekstrak dari hasil download direktori tersebut, dan memberi nama folder **semerub07.pw**
* Jalankan command sebgai berikut untuk enable konfigurasi website
```
a2ensite semerub07.pw
service apache2 restart
```
#### 9. Awalnya web dapat diakses menggunakan alamat **http://semeruyyy.pw/index.php/home**. Karena dirasa alamat urlnya kurang bagus, maka diaktifkan mod rewrite agar urlnya menjadi **http://semeruyyy.pw/home**.
* Membuka folder **/var/www/semerub07.pw** lalu membuat file **.htaccess** dan berisikan sebagai berikut
```
cd /var/www/semerub07.pw
nano .htaccess
``` 
![Isi /var/www/semerub07.pw/.htaccess](images/91.jpg)
* Setelah itu membuka file konfigurasi di **/etc/apache2/sites-available/semerub07.pw** dan menambahkan script berikut
```
cd /etc/apache2/sites-available
nano semerub07.pw
```
![/etc/apache2/sites-available/semerub07.pw](images/92.jpg)
* Jalankan command sebgai berikut untuk enable konfigurasi website
```
a2ensite semerub07.pw
service apache2 restart
```
#### 10. Web **http://penanjakan.semeruyyy.pw** akan digunakan untuk menyimpan assets file yang memiliki _DocumentRoot_ pada **/var/www/penanjakan.semeruyyy.pw** dan memiliki struktur folder sebagai berikut: 
```
/var/www/penanjakan.semeruyyy.pw 
                                /public/javascripts 
                                /public/css 
                                /public/images 
                                /errors
```
* Pindah direktori ke **/etc/apache2/sites-available**
* Mengcopy file konfigurasi **default** dengan nama **penanjakan.semerub07.pw** setelah itu buka file dan mengganti konfigurasi _ServerName ServerAlias DocumentRoot_ seperti dibawah
```
cd /etc/apache2/sites-available
cp default penanjakan.semerub07.pw
nano penanjakan.semerub07.pw
``` 
![Isi /etc/apache2/sites-available/penanjakan.semerub07.pw](images/10.jpg)
* Pindah direktori ke **/var/www/**, setelah itu move folder yang sudah diekstrak dari hasil download direktori tersebut, dan memberi nama folder **penanjakan.semerub07.pw**
* Jalankan command sebgai berikut untuk enable konfigurasi website
```
a2ensite penanjakan.semerub07.pw
service apache2 restart
```
#### 11. Pada folder */public* dibolehkan directory listing namun untuk folder yang berada di dalamnya tidak dibolehkan. 
* Menambahkan konfigurasi pada file **/etc/apache2/sites-available/penanjakan.semerub07.pw** untuk indexing directory seperti berikut
![Isi /etc/apache2/sites-available/penanjakan.semerub07.pw](images/10.jpg)
#### 12. Untuk mengatasi HTTP Error code 404, disediakan file 404.html pada folder **/errors** untuk mengganti error default 404 dari Apache
* Membuka folder **/var/www/penanjakan.semerub07.pw** lalu membuat file **.htaccess** dan berisikan sebagai berikut
```
cd /var/www/penanjakan.semerub07.pw
nano .htaccess
``` 
![Isi /var/www/penanjakan.semerub07.pw/.htaccess](images/121.jpg)
* Setelah itu membuka file konfigurasi di **/etc/apache2/sites-available/penanjakan.semerub07.pw** dan menambahkan script berikut
```
cd /etc/apache2/sites-available
nano penanjakan.semerub07.pw
```
![/etc/apache2/sites-available/penanjakan.semerub07.pw](images/122.jpg)
* Jalankan command sebgai berikut untuk enable konfigurasi website
```
a2ensite penanjakan.semerub07.pw
service apache2 restart
```
#### 13. Untuk mengakses file assets javascript awalnya harus menggunakan url **http://penanjakan.semeruyyy.pw/public/javascripts**. Karena terlalu panjang maka dibuatkan konfigurasi virtual host agar ketika mengakses file assets menjadi **http://penanjakan.semeruyyy.pw/js**. 
* Membuka file konfigurasi pada **/etc/apache2/sites-available/penanjakan.semerub07.pw**
* Menambahkan _Alias_ pada script konfigurasi sebagai berikut
![/etc/apache2/sites-available/penanjakan.semerub07.pw](images/131.jpg)
* Jalankan command sebgai berikut untuk enable konfigurasi website
```
a2ensite penanjakan.semerub07.pw
service apache2 restart
```
#### 14. Untuk web **http://gunung.semeruyyy.pw** belum dapat dikonfigurasi pada web server karena menunggu pengerjaan website selesai. sedangkan web **http://naik.gunung.semeruyyy.pw** sudah bisa diakses hanya dengan menggunakan port **8888**. DocumentRoot web berada pada **/var/www/naik.gunung.semeruyyy.pw**.

#### 15. Dikarenakan web **http://naik.gunung.semeruyyy.pw** bersifat private Bibah meminta kamu membuat web **http://naik.gunung.semeruyyy.pw** agar diberi autentikasi password dengan username **“semeru”** dan password **“kuynaikgunung”** supaya aman dan tidak sembarang orang bisa mengaksesnya. 
#### 16. Saat Bibah mengunjungi **IP PROBOLINGGO**, yang muncul bukan web utama **http://semeruyyy.pw** melainkan laman default Apache yang bertuliskan “It works!”. Karena dirasa kurang profesional, maka setiap Bibah mengunjungi IP PROBOLINGGO akan dialihkan secara otomatis ke **http://semeruyyy.pw**. 
#### 17. Karena pengunjung pada **/var/www/penanjakan.semeruyyy.pw/public/images** sangat banyak maka semua request gambar yang memiliki substring **“semeru”** akan diarahkan menuju **semeru.jpg**