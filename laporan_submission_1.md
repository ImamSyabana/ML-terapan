# Laporan Proyek Model Pembelajaran Mesin untuk Memprediksi Harga Rumah  - Muhammad Imam Ariq Sya'bana

## Domain Proyek

*Bubble economy* di Jepang merupakan periode pertumbuhan ekonomi yang sangat cepat dan spektakuler, di mana harga aset seperti tanah dan properti mengalami kenaikan yang tajam sebelum akhirnya mengalami kejatuhan yang dramatis. Oleh karena itu, penting bagi para pembeli rumah dan para pemangku kepentingan di pasar perumahan untuk dapat memahami dan mengantisipasi kemungkinan terjadinya lonjakan harga yang signifikan.

Projek ini bertujuan untuk membangun model *machine learning* yang dapat memprediksi harga rumah di masa depan dan mengidentifikasi kemungkinan adanya lonjakan harga rumah yang tinggi seperti yang terjadi pada *bubble economy* di Jepang pada tahun 1980-an.

*Bubble economy* adalah kenaikan harga asset yang dampaknya cukup luas untuk suatu perekonomian negara. Karena kasus di Jepang pada tahun 1984 properti adalah aset yang banyak dimiliki banyak orang maka jika harga nya naik drastis dan selanjutnya turun drastis dapat memengaruhi ekonomi sosial negara. *Buble economy* yang membuat harga aset meningkat bukan didasarkan pada nilai intrinsiknya, melainkan pada spekulasi masyarakat yang ingin berinvestasi. 

Saat gelembung tumbuh harga-harga aset sudah pasti naik drastis sehingga lebih banyak investor tertarik ke pasar, yang menyebabkan kenaikan harga lebih lanjut dan menyebabkan keuntungan bagi investor. Tetapi untuk masyarakat yang benar-benar membutuhkan rumah untuk kebutuhan bukan untuk investasi akan merasa sangat keberatan karena harga-harga rumah sudah sangat tinggi. Maka dari itu akan terjadi penurunan anjlok harga aset untuk membuat harga rumah normal kembali yang disebabkan oleh peraturan pemerintah, sehingga menghasilkan kerugian pada sisi investor karena harga jual yang turun sangat jauh dibawah saat mereka membeli harga aset tersebut saat sebelum anjlok, ditambah banyak investor yang berinvestasi dengan menggunakan dana pinjaman dari bank dan karena harga aset yang dibeli turun drastis maka mereka tidak dapat melunasi pinjamannya menyebabkan banyak bank yang mengalami kebangkrutan sehingga berimplikasi pada penurunan pertumbuhan ekonomi yang signifikan.


## Business Understanding

*Bubble Economy* dapat menyebabkan peningkatan harga rumah yang signifikan, sehingga menarik banyak investor ke pasar perumahan dan menciptakan keuntungan besar bagi mereka. Namun, di sisi lain, masyarakat yang benar-benar membutuhkan rumah untuk kebutuhan bukan untuk tujuan investasi akan merasa kesulitan dan terbebani dengan harga rumah yang sangat tinggi. *Bubble Economy* yang terjadi di Jepang dapat dijadikan contoh pengalaman buruk untuk negara-negara lain dengan cara mempelajari apa yang terjadi dimasa lalu. Pemerintah dan para pemangku kepentingan dapat mencari tahu cara untuk mencegah lonjakan harga terjadi kembali dengan menormalkan harga sebelum harga rumah memasuki periode *bubble economy*. Sebab jika harga-harga aset properti sudah muncul indikasi-indikasi akan melonjak, jika tidak dicegah masyarakat akan mengalami hal yang serupa seperti yang dialami masyarakat Jepang pada tahun 1980-an. Maka dari itu dengan membuat model pembelajaran mesin yang dapat memprediksi data *time series* tentang harga rumah dengan hasil prediksi yang dapat diandalkan, pemerintah dan para pemangku kepentingan lainnya dapat memprediksi apakah akan ada lonjakan harga dimasa depan. Jika harga aset rumah dan bangunan dapat diprediksi, dengan begitu pemerintah dan para pemangku kepentingan dapat membuat langkat preventif dengan mengeluarkan peraturan baik pajak dan lain-lain untuk menekan masyarakat yang spekulatif ingini memiliki aset sebanyak-banyaknya untuk investasi.  

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
Dataset yang penulis gunakan pada projek ini berisi informasi historis tentang harga rumah, termasuk fitur-fitur seperti kode pos, jumlah kamar tidur, harga, tahun dijual dan tipe properti. Data ini akan digunakan untuk melatih model machine learning untuk memprediksi harga rumah di masa depan dan menganalisis perubahan tren harga untuk mengidentifikasi potensi lonjakan harga.

House Property Sales Time Series (https://www.kaggle.com/datasets/htagholdings/property-sales?select=raw_sales.csv).

### Variabel-variabel pada House Property Sales Time Series dataset adalah sebagai berikut:
- datesold : merupakan tipe data datetime yang menunjukkan kapan data rumah tersebut dijual.
- postcode : berupa empat digit kode pos dari distrik tempat properti tersebut dijual.
- price : Harga jual properti yang telah berhasil terjual (Mata uang dari harga rumah di atribut *price* tidak dijelaskan dalam dataset).
- propertyType : Tipe properti i.e. house atau unit
- bedrooms : Jumlah kamar tidur


Untuk memahami atribut-atribut yang ada di dalam dataset tersebut dilakukan beberapa langkah untuk memahami isi dan tipe atribut tersebut. Pertama, dengan menggunakan fungsi bawaan dari python yaitu .info() kita bisa mendapatkan bahwa dalam dataset tersebut tidak terdapat data yang kosong dan bisa mengetahui tipe data dari masing-masing atribut yang ada pada dataset. 

Tabel 1. keluaran dari *built-in function* bahasa pemrograman Python pada dataset *house price*

| Column | Non-Null Count | Dtype |
|:----------------:|:---------------:|:---------------:|
| postcode     | 29580 non-null    | int64     |
| price     | 29580 non-null    | int64     |
| propertyType       | 29580 non-null   | object    |
| bedrooms       | 29580 non-null   | int64     |



Kedua, dengan menggunakan .describe() kita dapat mengetahui statistik dasar dari data seperti percentile, mean, standar deviasi, jumlah data, min, dan max. Hasil fungsi ini ditampilkan pada tabel 2 seperti berikut.

Tabel 2. statistik dataset *house price* hasil dari fungsi *.describe()*

|  | postcode | price | bedrooms |
|:----------------:|:---------------:|:---------------:|:---------------:|
| count     | 29580.000000    | 29580.000000     | 29580.000000|
| mean     | 2730.249730    | 6.097363e+05     |3.250169|
| std       | 146.717292   | 2.817079e+05    |0.951275|
| min       | 2600.000000   | 5.650000e+04    |0.000000|
| 25%       | 2607.000000  | 4.400000e+05     |3.000000|
| 50%       | 2615.000000   | 5.500000e+05     |3.000000|
| 75%       | 2905.000000   | 7.050000e+05     |4.000000|
| max       | 2914.000000   | 8.000000e+06     |5.000000|

Pada notebooks dilakukan visualisasi untuk membandingkan rerata data keseluruhan harga rumah yang bertipe *house* dan yang bertipe *unit*. Didapatkan bahwa rerata harga rumah yang bertipe *house* lebih tinggi daripada rerata harga rumah yang bertipe *unit*.

![image](https://github.com/Zelkova46/ML-terapan/assets/70127988/e5edcf5c-d69b-4a54-872a-ef0784a36018)Gambar 1. rerata harga terhadap *propertyType*

Untuk atirbut propertyType dilakukan visualisasi jumlah data rumah yang bertipe house dan unit. Dari visualisasi yang dilakukan pada Gambar 1, didapatkan bahwa jumlah data yang bertipe house dan unit tidak seimbang, maka dari itu pada tahap selanjutnya atribut property type tidak dimasukkan untuk perhitungan karena dianggap tidak akan relevan karena distribusi data yang tidak seimbang.

Fitur *propertyType* menunjukkan bahwa tipe *unit* memiliki harga rerata yang lebih rendah dari pada tipe *house* yang memiliki harga yang lebih tinggi. Perbedaan rerata harga unit hanya tertinggal sekitar kurang dari 30% dari harga rerate house. Hal tersebut juga mungkin bisa disebabkan oleh lokasi dari tipe unit yang rata-rata memiliki lokasi yang sangat berbeda dibandingkan dengan tipe house. Hal ini berarti bahwa fitur *propertyType* memiliki pengaruh yang rendah terhadap harga.

Tabel 3. Jumlah sebaran data rumah bertipe *house* dan *unit* 

|  | jumlah sampel | presentase |
|:----------------:|:---------------:|:---------------:|
| house     | 24552            | 83.0     |
| unit    |5028            | 17.0     |

Ditambah jika kita melihat sebaran data untuk tipe *unit* dan tipe *house* yang ada pada tabel 2, didapat bahwa jumlah data rumah dengan tipe *unit* hanya 17% dari keseluruhan data, sedangkan rumah dengan tipe *house* memiliki 83%. Ketidakseimbangan distribusi data ini membuat atribut *propertyType* tidak dapat digunakan untuk menebak prediksi harga rumah karena dianggap tidak akan relevan karena distribusi data yang tidak seimbang. Maka dari itu selanjutnya atribut tipe properti tidak akan digunakan.

![image](https://github.com/Zelkova46/ML-terapan/assets/70127988/f575620c-ffa3-4372-8010-529b46b5073a) 

Gambar 2. Visualisasi histogram jumlah sebaran data rumah bertipe *house* dan *unit* 

Pada atribut fitur price dilakukan visualisasi data seperti tampak di gambar 3, visualisasi harga yang dilakukan adalah dengan memanfaatkan histogram untuk mengetahui jumlah data pada masing-masing rentang harga rumah yang ada didataset.

![image](https://github.com/Zelkova46/ML-terapan/assets/70127988/61b674c8-0fb6-4e51-8d41-765b7a1da51b)

Gambar 3. Visualisasi histogram sebaran harga rumah yang ada di dalam *dataset*

Pada atribut fitur bedrooms dilakukan visualisasi data, visualisasi harga yang dilakukan adalah dengan memanfaatkan histogram kembali untuk mengetahui sebaran nilai jumlah kamar tidur setiap data rumah yang ada didataset. Dengan visualisasi ini kita dapat mengetahui rumah dengan jumlah kamar tidur berapa yang mendominasi dataset.

![image](https://github.com/Zelkova46/ML-terapan/assets/70127988/02ac47f6-b54b-49f1-8fb3-f7f5f9104af8)

Gambar 4. Visualisasi histogram sebaran jumlah kamar tidur masing-masing data rumah pada di *dataset*

Selanjutnya untuk mengetahui hubungan masing-masing fitur terhadap satu sama lain dihitung korelasinya. Menghasilkan bahwa fitur price memiliki korelasi positif terhadap fitur jumlah bedrooms. Karena terdapat sejumlah data yang tidak konsisten, dalam arti ada data yang jumlah bedrooms yang tinggi tetapi memiliki price yang tinggi dan ada juga rendah. Dengan begitu nilai korelasi tidak mendekati positif satu, hanya bernilai 0.48

![image](https://github.com/Zelkova46/ML-terapan/assets/70127988/6dc000d1-099f-4837-96ed-39ad9b9e16dc)

Gambar 5. Grafik korelasi antara fitur *bedroom*, *price*, dan *postcode*.

Hasil nilai korelasi dan visualisasi yang ada pada gambar 5 di atas didapatkan dari pemetaan nilai dari masing-masing fitur yang berlainan didalam scatterplot dibawah ini. Dapat dilihat kenapa korelasi antara fitur *bedrooms* dan *price* memiliki nilai korelasi postif dan tidak mendekati satu. Nilai korelasi 0.48 didapat karena peningkatan harga diiringi dengan peningkatan jumlah *bedroom*. Walaupun terdapat pula jumlah *bedrooms* yang tinggi tetapi memiliki *price* yang paling rendah, tetapi pola yang bisa dipastikan adalah tidak mungkin jumlah *bedrooms* yang rendah memiliki harga yang tinggi.

![image](https://github.com/Zelkova46/ML-terapan/assets/70127988/7f9f0bbe-dbdd-4c75-9fb7-25c0ed399810)

Gambar 6. Visualisasi grafik untuk mengamati hubungan antara fitur numerik.

## Data Preparation

- 1. Membuat data iregular menjadi regular
     
Data time series yang didapat dari kaggle ternyata irregular, artinya selang antar timestamps tidak selalu sama. Hal ini membuat prediktif pada tahap pemodelan akan menjadi sulit diprediksi waktu dan valuenya. Selanjutnya adalah usaha untuk membuat data menjadi lebih menjadi regular dengan cara menghilangkan beberapa data yang tidak sesuai pola.

Metode dalam membuat data yang tidak regular menjadi regular adalah dengan menghitung nilai mean pada data-data yang terletak dalam rentang waktu yang ditentukan. Dibawah ini selang waktu yang ditentukan adalah mingguan, jadi data-data yang berada pada minggu yang sama akan diratakan dan menjadi satu data baru yang merepresentasikan harga rumah rata-rata yang ada dihari-hari pada minggu tersebut. Ini membuat data yang sebelumnya perhari yang tidak memiliki pola, sekarang menjadi perminggu dan sudah teratur tanpa menghilangkan informasi data secara keseluruhan karena data yang perhari memiliki peran untuk menentukan nilai rerata perminggu.

Algoritma yang digunakan untuk melakukan hal tersebut adalah dengan memanfaatkan *method* ```resample()``` yang ada di dalam *library* pandas. *Method* ```resample()``` merupakan *method* di dalam *library* pandas yang digunakan untuk mengubah interval frekuensi data berjenis *time-series*, maksudnya adalah dengan menggunakan *method* ini kita dapat merubah *dataset* dari frequensi awal ke frequensi tertentu. Dalam kasus kali ini penggunaannya digunakan untuk merubah *dataset* yang memiliki frequensi yang tidak menentu atau iregular menjadi *dataset* yang frequensinya mingguan.

Metode ini bekerja dengan cara menyamakan frequensi yang ada pada dataset dengan cara membuat interval indeks yang berupa *timestamps* atau *dates* memiliki jarak yang sama. *Method* ini menerima satu argumen bertipe *string* yang merepresentasikan periode waktu seperti dalam projek kali ini 'W' merepresentasikan minggu, ada pula 'D' yang merepresentasikan hari, dan 'M' yang merepresentasikan bulan. Kemudian,  ```resample()``` juga dapat di tambah dengan fungsi lain untuk dapat meringkas data ke frequensi yang diinginkan. Beberapa fungsi agregasi yang sering dipakai adalah ```mean()```, ```sum()```, ```max()```, ```min()```, ```count()```, dan lain-lain. Fungsi-fungsi ini disambung dengan *method* ```resample()```. Dengan menggunakan fungsi-fungsi tersebut kita dapat membuat data *timeseries* yang iregular menjadi regular dengan meringkas data-data yang ada pada interval tertentu dengan mengambil rerata, jumlah, nilai maksimum atau minimum, dan sebagainya.

```
import pandas as pd
house_price_df = house_price_df.resample('w').mean()
house_price_df.head(20)

house_price_df
```

Setelah membuat data menjadi regular, jumlah data akan berkurang dari sebelumnya dan masing-masing satu data merepresentasikan harga pada tiap-tiap minggunya.

- 2. Memotong-motong data timeseries menjadi ke bentuk *window* sebagai independent variable dan *horizon* sebagai dependent variable
 
Untuk dapat membuat data timeseries dapat dimasukkan ke dalam machine learning supervised learning, diperlikan metode windowing. *window* dari jangka waktu dimasa lalu digunakan untuk menebak masa depan (*horizon*).

Pada program telah didefinisikan nilai untuk menentukan interval *window* dan *horizon* atau seberapa jauh prediksi ke masa depan. 

```
HORIZON = 1 # menebak price rata-rata pada 1 minggu kedepannya
WINDOW_SIZE = 8 #menebak price 2 bulan sebelumnya
```

Untuk feature berisi oleh *window* harga pada beberapa waktu kebelakang sesuai dengan nilai WINDOW_SIZE yang didefinisikan ditambah dengan jumlah bedrooms karena ini merupakan multivariate time series. Lalu, untuk label diisi oleh keterangan price untuk beberapa waktu kedepan sesuai dengan nilai HORIZON yang didefinisikan sebelumnya.

Untuk melakukan tersebut di dalam Python kode berikut ini berperan dalam membuat *dataset* menjadi format *window* dan *horizon*. *Window* berisi dengan sejumlah data yang telah terdefinisi serta berurutan. Kemudian, *horizon* adalah rangkaian data terurut yang ada setelah *window*

Pertama, kita menentukan iterasi sebanyak dengan ukuran dari WINDOW_SIZE yang sudah ditentukan. Kemudian pada bagian ```house_prices_windowed[f"Price+{i+1}"]``` akan membuat kolom-kolom baru di *dataframe* ```house_price_windowed```. Kolom-kolom tersebut akan menjadi Price+1, Price+2, dan seterusnya sampai Price+WINDOW_SIZE. Selanjutnya, pada bagian ```house_prices_windowed["price"].shift(periods=i+1)``` melakukan operasi untuk menggeser *window* sebanyak satu data, dapat dilihat dari parameter ```periods``` yang diisi dengan nilai i+1. *Methods* ```shift```digunakan untuk menggeser nilai-nilai yang ada di kolom ke arah data-data selanjutnya sebanyak satu langkah dalam kasus ini. Setelah melakukan semua hal tersebut, hasil lima *window* pertama tertera pada tabel 4.

Tabel 4. Hasil pemetaan dataset menjadi lima *WINDOW* pertama untuk digunakan pada tahap *modelling*.

| datesold   | bedrooms | Price+1     | Price+2    | Price+3     | Price+4     | Price+5  | Price+6   | Price+7  | Price+8  |
|:----------:|:--------:|:-----------:|:----------:|:-----------:|:-----------:|:--------:|:---------:|:--------:|:--------:|
| 2007-07-01 | 3.333333 | 339500.000  | 1.530e+06  | 3.990e+05   | 4.650e+05   | 310000.0  | 354000.0  | 290000.0 | 525000.0 |
| 2007-07-08 | 3.333333 | 520333.344  | 3.395e+05  | 1.530e+06   | 3.990e+05   | 465000.0  | 310000.0  | 354000.0 | 290000.0 |
| 2007-07-15 | 3.000000 | 533000.000  | 5.203e+05  | 3.395e+05   | 1.530e+06   | 399000.0  | 465000.0  | 310000.0 | 354000.0 |
| 2007-07-22 | 3.142857 | 603750.000  | 5.330e+05  | 5.203e+05   | 3.395e+05   | 1530000.0 | 399000.0  | 465000.0 | 310000.0 |
| 2007-08-05 | 3.333333 | 687714.313  | 6.037e+05  | 5.330e+05   | 5.203e+05   | 339500.0  | 1530000.0 | 399000.0 | 465000.0 |

Dan hasil dari Horizon untuk lima *horizon* pertama yang bernilai satu tampak pada tabel 5.

Tabel 5. Hasil pemetaan dataset menjadi lima *HORIZON* pertama untuk digunakan pada tahap *modelling*.

|   datesold   |     price     |
|:------------:|:-------------:|
| 2007-07-01   | 520333.34375  |
| 2007-07-08   | 533000.00000  |
| 2007-07-15   | 603750.00000  |
| 2007-07-22   | 687714.31250  |
| 2007-08-05   | 488833.34375  |

## Modeling

Metode yang penulis pilih untuk menentukan metode machine learning terbaik untuk kasus menebak prediksi harga rumah dimasa depan yang melampaui data yang ada pada datasets awal adalah dengan membandingkan dua model machine learning yaitu CNN dan RNN. Arsitektur dari kedua model tersebut dibuat menjadi indentik. Dua model tersebut sama-sama memiliki tiga hidden layer, dimana layer pertama memiliki 64 neuron unit, layer kedua memiliki 128 neuron unit, layer ketiga memiliki 256 neuron unit, input layer sebesar dengan nilai *window* yang didefinisikan dan output layer berupa fully connected layer yang berdimensi sebesar nilai HORIZON yang didefinisikan sebelumnya. Dua hal yang membedakan kedua model tersebut adalah untuk model yang menggunakan CNN pada hiden layer digunakan Convolution layer untuk dimaensi satu yaitu Conv1D, sedangkan pada model RNN pada hidden layer memanfaatkan LSTM. Selanjutnya karna model konvolusi membutuhkan kernel size sedangkan model RNN tidak, maka hanya model konvolusi yang memiliki parameter kernel_size yang nilainya 5.

Setelah melakukan training untuk kedua model, didapatkan bahwa model konvolusi yang menggunakan Conv1D berhasil memprediksi harga rumah yang mendekati ke harga aslinya lebih baik dari pada model Recurrent Neural Network yang menggunakan LSTM.

Karena *metrics* yang digunakan untuk mengukur performa model masalah time series kali ini adalah MAE maka hasil training yang terbaik dari kedua model tersebut dapat ditentukan dengan menggunakan parameter loss dan validation loss. Parameter *Loss* adalah parameter yang mengukur sebaik apa model dapat memprediksi target nilai harga rumah sebenarnya pada *training data*. *Validation loss* adalah parameter yang mengukur sebaik mana model dapat memprediksi target nilai harga rumah sebenarnya pada *validation data* yang mana serangkaian data yang terpisah dari *training data*.

Gambar 7 dibawah ini adalah grafik yang menggambarkan *loss* dan *validation loss* untuk performa dari model yang menggunakan layer *convolutional* atau *Conv1D layer*. Pada grafik terlihat nilai *loss* dan *validation loss* mampu konvergen lebih cepat daripada model yang menggunakan layer RNN, dapat dilihat pada tahap awal *epochs* sekitar epoch ke-15 nilai *loss* dan *validation loss* sudah mencapai nilai terkecilnya atau sudah konvergen. 

![image](https://github.com/Zelkova46/ML-terapan/assets/70127988/29dcc936-ce1d-4104-a85f-acc3de87002c) Gambar 7. Visualisasi hasil training model konvolusi yang memberi informasi parameter evaluasi *loss* dan *validation loss* pada masing-masing *epoch*

Gambar dibawah ini adalah grafik yang menggambarkan *loss* dan *validation loss* untuk performa dari model yang dilatih dengan menggunakan layer jenis RNN yaitu LSTM. Pada grafik terlihat nilai *loss* dan *validation loss* konvergen lebih lambat daripada model yang menggunakan layer konvolusi, dapat dilihat baru pada sekitar *epoch* ke-46 nilai *loss* dan *validation loss* sudah mencapai nilai terkecilnya atau konvergen. 

![image](https://github.com/Zelkova46/ML-terapan/assets/70127988/111bec3a-3c40-402c-af52-5208f8639c20) Gambar 8. Visualisasi hasil training model RNN yang memberi informasi parameter evaluasi *loss* dan *validation loss* pada masing-masing *epoch*

Dari kedua grafik diatas dapat ditarik kesimpulan bahwa model konvolusi memiliki kedua nilai evaluasi model MSE dan MAE jauh lebih kecil daripada model RNN sehingga untuk memprediksi harga yang ada dimasa depan kita akan menggunakan model konvolusi. Jika melihat dari grafik saja kurang dapat dilihat mana yang nilai MAE-nya lebih kecil karena selisih yang mendekati, maka dari itu kita akan menarik prediksi nilai MAE dan MSE dari pengujian dan validasi terhadap data validasi. Didapatkan bahwa sesuai dengan performa kecepatan konvergen pada kedua model, model yang lebih cepat konvergen memiliki performa yang lebih baik.  

```
model_conv_results = {'mae': 39565.105, 'mse': 3369372200.0}

model_rnn_results = {'mae': 46709.727, 'mse': 4563947500.0}
```

## Evaluation

- 1. Metode Evaluasi
     
**Mean Absolute Error (MAE)** dan **Mean Squared Error (MSE)** adalah dua metrik evaluasi yang umum digunakan dalam pemodelan regresi dan prediksi. Keduanya digunakan untuk mengukur seberapa baik model machine learning dapat memprediksi nilai kontinu (numerik) seperti harga rumah, suhu, atau pendapatan berdasarkan data pelatihan yang ada. 

**MAE** mengukur rata-rata dari selisih absolut antara nilai prediksi dan nilai sebenarnya. Secara matematis, untuk setiap titik data i, MAE dihitung sebagai:


MAE = $\frac{1}{n} \Sigma_{i=1}^{n} |y_i - \hat{y}_i|$


${n}$: Jumlah total titik data dalam data uji atau validasi.

$y_i$: Nilai sebenarnya (ground truth) dari titik data i.

$\hat{y}_i$ : Nilai prediksi dari model untuk titik data i.

**MAE** merupakan nilai positif, dan semakin kecil nilai MAE, semakin baik performa model dalam memprediksi nilai sebenarnya. MAE juga memiliki interpretasi yang intuitif, yaitu rata-rata kesalahan prediksi secara absolut dalam satuan aslinya.

**MSE** mengukur rata-rata dari kuadrat selisih antara nilai prediksi dan nilai sebenarnya. Ini berfungsi untuk memberikan bobot lebih besar pada kesalahan yang lebih besar. MSE dihitung sebagai:


MSE = $\frac{1}{n} \Sigma_{i=1}^n({y_i}-\hat{y}_i)^2$


${n}$: Jumlah total titik data dalam data uji atau validasi.

$y_i$ : Nilai sebenarnya (ground truth) dari titik data i.

$\hat{y}_i^2$ : Nilai prediksi dari model untuk titik data i.

**MSE** menghasilkan nilai yang positif, dan semakin kecil nilai MSE, semakin baik performa model. Namun, MSE dapat menyebabkan efek outlier yang lebih signifikan daripada MAE karena penggunaan kuadrat dalam perhitungannya. Hal ini berarti bahwa kesalahan yang lebih besar akan memiliki dampak yang lebih besar pada nilai MSE.

- 2. Hasil Proyek
     
Setelah mengetahui bahwa model dengan menggunakan konvolusi bekerja lebih baik, selanjutnya adalah tahap memprediksi harga rumah di masa depan. Dalam proyek ini, model dites untuk memprediksi harga rumah untuk 48 minggu kedepan. 

Hasilnya adalah pada dua bulan pertama hasil prediksi masih tidak menunjukkan anomali, tetapi untuk prediksi minggu-minggu selanjutnya prediksi terus menerus naik dengan besar kenaikan yang sama. Hasil ini merupakan indikasi terjadinya ketidakwajaran  dan tidak dapat digunakan sebagai prediksi harga pada masa depan yang masih sangat jauh. Saat memprediksi harga rumah di masa depan yang masih dekat, model masih dapat menangkap pola-pola yang ada dalam data hitoris awal dengan baik. Ini membuat model dapat bekerja dengan baik karena perubahan harga mungkin lebih stabil dam masih dapat dijelaskan oleh tren harga pada masa lampau yang masih dekat.

Untuk perihal tentang prediksi terus menerus naik secara progressif, hal ini menjadi tidak wajar mengingat dalam pasar aset rumah dan bangunan harga tidak mungkin terus menerus naik dengan jumlah nilai kenaikan yang sama dalam kurun waktu tertentu, perubahan harga tidak selalu terjadi dalam pola linier yang terus menerus naik. Model yang hanya memperpanjang pola linier ini mungkin mengabaikan faktor-faktor kompleks yang mempengaruhi perubahan harga sebenarnya. Prediksi jauh di masa depan lebih sulit karena banyak faktor dan peristiwa yang tidak terduga dapat mempengaruhi pasar. Model mungkin menghadapi kesulitan dalam mengenali pola jangka panjang yang sebenarnya menggerakkan harga. Model mungkin hanya dapat menangkap pola jangka pendek atau menengah yang lebih mudah dikenali.

Apabila model hanya mengandalkan pola yang terlihat dimasa lalu, model tersebut mungkin tidak sensitif terhadap perubahan fundamental yang terjadi di masa depan. Projek ini memanfaatkan hasil prediksi sebelumnya sebagai data latihan untuk prediksi selanjutnya pada rentang waktu di masa depan. Prediksi yang terdapat pada prediksi sebelumnya pasti memiliki nilai residual yang mana jika hasil prediksi masa lalu yang memiliki nilai error digunakan kembali untuk melakukan prediksi ke masa depan yang lebih jauh, maka akan terjadi *cummulative error* model mulai belajar dari kesalahan yang terakumulasi, sehingga prediksi menjadi semakin tidak akurat seiring waktu. 


![image](https://github.com/Zelkova46/ML-terapan/assets/70127988/ae6a4061-9409-457b-af98-5b157c438ca2) 
Gambar 9. Grafik prediksi harga rumah untuk 48 minggu ke depan

Kesimpulannya adalah untuk memprediksi harga rumah yang jauh di masa depan, model akan bingung dan tidak dapat menentukan harga yang normal sehingga prediksi harga seakan-akan hanya tebakan saja. Sama seperti kita ingin memprediksi apakah bulan depan akan terjadi hujan atau tidak, pasti akan lebih sulit menebak terjadinya hujan satu bulan kedepan dibandingkan satu jam kedepan. 

Solusinya adalah setiap kali satu prediksi harga rumah dibuat oleh model dan data harga rumah baru untuk masa depan telah dibuat, model harus dilatih ulang dengan menggunakan data baru yang berupa data awal keseluruhan ditambah dengan satu data hasil dari prediksi sebelumnya. Lalu, model dilatih kembali sehingga model akan menghasilkan tebakan yang lebih akurat dalam hal memprediksi harga rumah selanjutnya. Iterasu selanjutnya adalah model akan dilatih kembali dengan menggunakan dataset awal ditambah dengan dua prediksi dari dua kali training model sebelumnya. Jika iterasi ini terus diulang maka hasil prediksi akan menjadi relevan.


_Catatan:_
- Untuk pelatihan model berulang dengan menggunakan satu data baru yang dihasilkan setiap kali model memprediksi belum dilakukan karena tahapannya juga sangat repetitif.


_Referensi:_

- [Land-use conversion and residential recentralization: Evidence from Japan's real estate bubble in the 1980s](https://mpra.ub.uni-muenchen.de/id/eprint/105961) 

- [Where and when was the 1980s bubble emerged in Japan? Evidence from prefecture-level land price data](https://feb.ugm.ac.id/id/profil/staf-pengajar/2576-traheka-erdyas-bimanatya) 

- [Oizumi, Eiji. "Property finance in Japan: expansion and collapse of the bubble economy." Environment and Planning A 26.2 (1994): 199-213.](https://journals.sagepub.com/doi/pdf/10.1068/a260199)
  
- [Yu, Li, Chenlu Jiao, Hongrun Xin, Yan Wang, and Kaiyang Wang. "Prediction on housing price based on deep learning." International Journal of Computer and Information Engineering 12, no. 2 (2018): 90-99.](https://publications.waset.org/10008599/prediction-on-housing-price-based-on-deep-learning)
  
- [Xu, Hangtian. "Land-use conversion and residential recentralization: Evidence from Japan's real estate bubble in the 1980s." (2020).](https://mpra.ub.uni-muenchen.de/105961/1/MPRA_paper_105961.pdf)
  
- [Xu, Xiaojie, and Yun Zhang. "House price forecasting with neural networks." Intelligent Systems with Applications 12 (2021): 200052.](https://www.sciencedirect.com/science/article/pii/S2667305321000417/pdfft?md5=aad456a2f3d0fe5ff87e775ba5a6c666&pid=1-s2.0-S2667305321000417-main.pdf)
  
- [Clapp, John, and Carmelo Giaccotto. "Evaluating house price forecasts." Journal of Real Estate Research 24.1 (2002): 1-26.](https://core.ac.uk/download/pdf/7162682.pdf)  

- [Hua, Yuxiu, et al. "Deep learning with long short-term memory for time series prediction." IEEE Communications Magazine 57.6 (2019): 114-119.](https://arxiv.org/pdf/1810.10161)
  
