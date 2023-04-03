---
title: "Tutorial Golang: Variadic Function"
date: 2023-03-20T22:24:21+07:00
draft: false
author: "Adhika Guna"
thumbnail: /015-variadic/thumbnail.png
description: "Belajar Variadic Function pada Golang"
---


### Variadic Function

Function variadic adalah function yang dapat menerima banyak argument sekaligus. Bukan berarti kita harus mendefine banyak parameter juga, dalam variadic function kita cukup mendefinisikan 1 parameter tapi saat definisi parameter kita harus menambahkan dengan symbol variadic {{<singlelinecodeblock text="...">}} sebelum tipe data. 

Berikut contohnya:
```golang
func sum(nums ...int) int {
	return -1
}
```

### Pemakaian parameter Variadic function

Cara pemakaian parameter variadic sama dengan array, jadi secara tidak langsung parameter {{<singlelinecodeblock text="nums">}} dicontoh atas, adalah {{<singlelinecodeblock text="array of integer">}}

Berikut contoh kodenya:
```golang
func main() {
	total := sum(3, 5, 10, 2, 4, 5, 2, 3)
	fmt.Println("total:", total) //total: 34

}

func sum(nums ...int) int {
	fmt.Println("nums:", nums) //nums: [3 5 10 2 4 5 2 3]

	total := 0

	for _, num := range nums {
		total = total + num
	}

	return total
}
```

### Normal function parameter dengan variadic function parameter

Apakah variadic function bisa memakain normal parameter juga? Tentu saja bisa. 

Variadic parameter diwajibkan ditaruh di akhir parameter {{<singlelinecodeblock text="func sum(operator string, nums ...int)">}}

Jika variadic parameter ditaruh sebelum normal parameter, akan terjadi error {{<singlelinecodeblock text="./main.go:11:32: can only use ... with final parameter in list">}}

Berikut contoh kodenya:
```golang
func main() {
	total := sum("*", 3, 5, 10, 2, 4, 5, 2, 3)
	fmt.Println("total:", total)

}

func sum(operator string, nums ...int) (total int) {
	fmt.Println("nums:", nums)

	switch operator {
	case "+":
		for _, num := range nums {
			total = total + num
		}
	case "*":
		for _, num := range nums {
			if total == 0 {
				total = num
				continue
			}
			total = total * num
		}
	default:
		return -1
	}

	return total
}
```

### Bisakah sebuah function memiliki lebih dari 1 variadic parameter?

Sayangnya dalam Go, kita tidak dapat membuah sebuah function dengan lebih dari 1 variadic parameter.


### Variadic Function dengan interface{} 

Kita dapat membuat function yang dapat menerima parameter apapun, dengan cara membuat function dengan variadic {{<singlelinecodeblock text="interface{}">}} sebagai parameter, dikarenakan {{<singlelinecodeblock text="interface{}">}} dapat menerima semua tipe data.

Berikut contoh kodenya:
```golang
func main() {
	contohVariadic(1, "red", true, 10.5, []string{"foo", "bar", "baz"}, map[string]int{"apple": 23, "tomato": 13})
}

func contohVariadic(any ...interface{}) {
	for _, v := range any {
		fmt.Println(v, "--", reflect.ValueOf(v).Kind())
	}
}
```

Hasil eksekusi kode diatas:
![image info](/015-variadic/pict1.jpg)

### Apa selanjutnya?
Selanjutnya kita akan belajar function closure pada golang

Happy learning! 😆
