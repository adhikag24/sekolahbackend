---
title: "Tutorial Golang: Interface Kosong"
date: 2023-04-05T21:34:05+07:00
draft: false
author: "Adhika Guna"
thumbnail: /022-empty-interface/thumbnail.png
description: "Belajar Interface kosong pada Golang"
---

### Interface kosong

Salah satu fitur yang menarik di Golang adalah penggunaan empty interface. 

```golang
interface{}
```
Empty interface atau interface kosong, dapat digunakan untuk mewakili nilai apa pun di Golang.

Empty interface tidak memiliki method yang didefinisikan di dalamnya. Ini berarti empty interface tidak memiliki aturan apapun terkait dengan struktur atau nilai yang akan diterima.

Empty interface dapat merepresentasikan nilai apa pun, bahkan objek dari tipe data yang berbeda.

### Penggunaan Empty Interface

Berikut contoh penggunaan Empty Interface
```golang
func printAny(i interface{}) {
    fmt.Println(i)
}
```
Pada kode di atas, kita dapat melihat bahwa parameter fungsi didefinisikan sebagai {{<singlelinecodeblock text="interface{}">}}. 

Ini berarti bahwa fungsi tersebut menerima nilai apa pun sebagai argumen. 

Ketika kita memanggil fungsi tersebut dengan argumen {{<singlelinecodeblock text="printAny(1)">}}, kita akan mendapatkan output {{<singlelinecodeblock text="1">}}, sedangkan jika kita memanggil dengan argumen {{<singlelinecodeblock text="printAny('hello')">}}, maka outputnya akan menjadi {{<singlelinecodeblock text="hello">}}. 

**Ini menunjukkan bahwa empty interface dapat merepresentasikan nilai apa pun.**

### Kelemahan Empty Interface

Penggunaan empty interface juga memiliki kelemahan. Karena empty interface dapat menerima nilai apa pun, maka kita tidak dapat menentukan method yang tersedia pada nilai tersebut. 

Sebagai contoh, jika kita menggunakan empty interface untuk merepresentasikan sebuah `string`, maka kita tidak dapat memanggil method khusus seperti {{<singlelinecodeblock text="len()">}} atau {{<singlelinecodeblock text="ToUpper()">}} pada nilai tersebut. 

Hal ini yang membuat kita perlu melakukan konversi tipe data agar dapat mengakses method yang diperlukan.

### Konversi tipe data dari empty interface

Berikut ini contoh kode yang menunjukkan cara menggunakan empty interface dan melakukan konversi tipe data untuk mengakses method spesifik:
```golang
func main() {
	var data interface{}
	data = "Hello, World!"

	strData, isOk := data.(string)

	fmt.Println("isOk:", isOk)
	fmt.Println("string:", strData)
	fmt.Println("stringUpper:", strings.ToUpper(strData))
}
```

Pada kode di atas, kita menggunakan empty interface untuk merepresentasikan nilai string. 

Kita kemudian melakukan konversi tipe data menggunakan {{<singlelinecodeblock text="(string)">}} untuk mengakses method {{<singlelinecodeblock text="strings.ToUpper()">}} pada nilai tersebut.

{{<singlelinecodeblock text="(string)">}} mengembalikan 2 data:
- Data yang sudah dikonversikan ke string
- Data boolean yang memberitahu apakah process konversi berhasil atau tidak (true jika berhasil, false jika gagal / error)

Hasil eksekusi kode diatas:
![image info](/022-empty-interface/pict1.jpeg)

Berikut lebih banyak contoh konversi untuk tipe data lainnya:
```golang
func main() {
	var data1, data2, data3 interface{}

	data1 = 23
	data2 = true
	data3 = 23.4

	data1Converted := data1.(int)
	data2Converted := data2.(bool)
	data3Converted := data3.(float64)

	fmt.Println("int:", data1Converted)
	fmt.Println("bool:", data2Converted)
	fmt.Println("float64:", data3Converted)
}
```


Berikut hasil eksekusi kode diatas:
![image info](/022-empty-interface/pict2.jpg)

### any

Dalam go kita juga dapat menggunakan tipe data {{<singlelinecodeblock text="any">}} jika tidak ingin menulis empty interface.


Tapi pada dasarnya {{<singlelinecodeblock text="any == interface{}">}}, {{<singlelinecodeblock text="any">}} hanyalah alias dari interface kosong, jadi penggunaan dan fungsinya juga sama saja.
![image info](/022-empty-interface/pict3.jpg)


Berikut contoh kode jika menggunakan any:

```golang
func main() {
	var stringInterface interface{}
	var stringAny any

	stringInterface = "Hello all!"
	stringAny = "Hello all!"

	stringDataInterface := stringInterface.(string)
	stringDataAny := stringAny.(string)

	fmt.Println("string from interface", stringDataInterface)
	fmt.Println("string from any", stringDataAny)
}
```

Berikut hasil eksekusi kode diatas:
![image info](/022-empty-interface/pict4.jpg)





### Apa selanjutnya?
Selanjutnya kita akan belajar mengenai package reflect pada golang

Happy learning! 😆