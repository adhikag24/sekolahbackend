---
title: "Tutorial Golang: Mutex"
date: 2023-04-25T22:55:11+07:00
draft: false
author: "Adhika Guna"
thumbnail: /034-mutex/thumbnail.png
description: "Belajar mengenai Mutex pada Golang"
---



### Mutex

Mutex (Mutual Exclusion) adalah sebuah mekanisme yang digunakan dalam pemrograman untuk mengontrol akses ke sumber daya bersama (shared resource) yang digunakan oleh dua atau lebih thread secara bersamaan. 

Dalam sebuah program yang menggunakan thread, Mutex memastikan bahwa hanya satu thread yang dapat mengakses sumber daya bersama pada suatu waktu. Saat satu thread mendapatkan akses ke sumber daya bersama, Mutex akan mengunci (lock) sumber daya tersebut, sehingga thread lain harus menunggu sampai sumber daya tersebut dilepaskan (unlock) sebelum dapat mengaksesnya. 

Dengan demikian, Mutex membantu mencegah terjadinya race condition, deadlock, dan masalah lain yang dapat terjadi ketika dua atau lebih thread mencoba mengakses sumber daya bersama secara bersamaan.

### Race condition dalam Go

Sebelum lebih lanjut, ada baiknya kita memahami terlebih dahulu, apa itu race condition, dan bagaimana kita mengetahui jika program kita mengalami race condition.

Race condition dalam Go terjadi ketika dua atau lebih goroutine mencoba mengakses dan memanipulasi variabel yang sama secara bersamaan dan tidak terkoordinasi. 

Hal ini dapat terjadi ketika variabel tersebut diakses oleh dua goroutine atau lebih tanpa adanya mekanisme pengamanan untuk mengontrol akses ke variabel tersebut. 

Akibatnya, nilai variabel tersebut dapat berubah secara tidak terduga atau tidak sesuai dengan yang diharapkan, karena tidak ada jaminan urutan eksekusi dari goroutine yang bersangkutan.

Race condition adalah masalah umum pada program konkuren seperti yang umumnya ditulis dalam Go, di mana banyak goroutine dapat menjalankan kode secara bersamaan. 

Race condition dapat menyebabkan masalah seperti deadlock, livelock, dan masalah data inconsistency.

### Cara mengetahui jika program kita mengalami race condition

Untuk mengecek apakah ada race condition pada kode Go, kita dapat menggunakan tool bawaan Go yaitu race detector. 

Race detector adalah fitur yang disediakan oleh Go untuk mendeteksi race condition pada kode Go.

Untuk menggunakan race detector, Anda dapat menambahkan flag `-race` pada command `go build`, `go test`, atau `go run`.

Sebagai contoh, jika Anda ingin mengecek race condition pada file `main.go`, Anda dapat menggunakan command 
```bash
go run -race main.go
```

Berikut contoh output jika program terdeteksi race condition:
![image info](/034-mutex/pict1.jpeg)

Jika terdapat race condition pada kode, race detector akan memberikan output yang menunjukkan letak terjadinya race condition dan goroutine mana yang terlibat dalam race condition.


### Contoh kode yang mengalami race condition
Berikut contoh kode dalam Go yang mengalami race condition:
```golang
package main

import (
	"fmt"
	"sync"
)

var (
	counter = 0
)

func main() {
	var wg sync.WaitGroup
	for i := 0; i < 10; i++ {
		wg.Add(1)
		go incrementCounter(&wg)
	}
	wg.Wait()
	fmt.Println("Final Counter:", counter)
}

func incrementCounter(wg *sync.WaitGroup) {
	defer wg.Done()
	counter++
	fmt.Println("Counter:", counter)
}
```

Pada contoh diatas, variabel {{<code text="counter">}} tetap digunakan sebagai sumber daya bersama yang dapat diakses oleh 10 goroutine, tetapi tidak ada mekanisme pengamanan yang digunakan untuk mengontrol akses ke variabel {{<code text="counter">}}.  

Sehingga menyebabkan terjadinya race condition.

### Penggunaan Mutex dalam Go

Pada contoh diatas, program kita mengalami race condition, sekarang kita akan mencoba mengatasinya dengan Mutex.

Dalam Go, kita dapat menggunakan package `sync` untuk membuat Mutex.

Berikut adalah kode race condition yang sudah diperbaiki dengan menggunakan Mutex:
```golang
package main

import (
    "fmt"
    "sync"
)

var counter int
var mutex = &sync.Mutex{}

func main() {
    var wg sync.WaitGroup
    for i := 0; i < 10; i++ {
        wg.Add(1)
        go incrementCounter(&wg)
    }
    wg.Wait()
    fmt.Println("Counter:", counter)
}

func incrementCounter(wg *sync.WaitGroup) {
    mutex.Lock()
    defer mutex.Unlock()
    counter++
    fmt.Println("Counter:", counter)
    wg.Done()
}
```
Hasil eksekusi kode diatas:
![image info](/034-mutex/pict2.jpeg)

Seperti kita lihat hasil eksekusi kode diatas, tidak terjadi race condition, dan data counter menjadi konsisten.

Penjelasan kodenya:

Pada contoh di atas, kita menggunakan variabel {{<code text="counter">}} sebagai contoh sumber daya yang perlu diakses secara eksklusif. 

Kita membuat variabel {{<code text="mutex">}} sebagai instance dari {{<code text="sync.Mutex">}}, yang akan kita gunakan untuk mengamankan akses ke sumber daya ini.

Kemudian, kita menggunakan package "sync" untuk membuat instance dari sync.WaitGroup. Kita menggunakan sync.WaitGroup untuk menunggu hingga semua goroutine selesai dijalankan sebelum program berakhir.

Dalam fungsi {{<code text="incrementCounter">}}, kita menggunakan {{<code text="mutex.Lock()">}} untuk mengamankan akses ke variabel {{<code text="counter">}}, sehingga hanya satu goroutine yang dapat mengakses variabel ini pada satu waktu. 

Setelah operasi selesai dilakukan, kita menggunakan {{<code text="mutex.Unlock()">}} untuk membebaskan Mutex.

Dalam `loop for` di fungsi `main`, kita membuat 10 goroutine yang masing-masing akan memanggil fungsi {{<code text="incrementCounter">}}. 

Kita menggunakan {{<code text="sync.WaitGroup">}} untuk menunggu hingga semua goroutine selesai dijalankan sebelum mencetak nilai variabel {{<code text="counter">}}.

Dengan menggunakan teknik Mutex, kita dapat memastikan bahwa variabel {{<code text="counter">}} hanya diakses oleh satu goroutine pada satu waktu, sehingga mencegah data race dan menjaga konsistensi data.


### Apa selanjutnya?
Selanjutnya kita akan belajar mengenai Testing pada Golang

Happy learning! 😆
