---
title: "Tutorial Kafka: Instalasi Kafka"
date: 2023-06-21T22:22:39+07:00
draft: false
author: "Adhika Guna"
thumbnail: /kafka/02-instalasi/thumbnail.png
description: "Belajar Instalasi Kafka"
---


### Instalasi Kafka

Ada banyak cara untuk instalasi kafka, melalui Docker, Cloud Provider, atau install langsung dari websitenya. Biasanya jika lewat Docker instalasi akan mudah karena semua sudah disediakan oleh Docker.

Tapi di artikel ini kita akan mencoba install kafka langsung melalui websitenya dan menjalankan kafka pada laptop / komputer kita.

### Langkah 1: Requirement

Requirement untuk menginstall kafka adalah memiliki Java Development Kit (JDK) versi 8 atau yang lebih baru, saya sarankan install yang dibawa versi 15.

### Langkah 2: Download Kafka

Untuk mendownload kafka kita bisa mengikuti step-step berikut:
1. Buka halaman download Kafka di situs resmi Apache Kafka (https://kafka.apache.org/downloads).
2. Pilih versi terbaru.
3. Unduh file tarball yang sesuai dengan sistem operasi Anda. Misalnya, jika Anda menggunakan Linux, pilih file tarball dengan ekstensi .tgz.
4. Setelah unduhan selesai, ekstrak file tarball ke direktori tujuan di sistem kita.


### Langkah 3: Konfigurasi Kafka

Setelah Kita mengunduh dan mengekstrak Kafka, kita perlu melakukan beberapa konfigurasi sebelum menjalankannya.

1. Buka folder Kafka yang baru saja diekstrak menggunakan code editor favorite, disini saya pakai VScode.
2. Masuk ke direktori konfigurasi Kafka
```bash
cd kafka_2.13-2.8.0/config
```
3. Edit file `server.properties` sesuai kebutuhan kita
4. Sebenernya di file `server.properties`  kita boleh menyesuaikan konfigurasi Kafka sesuai kebutuhan kita. Beberapa konfigurasi umum yang dapat kita sesuaikan termasuk:
   - `advertised.listeners`: Menentukan alamat dan port yang akan didengarkan oleh Kafka. Misalnya, localhost:9092.
   - `zookeeper.connect`: Menentukan lokasi ZooKeeper yang digunakan oleh Kafka. Misalnya, localhost:2181.

Konfigurasi lainnya seperti retention policies, ukuran partisi, dan banyak lagi.
5. Untuk tutorial ini mari kita edit:
   - `advertised.listeners` menjadi `localhost:9092`
```properties
advertised.listeners=localhost:9092
```
   - `zookeeper.connect` menjadi `localhost:2181`
```properties
zookeeper.connect=localhost:2182
```

### Langkah 4: Jalankan ZooKeeper

Kafka menggunakan ZooKeeper untuk manajemen koordinasi antara broker. Kita perlu menjalankan ZooKeeper sebelum menjalankan Kafka.

1. Buka terminal di root project Kafka.
2. Jalankan perintah ZooKeeper menggunakan script bawaan Kafka:
```bash
bin/zookeeper-server-start.sh config/zookeeper.properties
```
Berikut contohnya jika sudah berhasil menjalankan ZooKeeper:
![image info](/kafka/02-instalasi/pict1.jpeg)



### Langkah 5: Jalankan Kafka Broker
Setelah ZooKeeper berjalan, kita sekarang dapat menjalankan broker Kafka.

1. Buka terminal di root project Kafka.
2. Jalankan perintah Kafka menggunakan script bawaan Kafka:
```bash
bin/kafka-server-start.sh config/server.properties
```
Jika berhasil terminal akan terlihat seperti ini:
![image info](/kafka/02-instalasi/pict2.jpeg)

### Langkah 6: Verifikasi Instalasi
Untuk memastikan instalasi Kafka berjalan dengan baik, Kita dapat mencoba beberapa perintah sederhana, seperti mempublish pesan lalu mengconsumenya kembali.

1. Buka terminal di root project Kafka.
2. Buat topic dengan nama {{<code text="sekolahbackend.topic">}}
Berikut commandnya:
```bash
bin/kafka-topics.sh --create --topic sekolahbackend.topic --bootstrap-server localhost:9092 --partitions 1 --replication-factor 1
```
Jika berhasil terminal akan terlihat seperti ini:
![image info](/kafka/02-instalasi/pict3.jpeg)

3. Untuk mengirim pesan ke topik {{<code text="sekolahbackend.topic">}}, mari kita jalankan perintah berikut:
```bash
bin/kafka-console-producer.sh --topic sekolahbackend.topic --bootstrap-server localhost:9092
```
Jika berhasil terminal akan terlihat seperti ini:
![image info](/kafka/02-instalasi/pict4.jpeg)
Setelah menjalankan command diatas, terminal akan masuk ke mode prompt, dimana kita bisa memasukan text lalu menekan `Enter`. Setiap kita menekan `Enter` text yang kita tulis akan di publish ke topic {{<code text="sekolahbackend.topic">}}. 

4. Untuk membaca pesan dari topik {{<code text="sekolahbackend.topic">}}, mari kita jalankan perintah berikut:
```bash
bin/kafka-console-consumer.sh --topic sekolahbackend.topic --from-beginning --bootstrap-server localhost:9092
```

Berikut hasilnya jika berhasil:
![image info](/kafka/02-instalasi/pict5.jpeg)

Kita akan melihat pesan-pesan yang telah kita kirim sebelumnya.

Berikut jika disandingkan antara `producer` dan `consumer`, ketika kita mengpublish pesan melalui `producer`, pesannya akan langsung di terima oleh `consumer`:
![image info](/kafka/02-instalasi/pict6.jpeg)

Selamat!! kita sudah berhasil melihat pesan-pesan yang telah dikirim, berarti instalasi Kafka Anda berjalan dengan sukses.

### Apa selanjutnya?
Kita sudah mempelajari cara instalasi Kafka dan mencoba publish dan consume sebuah pesan. Selanjutnya kita akan belajar lebih dalam mengenai Topic dan Partition.

Happy learning! 😆
