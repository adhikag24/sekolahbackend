---
title: "Tutorial Golang: Kondisi"
date: 2023-03-01T22:06:06+07:00
draft: false
author: "Adhika Guna"
tags: ["golang"]
thumbnail: /009-kondisi/thumbnail.png
description: "Belajar Kondisi pada Golang"
---


### Kondisi
Kondisi pada pemrograman di gunakan untuk mengatur flow dari sebuah program, sama saja dengan pengambilan keputusan pada dunia nyata, misalnya saat kita puasa kita di perbolehkan makan setelah jam tertentu, nah jam tertentu inilah sebuah kondisi yang menentukan kita boleh makan atau tidak. Sama juga dengan pengambilan keputusan pada sebuah program, sebuah kode dieksekusi ketika kondisi yang diberikan terpenuhi. Ini biasa juga di sebut sebagai Control flow statements.

Go mempunyai 2 macam keyword untuk memilih kondisi, yakni:
- if, else statement
- switch case

### if, else if, else statement 
Berikut contoh penggunaan if, else statement pada golang
```golang
package main
import "fmt"

func main() {
	time := 16
	bukaPuasa := 18

	if time > bukaPuasa {
		fmt.Println("saatnya makannn...")
	} else {
		fmt.Println("masih belum boleh makan")
	}
}
```
Kalau kita eksekusi kode diatas, hasilnya adalah:
![image info](/009-kondisi/pict1.jpg)

Yappp, karna kondisi {{<singlelinecodeblock text="time > bukaPuasa">}} tidak terpenuhi, maka code yang di dalam {{<singlelinecodeblock text="else">}} lah yang akan tereksekusi.

Coba sekarang kita ganti value {{<singlelinecodeblock text="time">}} nya menjadi 20, agar kondisi {{<singlelinecodeblock text="time > bukaPuasa">}} terpenuhi.
```golang
package main
import "fmt"

func main() {
	time := 20
	bukaPuasa := 18

	if time > bukaPuasa {
		fmt.Println("saatnya makannn...")
	} else {
		fmt.Println("masih belum boleh makan")
	}
}
```

hasilnya adalah:
![image info](/009-kondisi/pict2.jpg)

Jika kita ingin menggunakan if,else untuk lebih dari 1 kondisi, kita bisa memakai keyword  {{<singlelinecodeblock text="else if">}}

Berikut contoh kodenya:
```golang
package main
import "fmt"

func main() {
	lampuLaluLintas := "HIJAU"

	if lampuLaluLintas == "MERAH" {
		fmt.Println("Berhenti")
	} else if lampuLaluLintas == "KUNING" {
		fmt.Println("Hati-hati")
	} else if lampuLaluLintas == "HIJAU" {
		fmt.Println("Jalan")
	} else {
		fmt.Println("Lampu tidak benar / mati")
	}
}
```
Hasil eksekusi kode diatas:
![image info](/009-kondisi/pict4.jpg)



###  if, else if, else statement dengan inisialisasi

Saat menggunakan {{<singlelinecodeblock text="if">}} statement pada golang kita juga di perbolehkan untuk melakukan inisialisasi value, begini contohnya:
```golang
package main
import "fmt"

func main() {
	if lampu := "Kuning"; lampu == "Kuning" {
		fmt.Println("Hati-hati")
	}
}
```
Hasil eksekusi kode diatas:
![image info](/009-kondisi/pict5.jpg)

Perlu di ingat, bahwa variable {{<singlelinecodeblock text="lampu">}} hanya bisa di panggil di dalam block {{<singlelinecodeblock text="if">}} tersebut, di luar block variable lampu tidak dapat di kenali.


### if, else if, else statement bercabang / nested
Dalam perkondisian, ada istilah {{<singlelinecodeblock text="nested if">}}, nested if ini artinya ada if didalam if, berikut contoh kodenya:

```golang
package main
import "fmt"

func main() {

	nilai := 57

	if nilai > 80 {
		fmt.Println("A")
	} else if nilai > 60 {
		fmt.Println("B")
	} else {
		if nilai < 30 {
			fmt.Println("D")
		} else if nilai < 60 {
			fmt.Println("C")
		}
	}
}
```
Hasil eksekusi kode diatas:
![image info](/009-kondisi/pict6.jpg)

Nested if kurang di anjurkan karna kodenya cenderung komplex.

if,else juga kurang di rekomendasikan, jika kondisinya terlalu banyak. Jika kondisinya banyak, lebih di anjurkan memakai switch-case yang akan kita bahas 😃.


### switch-case pada golang
switch-case bisa kita pakai sebagai alternative if-else, jika kondisi alur program terlalu banyak. Berikut contoh kode penggunaan switch-case:

```golang
package main
import (
	"fmt"
)

func main() {
	lampuLaluLintas := "KUNING"

	switch lampuLaluLintas {
	case "MERAH":
		fmt.Println("Stop!!")
	case "KUNING":
		fmt.Println("Hati-hati!")
	case "HIJAU":
		fmt.Println("Jalann!")
	default:
		fmt.Println("Lampu tidak valid")
	}
}
```
Hasil eksekusi kode diatas:
![image info](/009-kondisi/pict5.jpg)

switch-case dinilai lebih elegan, dan lebih mudah terbaca dibanding if-else jika kondisi yang akan di seleksinya banyak. 

keyword {{<singlelinecodeblock text="switch">}} digunakan untuk memberitahu program, mana variable yang akan kita seleksi

keyword {{<singlelinecodeblock text="case">}} digunakan untuk memberitahu program kondisi yang akan di cek

keyword {{<singlelinecodeblock text="default">}} digunakan untuk nilai default, jika tidak ada kondisi yang terpenuhi, sama saja dengan keyword {{<singlelinecodeblock text="else">}}


### Apa selanjutnya?

Selanjutnya kita akan belajar pengulangan pada golang.

Happy learning! 😆