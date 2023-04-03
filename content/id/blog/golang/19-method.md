---
title: "Tutorial Golang: Method"
date: 2023-03-28T15:42:33+07:00
draft: false
author: "Adhika Guna"
thumbnail: /019-method/thumbnail.png
description: "Belajar Method pada Golang"
---

### Method

Dalam Go, method sama dengan function, bedanya method memiliki receiver dan hanya dapat dipanggil melalui object / receivernya. 

Berikut contoh syntax untuk membuat method pada Go:
```golang
func (r Receiver) namaFunc(arg int) string {
	return ""
}
```

Lalu untuk memanggilnya, kita dapat melakukan seperti ini:
```golang
result := r.namaFunc(arg)
```

### Receiver

Receiver ini bisa dibilang pemilik dari sebuah method, ketika method dipanggil method akan memiliki nilai dari receivernya.

Begini contohnya:
```golang
type Murid struct {
	nama  string
	kelas string
	umur  int
}

func (m Murid) getNama() string {
	return m.nama
}

func main() {
	murid := Murid{nama: "Budi", kelas: "7B", umur: 12}
	namaMurid := murid.getNama()

	fmt.Println("namaMurid:", namaMurid)
}
```

Hasil eksekusi kode diatas adalah:
```bash
namaMurid: Budi
```

Pada contoh kode diatas, kita menginisiasi variable {{<singlelinecodeblock text="murid">}} dengan struct {{<singlelinecodeblock text="Murid">}} dengan value {{<singlelinecodeblock text="{nama: \"Budi\", kelas: \"7B\", umur: 12}">}}

Lalu saat kita memanggil method {{<singlelinecodeblock text="murid.getName()">}} value yang kita terima adalah {{<singlelinecodeblock text="Budi">}} 

>Method sangat sering digunakan jika kita ingin membuat aplikasi dengan design OOP, setiap object yang dibuat memiliki function yang dapat dipanggil alias method.

### Receiver Pointer

Dalam Go kita juga dapat membuat receiver sebagai pointer, cukup dengan menambahkan symbol {{<singlelinecodeblock text="*">}} sebelum penulisan tipe data.

Begini contohnya:
```golang
func (m *Murid) setNamaToAnton() {
}
```

Dengan menggunakan `receiver pointer`, kita dapat memanipulasi data asli dari objectnya. Sedangkan jika tidak menggunakan pointer (pass by value) jika kita memodifikasi data object didalam function, maka data asli object tersebut tidak akan berubah.

Begini contohnya:
```golang
func (m *Murid) setNamaToAnton() {
	m.nama = "Anton"
}

func (m Murid) setNamaToAnggi() {
	m.nama = "Anggi"
}
func main() {
	murid := Murid{nama: "Budi", kelas: "7B", umur: 12}

	murid.setNamaToAnggi()

	fmt.Println("receiver biasa:", murid.nama)

	murid.setNamaToAnton()

	fmt.Println("receiver pointer:", murid.nama)
}
```

Hasil eksekusi kode diatas:
```bash
receiver biasa: Budi
receiver pointer: Anton
```

Seperti yang kita lihat diatas, ketika memanggil method {{<singlelinecodeblock text="setNamaToAnggi">}}, value dari {{<singlelinecodeblock text="murid.nama">}} tidak berubah valuenya tetap {{<singlelinecodeblock text="Budi">}}.

Tapi ketika memanggil method {{<singlelinecodeblock text="setNamaToAnton">}}, value dari {{<singlelinecodeblock text="murid.nama">}} berubah menjadi {{<singlelinecodeblock text="Anton">}}.

Itu dikarenakan receiver method {{<singlelinecodeblock text="setNamaToAnton">}} adalah pointer.


### Method dapat dibuat dengan tipe data lain selain struct


Perlu diketahui kita dapat membuat method dengan tipe data lain, selain struct.

Kita dapat membuat method dengan semua tipe data seperti, array of string, string, int. 

Selama kita membuatnya sebagai {{<singlelinecodeblock text="type">}} baru.

>Di Go, type digunakan untuk mendefinisikan tipe data bernama baru berdasarkan tipe yang sudah ada.

Berikut contohnya:
```golang
type DaftarMurid []string

func newDaftarMurid(daftarMurid []string) DaftarMurid {
	return daftarMurid
}

func (d DaftarMurid) isDavidExist() bool {
	for _, murid := range d {
		if murid == "David" {
			return true
		}
	}

	return false
}

func main() {
	daftarMurid := newDaftarMurid([]string{"David", "Bagus", "Salma"})

	isDavidExist := daftarMurid.isDavidExist()

	fmt.Println("Apakah David ada:", isDavidExist)
}
```
Hasil eksekusi kode diatas:
```bash
Apakah David ada: true
```

### Apa selanjutnya?
Selanjutnya kita akan belajar mengenai Public dan Private pada golang

Happy learning! 😆






