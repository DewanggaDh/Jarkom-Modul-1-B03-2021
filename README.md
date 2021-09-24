# Jarkom-Modul-1-B03-2021

Ada 15 soal, dibagi jadi 3

Kalau mau mengecilkan gambar

//<< img src=link height= widht= >>

10. Selain itu terdapat "history.txt" yang kemungkinan berisi history bash server tersebut! Gunakan isi dari "history.txt" untuk menemukan password untuk membuka file rahasia yang ada di "secret.zip"!

Filter : ftp-data and ftp-data.command contains ".txt"
<img src="https://user-images.githubusercontent.com/73766205/134611025-6081de7b-ea7b-4c15-8000-41d930a8e054.png" height="25%" widht="25%">

<img src="https://user-images.githubusercontent.com/73766205/134611076-bee2956b-a949-4fee-8cd8-147ede5548d1.png" height="25%" widht="25%">

<img src="https://user-images.githubusercontent.com/73766205/134611540-4f2a956e-3a36-4041-8628-8b95b24f5415.png" height="25%" widht="25%">

<img src="https://user-images.githubusercontent.com/73766205/134611554-25cf3d10-0b83-446b-aa52-ab3245882131.png" height="25%" widht="25%">

Password Zip : d1b1langbukanapaapajugagapercaya

<img src="https://user-images.githubusercontent.com/73766205/134611575-6bf386c3-f828-4528-b958-383e93a74d90.png" height="25%" widht="25%">

11.Filter sehingga wireshark hanya mengambil paket yang berasal dari port 80!

Filter:
tcp.srcport == 80

<img src="https://user-images.githubusercontent.com/73766205/134611863-6691920d-9b39-41f5-9e32-b1b8154f5c5c.png" height="25%" widht="25%">

12.	Filter sehingga wireshark hanya mengambil paket yang mengandung port 21!

Filter:
tcp.port == 21

<img src="https://user-images.githubusercontent.com/73766205/134611912-fb51ad83-6f45-4f20-9c5d-1720b14ca25c.png" height="25%" widht="25%">

13.	Filter sehingga wireshark hanya menampilkan paket yang menuju port 443!

Filter:
tcp.dstport == 443

<img src="https://user-images.githubusercontent.com/73766205/134611954-f04ca124-7ae9-4723-b92b-8512d5405ee5.png" height="25%" widht="25%">

14.	Filter sehingga wireshark hanya mengambil paket yang tujuannya ke kemenag.go.id!

Filter:
https.host contains “kemenag”

<img src="https://user-images.githubusercontent.com/73766205/134612107-6f494300-52a3-4cfd-bb03-1c6efe17f30b.png" height="25%" widht="25%">

15.	Filter sehingga wireshark hanya mengambil paket yang berasal dari ip kalian!
membuka cmd untuk mengetahui ip dengan ‘ipconfig’
kemudian ip.src di wireshark 

Filter:
ip.src == 192.68.1.3

<img src="https://user-images.githubusercontent.com/73766205/134612245-8bf01282-f0a6-45c7-8f2a-60ccec8fda38.png" height="25%" widht="25%">
