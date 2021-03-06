# Jarkom-Modul-1-B03-2021

Jaringan Komputer B
Kelompok B3
-	Dewangga Dharmawan (05111940000029)
-	Ahmad Syafiq Aqil Wafi (05111940000089)
-	Nouvelli Cornelia (05111940000011)

## 1.	Sebutkan webserver yang digunakan pada "ichimarumaru.tech"! (nginx/1.18.0 (Ubuntu))

Filter:
	```http.host eq “ichimarumaru.tech” ```

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
```mysql contains SELECT ```

![image](https://user-images.githubusercontent.com/73766205/134773069-7f3a1a7e-1698-4aa8-ba18-8636779fcc91.png)

Maka akan ditampilkan sesuai filter
 
## 5.	Login ke portal.ichimarumaru.tech kemudian ikuti perintahnya! Username dan password bisa didapat dari query insert pada table users dari file .pcap!

Filter:
``` mysql contains INSERT ```

![image](https://user-images.githubusercontent.com/73766205/134773040-ea49b79d-a14e-4014-9e84-8a7c3d071ae2.png)

```
Username: akakanomi
Password: pemisah4lautan
```

![5b](https://user-images.githubusercontent.com/55073331/134757544-e3744bc5-e1df-44ba-a174-193d106afcb8.jpg)

## 6. Cari username dan password ketika melakukan login ke FTP Server!

Untuk melakukan filter FTP maka kita gunakan filter `ftp`.

Karena yang dicari merupakan info login, maka terjadi request login ke ftp jadi kita gunakan filter `ftp.request`.

Karena mencari user untuk login ftp maka kita cari command USER menggunakan filter `ftp.request.command == USER`

Karena mencari password untuk login ftp maka kita cari command PASS menggunakan filter `ftp.request.command == PASS`

Sehingga kita gabungkan filter tersebut menjadi berikut.

```
ftp.request.command == USER || ftp.request.command == PASS
```

Sehingga didapatkan hasil sebagai berikut.

![6a](Images/6a.png)

Sehingga informasi user ftp dapat diambil kesimpulan sebagai berikut.

```
username: secretuser
password: aku.pengen.pw.aja
```

## 7. Ada 500 file zip yang disimpan ke FTP Server dengan nama 0.zip, 1.zip, 2.zip, ..., 499.zip. Simpan dan Buka file pdf tersebut. (Hint = nama pdf-nya "Real.pdf")

Untuk melakukan filter upload sebuah file ftp maka kita gunakan filter `ftp.data`.

Karena diketahui yang dicari adalah file `.zip` maka kita cari yang terdapat perintah ".zip" maka kita gunakan filter berikut.

```
ftp-data and ftp-data.command contains ".zip"
```

Sehingga didapatkan hasil sebagai berikut.

![7a](Images/7a.png)

Karena terdapat banyak sekali file `.zip` dan tidak dimungkinkan untuk mencari satu - satu pada setiap packet nya. Maka kita manfaatkan fitur filter packet bytes dan mencari file dengan nama "Real.pdf".

Untuk melakukan filter packet kita buka menu nya dari Edit > Find Packet. Lalu pilih settings filter Packet Bytes dengan tipe String. Untuk mempermudah kita matikan pencarian secara Case Sensitive. Lalu filter "Real.pdf". Sehingga didapatkan hasil sebagai berikut.

![7b](Images/7b.png)

Dapat terlihat bahwa yang memiliki string "Real.pdf" adalah file "200.zip" dan "201.zip". Sehingga kita perlu periksa kedua file tersebut. Namun untuk lebih sederhana, kami telah memeriksa kedua file dan file ada pada file "201.zip" sehingga kami hanya menjelaskan file "201.zip".

Karena kita tahu file ada pada "201.zip" maka lakukan filter file tersebut menggunakan filter berikut.

```
ftp-data and ftp-data.command contains "201.zip"
```

![7c](Images/7c.png)

Pada hasil filter file "201.zip" yang paling pertama lakukan Follow TCP Stream.

Lalu kita extract / download packet tersebut dan menyimpannya pada suatu directory. Lakukan settings sebelum menyimpan file dengan lakukan save Entire Conversation, Show and Save data as Raw lalu Save As dan beri nama "Real.pdf".

![7d](Images/7d.png)

Langkah terakhir buka file tersebut.

![7e](Images/7e.png)

## 8. Cari paket yang menunjukan pengambilan file dari FTP tersebut!

Pada pengambilan packet FTP berarti terjadi proses download dari FTP yang berarti menggunakan command RETR.

Untuk melakukan filter pengambilan packet ftp maka kita gunakan filter berikut.

```
ftp contains RETR
```

Dapat dilihat bahwa tidak ada packet pengambilan data dari FTP yang terjadi.

![8a](Images/8a.png)

## 9. Dari paket-paket yang menuju FTP terdapat indikasi penyimpanan beberapa file. Salah satunya adalah sebuah file berisi data rahasia dengan nama "secret.zip". Simpan dan buka file tersebut!

Untuk melakukan filter upload sebuah file ftp maka kita gunakan filter `ftp.data`.

Karena diketahui yang dicari adalah file `.zip` maka kita cari yang terdapat perintah ".zip" maka kita gunakan filter berikut.

```
ftp-data and ftp-data.command contains "secret.zip"
```

Sehingga didapatkan hasil sebagai berikut.

![9a](Images/9a.png)

Pada hasil filter file "secret.zip" yang paling pertama lakukan Follow TCP Stream.

Lalu kita extract / download packet tersebut dan menyimpannya pada suatu directory. Lakukan settings sebelum menyimpan file dengan lakukan save Entire Conversation, Show and Save data as Raw lalu Save As dan beri nama "secret.zip".

![9b](Images/9b.png)

Langkah terakhir buka file tersebut.

![9c](Images/9c.png)

## 10. Selain itu terdapat "history.txt" yang kemungkinan berisi history bash server tersebut! Gunakan isi dari "history.txt" untuk menemukan password untuk membuka file rahasia yang ada di "secret.zip"!

Filter : ftp-data and ftp-data.command contains ".txt"

<img src="https://user-images.githubusercontent.com/73766205/134611025-6081de7b-ea7b-4c15-8000-41d930a8e054.png">

Ada dua file, history.txt dan bukanapaapa.txt. Pertama follow TCP paket berisi history.txt sehingga ditemukan riwayat perubahan sebuah file secret.zip, yang mana passwordnya diubah menurut apa yang ada di dalam file bukanapaapa.txt.

<img src="https://user-images.githubusercontent.com/73766205/134611076-bee2956b-a949-4fee-8cd8-147ede5548d1.png">

Lalu difollow TCP paket berisi bukanapaapa.txt sehingga ditemukan isi filenya.

<img src="https://user-images.githubusercontent.com/73766205/134611540-4f2a956e-3a36-4041-8628-8b95b24f5415.png">

<img src="https://user-images.githubusercontent.com/73766205/134611554-25cf3d10-0b83-446b-aa52-ab3245882131.png">

Password Zip : d1b1langbukanapaapajugagapercaya

Untuk membuka zip tersebut, dimasukkan password diatas untuk membuka gambar png berikut.

<img src="https://user-images.githubusercontent.com/73766205/134611575-6bf386c3-f828-4528-b958-383e93a74d90.png">

## 11.Filter sehingga wireshark hanya mengambil paket yang berasal dari port 80!

Filter:
tcp.srcport == 80

<img src="https://user-images.githubusercontent.com/73766205/134768901-db51ca6f-872c-4895-9fc6-0464510b56cd.png" height="%25">

## 12.	Filter sehingga wireshark hanya mengambil paket yang mengandung port 21!

Filter:
tcp.port == 21

<img src="https://user-images.githubusercontent.com/73766205/134768978-c384431a-0f23-4d1c-916c-41e589b2c35a.png" height="25%">

## 13.	Filter sehingga wireshark hanya menampilkan paket yang menuju port 443!

Filter:
tcp.dstport == 443

![image](https://user-images.githubusercontent.com/73766205/134769026-d00f3d54-bd3a-45f4-a683-72f21ed2ab3e.png)

## 14.	Filter sehingga wireshark hanya mengambil paket yang tujuannya ke kemenag.go.id!

Filter:
tcp contains "kemenag" and ip.src == 192.168.1.3

<img src="https://user-images.githubusercontent.com/73766205/134768765-6f1981c9-cf49-41c0-bfc6-dbe7319eeace.png" height="25%">

## 15.	Filter sehingga wireshark hanya mengambil paket yang berasal dari ip kalian!
membuka cmd untuk mengetahui ip dengan ‘ipconfig’
kemudian ip.src di wireshark 

Pertama, cari alamat IPv4 melalui CmD

![image](https://user-images.githubusercontent.com/73766205/134768812-8117b79c-6faa-427f-a23f-6f74e9b24b6e.png)

Ditemukan alamat 192.168.1.3

Filter:
ip.src == 192.168.1.3

<img src="https://user-images.githubusercontent.com/73766205/134612245-8bf01282-f0a6-45c7-8f2a-60ccec8fda38.png">
