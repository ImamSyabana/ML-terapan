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

Dataset yang penulis gunakan pada projek ini berisi tentang paper penelitian di dalam domain NLP, dimana di dalam file terdapat beberapa informasi atribut yang dapat digunakan untuk melakukan *information retrieval*. *Dataset* berisi atribut mengenai judul, penulis, tautan, domain, dan subdomain paper. Untuk indeks masing-masing paper didaftarkan ke dalam atribut yang bernamaa Sno.

Tautan ke Research Paper dataset : https://www.kaggle.com/datasets/vijendersingh412/research-paper

### Variabel-variabel pada Research Paper dataset adalah sebagai berikut:
- Sno : merupakan tipe data integer yang menunjukkan index masing-masing paper.
- Paper : atribut dengan tipe data string yang menunjukkan judul paper jurnal.
- Link : atribut dengan tipe data string yang berisi tautan ke paper jurnal di internet.
- Authors : Atribut dengan tipe data string yang mencantumkan informasi tentang penulis dari paper.
- Domain : Ranah pembahasan paper, bertipe data string.
- Subdomain : Bagian dari domain yang berisi tema pembahasan lebih menjurus, bertipe data string. 

Untuk memahami atribut-atribut yang ada di dalam dataset tersebut dilakukan beberapa langkah untuk memahami isi dan tipe atribut tersebut. Pertama, dengan menggunakan fungsi bawaan dari python yaitu .info() penulis bisa mendapatkan bahwa dalam dataset tersebut tidak terdapat data yang kosong dan bisa mengetahui tipe data dari masing-masing atribut yang ada pada dataset. 

Tabel 1. keluaran dari *built-in function* bahasa pemrograman Python pada dataset *house price*

| Column | Non-Null Count | Dtype |
|:----------------:|:---------------:|:---------------:|
| Sno     | 82 non-null   | int64     |
| Paper     | 82 non-null  | object     |
| Link       | 82 non-null | object    |
| Authors       | 82 non-null | object     |
| Domain       | 82 non-null  | object     |
| Subdomain       | 82 non-null  | object     |

Pada tahap *data understanding* dilakukan eksplorasi data yang dilakukan untuk mengetahui jumlah data yang unik untuk masing-masing atribut. Dengan mengetahui jumlah data yang unik pada setiap atribut, dapat diketahui seberapa luas koleksi paper yang dikumpulkan pada *dataset* ini.

Hasil dari eksplorasi data tersebut menunjukkan bahwa ada 82 judul paper yang unik dari keseluruhan 82 data yang ada di dataset, ini menunjukkan tidak ada judul paper yang duplikat. Selanjutnya, pada atribut Link diketahui terdapat 82 tautan unik yang mengarah ke sumber dari masing-masing paper tersebut di internet. Untuk atribut Authors diketahui bahwa terdapat 81 *authors* yang berkontribusi dalam penulisan paper yang ada di dataset ini. Apabila *authors* hanya terdapat 81, sementara jumlah paper keseluruhan ada 82, ini berarti ada satu *author* atau beberapa *authors* yang sama menulis dua judul paper yang berbeda. Untuk atribut selanjutnya adalah domain. Di dalam dataset ini, seperti yang dideskripsikan pada *webiste* kaggle, jurnal yang dikumpulkan berfokus pada paper penelitian pada bidang NLP, sehingga jumlah domain yang unik pada dataset ini hanya ada satu yaitu NLP. Terakhir, untuk atribut Subdomain, terdapat dua belas subdomain yang unik meliputi _***Machine Learning***_, _***Neural Models***_, _***Clustering & Word/Sentence Embeddings***_, _***Topic Models***_, _***Language Modeling***_, _***Segmentation, Tagging, Parsing***_, _***Sequential Labeling & Information Extraction***_, _***Machine Translation & Transliteration***_, _***Sequence-to-Sequence Models***_, _***Coreference Resolution***, ***Automatic Text Summarization***, ***Question Answering and Machine Comprehension***_, _***Generation, Reinforcement Learning***_

Tahap eksplorasi data juga dilanjutkan dengan memeriksa apakah didalam dataset terdapat data yang memiliki atribut dengan nilai kosong atau *null* dengan memanfaatkan fungsi Python ```isnull()``` dan ```sum()``` untuk mengetahui jumlah data yang tidak memiliki nilai. Setelah memeriksa nilai kosong dalam dataset didapatkan data yang nilainya kosong tidak ditemukan, karena jumlah nilai kosong pada dataset berjumlah nol.

Eksplorasi data yang terakhir adalah mengecek apakah ada data di dalam dataset yang serupa dengan data yang lain atau disebut duplikat. Setelah mengeksplor dataset untuk menemukan data duplikat dengan menggunakan fungsi ```duplicated()``` dan menjumlahkan data duplikat tersebut dengan menggunakkan fungsi ```sum``` didapatkan jumlah data duplikat adalah nol.

## Data Preparation

Di dalam projek ini proses *data preparation* yang dilakukan kebanyakan dilakukan di dalam hal menganalisis data dan memanipulasi data. Pertama-tama dataset di inputkan ke dalam projek dan data tersebut disajikan ke dalam bentuk *dataframe*. *Dataset* yang sudah dimasukkan ke dalam objek *dataframe* akan diakses dan datanya diambil dengan menggunakan fungsi yang ada pada python yang dirujuk dengan metode *integer-based indexing*.

- 1. Memetakan semua atribut yang ada di dataset ke dalam variabelnya masing-masing

Untuk sistem rekomendasi dengan menggunakan metode *content based filtering* semua atribut yang ada di dalam dataset berperan penting untuk menentukan hasil perangkingan rekomendasi. Tahapan selanjutnya dalam pembangunan sistem pada proses *modeling* juga diminta untuk memisahkan atribut tertentu saja yang diproses, sehingga tahapan memecah dataset yang sudah diinputkan menjadi bentuk *dataframe* esensial untuk dilakukan. 
 
- 2. Mengubah tipe data variabel masing-masing atribut dari numpy.ndarray menjadi list
 
Untuk mempersiapkan tahap *modeling* yang akan dilakukan setelah tahap *data preparation* ini, perlu dilakukan konversi tipe data untuk masing-masing variabel atribut dataset. Konversi tipe data ini diperlukan karena tahap *modeling* nantinya akan menerapkan algoritma *Cosine Simmilarity* dengan memanfaatkan *library* yang dimiliki oleh scikit-learn yaitu TfidfVectorizer dan cosine_similarity. Pada *library* tersebut menerima input parameter yang akan mengeluarkan hasil eror jika argumen yang dimasukkan memiliki tipe data numpy.ndarray. Maka dari itu penulis akan merubah tipe data masing-masing variabel atribut menjadi tipe *list*

## Modeling

Metode yang digunakan untuk tahap pembuatan model *machine learning* untuk projek *research paper recommendation* adalah *cosine similarity*. *Cosine simmilarity* dalam projek ini merupakan metode untuk menghitung kesamaan antara dua buah objek yang dinyatakan dalam dua buah vector dengan menggunakan kata kunci dari sebuah dokumen sebagai ukuran. Penulis menggunakan metode ini untuk pengembangan projek *research paper recommendation* karena metode *cosine simmilarity* memiliki kelebihan-kelebihan yang sangat berguna dan tepat untuk diimplementasikan utuk *information retrieval system* pada jurnal-jurnal ilmiah.

Kelebihan metode *cosine similarity* yang dimanfaatkan pada projek ini diantaranya adalah kemampuan untuk mengukur kesamaan semantik diantara jurnal-jurnal. Kedua, judul yang ada pada masing-masing paper dapat digunakan untuk dirubah menjadi representasi vector numeric dengan menggunakan teknik TF-IDF yang dapat dilakukan dengan menggunakan *library* yang sama seperti cosine_similarity dimiliki juga oleh scikit-learn. Ketiga, *cosine similarity* merupakan metode yang penulis rasa paling tepat untuk diterapkan pada projek ini, mengingat projek ini mengambil pendekatan *content-based recommendation*. Judul yang ada pada paper dijadikan faktor utama untuk menghasilkan rekomendasi jurnal yang paling relevan sesuai dengan keinginan pengguna. Terakhir, hasil keluaran atau hasil rekomendasi dokumen yang dihasilkan oleh metode ini dapat direpresentasikan secara numerik dengan menggunakan nilai *similarity score*. Dokumen yang paling direkomendasikan ke pengguna akan ditampilkan paling atas oleh sistem dengan tambahan keterangan nilai *similarity score* yang dapat digunakan untuk mempertimbangkan relevansi jurnal rekomendasi dengan queri yang dimasukkan oleh pengguna. Semakin tinggi nilai *similarity score*, maka pengguna dapat semakin yakin bahwa hasil rekomoendasi jurnal yang sistem berikan valid. 

Pada tahap *modeling* terdapat beebrapa alur utama untuk mendapatkan rekomendasi jurnal yang paling relevan dengan input queri pengguna. Langkah pertama, pengguna harus memasukkan input berupa judul atau topik pembahasan jurnal ilmiah yang ingin dicari. Input dari pengguna akan dirubah menjadi bentuk string yang nantinya model akan mencari kecocokan dengan dokumen jurnal yang ada di *dataset*. Untuk dapat mencocokan queri pengguna dengan dokumen jurnal di dalam dataset, pertama penulis mendefinisikan *object vectorizer* untuk digunakan sebagai *TF-IDF vectorizer*. Objek tersebut digunakan untuk melakukan vektorisasi sehingga judul dokumen yang berupa kata-kata menjadi bentuk vektor numerik sehingga dapat dilakukan komputasi. Selanjutnya dengan menggunakan *object vectorizer* yang sama, queri yang diinputkan oleh pengguna juga perlu dilakukan vektorisasi sehingga queri pengguna yang berupa string juga menjadi bentuk vektor numerik. Langkah vektorisasi tersebut menggunakan ```TfidfVectorizer()``` yang berasal dari *library* scikit-learn. Setelah itu dengan mengunakan ```cosine_similarity``` milik *library* scikit-learn, dilakukan perhitungan nilai *cosine similarity* antara vektor queri dengan masing-masing vektor dokumen. Setelah masing-masing dokumen telah memiliki nilai *cosine similarity*, dokumen yang memiliki nilai  *cosine similarity* bukan nol akan ditampilkan ke pengguna dari dokumen yang memiliki nilai  *cosine similarity* tertinggi ke yang terendah. Dokumen yang nilai  *cosine similarity*-nya sama dengan nol tidak dimunculkan ke pengguna. Jurnal penelitian yang direkomendasikan sistem akan berupa judul jurnal paling relevan diikuti dengan atribut lain dari masing-masing jurnal seperti tautan ke jurnal, penulis, domain, dan subdomain jurnal.    


Tabel 2. Rekomendasi lima dokumen jurnal ilmiah paling relevan keluaran dari sistem

| Index Paper | Judul Paper | Tautan Paper | Penulis Paper | Domain Paper | Sub-Domain Paper | Nilai Kesamaan |
|-------------|-------------|--------------|---------------|--------------|------------------|----------------|
| 9           | Natural Language Processing (Almost) from Scratch | [Link](https://www.jmlr.org/papers/volume12/collobert11a/collobert11a.pdf) | Ronan Collobert | NLP | Neural Models | 0.5306739342378072 |
| 17          | Class-Based n-gram Models of Natural Language | [Link](https://www.aclweb.org/anthology/J92-4003.pdf) | Peter F. Brown, Vincent J. Della Pietra, Peter V. deSouza, Jenifer C. Lai, Robert L. Mercer | NLP | Clustering & Word/Sentence Embeddings | 0.30785002707851433 |
| 27          | A Bit of Progress in Language Modeling | [Link](https://arxiv.org/pdf/cs/0108005.pdf) | Joshua T. Goodman | NLP | Language Modeling | 0.28713991957257223 |
| 13          | Understanding LSTM Networks | [Link](http://colah.github.io/posts/2015-08-Understanding-LSTMs/) | Christopher Olah | NLP | Neural Models | 0.26575279920665473 |
| 49          | Bidirectional LSTM-CRF Models for Sequence Tagging | [Link](https://arxiv.org/pdf/1508.01991.pdf) | Zhiheng Huang, Wei Xu, Kai Yu | NLP | Sequential Labeling & Information Extraction | 0.18278553385147825 |

Tabel 2 diatas menampilkan lima dokumen jurnal ilmiah paling relevan dari keselueuhan dokumen yang ada pada dataset. Lima dokumen tersebut menurut sistem paling relevan jika input queri dari pengguna yaitu "LSTM network used in Natural Language Processing". Hasil keluaran dari sistem rekomendasi tersebut sebenarnya berjumlah enam belas dokumen jurnal relevan, jumlah tersebut karena ke-16 dokumen tersebut memiliki nilai *cosine similarity*. Tetapi, pada tabel 2 untuk mempersingkat dan efisiensi dalam visualisasi hanya ditampilkan lima dokumen jurnal ilmiah paling relevan saja.

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
- [Rizki Tri Wahyuni, Dhidik Prastiyanto, Eko Supraptono. Penerapan Algoritma Cosine Similarity dan Pembobotan TF-IDF pada Sistem Klasifikasi Dokumen Skripsi](https://journal.unnes.ac.id/nju/index.php/jte/article/view/10955)
- [Melita, Ria, et al. "Penerapan Metode Term Frequency Inverse Document Frequency (Tf-Idf) Dan Cosine Similarity Pada Sistem Temu Kembali Informasi Untuk Mengetahui Syarah Hadits Berbasis Web (Studi Kasus: Syarah Umdatil Ahkam)." J. Tek. Inform 11.2 (2018): 149-164.](https://pdfs.semanticscholar.org/9602/e7bae1c8b44f4b52e56fdca2b879dca6f1a2.pdf)
