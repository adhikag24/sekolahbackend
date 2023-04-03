---
title: "Tutorial Golang: Map"
date: 2023-03-06T22:41:34+07:00
draft: false
author: "Adhika Guna"
thumbnail: /012-map/thumbnail.png
description: "Belajar Map pada Golang"
---


### Map

Map adalah key-value data struktur, mungkin di bahasa pemrograman lain orang biasa memanggilnya {{<singlelinecodeblock text="hash map">}} atau {{<singlelinecodeblock text="dictionary">}} 

Dalam golang kita dapat menginisialisasi map kosong dengan keyword {{<singlelinecodeblock text="make(map[key-type]val-type)">}}

Kita juga dapat sekaligus menyimpan banyak value dalam sebuah map. Kita dapat menyimpan value baru di map dengan syntax {{<singlelinecodeblock text="mapVar[new-key] = new-val">}}.

Berikut contoh kode penerapan map pada Golang:
```golang
nilaiMurid := make(map[string]int)

nilaiMurid["Fauzan"] = 89
nilaiMurid["Adhika"] = 90
nilaiMurid["Budi"] = 100

fmt.Println(nilaiMurid) //map[Adhika:90 Budi:100 Fauzan:89]
```

### Inisialisasi Map sekaligus dengan valuenya

Dalam golang kita juga dapat menginisialisasi Map sekaligus valuenya
```golang
nilaiMurid := map[string]int{"Adhika": 99, "Fauzan": 100, "Budi": 87}
fmt.Println(nilaiMurid) //map[Adhika:99 Budi:87 Fauzan:100]
```

### Built-in function delete

Untungnya golang menyediakan built-in function untuk kita menghapus data pada map, kita dapat menggunakan function {{<singlelinecodeblock text="delete">}} 

Function {{<singlelinecodeblock text="delete">}} menerima 2 parameter yaitu:
- nama Mapnya
- nama key yang mau di hapus

Berikut contoh kodenya:
```golang
nilaiMurid := map[string]int{"Adhika": 99, "Fauzan": 100, "Budi": 87}
delete(nilaiMurid, "Adhika")

fmt.Println(nilaiMurid)
```
Hasil eksekusi kode diatas:
![image info](/012-map/pict1.jpg)

Bisa kita lihat data dengan key {{<singlelinecodeblock text="Adhika">}} di map {{<singlelinecodeblock text="nilaiMurid">}} sudah tidak ada.


### Apa yang terjadi kita memanggil key yang tidak ada?

Apa yang terjadi kita memanggil key yang tidak ada? yang terjadi adalah value yang dibalikan akan kosong, tidak akan terjadi error.

Berikut contohnya:
```golang
nilaiMurid := map[string]int{"Adhika": 99, "Fauzan": 100, "Budi": 87}

fmt.Println("Bagas:", nilaiMurid["Bagas"])
```
Berikut hasil eksekusinya:
![image info](/012-map/pict2.jpg)

Dan seperti kita lihat, tidak terjadi error walaupun kita memanggil key yang tidak ada.


### Apa selanjutnya?
Selanjutnya kita akan belajar slice pada golang

Happy learning! 😆

