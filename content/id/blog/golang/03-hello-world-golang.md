---
title: "Tutorial Golang: Hello World!"
date: 2023-02-19T22:01:03+07:00
draft: false
author: "Adhika Guna"
tags: ["golang"]
thumbnail: /003-hello-world/thumbnail.png
description: "Belajar membuat program program golang pertama kita, yaitu Hello World!"

---

### Hello World!

Siapa yang ga tau dengan `Hello World!` hello world adalah langkah pertama setiap kita belajar bahasa pemrograman, dan di tutorial kali ini kita akan belajar bagaimana membuat `Hello World!` di golang.

Pertama, kita buka project belajar-golang yang sebelumnya kita buat, lalu buat file baru dengan nama `main.go`, `main.go` ini biasanya adalah file utama dari project golang.

![image info](/003-hello-world/picture1.jpg)


### Setelah itu kita tulis kode seperti berikut: 
```
package main

import "fmt"

func main() {
	fmt.Println("Hello World!")
}

```
lalu kita bisa jalankan program dengan syntax `go run main.go`, dan begini lah hasilnya:
![image info](/003-hello-world/picture2.jpg)


### Penjelasan Kode:

#### package main
Sebenernya package ini hanyalah direktori dalam project Go, dan setiap file memiliki sebuah package.


#### import "fmt"
Import berarti kita sedang memakai / mengimport library dari luar, dan fmt adalah package dari golang yang berguna untuk input / output, di project ini kita pakai package fmt untuk print sebuah string kedalam console.

#### fmt.Println("Hello World!")
Ini berarti kita menggunakan function `Println` dari package `fmt` untuk print Hello World! di console.



### Apa selanjutnya?

Selanjutnya kita akan belajar tentang variable di Go.