---
title: "Tutorial Golang: Regex"
date: 2023-04-21T22:13:07+07:00
draft: false
author: "Adhika Guna"
thumbnail: /032-regex/thumbnail.png
description: "Belajar menggunakan Regex pada Golang"
---

### Regex

Regex atau Regular Expression adalah sebuah teks yang berisi pola yang digunakan untuk mencocokkan teks lainnya. Dalam bahasa pemrograman, penggunaan regex dapat membantu dalam mencari atau memproses sebuah string secara spesifik.

Contohnya, kita dapat menggunakan regex untuk mencocokkan sebuah email, nomor telepon, atau mencari sebuah kata dalam sebuah dokumen. 

Pola regex terdiri dari karakter-karakter atau meta-karakter yang memiliki arti spesifik, seperti huruf, angka, karakter spesial, tanda kurung, tanda kurung siku, tanda kurung kurawal, dan sebagainya.

Beberapa meta-karakte penting yang sering digunakan dalam regex adalah:

- `^` (caret) yang digunakan untuk mencocokkan karakter pada awal string.
- `$` (dollar) yang digunakan untuk mencocokkan karakter pada akhir string.
- `.` (dot) yang digunakan untuk mencocokkan karakter apapun kecuali karakter newline.
- `*` (asterisk) yang digunakan untuk mencocokkan nol atau lebih dari karakter sebelumnya.
- `+` (plus) yang digunakan untuk mencocokkan satu atau lebih dari karakter sebelumnya.
- `?` (question mark) yang digunakan untuk mencocokkan nol atau satu karakter sebelumnya.
- `[]` (square brackets) yang digunakan untuk mencocokkan karakter yang berada di dalam tanda kurung siku.
- `()` (parentheses) yang digunakan untuk mengelompokkan bagian-bagian dari pola regex.
- `|` (vertical bar) yang digunakan untuk mencocokkan dua atau lebih pola regex.

Dengan menggunakan kombinasi karakter-karakter dan meta-karakter tersebut, kita dapat membuat pola regex yang sesuai dengan kebutuhan. 

Namun, karena kompleksitas pola regex dapat sangat tinggi, maka diperlukan latihan dan pengalaman untuk dapat menguasai penggunaan regex secara efektif.

### Contoh pola regex yang umum digunakan

Berikut ini adalah beberapa contoh pola regex yang umum digunakan:

- Pola regex untuk mencari kata tertentu dalam sebuah teks:
```golang
polaRegex := regexp.MustCompile(`kata yang ingin dicari`)
```
Penjelasan: Pola regex ini akan mencocokkan setiap kali terdapat kata yang ingin dicari dalam teks.


- Pola regex untuk mencari email:
```golang
polaRegex := regexp.MustCompile(`[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}`)
```
Penjelasan: Pola regex ini akan mencocokkan setiap kali terdapat format email yang valid dalam teks.

- Pola regex untuk mencari nomor telepon:

```golang
polaRegex := regexp.MustCompile(`^\+?\d{2}[-.\s]?\d{3}[-.\s]?\d{3}[-.\s]?\d{4}$`)
```
Penjelasan: Pola regex ini akan mencocokkan setiap kali terdapat format nomor telepon yang valid dalam teks, seperti +62-123-456-7890 atau 0812 123 4567.

- Pola regex untuk mencari URL:
```golang
polaRegex := regexp.MustCompile(`https?://[^\s]+`)
```
Penjelasan: Pola regex ini akan mencocokkan setiap kali terdapat URL dalam teks, seperti `http://www.google.com` atau `https://www.youtube.com/watch?v=dQw4w9WgXcQ`.

- Pola regex untuk mencari kata yang diawali dengan huruf tertentu:

```golang
polaRegex := regexp.MustCompile(`\b[hH]\w+`)
```
Penjelasan: Pola regex ini akan mencocokkan setiap kali terdapat kata yang diawali dengan huruf `h` atau `H` dalam teks.

- Pola regex untuk mencari angka:

```golang
polaRegex := regexp.MustCompile(`\d+`)
```
Penjelasan: Pola regex ini akan mencocokkan setiap kali terdapat satu atau lebih angka dalam teks.

- Pola regex untuk mencari karakter non-alphanumeric:
```golang
polaRegex := regexp.MustCompile(`\W+`)
```
Penjelasan: Pola regex ini akan mencocokkan setiap kali terdapat satu atau lebih karakter non-alphanumeric dalam teks, seperti spasi, tanda baca, atau karakter khusus lainnya.


### Regex di Go

Go memiliki sebuah package yang disebut `regexp` yang dapat digunakan untuk bekerja dengan regex. 

Dalam paket ini, terdapat dua jenis fungsi yang dapat digunakan yaitu fungsi {{<code text="FindString">}} dan fungsi {{<singlelinecodeblock text="MatchString">}}.

### FindString & MatchString
Fungsi {{<code text="FindString">}} akan mencari sebuah string yang cocok dengan pola yang diberikan, sedangkan fungsi {{<code text="MatchString">}} akan mencocokkan seluruh string yang ada dalam teks dengan pola yang diberikan. 

Berikut adalah contoh penggunaannya:
```golang
package main

import (
	"fmt"
	"regexp"
)

func main() {
	r, _ := regexp.Compile("p([a-z]+)ch")

	fmt.Println(r.FindString("peach punch"))
	fmt.Println(r.FindString("The quick brown fox jumps over the lazy dog"))
	fmt.Println(r.MatchString("peach punch"))
}
```

Hasil eksekusi kode diatas:
![image info](/032-regex/pict1.jpeg)


Pada contoh di atas, kita menggunakan package `regexp` dan membuat sebuah variabel `r` yang merupakan hasil dari kompilasi pola regex {{<code text="p([a-z]+)ch">}}. 

Selanjutnya, kita menggunakan fungsi {{<code text="FindString">}} untuk mencari string yang cocok dengan pola tersebut pada string `"peach punch"` dan `""The quick brown fox jumps over the lazy dog""`. 

Hasilnya adalah `"peach"` dan `""` (karena tidak ada yang cocok). 

> Kenapa hasilnya `"peach"`, bukan `"peach punch"`? itu karena function {{<code text="FindString">}} mengembalikan string pertama yang ditemukan, karena string `"peach"` ditemukan terlebih dahulu, maka value tersebut yang dikembalikan.

Kemudian, kita juga menggunakan fungsi {{<code text="MatchString">}} untuk mencocokkan seluruh string pada string `"peach punch"`. 

Hasilnya adalah true karena string tersebut cocok dengan pola regex yang diberikan.

Selain itu, Go juga memiliki beberapa fungsi lain yang dapat digunakan dalam pengolahan regex seperti {{<code text="ReplaceAllString">}} dan {{<code text="Split">}}. 


### ReplaceAllString 

Fungsi {{<code text="ReplaceAllString">}} digunakan untuk mengganti setiap substring yang cocok dengan pola regex dengan string lain.

Berikut adalah contoh penggunaannya:

```golang
package main

import (
   "fmt"
   "regexp"
)

func main() {
   polaRegex := regexp.MustCompile(`\bdia\b|\bDia\b`)
   teks := "Dia pergi ke pasar dan membeli beberapa barang."
   teksBaru := polaRegex.ReplaceAllString(teks, "saya")
   fmt.Println(teksBaru)
}
```

Berikut hasil eksekusi kode diatas:
![image info](/032-regex/pict3.jpeg)

Pada contoh diatas pola regex {{<code text="\bdia\b">}} akan mencocokkan setiap kata `"dia"` (tidak diikuti atau diawali oleh huruf lain) dan fungsi {{<code text="ReplaceAllString()">}} akan mengganti setiap substring yang cocok dengan pola regex tersebut dengan string `"saya"`.

### Split

Fungsi {{<code text="Split()">}} digunakan untuk memisahkan sebuah string menjadi beberapa substring berdasarkan pola regex.

Berikut contohnya:
```golang
package main

import (
   "fmt"
   "regexp"
)

func main() {
   polaRegex := regexp.MustCompile(`[\s,;]+`)
   teks := "Ini adalah beberapa, teks; untuk di-split."
   hasilSplit := polaRegex.Split(teks, -1)
   for _, substring := range hasilSplit {
      fmt.Println(substring)
   }
}
```

Berikut hasil eksekusi kode diatas:
![image info](/032-regex/pict4.jpeg)

Pada contoh diatas pola regex {{<code text="[\s,;]+">}} akan mencocokkan setiap karakter spasi, koma, atau titik koma yang muncul satu kali atau lebih. 

Fungsi {{<code text="Split()">}} akan memisahkan teks menjadi beberapa substring berdasarkan pola regex tersebut, dan mengembalikan hasil split dalam bentuk array slice yang dapat diiterasi dengan {{<code text="for loop">}}.


### Apa selanjutnya?
Selanjutnya kita akan belajar mengenai WaitGroup pada Golang

Happy learning! 😆
