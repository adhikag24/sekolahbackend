---
title: "Tutorial Kafka: Cluster dan Broker"
date: 2023-06-26T20:24:17+07:00
draft: false
author: "Adhika Guna"
slug: "cluster-broker"
thumbnail: /kafka/04-broker-cluster/thumbnail.png
description: "Belajar mengenai Cluster dan Broker pada Kafka"
---

### Cluster pada Kafka

Cluster Kafka adalah sekelompok server (broker) yang bekerja sama untuk membuat sistem terdistribusi untuk menangani dan mengelola streaming data. Ini bertindak sebagai infrastruktur yang kuat (high availability) dan ketahanan (fault tolerance), berfungsi untuk memproses dan menyimpan data secara real-time. 

Sebuah cluster terdiri dari satu atau lebih broker yang berkolaborasi untuk melakukan tugasnya.

### Broker pada Kafka
Broker adalah instance atau server tunggal dalam sebuah cluster Kafka. 

Broker bertanggung jawab untuk menerima, menyimpan, dan melayani streaming data. Broker menangani publish dan consume pesan, serta penyimpanan dan replikasi data di seluruh cluster. 

Setiap broker dalam cluster memiliki pengidentifikasi unik dan dapat mengenali broker lain dalam sebuah cluster.

### Architecture Kafka
Broker adalah blok bangunan dari sebuah cluster pada Kafka. Mereka bekerja sama dalam cluster untuk memastikan ketahanan, skalabilitas, dan replikasi data. 

Dengan menggunakan arsitektur cluster memungkinkan distribusi data di beberapa broker, dan juga memungkinkan broker untuk melakukan load balancing dan pemrosesan data yang efisien.

Setiap broker didalam cluster dapat mengenali broker lain dan saling berkomunikasi untuk bertukar data, mereplikasi data, dan mengelola distribusi partisi dan topik.

Client, seperti producer dan consumer, dapat terhubung ke broker mana pun dalam cluster untuk mempublikasikan atau mengkonsumsi data. Tugas broker didalam cluster berkoordinasi untuk menangani load balancing dan replikasi data.

Berikut adalah gambaran architecture kafka:
![image info](/kafka/04-broker-cluster/pict1.png)



### Fungsi Kafka Cluster:

- High Availability: Cluster Kafka memberikan fitur ketahanan dan ketersediaan tinggi (High availability). Jika ada broker yang gagal / down, cluster dapat memastikan bahwa data yang tetap dapat diakses dengan mereplikasinya di beberapa broker.
- Scalability: Cluster Kafka memungkinkan scale secara horizontal yang mudah dengan menambahkan lebih banyak broker. Hal ini memungkinkan menghandle data dalam volume besar dan peningkatan beban kerja seiring pertumbuhan aplikasi.
- Data Replication: Cluster mempunyai feature replikasi data di seluruh broker, memastikan daya tahan dan keandalan. Setiap data yang masuk akan direplikasi, sehingga membuat data dapat selalu diakses dengan lancar jika terjadi kegagalan di sebuah broker.


### Fungsi Kafka Broker:

- Data Ingestion: Broker menerima data dari producer dan menyimpannya secara terus-menerus. Mereka bertanggung jawab untuk menerima pesan masuk dan membuat datanya tersedia untuk consumer.
- Message Storage: Broker menyimpan pesan pada disk, broker akan memastikan daya tahan dan keandalan. Bahkan jika broker down / mati, data yang disimpan tetap utuh dan dapat diakses ketika broker kembali online.
-Partition Handling: Setiap topik di Kafka dibagi menjadi beberapa partisi yang sudah kita bahas di artikel sebelumnya. Broker bertugas menangani dan menyimpan pesan dalam partisi ini, sehingga dapat mendistribusikan beban kerja di seluruh cluster.
- Data Replication: Broker dapat mereplikasi data di beberapa broker dalam cluster. Replikasi ini membuat data tetap dapat diakses walaupun salah satu broker down.


### Apa selanjutnya?
Kita sudah mempelajari broker dan cluster pada Kafka. Selanjutnya kita akan belajar lebih dalam mengenai Consumer pada Kafka.

Happy learning! 😆
