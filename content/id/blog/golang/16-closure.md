---
title: "Tutorial Golang: Closure"
date: 2023-03-24T16:37:28+07:00
draft: false
author: "Adhika Guna"
thumbnail: /016-closure/thumbnail.png
description: "Belajar Closure pada Golang"
---

### Anonymus Function
Sebelum memahami Closure, ada baiknya kita belajar apa itu anonymus function.

Anonymus function adalah function tanpa nama, anonymus function harus berada didalam function lainnya, tidak dapat menjadi function sendiri.

Berikut contoh anonymus function pada Golang:
```golang
func main() {
    //this is anonymus function
	func(message string) {
		fmt.Println(message)
	}("This is anonymus function!")
}
```

Berikut hasil eksekusinya:
![image info](/016-closure/pict1.jpg)


Anonymus function sama saja dengan function biasa, hanya saja tidak memiliki nama. Anonymus function juga langsung dieksekusi setelah di definisikan.



### Closure

Closure dalam golang adalah function yang dapat disimpan ke variable, kita juga dapat membuat function yang mengembalikan function, dan juga membuat function di dalam function.

Sebenarnya closure itu adalah function tanpa nama / alias {{<singlelinecodeblock text="anonymus function">}}, closure bisa dimanfaatkan untuk membungkus baris kode yang dipakai sekali / berkali2 tapi hanya dalam 1 function.

Berikut contoh definisi function yang disimpan ke variable:
```golang
print := func(message string) {
    fmt.Println(message)
}
```

Lalu untuk memanggilanya bisa seperti memanggil function pada umumnya, dengan **kurung buka dan tutup** seperti ini:
```golang
print("ini contoh closure")
```

Berikut hasil eksekusinya:
![image info](/016-closure/pict2.jpg)


Berikut contoh kode fullnya:
```golang
func main() {
	print := func(message string) {
		fmt.Println(message)
	}

	print("ini adalah closure")
}
```


### Closure sebagai return value

Seperti yang di tulis diatas kita dapat **membuat function yang mengembalikan function**

Berikut contohnya:
```golang
func getPrintFunc() func(message string) {
	return func(message string) {
		fmt.Println(message)
	}
}
```

Function {{<singlelinecodeblock text="getPrintFunc()">}} mendefinisikan {{<singlelinecodeblock text="func(string)">}} sebagai return value, itu karena function tersebut mengembalikan function dengan string sebagai parameter.

Berikut contoh memanggil function {{<singlelinecodeblock text="getPrintFunc()">}}:
```golang
print := getPrintFunc()
```
Sekarang kita dapat menggunakan variable print untuk "mengprint" / menulis output pada terminal.

```golang
print("Hi, ini contoh function dengan return function")
```

Hasil eksekusi kode diatas:
![image info](/016-closure/pict3.jpg)


### Closure untuk membuat kode lebih singkat

**Disclaimer dulu, ini hanyala contoh yaa**, bukan berarti saat kalian ngoding nanti kalian harus implementasi ini, karna yang paling penting adalah kode kalian dapat di pahami oleh orang lain, bukan dari singkatnya sebuah kode.


Semisal kita ingin membuat function yang dapat menambahkan angka terus menerus, angkanya bisa kita dapatkan dari parameter functionnya.

Berikut contohnya jika kita menggunakan **regular function**:
```golang
func infiniteSumRegular(tempValue, num int) int {
	return tempValue + num
}

func main() {
	total := infiniteSumRegular(0, 5)
	total = infiniteSumRegular(total, 5)
	total = infiniteSumRegular(total, 5)

	fmt.Println(total) // 15
}
```

Berikut contohnya jika kita menggunakan **Closure**:
```golang
func infiniteSum() func(num int) int {
	total := 0
	return func(num int) int {
		total = total + num
		return total
	}
}

func main() {
    sum := infiniteSum()

	sum(5)
	sum(5)
	fmt.Println(sum(5))
}
```

Seperti yang kita lihat, dengan menggunakan Closure, kita tidak perlu membuat variable untuk menyimpan hasil sementara dari penjumlahan, dan juga hanya cukup 1 parameter untuk function penambahannya.

### Apa selanjutnya?
Selanjutnya kita akan belajar pointer pada golang

Happy learning! 😆
