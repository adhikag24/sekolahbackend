---
title: "Tutorial Kafka: Konsep dan Terminologi pada Kafka"
date: 2023-06-18T22:29:58+07:00
draft: false
author: "Adhika Guna"
thumbnail: /kafka/01-terminology/thumbnail.png
description: "Belajar mengenai konsep dan terminologi pada kafka"
---


### Terminologi pada Kafka

Kafka memiliki konsep dan terminologi khusus yang penting untuk dipahami agar dapat menggunakan tool ini secara efektif. 

Berikut beberapa key concept dan terminologi dalam Kafka beserta penjelasannya.


### Topic

Topic dalam Kafka adalah saluran yang digunakan untuk mengorganisir dan mengelompokkan aliran data. 

Setiap pesan yang dikirim ke Kafka dikategorikan ke dalam topik tertentu. Misalnya, jika kita memiliki topik dengan nama `sensor-data` semua pesan sensor akan dikirim ke topik tersebut.

Bisa kita bilang `Topic` ini adalah sebuah "table", tempat dimana kita mengirim data.


### Partition
Partisi digunakan untuk membagi topik menjadi beberapa bagian yang lebih kecil atau segmen. 

Setiap partisi adalah unit pemrosesan paralel dalam Kafka. Partisi memungkinkan distribusi beban kerja dan mempercepat pengolahan data. 

Setiap pesan dalam topik ditempatkan ke salah satu partisi berdasarkan algoritma yang ditentukan.


### Producers

Produser dalam Kafka adalah yang bertanggung jawab untuk mengirim pesan ke topik. 

Produser dapat mengirimkan pesan ke satu atau beberapa partisi dalam topik. 

Mereka juga dapat mengonfigurasi cara pengiriman pesan, seperti apakah pesan harus disimpan secara synchron atau asynchronous.


### Consumers

Consumers / Konsumen dalam Kafka adalah yang membaca dan memproses pesan dari topik. 

Mereka dapat mengambil pesan dari satu atau beberapa partisi dalam topik.

Consumer dapat mengonsumsi pesan dalam urutan yang terjamin (sequential) atau tanpa memperhatikan urutan pesan (non-sequential).

Consumer juga dapat melanjutkan konsumsi dari posisi tertentu dalam partisi.

### Consumer Groups

Consumer Groups / Grup konsumen adalah kelompok consumer yang bekerja bersama untuk membaca dan memproses pesan dari topik yang sama. 

Setiap pesan dalam topik hanya akan dikonsume oleh salah satu consumer dalam grup secara sekuensial. 

Grup consumer memungkinkan skalabilitas dan redundansi dalam pemrosesan pesan.

### Commit

Commit / Komit dalam Kafka merujuk pada tindakan consumer untuk mengonfirmasi bahwa pesan telah berhasil diproses dan dapat dianggap selesai. 

Setelah sebuah pesan dikonsumsi dan diproses, konsumen dapat melakukan komit untuk memperbarui posisi konsumsi mereka dalam partisi.

### Apa selanjutnya?
Kita sudah mempelajari terminologi pada Kafka. Selanjutnya kita akan belajar Install kafka pada device kita.

Happy learning! 😆
