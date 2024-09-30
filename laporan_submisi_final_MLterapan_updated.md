# Laporan Proyek Sistem Pencarian Rekomendasi Ayat Al-Qur'an terjemahan yang terkait berdasarkan Nilai *cosine similarity* - Muhammad Imam Ariq Sya'bana

## Domain Proyek

Information Retrieval (IR) merupakan bidang yang berkaitan dengan struktur, analisis, organisasi, penyimpanan, pencarian, dan pengambilan informasi. Pada dasarnya, IR berfokus pada bagaimana kita bisa menemukan dan mengambil informasi yang relevan dari kumpulan data yang ada. Dalam konteks modern, kemajuan teknologi telah membuat proses pengumpulan informasi menjadi lebih mudah dan efisien.

Di era modern ini, dengan kemajuan teknologi yang pesat, mencari informasi menjadi jauh lebih mudah. Sebagai contoh, teknologi kini memungkinkan kita untuk mencari ayat-ayat Al-Qur'an secara cepat dan akurat. Berbagai platform digital seperti pada mesin pencari Google telah dikembangkan untuk mempermudah umat Muslim menemukan ayat yang sesuai dengan topik atau tema tertentu. Pengguna hanya perlu memasukkan kata kunci yang relevan, dan teknologi pencarian yang canggih akan menampilkan situs-situs web yang berbicara tentang ayat-ayat Al-Qur'an yang berkaitan dengan kata kunci tersebut. Algoritma yang digunakan memastikan bahwa hanya ayat yang relevan akan dimunculkan, memudahkan dalam studi dan pemahaman Al-Qur'an.

![image](https://github.com/user-attachments/assets/42f079a8-a1be-43af-ae55-5d83f2797529)
Gambar 1. Hasil rekomendasi pencarian ayat-ayat Al-Qur'an dengan menggunakan Google Scholar 

Google secara otomatis mencari dan menghitung relevansi dokumen berdasarkan prinsip flexible search. Hail pencarian tidak hanya menampilkan artikel-artikel yang relevan atau tidak relevan saja. Hasil pencarian menampilkan semua artikel dari yang paling relevan hingga yang kurang relevan. Ini adalah contoh implementasi sistem rekomendasi, di mana rekomendasi dokumen atau artikel disesuaikan dengan permintaan pengguna dan tingkat kesamaan dengan dokumen. Mesin pencari Google menggunakan pendekatan *content based filtering*, yang berfokus pada kata kunci yang dimasukkan pada search bar sebagai atribut penting dalam menilai relevansi.

Algoritma pencarian dokumen relevan milik Google yang diterapkan di dalam mesin pencari milik Google atau produk lain dari Google, seperti Google Scholar merupakan algoritma yang kompleks dan paten milik Google. Media Google menampilkan hasil pencarian ayat Qur'an yang terkait bersamaan dengan artikel-artikel yang membicarakan ayat tersebut. Apabila ingin lebih ringkas dan jika ingin mengetahui skor relevansi dari seluruh ayat Al-Qur'an dengan kata kunci yang kita masukkan, masih dibutuhkan program yang bisa merekomendasikan ayat-ayat Al-Qur'an yang relevan. Karena alasan tersebut penulis merasa projek untuk membuat sistem rekomendasi untuk pencarian ayat Al-Qur'an berdasarkan kata kunci masih perlu dikerjakan. Projek sistem temu kembali informasi ini akan dibuat dengan memperhatikan *Relevance Factor* yang ditentukan dengan menggunakan algoritma *Cossine similarity* untuk mengetahui nilai relevansi untuk masing-masing ayat Al-Qur'an yang direkomendasikan.


## Business Understanding

Permasalahan yang diangkat pada proyek ini berasal dari pengalaman penulis saat ingin mencari ayat-ayat Al-Qur'an yang relevan dengan topik tertentu, tetapi menghadapi kesulitan dalam menemukan hasil yang akurat dan cepat hanya dengan menggunakan aplikasi Al-Qur'an yang tersedia. Seperti yang telah dijelaskan pada bagian domain proyek, Google memiliki algoritma kompleks yang memadukan teknik machine learning untuk menghasilkan rekomendasi artikel yang relevan dengan topik yang pengguna ingin cari. Prinsip yang sama dapat diterapkan pada pencarian ayat Al-Qur'an, yaitu dengan memanfaatkan ide "flexible search". Sistem ini memungkinkan pencarian untuk memahami berbagai tipe kueri, maksud pengguna, dan kebutuhan informasi, bahkan jika kueri yang dimasukkan tidak tepat, mengandung kesalahan ejaan, atau tidak sepenuhnya sesuai dengan ayat yang ada di database. Algoritma flexible search tetap mampu memberikan hasil yang relevan, sehingga memudahkan pengguna dalam menemukan ayat Al-Qur'an yang sesuai dengan kata kunci yang diberikan. Implementasi flexible search ini bisa menjadi solusi penting dalam mempermudah studi dan pemahaman Al-Qur'an di era digital.

Selain itu, flexible search memiliki keunggulan dibandingkan dengan boolean search yang lebih tradisional. Pada boolean search, hasil pencarian sangat bergantung pada ketepatan kueri yang dimasukkan, sehingga jika pengguna salah mengetik atau menggunakan kata kunci yang tidak tepat, hasil ayat Al-Qur'an rekomendasi yang ditampilkan bisa saja kurang relevan atau bahkan tidak ada sama sekali. Di sisi lain, flexible search mampu menangani variasi kata kunci dengan lebih dinamis, karena algoritmanya tidak hanya fokus pada kecocokan kata kunci secara literal, tetapi juga pada konteks dan makna kueri. Dengan demikian, flexible search dapat memberikan hasil yang lebih luas dan relevan, meskipun input pengguna tidak sempurna. Hal ini menjadikannya lebih unggul dalam pencarian ayat Al-Qur'an, di mana kompleksitas bahasa dan variasi penulisan sering kali menjadi tantangan tersendiri dalam pencarian berbasis boolean.

Dengan demikian, perbedaan utama antara keduanya adalah dalam pendekatan flexible search, seperti yang dimiliki Google yang mampu memahami maksud pengguna dan memberikan rekomendasi relevan meskipun kueri tidak sempurna, sementara pendekatan tradisional boolean search  hanya membandingkan kata-kunci dalam kueri dengan isi ayat-ayat Al-Qur'an untuk menentukan hasil yang ditampilkan.

Dalam konteks proyek ini, perbedaan pendekatan boolean search dengan sistem rekomendasi modern yang menerapkan machine learning menjadi relevan. Sistem rekomendasi yang dibangun dalam proyek ini menggunakan algoritma *cosine similarity* untuk mengukur relevansi dan melakukan rekomendasi berdasarkan nilai-nilai relevansi antara ayat-ayat Al-Qur'an. Pendekatan ini lebih fleksibel dan mampu mengatasi variasi dalam kueri yang dimasukkan pengguna, seperti kesalahan pengejaan atau variasi kata. Dengan demikian, proyek ini mencoba mengatasi keterbatasan boolean search dengan memanfaatkan teknik machine learning yang lebih modern. Meotde *cosine similarity* ini akan mampu memberikan beberapa rekomendasi ayat-ayat Al-Qur'an beserta dengan memberikan nilai relevansi dengan kueri yang dimiliki pengguna sebagai pertimbangan pengguna apakah akan menerima ayat-ayat Al-Qur'an rekomendasi dari sistem atau tidak.  

### Problem Statements

- Bagaimana mengembangkan sistem temu kembali informasi atau sistem rekomendasi ayat Al-Qur'an yang memiliki nilai relevansi dengan kata kunci yang dimasukkan?
- Bagaimana mengimplementasikan algoritma *cosine similarity* dalam proses perankingan dan rekomendasi ayat Al-Qur'an kepada pengguna?

### Goals

- Mengembangkan sebuah sistem temu kembali informasi dan rekomendasi ayat Al-Qur'an yang menggunakan algoritma *cosine similarity* untuk mengukur nilai relevansi ayat dengan kueri yang diberikan pengguna. Sistem ini akan memanfaatkan model machine learning untuk menghitung kemiripan antara kueri pengguna dengan konten ayat-ayat Al-Qur'an. Tujuannya adalah untuk memberikan pengalaman pencarian yang lebih relevan dan akurat bagi pengguna. Langkah-langkah untuk mewujudkan hal tersebut adalah dengan mengumpulkan data ayat Al-Qur'an, melakukan pemrosesan teks untuk menghasilkan representasi vektor ayat terjemahan, serta menghitung kemiripan antara vektor kueri pengguna dan vektor ayat menggunakan *cosine similarity*.
  
- Mengimplementasikan algoritma *cosine similarity* dalam proses perankingan dan rekomendasi ayat Al-Qur'an kepada pengguna. Dalam hal ini, algoritma *cosine similarity* akan digunakan untuk mengukur sejauh mana ayat-ayat dalam Al-Qur'an memiliki relevansi dengan topik atau kata kunci yang diberikan oleh pengguna. Tujuan utama adalah menyajikan rekomendasi ayat-ayat Al-Qur'an yang paling sesuai dengan kebutuhan pengguna, sehingga memudahkan proses pencarian informasi dalam kitab Al-Qur'an yang lebih efektif.


## Data Understanding

Dataset yang penulis gunakan pada projek ini meliputi keseluruhan surat dan ayat di dalam Al-Qur'an yang sudah diterjemahkan ke Bahasa Indonesia, di mana di dalam file terdapat beberapa informasi atribut yang dapat digunakan untuk melakukan *information retrieval*. *Dataset* berisi keterangan mengenai nomor surat, ayat, dan isi terjemahannya.

Tautan ke dataset Al-Qur'an terjemahan Bahasa Indonesia : https://www.kaggle.com/datasets/zusmani/the-holy-quran/data?select=Indonesian.csv

### Variabel-variabel pada dataset Al-Qur'an terjemahan Bahasa Indonesia adalah sebagai berikut:
- Surat : atribut dengan tipe data integer yang menunjukkan urutan surat dalam Al-Qur'an.
- Ayat : atribut dengan tipe data integer yang menunjukkan nomor ayat yang berada di dalam surat Al-Qur'an tertentu yang ditunjukkan oleh atribut Surat.
- Terjemah : Atribut dengan tipe data string yang mencantumkan isi terjemahan Al-Qur'an secara keseluruhan.

Untuk memahami atribut-atribut yang ada di dalam dataset tersebut dilakukan beberapa langkah untuk memahami isi dan tipe atribut tersebut. Pertama, dengan menggunakan fungsi bawaan dari python yaitu .info() penulis bisa mendapatkan bahwa dalam dataset tersebut tidak terdapat data yang kosong dan bisa mengetahui tipe data dari masing-masing atribut yang ada pada dataset. 

Tabel 1. keluaran dari *built-in function* bahasa pemrograman Python pada dataset Al-Qur'an terjemahan Bahasa Indonesia

| Column | Non-Null Count | Dtype |
|:----------------:|:---------------:|:---------------:|
| Surat     | 6234 non-null  | int64     |
| Ayat       | 6234 non-null | int64    |
| terjemah       | 6234 non-null | object     |


Hasil dari eksplorasi data tersebut menunjukkan bahwa ada 6234 data dari atribut surat, ayat, dan terjeman dari keseluruhan 6234 data yang ada di dataset, baik yang unik maupun berulang. Tahap eksplorasi data juga dilanjutkan dengan memeriksa apakah didalam dataset terdapat data yang memiliki atribut dengan nilai kosong atau *null* dengan memanfaatkan fungsi Python ```isnull()``` dan ```sum()``` untuk mengetahui jumlah data yang tidak memiliki nilai. Setelah memeriksa nilai kosong dalam dataset, didapatkan data yang nilainya kosong tidak ditemukan, karena jumlah nilai kosong pada dataset berjumlah nol.

Eksplorasi data yang terakhir adalah mengecek apakah ada data di dalam dataset yang serupa dengan data yang lain atau disebut duplikat. Setelah mengeksplor dataset untuk menemukan data duplikat dengan menggunakan fungsi ```duplicated()``` dan menjumlahkan data duplikat tersebut dengan menggunakkan fungsi ```sum``` didapatkan jumlah data duplikat adalah nol.

## Data Preparation-

Di dalam projek ini, proses *data preparation* yang dilakukan kebanyakan dilakukan di dalam hal menganalisis data dan memanipulasi data. Pertama-tama dataset di inputkan ke dalam projek dan data tersebut disajikan ke dalam bentuk *dataframe*. *Dataset* yang sudah dimasukkan ke dalam objek *dataframe* akan diakses dan datanya diambil dengan menggunakan fungsi yang ada pada python yang dirujuk dengan metode *integer-based indexing*.

- 1. Melakukan *mapping* semua atribut yang ada di dataset ke dalam variabelnya masing-masing

Untuk sistem rekomendasi dengan menggunakan metode *content based filtering* semua atribut yang ada di dalam dataset berperan penting untuk menentukan hasil perangkingan rekomendasi. Tahapan selanjutnya dalam pembangunan sistem pada proses *modeling* juga diminta untuk memisahkan atribut tertentu saja yang diproses, sehingga tahapan memecah dataset yang sudah diinputkan menjadi bentuk *dataframe* esensial untuk dilakukan. 
 
- 2. Mengubah tipe data variabel masing-masing atribut dari numpy.ndarray menjadi list
 
Untuk mempersiapkan tahap *modeling* yang akan dilakukan setelah tahap *data preparation* ini, perlu dilakukan konversi tipe data untuk masing-masing variabel atribut dataset. Konversi tipe data ini diperlukan karena tahap *modeling* nantinya akan menerapkan algoritma *cosine similarity* dengan memanfaatkan *library* yang dimiliki oleh scikit-learn yaitu TfidfVectorizer dan cosine_similarity. Pada *library* tersebut menerima input parameter yang akan mengeluarkan hasil eror jika argumen yang dimasukkan memiliki tipe data numpy.ndarray. Maka dari itu penulis akan merubah tipe data masing-masing variabel atribut menjadi tipe *list*

- 3. Mempersiapkan queri dan ayat-ayat Al-Qur'an yang akan digunakan untuk membuat sistem rekomendasi pada tahap *modeling*.
 
Tahap *modeling* yang akan dilakukan setelah tahap *data preparation* ini akan membutuhkan dua elemen supaya fungsinya dapat bekerja. Kedua elemen tersebut adalah queri yang diinputkan pengguna dan ayat-ayat Al-Qur'an yang merupakan dokumen yang mengandung kata kunci untuk dirujuk oleh queri pengguna. Queri dalam projek sistem pencarian ayat-ayat Al-Qur'an relevan kali ini adalah suatu kata kunci (*keyword*) yang akan digunakan model untuk merekomendasikan ayat-ayat Al-Qur'an relevan yang dibutuhkan user pada tahap *modeling*. Input dari pengguna akan dirubah menjadi bentuk string agar bisa di vektorisasi pada tahap *modeling*. Semua isi Al-Qur'an terjemahan juga perlu dibuat menjadi daftar *string* seperti yang telah dilakukan pada tahap dua data preparation sebelumnya untuk dapat dilakukan vektorisasi dalam tahap *modeling*.


## Modeling


- 1. Melakukan vektorisasi dengan menggunakan fungsi TF-IDF Vectorizer

Dalam tahap pembuatan model *machine learning* untuk proyek sistem temu kembali rekomendasi ayat Al-Qur'an, metode yang digunakan adalah *cosine similarity*. Metode ini mengukur kesamaan antara ayat Al-Qur'an dengan kuerinya berdasarkan kata kunci dalam bentuk vektor. Kelebihan metode *cosine similarity* yang dimanfaatkan pada projek ini diantaranya adalah kemampuan untuk mengukur kesamaan semantik diantara ayat-ayat Al-Qur'an. Kedua, ayat-ayat Al-Qur'an dapat digunakan untuk dirubah menjadi representasi vector numeric dengan menggunakan teknik TF-IDF yang dapat dilakukan dengan menggunakan *library* yang sama seperti cosine_similarity dimiliki juga oleh scikit-learn. Ketiga, *cosine similarity* merupakan metode yang penulis rasa paling tepat untuk diterapkan pada projek ini, mengingat projek ini mengambil pendekatan *content-based recommendation*. Setiap kata yang ada di setiap ayat-ayat Al-Qur'an dijadikan faktor utama untuk menghasilkan rekomendasi ayat-ayat Al-Qur'an yang paling relevan sesuai dengan keinginan pengguna. Terakhir, hasil keluaran atau hasil rekomendasi ayat-ayat Al-Qur'an yang dihasilkan oleh metode ini dapat direpresentasikan secara numerik dengan menggunakan nilai *similarity score*. Ayat-ayat Al-Qur'an yang paling direkomendasikan ke pengguna akan ditampilkan paling atas oleh sistem dengan tambahan keterangan nilai *similarity score* yang dapat digunakan untuk mempertimbangkan relevansi ayat-ayat Al-Qur'an rekomendasi dengan kueri yang dimasukkan oleh pengguna. Semakin tinggi nilai *similarity score*, maka pengguna dapat semakin yakin bahwa hasil rekomoendasi ayat-ayat Al-Qur'an yang sistem berikan valid. 



- 2. Menghitung nilai *cosine similarity* dengan memanfaatkan fungsi ```cosine_similarity``` yang dimiliki oleh scikit-learn

Pada tahap *modeling* yang terjadi di projek ini terdapat beberapa alur utama untuk mendapatkan rekomendasi ayat-ayat Al-Qur'an yang paling relevan dengan input kueri pengguna. Langkah pertama, pada tahap *data preparation* pengguna harus memasukkan input berupa kata kunci atau topik pembahasan dalam Al-Qur'an yang ingin dicari. Input dari pengguna akan dirubah menjadi bentuk string yang nantinya model akan mencari kecocokan dengan ayat-ayat Al-Qur'an yang ada di *dataset*. Untuk dapat mencocokan kueri pengguna dengan ayat-ayat Al-Qur'an di dalam dataset, pertama penulis mendefinisikan *object vectorizer* untuk digunakan sebagai *TF-IDF vectorizer*. Objek tersebut digunakan untuk melakukan vektorisasi sehingga setiap kata ayat-ayat Al-Qur'an terjemahan yang berupa kata-kata menjadi bentuk vektor numerik sehingga dapat dilakukan komputasi. Selanjutnya dengan menggunakan *object vectorizer* yang sama, kueri yang diinputkan oleh pengguna juga perlu dilakukan vektorisasi sehingga kueri pengguna yang berupa string juga menjadi bentuk vektor numerik. Langkah vektorisasi tersebut menggunakan ```TfidfVectorizer()``` yang berasal dari *library* scikit-learn. Setelah itu dengan mengunakan ```cosine_similarity``` milik *library* scikit-learn, dilakukan perhitungan nilai *cosine similarity* antara vektor kueri dengan masing-masing vektor dokumen. Rumus *cosine similarity* yang diimplementasikan pada  fungsi ```cosine_similarity``` milik *library* scikit-learn tertera pada persamaan 1.

Persamaan 1. Rumus *cosine similarity*

Cosine(A,B) = $similarity = \cos (\theta) = \frac{A \cdot B}{||A|| \cdot ||B||} = \frac{\sum_{i=1}^{n} A_i B_i}{\sqrt{\sum_{i=1}^{n} A_i^2} \cdot \sqrt{\sum_{i=1}^{n} B_i^2}}$

Keterangan : 

${A}$: kueri dari pengguna yang sudah dalam bentuk vektor setelah melakukan vektorisasi

${B}$ : Setiap ayat-ayat Al-Qur'an yang ada di dataset yang telah berbentuk vektor setelah vektorisasi 

${n}$ : Jumlah seluruh ayat Al-Qur'an


- 3. Menampilkan hasil rekomendasi ayat-ayat Al-Qur'an beserta dengan nilai kesamaannya dengan queri pengguna

Setelah ayat-ayat Al-Qur'an telah memiliki nilai *cosine similarity*, ayat-ayat Al-Qur'an yang memiliki nilai  *cosine similarity* bukan nol akan ditampilkan ke pengguna dari ayat-ayat Al-Qur'an yang memiliki nilai  *cosine similarity* tertinggi ke yang terendah. Ayat-ayat Al-Qur'an yang nilai  *cosine similarity*-nya sama dengan nol tidak dimunculkan ke pengguna. Ayat-ayat Al-Qur'an yang direkomendasikan sistem akan berupa ayat-ayat Al-Qur'an terjemahan paling relevan diikuti dengan atribut lain dari masing-masing ayat Al-Qur'an tersebut, seperti nomor surat dan nomor ayat.    


Tabel 2. Rekomendasi 7 ayat-ayat Al-Qur'an paling relevan keluaran dari sistem

| index | Urutan Surat | Urutan Ayat | Terjemahan Indonesia | nilai kesamaan |
| --- | --- | --- | --- | --- |
| 280 | 2 | 275 | Orang-orang yang makan (mengambil) riba tidak dapat berdiri melainkan seperti berdirinya orang yang kemasukan setan lantaran (tekanan) penyakit gila. Keadaan mereka yang demikian itu adalah disebabkan mereka berkata (berpendapat) sesungguhnya jual beli itu sama dengan riba padahal Allah telah menghalalkan jual beli dan mengharamkan riba. Orang-orang yang telah sampai kepadanya larangan dari Tuhannya lalu terus berhenti (dari mengambil riba) maka baginya apa yang telah diambilnya dahulu (sebelum datang larangan) dan urusannya (terserah) kepada Allah. Orang yang mengulangi (mengambil riba) maka orang itu adalah penghuni-penghuni neraka mereka kekal di dalamnya. | 0.5701770468685109 |
| 284 | 2 | 279 | Maka jika kamu tidak mengerjakan (meninggalkan sisa riba) maka ketahuilah bahwa Allah dan Rasul-Nya akan memerangimu. Dan jika kamu bertobat (dari pengambilan riba) maka bagimu pokok hartamu kamu tidak menganiaya dan tidak (pula) dianiaya. | 0.46703283060831496 |
| 3445 | 30 | 39 | Dan sesuatu riba (tambahan) yang kamu berikan agar dia bertambah pada harta manusia maka riba itu tidak menambah pada sisi Allah. Dan apa yang kamu berikan berupa zakat yang kamu maksudkan untuk mencapai keridaan Allah maka (yang berbuat demikian) itulah orang-orang yang melipat gandakan (pahalanya). | 0.42593017411211087 |
| 421 | 3 | 130 | Hai orang-orang yang beriman janganlah kamu memakan riba dengan berlipat ganda dan bertakwalah kamu kepada Allah supaya kamu mendapat keberuntungan. | 0.36168243681967566 |
| 283 | 2 | 278 | Hai orang-orang yang beriman bertakwalah kepada Allah dan tinggalkan sisa riba (yang belum dipungut) jika kamu orang-orang yang beriman. | 0.35194184741023793 |
| 281 | 2 | 276 | Allah memusnahkan riba dan menyuburkan sedekah. Dan Allah tidak menyukai setiap orang yang tetap dalam kekafiran dan selalu berbuat dosa. | 0.3407315037752999 |
| 651 | 4 | 161 | dan disebabkan mereka memakan riba padahal sesungguhnya mereka telah dilarang daripadanya dan karena mereka memakan harta orang dengan jalan yang batil. Kami telah menyediakan untuk orang-orang yang kafir di antara mereka itu siksa yang pedih. | 0.28031661359393045 |

Tabel 2 diatas menampilkan tujuh ayat-ayat Al-Qur'an terjemahan Indonesua paling relevan dari keselueuhan ayat Al-Qur'an yang ada pada dataset. Tujuh ayat-ayat Al-Qur'an tersebut menurut sistem yang paling relevan jika input kueri dari pengguna yaitu "Riba". 


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
