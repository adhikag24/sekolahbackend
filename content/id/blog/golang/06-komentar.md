---
title: "Tutorial Golang: Komentar"
date: 2023-02-25T00:59:12+07:00
draft: false
author: "Adhika Guna"
tags: ["golang"]
thumbnail: /006-komentar/thumbnail.png
description: "Belajar komentar pada Golang"
---

### Komentar

Hampir semua bahasa pemrograman memiliki sintaks untuk menambahkan komentar ke kode, dan tentu saja Go juga mempunyainya. Komentar adalah baris dalam program yang menjelaskan dalam bahasa manusia bagaimana kode bekerja atau mengapa ditulis seperti itu. 

Komentar itu diabaikan oleh kompiler, compiler tidak akan mengkompile komentar. Komentar menambahkan informarsi berharga yang membantu 
kolaborator / programmer lain atau diri kita di masa depan untuk memahami kode biar kode lebih mudah di kelola dan maintain.

Ada 2 macam comment di Go, yaitu Single Line comment dan Multi line comment.

### Single Line Comment

Single Line Comment pada Go, kita dapat menggunakan syntax `'//'`, berikut adalah contohnya
```golang
// sum adalah function untuk menjumlah 2 integer
// [param] num1, num2 integer
func sum(num1, num2 int) int {
	return num1 + num2
}
```

### Multi Line Comment

Multi Line Comment pada Go, kita dapat menggunakan syntax `'/*'` untuk membuka dan `'*/'` untuk menutup komentar, berikut adalah contohnya
```golang
/* 
   sum adalah function untuk menjumlah 2 integer
   [param] num1, num2 integer
*/
func sum(num1, num2 int) int {
	return num1 + num2
}
```

### Apa selanjutnya?

Selanjutnya kita akan belajar konstanta pada golang.

Happy learning! 😆