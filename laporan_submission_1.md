# Laporan Proyek Model Machine Learning untuk Memprediksi Harga Runah  - Muhammad Imam Ariq Sya'bana

## Domain Proyek

Bubble economy di Jepang merupakan periode pertumbuhan ekonomi yang sangat cepat dan spektakuler, di mana harga aset seperti tanah dan properti mengalami kenaikan yang tajam sebelum akhirnya mengalami kejatuhan yang dramatis. Oleh karena itu, penting bagi para pembeli rumah dan para pemangku kepentingan di pasar perumahan untuk dapat memahami dan mengantisipasi kemungkinan terjadinya lonjakan harga yang signifikan.

Projek ini bertujuan untuk membangun model machine learning yang dapat memprediksi harga rumah di masa depan dan mengidentifikasi kemungkinan adanya lonjakan harga rumah yang tinggi seperti yang terjadi pada bubble economy di Jepang pada tahun 1980-an.

Bubble economy adalah kenaikan harga asset yang dampaknya cukup luas untuk suatu perekonomian negara. Karena kasus di Jepang 1984 properti adalah aset yang banyak dimiliki banyak orang maka jika harga nya naik drastis dan selanjutnya turun drastis dapat memengaruhi ekonomi sosial negara. Buble economy yang membuat harga aset meningkat bukan didasarkan pada nilai intrinsiknya, melainkan pada spekulasi masyarakat yang ingin berinvestasi. 

Saat gelembung tumbuh harga-harga aset sudah pasti naik drastis sehingga lebih banyak investor tertarik ke pasar, yang menyebabkan kenaikan harga lebih lanjut dan menyebabkan keuntungan bagi investor. Tetapi untuk masyarakat yang benar-benar membutuhkan rumah untuk kebutuhan bukan untuk investasi akan merasa sangat keberatan karena harga-harga rumah sudah sangat tinggi. Maka dari itu akan terjadi penurunan anjlok harga aset untuk membuat harga rumah normal kembali yang disebabkan oleh peraturan pemerintah, sehingga menghasilkan kerugian pada sisi investor karena harga jual yang turun sangat jauh dibawah saat mereka membeli harga aset tersebut saat sebelum anjlok, ditambah banyak investor yang berinvestasi dengan menggunakan dana pinjaman dari bank dan karena harga aset yang dibeli turun drastis maka mereka tidak dapat melunasi pinjamannya menyebabkan banyak bank yang mengalami kebangkrutan sehingga menyebabkakn penurunan pertumbuhan ekonomi yang signifikan.

[Land-use conversion and residential recentralization: Evidence from Japan's real estate bubble in the 1980s](https://mpra.ub.uni-muenchen.de/id/eprint/105961) 

[Where and when was the 1980s bubble emerged in Japan? Evidence from prefecture-level land price data](https://feb.ugm.ac.id/id/profil/staf-pengajar/2576-traheka-erdyas-bimanatya) 



## Business Understanding

### Problem Statements

Menjelaskan pernyataan masalah latar belakang:
- Bagaimana membangun model machine learning yang dapat memprediksi harga rumah pada validation set setelah model data dilatih dengan training set yang dibagi dari dataset asal?
- Model machine learning mana yang memiliki performa terbaik dalam memprediksi harga rumah?
- Bagaimana cara memprediksi harga rumah untuk data yang ada dimasa depan atau data yang lebih baru dan belum tercatat di dataset asal?

### Goals

Menjelaskan tujuan dari pernyataan masalah:
- Untuk memprediksi harga rumah di masa depan akan dibuat model machine learning dengan menggunakan dua dari beberapa metode yang ada yaitu Convolution Neural Network dan Recurrent Neural Network.
- Setelah kedua model machine learning dibuat, untuk mengetahui model yang bekerja lebih baik akan diuji dengan menggunakan metode evaluasi model MSE dan MAE. Model yang prediksinya paling mendekati harga rumah sebenarnya akan digunakan untuk memprediksi harga rumah dimasa depan yang tidak tercatat di dataset.  
- Untuk memprediksi data baru yang diluar dari dataset awal, konsep yang akan digunakan adalah dengan memanfaatkan data histori harga rumah dimasa lalu dalam kurun waktu tertentu untuk memprediksi harga rumah di minggu-minggu berikutnya. Selanjutnya hasil prediksi masa depan yang didapat di iterasi sebelumnya akan dimasukkan ke dalam pola data histori untuk menebak harga rumah pada minggu-minggu berikutnya.

## Data Understanding
Dataset yang Saya gunakan pada projek ini berisi informasi historis tentang harga rumah, termasuk fitur-fitur seperti kode pos, jumlah kamar tidur, harga, tahun dijual dan tipe properti. Data ini akan digunakan untuk melatih model machine learning untuk memprediksi harga rumah di masa depan dan menganalisis perubahan tren harga untuk mengidentifikasi potensi lonjakan harga.

House Property Sales Time Series (https://www.kaggle.com/datasets/htagholdings/property-sales?select=raw_sales.csv).

### Variabel-variabel pada Restaurant UCI dataset adalah sebagai berikut:
- datesold : merupakan tipe data datetime yang menunjukkan kapan data rumah tersebut dijual.
- postcode : berupa empat digit kode pos dari distrik tempat properti tersebut dijual.
- price : Harga jual properti yang telah berhasil terjual.
- propertyType : Tipe properti i.e. house atau unit
- bedrooms : Jumlah kamar tidur

**Rubrik/Kriteria Tambahan (Opsional)**:
- Melakukan beberapa tahapan yang diperlukan untuk memahami data, contohnya teknik visualisasi data atau exploratory data analysis.

Untuk memahami atribut-atribut yang ada di dalam dataset tersebut dilakukan beberapa langkah untuk memahami isi dan tipe atribut tersebut. Pertama, dengan menggunakan built-in function .info() kita bisa mendapatkan bahwa dalam dataset tersebut tidak terdapat data yang kosong dan bosa mengetahui tipe data dari masing-masing atribut yang ada pada dataset. Kedua, dengan menggunakan .describe() kita dapat mengetahui statistik dasar dari data seperti percentile, mean, standar deviasi, jumlah data, min, dan max.

Untuk atirbut propertyType dilakukan visualisasi jumlah data rumah yang bertipe house dan unit. Didapatkan bahwa jumlah data yang bertipe house dan unit tidak seimbang, maka dari itu pada tahap selanjutnya atribut property type tidak dimasukkan untuk perhitungan karena dianggap tidak akan relevan karena distribusi data yang tidak seimbang.
![image](https://github.com/Zelkova46/ML-terapan/assets/70127988/def5a074-4318-4f81-a35b-503cb777854c)



## Data Preparation
Pada bagian ini Anda menerapkan dan menyebutkan teknik data preparation yang dilakukan. Teknik yang digunakan pada notebook dan laporan harus berurutan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan proses data preparation yang dilakukan
- Menjelaskan alasan mengapa diperlukan tahapan data preparation tersebut.

## Modeling
Tahapan ini membahas mengenai model machine learning yang digunakan untuk menyelesaikan permasalahan. Anda perlu menjelaskan tahapan dan parameter yang digunakan pada proses pemodelan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan kelebihan dan kekurangan dari setiap algoritma yang digunakan.
- Jika menggunakan satu algoritma pada solution statement, lakukan proses improvement terhadap model dengan hyperparameter tuning. **Jelaskan proses improvement yang dilakukan**.
- Jika menggunakan dua atau lebih algoritma pada solution statement, maka pilih model terbaik sebagai solusi. **Jelaskan mengapa memilih model tersebut sebagai model terbaik**.

## Evaluation
Pada bagian ini anda perlu menyebutkan metrik evaluasi yang digunakan. Lalu anda perlu menjelaskan hasil proyek berdasarkan metrik evaluasi yang digunakan.

Sebagai contoh, Anda memiih kasus klasifikasi dan menggunakan metrik **akurasi, precision, recall, dan F1 score**. Jelaskan mengenai beberapa hal berikut:
- Penjelasan mengenai metrik yang digunakan
- Menjelaskan hasil proyek berdasarkan metrik evaluasi

Ingatlah, metrik evaluasi yang digunakan harus sesuai dengan konteks data, problem statement, dan solusi yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan formula metrik dan bagaimana metrik tersebut bekerja.

**---Ini adalah bagian akhir laporan---**

_Catatan:_
- _Anda dapat menambahkan gambar, kode, atau tabel ke dalam laporan jika diperlukan. Temukan caranya pada contoh dokumen markdown di situs editor [Dillinger](https://dillinger.io/), [Github Guides: Mastering markdown](https://guides.github.com/features/mastering-markdown/), atau sumber lain di internet. Semangat!_
- Jika terdapat penjelasan yang harus menyertakan code snippet, tuliskan dengan sewajarnya. Tidak perlu menuliskan keseluruhan kode project, cukup bagian yang ingin dijelaskan saja.
