---
title: "Tutorial Golang: Channel"
date: 2023-04-11T23:12:00+07:00
draft: false
author: "Adhika Guna"
thumbnail: /025-channel/thumbnail.png
description: "Belajar Channel pada Golang"
---

### Channel

Channel adalah fitur bawaan dalam Golang yang memungkinkan untuk komunikasi antara goroutine yang berbeda. 

Channel dapat dianggap sebagai saluran pipa tempat nilai dapat mengalir antara goroutine yang berbeda. 

Satu goroutine dapat mengirim nilai ke dalam channel, sedangkan goroutine lainnya dapat menerima nilai tersebut dari channel. 

Channel juga berguna untuk sinkronisasi, memungkinkan satu goroutine untuk menunggu hingga goroutine lain menyelesaikan tugas tertentu.

### Inisialisasi Channel
Dalam Golang, channel didefinisikan menggunakan kata kunci {{<singlelinecodeblock text="chan">}} , diikuti oleh tipe nilai yang akan dibawa oleh channel.

Misalnya, untuk membuat channel yang dapat membawa **integer**, kita akan menggunakan sintaks berikut:
```golang
ch := make(chan int)
```

### Menggunakan Channel

Ketika goroutine mengirim nilai ke dalam channel menggunakan operator {{<singlelinecodeblock text="<-">}}, nilai tersebut ditambahkan ke ujung antrian channel. 

Ketika goroutine menerima nilai dari channel menggunakan operator yang sama {{<singlelinecodeblock text="<-">}}, ia menghapus nilai pertama dari antrian dan mengembalikannya ke goroutine yang menerima.

Channel juga dapat digunakan untuk memberi sinyal ketika tugas tertentu telah selesai. 

Misalnya, jika kita memiliki dua goroutine yang perlu dijalankan dalam urutan tertentu, kita dapat menggunakan channel untuk menyinkronkannya. 

Goroutine pertama dapat mengirimkan sinyal ke channel ketika tugasnya selesai, sementara goroutine kedua dapat menunggu sinyal tersebut sebelum memulai tugasnya sendiri.

Berikut contoh penggunaan channel:

```golang
func main() {
    ch := make(chan bool) // membuat channel boolean

    // goroutine pertama
    go func() {
        fmt.Println("Goroutine pertama dimulai...")
        time.Sleep(2 * time.Second) // simulasi pekerjaan
        fmt.Println("Goroutine pertama selesai...")
        ch <- true // memberi sinyal bahwa pekerjaan selesai
    }()

    // goroutine kedua
    go func() {
        fmt.Println("Goroutine kedua menunggu...")
        <-ch // menunggu sinyal dari goroutine pertama
        fmt.Println("Goroutine kedua dimulai setelah goroutine pertama selesai...")
        time.Sleep(2 * time.Second) // simulasi pekerjaan
        fmt.Println("Goroutine kedua selesai...")
    }()

    // menunggu goroutine selesai
    time.Sleep(5 * time.Second)
    fmt.Println("Semua goroutine selesai!")
}
```

Berikut output kode diatas:
![image info](/025-channel/pict1.jpeg)

Dalam contoh diatas, goroutine pertama menunggu selama 2 detik, kemudian mengirimkan sinyal ke channel untuk memberi tahu goroutine kedua bahwa pekerjaannya selesai. 

Goroutine kedua kemudian menunggu sinyal dari channel sebelum memulai pekerjaannya sendiri. 

Akhirnya, program menunggu selama 5 detik sebelum mencetak pesan bahwa semua goroutine telah selesai.


### Apa selanjutnya?
Selanjutnya kita belajar mengenai Buffered Channel pada golang

Happy learning! 😆