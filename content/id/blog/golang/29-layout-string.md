---
title: "Tutorial Golang: Format String"
date: 2023-04-17T16:38:27+07:00
draft: false
author: "Adhika Guna"
thumbnail: /029-format-string/thumbnail.png
description: "Belajar mengenai Format String pada Golang"
---


### Format String

Format string merupakan salah satu fitur yang penting di dalam bahasa pemrograman Golang. Format string digunakan untuk memformat tampilan output yang dihasilkan oleh program Golang. Dalam Golang, format string diwakili oleh package "fmt".

Format string di Golang menggunakan placeholder yang diawali dengan karakter "%" dan diikuti oleh tipe data yang akan ditampilkan. 


### Contoh Penggunaan Format String

Berikut adalah beberapa contoh penggunaan format string di Golang:

1. Menampilkan nilai integer:
```golang
func main() {
    var x int = 42
    fmt.Printf("Nilai x = %d\n", x)
}
```

Output dari kode diatas:
```bash
Nilai x = 42
```

2. Menampilkan nilai float:
```golang
func main() {
    var pi float64 = 3.14159265358979323846
    fmt.Printf("Nilai pi = %f\n", pi)
}
```

Output dari kode diatas:
```bash
Nilai pi = 3.141593
```

Secara default, {{<singlelinecodeblock text="Printf">}} hanya akan mencetak 6 digit dibelakang koma untuk nilai float ketika menggunakan format specifier {{<singlelinecodeblock text="%f">}}.

Jika kita ingin menampilkan full digit dari nilai float, kita dapat menggunakan format specifier {{<singlelinecodeblock text="%g">}} sebagai ganti {{<singlelinecodeblock text="%f">}}. 

{{<singlelinecodeblock text="%g">}} akan menggunakan jumlah digit terkecil yang diperlukan untuk merepresentasikan nilai float dengan akurat, sehingga akan menampilkan presisi penuh dari nilai tersebut. 

Berikut adalah contoh menggunakan {{<singlelinecodeblock text="%g">}}:
```golang
func main() {
    var pi float64 = 3.14159265358979323846
    fmt.Printf("Nilai pi = %g\n", pi)
}
```
Output dari kode diatas:
```bash
Nilai pi = 3.141592653589793
```


Jika kita ingin menampilkan hanya 2 digit saja dibelakang koma, kita dapat menggunakan {{<singlelinecodeblock text="%.2f">}}.

Berikut contoh kodenya:
```golang
func main() {
    var pi float64 = 3.14159265358979323846
    fmt.Printf("Nilai pi = %f\n", pi)
}
```

Output dari kode diatas:
```bash
Nilai pi = 3.14
```

3. Menampilkan nilai string:
```golang
func main() {
    var nama string = "John Doe"
    fmt.Printf("Nama saya %s\n", nama)
}
```

Output dari kode diatas:
```bash
Output: "Nama saya John Doe"
```

4. Menampilkan nilai boolean:
```golang
func main() {
    var benar bool = true
    fmt.Printf("Nilai benar = %t\n", benar)
}
```

Output kode diatas:
```bash
Output: "Nilai benar = true"
```

5. Menampilkan nilai karakter:
```golang
func main() {
    var huruf rune = 'A'
    fmt.Printf("Karakter huruf = %c\n", huruf)
}
```

Output kode diatas:
```bash
Output: "Karakter huruf = A"
```

Itulah beberapa contoh penggunaan format string di Golang. 

Dengan menggunakan format string, kita dapat memformat tampilan output program Golang sesuai dengan kebutuhan kita. 

### Apa selanjutnya?
Selanjutnya kita akan belajar mengenai time pada Golang

Happy learning! 😆