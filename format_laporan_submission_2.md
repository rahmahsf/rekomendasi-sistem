# Laporan Proyek Machine Learning - Rahmah Sary Fadiyah

## Project Overview

Seiring dengan pesatnya pertumbuhan industri hiburan digital, terutama platform layanan streaming seperti Netflix, Disney+, dan Amazon Prime, pengguna dihadapkan pada pilihan ribuan film dan serial setiap harinya. Tantangan utama yang muncul adalah bagaimana menyajikan konten yang relevan dan sesuai dengan preferensi pengguna tanpa membuat mereka kewalahan dengan terlalu banyak pilihan. Oleh karena itu, sistem rekomendasi menjadi komponen penting dalam meningkatkan pengalaman pengguna dengan menyarankan konten yang kemungkinan besar akan disukai pengguna.

Masalah utama yang hendak diselesaikan adalah bagaimana mengidentifikasi film yang relevan bagi pengguna secara personal. Tanpa sistem rekomendasi yang efektif, pengguna bisa merasa frustasi dan kehilangan ketertarikan pada layanan yang ditawarkan. Sistem rekomendasi dapat mengatasi permasalahan ini dengan menganalisis preferensi pengguna, riwayat penelusuran, serta kesamaan antar konten atau antar pengguna lainnya [1].

## Business Understanding
### Problem Statements

Pernyataan masalah:
- Bagaimana cara membantu pengguna menemukan film yang sesuai dengan selera dan preferensi mereka di tengah banyaknya pilihan film yang tersedia?
- Bagaimana cara meningkatkan kepuasan dan keterlibatan pengguna melalui sistem rekomendasi yang lebih tepat sasaran?

### Goals

Menjelaskan tujuan proyek yang menjawab pernyataan masalah:
- Membangun sistem rekomendasi film yang mampu memahami dan memetakan preferensi pengguna secara akurat agar pengguna dapat menemukan film yang sesuai dengan selera mereka dengan cepat dan mudah di antara banyaknya pilihan film.
- Meningkatkan kepuasan dan keterlibatan pengguna pada platform dengan memberikan rekomendasi film yang lebih relevan dan personal, sehingga pengguna merasa lebih dihargai dan terdorong untuk terus menggunakan layanan.
Semua poin di atas harus diuraikan dengan jelas. Anda bebas menuliskan berapa pernyataan masalah dan juga goals yang diinginkan.


    ### Solution statements
    - Content-Based Filtering (CBF)
      Pendekatan ini memanfaatkan data atribut film seperti genre, keywords, overview, cast, dan director untuk membuat profil film dan profil preferensi pengguna. Sistem akan merekomendasikan film yang memiliki kemiripan konten dengan film-film yang pernah disukai atau ditonton oleh pengguna. Dengan demikian, pengguna dapat menemukan film yang sesuai selera secara cepat dan tepat.

    - Collaborative Filtering (CF)
      Metode ini menggunakan data interaksi pengguna (misalnya rating atau voting) untuk menemukan pola kesamaan preferensi antar pengguna. Rekomendasi diberikan berdasarkan film yang disukai oleh pengguna lain dengan preferensi serupa. Pendekatan ini meningkatkan relevansi rekomendasi dan memperkaya variasi film yang diberikan, sehingga dapat meningkatkan kepuasan dan keterlibatan pengguna.

    - Hybrid Recommendation System
      Kombinasi antara Content-Based Filtering dan Collaborative Filtering, yang bertujuan memanfaatkan keunggulan keduanya. Sistem hybrid dapat mengatasi keterbatasan masing-masing metode, seperti cold-start problem dan overspecialization, sehingga memberikan rekomendasi yang lebih personal, relevan, dan beragam bagi pengguna.

    - Incorporating Popularity and Trend Factors
      Menambahkan bobot popularitas (vote_count, popularity) dan tren rilis terbaru (release_date) dalam algoritma rekomendasi agar film yang direkomendasikan tidak hanya sesuai selera tetapi juga sedang digemari banyak pengguna, sehingga meningkatkan keterlibatan dan kepuasan pengguna.

## Data Understanding
Dataset yang digunakan dalam proyek ini berisi informasi tentang film-film yang tersedia pada sebuah platform streaming. Dataset terdiri dari **4.803 entri film** dengan berbagai atribut yang menggambarkan karakteristik film tersebut. Data ini mencakup informasi seperti genre, judul asli, bahasa, durasi, tanggal rilis, dan rating film. Dataset ini berasal dari [The Movie Database](https://www.kaggle.com/datasets/abdallahwagih/movies) dataset yang dapat diunduh secara gratis dari Kaggle.
Selanjutnya, uraikanlah seluruh variabel atau fitur pada data dengan jumlah **24 kolom** sebagai berikut: 
- index : Nomor indeks baris data.
- budget : Anggaran produksi film dalam satuan dolar.
- genres : Genre atau kategori film (misalnya Drama, Action).
- homepage : URL situs resmi film (jika tersedia).
- id : ID unik film.
- keywords : Kata kunci yang mendeskripsikan film.
- original_language : Bahasa asli film.
- original_title : Judul asli film.
- overview : Ringkasan cerita film.
- popularity : Skor popularitas film berdasarkan metrik internal platform.
- production_companies : Perusahaan produksi film.
- production_countries : Negara tempat film diproduksi.
- release_date : Tanggal rilis film.
- revenue : Pendapatan film dalam satuan dolar.
- runtime : Durasi film dalam menit.
- spoken_languages : Bahasa yang digunakan dalam film.
- status : Status rilis film (misalnya Released).
- tagline : Slogan film.
- title : Judul film.
- vote_average : Rata-rata rating film dari pengguna
- vote_count : Jumlah pengguna yang memberikan rating.
- cast : Daftar aktor utama dalam film.
- crew : Daftar kru produksi film.
- director : Sutradara film.

dengan tipe data seperti brikut: 

**Rubrik/Kriteria Tambahan (Opsional)**:
- Melakukan beberapa tahapan yang diperlukan untuk memahami data, contohnya teknik visualisasi data beserta insight atau exploratory data analysis.

## Data Preparation
Pada bagian ini Anda menerapkan dan menyebutkan teknik data preparation yang dilakukan. Teknik yang digunakan pada notebook dan laporan harus berurutan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan proses data preparation yang dilakukan
- Menjelaskan alasan mengapa diperlukan tahapan data preparation tersebut.

## Modeling
Tahapan ini membahas mengenai model sisten rekomendasi yang Anda buat untuk menyelesaikan permasalahan. Sajikan top-N recommendation sebagai output.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menyajikan dua solusi rekomendasi dengan algoritma yang berbeda.
- Menjelaskan kelebihan dan kekurangan dari solusi/pendekatan yang dipilih.

## Evaluation
Pada bagian ini Anda perlu menyebutkan metrik evaluasi yang digunakan. Kemudian, jelaskan hasil proyek berdasarkan metrik evaluasi tersebut.

Ingatlah, metrik evaluasi yang digunakan harus sesuai dengan konteks data, problem statement, dan solusi yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan formula metrik dan bagaimana metrik tersebut bekerja.

**---Ini adalah bagian akhir laporan---**

_Catatan:_
- _Anda dapat menambahkan gambar, kode, atau tabel ke dalam laporan jika diperlukan. Temukan caranya pada contoh dokumen markdown di situs editor [Dillinger](https://dillinger.io/), [Github Guides: Mastering markdown](https://guides.github.com/features/mastering-markdown/), atau sumber lain di internet. Semangat!_
- Jika terdapat penjelasan yang harus menyertakan code snippet, tuliskan dengan sewajarnya. Tidak perlu menuliskan keseluruhan kode project, cukup bagian yang ingin dijelaskan saja.
