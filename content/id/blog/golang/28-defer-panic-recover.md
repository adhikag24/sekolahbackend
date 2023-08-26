---
title: "Tutorial Golang: Defer, Panic and Recover"
date: 2023-04-16T13:22:30+07:00
draft: false
author: "Adhika Guna"
thumbnail: /028-defer-panic-recover/thumbnail.png
description: "Belajar mengenai Defer, Panic dan Recover pada Golang"
---

### Intro

Di tulisan kali ini, kita akan belajar apa itu Defer, Panic dan Recover pada Golang.

3 fitur ini adalah fitur yang jarang dimiliki oleh bahasa pemrograman lain.


### Defer

Mekanisme defer digunakan untuk menunda eksekusi suatu pernyataan atau fungsi sampai fungsi yang memanggilnya selesai dieksekusi. 

>Pernyataan defer dijalankan bahkan jika terjadi kesalahan atau panic pada fungsi yang memanggilnya.

Untuk menggunakan fitur defer, kita dapat menggunakan statement {{<singlelinecodeblock text="defer">}}.

Berikut contoh penggunaan defer pada Go:
```golang
func main() {
    defer fmt.Println("Program selesai dieksekusi")
    
    fmt.Println("Halo, ini adalah program Golang")
}
```

Hasil ekskusi kode diatas:
![image info](/028-defer-panic-recover/pict1.jpeg)

Pada contoh di atas, pernyataan {{<singlelinecodeblock text="fmt.Println('Program selesai dieksekusi')">}} akan dieksekusi setelah pernyataan {{<singlelinecodeblock text="fmt.Println('Halo, ini adalah program Golang')">}} selesai dieksekusi.

Defer menggunakan konsep `First In Last Out`, jadi setiap statement yang menggunakan {{<singlelinecodeblock text="defer">}} akan dimasukan kedalam list, dan statement pertama yang menggunakan {{<singlelinecodeblock text="defer">}} adalah statement paling terakhir akan dieksekusi.

Berikut contoh kodenya:
```golang
func main() {
	defer fmt.Println("Ini di eksekusi pertama")
	defer fmt.Println("Ini di eksekusi ke 2")
	defer fmt.Println("Ini di eksekusi ke 3")

	fmt.Println("Halo, ini adalah program Golang")
}
```

Berikut contoh diagram stacknya:
![image info](/028-defer-panic-recover/pict2.png)

Bisa kita lihat statement {{<singlelinecodeblock text="fmt.Println('Ini di eksekusi pertama')">}} berada di paling bawah stack, yang berarti akan dieksekusi paling terakhir.

Berikut hasil eksekusi kode diatas:
![image info](/028-defer-panic-recover/pict3.jpeg)


### Panic

Panic digunakan untuk menghentikan eksekusi suatu program secara paksa. 

Ketika `panic` terjadi, program akan berhenti dan menampilkan pesan error. 

Panic biasanya terjadi ketika suatu kondisi yang tidak diinginkan terjadi pada program.

Berikut contoh kodenya:
```golang
func main() {
    nilai := 11
    
    if nilai > 10 {
        panic("Nilai tidak boleh lebih dari 10")
    }
    
    fmt.Println("Nilai adalah", nilai)
}
```

Pada contoh di atas, jika nilai lebih besar dari 10, maka program akan mengalami `panic` dan menampilkan pesan `Nilai tidak boleh lebih dari 10`.


Hasil eksekusi kode diatas:
![image info](/028-defer-panic-recover/pict4.jpeg)


Biasanya `panic` juga terjadi pada beberapa kondisi umum seperti:

- Mengakses array atau slice di luar batas: Jika Anda mencoba mengakses elemen array atau slice yang tidak ada (misalnya, dengan menggunakan indeks yang lebih besar dari panjang array), maka akan terjadi panic.
```golang
func main() {
    arr := []int{1, 2, 3}
    fmt.Println(arr[3]) // ini akan memicu panic
}
```
- Dereferensi pointer `nil`: Jika Anda mencoba mengakses nilai dari pointer `nil` (pointer yang tidak menunjuk pada apa pun), maka akan terjadi `panic`.
```golang
func main() {
    var ptr *int
    fmt.Println(*ptr) // Ini akan memicu panic
}
```
- Memanggil metode pada interface `nil`: Jika Anda mencoba memanggil metode pada variabel interface yang `nil`, maka akan terjadi `panic`.
```golang
type MyInterface interface {
    MyMethod()
}

func main() {
    var i MyInterface
    i.MyMethod() // ini akan memicu panic
}
```

- Mengonversi nilai ke `interface` yang tidak diimplementasikan: Jika Anda mencoba mengonversi nilai ke tipe `interface` yang tidak diimplementasikan, maka akan terjadi `panic`.
```golang
type MyInterface interface {
    MyMethod()
}

type MyStruct struct{}

func main() {
    var s MyStruct
    var i MyInterface = s // ini akan memicu panic
}
```
- Mengirim atau menerima pada `channel` yang ditutup: Jika Anda mencoba mengirim atau menerima nilai pada `channel` yang sudah ditutup, maka akan terjadi `panic`.
```golang
func main() {
    ch := make(chan int)
    close(ch)
    ch <- 1 // ini akan memicu panic
}
```

- Pembagian dengan nol: Jika Anda mencoba membagi sebuah angka dengan nol, maka akan terjadi `panic`.
```golang
func main() {
    x := 5
    y := 0
    z := x / y // ini akan memicu panic
}
```


### Recover

Recover digunakan untuk menangkap `panic` yang terjadi pada program. 

Dengan `recover`, kita dapat mengendalikan bagaimana program merespon `panic` tersebut.

Contoh penggunaan recover dalam Go:
```golang
func main() {
    defer func() {
        if r := recover(); r != nil {
            fmt.Println("Panic terjadi:", r)
        }
    }()
    
    nilai := 15
    
    if nilai > 10 {
        panic("Nilai tidak boleh lebih dari 10")
    }
    
    fmt.Println("Nilai adalah", nilai)
}
```

Pada contoh di atas, ketika program mengalami `panic` karena nilai lebih besar dari 10, `recover` akan menangkap `panic` tersebut dan menampilkan pesan `Panic terjadi: Nilai tidak boleh lebih dari 10`.

Berikut hasil eksekusi kode diatas:
![image info](/028-defer-panic-recover/pict5.jpeg)


### Apa selanjutnya?
Selanjutnya kita akan belajar mengenai format string pada Golang

Happy learning! 😆

