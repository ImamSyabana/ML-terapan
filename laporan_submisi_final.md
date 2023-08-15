# Laporan Proyek Sistem Pencarian Rekomendasi Jurnal Pemrosesan Bahasa Alami berdasarkan Nilai *Cosine Simmilarity* - Muhammad Imam Ariq Sya'bana

## Domain Proyek

Definisi *Information Retrieval* atau temu kembali informasi menurut Gerard Salton (1968) dalam Arguilo (2013) adalah : *Information retrieval is a field concerned with the structure, analysis, organization, storage, searching, and retrieval of information.* (Arguello, Jaime, 2013). Berdasarkan pengertian tersebut *Information Retrieval* dapat diterapkan kepada bidang-bidang kehidupan manusia yang selalu melibatkan informasi, lebih spesifiknya adalah dalam kegiatan pengumpulan informasi. 

Di zaman yang sudah modern dimana teknologi sudah canggih seperti sekarang ini, kegiatan mengumpulkan informasi sudah lebih mudah. Sebelumnya, jika ingin mencari jurnal ilmiah para pelajar harus pergi ke perpustakaan untuk mendapatkan informasi yang mereka butuhkan. Sekarang, dimana penyebaran internet sudah masif dan sistem temu kembali informasi yang sudah canggih para pelajar dapat dengan mudah untuk mengumpulkan informasi lewat gawai asalkan terkoneksi ke jaringan internet. Penulis ingin memberikan contoh Google Scholar untuk perihal pengumpulan informasi pada masa kini. Google Scholar adalah layanan yang memungkinkan pengguna untuk melakukan pencarian materi-materi pelajaran berupa teks dalam berbagai format publikasi. Google Scholar menyediakan cara yang mudah untuk mencari literatur akademis secara luas. Saat pengguna memasukkan judul atau topik literatur yang ingin dicari pada *search bar*, Google Scholar akan menampilkan jurnal-jurnal yang memiliki relevansi dengan kata kunci atau kalimat yang diinputkan oleh pengguna.

![image](https://github.com/Zelkova46/ML-terapan/assets/70127988/fc45f3f4-c48c-4495-8e41-665f449a46d2)
Gambar 1. Hasil pencarian jurnal ilmiah dengan menggunakan Google Scholar 

Mesin pencari jurnal seperti Google Scholar sudah termasuk ke dalam sistem temu kembali informasi yang modern. Google Scholar akan otomatis mencari dokumen yang tersebar di internet, lalu berdasarkan relevansi yang dihitung oleh model yang dibuat Google dokumen tersebut akan masuk ke daftar hasil pencarian dokumen Google Scholar. Hasil dokumen yang ditampilkan ke pengguna untuk rekomendasi dokumen yang dianggap sesuai dengan keinginan pengguna sudah diprogram dengan menggunakan model *machine learning* sehingga dokumen yang paling relevan pada kueri akan ditampilkan dari yang paling relevan hingga ke yang paling tidak relevan. Pada bagian dimana Google Scholar menampilkan dokumen-dokumen yang relevan dengan kueri pengguna, hal tersebut merupakan pengimplementasian dari sistem rekomendasi. Rekomendasi Google Scholar dibuat berdasarkan kueri yang diinputkan pengguna, lalu dari kueri tersebut sistem dapat membuat rekomendasi dokumen-dokumen kepada pengguna berdasakran tinggat relevansinya terhadap kueri. Dalam kasus ini sistem rekomendasi yang diimplementasikan adalah berjenis *content based filtering*, karena hasil rekomendasi bergantung pada judul yang ada pada dokumen. Karena judul merupakan atribut atau salah satu konten dari dokumen tersebut, dapat dikatakan bahwa implementasi pada Google Scholar adalah sistem rekomendasi berbasis konten.  








Pada bagian ini, Kamu perlu menuliskan latar belakang yang relevan dengan proyek yang diangkat.

**Rubrik/Kriteria Tambahan (Opsional)**:
- Jelaskan mengapa proyek ini penting untuk diselesaikan.
- Menyertakan hasil riset terkait atau referensi. Referensi yang diberikan harus berasal dari sumber yang kredibel dan author yang jelas.
  
  Format Referensi: [Judul Referensi](https://scholar.google.com/) 

## Business Understanding

Pada bagian ini, Anda perlu menjelaskan proses klarifikasi masalah.

Bagian laporan ini mencakup:

### Problem Statements

Menjelaskan pernyataan masalah:
- Pernyataan Masalah 1
- Pernyataan Masalah 2
- Pernyataan Masalah n

### Goals

Menjelaskan tujuan proyek yang menjawab pernyataan masalah:
- Jawaban pernyataan masalah 1
- Jawaban pernyataan masalah 2
- Jawaban pernyataan masalah n

Semua poin di atas harus diuraikan dengan jelas. Anda bebas menuliskan berapa pernyataan masalah dan juga goals yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**:
- Menambahkan bagian “Solution Approach” yang menguraikan cara untuk meraih goals. Bagian ini dibuat dengan ketentuan sebagai berikut: 

    ### Solution statements
    - Mengajukan 2 atau lebih solution approach (algoritma atau pendekatan sistem rekomendasi).

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

