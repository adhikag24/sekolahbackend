---
title: "Tutorial Golang: Array"
date: 2023-03-05T15:47:57+07:00
draft: false
author: "Adhika Guna"
thumbnail: /011-array/thumbnail.png
description: "Belajar Array pada Golang"
---


### Array 

Array adalah data struktur paling sederhana dalam pemrograman, array berguna untuk menyimpan banyak data sekaligus, tapi hanya dapat menyimpan 1 jenis tipe data.

Jadi kita hanya bisa menyimpan 1 tipe data dalam sebuah array. Setiap element dalam array juga memiliki index, yang menandakan dimana posisi element itu berada.

![image info](/011-array/pict1.png)

Index juga berguna untuk mengambil value dalam sebuah array dengan menggunakan keyword {{<singlelinecodeblock text="array[num_of_index]">}}, misal dengan contoh array di atas {{<singlelinecodeblock text="array[3]">}} mengembalikan string dengan value {{<singlelinecodeblock text="Asep">}} 

### Inisialisasi Array pada Golang

Inisialisasi array di golang cukup mudah.

Kita dapat menggunakan keyword {{<singlelinecodeblock text="var">}} untuk menginisialisasi array kosong
```golang
var muridSekolah []string
var nilaiSekolah []int
```

Kita juga dapat menggunakan keyword {{<singlelinecodeblock text=":=">}} untuk inisialisasi array sekaligus valuenya.

```golang
muridSekolah := []string{"Budi", "Doni", "Haruka", "Asep", "Lili"}
nilaiSekolah := []int{89, 75, 45, 78, 65}
```


### Menambahkan value pada Array

Dalam menggunakan Array kita tidak dapat mengalokasikan value secara sembarangan.

Contohnya, dalam kode berikut akan terjadi error
```golang
muridSekolah := []string{"Budi", "Doni", "Haruka", "Asep", "Lili"}
muridSekolah[5] = "Lala"
```

karena pada dasarnya panjang array {{<singlelinecodeblock text="muridSekolah">}} hanyalah 4, akan terjadi panic jika mengalokasikan nilai pada index 5

Untungnya dalam golang ada built-in function {{<singlelinecodeblock text="append">}} 

```golang
muridSekolah := []string{"Budi", "Doni", "Haruka", "Asep", "Lili"}
muridSekolah = append(muridSekolah, "Lala")

fmt.Println(muridSekolah) // [Budi Doni Haruka Asep Lili Lala]
```

dengan {{<singlelinecodeblock text="append">}} kita dapat menambahkan value pada sebuah array, dengan aman.

### Pengulangan pada Array
Jika kita ingin melakukan pengulangan pada array, kita dapat menggunakan keyword {{<singlelinecodeblock text="for range">}}
```golang
muridSekolah := []string{"Budi", "Doni", "Haruka", "Asep", "Lili"}

for _, murid := range muridSekolah {
    fmt.Println(murid)
}
```
Hasil eksekusi kode diatas:
![image info](/011-array/pict2.jpeg)

Di kode di atas menggunakan {{<singlelinecodeblock text="_">}} karena, kita ingin menghiraukan value indexnya, karena tidak menggunakannya.

### Array multi-dimensional

Dalam golang juga kita dapat membuat Array multi-dimensional. Array multi-dimensional adalah Array didalam Array. Kita dapat menginisialiasi multi-dimensional array dengan menggunakan {{<singlelinecodeblock text="[][]">}}

Berikut contohnya:
```golang
muridSekolah := [][]string{
    []string{"Budi", "Yusuf", "Megumi"},
    []string{"Naruto", "Soga", "Dandan"},
}
```

#### For loop multi-dimensional array

Untuk melakukan loop dengan Array multi-dimensional, kita bisa melakukannya dengan  {{<singlelinecodeblock text="nested loop">}}  (Loop didalam loop)

Berikut contoh kodenya:
```golang
muridSekolah := [][]string{
		{"Budi", "Yusuf", "Megumi"},
		{"Naruto", "Soga", "Dandan"},
	}

	for _, muridKelas := range muridSekolah {
		for _, murid := range muridKelas {
			fmt.Println(murid)
		}
	}
```

Hasil kode diatas setelah di eksekusi:
![image info](/011-array/pict3.jpg)

### Apa Selanjutnya?

Selanjutnya kita akan belajar map pada golang

Happy learning! 😆


