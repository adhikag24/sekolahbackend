---
title: "Tutorial Golang: Slice"
date: 2023-03-10T12:20:37+07:00
draft: false
author: "Adhika Guna"
thumbnail: /013-slice/thumbnail.png
description: "Belajar Slice pada Golang"
---

### SLice

Slice sama dengan array, untuk menyimpan banyak value di dalam 1 variable. Tapi beda dengan array slice lebih powerful dan flexible dari pada array. Slice dapat menyesuaikan sizenya, sesuai jumlah data, tidak fixed seperti array.

### Inisialisasi Slice

Dalam Go kita dapat inisialiasi array dengan syntax {{<singlelinecodeblock text="[]data_type{value}">}}, untuk mengakses slice juga sama dengan array kita dapat menggunakan {{<singlelinecodeblock text="varArray[num_index]">}}.

Berikut contoh slice pada Go:
```golang
mySlice := []string{"Pisang", "Anggur", "Mangga", "Jeruk"}
fmt.Println(mySlice) //[Pisang Anggur Mangga Jeruk]
fmt.Println(mySlice[0]) //Pisang
```


### Slicing dengan slice

Dengan slice kita dapat memotong sebagian data, misal kita ingin hanya mengambil 5 data terakhir dalam / 5 data pertama, kita juga dapat menggambil data dengan range, misal kita ingin mengambil data dari index 2 sampai 5.

Kita dapat slicing slice menggunakan syntax {{<singlelinecodeblock text="[low:max]">}}
- Misal kita ingin mengambil {{<singlelinecodeblock text="5 data pertama">}}, syntaxnya akan seperti ini {{<singlelinecodeblock text="mySlice[:5]">}}
- Misal kita ingin mengambil {{<singlelinecodeblock text="5 data terakhir">}}, syntaxnya akan seperti ini {{<singlelinecodeblock text="mySlice[5:]">}}
- Misal kita ingin mengambil {{<singlelinecodeblock text="data dari index 2 - 5">}} syntaxnya akan seperti ini {{<singlelinecodeblock text="mySlice[len(mySlice)-5:]">}}

Berikut contoh kodenya:
```golang
mySlice := []string{"Pisang", "Anggur", "Mangga", "Jeruk", "Kiwi", "Alpuket", "Apel", "Nanas"}
fmt.Println("5 data pertama:", mySlice[:5])
fmt.Println("5 data terakhir:", mySlice[len(mySlice)-5:])
fmt.Println("data dari index 2 - 5:", mySlice[2:5])
```

Berikut hasilnya:
![image info](/013-slice/pict3.jpg)


### len() dan cap() pada slice

Kita dapat mengetahui panjang / banyaknya isi dari sebuah slice dengan menggunakan function {{<singlelinecodeblock text="len()">}} dan kita dapat mengecek kapasitas sebuah slice dengan function {{<singlelinecodeblock text="cap()">}}

Berikut contoh kodenya:
```golang
arrOfNum := []int{43, 56, 90, 100, 34}
fmt.Println("len():", len(arrOfNum))
fmt.Println("cap():", cap(arrOfNum))
```
Hasil eksekusi kode diatas:
![image info](/013-slice/pict4.jpg)

Kalau kita lihat di atas, hasilnya {{<singlelinecodeblock text="len()">}} dan {{<singlelinecodeblock text="cap()">}}, sama-sama 5.

Kita coba kurangi {{<singlelinecodeblock text="1">}} isi dari array {{<singlelinecodeblock text="arrOfNum">}}

Berikut contoh kodenya:
```golang
arrOfNum := []int{43, 56, 90, 100, 34}
arrOfNum = arrOfNum[:len(arrOfNum)-1]

fmt.Println("arrOfNum:", arrOfNum)
fmt.Println("len():", len(arrOfNum))
fmt.Println("cap():", cap(arrOfNum))
```
Hasil eksekusi kode diatas:
![image info](/013-slice/pict5.jpg)

Kalau kita lihat dari hasil eksekusi diatas, isi dari array {{<singlelinecodeblock text="arrOfNum">}} berkurang 1 menjadi 4, sedangkan kapasitas dari array {{<singlelinecodeblock text="arrOfNum">}} tetap 5.


### Slice adalah reference

Hati2 ketika ingin mengassign sebuah slice ke variable baru, jika kita mengubah data di slice yang lama, maka data di slice baru akan ikut terupdate juga, itu dikarenakan slice adalah {{<singlelinecodeblock text="reference">}}.

Berikut contoh kodenya:
```golang
arrOfNum := []int{43, 56, 90, 100, 34}
arrOfNumClone := arrOfNum

arrOfNum[0] = 0

fmt.Println("arrOfNum:", arrOfNum)
fmt.Println("arrOfNumClone:", arrOfNumClone)
```
Berikut hasi eksekusi kode diatas:
![image info](/013-slice/pict6.jpg)

Kalau kita lihat dari hasil di atas, data index ke {{<singlelinecodeblock text="0">}} pada {{<singlelinecodeblock text="arrOfNumClone">}} ikut terupdate menjadi 0. Lalu bagaiman ketika ingin mengcopy value slice ke variable baru?

Untungnya Go menyediakan built-in function bernama {{<singlelinecodeblock text="copy()">}}. Kita dapat menggunakan {{<singlelinecodeblock text="copy()">}} untuk mengcopy data dari 1 slice ke variable yang baru.

### copy() pada slice

Kita sudah belajar, kalau kita tidak bisa sembarangan mengassign slice pada variable baru. Kita dapat memanfaatkan function copy untuk mengcopy data slice dari 1 variable ke variable yang lain.

Berikut contoh kodenya:
```golang
arrOfNum := []int{43, 56, 90, 100, 34}
var arrOfNumClone = make([]int, len(arrOfNum))
copy(arrOfNumClone, arrOfNum)

arrOfNum[0] = 0

fmt.Println("arrOfNum:", arrOfNum)
fmt.Println("arrOfNumClone:", arrOfNumClone)
```
Berikut hasi eksekusi kode diatas:
![image info](/013-slice/pict7.jpg)

Kalau kita lihat dari hasil eksekusi kode diatas kita berhasil mengcopy slice dari variable {{<singlelinecodeblock text="arrOfNum">}} ke {{<singlelinecodeblock text="arrOfNumClone">}} dan ketika index ke {{<singlelinecodeblock text="0">}} pada {{<singlelinecodeblock text="arrOfNum">}} di update data pada {{<singlelinecodeblock text="arrOfNumClone">}} tidak ikut terupdate. 

#### Kelemahan copy()

Ketika kita ingin menggunakan {{<singlelinecodeblock text="copy()">}} kita harus memastikan variable tujuan memiliki kapasitas yang sama dengan source datanya. Jika kapasitas variable tujuannya 0 maka datanya tidak akan tercopy.

Berikut contoh kodenya:
```golang
arrOfNum := []int{43, 56, 90, 100, 34}
var arrOfNumClone = make([]int, 0)

copy(arrOfNumClone, arrOfNum)

fmt.Printf("arrOfNum: %d capacity: %d", arrOfNum, cap(arrOfNum))
fmt.Printf("\narrOfNumClone: %d, capacity: %d", arrOfNumClone, cap(arrOfNumClone))
```
Hasil eksekusi kode diatas:
![image info](/013-slice/pict8.jpg)

Bisa kita lihat variable {{<singlelinecodeblock text="arrOfNumClone">}} memiliki kapasitas 0, dan valuenya kosong.

Untuk menghindari hal seperti ini kita dapat menyamakan kapasitas variable {{<singlelinecodeblock text="arrOfNumClone">}} saat mengdeklarasikannya.

Daripada mengdeklarasikan sizenya sama dengan 0
```golang
var arrOfNumClone = make([]int, 0)
```
Lebih baik kita mengdeklarasikan sizenya sesuai dengan kapasitas dari {{<singlelinecodeblock text="arrOfNum">}} 
```golang
var arrOfNumClone = make([]int, cap(arrOfNum))
```

Berikut full contoh kodenya:
```golang
arrOfNum := []int{43, 56, 90, 100, 34}
var arrOfNumClone = make([]int, cap(arrOfNum))

copy(arrOfNumClone, arrOfNum)

fmt.Printf("arrOfNum: %d capacity: %d", arrOfNum, cap(arrOfNum))
fmt.Printf("\narrOfNumClone: %d, capacity: %d", arrOfNumClone, cap(arrOfNumClone))
```

Berikut hasil eksekusi kodenya:
![image info](/013-slice/pict9.jpg)

Dapat kita lihat, valuenya berhasil tercopy dengan baik.


### Apa selanjutnya?
Selanjutnya kita akan belajar function pada golang

Happy learning! 😆
