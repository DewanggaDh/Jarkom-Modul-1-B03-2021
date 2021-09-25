# Jarkom-Modul-1-B03-2021

Jaringan Komputer B
Kelompok B3
-	Dewangga Dharmawan (05111940000029)
-	Ahmad Syafiq Aqil Wafi (05111940000089)
-	Nouvelli Cornelia (05111940000011)

## 1.	Sebutkan webserver yang digunakan pada "ichimarumaru.tech"! (nginx/1.18.0 (Ubuntu))

Filter:
	```https.host eq “ichimarumaru.tech” ```

![1](https://user-images.githubusercontent.com/55073331/134757528-3748d4c8-2ccb-4fb8-a656-f4762c6c2812.jpg)

![1b](https://user-images.githubusercontent.com/55073331/134757534-a08b09ad-25de-4b97-8b30-325dc3cdc95d.jpg)

## 2.	Temukan paket dari web-web yang menggunakan basic authentication method!

Filter:
```http.authbasic```

![2](https://user-images.githubusercontent.com/55073331/134757537-5e765ae2-541f-4be5-8e57-28fda2bea03e.jpg)

 
## 3.	Ikuti perintah di basic.ichimarumaru.tech! Username dan password bisa didapatkan dari file .pcapng!

Filter:
```http.host eq "basic.ichimarumaru.tech" and http.authbasic```

```
Username : kuncimenujulautan
Password : tQKEJFbgNGC1NCZlWAOjhyCOm6o3xEbPkJhTciZN
```


![3](https://user-images.githubusercontent.com/55073331/134757538-5ab286a6-3b33-46bc-9447-43fe831f60d1.jpg)

Setelah masuk ke laman berikutnya 

![3b](https://user-images.githubusercontent.com/55073331/134757539-0293af32-3bdc-41d7-aac3-95da32e10f84.jpg)

## 4.	Temukan paket mysql yang mengandung perintah query select!

Filter:
```mysql.query == “select” ```
![4](https://user-images.githubusercontent.com/55073331/134757540-34ad1c70-19cc-4a2a-8033-b66dae055f47.jpg)

Maka akan ditampilkan sesuai filter
 

## 5.	Login ke portal.ichimarumaru.tech kemudian ikuti perintahnya! Username dan password bisa didapat dari query insert pada table users dari file .pcap!

Filter:
``` mysql ```

![5](https://user-images.githubusercontent.com/55073331/134757542-5210f0eb-1741-44be-a681-1c5791154466.jpg)

```
Username: akakanomi
Password: pemisah4lautan
```
![5b](https://user-images.githubusercontent.com/55073331/134757544-e3744bc5-e1df-44ba-a174-193d106afcb8.jpg)


## 10. Selain itu terdapat "history.txt" yang kemungkinan berisi history bash server tersebut! Gunakan isi dari "history.txt" untuk menemukan password untuk membuka file rahasia yang ada di "secret.zip"!

Filter : ftp-data and ftp-data.command contains ".txt"

<img src="https://user-images.githubusercontent.com/73766205/134611025-6081de7b-ea7b-4c15-8000-41d930a8e054.png" height="25%" widht="25%">

<img src="https://user-images.githubusercontent.com/73766205/134611076-bee2956b-a949-4fee-8cd8-147ede5548d1.png" height="25%" widht="25%">

<img src="https://user-images.githubusercontent.com/73766205/134611540-4f2a956e-3a36-4041-8628-8b95b24f5415.png" height="25%" widht="25%">

<img src="https://user-images.githubusercontent.com/73766205/134611554-25cf3d10-0b83-446b-aa52-ab3245882131.png" height="25%" widht="25%">

Password Zip : d1b1langbukanapaapajugagapercaya

<img src="https://user-images.githubusercontent.com/73766205/134611575-6bf386c3-f828-4528-b958-383e93a74d90.png" height="25%" widht="25%">

## 11.Filter sehingga wireshark hanya mengambil paket yang berasal dari port 80!

Filter:
tcp.srcport == 80

<img src="https://user-images.githubusercontent.com/73766205/134611863-6691920d-9b39-41f5-9e32-b1b8154f5c5c.png" height="25%" widht="25%">

## 12.	Filter sehingga wireshark hanya mengambil paket yang mengandung port 21!

Filter:
tcp.port == 21

<img src="https://user-images.githubusercontent.com/73766205/134611912-fb51ad83-6f45-4f20-9c5d-1720b14ca25c.png" height="25%" widht="25%">

## 13.	Filter sehingga wireshark hanya menampilkan paket yang menuju port 443!

Filter:
tcp.dstport == 443

<img src="https://user-images.githubusercontent.com/73766205/134611954-f04ca124-7ae9-4723-b92b-8512d5405ee5.png" height="25%" widht="25%">

## 14.	Filter sehingga wireshark hanya mengambil paket yang tujuannya ke kemenag.go.id!

Filter:
tcp contains "kemenag" and ip.src == 192.168.1.3

<img src="https://user-images.githubusercontent.com/73766205/134768765-6f1981c9-cf49-41c0-bfc6-dbe7319eeace.png" height="25%">


## 15.	Filter sehingga wireshark hanya mengambil paket yang berasal dari ip kalian!
membuka cmd untuk mengetahui ip dengan ‘ipconfig’
kemudian ip.src di wireshark 

Pertama, cari alamat IPv4 melalui CmD

![image](https://user-images.githubusercontent.com/73766205/134768812-8117b79c-6faa-427f-a23f-6f74e9b24b6e.png)

Ditemukan alamat 92.168.1.3

Filter:
ip.src == 192.168.1.3

<img src="https://user-images.githubusercontent.com/73766205/134612245-8bf01282-f0a6-45c7-8f2a-60ccec8fda38.png" height="25%" widht="25%">
