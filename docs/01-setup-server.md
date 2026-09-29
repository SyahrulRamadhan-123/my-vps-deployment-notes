# Set up server dari awal 

Langkah - langkah dan beberapa catat  terkait permasalahan saat konfigrasi ada dibawah

## 1. Akses VPS pertama

Remote VPS menggunakan SSH sebagai `root`:
```
ssh root@IP_ADDRESS_VPS
```
## Catatan SSH: Kenapa Gak bisa login as Root?
kalau saat pertama remote VPS menggunakan SSH muncul pesan error => *Please login as the user "user-VPS" rather than the user "root".*

**Solusi**
Artinya provider VPS, menerapkan standar keamanan terhadap akses tingkat `root` langsung ditutup, dan diharuskan login menggunakan *default user atau yang sudah dibuat saat menyewa VPS itu* Contohnya: 
```
ssh -i file-kunci.pem ubuntu@IP_ADDRESS_VPS
```

## 2. Update & Upgrade Sistem
```
sudo apt update && sudo apt upgrade -y
```
## Tujuan dari printah
untuk memastikan semua paket sistem operasi (Ubuntu) berada dalam versi terbaru dan `-y` itu menandakan bahwa meng-iyakan semua proses konfirmasi upgrade paket yang akan muncul.

## 3. Konfigurasi UFW (Uncomplicated Firewall)

## Catata UFW: Sebagian besar VPS dengan os Ubuntu sudah ada UFW secara default 
kalau belum terinstall bisa menginstall nya dengan cara berikut:

```
sudo apt install ufw -y
```
## Tujuan dari printah
untuk menginstall sebuah paket berupa ufw (Uncomplicated Firewall)

```
sudo ufw allow OpenSSH
```
## Tujuan dari printah
untuk memberikan izin akses SSH *penting* kalau engga pada saat UFW dinyalakan sesi remot sekarang terganggu atau bermasalah, bahkan hingga terkunci dari server sendiri!

```
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp
```
## Tujuan dari printah
untuk memberikan izin akses Web *(HTTP & HTTPS)*

```
sudo ufw enable
```
## Tujuan dari printah
untuk menjalankan UFW

```
sudo ufw status
```
## Tujuan dari printah
untuk melihat status firewall 