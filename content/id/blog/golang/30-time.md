---
title: "Tutorial Golang: Package Time"
date: 2023-04-19T22:36:31+07:00
draft: false
author: "Adhika Guna"
thumbnail: /030-time/thumbnail.png
description: "Belajar Package Time pada Golang"
---



### Time

Golang memiliki built-in package bernama `time` yang berguna untuk memanipulasi waktu dan tanggal. 

Paket ini memiliki berbagai macam fungsi dan metode untuk mengambil waktu saat ini, mengonversi waktu antara zona waktu yang berbeda, menghitung durasi, dan banyak lagi.

### time.Now()

Package `time` memiliki banyak method terkait waktu dan tanggal, kita mulai dengan {{<singlelinecodeblock text="time.Now()">}}, dengan {{<singlelinecodeblock text="time.Now()">}} kita dapat mengambil waktu saat ini.

Berikut contoh kodenya:

```golang
func main() {
    now := time.Now()
    fmt.Println("Waktu saat ini:", now)
}
```
Output dari method {{<singlelinecodeblock text="time.Now()">}} menunjukkan waktu saat ini dalam format {{<singlelinecodeblock text="YYYY-MM-DD HH:mm:ss.ffffff +0000 UTC">}} 

Berikut adalah hasi eksekusi kode diatas:
![image info](/030-time/pict1.jpeg)


Dengan package `time` kita juga dapat memformat waktu, dengan menggunakan konstant format waktu yang telah disediakan oleh package time, dan kita juga membuat custom format waktu sendiri.

Berikut adalah beberapa contoh kode untuk memformat waktu dalam beberapa format umum:
```golang
func main() {
    now := time.Now()

    fmt.Println("Format waktu default:", now)
    fmt.Println("Format waktu RFC3339:", now.Format(time.RFC3339))
    fmt.Println("Format waktu custom:", now.Format("2006-01-02 15:04:05"))
}
```
Output dari program ini akan menunjukkan waktu saat ini dalam tiga format yang berbeda, yaitu format default, format RFC3339, dan format custom.

Berikut adalah hasil eksekusi kode diatas:
![image info](/030-time/pict2.jpeg)

### time.Sleep()

Package `time` juga menyediakan method {{<singlelinecodeblock text="time.Sleep()">}} untuk memberikan jeda antara eksekusi program. 

Berikut adalah contoh kode untuk memberikan jeda selama 2 detik:
```golang
func main() {
    fmt.Println("Sebelum jeda")
    time.Sleep(2 * time.Second)
    fmt.Println("Setelah jeda")
}
```

Output dari program diatas akan menunjukkan pesan `Sebelum jeda` diikuti dengan jeda selama 2 detik, dan kemudian pesan `Setelah jeda `akan muncul.



### Format waktu yang umum yang digunakan di Golang

Package `time` menyediakan beberapa konstanta format waktu yang telah ditentukan sebelumnya untuk memudahkan pengguna dalam memformat waktu dan tanggal. 

Berikut adalah beberapa format waktu yang umum digunakan di Golang:

```golang
time.ANSIC : "Mon Jan _2 15:04:05 2006"
time.UnixDate : "Mon Jan _2 15:04:05 MST 2006"
time.RubyDate : "Mon Jan 02 15:04:05 -0700 2006"
time.RFC822 : "02 Jan 06 15:04 MST"
time.RFC822Z : "02 Jan 06 15:04 -0700" // RFC822 with numeric zone
time.RFC850 : "Monday, 02-Jan-06 15:04:05 MST"
time.RFC1123 : "Mon, 02 Jan 2006 15:04:05 MST"
time.RFC1123Z : "Mon, 02 Jan 2006 15:04:05 -0700" // RFC1123 with numeric zone
time.RFC3339 : "2006-01-02T15:04:05Z07:00"
time.RFC3339Nano : "2006-01-02T15:04:05.999999999Z07:00"
time.Kitchen : "3:04PM"
time.Stamp : "Jan _2 15:04:05"
time.StampMilli : "Jan _2 15:04:05.000"
time.StampMicro : "Jan _2 15:04:05.000000"
time.StampNano : "Jan _2 15:04:05.000000000"
```

Setiap format waktu memiliki pola yang berbeda. 

Misalnya, format waktu {{<singlelinecodeblock text="time.RFC3339">}} menunjukkan waktu dalam format {{<singlelinecodeblock text="2006-01-02T15:04:05Z07:00">}}, sementara format waktu {{<singlelinecodeblock text="time.Kitchen">}} menunjukkan waktu dalam format {{<singlelinecodeblock text="3:04PM">}}.

Kita juga dapat membuat custom format waktu khusus sendiri menggunakan string yang menggambarkan pola waktu. 

Berikut adalah contoh kode untuk membuat format waktu khusus:

```golang
func main() {
    customFormat := "Jan 02, 2006 at 03:04 PM"
    t := time.Now()

    fmt.Println("Waktu saat ini:", t.Format(customFormat))
}
```

Berikut hasil eksekusi kode diatas:
![image info](/030-time/pict3.jpeg)


### Convert string to time

Dalam pengerjaan aplikasi, sering kali kita memerlukan cara untuk mengkonversi dari `string` ke `time`, agar kita dapat menggunakan method yang disediakan package `time`.

Berikut adalah contoh kode Golang untuk mengonversi string menjadi tipe data {{<singlelinecodeblock text="time.Time">}}:

```golang
func main() {
    // string yang akan dikonversi
    str := "2022-04-19 13:30:00"

    // format string untuk memparsing string menjadi tipe data time.Time
    layout := "2006-01-02 15:04:05"

    // konversi string menjadi time.Time
    t, err := time.Parse(layout, str)

    if err != nil {
        fmt.Println("Error:", err)
        return
    }

    fmt.Println("Waktu yang dikonversi:", t)
	fmt.Println("Check data type:", reflect.TypeOf(t))
}
```

Hasil eksekusi kode diatas:
![image info](/030-time/pict4.jpeg)

Pada contoh kode di atas, kita membuat variable `string str` yang akan diubah menjadi tipe data `time.Time`. 

Kemudian kita mendefinisikan custom format waktu yang akan digunakan untuk memparse `string str` menjadi tipe data `time.Time`. 

Selanjutnya, kita menggunakan fungsi {{<singlelinecodeblock text="time.Parse()">}} untuk melakukan konversi dari `string` menjadi tipe data `time.Time`. 

Jika konversi berhasil, maka kita akan mendapatkan variabel `t` dengan tipe data `time.Time`. 

Jika gagal, maka variabel `err` akan berisi `error` yang terjadi selama konversi.


### Convert time to string

Sekarang kita belajar bagaimana convert `time.Time` ke `string`.

Berikut adalah contoh kode untuk mengonversi tipe data `time.Time` menjadi `string`:
```golang
func main() {
    // waktu yang akan dikonversi
    t := time.Now()

    // format string untuk mengubah waktu menjadi string
    layout := "2006-01-02 15:04:05"

    // konversi time.Time menjadi string
    str := t.Format(layout)

    fmt.Println("Waktu dalam bentuk string:", str)
    fmt.Println("Check data type:", reflect.TypeOf(str))
}
```
Berikut hasil eksekusi kode diatas:

![image info](/030-time/pict5.jpeg)

Pada contoh kode di atas, kita membuat sebuah variabel `t` yang berisi waktu saat ini, dan akan diubah menjadi `string`. 

Kemudian kita mendefinisikan custom format waktu yang akan digunakan untuk mengubah `time.Time` menjadi `string`.

Selanjutnya, kita menggunakan fungsi {{<singlelinecodeblock text="time.Format()">}} untuk mengonversi tipe data `time.Time` menjadi `string`. 

Fungsi ini memerlukan parameter berupa format string layout yang telah didefinisikan sebelumnya.

Terakhir, kita mengprint hasil konversi dalam variabel `str` yang merupakan string yang berisi waktu sesuai dengan format layout.

### Apa selanjutnya?
Selanjutnya kita akan belajar bagaimana handle JSON pada Golang

Happy learning! 😆
