---
title: "Tutorial Golang: WaitGroup"
date: 2023-04-24T15:50:20+07:00
draft: false
author: "Adhika Guna"
thumbnail: /033-waitgroup/thumbnail.png
description: "Belajar menggunakan WaitGroup pada Golang"
---

### WaitGroup

WaitGroup berasal dari package `sync` di Golang. 

`sync` adalah package yang berisi fitur-fitur sinkronisasi untuk mengatur akses ke data yang bersamaan di antara goroutine.

WaitGroup adalah salah satu fitur di Golang yang berguna untuk menunggu beberapa goroutine selesai sebelum melanjutkan eksekusi program. 

WaitGroup memungkinkan kita untuk menambahkan goroutine ke dalam grup dan menunggu sampai semua goroutine selesai dijalankan sebelum melanjutkan eksekusi.


### Pengunaan WaitGroup pada Go

Berikut adalah contoh penggunaan WaitGroup pada Go:
```golang
package main

import (
	"fmt"
	"sync"
)

func main() {
	var wg sync.WaitGroup

	for i := 1; i <= 5; i++ {
		wg.Add(1)
		go func(num int) {
			defer wg.Done()
			fmt.Printf("Goroutine %d selesai\n", num)
		}(i)
	}

	wg.Wait()
	fmt.Println("Semua goroutine selesai")
}

```

Pada contoh di atas, kita membuat sebuah `WaitGroup` dengan menginisialisasi variabel {{<code text="wg">}} dari {{<code text="sync.WaitGroup">}}. 

Kemudian, kita menambahkan 5 goroutine ke dalam grup menggunakan {{<code text="wg.Add(1)">}}. 

Setiap goroutine akan dijalankan di dalam sebuah anonymous function dengan memanggil {{<code text="go func()">}}.

Dalam setiap goroutine, kita menambahkan defer {{<code text="wg.Done()">}} untuk menandakan bahwa goroutine tersebut telah selesai dijalankan dan mengurangi jumlah goroutine dalam grup.

Setelah menambahkan semua goroutine ke dalam grup, kita menunggu semua goroutine selesai dijalankan dengan memanggil {{<code text="wg.Wait()">}}. 

Setelah semua goroutine selesai, kita mencetak pesan `"Semua goroutine selesai"`.

Dalam penggunaan WaitGroup, penting untuk memanggil {{<code text="wg.Add()">}} sebelum menjalankan goroutine dan {{<code text="wg.Done()">}} setelah goroutine selesai dijalankan. 

Jika tidak, maka program akan mengalami deadlock dan tidak akan berjalan dengan benar.

### Penggunaan WaitGroup pada case nyata

Penggunaan WaitGroup pada case nyata cukup banyak, salah satu yang paling simple adalah ketika kita ingin mengambil data dari beberapa sumber, kita dapat mempercepat proses pengambilan data dengan goroutine dan WaitGroup, semisal:
- source data A, butuh 2 detik
- source data B, butuh 2 detik

Jika dilakukan secara synchronously, akan memakan waktu `4 detik`.

Tapi jika dilakukan secara asynchronously, akan memakan waktu `2 detik`.

Berikut contoh kode menggunakan cara `synchronously`:
```golang
package main

import (
	"fmt"
	"time"
)

func main() {
	start := time.Now()

	data1 := getData1()
	fmt.Println(data1)

	data2 := getData2()
	fmt.Println(data2)

	fmt.Println("Semua data telah diambil")

	duration := time.Since(start)
	fmt.Println("Duration:", duration)

}

func getData1() string {
	// simulasi pengambilan data dari database atau API
	time.Sleep(2. * time.Second)
	return "Data dari function getData1"
}

func getData2() string {
	// simulasi pengambilan data dari database atau API
	time.Sleep(2 * time.Second)
	return "Data dari function getData2"
}
```

Hasil eksekusi kode diatas:
![image info](/033-waitgroup/pict1.jpeg)

Pada contoh diatas function {{<code text="getData1">}} membutuhkan 2 detik, dan {{<code text="getData2">}} membutuhkan 2 detik juga.

Jika mengeksekusi secara synchronously akan memakan waktu `4 detik`.


Berikut contoh menggunakan cara `asynchronously`:
```golang
package main

import (
	"fmt"
	"sync"
	"time"
)

func main() {
	var wg sync.WaitGroup
	start := time.Now()
	// Code to measure

	wg.Add(2) // menambahkan 2 goroutine ke dalam WaitGroup

	// Goroutine 1: mengambil data dari function getData1
	go func() {
		defer wg.Done() // menandakan bahwa goroutine telah selesai dijalankan
		data1 := getData1()
		fmt.Println(data1)
	}()

	// Goroutine 2: mengambil data dari function getData2
	go func() {
		defer wg.Done() // menandakan bahwa goroutine telah selesai dijalankan
		data2 := getData2()
		fmt.Println(data2)
	}()

	wg.Wait() // menunggu semua goroutine selesai dijalankan
	fmt.Println("Semua data telah diambil")

	duration := time.Since(start)
	fmt.Println("Duration:", duration)

}

func getData1() string {
	// simulasi pengambilan data dari database atau API
	time.Sleep(2. * time.Second)
	return "Data dari function getData1"
}

func getData2() string {
	// simulasi pengambilan data dari database atau API
	time.Sleep(2 * time.Second)
	return "Data dari function getData2"
}
```

Hasil eksekusi kode diatas:
![image info](/033-waitgroup/pict2.jpeg)

Pada contoh di atas, kita menambahkan dua goroutine ke dalam `WaitGroup` dengan memanggil {{<code text="wg.Add(2)">}}. 

Setiap goroutine akan dijalankan secara asynchronous menggunakan {{<code text="go func()">}} dan mengambil data dari function {{<code text="getData1">}} dan {{<code text="getData2">}}.

Dalam setiap goroutine, kita menandakan bahwa goroutine telah selesai dijalankan menggunakan defer {{<code text="wg.Done()">}}.

Setelah menambahkan semua goroutine ke dalam WaitGroup, kita menunggu semua goroutine selesai dijalankan dengan memanggil {{<code text="wg.Wait()">}}. 

Setelah semua goroutine selesai, kita mencetak pesan `"Semua data telah diambil"`.

Dalam pengambilan data secara asynchronous seperti ini, kita dapat menghemat waktu eksekusi program dengan mengambil data dari beberapa function secara bersamaan menggunakan goroutine. Dalam contoh diatas kita berhasil menghemat `2 detik`.



### Apa selanjutnya?
Selanjutnya kita akan belajar mengenai Mutex pada Golang

Happy learning! 😆
