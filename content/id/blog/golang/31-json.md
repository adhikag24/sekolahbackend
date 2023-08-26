---
title: "Tutorial Golang: JSON"
date: 2023-04-20T23:40:21+07:00
draft: false
author: "Adhika Guna"
thumbnail: /031-json/thumbnail.png
description: "Belajar menghandle JSON pada Golang"
---

### JSON
JSON atau singkatan dari JavaScript Object Notation adalah format data ringan yang biasa digunakan untuk pertukaran data antara aplikasi. 

JSON sangat populer karena sifatnya yang mudah dipahami oleh manusia dan juga mudah diinterpretasikan oleh mesin. 

JSON berbasis teks dan terdiri dari pasangan `key-value` dan sering disebut sebagai objek.

Sebagai contoh, inilah sebuah objek JSON yang merepresentasikan seorang siswa:
```json
{
  "name": "John Doe",
  "age": 20,
  "address": {
    "street": "123 Main St",
    "city": "New York",
    "state": "NY"
  },
  "courses": ["Math", "Science", "History"]
}
```

### JSON dalam Go

Dalam Go, penggunaan JSON juga sangat umum karena sifatnya yang mudah digunakan dan cepat.

Untuk menggunakan JSON di Golang, kita dapat memakai package `encoding/json`. 

Paket ini berisi fungsi-fungsi yang dibutuhkan untuk mengonversi data Golang menjadi format JSON dan sebaliknya. 

Untuk menghandle data JSON dalam Go, `struct` sering digunakan untuk menghandle data JSON karena memudahkan konversi data dari JSON ke dalam objek atau struktur data yang dapat dikelola oleh aplikasi.

Struktur data yang dibuat menggunakan `struct` juga dapat membantu untuk memvalidasi data dan memastikan data JSON yang diterima memiliki format yang sesuai dengan yang diharapkan.

### Konversi Struct ke JSON


Berikut adalah contoh kode mengkonversi `struct` ke dalam `JSON`:

```golang
type Person struct {
	Name    string `json:"name"`
	Age     int    `json:"age"`
	Address string `json:"address,omitempty"`
}

func main() {
	person := Person{
		Name: "John Doe",
		Age:  30,
	}

	// Encode struct to JSON
	jsonData, err := json.Marshal(person)
	if err != nil {
		panic(err)
	}
	fmt.Println(string(jsonData))
}
```

Pada contoh di atas, terdapat struct Person yang memiliki tiga properti yaitu `Name`, `Age`, dan `Address`. 

Properti-properti ini diberikan tag `json` untuk menentukan namingnya masing-masing propertinya dalam format `JSON`.

Lalu, struct `person` di-encode menjadi format JSON menggunakan fungsi {{<singlelinecodeblock text="json.Marshal()">}}.

Setelah itu, hasilnya di-print pada layar menggunakan fungsi {{<singlelinecodeblock text="fmt.Println()">}}.

Berikut hasil eksekusi kode diatas:
![image info](/031-json/pict1.jpeg)


### Konversi JSON ke struct

Berikut adalah contoh kode mengkonversi `JSON` ke dalam `struct`:

```golang
type Person struct {
	Name    string `json:"name"`
	Age     int    `json:"age"`
	Address string `json:"address,omitempty"`
}

func main() {
	// Decode JSON to struct
	jsonStr := `{"name":"Jane Doe","age":25,"address":"123 Main St"}`
	var person Person

	err := json.Unmarshal([]byte(jsonStr), &person)
	if err != nil {
		panic(err)
	}

	fmt.Printf("%+v\n", person)
	fmt.Printf("%+v\n", person.Name)
}
```

Pada kode diatas, terdapat variabel `jsonStr` yang berisi data JSON. 

Variabel ini kemudian di-decode menjadi `struct person` menggunakan fungsi {{<singlelinecodeblock text="json.Unmarshal()">}}. 

Hasilnya kemudian di-print pada layar menggunakan fungsi {{<singlelinecodeblock text="fmt.Printf()">}}.

Berikut hasil eksekusi kode diatas:
![image info](/031-json/pict3.jpeg)


### Apa selanjutnya?
Selanjutnya kita akan belajar bagaimana menggunakan Regex pada Golang

Happy learning! 😆
