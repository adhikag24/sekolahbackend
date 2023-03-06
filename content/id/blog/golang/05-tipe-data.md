---
title: "Tutorial Golang: Tipe Data"
date: 2023-02-22T22:34:54+07:00
draft: false
author: "Adhika Guna"
tags: ["golang"]
thumbnail: /005-tipe-data/thumbnail.png
description: "Mengenal dan memahami semua macam tipe data pada Golang"
---

### Tipe Data
Tipe data adalah cara kita mengklasifikasikan jenis variable, karna dengan tipe data kita memberi tahu komputer jenis data yang digunakan untuk sebuah variable, Go mempunyai 3 tipe data dasar:
- bool: merepresentasikan bilai boolean, nilainya hanya aja 2, antara true atau false
- Numeric: merepresentasikan nilai dalam bentuk angka, yaitu integer, dan juga float (untuk decimal)
- string: merepresentasikan nilai dalam bentuk `string` string itu bisa dibilan text biasa dengan ciri ada titik 2 di awal dan di akhir seperti ini `"ini string"`

### boolean

Tipe data boolean dapat di deklarasi dengan syntax `bool` tipe boolean ini hanya bisa menerima 2 nilai `true` atau `false`, dan setiap kita inisiali variable boolean defaultnya adalah `false`

Berikut contoh deklarasi boolean pada golang
```golang
package main
import "fmt"

func main() {
	var bool1 bool
	bool2 := true

	fmt.Println("bool1:", bool1) // Return false
	fmt.Println("bool2:", bool2) // Return true
}
```


### integer

Tipe data integer digunakan untuk menyimpan data angka tanpa desimal seperti 35, 50, -5, 100 dsb

Tipe data integer dibagi menjadi 2 kategori yaitu:
- Signed integer dapat menyimpan nilai positive dan juga negative
- Unsigned integer hanya bisa menyimpan nilai non-negative atau nilai yang disimpan akan selalu positive

#### Signed integer

Signed integer dapat dideklarasi dengan syntax `int`, jika kita deklarasi `int` tanpa memberitahu nilainya secara default valuenya adalah 0, berikut contohnya:
```golang
package main
import "fmt"

func main() {
	var num1 int
	num2 := 100

	fmt.Println("num1:", num1) // return 0
	fmt.Println("num2:", num2) // return 100
}
```

#### Unsigned integer

Kalau Unsigned integer dapat kita deklarasi dengan syntax `uint` bedanya dia Unsigned integer hanya dapat menyimpan nilai positive, lalu apa bila terjadi pengurangan yang mengharuskan nilainya menjadi negative `(conton 50 - 100)` apa yang akan terjadi?

Berikut contoh programnya:
```golang
package main
import "fmt"

func main() {
	var num1 uint
	var num2 uint
	num2 = 50
	fmt.Println("num2:", num2) // return 50
	num2 = num2 - 100

	fmt.Println("num1:", num1) // return 0
	fmt.Println("num2:", num2) // return 18446744073709551566
}
```
dan hasil dari 50 - 100 pada num2 adalah `18446744073709551566`, wow banyak sekali? kenapa bisa begitu? jadi pada Unsigned integer bilai nilainya kurang dari 0 maka dia akan mengulang lagi dari value maximalnya, berdasarkan dokumentasi [ini](https://golang-id.org/ref/spec) nilai maximum dari Unsigned integer adalah `18446744073709551615`. Jadi jika kalian perhatikan `18446744073709551566` / value 50 - 100 pada Unsigned integer adalah nilai maximum Unsigned integer dikurangi 49, mengapa 49? karna 1 nya dipakai untung menghitung 0.


### Float

Tipe data float pada Golang digunakan untuk menyimpan value desimal, seperti 0.1, 5.4, 25000.500

Ada 2 tipe float yaitu:
- `float32` dengan range `-3.4e+38 to 3.4e+38`
- `float64` dengan range `-1.7e+308 to +1.7e+308`

#### float32

Berikut contoh penggunaan `float32`
```golang
package main
import "fmt"

func main() {
	var num1 float32
	num2 := 3.4
	num3 := 5.0 - 100

	fmt.Println("num1:", num1) // return 0
	fmt.Println("num2:", num2) // return 3.4
	fmt.Println("num3:", num3) // return -95
}
```

#### float64

Penggunaan `float64` sama saja dengan `float32` hanya saja `float64` dapat menyimpan value lebih banyak

Berikut contoh penggunaan `float64`
```golang
package main
import "fmt"

func main() {
	var num1 float64
	num2 := 3.4
	num3 := 5.0 - 100

	fmt.Println("num1:", num1) // return 0
	fmt.Println("num2:", num2) // return 3.4
	fmt.Println("num3:", num3) // return -95
}
```


### String

Tipe data `string` digunakan untuk menyimpan data text, dan nilai dari string harus dibuka dan ditutup dengan titik 2 seperti ini: `"ini string"`

Berikut contoh penggunaan `string`
```golang
package main
import "fmt"

func main() {
	var text1 string
	text2 := "halo budi"

	fmt.Println("text1:", text1) // return 
	fmt.Println("text2:", text2) // return "halo budi
}
```

###


### interface{}

`interface{}` ini tipe data yang cukup spesial pada Golang, tipe data `interface{}` itu dapat menyimpan jenis data apa pun, boolean, numeric, string dan juga null value. Penggunaan `interface{}` dapat menggunakan syntax `interface{}`.

Berikut contoh penggunaan `interface{}`
```golang
package main
import "fmt"

func main() {
	var interface1 interface{}

	interface1 = "ini string"
	fmt.Println(interface1) //Return ini string
	interface1 = 123
	fmt.Println(interface1) //Return 123
	interface1 = 50.0
	fmt.Println(interface1) //Return 50
	interface1 = nil
	fmt.Println(interface1) //Return <nil>
}
```

Nah kalau kita lihat dari kode diatas, variable `interface1` bisa kita eksekusi tanpa ada error sama sekali, karna tipe data `interface{}` bisa kita pakai untuk menyimpan data apa pun.


### Apa selanjutnya?

Selanjutnya kita akan belajar komentar pada golang.

Happy learning! 😆