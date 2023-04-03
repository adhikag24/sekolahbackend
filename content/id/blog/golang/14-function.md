---
title: "Tutorial Golang: Function"
date: 2023-03-14T22:16:40+07:00
draft: false
author: "Adhika Guna"
thumbnail: /014-function/thumbnail.png
description: "Belajar Function pada Golang"
---

### Function

Function adalah cara kita membuat sebuah blok kode untuk menjalankan tugas secara spesifik. Misal dalam program kita, di butuhkan kode untuk menambahkan 2 angka, daripada kita menulis kodenya berulang2 lebih baik kita membuat fungsinya.

Dalam Go kita dapat membuat function dengan keyword {{<singlelinecodeblock text="func">}}. 

### Membuat function pada Golang

Berikut contoh pembuatan function pada Go:
```golang
func sum(num1 int, num2 int) int {
	return num1 + num2
}
```

Penjelasan:
- {{<singlelinecodeblock text="sum">}} adalah nama function
- {{<singlelinecodeblock text="num1">}} dan {{<singlelinecodeblock text="num2">}} adalah parameter dengan tipe data {{<singlelinecodeblock text="int">}} yang digunakan di dalam function 
- {{<singlelinecodeblock text="int">}} setelah tutup kurung, adalah tipe data yang akan di kembalikan function

Contoh pemakaian function sum:
```golang
sumResult := sum(3, 5)
fmt.Println("sumResult:", sumResult) //sumResult: 8
```

### Return function dengan nama

Dalam Go, function dapat mengembalikan nilai, dan nilai yang dikembalikan dapat juga diberi nama dengan cara menginisialisasi variable saat function dibuat. Contoh dibawah variable {{<singlelinecodeblock text="total">}} untuk menampung Return value dari function {{<singlelinecodeblock text="sum">}}.

Berikut contoh function dengan return value yang memiliki nama pada Go:
```golang
func sum(num1 int, num2 int) (total int) {
	total = num1 + num2
	return total
}
```

Lalu apa manfaat dari naming (menamakan) return value dari sebuah function? toh hasilnya sama saja ~~

Naming return value akan saat bermanfaat jika return value dari sebuah function lebih dari 1, memudahkan untuk memantain kode kedepannya. 

Yapp dalam Go kita dapat mengembalikan lebih dari 1 value dalam sebuah function.

### Function return multiple value

Function dalam Go dapat mengembalikan banyak value sekaligus, jadi biasanya di bahasa pemrograman lain kita hanya dapat mengembalikan 1 value, namu dalam Go kita dapat mengembalikan multiple value. 

Untuk mengembalikan banyak value dalam function, kita dapat mendeklarasi value apa saja yang akan di kembalikan seperti ini {{<singlelinecodeblock text="func rectangle(panjang int, lebar int) (int, int) {}">}} atau lebih baik kita beri nama return valuenya, agar function lebih muda dibaca {{<singlelinecodeblock text="func rectangle(panjang int, lebar int) (luas int, keliling int) {}">}}.

Berikut contoh kode function return multiple value
```golang
func rectangle(panjang int, lebar int) ( int,  int) {
	keliling = 2 * (panjang + lebar)
	luas = panjang * lebar
	return luas, keliling
}
```

Contoh pemakaian function rectangle:
```golang
area, parameter := rectangle(3, 5)
fmt.Println("area:", area) // area: 15
fmt.Println("parameter", parameter) // parameter 16
```

### Deklarasi parameter dengan tipe data sama

Jika dalam funtion kita memiliki lebih dari 1 parameter, dan memiliki tipe data yang sama, kita cukup menulis tipe data di paling akhir setelah penulisan variable parameter. Cara ini juga berlaku untuk return value.

Berikut contohnya:

```golang
func rectangle(panjang int, lebar int) (luas int, keliling int) {
	keliling = 2 * (panjang + lebar)
	luas = panjang * lebar
	return luas, keliling
}


func rectangle(panjang, lebar int) (luas, keliling int) {
	keliling = 2 * (panjang + lebar)
	luas = panjang * lebar
	return luas, keliling
}
```


### Apa selanjutnya?
Selanjutnya kita akan belajar function variadic pada golang

Happy learning! 😆
