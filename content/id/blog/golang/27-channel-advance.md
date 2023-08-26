---
title: "Tutorial Golang: Channel - Advance"
date: 2023-04-15T11:07:38+07:00
draft: false
author: "Adhika Guna"
thumbnail: /027-channel-advance/thumbnail.png
description: "Belajar mengenai fitur-fitur channel pada Golang"
---


### Intro

Dalam tulisan sebelumnya kita sudah belajar mengenai Channel dan Buffered Channel, dalam tulisan kali ini kita akan belajar beberapa fitur channel yang dapat kita gunakan seperti:
- Select
- Range & Close
- Timeout



### Select

`Select` memungkinkan kita untuk melakukan operasi pada beberapa channel secara bersamaan dalam program Golang kita. 

Untuk melakukan ini, Golang menyediakan statement `select` yang memungkinkan kita untuk menunggu operasi pada beberapa channel sekaligus.

Pertama, kita mendefinisikan beberapa channel yang ingin kita operasikan menggunakan statement {{<singlelinecodeblock text="make">}}. 

Misalnya, kita punya dua channel, {{<singlelinecodeblock text="ch1">}} dan {{<singlelinecodeblock text="ch2">}}.

```golang
ch1 := make(chan int)
ch2 := make(chan int)
```

Kita ingin menunggu operasi pada kedua channel tersebut sebelum melanjutkan program. Untuk melakukan ini, kita menggunakan statement `select`. 

Statement ini menunggu hingga salah satu dari operasi pada channel-channels tersebut siap.

```golang
select {
case msg1 := <-ch1:
    fmt.Println("menerima dari ch1", msg1)
case msg2 := <-ch2:
    fmt.Println("menerima dari ch2", msg2)
}
```
Dalam kode diatas kita menunggu hingga salah satu dari operasi berikut siap:
- menerima data dari {{<singlelinecodeblock text="ch1">}}
- menerima data dari {{<singlelinecodeblock text="ch2">}}

Ketika operasi pada salah satu channel siap, blok kode dalam case yang sesuai akan dieksekusi. 

Sebagai contoh, jika data tersedia di {{<singlelinecodeblock text="ch1">}}, maka blok kode dalam case pertama akan dijalankan. 

Demikian juga, jika data tersedia di {{<singlelinecodeblock text="ch2">}}, maka blok kode dalam case kedua akan dijalankan.

Berikut contoh full kodenya:
```golang

func main() {
	ch1 := make(chan string)
	ch2 := make(chan string)

	go func() {
		time.Sleep(1 * time.Second)
		ch1 <- "hello"
	}()

	go func() {
		time.Sleep(2 * time.Second)
		ch2 <- "world"
	}()

	for i := 0; i < 2; i++ {
		select {
		case msg1 := <-ch1:
			fmt.Println(msg1)
		case msg2 := <-ch2:
			fmt.Println(msg2)
		}

		fmt.Println("Check")
	}
}
```

Berikut hasil eksekusi kode diatas:
![image info](/027-channel-advance/pict1.jpeg)

Dalam kode diatas kita menunggu value dari {{<singlelinecodeblock text="ch1">}} lalu mengprint {{<singlelinecodeblock text="Check">}} untuk menandakan bahwa operasi dalam `select` sudah terpenuhi dan terus berlanjut sampai value dari {{<singlelinecodeblock text="ch2">}}.


### Range & Close

Dalam program Golang, penggunaan channel sangat umum dalam pemrograman konkuren. 

Ketika kita mengirim atau menerima data melalui channel, kita harus mengetahui apakah channel tersebut sudah ditutup atau belum. 

Salah satu cara untuk mengetahuinya adalah dengan menggunakan statement range.

Ketika kita melakukan operasi range pada channel, operasi tersebut akan berjalan hingga channel tersebut ditutup. 

Misalnya, kita punya sebuah {{<singlelinecodeblock text="channel ch">}} dan kita ingin mengirimkan beberapa data ke channel tersebut.

```golang
ch := make(chan int)
go func() {
    for i := 0; i < 5; i++ {
        ch <- i
    }
}()
```
Di sini, kita mengirimkan nilai `0`, `1`, `2`, `3`, dan `4` ke dalam {{<singlelinecodeblock text="channel ch">}}. 

Namun, bagaimana jika kita ingin membaca data dari channel tersebut? Kita bisa menggunakan statement {{<singlelinecodeblock text="range">}} untuk melakukan ini.
```golang
for val := range ch {
    fmt.Println("menerima data dari channel", val)
}
```

Di sini, kita menggunakan range untuk membaca nilai dari {{<singlelinecodeblock text="channel ch">}}. 

Loop for akan berjalan hingga channel tersebut ditutup, yang berarti operasi range pada {{<singlelinecodeblock text="channel ch">}}.  telah selesai. 

Ketika operasi tersebut selesai, loop for juga akan berhenti.

Untuk menutup channel, kita bisa menggunakan statement {{<singlelinecodeblock text="close">}}. . 

Ketika channel ditutup, tidak akan mungkin lagi untuk mengirimkan data ke dalam channel tersebut. 

Namun, kita masih bisa membaca data dari channel tersebut.

```golang
close(ch)
```

Dalam contoh ini, kita menutup {{<singlelinecodeblock text="channel ch">}} setelah mengirimkan semua nilai ke dalam channel tersebut. Setelah channel ditutup, loop `for` pada statement `range` akan berhenti dan program akan keluar.

Jadi, penggunaan statement `range` pada channel memungkinkan kita untuk membaca data dari channel hingga channel tersebut ditutup. 

Kita juga harus menutup channel ketika tidak memerlukan lagi untuk mengirimkan data ke dalamnya.

Berikut contoh kode lengkapnya:
```golang
func main() {
	ch := make(chan int)

	go func() {
		for i := 0; i < 5; i++ {
			ch <- i
			fmt.Println("udah assign")
		}
		close(ch)
	}()

	for val := range ch {
		fmt.Println("menerima data dari channel", val)
	}
}
```

Berikut hasil eksekusi kode diatas:
![image info](/027-channel-advance/pict2.jpeg)


### Timeout
Dalam penggunaan channel, sangat umum jika pengiriman atau penerimaan data melalui channel mungkin terjebak dalam situasi yang tidak berakhir, seperti blocking yang tidak terduga atau kegagalan komunikasi.

Untuk menghindari masalah tersebut, Golang menyediakan fitur timeout pada channel.

Dalam konteks channel, timeout berarti kita menetapkan batas waktu tertentu untuk menerima data dari channel. 
 
Jika batas waktu tersebut terlampaui, program akan keluar dari loop atau menampilkan pesan kesalahan.
 

 Berikut adalah contoh penggunaan timeout pada channel di Golang:
 ```golang
func main() {
	ch := make(chan string)

	// Goroutine untuk mengirim data ke dalam channel setelah 2 detik
	go func() {
		time.Sleep(2 * time.Second)
		ch <- "data telah dikirim"
	}()

	// Menunggu data dari channel, timeout setelah 1 detik
	select {
	case res := <-ch:
		fmt.Println(res)
	case <-time.After(1 * time.Second):
		fmt.Println("timeout")
	}
}
```

Berikut hasil eksekusi kode diatas:
![image info](/027-channel-advance/pict3.jpeg)


Dalam contoh ini, kita membuat sebuah {{<singlelinecodeblock text="channel ch">}} dan mengirimkan data ke dalam channel tersebut setelah 2 detik menggunakan goroutine. 

Selanjutnya, kita menunggu data dari channel menggunakan statement `select`.

Namun, kita menetapkan batas waktu untuk menerima data dari channel menggunakan fungsi {{<singlelinecodeblock text="time.After()">}}.

Dalam contoh ini, batas waktu adalah 1 detik. Jika waktu yang ditetapkan terlampaui, program akan keluar dari loop dan menampilkan pesan `timeout`.

Jika data diterima dari channel sebelum batas waktu yang ditetapkan, program akan mencetak nilai dari channel tersebut ke konsol.

Jadi, dengan menggunakan `timeout` pada channel, kita dapat memastikan bahwa program tidak terjebak dalam situasi yang tidak berakhir saat mengirim atau menerima data melalui channel. 

Hal ini sangat berguna dalam pemrograman konkuren untuk menghindari masalah blocking atau kegagalan komunikasi.

### Apa selanjutnya?
Selanjutnya kita akan belajar mengenai Defer, Panic & Recover pada Golang

Happy learning! 😆

