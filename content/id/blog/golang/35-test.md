---
title: "Tutorial Golang: Unit Test"
date: 2023-06-11T23:23:35+07:00
draft: false
author: "Adhika Guna"
thumbnail: /035-test/thumbnail.png
description: "Belajar mengenai Unit Test pada Golang"
---


### Unit Testing

Unit testing adalah proses pengujian perangkat lunak yang fokus pada pengujian unit-unit terkecil dari sebuah program, seperti fungsi atau metode. Dalam bahasa pemrograman Golang, unit testing sangat didukung dan telah disediakan oleh testing package bawaan. Dalam panduan ini, kita akan membahas cara melakukan unit testing di Golang menggunakan {{<code text="testing">}} package.

### Membuat Test

Misalnya kita punya fungsi {{<code text="Add">}} yang kita ingin buatkan testnya. 

Berikut kode fungsi {{<code text="Add">}}:
```golang
func Add(num1, num2 int) int{
   return num1 + num2
}
```

Mari kita buat testnya.

#### Import Package testing
Di awal file {{<code text="test">}}, import package testing seperti berikut:

```golang
import (
    "testing"
)
```

#### Persiapan File Test
Buat file test yang terpisah untuk setiap file sumber yang ingin diuji. Misalnya, jika kita memiliki file `calculator.go` yang ingin diuji, buat file baru bernama `calculator_test.go`. 

Pastikan file test menggunakan nama yang sama dengan file sumber yang ingin diuji, dengan tambahan sufiks _test.

Untuk contoh kita mari kita buat file `add_test.go`.

#### Import Package testing
Di awal file {{<code text="test">}}, import package testing seperti berikut:

```golang
import (
    "testing"
)
```

#### Menulis Fungsi Test
Setiap fungsi test harus memiliki signature yang mengikuti pola `func TestXxx(t *testing.T)`, di mana Xxx adalah nama fungsi yang ingin kita uji. 

Fungsi test harus menerima parameter t *testing.T yang merupakan testing.T object yang digunakan untuk melaporkan hasil pengujian.

Berikut adalah contoh fungsi test untuk fungsi {{<code text="Add">}}:
```golang
func TestAdd(t *testing.T) {
    result := Add(2, 3)
    expected := 5

    if result != expected {
        t.Errorf("Expected %d, but got %d", expected, result)
    }
}
```

Dalam contoh di atas, kita menguji fungsi `Add` yang mengharapkan hasil penjumlahan 2 dan 3 sebesar 5. 

Jika hasil yang dikembalikan tidak sesuai dengan yang diharapkan, kita menggunakan `t.Errorf` untuk memberikan pesan error yang spesifik.


#### Menjalankan Unit Test
Untuk menjalankan unit test, cukup jalankan perintah {{<code text="go test">}} dari terminal di direktori proyek kita. 

Golang akan secara otomatis menemukan dan menjalankan semua fungsi test yang ada. Hasil pengujian akan ditampilkan di terminal.

Berikut hasilnya:
![image info](/035-test/pict1.jpeg)

#### Menjalankan Spesifik Fungsi Test
Jika kita hanya ingin menjalankan satu fungsi test tertentu, kita dapat menggunakan argumen `-run` saat menjalankan perintah go test. 

Misalnya, jika kita hanya ingin menjalankan fungsi test {{<code text="TestAdd">}}, gunakan perintah berikut:
```bash
go test -run TestAdd
```

#### Menambahkan assertion
Assertion digunakan untuk memastikan bahwa kondisi yang diharapkan dalam unit test terpenuhi. 

Golang tidak memiliki assertion bawaan seperti bahasa pemrograman lain, tetapi kita dapat menggunakan `testify package` untuk melakukan hal tersebut. 

Sebelum menggunakan assertion kita harus mengimport `package testify` terlebih dahulu seperti ini:
```golang
import (
	"github.com/stretchr/testify/assert"
)
```

Berikut kita modifikasi test diatas agar menggunakan assertion:
```golang
package main

import (
	"testing"
	"github.com/stretchr/testify/assert"
)

func TestAdd(t *testing.T) {
	result := Add(2, 3)
	expected := 5

	assert.Equal(t, result, expected)
}
```

### Benchmarking
Selain melakukan unit testing, Golang juga mendukung benchmarking untuk mengukur kinerja program. 

Kita dapat menambahkan fungsi benchmark yang mengikuti pola `func BenchmarkXxx(b *testing.B)`, di mana Xxx adalah nama fungsi yang ingin di-benchmark. 

Fungsi benchmark harus menggunakan parameter `b *testing.B` yang digunakan untuk mengontrol dan melaporkan hasil benchmark. 

Berikut adalah contoh penggunaan benchmark pada fungsi `Add`:
```golang
func BenchmarkAdd(b *testing.B) {
    for i := 0; i < b.N; i++ {
        Add(2, 3)
    }
}
```

Dalam contoh di atas, kita menguji kinerja fungsi Add dengan melakukan penjumlahan 2 dan 3 sebanyak `b.N` kali. 

Value `b.N` ditentukan secara otomatis oleh package `testing` untuk menentukan jumlah iterasi yang optimal agar mendapatkan hasil pengujian yang akurat dan dapat diandalkan.

Hasil benchmark akan mencakup waktu yang dibutuhkan untuk menjalankan operasi tersebut.

Kita dapat menjalankan unit test dan benchmark secara bersamaan menggunakan command {{<code text="go test -bench .">}}.

`-bench` akan menjalankan semua fungsi benchmark yang ada.

Berikut hasil dari benchmark diatas:
![image info](/035-test/pict2.jpeg)


### Menampilkan Detail
Golang memiliki fitur verbose yang dapat digunakan untuk menampilkan detail hasil pengujian. 

Untuk mengaktifkan fitur ini, gunakan argumen -v saat menjalankan perintah go test.

Contoh: {{<code text="go test -v">}}.