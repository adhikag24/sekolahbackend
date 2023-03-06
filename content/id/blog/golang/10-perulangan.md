---
title: "Tutorial Golang: Perulangan"
date: 2023-03-04T15:17:37+07:00
draft: false
author: "Adhika Guna"
thumbnail: /010-perulangan/thumbnail.png
description: "Belajar Perulangan pada Golang"
---


### Perulangan 
Perulangan pada pemrograman berarti, mengeksekusi blok kode tanpa heti, kecuali kondisi yang diajukan sebagai acuan terpenuhi. Pada perulangan biasanya ada variable dan kondisi, dan jika kondisinya terpenuhi maka perulangan akan berakhir.

Sebagai contoh, jika kita ingin print sebuah {{<singlelinecodeblock text="string">}} sebanyak 50x, kita hanya perlu melakukan perulangan, dibanding kita menulis kode {{<singlelinecodeblock text="fmt.Println()">}} sebanyak 50x.

Pada golang perulangan hanya dapat memakai syntax {{<singlelinecodeblock text="for">}}, tapi itu cukup mengcakup fungsi perulangan di bahasa pemrograman lain seperti {{<singlelinecodeblock text="while">}} dan {{<singlelinecodeblock text="foreach">}}.

### for loop
Berikut adalah format pemakaian {{<singlelinecodeblock text="for">}} pada Golang:
```golang
for inisialisasi; kondisi; update {
  statement(s)
}
```
- inisialisasi, kita menginisialisasi sebuah variable, misal kita mau menginisialisasi {{<singlelinecodeblock text="i := 0">}}
- kondisi, kondisi ini berguna sebagai acuan dalam perulangan, selama kondisi ini bernilai true, maka perulangan akan tetap berjalan, contoh kondisinya adalah {{<singlelinecodeblock text="i < 10">}}.
- update, update disini, kita berguna untuk mengupdate variable yang telah kita inisialisasi contoh update adalah {{<singlelinecodeblock text="i++">}}.

Berikut contoh kodenya:
```golang
for i := 0; i < 10; i++ {
    fmt.Println("i =", i)
}
```

Berikut hasilnya ketika dieksekusi:
![image info](/010-perulangan/pict1.jpg)

Kalau kita lihat dari hasil diatas, value variable {{<singlelinecodeblock text="i">}} hanya sampai {{<singlelinecodeblock text="9">}}, itu di karenakan kondisi {{<singlelinecodeblock text="i < 10">}}. Jika {{<singlelinecodeblock text="i = 10">}}, maka kondisi tersebut akan mengembalikan nilai {{<singlelinecodeblock text="false">}}

### while loop

Jika kita tidak memakai {{<singlelinecodeblock text="inisialisasi">}}, dan {{<singlelinecodeblock text="update">}} kita akan mendapatkan {{<singlelinecodeblock text="while loop">}}. Berikut contoh kode {{<singlelinecodeblock text="while loop">}} pada golang:
```golang
i := 0
for i < 5 {
    i += 1
    fmt.Println(i)

}
fmt.Println("i after while loop:", i)
```
Berikut hasil eksekusi kode:
![image info](/010-perulangan/pict2.jpg)

Kita dapat membuat infinite loop juga pakai while loop 
```golang
for true {
    fmt.Println("this program will never ends")
}
```

### for-each range loop

{{<singlelinecodeblock text="for range">}} loop pada golang, biasa digunakan untuk iterasi ke setiap element, pada array, slice, map, bahkan sebuah string.

Berikut format {{<singlelinecodeblock text="for range">}} pada golang:
```golang
for index, element := range array {
  statement(index, element)
}
```
- index, index merujuk pada index element pada array yang sedang di iterasi
- element, element adalah value pada array yang sedang di iterasi

Berikut contoh kodenya:
```golang
arrayString := []string{"Merah", "Kuning", "Hijau", "Biru"}

for i, color := range arrayString {
    fmt.Println(i, "=", color)
}
```
Berikut hasil eksekusi kode:
![image info](/010-perulangan/pict3.jpg)

Dilihat dari hasil eksekusinya, variable {{<singlelinecodeblock text="i">}} adalah index dan {{<singlelinecodeblock text="color">}} adalah nilai dari {{<singlelinecodeblock text="arrayString">}} yang sedang di iterasi



### Apa selanjutnya?

Selanjutnya kita akan belajar array pada golang

Happy learning! 😆


