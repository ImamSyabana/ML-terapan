# Laporan Proyek Sistem Pencarian Rekomendasi Jurnal Pemrosesan Bahasa Alami berdasarkan Nilai *Cosine Simmilarity* - Muhammad Imam Ariq Sya'bana

## Domain Proyek

Definisi *Information Retrieval* atau temu kembali informasi menurut Gerard Salton (1968) dalam Arguilo (2013) adalah : *Information retrieval is a field concerned with the structure, analysis, organization, storage, searching, and retrieval of information.* (Arguello, Jaime, 2013). Berdasarkan pengertian tersebut *Information Retrieval* dapat diterapkan kepada bidang-bidang kehidupan manusia yang selalu melibatkan informasi, lebih spesifiknya adalah dalam kegiatan pengumpulan informasi. 

Di zaman yang sudah modern dimana teknologi sudah canggih seperti sekarang ini, kegiatan mengumpulkan informasi sudah lebih mudah. Sebelumnya, jika ingin mencari jurnal ilmiah para pelajar harus pergi ke perpustakaan untuk mendapatkan informasi yang mereka butuhkan. Sekarang, dimana penyebaran internet sudah masif dan sistem temu kembali informasi yang sudah canggih para pelajar dapat dengan mudah untuk mengumpulkan informasi lewat gawai asalkan terkoneksi ke jaringan internet. Penulis ingin memberikan contoh Google Scholar untuk perihal pengumpulan informasi pada masa kini. Google Scholar adalah layanan yang memungkinkan pengguna untuk melakukan pencarian materi-materi pelajaran berupa teks dalam berbagai format publikasi. Google Scholar menyediakan cara yang mudah untuk mencari literatur akademis secara luas. Saat pengguna memasukkan judul atau topik literatur yang ingin dicari pada *search bar*, Google Scholar akan menampilkan jurnal-jurnal yang memiliki relevansi dengan kata kunci atau kalimat yang diinputkan oleh pengguna.

![image](https://github.com/Zelkova46/ML-terapan/assets/70127988/fc45f3f4-c48c-4495-8e41-665f449a46d2)
Gambar 1. Hasil pencarian jurnal ilmiah dengan menggunakan Google Scholar 

Mesin pencari jurnal seperti Google Scholar sudah termasuk ke dalam sistem temu kembali informasi yang modern. Google Scholar akan otomatis mencari dokumen yang tersebar di internet, lalu berdasarkan relevansi yang dihitung oleh model yang dibuat Google dokumen tersebut akan masuk ke daftar hasil pencarian dokumen Google Scholar. Hasil dokumen yang ditampilkan ke pengguna untuk rekomendasi dokumen yang dianggap sesuai dengan keinginan pengguna sudah diprogram dengan menggunakan model *machine learning* sehingga dokumen yang paling relevan pada kueri akan ditampilkan dari yang paling relevan hingga ke yang paling tidak relevan. Pada bagian dimana Google Scholar menampilkan dokumen-dokumen yang relevan dengan kueri pengguna, hal tersebut merupakan pengimplementasian dari sistem rekomendasi. Rekomendasi Google Scholar dibuat berdasarkan kueri yang diinputkan pengguna, lalu dari kueri tersebut sistem dapat membuat rekomendasi dokumen-dokumen kepada pengguna berdasakran tinggat relevansinya terhadap kueri. Dalam kasus ini sistem rekomendasi yang diimplementasikan adalah berjenis *content based filtering*, karena hasil rekomendasi bergantung pada judul yang ada pada dokumen. Karena judul merupakan atribut atau salah satu konten dari dokumen tersebut, dapat dikatakan bahwa implementasi pada Google Scholar adalah sistem rekomendasi berbasis konten.  

Algoritma pencarian dokumen yang relevan milik Google yang diterapkan di dalam Google Scholar atau produk lain dari Google seperti Google *search engine* merupakan algoritma yang kompleks dan juga sudah paten milik Google yang dibangun dari kombinasi beberapa teknik, input, dan model pembelajaran mesin untuk menentukan relevansi dan kualitas dari dokumen untuk di rekomendasikan berdasarkan kueri yang diinputkan pengguna. Google tentu saja tidak secara publik membeberkan detail menyeluruh tentang bagaimana cara algoritma milik Google tersebut. Karena alasan tersebut penulis merasa projek untuk membuat sistem rekomendasi untuk pencarian jurnal ilmiah masih perlu dikerjakan. Projek sistem temu kembali informasi ini akan dibuat untuk berusaha menirukan algoritma sistem temu kembali informasi Google dengan memperhatikan *Relevance Factor* yang ditentukan dengan menggunakan algoritma *Cossine Simmilarity* untuk mengetahui nilai relevansi untuk masing-masing dokumen yang direkomendasikan.


## Business Understanding

Permasalahan yang diangkat pada projek kali ini dan mendasari untuk dikembangkannya projek ini adalah berasal dari pengalaman yang dialami oleh penulis saat ingin mencari dokumen jurnal ilmiah disitus perpustakaan digital milik universitas tempat penulis kuliah. Seperti yang telah dijelaskan sebelumnya pada bagian domain proyek, telah diketahui bahwa Google menerapkan algoritma yang kompleks, memadukan teknik-teknik *machine learning* yang membuat hasil rekomendasi dokumen relevan yang ditunjukkan pada pengguna sesuai dengan apa yang pengguna inginkan dan yang paling penting tidak ada dokumen relevan yang tidak terpilih untuk direkomendasikan ke pengguna. Algoritma kompleks yang diterapkan Google dalam *information retrieval* merupakan implementasi dari penerapan ide *flexible search*, yaitu kemampuan sistem pencari dokumen dalam memahami berbagai tipe queri, maksud pengguna, dan informasi yang dibutuhkan. *Flexible search* tetap dapat memberikan hasil dokumen yang relevan walaupun queri yang diinputkan pengguna tidak tepat, tidak jelas, terdapat salah pengejaan, dan yang paling penting masih dapat memberikan rekomendasi yang relevant walaupun queri tidak seratus persen sama dengan dokumen yang ada di database. Contoh penerapan *flexible search* pada Google Schoolar tertera pada Gambar 2.

![image](https://github.com/Zelkova46/ML-terapan/assets/70127988/e6667537-0c30-44c1-8397-2539b506b439)
Gambar 2. Hasil pencarian Google Scholar yang masih dapat memberi hasil dokumen relevan saat queri yang diinputkan pengguna terdapat kesalahan pengejaan.

Berlawanan dengan apa yang diimplementasikan oleh Google, pada [*website* perpusatakaan digital milik UIN Sunan Kalijaga Yogyakarta](https://digilib.uin-suka.ac.id/) masih menerapkan algoritma konvensional untuk melakukan *information retrieval* pada dokumen jurnal-jurnal ilmiahnya. Logika konvensional yang diterapkan pada *website* perpusatakaan digital tersebut merupakan algoritma *boolean search*. *Boolean search* adalah metode yang dapat digunakan untuk melakukan *information retrieval* dari kumpulan dokumen, metode ini berdasar kepada kombinasi antara logika boolean dan teori himpunan. Metode *boolean search* akan mencocokan kesamaan yang terdapat pada kata-kata yang ada di dalam queri yang dimasukkan oleh pengguna sebagai kumpulan kata kunci dengan judul dari dokumen-dokumen yang terdapat didalam kumpulan jurnal tempat perpustakaan menyimpan dokumen-dokumennya. Dokumen jurnal yang akan ditampilkan ke pengguna adalah dokumen yang memiliki judul yang berisi dengan kata kunci yang berada pada queri.

Penulis juga tidak memiliki akses terhadap algoritma yang diterapkan pada perpustakaan digital milik universitas tempat penulis kuliah, tetapi berdasarkan gambar 3 dan gambar 4 penulis dapat memastikan bahwa algoritma yang diterapkan berbeda dengan algoritma *machine learning* modern yang diterapkan Google. Pada gambar 3 perpustakaan digital berhasil menampilkan dokumen-dokumen yang berhubungan dengan queri "SISTEM TEMU KEMBALI INFORMASI", tetapi pada gambar 4 dimana perpustakaan digital diuji dengan menggunakan queri "SISTEM TEMU KEMBALI INFORMASII" yang dimana terdapat kesalahan dalam penulisan, sistem perpustakaan tidak mampu mengetahui maksud pengguna sebenarnya saat diberi queri yang memiliki kesalahan ketik. Ini merupakan indikasi bahwa sistem perpustakaan digital tersebut menerapkan model *information retrieval* metode konvensional *boolean search* karena sama sekali tidak merekomendasikan satu dokumen yang relevan seperti yang direkomendasikan pada gambar 3. 

![image](https://github.com/Zelkova46/ML-terapan/assets/70127988/93dcfd73-91da-47b9-99db-2ef3acf52ff6)
Gambar 3. Sistem perpustakaan digital merekomendasikan sejumlah dokumen berdasarkan queri normal dari pengguna

![image](https://github.com/Zelkova46/ML-terapan/assets/70127988/3ceb0e49-cdad-46c9-abbc-c124c89db8c0)
Gambar 4. Sistem perpustakaan digital gagal menemukan dokumen untuk queri abnormal dari pengguna

Permasalahan yang telah dipaparkan tersebut akan membatasi dan merupakan sebuah rintangan yang perlu diselesaikan dalam bidang *information retrieval* di zaman modern ini. Dengan berusaha menerapkan model yang menerapkan *flexible search*, walaupun mungkin hasilnya masih tidak sebaik algoritma yang dimiliki Google, algoritma *flexible search* ini masih lebih baik dari *boolean search* karena tetap mampu memberikan beberapa rekomendasi dokumen dengan memberikan nilai relevansi dengan queri yang dimiliki pengguna sebagai pertimbangan pengguna apakah akan menerima dokumen rekomendasi dari sistem atau tidak.  


### Problem Statements

- Bagaimana mengembangkan sistem temu kembali informasi dan rekomendasi jurnal ilmiah untuk mengukur nilai relevansi dokumen?
- Bagaimana mengimplementasikan algoritma Cosine Similarity dalam proses perankingan dan rekomendasi jurnal ilmiah kepada pengguna?

### Goals

- Mengembangkan sebuah sistem temu kembali informasi dan rekomendasi jurnal ilmiah yang menggunakan algoritma *Cosine Similarity* untuk mengukur nilai relevansi dokumen. Sistem ini akan memanfaatkan model machine learning untuk menghitung kemiripan antara queri pengguna dengan konten jurnal ilmiah. Tujuannya adalah untuk memberikan pengalaman pencarian yang lebih relevan dan akurat bagi pengguna. Langkah-langkah untuk mewujudkan hal tersebut adalah dengan mengumpulkan data jurnal ilmiah, melakukan pemrosesan teks untuk menghasilkan representasi vektor dokumen, menghitung kemiripan antara vektor query pengguna dan vektor dokumen menggunakan Cosine Similarity.
  
- Mengimplementasikan algoritma *Cosine Similarity* dalam proses perankingan dan rekomendasi jurnal ilmiah kepada pengguna. Dalam hal ini, algoritma *Cosine Similarity* akan digunakan untuk mengukur sejauh mana dokumen-dokumen dalam koleksi memiliki relevansi dengan query yang diberikan oleh pengguna. Tujuan utama adalah menyajikan rekomendasi jurnal ilmiah yang paling sesuai dengan preferensi dan kebutuhan pengguna, sehingga memudahkan proses pencarian informasi yang lebih efektif.


## Data Understanding
Paragraf awal bagian ini menjelaskan informasi mengenai jumlah data, kondisi data, dan informasi mengenai data yang digunakan. Sertakan juga sumber atau tautan untuk mengunduh dataset. Contoh: [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/Restaurant+%26+consumer+data).

Selanjutnya, uraikanlah seluruh variabel atau fitur pada data. Sebagai contoh:  

Variabel-variabel pada Restaurant UCI dataset adalah sebagai berikut:
- accepts : merupakan jenis pembayaran yang diterima pada restoran tertentu.
- cuisine : merupakan jenis masakan yang disajikan pada restoran.
- dst

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



_Referensi:_

- [Arguello, Jaime (2013). INLS 509 : Introduction to Information Retrieval.](https://ils.unc.edu/courses/2021_fall/inls509_001/) 
- [Beel, Joeran; Gipp, Bela; Lange, Stefan; Breitinger, Corinna (2015-07-26). "Research-paper recommender systems: a literature survey".](https://kops.uni-konstanz.de/entities/publication/861ddd16-fbc6-4ee4-a77f-6bba081041f3)
- Lancaster, F.W.; Fayen, E.G. (1973), Information Retrieval On-Line, Melville Publishing Co., Los Angeles, California
