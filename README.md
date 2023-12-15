# Cloud-Server-Load-Test-Kelompok-3

|       Nama      | NRP        | 
| -----------     | :---------: 
| Athallah Narda W | 5027211041 |
| Moh. Sulthan Arief R | 5027211045 |
| Raditya Pratama | 5027211047 |
| Vira Datry M | 5027211050 |
| Wisnu Adjie Saka | 5027211051 | 
| Adimasdefatra Bimasena | 5027211040 | 


# Permasalahan

Anda adalah seorang lulusan Teknologi Informasi, sebagai ahli IT, salah satu kemampuan yang harus dimiliki adalah Keampuan merancang, membangun, mengelola aplikasi berbasis komputer menggunakan layanan awan untuk memenuhi kebutuhan organisasi.(menurut kurikulum IT ITS 2023 😙)

Pada suatu saat teman anda ingin mengajak anda memulai bisnis di bidang digital marketing, anda diberikan sebuah aplikasi berbasis API File: app.py dengan spesifikasi yang terdapat pada soal github.

# Rancangan Arsitektur Cloud

 Kami membuat 2 model arsitektur cloud yang kami buat dari  cloud provider Digital Ocean.

- Pertama, menggunakan 2 worker dan 1 load balancer yang dihubungkan ke database:

![image](https://github.com/Delsea12/Jarkom-Modul-4-IT13-2023/assets/113821220/559af413-82c5-4901-b8dd-f34749941e22)

Tabel Spesifikasi dan Harga:

![image](https://github.com/Delsea12/Jarkom-Modul-4-IT13-2023/assets/113821220/2f534615-5678-4c40-99cd-ffbd00a14cf5)

- Kedua, menggunakan 1 worker yang langsung dihubungkan ke database:

![image](https://github.com/RP-Tama/Cloud-Server-Load-Test-Kelompok-3/assets/113072294/9ebf370f-99a2-4cfb-821f-1f93187fdf47)

Tabel Spesifikasi dan Harga:

![image](https://github.com/RP-Tama/Cloud-Server-Load-Test-Kelompok-3/assets/113072294/ab6cd410-9b17-4f21-baf9-93df8a435df1)



# Implementasi dan Konfigurasi
## 1. Persiapan Database
Sebelum mulai praktik install MongoDB di Ubuntu, ada beberapa hal yang perlu Anda persiapkan, yaitu:

- **Perangkat Ubuntu** – Siapkan komputer atau server VPS dengan sistem operasi Linux Ubuntu. Sebagai contoh, kami akan menggunakan layanan VPS dari Niagahoster.
- **Versi Ubuntu** - Pada kali ini, kami akan menginstall MongoDB di Ubuntu 20.04. Namun, panduan ini juga kompatibel dengan versi lain, misalnya Ubuntu 18.04.
Jika dua hal di atas sudah siap, mari lanjutkan ke langkah berikutnya!

## 2. Login dan Update Server
Langkah kedua dalam cara install MongoDB di Ubuntu 20.04 adalah login ke server Ubuntu dengan cara menggunakan SSH. Jika sudah, ikuti tahap-tahap berikut ini untuk mengupdate server:

- Pertama, jalankan perintah berikut untuk memperbarui repository Ubuntu:
```bash
sudo apt-get update && sudo apt-get upgrade
```
- Silakan tunggu, proses update server sedang berlangsung. Apabila berhasil, Anda akan melihat tampilan berikut:
![gambar](https://niagaspace.sgp1.digitaloceanspaces.com/blog/wp-content/uploads/2023/05/31073042/1-update-server-ubuntu.webp)
*Diatas ini merupakan output yang dihasilkan setelah menjalankan perintah update repository Ubuntu*

## 3. Install MongoDB
Setelah server Ubuntu diperbarui, tahap berikutnya adalah instalasi MongoDB Ubuntu. Untuk melakukannya, Anda hanya perlu menjalankan perintah sederhana di bawah:
```bash
sudo apt-get install mongo
```
Proses instalasi MongoDB akan berjalan. Jika sudah, output yang muncul di layar kurang lebih seperti ini:
![gambar](https://niagaspace.sgp1.digitaloceanspaces.com/blog/wp-content/uploads/2023/05/31073045/2-cara-install-mongodb-di-ubuntu.webp)
*Output yang dihasilkan setelah mengeksekusi perintah instalasi MongoDB*

## 4. Aktifkan MongoDB
Tutorial install MongoDB Ubuntu 20.04 dilanjutkan dengan mengaktifkan database MongoDB. Caranya mudah, cukup eksekusi command berikut ini:
```bash
sudo systemctl enable mongodb
```
Kemudian, jalankan MongoDB pada server Ubuntu lewat perintah di bawah:
```bash
sudo systemctl start mongodb
```
Tampilan yang dihasilkan adalah sebagai berikut:
![gambar](https://niagaspace.sgp1.digitaloceanspaces.com/blog/wp-content/uploads/2023/05/31073047/3-mengaktifkan-dan-menjalankan-mongodb-dalam-cara-install-mongodb.webp)
*Eksekusi perintah untuk mengaktifkan dan menjalankan MongoDB di Ubuntu*

## 5. Cek Status MongoDB Ubuntu
Langkah terakhir dalam cara install MongoDB di Ubuntu ini sebenarnya opsional. Namun, Anda dapat memastikan apakah aplikasi database ini sudah berhasil aktif di Ubuntu menggunakan perintah di bawah:
```bash
sudo systemctl status mongodb
```
Anda akan melihat output yang satu ini jika MongoDB sudah berjalan di Ubuntu:
![gambar](https://niagaspace.sgp1.digitaloceanspaces.com/blog/wp-content/uploads/2023/05/31073049/4-cek-status-mongodb-dalam-install-mongodb-ubuntu.webp)
*MongoDB dalam keadaan aktif pada server Ubuntu8*

Sampai di sini, Anda telah menyelesaikan tutorial install MongoDB Ubuntu.

## 6. Persiapan Worker
Setelah membuat droplet worker pada digital ocean berdasarkan topologi. Akses worker tersebut melalui terminal dengan cara:
```bash
ssh root@[IP Worker]
```
Berikut adalah contohnya ketika sudah berhasil mengakses VPS cloud:

![image](https://github.com/RP-Tama/Cloud-Server-Load-Test-Kelompok-3/assets/113072294/0f74decc-30e1-4823-8494-009788f4b412)

## 7. Git Clone Repository FP TKA
Setelah berhasil mengakses VPS Worker kita bisa meng git clone repository soal FP TKA untuk mendapatkan script python app.py soal dengan cara:
```bash
git clone https://github.com/fuaddary/fp-tka.git
```
Tetapi sebelum itu kita harus mengupdate repository ubuntu
```bash
sudo apt-get update && sudo apt-get upgrade
```
Setelah berhasil menginstal akan ada folder fp-tka

![image](https://github.com/RP-Tama/Cloud-Server-Load-Test-Kelompok-3/assets/113072294/59132cae-b9e2-4b78-883f-9d3b62dd708d)

## 8. Buat Virtual Environment
Virtual Environment digunakan untuk membuat lingkungan yang terisolasi di dalam proyek Anda dan menginstal paket yang dibutuhkan tanpa mempengaruhi instalasi global di sistem operasi Anda. Ini membantu mencegah konflik antara versi pustaka dan memudahkan manajemen dependensi proyek. Untuk menginstalnya pertama instal python:
```bash
sudo apt-get install python3
sudo apt-get install python3-pip
sudo apt-get install python3-venv
```
Setelah menginstal python kita bisa membuat venv di dalam folder fp-tka
```bash
cd fp-tka
python3 -m venv venv
```
Setelah itu kita bisa mengaktifkan virtual environment dengan menjalankan command:
```bash
source venv/bin/activate
```
Setelah aktif kita bisa menggunakan pip.

## 9. Menginstal Dependensi
Setelah masuk di virtual environment kita perlu menginstal dependensi yang dibutuhkan. Berikut dependensinya:
```bash
pip install flask
pip install gunicorn
pip install flask_pymongo
pip install gevent
```

## 10. Memasukkan database ke app.py
buka app.py dan ganti MONGO_URI nya menjadi IP dari Database
```bash
# Configuration for MongoDB
app.config['MONGO_URI'] = 'mongodb://178.128.61.6:27017/orders_db'
mongo = PyMongo(app)
```

## 11. Menajalankan Worker
Didalam virtual environment masukan command berikut untuk menjalankan gunicorn:
```bash
gunicorn --bind 0.0.0.0:80 -w 8 -k gevent app:app
```
worker berjalan pada port 80

## 12. Persiapan Load Balancer
Sebelum memulai, kita melakukan install load balancer terlebih dahulu menggunakan perintah 

`sudo apt-get install nginx`

Lakukan konfigurasi Nginx Setelah instalasi selesai, buka dan edit file konfigurasi Nginx dengan menggunakan teks editor dengan perintah seperti dibawah ini

`sudo nano /etc/nginx/nginx.conf`

Jika sudah masuk pada edit file tambahkan konfigurasi berikut di dalam blok http

```
upstream backend {
        server 139.59.248.121;
        server 68.183.181.9;
    }
```
dan untuk setingan fullnya ada disini

```
worker_processes auto;
worker_rlimit_nofile 10000000;

error_log /var/log/nginx/error.log crit;

events {
    worker_connections 4000;
    use epoll;
    multi_accept on;
}

http {

    upstream backend {
        server 139.59.248.121;
        server 68.183.181.9;
    }
    open_file_cache max=200000 inactive=20s;
    open_file_cache_valid 30s;
    open_file_cache_min_uses 2;
    open_file_cache_errors on;

    access_log off;

    sendfile on;
    tcp_nopush on;
    tcp_nodelay on;

    gzip on;
    gzip_min_length 10240;
    gzip_comp_level 1;
    gzip_vary on;
    gzip_disable msie6;
    gzip_proxied expired no-cache no-store private auth;
    gzip_types
        text/css
        text/javascript
        text/xml
        text/plain
        text/x-component
        application/javascript
        application/x-javascript
        application/json
        application/xml
        application/rss+xml
        application/atom+xml
        font/truetype
        font/opentype
        application/vnd.ms-fontobject
        image/svg+xml;

    reset_timedout_connection on;
    client_body_timeout 10;
    send_timeout 2;
    keepalive_timeout 30;
    keepalive_requests 100000;

    # Konfigurasi Cache


    # Konfigurasi Cache
    proxy_cache_path /var/cache/nginx levels=1:2 keys_zone=my_cache:10m max_size=10g inactive=60m use_temp_path=off;

    # Reverse Proxy Configuration
    server {
        listen 80 backlog=16384;
        server_name localhost; # Atau domain Anda

        location / {
            proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
            proxy_set_header X-Forwarded-Proto $scheme;
            proxy_set_header Host $http_host;
            # we don't want nginx trying to do something clever with
            # redirects, we set the Host: header above already.
            proxy_redirect off;
            proxy_pass http://backend;

            # Setelan Cache
            proxy_cache my_cache;
            proxy_cache_valid 200 60m;
            proxy_cache_valid 404 1m;
        }
    }
}





```

Jika sudah lakukan uji konfigurasi nginx dengan perintah `sudo nginx -t`, jika berhasil dan tidak terjadi kesalahan selanjutnya melakukan restrat pada nginx `sudo systemctl restart nginx`
## 13. Testing EndPoint
* Get /orders
![image](https://github.com/RP-Tama/Cloud-Server-Load-Test-Kelompok-3/assets/88955368/f9ff4678-d6a8-4b25-8592-ef7166d0e150)

* Get /orders/<string:order_id>
![image](https://github.com/RP-Tama/Cloud-Server-Load-Test-Kelompok-3/assets/88955368/005d7254-dfe9-44b4-abff-278a8af592bd)

* Post /orders
![image](https://github.com/RP-Tama/Cloud-Server-Load-Test-Kelompok-3/assets/88955368/2e6e8bd0-faf8-4eb7-a3a5-fdd18823c16e)


* Put /orders/<string:order_id>
![image](https://github.com/RP-Tama/Cloud-Server-Load-Test-Kelompok-3/assets/88955368/2e6e8bd0-faf8-4eb7-a3a5-fdd18823c16e)

* Delete /orders/<string:order_id>
![image](https://github.com/RP-Tama/Cloud-Server-Load-Test-Kelompok-3/assets/88955368/e38055ea-2e12-474e-89a1-d56749f01dce)

## 14. Hasil Load testing
| Spawn Rate | Arsitektur 1 User | Arsitektur 1 RPS | Arsitektur 2 User | Arsitektur 2 RPS |
|------------|-------------------|------------------|-------------------|------------------|
| 25         | 825               | 259              | 1425              | 534              |
| 50         | 900               | 234              | 2850              | 1106             |
| 100        | 1200              | 202              | 3900              | 1145             |

Tetapi kami menemukan ke anehan pada saat kami run di pagi hari (jam sibuk)
| Spawn Rate | Arsitektur 2 User | Arsitektur 2 RPS |
|------------|-------------------|------------------|
| 25         | 1500               | 429             |
| 50         | 1250              | 109              |
| 100        | 2300              | 494              |


## 15. Kesimpulan yang kami dapatkan saat mengerjakan fp ini
* Kami menemukan hal yang paling berpengaruh pada peningkatan RPS ini adalah CPU. Hal ini saat kami melakukan pemantauan bahwa saat melakukan request tanpa cache CPU meningkat drastis bahkan sampai 100%
![Screenshot (622)](https://github.com/RP-Tama/Cloud-Server-Load-Test-Kelompok-3/assets/88955368/07bac12c-1609-4110-84c5-49f61e65d412)

dah pada server mongo nya ternyata tidak sampai 100% 

* Error fail pada Arsitektur 1 dan 2 juga berbeda, pada arsitektur 1 fail nya gara gara terkada kita tidak bisa menemukan endpoint /orders aneh nya kedua worker dalam kondisi sehat error nya `HTTPError('500 Server Error: Internal Server Error for url: /orders')` sedang pada arsitektur 2 errornya connection timeout yang mana berarti seiring meningkatnya user maka respon time dari server juga semakin lama hingga terjadi timeout
* RPS meningkat drastis dan CPU berkurang drastis saat kita mengaplikasi cache, yang mana ini sangat berpengaruh bahkan 3x lipat dari sebelumnya
* Penggunaan NGINX juga Berpengaruh dari pada langsung serving dari gunicorn langsung ke internet lebih baik diarahkan ke NGINX dulu
* Penggunaan woker asnchronus, karena command running kami `gunicorn app:app --workers=9 --worker-class=eventlet --bind=0.0.0.0:8000` yang mana eventlet adalah library concurrent networking untuk Python yang menggunakan coroutines (atau green threads) untuk mencapai efisiensi tinggi dalam menjalankan operasi I/O secara asynchronous. Mungkin kelompok lain banyak yg pakai gevent itu karena awalnya mungkin kelompok kami juga yg memakainya tapi ternyata dari segi performa lebih baik eventlet
* Setingan NGINX yang optimal juga sangat berpengaruh
* Koneksi internet dari host locust juga mempengaruhi keberhasilan
* Karena concurent itu adalah CPU-bound jadi semakin banyak core CPU maka semakin banyak pula request yang bisa handle oleh server

## 16. Percobaan yang mungkin bisa di lakukan di kedepannya untuk meng optimalkan server
* menggunanakan 7 worker dengan 1CPU dan 512MB ram
* membuat get /orders menjadi pagination agar saat document sudah sangat banyak server tidak mengirimkan data yang begitu besar
* mengganti Flask menjadi FastAPI: Berikur penjelasan dari ChatGPT kenapa fast api lebih unggul Salah satu perbedaan utama antara Flask dan FastAPI adalah dukungan untuk asynchronous programming. FastAPI dibangun di atas Starlette dan Pydantic, yang mendukung asynchronous request handling. Ini berarti FastAPI dapat menangani banyak request secara simultan dan efisien, terutama dalam situasi dengan banyak operasi I/O, seperti permintaan ke database atau layanan eksternal. Sementara itu, Flask didesain untuk synchronous programming, yang cenderung lebih lambat dalam menangani banyak request secara simultan.
* Pengunaan load balancer yang lebih complex


## 17. Kendala yang kami hadapi
* mongo db ter hack, kemungkinan karena terkena botnet karena portnya terbukan dan tidak diberi password
* susah mendaftar free trial azure/digital ocean

# Referensi untuk membuat script yg kami gunakan
* nginx.conf
Sumber: https://gist.github.com/denji/8359866

* TCP Tweak
sumber: https://github.com/iahmad-khan/system-admin/blob/master/linux-tcp-tweaks

* Gunicorn conf
Sumber: https://medium.com/building-the-system/gunicorn-3-means-of-concurrency-efbb547674b7
https://stackoverflow.com/questions/71893002/how-to-make-flask-handle-25k-request-per-second-like-express-js

* Cache
Sumber: https://tonyteaches.tech/nginx-server-cache/



```
