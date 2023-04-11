---
title: "Tutorial Golang: Interface"
date: 2023-04-03T22:05:12+07:00
draft: false
author: "Adhika Guna"
thumbnail: /021-interface/thumbnail.png
description: "Belajar Interface pada Golang"
---

### Interface

Interface adalah salah satu fitur penting yang ada di bahasa pemrograman Go (Golang). Interface membantu developer dalam membuat kode yang fleksibel dan mudah di-maintain. 

Interface adalah kumpulan definisi method tanpa implementasi yang digunakan sebagai template untuk mengimplementasikan fungsi yang berbeda-beda dari satu tipe data. 

Artinya, interface memberikan sebuah blueprint tentang fungsi apa yang harus diimplementasikan oleh suatu tipe data yang memenuhi syarat-syarat yang telah ditentukan oleh interface.

Setiap tipe yang memenuhi semua metode dalam sebuah interface dianggap sebagai implementasi dari interface tersebut. 

Ini berarti bahwa tidak ada deklarasi eksplisit yang diperlukan untuk mengimplementasikan sebuah interface. 

Sebagai contoh, jika kita memiliki sebuah interface bernama {{<singlelinecodeblock text="Printer">}} dengan metode {{<singlelinecodeblock text="Print()">}}, maka kita dapat membuat implementasi untuk tipe data apa pun yang memiliki metode {{<singlelinecodeblock text="Print()">}}.


### Inisialisasi Interface 

Kita dapat inisialisasi Interface dengan sintaks {{<singlelinecodeblock text="type <nama_interface> interface {}">}}

Berikut Contohnya:
```golang
type NamaInterface interface {
    namaMethod1(param1 type1, param2 type2) returnType1
    namaMethod2(param3 type3, param4 type4) returnType2
    // ...
}
```

### Cara menggunakan Interface

Sebagai contoh kita buat interface dengan nama {{<singlelinecodeblock text="Shape">}} dengan method {{<singlelinecodeblock text="Luas()">}} yang mengembalikan nilai {{<singlelinecodeblock text="float64">}}

```golang
type Shape interface {
    Luas() float64
}
```
Selanjutnya, mari kita lihat bagaimana kita dapat mengimplementasikan interface tersebut.

Sebagai contoh, kita akan membuat implementasi {{<singlelinecodeblock text="interface Shape">}} untuk tipe {{<singlelinecodeblock text="Rectangle">}}. 

Berikut adalah contohnya:
```golang
type Rectangle struct {
    width  float64
    height float64
}

func (r Rectangle) Luas() float64 {
    return r.width * r.height
}
```

Dalam contoh diatas, kita membuat sebuah struct bernama {{<singlelinecodeblock text="Rectangle">}} yang memiliki dua properti: {{<singlelinecodeblock text="width">}} dan {{<singlelinecodeblock text="height">}}. 

Kemudian, kita mendefinisikan sebuah fungsi bernama {{<singlelinecodeblock text="Luas()">}} yang mengembalikan nilai luas persegi panjang.

Setelah kita membuat implementasi, kita dapat menggunakannya dengan cara yang sama seperti kita menggunakan tipe data lainnya. 


Berikut adalah contoh penggunaan interface {{<singlelinecodeblock text="Shape">}}:
```golang
func main() {
    var s Shape = Rectangle{width: 5, height: 10}
    fmt.Println("Luas dari Rectangle:", s.Luas())
}
```
Berikut hasil eksekusi kode diatas:
![image info](/021-interface/pict1.jpg)

> Perlu diingat, kita tidak perlu secara eksplisit mendeklarasi bahwa Rectangle adalah implementasi dari interface Shape, jika mereka memiliki method yang sama, maka secara tidak langsung Rectangle adalah implementasi dari Shape

Sekarang kita mencoba untuk menambahkan 1 method lagi pada {{<singlelinecodeblock text="Shape">}}, yaitu {{<singlelinecodeblock text="Keliling">}}.

Tambahkan method {{<singlelinecodeblock text="Keliling()">}} pada {{<singlelinecodeblock text="Shape">}} seperti ini:
```golang
type Shape interface {
    Luas() float64
    Keliling() float64
}
```

Jika kalian ikut mencoba, pasti akan terjadi error seperti ini:
![image info](/021-interface/pict2.jpg)


Ini dikarenakan struct {{<singlelinecodeblock text="Rectangle">}} tidak lagi implementasi {{<singlelinecodeblock text="Shape">}} karena struct {{<singlelinecodeblock text="Rectangle">}} tidak memiliki method {{<singlelinecodeblock text="Keliling()">}}
 

Mari kita tambahkan method {{<singlelinecodeblock text="Keliling()">}} pada {{<singlelinecodeblock text="Rectangle">}}

```golang
func (r Rectangle) Keliling() float64 {
	return 2 * (r.height + r.width)
}
```

Jika kita check lagi, sekarang pasti errornya sudah hilang, itu karena kita sudah menambahkan method {{<singlelinecodeblock text="Keliling()">}} pada {{<singlelinecodeblock text="Rectangle">}}.

Kode untuk memanggil method {{<singlelinecodeblock text="Keliling()">}}:
```golang
func main() {
	var s Shape = Rectangle{width: 5, height: 10}
	fmt.Println("Luas of rectangle:", s.Luas())
	fmt.Println("Keliling of rectangle:", s.Keliling())
}
```

Hasil eksekusi kode diatas:
![image info](/021-interface/pict3.jpg)


### Apa selanjutnya?
Selanjutnya kita akan belajar mengenai interface kosong pada golang

Happy learning! 😆