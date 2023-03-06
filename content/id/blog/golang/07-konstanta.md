---
title: "Tutorial Golang: Konstanta"
date: 2023-02-25T01:47:38+07:00
draft: false
author: "Adhika Guna"
tags: ["golang"]
thumbnail: /007-konstanta/thumbnail.png
description: "Belajar konstanta pada Golang"
---


### Konstanta

Konstanta adalah nilai tetap yang tidak bisa diubah, itu menurut wikipedia ya hehe. 

Cara mendeklarasi konstanta (selanjutnya akan di sebut sebagai const) pada golang sama dengan deklarasi variable tapi dengan keyword `const` 

Const dapat di deklarasi dengan beberapa tipe data seperti char, string, boolean dan numerin (integer dan float)

Const harus di declare sebelum program jalan, contoh program dibawah adalah deklarasi const setelah program jalan yang akan menghasilkan error
```golang
func addMinutes(minutes int) {
	const more = minutes + 60
	return more
}
```

Ada 2 cara untuk mendeklasi const pada golang yaitu, single declaration dan multi declaration


### Single Declaration

Single declaration const bisa di lakukan seperti deklarasi variable, hanya saja tidak bisa menggunakan syntax `:=` untuk deklarasi const
```golang
const second int = 30
const minute string = "60"
const phi float64 = 3.14
```


### Multi declaration

Multi declaration dapat dilakukan dengan kurung `(`

```golang
const (
	second int     = 30
	minute string  = "60"
	phi    float64 = 3.14
)
```



### Apa selanjutnya?

Selanjutnya kita akan belajar operator pada golang.

Happy learning! 😆