---
title: "Tutorial Golang: Public and Private"
date: 2023-03-30T20:55:34+07:00
draft: false
author: "Adhika Guna"
thumbnail: /020-public-private/thumbnail.png
description: "Belajar Public dan Private pada Golang"
---


### Package

Sebelum belajar apa itu Public dan Private pada Go, ada baiknya kita memahami apa itu Package pada golang.

Di Go, package adalah cara untuk mengatur file source kode Go agar saling terikat. 

Setiap program Go terdiri dari satu atau lebih package, dengan satu paket ditetapkan sebagai package utama. 

Package utama adalah pintu masuk program dan berisi fungsi {{<singlelinecodeblock text="main()">}} yang dijalankan pertama kali saat program dijalankan.

Sebuah package juga dapat digunakan oleh package lain dengan mengimpornya. Kata kunci {{<singlelinecodeblock text="import">}} digunakan untuk memasukkan sebuah paket ke dalam package lain. 

Package yang diimpor kemudian dapat digunakan untuk mengakses fungsi, variabel, dan tipe yang diekspor.

### Public dan Private

Dalam Go, konsep public dan private menentukan visibilitas identifier. Identifier adalah nama yang diberikan pada variabel, fungsi, tipe data, atau entity lainnya di Go.

Identifier public adalah identifier yang diawali dengan huruf besar. Identifier public bisa diakses oleh package lain dan terlihat dari luar package di mana ia dideklarasikan. 

>Identifier public juga sering disebut sebagai exported identifier.

Contohnya, pada kode berikut, {{<singlelinecodeblock text="MyFunction">}} dan {{<singlelinecodeblock text="MyVariable">}} adalah identifier public karena diawali dengan huruf besar:
```golang
package mypackage

func MyFunction() {
  // ...
}

var MyVariable string = "Hello, World!"
```

Sedangkan identifier private, diawali dengan huruf kecil. Identifier private hanya bisa diakses di dalam package di mana ia dideklarasikan dan tidak bisa diakses oleh package lain. 

>Identifier private juga sering disebut sebagai unexported identifier.

Contohnya, pada kode berikut, myFunction dan myVariable adalah identifier private karena diawali dengan huruf kecil:
```golang
package mypackage

func myFunction() {
  // ...
}

var myVariable string = "Hello, World!"
```


### Hands-on Public dan Private pada Go

Untuk memahami Public dan Private pada go, lebih mudah dipahami jika kita mencobanya langsung.

1. Buat folder baru, bebas namanya disini saya pakai `belajar-golang`
![image info](/020-public-private/pict1.jpg)

2. Jalankan go mod init sesuai nama project kalian, kalau saya seperti ini {{<singlelinecodeblock text="go mod init belajar-golang">}}

3. Buat file {{<singlelinecodeblock text="main.go">}}, dengan package main dan function main yang kosong, seperti ini contohnya:
```golang
package main

func main() {

}
```
Kalau sudah pasti folder kita berisi 2 file ini 

![image info](/020-public-private/pict2.jpg)


4. Buat folder baru sejajar dengan {{<singlelinecodeblock text="main.go">}} dengan nama helper.
![image info](/020-public-private/pict3.jpg)

5. Buat file {{<singlelinecodeblock text="helper.go">}} di dalam folder helper, lalu buat function {{<singlelinecodeblock text="Sum()">}} seperti ini:
>Karena file helper.go berada di dalam folder helper, maka packagenya bernama helper
```golang{{<singlelinecodeblock text="Sum()">}}
package helper

func Sum(num1, num2 int) int {
	return num1 + num2
}
```

6. Panggil package helper dalam {{<singlelinecodeblock text="main.go">}} lalu gunakan function {{<singlelinecodeblock text="Sum()">}}. 

Seperti ini contohnya:
```golang
package main

import (
	"belajar-golang/helper"
	"fmt"
)

func main() {
	total := helper.Sum(5, 6)

	fmt.Println("total:", total)
}
```

Hasil eksekusi program diatas:
```golang
total: 11
```

7. Contoh yang kita lakukan di atas adalah, kita mengexport function {{<singlelinecodeblock text="Sum()">}} sehingga dapat digunakan diluar package helper.

8. Sekarang kita akan mengubah function {{<singlelinecodeblock text="Sum()">}} menjadi private.

Dengan cara mengubah huruf depan menjadi huruf kecil. Menjadi {{<singlelinecodeblock text="sum()">}}

9. Kita coba lagi menjalankan lagi programnya, dan pasti akan terjadi error seperti ini:
```bash
# command-line-arguments
./main.go:9:18: undefined: helper.Sum
```


10. Hal ini terjadi karna function {{<singlelinecodeblock text="sum()">}} bukan lagi public function, hanya package helper saja yang dapat memanggilnya.

11. Penerapan Public dan Private sama untuk semua entitas lain, seperti variable, const, struct, cukup awali dengan huruf besar untuk Public, awali dengan huruf kecil untuk Private.

### Jenis import pada Go

Dalam Go ada banyak jenis import, masing-masing memiliki fungsi yang berbeda.

#### Import blank

Import blank adalah saat kita mengimport sebuah package namun kita tidak memakai entitas apapun dari package tersebut. Ini biasanya digunakan untuk menjalankan kode inisialisasi pada package yang dipanggil.

Berikut contohnya:
```golang
import 	_ "belajar-golang/helper"
```

#### Import alias

Import alias membuat kita dapat mengimport package dan mengubah namanya saat kita gunakan, ini cukup berguna jika dalam 1 file Go kita mengimport lebih dari 1 package dengan nama yang sama.
```golang
import (
	helper1 "belajar-golang/aritmethic/helper"
	helper2 "belajar-golang/print/helper"
)
```

Cara memanggil function dari kedua helper:
```golang
func main() {
	total := helper1.Sum(5, 6)

	helper2.Print(fmt.Sprintf("total: %d", total))
}
```
 
### Import dot (.)

Dengan Import dot(.) kita dapat mengimport package seakan-akan kedua package itu setara. 

Jadi kita tidak perlu memanggil nama packagenya sebelum memanggil entitasnya, seperti ini {{<singlelinecodeblock text="helper.Sum()">}}

Kita cukup memanggil function {{<singlelinecodeblock text="Sum()">}} nya saja.

Berikut Contohnya:
```golang
package main

import (
	. "belajar-golang/aritmethic/helper"
	. "belajar-golang/print/helper"
	"fmt"
)

func main() {
	total := Sum(5, 6)

	Print(fmt.Sprintf("total: %d", total))
}
```

Hasil eksekusi kode:
```bash
total: 11
```

Seperti kita lihat diatas, kita tidak perlu memanggil nama packagenya saat memanggil functionya.

>Disclaimer: menurut saya cara ini kurang baik ya, karna developer akan sulit melacak dimana function itu dibuat.

### Apa selanjutnya?
Selanjutnya kita akan belajar mengenai interface pada golang

Happy learning! 😆