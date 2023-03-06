---
title: "Tutorial Golang: Variable"
date: 2023-02-20T21:17:19+07:00
draft: false
author: "Adhika Guna"
tags: ["golang"]
thumbnail: /004-variable/thumbnail.png
description: "Mengenal Variable pada Golang dan bagaimana cara menggunakannya"
---


### Variable
Dalam go ada beberapa cara untuk deklarasi variable, ada yang memakai tipe datanya, ada juga yang tidak.

### Deklarasi dengan tipe data
Dalam go kita bisa deklasari variable dengan keyword {{< singlelinecodeblock text="var" >}}, dengan format seperti ini {{< singlelinecodeblock text="var <nama_variable> <tipe_data>" >}}
dan, berikut contoh kodenya:
```golang
package main

import "fmt"

func main() {
	var murid string

	murid = "Budi"
	fmt.Println(murid)
}

```
Dan ini hasilnya ketika program dijalankan:
![image info](/004-variable/pict1.jpg)

Deklarasi variable dengan tipe data juga bisa sekaligus loh, seperti ini
```golang
var (
		murid string
		kelas int
		nilai float64
	)

```
atau bisa juga membuat banyak variable sekaligus dengan 1 tipe data dalam 1 baris kode, seperti ini
```golang
var murid, jurusan, nama string
```

### Deklarasi tanpa tipe data

Nah, selain deklarasi dengan tipe data seperti contoh di atas, golang juga dapat deklarasi variable tanpa tipe data. Kita dapat memakai syntax ```:=``` untuk assignment value, sekaligus deklarasi variable.
```golang
murid := "budi"
```
dengan cara di atas, variable ```murid``` otomatis terdeklarasi dengan tipe data ```string``` (mengikuti value yang di assign)

Dengan cara ini juga kita dapat deklarasi banyak variable sekaligus, seperti ini
```golang
murid, murid2 := "Budi", "Doni"
```
Contoh Kode:
```golang
func main() {

	murid, murid2 := "Budi", "Doni"

	fmt.Println(murid, murid2)
}

```
Ketika dijalankan:
![image info](/004-variable/pict2.jpg)


### Variable _

Di golang ada special variable yaitu ```_``` yapp, itu hanya sebuah ```underscore```, dengan deklarasi variable menggunakan ```_``` kita menandakan bahwa variable ini tidak akan terpakai, karna pada golang kita harus menggunakan variable yang di deklarasi, jika tidak akan muncul error seperti ini:
![image info](/004-variable/pict3.jpg)

dan ketika kita ganti variable ```murid2``` menjadi ```_``` error akan menghilang
```golang
func main() {

	murid, _ := "Budi", "Doni"

	fmt.Println(murid)
}
```

### Deklarasi dengan syntax new()

Di golang kita dapat deklarasi variable dengan syntax ```new``` seperti ini:
```golang
nilai := new(int)
```
dengan menggunakan syntax new variable tersebut secara otomatis berubah penjadi ```pointer``` nanti kita akan bahas apa itu pointer. Singkatnya pointer adalah variabel yang digunakan untuk menyimpan alamat memori dari variabel lain. 

Contoh Kode:
```golang
func main() {

	nilaiBudi := 64

	nilai := new(int)

	nilai = &nilaiBudi

	fmt.Println("Value dari nilaiBudi: ", *nilai)
	fmt.Println("Memory dari nilaiBudi: ", &nilai)
}
```
Kalau lihat dari kode di atas variable ```nilai``` hanya menyimpan memory address untuk variable ```nilaiBudi```, dan kita bisa menggunakan ```*``` untuk mendapatkan value dari memory yang disimpan atau ```&``` untuk melihat memory addressnya. 

Berikut hasilnya ketika kode dieksekusi:
![image info](/004-variable/pict4.jpg)

Seperti bisa kita lihat dari hasil eksekusi kode di atas, ```*nilai``` menghasilkan ```64``` yakni value dari ```nilaiBudi```, dan ```&nilai``` menghasilkan ```0x14000120018``` yakni memory address dari ```nilaiBudi```



### Apa selanjutnya?

Selanjutnya kita akan belajar tipe data pada golang.

Happy learning! 😆