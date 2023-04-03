---
title: "Tutorial Golang: Pointer"
date: 2023-03-26T15:24:31+07:00
draft: false
author: "Adhika Guna"
thumbnail: /017-pointer/thumbnail.png
description: "Belajar Pointer pada Golang"
---

### Pointer

Bahasa pemrograman Go memiliki pointer, mungkin buat yang pernah belajar bahasa C dan C++ ga asing lagi ya dengan namanya pointer.

Pointer itu fungsinya untuk menampung memory address dari sebuah value / variable.

>Variable dan Pointer itu 2 hal yang berbeda, walau cara deklarasinya mirip.

Keuntungan pointer kita dapat menyimpan value {{<singlelinecodeblock text="nil">}} 

### Inisialisasi Pointer

Cara inisialisasi pointer sama dengan inisialisasi variable pada umumnya, hanya saja untuk pointer ditandai dengan symbol {{<singlelinecodeblock text="*">}} sebelum penulisan tipe data.

Berikut contohnya:
```golang
var pointerInteger *int
```

Kita juga dapat inisialisasi pointer dengan operator {{<singlelinecodeblock text=":=">}}, dengan catatan kita langsung menginisalisasi dengan memberikan memory address variable yang sudah ada, tidak bisa deklarasi data kosong.

Berikut contohnya:
```golang
value := 56
pointerInteger := &value
```

Inisilisasi dengan keyword {{<singlelinecodeblock text="new">}}. Dengan keyword {{<singlelinecodeblock text="new">}} pada golang, kita dapat inisialisasi pointer kosong.

Berikut contohnya:
```golang
pointerInteger := new(int)
```

### Fungsi operator * dan &
Nah sebelum lanjut baiknya kita membahas apa fungsi dari operator {{<singlelinecodeblock text="*">}} dan {{<singlelinecodeblock text="&">}}.

Simplenya:
- {{<singlelinecodeblock text="*">}} mengembalikan value dibalik memory address yang disimpan pointer (contohnya: 5,6,7,8,9,10)
```golang
stringValue := "ini adalah pointer"
boolValue := true
integerValue := 123123123

stringPointer := &stringValue
boolPointer := &boolValue
integerPointer := &integerValue

fmt.Println(*stringPointer) //ini adalah pointer
fmt.Println(*boolPointer) //true
fmt.Println(*integerPointer) //123123123
```
- {{<singlelinecodeblock text="&">}} mengembalikan memory address dari variable (contohnya: 0x14000104220,0x1400011c002,0x1400011c008)
```golang
stringPointer := "ini adalah pointer"
boolPointer := true
integerPointer := 123123123

fmt.Println(&stringPointer) //0x14000104220
fmt.Println(&boolPointer) //0x1400011c002
fmt.Println(&integerPointer) //0x1400011c008
```


### Mengubah value pointer sama dengan mengubah value dari variable yang disimpan


Hati2 jika ingin mengubah valu dari pointer, pastikan value sebelumnya sudah tidak terpakai / aman untuk di ubah juga. 

Ketika kita ingin mengubah value pada pointer, secara otomotasi value pada variable yang sebelumnya di assign ke pointer akan ikut berubah juga itu terjadi karena pointer menyimpan memory address dari variable, jadi akan saling terhubung.

Berikut contohnya:
```golang
stringValue := "ini adalah pointer"
stringPointer := &stringValue

fmt.Println("stringValue:", stringValue) //stringValue: ini adalah pointer
fmt.Println("stringPointer:", *stringPointer) //stringPointer: ini adalah pointer

*stringPointer = "value diubah nih"
 
fmt.Println("stringValue:", stringValue) //stringValue: value diubah nih
fmt.Println("stringPointer:", *stringPointer) //stringPointer: value diubah nih
```
Hasil eksekusi kode diatas:
![image info](/017-pointer/pict1.jpg)


### Pointer dapat menyimpan nil

Ini nilai plus dari pointer, kita dapat menyimpan nil.

Dengan menyimpan {{<singlelinecodeblock text="nil">}} dapat mempermudah kita dalam melakukan validasi, jadi dari pada menyimpan value kosong seperti 0 lebih baik menyimpannya sebagai {{<singlelinecodeblock text="nil">}}.

```golang
var integerPointer *int
	integerPointer = nil

	if integerPointer == nil {
		fmt.Println("integerPointer:", integerPointer)
	}
```
Hasil eksekusi kode diatas:
![image info](/017-pointer/pict2.jpg)


### Apa selanjutnya?
Selanjutnya kita akan belajar struct pada golang

Happy learning! 😆
