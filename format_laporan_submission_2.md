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

dengan tipe data seperti berikut: 
| #  | Column                | Non-Null Count | Dtype   |
|-----|----------------------|----------------|---------|
| 0   | index                 | 4803 non-null  | int64   |
| 1   | budget                | 4803 non-null  | int64   |
| 2   | genres                | 4775 non-null  | object  |
| 3   | homepage              | 1712 non-null  | object  |
| 4   | id                    | 4803 non-null  | int64   |
| 5   | keywords              | 4391 non-null  | object  |
| 6   | original_language     | 4803 non-null  | object  |
| 7   | original_title        | 4803 non-null  | object  |
| 8   | overview              | 4800 non-null  | object  |
| 9   | popularity            | 4803 non-null  | float64 |
| 10  | production_companies  | 4803 non-null  | object  |
| 11  | production_countries  | 4803 non-null  | object  |
| 12  | release_date          | 4802 non-null  | object  |
| 13  | revenue               | 4803 non-null  | int64   |
| 14  | runtime               | 4801 non-null  | float64 |
| 15  | spoken_languages      | 4803 non-null  | object  |
| 16  | status                | 4803 non-null  | object  |
| 17  | tagline               | 3959 non-null  | object  |
| 18  | title                 | 4803 non-null  | object  |
| 19  | vote_average          | 4803 non-null  | float64 |
| 20  | vote_count            | 4803 non-null  | int64   |
| 21  | cast                  | 4760 non-null  | object  |
| 22  | crew                  | 4803 non-null  | object  |
| 23  | director              | 4773 non-null  | object  |

| Statistik | index  |     budget     |      id       |  popularity  |    revenue    |  runtime  | vote_average | vote_count |
|-----------|--------|---------------|--------------|--------------|---------------|-----------|--------------|------------|
| count     | 4803   | 4,803         | 4803         | 4803         | 4,803         | 4801      | 4803         | 4803       |
| mean      | 2401.0 | 29,045,040.43 | 57,165.48    | 21.49        | 82,260,640.64 | 106.88    | 6.09         | 690.22     |
| std       | 1386.65| 40,722,390.33 | 88,694.61    | 31.82        | 162,857,100.87| 22.61     | 1.19         | 1234.59    |
| min       | 0      | 0             | 5            | 0            | 0             | 0         | 0            | 0          |
| 25%       | 1200.5 | 790,000       | 9,014.5      | 4.67         | 0             | 94.0      | 5.6          | 54         |
| 50%       | 2401.0 | 15,000,000    | 14,629       | 12.92        | 19,170,000    | 103.0     | 6.2          | 235        |
| 75%       | 3601.5 | 40,000,000    | 58,610.5     | 28.31        | 92,917,190    | 118.0     | 6.8          | 737        |
| max       | 4802   | 380,000,000   | 459,488      | 875.58       | 2,787,965,000 | 338.0     | 10           | 13,752     |
Penjelasan:
- Data menunjukkan variasi besar dalam anggaran, popularitas, dan pendapatan film, mencerminkan perbedaan antara film low-budget hingga blockbuster.
- Sebagian data seperti anggaran dan revenue mengandung nilai 0, mungkin perlu diproses lebih lanjut untuk mengatasi data hilang.
- Durasi film rata-rata sekitar 1,5 jam, cukup standar untuk film bioskop.
- Rating dan jumlah voting bervariasi, memungkinkan analisis lebih lanjut untuk mencari film dengan kualitas dan popularitas tinggi.

**Kondisi dari data**:
- missing value

  | Kolom                | Jumlah Missing Value |
  |----------------------|---------------------:|
  | index                | 0                    |
  | budget               | 0                    |
  | genres               | 28                   |
  | homepage             | 3091                 |
  | id                   | 0                    |
  | keywords             | 412                  |
  | original_language    | 0                    |
  | original_title       | 0                    |
  | overview             | 3                    |
  | popularity           | 0                    |
  | production_companies | 0                    |
  | production_countries | 0                    |
  | release_date         | 1                    |
  | revenue              | 0                    |
  | runtime              | 2                    |
  | spoken_languages     | 0                    |
  | status               | 0                    |
  | tagline              | 844                  |
  | title                | 0                    |
  | vote_average         | 0                    |
  | vote_count           | 0                    |
  | cast                 | 43                   |
  | crew                 | 0                    |
  | director             | 30                   |

Penjelasaanya:
    - Kolom homepage memiliki jumlah missing value paling banyak yaitu 3091, ini karena tidak semua film memiliki halaman resmi.
    - Beberapa kolom seperti genres, keywords, tagline, cast, dan director juga memiliki missing value yang cukup signifikan, perlu dipertimbangkan saat analisis.
    - Kolom penting seperti budget, revenue, vote_average, dan title tidak memiliki missing value, sehingga data utama terkait performa film relatif lengkap.
    - Data missing di kolom seperti runtime 2 dan release_date 1 sangat sedikit, tagline memiliki 844, cast 43, direktur 30,genres 28, dan keyword 412
    
- Duplikat data
 Data yang digunakan dalam dataset ini telah melalui proses pengecekan untuk memastikan keunikan setiap entri. Hasil pemeriksaan menunjukkan bahwa tidak terdapat duplikat data pada seluruh baris dataset, yang berarti setiap rekaman film adalah unik dan tidak berulang.

![Alt Text](Resource/korelasi.PNG)

| Fitur 1        | Fitur 2      | Korelasi | Interpretasi                                                                               |
| -------------- | ------------ | -------- | ------------------------------------------------------------------------------------------ |
| `popularity`   | `vote_count` | 0.78     | Sangat kuat positif — Film yang populer cenderung mendapat banyak vote.                    |
| `budget`       | `vote_count` | 0.59     | Cukup kuat positif — Film dengan anggaran besar cenderung mendapat lebih banyak suara.     |
| `budget`       | `popularity` | 0.51     | Sedang positif — Film dengan budget besar cenderung populer.                               |
| `vote_average` | `runtime`    | 0.38     | Lemah hingga sedang — Film yang lebih lama cenderung mendapat rating sedikit lebih tinggi. |
| `vote_average` | `budget`     | 0.09     | Sangat lemah — Budget tidak berpengaruh signifikan ke rating.                              |


## Data Preparation

- **Menghapus atribut yang tidak digunakan**
  Field `id`, `index`, dan `homepage` kemungkinan besar **dihapus atau tidak digunakan dalam proyek sistem rekomendasi film berbasis machine learning** karena alasan berikut:
   - **`id` dan `index`** Biasanya hanya digunakan untuk identifikasi internal dalam dataset (misalnya sebagai primary key). Tidak mengandung informasi bermakna untuk pemodelan atau analisis.
   - **`homepage`** Merupakan link ke situs resmi film (misalnya situs promosi). Tidak memberikan nilai prediktif untuk sistem rekomendasi. Sering kali data ini kosong atau tidak konsisten, sehingga tidak layak diproses lebih lanjut.

- **Menghapus missing value**
  Menghapus missing value penting dilakukan untuk menjaga kualitas data dan mencegah error saat proses analisis atau pelatihan model machine learning. dan setelah dihapus datanya terdapat **3757 baris** dan **21 kolom**

## Modeling

1. **Content-Based Filtering (CBF)**
   Content-Based Filtering merupakan pendekatan sistem rekomendasi yang merekomendasikan item (dalam hal ini film) kepada pengguna berdasarkan kemiripan konten (genre, deskripsi, dan informasi metadata lainnya) dengan film yang pernah disukai atau ditonton oleh pengguna tersebut. Berikut adalah penjelasan **per bagian kode** dari implementasi sistem **Content-Based Filtering (CBF)** menggunakan **TF-IDF** dan **cosine similarity**:
   - **Membangun TF-IDF Matrix**

        ```python
        tfidf = TfidfVectorizer(stop_words='english')
        tfidf_matrix = tfidf.fit_transform(df['genres'])
        ```
    * `TfidfVectorizer(stop_words='english')`:
      * Digunakan untuk mengubah data teks (dalam hal ini kolom `genres`) menjadi representasi numerik berbasis **TF-IDF (Term Frequency-Inverse Document Frequency)**.
       * `stop_words='english'` akan mengabaikan kata-kata umum dalam bahasa Inggris (seperti *the*, *and*, *is*, dll.) agar tidak memengaruhi hasil.
    * `tfidf.fit_transform(df['genres'])`:
      * Membangun vektor TF-IDF untuk setiap film berdasarkan nilai genre-nya.
      * Hasil akhirnya adalah **matriks berdimensi (jumlah film x jumlah kata unik di semua genre)**.
        
   - **Menghitung Cosine Similarity**

        ```python
        cosine_sim = linear_kernel(tfidf_matrix, tfidf_matrix)
        ```

    * `linear_kernel()` digunakan untuk menghitung **cosine similarity** antar semua pasangan film berdasarkan TF-IDF matrix.
    * Output-nya adalah matriks kesamaan (similarity matrix) berukuran `(n_film x n_film)` di mana setiap nilai `[i][j]` menunjukkan seberapa mirip film ke-i dan film ke-j berdasarkan genre.

    - **Fungsi Rekomendasi Content-Based**
        ```python
        def content_based_recommendations(title, df_movies, cosine_sim, top_n=5):
        ```

    * Fungsi ini menerima:

        * `title`: Judul film yang dijadikan referensi.
        * `df_movies`: DataFrame berisi data film.
        * `cosine_sim`: Matriks kesamaan antar film.
        * `top_n`: Jumlah film teratas yang akan direkomendasikan.

    - **Mengambil Indeks Film Referensi**
        ```python
        indices = pd.Series(df_movies.index, index=df_movies['title'])
        idx = indices[title]
        ```

        * Membuat `Series` yang memetakan judul film ke indeks-nya dalam DataFrame.
        * `idx` adalah indeks dari film yang menjadi input (judul yang ingin dicari rekomendasinya).

    - **Mengambil dan Mengurutkan Skor Similarity**

        ```python
        sim_scores = list(enumerate(cosine_sim[idx]))
        sim_scores = sorted(sim_scores, key=lambda x: x[1], reverse=True)
        sim_scores = sim_scores[1:top_n+1]
        ```
        * `enumerate(cosine_sim[idx])`: Mengambil semua nilai kesamaan film referensi dengan film lain.
        * `sorted(..., reverse=True)`: Mengurutkan berdasarkan skor similarity tertinggi.
        * `sim_scores[1:top_n+1]`: Mengambil `top_n` film teratas, dengan menghindari film itu sendiri (karena skor similarity-nya pasti 1 dengan dirinya sendiri).

    - **Mengambil Judul Film Hasil Rekomendasi**

        ```python
        movie_indices = [i[0] for i in sim_scores]
        return df_movies.iloc[movie_indices]['title'].tolist()
        ```

        * Mengambil indeks dari film yang paling mirip.
        * Mengambil judul-judul film berdasarkan indeks tersebut dan mengembalikannya dalam bentuk list.

    - **INFERENCE**
      Dengan memanfaatkan vektor TF-IDF dari genre dan menghitung cosine similarity antar film, fungsi ini menampilkan lima film teratas yang paling mirip dengan "Avatar" beserta skor kemiripannya. Pendekatan ini memungkinkan sistem merekomendasikan film lain yang memiliki genre atau elemen cerita serupa, meskipun belum pernah ditonton sebelumnya oleh pengguna, sehingga memberikan rekomendasi yang relevan secara tematik dan akan menampilkam top 5.

    Berikut adalah tabel hasil rekomendasinya:

    | No | Judul Film                 | Similarity |
    | -- | -------------------------- | ---------- |
    | 1  | Man of Steel               | 1.0000     |
    | 2  | X-Men: Days of Future Past | 1.0000     |
    | 3  | Jupiter Ascending          | 1.0000     |
    | 4  | The Wolverine              | 1.0000     |
    | 5  | Superman                   | 1.0000     |

    Hasil rekomendasi di atas menunjukkan bahwa kelima film yang direkomendasikan memiliki nilai *similarity* sebesar **1.0000** terhadap film *Avatar*, berdasarkan pendekatan **Content-Based Filtering (CBF)** dengan fitur `genres`. Artinya, kelima film tersebut memiliki genre yang sangat mirip atau bahkan identik dengan *Avatar*, seperti **Action**, **Adventure**, **Fantasy**, atau **Science Fiction**.

    Nilai *similarity* maksimum (1.0) menunjukkan bahwa vektor TF-IDF dari film-film ini berada pada arah yang sama dalam ruang vektor, menandakan kesamaan konten genre secara penuh. Ini juga bisa terjadi karena genre ditulis identik dalam bentuk string, sehingga hasil *TF-IDF* dan cosine similarity menjadi maksimal.

   - **Kelebihan & Kekurangan**
     
     | Kelebihan                           | Penjelasan                                                                                                |
| ----------------------------------- | --------------------------------------------------------------------------------------------------------- |
| Tidak butuh interaksi pengguna lain | CBF hanya bergantung pada informasi konten item yang tersedia. Cocok untuk sistem baru (cold-start user). |
| Personal dan transparan             | Rekomendasi dihasilkan berdasarkan preferensi pengguna yang jelas (misal, genre yang sering dipilih).     |
| Mudah diinterpretasi                | Mudah menjelaskan kenapa sistem merekomendasikan film tertentu.                                           |
 
    | Kekurangan                                  | Penjelasan                                                                     |
| ------------------------------------------- | ------------------------------------------------------------------------------ |
| Tidak bisa merekomendasikan genre baru      | Sistem tidak bisa keluar dari pola preferensi yang sama (over-specialization). |
| Butuh representasi konten yang bagus        | Jika genre/deskripsi tidak lengkap, performa sistem menurun.                   |
| Tidak mempertimbangkan rating pengguna lain | Kurang efektif menangkap tren umum dari komunitas pengguna.                    |


3. **Collaborative Filtering (CF)**
   Fungsi dan kode di atas merupakan implementasi sistem **Collaborative Filtering (CF)** menggunakan pendekatan **Matrix Factorization** dengan algoritma **Singular Value Decomposition (SVD)** dari library `Surprise`. Berikut penjelasan dari setiap bagian kode:
   - **Dataset Interaksi Pengguna**

    ```python    
        ratings_dict = {
    "user_id": [1, 1, 1, 2, 2, 3, 3],
    "movie_id": [10, 20, 30, 10, 30, 20, 40],
    "rating": [4, 5, 2, 5, 3, 4, 1]
    }
    ```
    Data ini berisi **penilaian (rating)** pengguna terhadap berbagai film. Misalnya, pengguna `user_id=1` memberi rating 4 untuk `movie_id=10`, rating 5 untuk `movie_id=20`, dan seterusnya.

    - **Training Model SVD**

        ```python
            algo = SVD()
            algo.fit(trainset)
        ```
    Model dilatih menggunakan **SVD**, yang memfaktorkan matriks pengguna-film menjadi representasi laten dari pengguna dan film. Ini memungkinkan prediksi rating untuk film yang belum dilihat oleh pengguna.

    - **Fungsi Rekomendasi**

        ```python
        def collaborative_recommendations(user_id, df_movies, algo, top_n=5):
        ```

        Fungsi ini akan merekomendasikan **Top-N film** untuk `user_id` tertentu dengan langkah:
        1. Mengambil semua `movie_id` dari dataframe film.
        2. Melakukan **prediksi rating** untuk setiap film menggunakan model SVD.
        3. Mengurutkan film berdasarkan prediksi tertinggi.
        4. Mengambil `top_n` film teratas dan mengembalikan judulnya.

    - **Contoh Inference (Jika user\_id=1):**
      Fungsi `collaborative_inference` digunakan untuk menghasilkan rekomendasi film bagi pengguna tertentu berdasarkan pendekatan **Collaborative Filtering** menggunakan algoritma SVD. Fungsi ini memprediksi rating yang mungkin diberikan oleh pengguna terhadap semua film yang tersedia, lalu mengurutkannya berdasarkan skor prediksi tertinggi. Dalam contoh penggunaan untuk `user_id=1`, sistem memberikan lima rekomendasi film dengan prediksi rating tertinggi, seperti terlihat dalam output yang mencantumkan judul film dan nilai prediksi ratingnya. Pendekatan ini memungkinkan sistem untuk merekomendasikan film yang kemungkinan besar disukai pengguna berdasarkan pola penilaian pengguna lain yang serupa, tanpa mempertimbangkan konten film seperti genre atau sinopsis.
      Berikut adalah hasil rekomendasi film untuk **User 1** menggunakan pendekatan **Collaborative Filtering** berbasis algoritma SVD. Sistem memperkirakan seberapa besar kemungkinan pengguna akan menyukai film-film tertentu berdasarkan preferensi pengguna lain dengan pola penilaian serupa. Semua film dalam daftar memiliki **prediksi rating yang sama sebesar 3.61**, yang menunjukkan bahwa menurut model, film-film ini memiliki tingkat ketertarikan yang setara bagi User 1. Ini bisa terjadi karena data interaksi pengguna masih terbatas, sehingga model belum cukup terkalibrasi untuk membedakan preferensi secara signifikan.

Berikut tabel hasil rekomendasinya:

| No. | Judul Film                               | Predicted Rating |
| --- | ---------------------------------------- | ---------------- |
| 1   | Avatar                                   | 3.61             |
| 2   | Pirates of the Caribbean: At World's End | 3.61             |
| 3   | Spectre                                  | 3.61             |
| 4   | The Dark Knight Rises                    | 3.61             |
| 5   | John Carter                              | 3.61             |

Pendekatan Collaborative Filtering seperti ini sangat berguna karena bisa menemukan keterkaitan film yang tidak terduga tanpa melihat kontennya, namun model sangat bergantung pada kualitas dan jumlah interaksi data pengguna.

**Kelebihan & Kekurangan**

| Kelebihan                                                                   | Kekurangan                                                     |
| --------------------------------------------------------------------------- | -------------------------------------------------------------- |
| Dapat menangkap preferensi laten pengguna                                   | Butuh cukup data interaksi pengguna                            |
| Tidak tergantung fitur film seperti genre                                   | Tidak bisa memberi rekomendasi pada pengguna baru (cold start) |
| Bisa merekomendasikan film yang sangat berbeda tapi disukai pengguna serupa | Tidak menjelaskan alasan rekomendasi (black-box)               |

---

## Evaluation
Pada bagian ini Anda perlu menyebutkan metrik evaluasi yang digunakan. Kemudian, jelaskan hasil proyek berdasarkan metrik evaluasi tersebut.

Ingatlah, metrik evaluasi yang digunakan harus sesuai dengan konteks data, problem statement, dan solusi yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan formula metrik dan bagaimana metrik tersebut bekerja.

**---Ini adalah bagian akhir laporan---**

_Catatan:_
- _Anda dapat menambahkan gambar, kode, atau tabel ke dalam laporan jika diperlukan. Temukan caranya pada contoh dokumen markdown di situs editor [Dillinger](https://dillinger.io/), [Github Guides: Mastering markdown](https://guides.github.com/features/mastering-markdown/), atau sumber lain di internet. Semangat!_
- Jika terdapat penjelasan yang harus menyertakan code snippet, tuliskan dengan sewajarnya. Tidak perlu menuliskan keseluruhan kode project, cukup bagian yang ingin dijelaskan saja.
