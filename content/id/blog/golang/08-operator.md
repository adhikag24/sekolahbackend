---
title: "Tutorial Golang: Operator"
date: 2023-02-27T01:22:24+07:00
draft: false
author: "Adhika Guna"
tags: ["golang"]
thumbnail: /008-operator/thumbnail.png
description: "Belajar Operator pada Golang"
---

### Operator

Dalam istilah komputer, operator adalah sebuah simbol yang melakukan operasi pada value atau variable.

Contohnya operator {{<singlelinecodeblock text="+">}} melakukan pertambahan pada 2 value


Go menyediakan berbagai operator yang dapat kita kategorikan sebagai berikut:
- Operator Aritmatika
- Operator Perbandingan
- Operator Logika

### Operator Aritmatika
Operator Aritmatika digunakan untuk melakukan operasi bilangan seperti penambahan, pengurangan, perkalian, pembagian, dsb

Berikut table operator aritmatika pada Go:
| Operator| Deskripsi|
|----------|----------|
| + (Addition)  |  Pertambahan | 
| - (Subtraction) |  Pengurangan |
| * (Multiplication) |  Perkalian |
| / (Division) |  Pembagian|
| % (Modulo Division) | Sisa Bagi  |

Berikut contoh kodenya:
```golang
package main
import "fmt"

func main() {
	num1, num2 := 5, 75

	fmt.Println("num1 + num2 =", num1+num2) //num1 + num2 = 80
	fmt.Println("num1 - num2 =", num1-num2) //num1 - num2 = -70
	fmt.Println("num1 * num2 =", num1*num2) //num1 * num2 = 375
	fmt.Println("num1 / num2 =", num1/num2) //num1 / num2 = 0
	fmt.Println("num1 % num2 =", num1%num2) //num1 % num2 = 5
}
```

### Operator Perbandingan
Operator perbandingan digunakan untuk membandingkan 2 / lebih nilai, contohnya kita mau membandingkan apakah 50 sama dengan 70, kita bisa menggunakan operator {{<singlelinecodeblock text="==">}}

Operator perbandingan pada Go mengembalikan value dengan tipe data boolean (true / false)

Berikut table operator perbandingan pada Go:
| Operator| Deskripsi|
|----------|----------|
| == (equal to)  | sama dengan | 
| != (not equal to) | tidak sama dengan |
| > (greater than) | lebih dari |
| < (less than) | kurang dari |
| >= (greater than or equal to) |  lebih dari atau sama dengan  |
| <= (less than or equal to)|  kurang dari atau sama dengan  |

```golang
package main
import "fmt"

func main() {
	num1, num2 := 5, 75
	num3, num4 := 75, 75

	fmt.Println("num1 == num2 =", num1 == num2) //num1 == num2 = false
	fmt.Println("num1 != num2 =", num1 != num2) //num1 != num2 = true
	fmt.Println("num1 > num2 =", num1 > num2)   //num1 > num2 = false
	fmt.Println("num1 < num2 =", num1 < num2)   //num1 < num2 = true
	fmt.Println("num1 >= num2 =", num1 >= num2) //num1 >= num2 = false
	fmt.Println("num3 <= num4 =", num3 <= num4) //num3 <= num4 = true (karna value num3 dan num4 itu sama, maka hasilnya true)
}
```


### Operator Logika
Operatork Logika adalah operator yang digunakan untuk melakukan operasi logika (AND, OR, NOT) kalau kalian pernah belajar Gerbang logika di kuliah / sekolah mungkin akan familiar dengan ini

Operator Logika membandingkan 2 value boolean, dan mengembalikan value dengan tipe data boolean (true / false)

Berikut table operator logika pada Go:
| Operator| Deskripsi|
|----------|----------|
| && (AND) | jika 2 expression sama2 true, maka akan mengembalikan nilai true|  
| \|\| (OR) | jika salah 1 dari 2 expression bernilai true, maka akan mengembalikan nilai true|
| ! (NOT) | mengembalikan true, jika expression false, dan mengembalikan false jika expressionya true |

Berikut contoh kodenya:
```golang
package main
import "fmt"

func main() {
	isUserAdmin := true
	isUserHaveEditAccess := true

	fmt.Println("isUserAdmin && isUserHaveEditAccess =", isUserAdmin && isUserHaveEditAccess) //isUserAdmin && isUserHaveEditAccess = true
	fmt.Println("isUserAdmin || isUserHaveEditAccess =", isUserAdmin || isUserHaveEditAccess) //isUserAdmin || isUserHaveEditAccess = true
	fmt.Println("!isUserAdmin =", !isUserAdmin)                                               //!isUserAdmin = false
}
```


### Apa selanjutnya?

Selanjutnya kita akan belajar kondisi pada golang.

Happy learning! 😆