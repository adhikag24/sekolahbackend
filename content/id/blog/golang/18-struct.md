---
title: "Tutorial Golang: Struct"
date: 2023-03-27T14:45:37+07:00
draft: false
author: "Adhika Guna"
thumbnail: /018-struct/thumbnail.png
description: "Belajar Struct pada Golang"
---

### Struct 

Struct pada golang bisa dibilang sama dengan **class**  pada bahasa pemrograman lain.

Struct berguna untuk mengelompokkan data bersama untuk membentuk kelompok data yang baru.

### Inisialiasi struct

Untuk inisialisasi struct, cukup dengan {{<singlelinecodeblock text="type Murid struct{}">}}. Dengan berikut kita sudah membuat struct kosong bernama {{<singlelinecodeblock text="Murid">}}.

Berikut contoh inisialisasi struct pada Golang:
```golang
type Murid struct {
	nama  string
	kelas string
	umur  int
}
```

Contoh diatas kita berhasil membuat struct {{<singlelinecodeblock text="Murid">}} dengan attribute nama, kelas dan umur.

### Penggunaan struct

Untuk mengassign value pada struct kita bisa melakukannya dengan mengassign value ke masing-masing attribute seperti ini:
```golang
budi := Murid{nama: "Budi", kelas: "7B", umur: 12}
```

Cara seperti ini juga bisa. Inisialisasi struct murid tanpa data (kosong), lalu assign satu-satu datanya.
```golang
budi := Murid{}
budi.nama = "Budi"
budi.kelas = "7B"
budi.umur = 12
```

Hasilnya jika di print akan sama, yaitu:
![image info](/018-struct/pict1.jpg)

Agar membuat kode kita lebih elegan dan rapih, kita dapat membuat function bernama  {{<singlelinecodeblock text="newMurid">}} guna untuk inisialisasi struct  {{<singlelinecodeblock text="Murid">}}. Berikut contohnya:
```golang
type Murid struct {
	nama  string
	kelas string
	umur  int
}

func newMurid(nama, kelas string, umur int) Murid {
	murid := Murid{nama: nama, kelas: kelas, umur: umur}
	return murid
}

func main() {
	budi := newMurid("Budi", "7B", 12)
	fmt.Println(budi) //{Budi 7B 12}
}
```
Dengan cara diatas kita cuku memanggil function {{<singlelinecodeblock text="newMurid">}} ketika ingin inisialisasi struct {{<singlelinecodeblock text="Murid">}}.


### Anonymus struct

Sama dengan function, dalam struct juga kita dapat membuat anonymus struct. Tentu dengan menggunakan closure. Berikut contohnya:
```golang
anonymusStruct := struct {
    nama  string
    umur  int
    kelas string
}{}
```

Anonymus struct cukup berguna, jika kita ingin menggunakan struct hanya dalam 1 function / scope saja, agar tidak perlu mendefinisikan struct lagi.

Cara mengisi value ke anonymus struct:
```golang
anonymusStruct := struct {
    nama  string
    umur  int
    kelas string
}{nama: "Budi", umur: 12, kelas: "7B"}

fmt.Println(anonymusStruct)
```

Hasil eksekusi kode:
![image info](/018-struct/pict2.jpg)



### Nested struct

Dalam Go kita juga dapat membuat nested struct, berikut contohnya:

```golang
type Murid struct {
	nama      string
	kelas     string
	umur      int
	WaliKelas WaliKelas
}

type WaliKelas struct {
	nama          string
	umur          int
	mataPelajaran []string
}
```
Cara penggunaan:
```golang
waliKelas := WaliKelas{nama: "Ibu tetha", umur: 29, mataPelajaran: []string{"Penjas", "MTK", "Fisika", "Kimia"}}
budi := Murid{nama: "Budi", kelas: "7B", umur: 20, WaliKelas: waliKelas}

fmt.Println(budi)//{Budi 7B 20 {Ibu tetha 29 [Penjas MTK Fisika Kimia]}}
```


Bisa juga langsung inisialisasi tanpa membuat struct baru, berikut contohnya:
```golang
type Murid struct {
	nama      string
	kelas     string
	umur      int
	WaliKelas struct {
		nama          string
		umur          int
		mataPelajaran []string
	}
}
```

Cara penggunaan:
```golang
waliKelas := struct {
    nama          string
    umur          int
    mataPelajaran []string
}{nama: "Ibu tetha", umur: 29, mataPelajaran: []string{"Penjas", "MTK", "Fisika", "Kimia"}}
budi := Murid{nama: "Budi", kelas: "7B", umur: 20, WaliKelas: waliKelas}

fmt.Println(budi)//{Budi 7B 20 {Ibu tetha 29 [Penjas MTK Fisika Kimia]}}
```

Namun cara ke-2 kurang direkomendasikan, karna struct tidak terdefinisi dengan baik alias anonymus struct.

### Kombinasi slice dan struct
Tentu saja saat membuat aplikasi nanti, kita akan sering menggunakan kombinasi slice dan struct. Jika kita ingin menerima data dari database, kita pasti menampungnya dalam slice of struct.

Berikut contoh inisialisasi slice dengan struct:
```golang
daftarMurid := []Murid{}
```

Berikut contoh inisialisasi dan pengisian data slice dengan struct:
```golang
daftarMurid := []Murid{
    {nama: "Budi", kelas: "7B", umur: 12},
    {nama: "Adhika", kelas: "7B", umur: 12},
    {nama: "Ratni", kelas: "7B", umur: 12},
    {nama: "Doni", kelas: "7B", umur: 12},
    {nama: "Salma", kelas: "7B", umur: 12},
}

fmt.Println(daftarMurid) 
```

Hasil eksekusi kode:
![image info](/018-struct/pict3.jpg)

### Membuat pointer struct

Kita juga dapat membuat pointer struct, caranya sama dengan penggunaan pointer pada umumnya, kita menampung memory address dari variable lain.

Berikut contohnya:
```golang
budi := Murid{nama: "Budi", kelas: "7B", umur: 12}
budiPointer := &budi

fmt.Println("budi:", budi)
fmt.Println("budi2:", *budiPointer)
```
Hasil eksekusi kode diatas:
![image info](/018-struct/pict4.jpg)

Kita juga dapat membuat pointer struct kosong dengan menggunakan {{<singlelinecodeblock text="new()">}}. 

Berikut contohnya:
```golang
budiPointer := new(Murid)
budiPointer.nama = "Budi"
budiPointer.kelas = "7B"
budiPointer.umur = 12

fmt.Println("budiPointer:", *budiPointer)
```
Hasil eksekusi kode diatas:
![image info](/018-struct/pict5.jpg)


### Apa selanjutnya?
Selanjutnya kita akan belajar method pada golang

Happy learning! 😆





