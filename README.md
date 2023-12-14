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
Virtual Environment digunakan

## 9. Persiapan Load Balancer
Sebelum memulai, kita melakukan install load balancer terlebih dahulu menggunakan perintah 

`sudo apt-get install nginx`

Lakukan konfigurasi Nginx Setelah instalasi selesai, buka dan edit file konfigurasi Nginx dengan menggunakan teks editor dengan perintah seperti dibawah ini

`sudo nano /etc/nginx/nginx.conf`

Jika sudah masuk pada edit file tambahkan konfigurasi berikut di dalam blok http

```
upstream mongodb_servers {
    server <worker1_ip>:27017;
    server <worker2_ip>:27017;
    # Add more worker instances if needed
}
```
Sekarang, buat konfigurasi untuk Load Balancer dengan membuat file baru di direktori dengan perinatah `sudo nano /etc/nginx/conf.d/mongodb_load_balancer.conf
` lalu tambahkan konfigurasi sebagai berikut

```
server {
    listen 80;
    server_name mongodb-loadbalancer;

    location / {
        proxy_pass http://mongodb_servers;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
    }
}
```

Jika sudah lakukan uji konfigurasi nginx dengan perintah `sudo nginx -t`, jika berhasil dan tidak terjadi kesalahan selanjutnya melakukan restrat pada nginx `sudo systemctl restart nginx`

