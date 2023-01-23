# Laporan Proyek Machine Learning - Lalu Ardita Arip
## Domain Proyek

Mobil merupakan suatu hal yang penting yang dianggap mampu mempermudah kebutuhan hidup manusia, sejak ditemukannya mobil sebagai alat transportasi, manusia lebih dipermudah dalam bepergian dan juga lebih praktis daripada sepeda motor yang hanya bisa bermuatan terbatas, mobil mampu mengangkut penumpang atau muatan lebih banyak dari pada sepeda motor. Seiring perkembangan zaman banyak model dari mobil yang mulai dikembangkan dan juga model yang awalnya hanya menggunakan transmisi manual kini terdapat transmisi otomatis dan semi auto, serta bahan bakar yang mulai dikembangkan. Dengan berkembangnya model dan jenis dari mobil tersebut tentu akan berpengaruh terhadap harga dari mobil tersebut.
Tentunya setiap tahun masing-masing perusahaan memproduksi mobil dengan jenis yang berbeda, sehingga tercatat mobil yang diproduksi dengan kriteria tertentu, sehingga kita dapat memprediksi harga mobil dengan menggunakan data yang telah tercatat.
Melakukan prediksi terhadap data mobil dengan algoritma KNN, random forest dan boosting. Kemudian dapat dilakukan evaluasi performa terhadap masing-masing algoritma dengan tujuan mendapatkan hasil prediksi terbaik.

## Business Understanding
### Problem Statements
- Apakah model dapat memprediksi harga mobil dengan baik?
### Goals
- Mengetahui model yang terbaik dalam memprediksi harga mobil

### Solution Statements
- Menggunakan EDA agar kita dapat melihat fitur apa saja yang berkorelasi dan memiliki pengaruh terhadap harga dari sebuah mobil.
- Lalu kita juga dapat menggunakan Model Machine Learning yang sesuai, contohnya pada proyek ini menggunakan regresi untuk membantu menyelesaikan masalah. Untuk melihat model mana yang memberikan hasil yang terbaik dalam memprediksi harga mobil. Adapun model yang akan digunakan antara lain :
    - K-Neighbors Regressor
    - Random Forest Regressor
    - AdaBoost Regressor 
## Data Understanding
 Dataset yang digunakan merupakan dataset yang diambil dari platform kaggel yang dipublikasikan oleh Adhurim Quku. Dataset ini terdiri dari sebuah data yaitu data ford.csv. Berikut akses link menuju dataset tersebut https://www.kaggle.com/datasets/adhurimquku/ford-car-price-prediction. Data tersebut berisi sekitar 17.966 merek mobil yang terdiri dari beberapa fitur antara lain.
 - Model		: Variabel yang mencantumkan merek dari mobil
 - Year		: Tahun produksi
 - Price		: Harga Mobil dalam $
 - Transmission	: Terdiri dari Automatic, Manual, Semi-Auto
 - Mileage	: Jumlah mil yang ditempuh
 - fuel_Type	: tipe bahan bakar yang digunakan (Diesel, Bensin, Hybrid)
 - Tax		: pajak yang ditanggung
 - Mpg		: Miles per gallon
 - engineSize 	: Ukuran mesin mobil.

Lalu dilakukan Exploratory Data Analysis(EDA) dengan tujuan untuk menghilangkan outlier, dan memperlihatkan korelasi antara data numerik dan kategorikal.
Dapat dilihat dari bentuk boxplot dari data numerik dari year, price, mileage, tax, mpg dan engineSize.

![year](https://user-images.githubusercontent.com/86635607/190564616-8b64641e-30cc-481e-a71f-776911cf21c5.png)

![mileage](https://user-images.githubusercontent.com/86635607/190564871-059fcda6-06d6-4774-a05a-28fb854616d6.png)

![tax](https://user-images.githubusercontent.com/86635607/190565231-4608b724-e2e5-4bb4-a718-3921097a8bbc.png)

![mpg](https://user-images.githubusercontent.com/86635607/190565321-a4477f5c-ab4b-4eab-9d68-2691ac88db5d.png)

![ES](https://user-images.githubusercontent.com/86635607/190565387-1ccc1aee-85f1-4732-8cac-a09ceeacacee.png)

Dari boxplot diatas dapat dilihat bahwa semua fitur memiliki outliers. Sehingga digunakan lah metode Interquartile Range (IQR) agar dapat mengatasi outliers dengan cara mereduksi dan mengeliminasi data agar outliers dapat teratasi.

Melakukan *univariate analysis* untuk data numerik dan kategorik pada data tersebut.

![model](https://user-images.githubusercontent.com/86635607/190565585-f9c9ac27-9398-4a89-90a3-729fe046bdfd.png)
Terdapat 18 kategori pada fitur model dengan presentasi fiesta dengan model terbanyak dan musatang merupakan model dengan persentase paling sedikit.

![transmisi](https://user-images.githubusercontent.com/86635607/190565671-f22ff8dc-7c9f-49b0-9ebf-84f60fbfdbc0.png)
Pada transmission terdapat transmission manual, automatic dan semi-auto, dengan manual memiliki persentase paling tinggi.

![bensin](https://user-images.githubusercontent.com/86635607/190565784-d5190ccb-8778-4c5d-a205-bb655c10b92b.png)
Pada tipe bahan bakar terdiri dari petrol, diesel dan hybrid. dan dengan penggunaan bahan bakar petrol yang paling banyak.

Dan untuk visualisasi numerik dilakukan menggunakan plot histogram.
![histogram](https://user-images.githubusercontent.com/86635607/190566005-5583d14c-68da-4968-80fb-7151f58cd85b.png)
Dari plot histogram tersebut dapat dilihat bahwa:
- Pada data price data rumah dimulai dari rentang harga 5000 hingga 25000.
- Distribusi pada data miring ke kanan (right skewed) yang dimana akan berdampak pada hasil prediksi model yang akan digunakan..

Lalu menggunakan multivariate analysis EDA untuk data numerik dan kategorikal
![EDA model](https://user-images.githubusercontent.com/86635607/190567060-216686ef-fdb9-4753-999a-c0560881de61.png)
![EDA transmisi](https://user-images.githubusercontent.com/86635607/190567097-6d549cce-eaf8-475d-95b5-afc360cfa8ea.png)
![EDA bb](https://user-images.githubusercontent.com/86635607/190567112-d4a68f30-9693-4324-a465-30a62386718d.png)

Dari data diatas dapat disimpulkan bahwa:
- Data pada model dapat menyimpulkan bahwa dari model mobil memiliki pengaruh yang besar terhadap harga mobil dengan mustang merupakan model dengan harga tertinggi.
- Data pada transmission, masing-masing transmission memiliki nilai yang hampir mirip satu dengan yang lain namun automatic transmission merupakan mobil dengan dengan harga yang paling tinggi.
- Data pada bahan bakar, bahan bakar dengan jenis hybrid merupakan bahan bakar dengan nilai jual yang tinggi.

Lalu menggunakan pairplot untuk melihat hubungan antara data pada fitur dan target.

![pairplot](https://user-images.githubusercontent.com/86635607/190567466-49529306-250f-4d99-8d9b-79e6c9ce75e4.png)
Dari pairplot diatas beberapa data seperti mpg memiliki hubungan yang kurang bagus dengan data harga hal tersebut dapat dilihat dari persebaran hubungan antara data price dan mpg.

Korelasi juga dapat dilihat dengan membuat heatmap yang bertujuan untuk mempermudah dalam memahami hubungan dengan data harga.

![korelasi](https://user-images.githubusercontent.com/86635607/190567681-2c8cff08-f223-4521-8ed7-5d528417569d.png)
dari pairplot diatas di jelaskan bahwa korelasi antara mpg terhadap price merupakan korelas terendah daibandingkan yang lainnya, karena korelasi dengan mpg merupakan yang terendah fitur mpg dapat di hapus.

## Data Preparation

- Menggunakan metode *Interquartile Range* (IQR) untuk mengatasi masalah outlier  yang akan berdampak pada pengurangan data pada dataset namun akan lebih mempermudah dalam menganalisis data.
- Menggunakan fungsi one hot encoding pada data kategorikal. dengan memanfaatkan  fungsi *get_dummies* pada library Pandas yang sudah di import, dimana mengubah data  menjadi bilangan biner.
- Membagi data menjadi dua data  yaitu train data dan test data, dengan memanfaatkan  fungsi *train_test_split*. Data dibagi menjadi  80% untuk data train dan 20% untuk data test.
- Melakukan standarisasi terhadap fitur numerik agar menghasilkan nilai standar deviasi sama dengan 1 dan mean sama dengan 0. Standarisasi dilakukan agar memudahkan algoritma dalam melakukan komputasi perhitungan sehingga mempermudah dalam menyelesaikan masalah.

## Modeling

- Dalam tahap modeling berikut algoritma yang digunakan dalam pembuatan model machine learning, yang diaman algoritma-algoritma yang digunakan merupakan algoritma bertipe regresi.
    - **K-Neighbors Regressor**,merupakan algoritma sederhana yang menggunakan kesamaan fitur untuk memprediksi nilai dari setiap data yang baru. Kelebihan dari algoritma ini yaitu melakukan perhitungan yang baik pada data yang bersifat non-linear, namun algoritma ini juga memiliki kelemahan yaitu sangat sensitif terhadap missing value dan outliers.
    - **Random Forest**, merupakan algoritma supervised learning. Algoritma ini dapat digunakan untuk menyelesaikan masalah klasifikasi dan regresi karena memiliki stabilitas yang bagus.
    - **Boosting**, merupakan metode yang ensemble learning dimana model dilatih secara berurutan atau dalam proses yang iteratif.

- Tahapan dalam membuat model dengan beberapa algoritma yang berbeda.
    1. Pembuatan data frame yang akan diisi menggunakan data hasil MSE dari data latih dan data uji pada setiap algoritma yang akan digunakan.
    2. Selanjutnya mengambil fungsi KNeighborsRegressor. Pada algoritma K-Neighbors Regressor, digunakan parameter n_neighbors=10.
    3. Lalu mengambil fungsi RandomForestRegressor. Setelah itu membuat model dengan diisikan beberapa parameter seperti n_estimators=50, max_depth=16, dan random_state=55.
    4. Selanjutnya mengambil fungsi AdaBoostRegressor. Digunakan beberapa parameter seperti learning_rate=0.05, dan random_state=55.

## Evaluation

Pada tahap evaluasi, kita menggunakan  Mean Squared Error (MSE) untuk menghitung nilai rata-rata dari jumlah selisih dari rata-rata nilai sebenarnya dengan nilai hasil prediksi.

![rumus MSE](https://user-images.githubusercontent.com/86635607/190569248-4db33849-6e5f-4f48-9422-4be69ad4b636.png)

Keterangan:
n : jumlah dataset
Yi : nilai sebenarnya
Ŷi = nilai prediksi

Adapun hasil yang diperoleh dari MSE dari ketiga algoritma model machine learning sebagai berikut.

![Hasil visualisasi MSE](https://user-images.githubusercontent.com/86635607/190569726-5cabd790-a248-46d5-8da0-f24e0e5f858b.png)
Pada hasil diatas dapat dilihat bahwa algoritma KNN memiliki nilai error yang paling kecil pada data uji dibandingkan dengan algoritma random forest dan boosting.

![hasil](https://user-images.githubusercontent.com/86635607/190569897-3489cd45-926f-473d-a9ce-a4e3c71d9a39.png)
Hasil dari prediksi model dapat ditampilkan dalam bentuk tabel yang berisi nilai aktual yang akan menampilkan data uji dengan data yang diprediksi oleh model machine learning. Dari hasil diatas dinyatakan bahwa algoritma KNN memiliki hasil prediksi yang paling mendekati dengan hasil 9885.4 dari 9750, random forest dengan hasil 9991.1 dari 9750 dan boosting dengan 11013.6 dari 9750. dengan agoritma KNN yang memiliki seslisih terkecil yaitu 135,4.

## Kesimpulan

Dari hasil uji data terhadap dataset prediksi harga mobil ford menggunakan tiga model machine learning, dapat ditarik kesimpulan bahwa di antara algoritma KNN, random forest dan boosting, algoritma KNN memiliki hasil yang paling mendekati prediksi tentunya hal ini  dapat dilihat dari nilai *Mean Squared Error* (MSE) yang dihasilkan lebih kecil dan lebih mendekati dibanding algoritma random forest dan boosting, shingga dapat ditarik kesimpulan bahwa algooritma KNN marupakan algoritma terbaik untuk memperediksi harga mobil.

## Referensi

https://www.kaggle.com/datasets/adhurimquku/ford-car-price-prediction
http://repository.upbatam.ac.id/id/eprint/540



