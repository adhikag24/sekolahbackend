---
title: "Tutorial Kafka: Partition dan Topic"
date: 2023-06-23T22:41:26+07:00
draft: false
author: "Adhika Guna"
thumbnail: /kafka/03-topic-partition/thumbnail.png
description: "Belajar mengenai Partition dan Topic pada Kafka"
---


Dalam Apache Kafka, terdapat dua konsep yang menjadi dasar dari sistem streaming ini, yaitu `partition` dan `topic`. 


Partisi dan topik memainkan peran penting dalam mengorganize dan menyimpan data stream secara real-time. 


### Partition dalam Kafka
Partition adalah unit dasar penyimpanan dan replikasi data dalam sebuah topic di Kafka. 

Setiap topik dalam Kafka terdiri dari satu atau lebih partition yang menyimpan urutan pesan. Setiap pesan yang dikirimkan ke topik akan di-assign secara otomatis ke salah satu partition.

Partition memungkinkan Kafka untuk mendistribusikan data di antara node-node dalam topic dengan cara yang efisien. 
 
Partition juga memungkinkan Kafka untuk melakukan pemrosesan paralel pada data yang masuk.

Berikut adalah ilustrasi Partition dalam kafka:
![image info](/kafka/03-topic-partition/pict1.png)

Ketika publisher mengirimkan pesan ke sebuah topic, pesan itu akan di assign ke salah 1 partition menggunakan algoritma yang disediakan kafka, atau kita bisa menentukan sendiri mau di assign ke partition ke berapa. 


### Topic dalam Kafka
Topic adalah kategori atau kanal yang digunakan untuk mengelompokkan aliran data yang memiliki karakteristik yang sama. 

Misalnya, jika kita memiliki aplikasi e-commerce, kita dapat memiliki topic seperti {{<code text="pesanan">}}, {{<code text="pengiriman">}}, atau {{<code text="pembayaran">}}. 

Setiap topic terdiri dari satu atau lebih partition, dan setiap partition menyimpan urutan pesan. 

Topic memungkinkan user untuk mengatur dan mengakses data yang relevan dengan cara yang terstruktur.



### Manfaat Partition dan Topic:
Partisi dan topic memberikan beberapa manfaat dalam penggunaan Kafka:

- `Skalabilitas`: Partisi memungkinkan distribusi data di antara node-node dalam kluster, memungkinkan Kafka untuk menangani beban tinggi dan meningkatkan kapasitas dan throughput.
- `Toleransi Kesalahan`: Dengan replikasi partisi, Kafka dapat mempertahankan salinan cadangan data untuk memastikan ketersediaan dan keandalan data. Jika salah satu node gagal, replika partisi lainnya masih dapat melayani data.
- `Pemrosesan Paralel`: Partisi memungkinkan pemrosesan pesan secara paralel. Dengan menggunakan konsumen yang berbeda untuk setiap partisi, Kafka dapat mengolah aliran data dengan cepat dan efisien.
- `Organisasi Data`: Topic memungkinkan pengelompokan data berdasarkan kategori atau konteks yang relevan. Hal ini mempermudah dalam mengakses dan memproses data yang spesifik.
- `Retensi Data`: Partisi dan topic juga memungkinkan kita untuk mengatur retensi data. Kita dapat mengkonfigurasi berapa lama data akan disimpan sebelum dihapus.



### Apa selanjutnya?
Kita sudah mempelajari partition dan topic pada Kafka. Selanjutnya kita akan belajar lebih dalam mengenai Cluster dan Broker pada Kafka.

Happy learning! 😆
