---
title: "Tutorial Golang: Goroutine"
date: 2023-04-10T19:52:42+07:00
draft: false
author: "Adhika Guna"
thumbnail: /024-goroutine/thumbnail.png
description: "Belajar Goroutine pada Golang"
---

### Goroutine

Goroutine adalah fitur dalam bahasa pemrograman Go yang dapat membuat sebuah tugas ringan (lightweight task) atau proses kecil yang berjalan secara independen di dalam aplikasi. 

Dalam bahasa lain, Goroutine dapat diartikan sebagai sebuah bentuk konkurensi (concurrency) / asynchronous di mana tugas-tugas kecil atau proses-proses kecil dapat dijalankan secara bersamaan tanpa mengganggu satu sama lain. 

Goroutine menggunakan thread sebagai sarana untuk menjalankan proses kecil tersebut. 

Tapi, perlu diketahui bahwa Goroutine tidak sama dengan thread pada umumnya. Hal ini disebabkan karena Goroutine lebih ringan dibandingkan dengan thread dan dapat dijalankan secara lebih efisien.

### Cara Menggunakan Goroutine

Untuk menggunakan Goroutine, kita perlu menggunakan perintah {{<singlelinecodeblock text="go">}} di depan sebuah fungsi. 

Sebagai contoh, mari kita lihat sebuah contoh program sederhana yang menggunakan Goroutine:
```golang
func printMessage(message string) {
    for i := 0; i < 5; i++ {
        fmt.Println(message)
        time.Sleep(time.Millisecond * 500)
    }
}

func main() {
    go printMessage("Hello")
    go printMessage("World")

    time.Sleep(time.Second * 3)
}
```

Hasil eksekusi kode diatas:
![image info](/024-goroutine/pict1.jpg)

Dalam contoh program di atas, kita menggunakan Goroutine untuk menjalankan fungsi {{<singlelinecodeblock text="printMessage">}} dua kali dengan pesan yang berbeda {{<singlelinecodeblock text="('Hello' dan 'World')">}}. 

Kedua Goroutine tersebut dijalankan secara bersamaan dan tidak saling mengganggu satu sama lain. Kita juga menggunakan perintah {{<singlelinecodeblock text="time.Sleep">}} untuk memberikan waktu yang cukup agar kedua Goroutine dapat berjalan dan menyelesaikan tugasnya.

Jika kita tidak menambahkan perintah sleep program tidak akan mengprint apapun, karna program sudah terlanjur selesai, sedangkan gorutine belum mulai bekerja.

Berikut hasil eksekusi kode diatas tanpa perintah `sleep`:
![image info](/024-goroutine/pict2.jpeg)



### Benefit dari Goroutine

Penggunaan Goroutine pada aplikasi Go memiliki beberapa manfaat, di antaranya:

- Efisien: Goroutine lebih ringan dibandingkan dengan thread sehingga dapat dijalankan secara lebih efisien.

- Mudah digunakan: Goroutine dapat digunakan dengan mudah tanpa memerlukan konfigurasi yang rumit.

- Kontrol konkurensi: Dalam aplikasi Go, Goroutine dapat digunakan untuk mengimplementasikan kontrol konkurensi yang baik.

- Mempercepat aplikasi: Penggunaan Goroutine pada aplikasi Go dapat mempercepat waktu eksekusi aplikasi karena proses-proses kecil dapat dijalankan secara bersamaan.

### Apa selanjutnya?
Selanjutnya kita akan belajar mengenai Channel pada golang

Happy learning! 😆