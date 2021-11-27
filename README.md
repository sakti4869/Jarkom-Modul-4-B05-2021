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

Langkah 3 : Mengatur konfigurasi pada router

| Router  | Network | Mask  | Next Hop |
| ------------- | ------------- | ------------- | ------------- |
| Foosha | 192.179.12.0<br>192.179.0.0<br>0.0.0.0<br>192.179.27.0<br>192.179.27.144 | 255.255.252.0<br>255.255.248.0<br>0.0.0.0<br>255.255.252.128<br>255.255.255.252 | 192.179.27.149<br>192.179.27.149<br>192.179.27.154<br>192.179.27.149<br>192.179.27.149 |
| Water7 | 0.0.0.0<br>192.179.27.0<br>192.179.0.0 | 0.0.0.0<br>255.255.252.128<br>255.255.248.0 | 192.179.27.150<br>192.179.27.146<br>192.179.27.146 |
| Pucci | 0.0.0.0 | 0.0.0.0 | 192.179.27.145 |
| Guanhao | 0.0.0.0<br>192.179.27.128<br>192.179.20.0<br>192.179.26.0<br>192.179.27.164 | 0.0.0.0<br>255.255.255.240<br>255.255.252.0<br>255.255.255.0<br>255.255.255.252 | 192.179.27.153<br>192.179.24.2<br>192.179.27.157<br>192.179.27.157<br>192.179.27.157 |
