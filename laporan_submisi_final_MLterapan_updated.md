# Laporan Proyek Sistem Pencarian Rekomendasi Ayat Al-Qur'an terjemahan yang terkait berdasarkan Nilai *cosine similarity* - Muhammad Imam Ariq Sya'bana

## Domain Proyek

Information Retrieval (IR) merupakan bidang yang berkaitan dengan struktur, analisis, organisasi, penyimpanan, pencarian, dan pengambilan informasi. Pada dasarnya, IR berfokus pada bagaimana kita bisa menemukan dan mengambil informasi yang relevan dari kumpulan data yang ada. Dalam konteks modern, kemajuan teknologi telah membuat proses pengumpulan informasi menjadi lebih mudah dan efisien.

Di era modern ini, dengan kemajuan teknologi yang pesat, mencari informasi menjadi jauh lebih mudah. Sebagai contoh, teknologi kini memungkinkan kita untuk mencari ayat-ayat Al-Qur'an secara cepat dan akurat. Berbagai platform digital seperti pada mesin pencari Google telah dikembangkan untuk mempermudah umat Muslim menemukan ayat yang sesuai dengan topik atau tema tertentu. Pengguna hanya perlu memasukkan kata kunci yang relevan, dan teknologi pencarian yang canggih akan menampilkan situs-situs web yang berbicara tentang ayat-ayat Al-Qur'an yang berkaitan dengan kata kunci tersebut. Algoritma yang digunakan memastikan bahwa hanya ayat yang relevan akan dimunculkan, memudahkan dalam studi dan pemahaman Al-Qur'an.

![image](https://github.com/user-attachments/assets/42f079a8-a1be-43af-ae55-5d83f2797529)
Gambar 1. Hasil rekomendasi pencarian jurnal ilmiah dengan menggunakan Google Scholar 

Google secara otomatis mencari dan menghitung relevansi dokumen berdasarkan prinsip flexible search. Hail pencarian tidak hanya menampilkan artikel-artikel yang relevan atau tidak relevan saja. Hasil pencarian menampilkan semua artikel dari yang paling relevan hingga yang kurang relevan. Ini adalah contoh implementasi sistem rekomendasi, di mana rekomendasi dokumen atau artikel disesuaikan dengan permintaan pengguna dan tingkat kesamaan dengan dokumen. Mesin pencari Google menggunakan pendekatan *content based filtering*, yang berfokus pada kata kunci yang dimasukkan pada search bar sebagai atribut penting dalam menilai relevansi.

Algoritma pencarian dokumen relevan milik Google yang diterapkan di dalam mesin pencari milik Google atau produk lain dari Google, seperti Google Scholar merupakan algoritma yang kompleks dan paten milik Google. Media Google menampilkan hasil pencarian ayat Qur'an yang terkait bersamaan dengan artikel-artikel yang membicarakan ayat tersebut. Apabila ingin lebih ringkas dan jika ingin mengetahui skor relevansi dari seluruh ayat Al-Qur'an dengan kata kunci yang kita masukkan, masih dibutuhkan program yang bisa merekomendasikan ayat-ayat Al-Qur'an yang relevan. Karena alasan tersebut penulis merasa projek untuk membuat sistem rekomendasi untuk pencarian ayat Al-Qur'an berdasarkan kata kunci masih perlu dikerjakan. Projek sistem temu kembali informasi ini akan dibuat dengan memperhatikan *Relevance Factor* yang ditentukan dengan menggunakan algoritma *Cossine similarity* untuk mengetahui nilai relevansi untuk masing-masing ayat Al-Qur'an yang direkomendasikan.


## Business Understanding

Permasalahan yang diangkat pada proyek ini berasal dari pengalaman penulis saat ingin mencari ayat-ayat Al-Qur'an yang relevan dengan topik tertentu, tetapi menghadapi kesulitan dalam menemukan hasil yang akurat dan cepat hanya dengan menggunakan aplikasi Al-Qur'an yang tersedia. Seperti yang telah dijelaskan pada bagian domain proyek, Google memiliki algoritma kompleks yang memadukan teknik machine learning untuk menghasilkan rekomendasi artikel yang relevan dengan topik yang pengguna ingin cari. Prinsip yang sama dapat diterapkan pada pencarian ayat Al-Qur'an, yaitu dengan memanfaatkan ide "flexible search". Sistem ini memungkinkan pencarian untuk memahami berbagai tipe kueri, maksud pengguna, dan kebutuhan informasi, bahkan jika kueri yang dimasukkan tidak tepat, mengandung kesalahan ejaan, atau tidak sepenuhnya sesuai dengan ayat yang ada di database. Algoritma flexible search tetap mampu memberikan hasil yang relevan, sehingga memudahkan pengguna dalam menemukan ayat Al-Qur'an yang sesuai dengan kata kunci yang diberikan. Implementasi flexible search ini bisa menjadi solusi penting dalam mempermudah studi dan pemahaman Al-Qur'an di era digital.

Selain itu, flexible search memiliki keunggulan dibandingkan dengan boolean search yang lebih tradisional. Pada boolean search, hasil pencarian sangat bergantung pada ketepatan kueri yang dimasukkan, sehingga jika pengguna salah mengetik atau menggunakan kata kunci yang tidak tepat, hasil ayat Al-Qur'an rekomendasi yang ditampilkan bisa saja kurang relevan atau bahkan tidak ada sama sekali. Di sisi lain, flexible search mampu menangani variasi kata kunci dengan lebih dinamis, karena algoritmanya tidak hanya fokus pada kecocokan kata kunci secara literal, tetapi juga pada konteks dan makna kueri. Dengan demikian, flexible search dapat memberikan hasil yang lebih luas dan relevan, meskipun input pengguna tidak sempurna. Hal ini menjadikannya lebih unggul dalam pencarian ayat Al-Qur'an, di mana kompleksitas bahasa dan variasi penulisan sering kali menjadi tantangan tersendiri dalam pencarian berbasis boolean.

![image](https://github.com/Zelkova46/ML-terapan/assets/70127988/93dcfd73-91da-47b9-99db-2ef3acf52ff6)
Gambar 3. Sistem perpustakaan digital merekomendasikan sejumlah dokumen berdasarkan kueri normal dari pengguna


![image](https://github.com/Zelkova46/ML-terapan/assets/70127988/3ceb0e49-cdad-46c9-abbc-c124c89db8c0)
Gambar 4. Sistem perpustakaan digital gagal menemukan dokumen untuk kueri abnormal dari pengguna

Dengan demikian, perbedaan utama antara keduanya adalah dalam pendekatan flexible search Google yang mampu memahami maksud pengguna dan memberikan rekomendasi relevan meskipun kueri tidak sempurna, sementara boolean search perpustakaan digital hanya membandingkan kata-kunci dalam kueri dengan judul dokumen untuk menentukan hasil yang ditampilkan.

Dalam konteks proyek ini, perbedaan pendekatan boolean search dengan sistem rekomendasi modern yang menerapkan machine learning menjadi relevan. Sistem rekomendasi yang dibangun dalam proyek ini menggunakan algoritma *cosine similarity* untuk mengukur relevansi dan melakukan rekomendasi berdasarkan nilai-nilai relevansi antara judul-judul dokumen. Pendekatan ini lebih fleksibel dan mampu mengatasi variasi dalam kueri pengguna, seperti kesalahan pengejaan atau variasi kata. Dengan demikian, proyek ini mencoba mengatasi keterbatasan boolean search dengan memanfaatkan teknik machine learning yang lebih modern. Meotde *cosine similarity* ini akan mampu memberikan beberapa rekomendasi dokumen beserta dengan memberikan nilai relevansi dengan kueri yang dimiliki pengguna sebagai pertimbangan pengguna apakah akan menerima dokumen rekomendasi dari sistem atau tidak.  

### Problem Statements

- Bagaimana mengembangkan sistem temu kembali informasi dan rekomendasi jurnal ilmiah untuk mengukur nilai relevansi dokumen?
- Bagaimana mengimplementasikan algoritma *cosine similarity* dalam proses perankingan dan rekomendasi jurnal ilmiah kepada pengguna?

### Goals

- Mengembangkan sebuah sistem temu kembali informasi dan rekomendasi jurnal ilmiah yang menggunakan algoritma *cosine similarity* untuk mengukur nilai relevansi dokumen. Sistem ini akan memanfaatkan model machine learning untuk menghitung kemiripan antara kueri pengguna dengan konten jurnal ilmiah. Tujuannya adalah untuk memberikan pengalaman pencarian yang lebih relevan dan akurat bagi pengguna. Langkah-langkah untuk mewujudkan hal tersebut adalah dengan mengumpulkan data jurnal ilmiah, melakukan pemrosesan teks untuk menghasilkan representasi vektor dokumen, menghitung kemiripan antara vektor queri pengguna dan vektor dokumen menggunakan *cosine similarity*.
  
- Mengimplementasikan algoritma *cosine similarity* dalam proses perankingan dan rekomendasi jurnal ilmiah kepada pengguna. Dalam hal ini, algoritma *cosine similarity* akan digunakan untuk mengukur sejauh mana dokumen-dokumen dalam koleksi memiliki relevansi dengan kueri yang diberikan oleh pengguna. Tujuan utama adalah menyajikan rekomendasi jurnal ilmiah yang paling sesuai dengan preferensi dan kebutuhan pengguna, sehingga memudahkan proses pencarian informasi yang lebih efektif.


## Data Understanding

Dataset yang penulis gunakan pada projek ini berisi tentang paper penelitian di dalam domain NLP, dimana di dalam file terdapat beberapa informasi atribut yang dapat digunakan untuk melakukan *information retrieval*. *Dataset* berisi atribut mengenai judul, penulis, tautan, domain, dan subdomain paper. Untuk indeks masing-masing paper didaftarkan ke dalam atribut yang bernamaa Index_Paper (Sno).

Tautan ke Research Paper dataset : https://www.kaggle.com/datasets/vijendersingh412/research-paper

### Variabel-variabel pada Research Paper dataset adalah sebagai berikut:
- Index_Paper (Sno): merupakan tipe data integer yang menunjukkan index masing-masing paper.
- Paper : atribut dengan tipe data string yang menunjukkan judul paper jurnal.
- Link : atribut dengan tipe data string yang berisi tautan ke paper jurnal di internet.
- Authors : Atribut dengan tipe data string yang mencantumkan informasi tentang penulis dari paper.
- Domain : Ranah pembahasan paper, bertipe data string.
- Subdomain : Bagian dari domain yang berisi tema pembahasan lebih menjurus, bertipe data string. 

Untuk memahami atribut-atribut yang ada di dalam dataset tersebut dilakukan beberapa langkah untuk memahami isi dan tipe atribut tersebut. Pertama, dengan menggunakan fungsi bawaan dari python yaitu .info() penulis bisa mendapatkan bahwa dalam dataset tersebut tidak terdapat data yang kosong dan bisa mengetahui tipe data dari masing-masing atribut yang ada pada dataset. 

Tabel 1. keluaran dari *built-in function* bahasa pemrograman Python pada dataset *house price*

| Column | Non-Null Count | Dtype |
|:----------------:|:---------------:|:---------------:|
| Index Paper (Sno)     | 82 non-null   | int64     |
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

- 1. Melakukan *mapping* semua atribut yang ada di dataset ke dalam variabelnya masing-masing

Untuk sistem rekomendasi dengan menggunakan metode *content based filtering* semua atribut yang ada di dalam dataset berperan penting untuk menentukan hasil perangkingan rekomendasi. Tahapan selanjutnya dalam pembangunan sistem pada proses *modeling* juga diminta untuk memisahkan atribut tertentu saja yang diproses, sehingga tahapan memecah dataset yang sudah diinputkan menjadi bentuk *dataframe* esensial untuk dilakukan. 
 
- 2. Mengubah tipe data variabel masing-masing atribut dari numpy.ndarray menjadi list
 
Untuk mempersiapkan tahap *modeling* yang akan dilakukan setelah tahap *data preparation* ini, perlu dilakukan konversi tipe data untuk masing-masing variabel atribut dataset. Konversi tipe data ini diperlukan karena tahap *modeling* nantinya akan menerapkan algoritma *cosine similarity* dengan memanfaatkan *library* yang dimiliki oleh scikit-learn yaitu TfidfVectorizer dan cosine_similarity. Pada *library* tersebut menerima input parameter yang akan mengeluarkan hasil eror jika argumen yang dimasukkan memiliki tipe data numpy.ndarray. Maka dari itu penulis akan merubah tipe data masing-masing variabel atribut menjadi tipe *list*

- 3. Mempersiapkan queri dan dokumen yang akan digunakan untuk membuat sistem rekomendasi pada tahap *modeling*.
 
Tahap *modeling* yang akan dilakukan setelah tahap *data preparation* ini akan membutuhkan dua elemen supaya fungsinya dapat bekerja. Kedua elemen tersebut adalah queri yang diinputkan pengguna dan jurnal ilmiah yang merupakan dokumen yang mengandung kata kunci untuk dirujuk oleh queri pengguna. Queri dalam projek sistem pencarian jurnal ilmiah kali ini adalah suatu kata kunci (*keyword*) yang akan digunakan model untuk merekomendasikan dokumen relevan yang dibutuhkan user pada tahap *modeling*. Input dari pengguna akan dirubah menjadi bentuk string agar bisa di vektorisasi pada tahap *modeling*. Semua judul dokumen jurnal penelitian ilmiah juga perlu dibuat menjadi daftar *string* seperti yang telah dilakukan pada tahap dua data preparation sebelumnya untuk dapat dilakukan vektorisasi dalam tahap *modeling*.


## Modeling


- 1. Melakukan vektorisasi dengan menggunakan fungsi TF-IDF Vectorizer

Dalam tahap pembuatan model *machine learning* untuk proyek *research paper recommendation*, metode yang digunakan adalah *cosine similarity*. Metode ini mengukur kesamaan antara dokumen berdasarkan kata kunci dalam bentuk vektor. Kelebihan metode *cosine similarity* yang dimanfaatkan pada projek ini diantaranya adalah kemampuan untuk mengukur kesamaan semantik diantara jurnal-jurnal. Kedua, judul yang ada pada masing-masing paper dapat digunakan untuk dirubah menjadi representasi vector numeric dengan menggunakan teknik TF-IDF yang dapat dilakukan dengan menggunakan *library* yang sama seperti cosine_similarity dimiliki juga oleh scikit-learn. Ketiga, *cosine similarity* merupakan metode yang penulis rasa paling tepat untuk diterapkan pada projek ini, mengingat projek ini mengambil pendekatan *content-based recommendation*. Judul yang ada pada paper dijadikan faktor utama untuk menghasilkan rekomendasi jurnal yang paling relevan sesuai dengan keinginan pengguna. Terakhir, hasil keluaran atau hasil rekomendasi dokumen yang dihasilkan oleh metode ini dapat direpresentasikan secara numerik dengan menggunakan nilai *similarity score*. Dokumen yang paling direkomendasikan ke pengguna akan ditampilkan paling atas oleh sistem dengan tambahan keterangan nilai *similarity score* yang dapat digunakan untuk mempertimbangkan relevansi jurnal rekomendasi dengan kueri yang dimasukkan oleh pengguna. Semakin tinggi nilai *similarity score*, maka pengguna dapat semakin yakin bahwa hasil rekomoendasi jurnal yang sistem berikan valid. 



- 2. Menghitung nilai *cosine similarity* dengan memanfaatkan fungsi ```cosine_similarity``` yang dimiliki oleh scikit-learn

Pada tahap *modeling* yang terjadi di projek ini terdapat beberapa alur utama untuk mendapatkan rekomendasi jurnal yang paling relevan dengan input kueri pengguna. Langkah pertama, pada tahap *data preparation* pengguna harus memasukkan input berupa judul atau topik pembahasan jurnal ilmiah yang ingin dicari. Input dari pengguna akan dirubah menjadi bentuk string yang nantinya model akan mencari kecocokan dengan dokumen jurnal yang ada di *dataset*. Untuk dapat mencocokan kueri pengguna dengan dokumen jurnal di dalam dataset, pertama penulis mendefinisikan *object vectorizer* untuk digunakan sebagai *TF-IDF vectorizer*. Objek tersebut digunakan untuk melakukan vektorisasi sehingga judul dokumen yang berupa kata-kata menjadi bentuk vektor numerik sehingga dapat dilakukan komputasi. Selanjutnya dengan menggunakan *object vectorizer* yang sama, kueri yang diinputkan oleh pengguna juga perlu dilakukan vektorisasi sehingga kueri pengguna yang berupa string juga menjadi bentuk vektor numerik. Langkah vektorisasi tersebut menggunakan ```TfidfVectorizer()``` yang berasal dari *library* scikit-learn. Setelah itu dengan mengunakan ```cosine_similarity``` milik *library* scikit-learn, dilakukan perhitungan nilai *cosine similarity* antara vektor kueri dengan masing-masing vektor dokumen. Rumus *cosine similarity* yang diimplementasikan pada  fungsi ```cosine_similarity``` milik *library* scikit-learn tertera pada persamaan 1.

Persamaan 1. Rumus *cosine similarity*

Cosine(A,B) = $similarity = \cos (\theta) = \frac{A \cdot B}{||A|| \cdot ||B||} = \frac{\sum_{i=1}^{n} A_i B_i}{\sqrt{\sum_{i=1}^{n} A_i^2} \cdot \sqrt{\sum_{i=1}^{n} B_i^2}}$

Keterangan : 

${A}$: kueri dari pengguna yang sudah dalam bentuk vektor setelah melakukan vektorisasi

${B}$ : Setiap judul jurnal yang ada di dataset yang telah berbentuk vektor setelah vektorisasi 

${n}$ : Jumlah seluruh dokumen


- 3. Menampilkan hasil rekomendasi jurnal ilmiah beserta dengan nilai kesamaannya dengan queri pengguna

Setelah masing-masing dokumen telah memiliki nilai *cosine similarity*, dokumen yang memiliki nilai  *cosine similarity* bukan nol akan ditampilkan ke pengguna dari dokumen yang memiliki nilai  *cosine similarity* tertinggi ke yang terendah. Dokumen yang nilai  *cosine similarity*-nya sama dengan nol tidak dimunculkan ke pengguna. Jurnal penelitian yang direkomendasikan sistem akan berupa judul jurnal paling relevan diikuti dengan atribut lain dari masing-masing jurnal seperti tautan ke jurnal, penulis, domain, dan subdomain jurnal.    


Tabel 2. Rekomendasi lima dokumen jurnal ilmiah paling relevan keluaran dari sistem

| Index Paper | Judul Paper | Tautan Paper | Penulis Paper | Domain Paper | Sub-Domain Paper | Nilai Kesamaan |
|-------------|-------------|--------------|---------------|--------------|------------------|----------------|
| 9           | Natural Language Processing (Almost) from Scratch | [Link](https://www.jmlr.org/papers/volume12/collobert11a/collobert11a.pdf) | Ronan Collobert | NLP | Neural Models | 0.5306739342378072 |
| 17          | Class-Based n-gram Models of Natural Language | [Link](https://www.aclweb.org/anthology/J92-4003.pdf) | Peter F. Brown, Vincent J. Della Pietra, Peter V. deSouza, Jenifer C. Lai, Robert L. Mercer | NLP | Clustering & Word/Sentence Embeddings | 0.30785002707851433 |
| 27          | A Bit of Progress in Language Modeling | [Link](https://arxiv.org/pdf/cs/0108005.pdf) | Joshua T. Goodman | NLP | Language Modeling | 0.28713991957257223 |
| 13          | Understanding LSTM Networks | [Link](http://colah.github.io/posts/2015-08-Understanding-LSTMs/) | Christopher Olah | NLP | Neural Models | 0.26575279920665473 |
| 49          | Bidirectional LSTM-CRF Models for Sequence Tagging | [Link](https://arxiv.org/pdf/1508.01991.pdf) | Zhiheng Huang, Wei Xu, Kai Yu | NLP | Sequential Labeling & Information Extraction | 0.18278553385147825 |

Tabel 2 diatas menampilkan lima dokumen jurnal ilmiah paling relevan dari keselueuhan dokumen yang ada pada dataset. Lima dokumen tersebut menurut sistem paling relevan jika input kueri dari pengguna yaitu "LSTM network used in Natural Language Processing". Hasil keluaran dari sistem rekomendasi tersebut sebenarnya berjumlah lima belas dokumen jurnal relevan, jumlah tersebut karena ke-15 dokumen tersebut memiliki nilai *cosine similarity*. Tetapi, pada tabel 2 untuk mempersingkat dan efisiensi dalam visualisasi hanya ditampilkan lima dokumen jurnal ilmiah paling relevan saja.

## Evaluation

Metode yang digunakan untuk mengevaluasi seberapa baik model sistem rekomendasi jurnal merekomendasikan dokumen yang relevan dengan kueri yang dimasukkan pengguna adalah dengan menggunakan penentuan klasifikasi biner. Metode yang diterapkan akan menilai apakah model merekomendasikan dokumen relevan atau tidak relevan, karena opsi kemungkinan ada dua maka metode klasifikasi biner dipilih dalam projek ini. Apabila dokumen dapat menampilkan dokumen yang relevan dan oleh pengguna juga merasa dokumen yang direkomendasikan itu relevan maka model semakin bagus. Kebalikannya, apabila sistem menampilkan rekomendasi dokumen yang menurut pengguna tidak relevan dengan kueri yang diinputkan, maka model akan dinilai semakin buruk.

Untuk mendapatkan data guna mengevaluasi model sistem rekomendasi tersebut, penulis perlu mengecek satu per satu secara manual apakah jurnal yang direkomendasikan oleh sistem adalah benar relevan. Pada tahap evaluasi model sistem ini penulis mengevaluasi semua jurnal yang direkomendasikan oleh sistem. Apabila sistem memberi nilai kesamaan bukan nol artinya jurnal tersebut adalah relevan menurut sistem. Model yang bekerja dengan baik adalah saat dievaluasi oleh penulis, penulis juga menganggap bahwa dokumen tersebut relevan.  Apabila sistem memberikan rekomendasi jurnal yang salah, karena pada saat di evaluasi oleh penulis, penulis tidak menganggap itu relevan maka akan mengurangi penilaian evaluasi terhadap model. Terakhir model juga akan mendapatkan nilai yang rendah apabila terdapat jurnal yang menurut penulis relevan, tetapi tidak direkomendasikan atau mendapat nilai kesamaan dengan kueri sama dengan nol. Proses penulis mengevaluasi hasil rekomendasi jurnal yang dikeluarkan oleh sistem terlampir di tabel 3.


Tabel 3. Tabel evaluasi hasil rekomendasi dokumen jurnal ilmiah dari sistem

| | |
|:----------------:|:---------------:|
| Nomor Jurnal     | 49   |
| Judul     | Bidirectional LSTM-CRF Models for Sequence Tagging  |
| Penulis       | Zhiheng Huang, Wei Xu, Kai Yu |
| Domain      | NLP |
| Subdomain      | Sequential Labeling & Information Extraction |
| queri pengguna   | LSTM network used in Natural Language Processing |
| Nilai kesamaan dengan queri      | 0.18278553385147825 |
| Evaluasi kerelevanan dokumen dengan queri     | True |


Dalam pengimplementasian klasifikasi biner diperlukan nilai  *True positives* (TP), *True negatives* (TN), *False positives* (FP), dan *False negatives* (FN). True positive (TP) adalah nilai seberapa banyak model mampu memprediksi dokumen relevan dengan benar. True negative (TN) adalah nilai seberapa banyak model mampu memprediksi dokumen tidak relevan dengan benar. False positive (FP) adalah nilai seberapa banyak model mampu memprediksi dokumen relevan pada dokumen tidak relevan. False negative (FN) adalah nilai seberapa banyak model mampu memprediksi dokumen tidak relevan pada dokumen relevan.

Untuk melakukan hal tersebut kali ini akan diterapkan beberapa metrik untuk melakukan evaluasi penentuan klasifikasi biner. Metrik tersebut adalah *precision, recall, F1-score, dan akurasi*. Metrik *accuracy* adalah nilai yang didapat dari seluruh dokumen yang sukses diprediksi secara benar baik relevan maupun tidak relevan (TP + TN), dibagi dengan seluruh dokumen yang ada (TP + FN + FP + TN). Nilai *precision* didapat dari seluruh dokumen yang direkomendasikan ke user dan user menganggap dokumen tersebut memang relevan artinya dokumen yang benar-benar relevan (TP) dibagi dengan seluruh dokumen yang menurut sistem relevan (TP + FP). *Precision* dapat mengukur berapa banyak paper yang direkomendasikan yang benar-benar relevan. Metrik *Recall* adalah nilai yang didapat dari rekomendasi dokumen yang benar-benar relevan (TP) dibagi dengan semua dokumen yang relevan, ini termasuk dokumen yang benar-benar relevan (TP) dan dokumen yang sebenarnya relevan tetapi tidak direkomendasikan oleh sistem (FP). Terakhir adalah F1-score, *F1-Score* adalah metrik yang menilai keseimbangan antara nilai *precision* dan *recall*. Formula metrik *precision, recall, F1-score, dan akurasi* tertulis pada persamaan 2.

Persamaan 2. Rumus *precision, recall, F1-score, dan akurasi*

Accuracy = $\frac{TP+TN}{TP+TN+FP+FN}$

Precision = $\frac{TP}{TP+FP}$

Recall = $\frac{TP}{TP+FN}$

F1 = $\frac{2 \cdot Precision \cdot Recall}{Precision + Recall}$

 
Setelah empat metrik tersebut telah selesai dihitung, hasil nilai masing-masing metrik tertera pada tabel 3. Nilai *precision* menunjukkan 0.8, *recall* model mendapat skor 0.48, *accuracy* model adalah 0.8049, dan *F1-score* adalah 0.6. 

Tabel 4. Nilai metrik hasil evaluasi model rekomendasi

| Metrics | Score |
|:----------------:|:---------------:|
| Precision     | 0.8   |
| Recall     | 0.48  |
| F1-Score       | 0.6 |
| Accuracy      | 0.8049 |


_Catatan:_

- Untuk projek sistem rekomendasi jurnal ilmiah kali ini, karena penulis hanya menggunakan *dataset* milik orang lain yang berisi kurang dari 100 data, penulis memilih cara evaluasi ini karena penulis masih mampu mengevaluasi data yang hanya sedikit. Apabila projek rekomendasi digunakan pada data yang berjumlah sangat besar cara ini tidak masuk akal karena dokumen terlalu banyak untuk dievaluasi satu per satu, tetapi penulis akan menggunakan metode evaluasi dengan cara *cross-validation*. Cross-validation adalah teknik untuk mengevaluasi model *machine learning* dengan cara melatih model rekomendasi dengan input sebagian dataset atau subset dari dataset (training sets) dan menguji model yang sudah ditrain tersebut dengan menggunakan data yang belum dipakai untuk melatih model (test sets) dalam mengklasifikasikan jurnal yang relevan atau bukan. Untuk menggunakan metode *cross-validation* membutuhkan sample data yang banyak supaya model bisa belajar dengan baik mengklasifikasikan dokumen termasuk ke dalam dokumen relevan atau bukan relevan, dan menghasilkan rekomendasi yang dapat diandalkan. Karena jumlah data yang ada pada dataset yang digunakan pada projek ini hanya sedikit, maka metode evaluasi *cross-validation* tidak dapat digunakan.


_Referensi:_

- [Arguello, Jaime (2013). INLS 509 : Introduction to Information Retrieval.](https://ils.unc.edu/courses/2021_fall/inls509_001/) 
- [Beel, Joeran; Gipp, Bela; Lange, Stefan; Breitinger, Corinna (2015-07-26). "Research-paper recommender systems: a literature survey".](https://kops.uni-konstanz.de/entities/publication/861ddd16-fbc6-4ee4-a77f-6bba081041f3)
- Lancaster, F.W.; Fayen, E.G. (1973), Information Retrieval On-Line, Melville Publishing Co., Los Angeles, California
- [Rizki Tri Wahyuni, Dhidik Prastiyanto, Eko Supraptono. Penerapan Algoritma Cosine Similarity dan Pembobotan TF-IDF pada Sistem Klasifikasi Dokumen Skripsi](https://journal.unnes.ac.id/nju/index.php/jte/article/view/10955)
- [Melita, Ria, et al. "Penerapan Metode Term Frequency Inverse Document Frequency (Tf-Idf) Dan Cosine Similarity Pada Sistem Temu Kembali Informasi Untuk Mengetahui Syarah Hadits Berbasis Web (Studi Kasus: Syarah Umdatil Ahkam)." J. Tek. Inform 11.2 (2018): 149-164.](https://pdfs.semanticscholar.org/9602/e7bae1c8b44f4b52e56fdca2b879dca6f1a2.pdf)
- [Caelen, O. (2017). A Bayesian interpretation of the confusion matrix. Annals of Mathematics and Artificial Intelligence, 81(3–4), 429–450.](https://doi.org/10.1007/s10472-017-9564-8)
- [Kulkarni, A., Chong, D., & Batarseh, F. A. (2020). Foundations of data imbalance and solutions for a data democracy. Data Democracy: At the Nexus of Artificial Intelligence, Software Development, and Knowledge Engineering, 83–106.](https://doi.org/10.1016/B978-0-12-818366-3.00005-8)
- [Lahitani, Alfirna Rizqi, Adhistya Erna Permanasari, and Noor Akhmad Setiawan. "Cosine similarity to determine similarity measure: Study case in online essay assessment." 2016 4th International Conference on Cyber and IT Service Management. IEEE, 2016.](https://ieeexplore.ieee.org/abstract/document/7577578/)
- [Zulfikar Ghazali, 1420010014 (2016) EVALUASI SISTEM TEMU KEMBALI INFORMASI OPAC (ONLINE PUBLIC ACCESS CATALOGUE) DI PERPUSTAKAAN UNIVERSITAS ISLAM NEGERI (UIN) SUNAN KALIJAGA YOGYAKARTA.](https://digilib.uin-suka.ac.id/id/eprint/22931/)
- [Ayani Anugerah Wardani, NIM.: 17101040033 (2021) EFEKTIVITAS OPAC SEBAGAI SISTEM TEMU KEMBALI INFORMASI KOLEKSI ISLAM BUKU BERBAHASA ARAB DI PERPUSTAKAAN UIN SUNAN KALIJAGA YOGYAKARTA (TINJAUAN RECALL DAN PRECISION). ](https://digilib.uin-suka.ac.id/id/eprint/49325/)
