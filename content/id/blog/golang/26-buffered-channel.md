---
title: "Tutorial Golang: Buffered Channel"
date: 2023-04-13T20:08:53+07:00
draft: false
author: "Adhika Guna"
thumbnail: /026-buffered-channel/thumbnail.png
description: "Belajar Buffered Channel pada Golang"
---



### Buffered Channel

Pada tulisan [sebelumnya](https://sekolahbackend.com/id/blog/golang/25-channel/) kita sudah belajar apa itu channel, dan bagaimana menggunakannya, dan di tulisan ini kita akan belajar apa itu Buffered Channel.

Buffered channel adalah jenis channel yang memiliki kapasitas tertentu untuk menampung data.

Pada dasarnya, buffered channel adalah jenis channel yang memungkinkan goroutine untuk mengirim data ke channel tanpa harus menunggu goroutine lainnya untuk menerima data dari channel tersebut. 

Ketika buffered channel telah mencapai kapasitas maksimumnya, goroutine yang mencoba mengirim data ke channel akan diblokir hingga ada goroutine lain yang mengambil data dari channel tersebut.


### Inisialisasi Buffered Channel
Inisialisasi Buffered Channel, sama dengan Channel hanya saja kita dapat menuliskan kapasitasnya pada parameter ke 2.

Berikut contohnya:
```golang
ch := make(chan int, 2)
````

Pada inisialisasi diatas kita membuat buffered channel dengan kapasitas 2.

### Contoh Penggunaan Buffered Channel

Dengan Buffered Channel goroutine dapat mengirim data ke channel lebih dari 1x.

Berikut contoh kodenya:
```golang
func main() {
    // membuat buffered channel dengan kapasitas 2
    ch := make(chan int, 2)

    // mengirim data ke buffered channel
    ch <- 1
    ch <- 2

    // mencetak data dari buffered channel
    fmt.Println(<-ch)
    fmt.Println(<-ch)
}
```

Berikut hasil eksekusi kode diatas: 
![image info](/026-buffered-channel/pict1.jpeg)

Pada contoh di atas, kita membuat buffered channel dengan kapasitas 2 dan mengirimkan 2 data ke channel tersebut menggunakan operator {{<singlelinecodeblock text="<-">}}. 

Kemudian, kita mengambil data dari channel tersebut menggunakan operator {{<singlelinecodeblock text="<-">}} dan mengprint data tersebut.

---

Lalu apakah Buffered channel dapat menerima data, lebih dari kapasitasnya?

Jawabannya adalah **tidak**, ketika channel menerima value lebih dari kapasitasnya goroutine akan diblokir, karena buffered channel sudah penuh.

Berikut contoh kodenya:
```golang
func main() {
    // membuat buffered channel dengan kapasitas 2
    ch := make(chan int, 2)

    // mengirim data ke buffered channel
    ch <- 1
    ch <- 2

    // mencoba mengirim data ke buffered channel yang sudah penuh
    // goroutine akan diblokir
    ch <- 3

    // mencetak data dari buffered channel
    fmt.Println(<-ch)
    fmt.Println(<-ch)
    fmt.Println(<-ch)
}
```

Berikut hasil eksekusi kode diatas:
![image info](/026-buffered-channel/pict2.jpeg)


Seperti kita lihat pada hasil eksekusi diatas, terjadi error, karena melebihi kapasitas dari channel.

Lalu bagaimana agar kode diatas tidak error?

Kita bisa menggunakan valuenya terlebih dahulu, baru kita assign lagi value ke 3-nya.


Berikut contohnya:
```golang
func main() {
	// membuat buffered channel dengan kapasitas 2
	ch := make(chan int, 2)

	// mengirim data ke buffered channel
	ch <- 1
	ch <- 2

	// gunakan value dari channel, agar channel bisa diisi kembali
	fmt.Println(<-ch)

	ch <- 3

	// mencetak data dari buffered channel
	fmt.Println(<-ch)
	fmt.Println(<-ch)
}
```
Berikut hasil eksekusi kode diatas:
![image info](/026-buffered-channel/pict3.jpg)


### Apa selanjutnya?
Selanjutnya kita akan belajar mengenai Channel tapi lebih advance lagi untuk materinya

Happy learning! 😆