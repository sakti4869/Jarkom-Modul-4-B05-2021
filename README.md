# Jarkom-Modul-4-B05-2021

## VLSM (Variable Length Subnet Masking) - CPT

Langkah 1 : Menentukan jumlah alamat IP yang dibutuhkan oleh tiap subnet dan melakukan labelling netmask berdasarkan jumlah IP yang dibutuhkan

![2021-11-23 09 28 02](https://user-images.githubusercontent.com/71221969/143668982-39e96e7d-6e0a-4711-9400-09a30ba2f6b4.png)

Sehingga didapatkan tabel berikut:

| Subnet  | IP | Subnet Mask  | Lenghth | Jumlah IP |
| ------------- | ------------- | ------------- | ------------- | ------------- |
| A1 (blueno) | 192.179.8.0 | 255.255.252.0 | /22 | 1001 |
| A2 (chiper) | 192.179.12.0 | 255.255.252.0 | /22 | 701 |
| A3 (jipangu) | 192.179.27.0 | 255.255.252.128 | /25 | 101 |
| A4 (calmbelt + courtyard) | 192.179.0.0 | 255.255.248.0 | /21 | 2021 |
| A5 (water7 + pucci) | 192.179.27.144 | 255.255.255.252 | /30 | 2 |
| A6 (foosha + water7) | 192.179.27.148 | 255.255.255.252 | /30 | 2 |
| A7 (jabra) | 192.179.16.0 | 255.255.252.0 | /22 | 521 |
| A8 (foosha + guanhao) | 192.179.27.152 | 255.255.255.252 | /30 | 2 |
| A9 (enieslobby) | 192.179.26.0 | 255.255.255.0 | /24 | 251 |
| A10 (guanhao + oimo) | 192.179.27.156 | 255.255.255.252 | /30 | 2 |
| A11 (elena) | 192.179.20.0 | 255.255.252.0 | /22 | 721 |
| A12 (maingate) | 192.179.24.0 | 255.255.254.0 | /23 | 501 |
| A13 (jorge) | 192.179.27.128 | 255.255.255.240 | /28 | 13 |
| A14 (doriki) | 192.179.27.160 | 255.255.255.252 | /30 | 2 |
| A15 (fukurou) | 192.179.27.164 | 255.255.255.252 | /30 | 2 |
| Total |  | 	255.255.224.0 | /19 | 5845 |

Langkah 2 : Subnet besar yang dibentuk memiliki NID 10.2.0.0 dengan netmask length /19. Hitung pembagian IP berdasarkan NID dan netmask tersebut menggunakan pohon seperti gambar di bawah

![660221](https://user-images.githubusercontent.com/71221969/143668987-e09ba896-28ee-421a-a78c-2a995da6f2ab.jpg)

Langkah 3 : Mengatur konfigurasi pada menu routing>static pada router

| Router  | Network | Mask  | Next Hop |
| ------------- | ------------- | ------------- | ------------- |
| Foosha | 192.179.12.0<br>192.179.0.0<br>0.0.0.0<br>192.179.27.0<br>192.179.27.144 | 255.255.252.0<br>255.255.248.0<br>0.0.0.0<br>255.255.252.128<br>255.255.255.252 | 192.179.27.149<br>192.179.27.149<br>192.179.27.154<br>192.179.27.149<br>192.179.27.149 |
| Water7 | 0.0.0.0<br>192.179.27.0<br>192.179.0.0 | 0.0.0.0<br>255.255.252.128<br>255.255.248.0 | 192.179.27.150<br>192.179.27.146<br>192.179.27.146 |
| Pucci | 0.0.0.0 | 0.0.0.0 | 192.179.27.145 |
| Guanhao | 0.0.0.0<br>192.179.27.128<br>192.179.20.0<br>192.179.26.0<br>192.179.27.164 | 0.0.0.0<br>255.255.255.240<br>255.255.252.0<br>255.255.255.0<br>255.255.255.252 | 192.179.27.153<br>192.179.24.2<br>192.179.27.157<br>192.179.27.157<br>192.179.27.157 |
| Alabasta | 0.0.0.0 | 0.0.0.0 | 192.179.24.1 |
| Oimo | 0.0.0.0<br>192.179.20.0 | 0.0.0.0<br>255.255.252.0 | 192.179.27.158<br>192.179.26.2 |
| Seast One | 0.0.0.0 | 0.0.0.0 | 192.179.26.1 |

Langkah 4: Paket siap dijalankan
![image](https://user-images.githubusercontent.com/71221969/143669628-19c10699-30b4-4e36-853d-dd1f82f49dea.png)

## CIDR - GNS3
Menggabungkan subnet-subnet paling bawah dalam topologi yaitu dimulai dari subnet yang paling jauh dari internet(gambar awan).

#### Kondisi Awal

[![soal2.jpg](https://i.postimg.cc/C5m29jmh/soal2.jpg)](https://postimg.cc/Lggv1gcw)

#### Gabungan Pertama(Subnet B)

1. Penggabungan 1 yaitu subnet A1 dan A2 menghasilkan B1 dengan netmask /20 yaitu satu tingkat dari netmask terbesar yang diambil yaitu /21 dari A2.
2. Penggabungan 2 yaitu subnet A12 dan A13 menghasilkan B2 dengan netmask /21 (satu tingkat dari /22).
3. Penggabungan 3 yaitu subnet A9 dan A10 menghasilkan B3 dengan netmask /22 (satu tingkat dari /23).

[![soal3.jpg](https://i.postimg.cc/tC4wWM4Y/soal3.jpg)](https://postimg.cc/7bjKyX7k)

#### Gabungan Pertama(Subnet C)

1. Penggabungan 1 yaitu subnet B1 dan A3 menghasilkan C1 dengan netmask /19 yaitu satu tingkat dari netmask terbesar yang diambil yaitu /20 dari B1.
2. Penggabungan 2 yaitu subnet B2 dan A15 menghasilkan C2 dengan netmask /20.
3. Penggabungan 3 yaitu subnet B3 dan A8 menghasilkan B3 dengan netmask /21.

[![soal.jpg](https://i.postimg.cc/FHf6nkcv/soal.jpg)](https://postimg.cc/FY4GYRDC)

#### Gabungan Kedua(Subnet D)

1. Penggabungan 1 yaitu subnet C1 dan A4 menghasilkan D1 dengan netmask /18 yaitu satu tingkat dari netmask terbesar yang diambil yaitu /19 dari C1.
2. Penggabungan 2 yaitu subnet C2 dan A11 menghasilkan D2 dengan netmask /19.

[![soal5.jpg](https://i.postimg.cc/25hKCp2X/soal5.jpg)](https://postimg.cc/f3WKvP4x)

#### Gabungan Ketiga(Subnet E)

1. Penggabungan 1 yaitu subnet D1 dan A6 menghasilkan E1 dengan netmask /17 yaitu satu tingkat dari netmask terbesar yang diambil yaitu /18 dari D1.
2. Penggabungan 2 yaitu subnet D2 dan C3 menghasilkan E2 dengan netmask /18.

[![soal6.jpg](https://i.postimg.cc/PxMV8WGW/soal6.jpg)](https://postimg.cc/YGhz5mC0)

#### Gabungan Keempat(Subnet F)

1. Penggabungan 1 yaitu subnet E1 dan A5 menghasilkan F1 dengan netmask /16 yaitu satu tingkat dari netmask terbesar yang diambil yaitu /17 dari E1.
2. Penggabungan 2 yaitu subnet E2 dan A7 menghasilkan F2 dengan netmask /17.

[![soal7.jpg](https://i.postimg.cc/2ycH0CS3/soal7.jpg)](https://postimg.cc/rR4CmXWL)

#### Gabungan Kelima(Subnet G)

Pada step ini hanya terjadi satu penggabungan yaitu subnet F2 dan A14 menghasilkan G1 dengan netmask /16 yaitu satu tingkat dari netmask terbesar yang diambil yaitu /17 dari F2.

[![soal5-1.jpg](https://i.postimg.cc/d0P5HHwR/soal5-1.jpg)](https://postimg.cc/9DbPzB4z)

#### Gabungan Keenam(Subnet H)

Step terakhir yaitu menggabungkan dua kelompok F1 dan G1 menjadi satu yaitu subnet H1 dengan netmask /15.

[![soal9.jpg](https://i.postimg.cc/SsmDqnXJ/soal9.jpg)](https://postimg.cc/nswvGcGJ)

### Pohon IP

Dari penggabungan yang telah dilakukan, didapatkan pohon pembagian IP sebagai berikut.

[![Decision-Tree.png](https://i.postimg.cc/gc8qGnxY/Decision-Tree.png)](https://postimg.cc/14RNHR0T)

### Tabel Pembagian IP

Maka didapatkan hasil pembagian IP sesuai pada tabel berikut.

| Subnet | Node | IP | Subnet Mask | Length |
| --- | --- | --- | --- | --- |
| A1 | jipangu pucci | 192.180.8.0 | 255.255.255.128 | 25 |
| A2 | court, calm, pucci | 192.180.0.0 | 255.255.248.0 | 21 |
| A3 | pucci water | 192.180.16.0 | 255.255.255.252 | 30 |
| A4 | cipher water | 192.180.32.0 | 255.255.252.0 | 22 |
| A5 | blueno foosh | 192.180.128.0 | 255.255.252.0 | 22 |
| A6 | foosh wat | 192.180.64.0 | 255.255.255.252 | 30 |
| A7 | foosh guan | 192.179.64.0 | 255.255.255.252 | 30 |
| A8 | guan jabra | 192.179.36.0 | 255.255.252.0 | 22 |
| A9 | guanhao maingate alabas | 192.179.32 .0 | 255.255.254.0 | 23 |
| A10 | alabas jorge | 192.179.34.0 | 255.255.255.240 | 28 |
| A11 | guan oimo | 192.179.16.0 | 255.255.255.252 | 30 |
| A12 | oimo enies seastone | 192.179.4.0 | 255.255.255.0 | 24 |
| A13 | seas elena | 192.179.0.0 | 255.255.252.0 | 22 |
| A14 | foosha doriki | 192.179.128.0 | 255.255.255.252 | 30 |
| A15 | fukurou oimo | 192.179.8.0 | 255.255.255.252 | 30 |

### Konfigurasi ETH

Pada network configuration, kita melakukan assignment dengan IP yang telah ditetapkan sesuai dengan subnet

#### Jipangu

```bash
auto eth0
iface eth0 inet static
address 192.180.8.2
netmask 255.255.255.128
gateway 192.180.8.1
```

#### Pucci

```bash
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.180.16.1
netmask 255.255.255.252
gateway 192.180.16.2

auto eth1
iface eth1 inet static
address 192.180.8.1
netmask 255.255.255.128

auto eth2
iface eth2 inet static
address 192.180.0.1
netmask 255.255.248.0
```

#### Courtyard

```bash
auto eth0
iface eth0 inet static
address 192.180.0.2
netmask 255.255.248.0
gateway 192.180.0.1
```

#### Calmbelt

```bash
auto eth0
iface eth0 inet static
address 192.180.0.3
netmask 255.255.248.0
gateway 192.180.0.1
```

#### Water7

```bash
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.180.64.1
netmask 255.255.255.252
gateway 192.180.64.2

auto eth1
iface eth1 inet static
address 192.180.32.1
netmask 255.255.252.0

auto eth2
iface eth2 inet static
address 192.180.16.2
netmask 255.255.255.252
```

#### Cipher

```bash
auto eth0
iface eth0 inet static
address 192.180.32.2
netmask 255.255.252.0
gateway 192.180.32.1
```

#### Foosha

```bash
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
address 192.180.128.1
netmask 255.255.252.0

auto eth2
iface eth2 inet static
address 192.180.64.2
netmask 255.255.255.252

auto eth3
iface eth3 inet static
address 192.179.128.1
netmask 255.255.255.252

auto eth4
iface eth4 inet static
address 192.179.64.1
netmask 255.255.255.252
```

#### Blueno

```bash
auto eth0
iface eth0 inet static
address 192.180.128.2
netmask 255.255.252.0
gateway 192.180.128.1
```

#### Doriki

```bash
auto eth0
iface eth0 inet static
address 192.179.128.2
netmask 255.255.255.252
gateway 192.179.128.1
```

#### Guanhao

```bash
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.179.64.2
netmask 255.255.255.252
gateway 192.179.64.1

auto eth1
iface eth1 inet static
address 192.179.36.1
netmask 255.255.252.0

auto eth2
iface eth2 inet static
address 192.179.32.1
netmask 255.255.254.0


auto eth3
iface eth3 inet static
address 192.179.16.1
netmask 255.255.255.252
```

#### Jabra

```bash
auto eth0
iface eth0 inet static
address 192.179.36.2
netmask 255.255.252.0
gateway 192.179.36.1
```

#### Maingate

```bash
auto eth0
iface eth0 inet static
address 192.179.32.3
netmask 255.255.254.0
gateway 192.179.32.1
```

#### Alabasta

```bash
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.179.32.2
netmask 255.255.254.0
gateway 192.179.32.1

auto eth1
iface eth1 inet static
address 192.179.34.1
netmask 255.255.255.240
```

#### Jorge

```bash
auto eth0
iface eth0 inet static
address 192.179.34.2
netmask 255.255.255.240
gateway 192.179.34.1
```

#### Oimo

```bash
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.179.16.2
netmask 255.255.255.252
gateway 192.179.16.1

auto eth1
iface eth1 inet static
address 192.179.8.1
netmask 255.255.255.252

auto eth2
iface eth2 inet static
address 192.179.4.1
netmask 255.255.255.0
```

#### EniesLobby

```bash
auto eth0
iface eth0 inet static
address 192.179.4.3
netmask 255.255.255.0
gateway 192.179.4.1
```

#### Seastone

```bash
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.179.4.2
netmask 255.255.255.0
gateway 192.179.4.1

auto eth1
iface eth1 inet static
address 192.179.0.1
netmask 255.255.252.0
```

#### Elena

```bash
auto eth0
iface eth0 inet static
address 192.179.0.2
netmask 255.255.252.0
gateway 192.179.0.1
```

### Routing

Routing yang dilakukan di GNS sama persis dengan di CPT, hanya saja syntax dan IPnya berbeda.

#### Pucci

```bash
route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.180.16.2
```

#### Water7

```bash
route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.180.64.2
route add -net 192.180.8.0 netmask 255.255.255.128 gw 192.180.16.1
route add -net 192.180.0.0 netmask 255.255.248.0 gw 192.180.16.1
route add -net 192.180.16.0 netmask 255.255.255.252 gw 192.180.16.1
```

#### Seastone

```bash
route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.179.4.1
```

#### Oimo

```bash
route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.179.16.1
route add -net 192.179.0.0 netmask 255.255.252.0 gw 192.179.4.2
```

#### Alabasta

```bash
route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.179.32.1
```

#### Guanhao

```bash
route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.179.64.1
route add -net 192.179.4.0 netmask 255.255.255.0 gw 192.179.16.2
route add -net 192.179.0.0 netmask 255.255.252.0 gw 192.179.16.2
route add -net 192.179.8.0 netmask 255.255.255.252 gw 192.179.16.2
route add -net 192.179.34.0 netmask 255.255.255.240 gw 192.179.32.2
# oimo-guan subnet
route add -net 192.179.16.0 netmask 255.255.255.252 gw 192.179.32.2
# doriki
route add -net 192.179.128.0 netmask 255.255.255.252 gw 192.179.64.1
```

#### Foosha

```bash
# bawah
route add -net 192.179.4.0 netmask 255.255.255.0 gw 192.179.64.2
route add -net 192.179.0.0 netmask 255.255.252.0 gw 192.179.64.2
route add -net 192.179.8.0 netmask 255.255.255.252 gw 192.179.64.2
route add -net 192.179.36.0 netmask 255.255.252.0 gw 192.179.64.2
route add -net 192.179.32.0 netmask 255.255.254.0 gw 192.179.64.2
route add -net 192.179.34.0 netmask 255.255.255.240 gw 192.179.64.2
route add -net 192.179.16.0 netmask 255.255.255.252 gw 192.179.64.2

# kiri
route add -net 192.180.8.0 netmask 255.255.255.128 gw 192.180.64.1
route add -net 192.180.0.0 netmask 255.255.248.0 gw 192.180.64.1
route add -net 192.180.32.0 netmask 255.255.252.0 gw 192.180.64.1
route add -net 192.180.16.0 netmask 255.255.255.252 gw 192.180.64.1
```



### Kendala Pengerjaan

1. Pada awalnya masih bingung dengan aturan dan arah penggabungan subnet pada CIDR.
2. Pada GNS sempat ada yang salah menurunkan dan lumayan sulit untuk dideteksi jadi cukup memaka
n waktu

