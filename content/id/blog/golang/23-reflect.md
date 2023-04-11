---
title: "Tutorial Golang: Package Reflect"
date: 2023-04-06T23:41:42+07:00
draft: false
author: "Adhika Guna"
thumbnail: /023-reflect/thumbnail.png
description: "Belajar Package Reflect pada Golang"
---


### Reflect

Reflect merupakan package bawaan dari Go yang digunakan untuk mengakses dan memanipulasi informasi pada saat runtime.

Dalam Go informasi seperti tipe data, nama fungsi, dan struktur data tersedia pada saat kompilasi.

Namun, pada saat runtime, kita seringkali memerlukan akses ke informasi ini untuk membuat kode yang dinamis dan fleksibel. 

Hal ini dimungkinkan dengan adanya package reflect.


### Fungsi Package Reflect

Package reflect menyediakan beberapa fungsi dan struktur data yang dapat digunakan untuk membaca informasi tipe data dan nilai pada saat runtime. 

Berikut beberapa contoh penggunaan dari package reflect:
- Mengetahui tipe data sebuah variabel
- Mengakses nilai pada sebuah variabel
- Mengakses metode pada sebuah objek
- Membuat objek baru dari sebuah tipe data
- Mengcopy data dari sebuah slice atau array

### reflect.TypeOf()
{{<singlelinecodeblock text="reflect.TypeOf()">}} berguna untuk mengakses informasi tipe data sebuah variabel.

Berikut adalah contoh kodenya:
```golang
func main() {
	var x int = 10
	fmt.Println("tipe data dari x adalah:", reflect.TypeOf(x))
}
```
Berikut hasil eksekusi kode diatas:
![image info](/023-reflect/pict1.jpg)

Pada kode di atas, kita mendefinisikan sebuah variabel {{<singlelinecodeblock text="x">}} dengan tipe data {{<singlelinecodeblock text="int">}}. 

Kemudian, kita menggunakan fungsi {{<singlelinecodeblock text="reflect.TypeOf()">}} untuk mendapatkan informasi tipe data dari variabel {{<singlelinecodeblock text="x">}}. 

Output yang dihasilkan adalah {{<singlelinecodeblock text="int">}}.

### reflect.Copy()

{{<singlelinecodeblock text="reflect.Copy()">}} berguna untuk mengcopy data dari sebuah array atau slice.

Berikut adalah contoh kodenya:
```golang
func main() {
	nilaiAwal := reflect.ValueOf([]string{"A", "B", "C"})
	tujuan := reflect.ValueOf([]string{"D", "E", "F"})

	// Function Copy() mengembalikan berapa banyak element yang berhasil dicopy
	counter := reflect.Copy(nilaiAwal, tujuan)

	fmt.Println("jumlah counter:", counter)
	fmt.Println("nilaiAwal:", nilaiAwal)
	fmt.Println("tujuan:", tujuan)
}
```

Berikut hasil eksekusi kode diatas:
![image info](/023-reflect/pict2.jpg)

{{<singlelinecodeblock text="reflect.Copy()">}} berguna untuk mengcopy data, bukan mengcopy memory address, jadi cukup berguna jika kita ingin mengcopy data dari 1 array ke array lainnya.

### reflect.DeepEqual()

{{<singlelinecodeblock text="reflect.DeepEqual()">}} adalah sebuah fungsi di Golang yang dapat digunakan untuk membandingkan dua buah nilai. Fungsi ini akan mengembalikan nilai True atau False, tergantung pada apakah kedua nilai tersebut **deeply equal** atau tidak.

Ketika kita berbicara tentang **deeply equal**, kita berbicara tentang kesamaan yang mendalam. 

Nilai array atau slice dikatakan **deeply equal** jika elemen-elemennya yang sesuai sama persis satu sama lain. 

Begitu pula dengan nilai Struct, nilai tersebut dikatakan **deeply equal** jika bidang-bidang yang sesuai sama persis satu sama lain.

DeepEqual sangat berguna untuk membandingkan nilai-nilai kompleks yang terdiri dari beberapa elemen. 

Fungsi ini memudahkan kita dalam memastikan bahwa dua nilai yang kita bandingkan benar-benar sama persis satu sama lain.

Berikut adalah contoh kodenya:
```golang
type Murid struct {
	nama  string
	nilai float64
}

func main() {
	// DeepEqual berguna untuk mengcheck 2 slices equal atau tidak
	s1 := []string{"A", "B", "C", "D", "E"}
	s2 := []string{"D", "E", "F"}
	result := reflect.DeepEqual(s1, s2)
	fmt.Println("s1 dan s2:", result)

	// DeepEqual berguna untuk mengcheck 2 array equal atau tidak
	n1 := [5]int{1, 2, 3, 4, 5}
	n2 := [5]int{1, 2, 3, 4, 5}
	result = reflect.DeepEqual(n1, n2)
	fmt.Println("n1 dan n2:", result)

	// DeepEqual berguna untuk mengcheck 2 struct equal atau tidak
	m1 := Murid{"Budi", 67.6}
	m2 := Murid{"Budi", 67.7}
	m3 := Murid{"Budi", 67.6}
	result = reflect.DeepEqual(m1, m2)
	fmt.Println("m1 dan m2:", result)

	result = reflect.DeepEqual(m3, m1)
	fmt.Println("m1 dan m3:", result)
}
```

Berikut hasil eksekusi kodenya:
![image info](/023-reflect/pict3.jpg)

Bisa kita lihat {{<singlelinecodeblock text="reflect.DeepEqual()">}} dapat diandalkan untuk mengecheck apakah ke dua struct sama persis atau tidak, pada {{<singlelinecodeblock text="m1">}} dan {{<singlelinecodeblock text="m2">}} {{<singlelinecodeblock text="reflect.DeepEqual()">}} mengembalikan nilai false, itu karena nilainya berbeda **0.1**, `67.6` dan `67.7`


### Selengkapnya tentang reflect

Tentunya masih banyak fungsi reflect yang dapat kita gunakan, jika teman2 penasaran bisa buka dokumentasi resminya disini untuk melihat apa saja yang bisa dilakukan package reflect 😆

https://pkg.go.dev/reflect


### Apa selanjutnya?
Selanjutnya kita akan belajar mengenai Goroutine pada golang

Happy learning! 😆