# Laporan Proyek Machine Learning - Mufidatul Ngazizah
## Domain Proyek
Penyakit jantung menjadi momok menakutkan bagi banyak orang di seluruh dunia,  menurut WHO (World Health Organization) penyakit jantung merupakan penyebab kematian beberapa negara termasuk Indonesia, Inggris Raya, Autralia, Kanada, Amerika dan beberapa negara lain [1]. Penyakit ini menduduki posisi terdepan sebagai penyebab kematian, merenggut jutaan nyawa setiap tahunnya. Maka dari itu akurasi prediksi dalam mendeteksi penyakit jantung sangatlah krusial untuk diagnosis dan pengelolaan penyakit yang efektif. Namun, sayangnya, masih banyak tantangan yang dihadapi dalam mencapai hal ini.

Memahami kompleksitas penyakit jantung dan hubungannya dengan berbagai faktor risiko merupakan kunci utama dalam meningkatkan akurasi prediksi. Berbagai faktor, seperti usia, jenis kelamin, tekanan darah, denyut jantung, tekanan darah sistolik, tekanan darah diastolik, CK-MB, dan troponin, memainkan peran penting dalam menentukan risiko seseorang terkena penyakit jantung. Proyek ini hadir untuk menjawab tantangan tersebut. Dengan memanfaatkan kemajuan teknologi machine learning dan analisis data, proyek ini bertujuan untuk mengembangkan model prediksi penyakit jantung yang canggih dan akurat, menggunakan faktor medis yang tersedia. Diharapkan, proyek ini mengidentifikasi pasien dengan risiko tinggi terkena penyakit jantung sehingga memungkinkan intervensi dini dan pencegahan yang efektif. Selain itu, dengan model ini diharapkan dokter dapat mempercepat diagnosis penyakit jantung sehingga mempercepat pengobatan. Alat ini juga diharapkan dapat membantu dokter dalam meningkatkan akurasi diagnosis sehingga mengurangi risiko misdiagnosis dan komplikasi.

# Bussines Understanding
Pada kasus ini sebuah rumah sakit ingin mengembangkan alat pendeteksi penyakit jantung. Mereka memiliki data rekam medis terkait pasien yang beresiko dan terdiagnosis memiliki penyakit jantung yang menjadi parameter untuk memaksimalkan pembuatan alat pendeteksi penyakit jantung. Penelitian ini memiliki potensi dampak yang signifikan terhadap kepentingan bisnis dan ekonomi rumah sakit, yaitu dapat meningkatkan efisiensi diagnosis penyakit jantung, hal ini dapat menghemat waktu dan biaya bagi rumah sakit. Selain itu, diagnosis dan pengobatan yang lebih akurat dapat meningkatkan kepuasan pasien dan reputasi rumah sakit.

## Problem Statemen
1. Bagaimana mengembangkan model prediksi penyakit jantung yang akurat dan dapat diandalkan untuk membantu dokter dalam mendiagnosis penyakit jantung secara dini?
   
2.  Model machine learning seperi apa yang dapat memprediksi penyakit jantung dengan akurasi yang paling tinggi?
   
## Goal
1. Mengetahui variabel karakteristik apa yang paling berpengaruh terhadap diagnosis penyakit jantung.
   
2. Menentukan model machine learning yang menghasilkan akurasi prediksi tertinggi dengan nilai akurasi lebih dari 95%

## Solution Statement
Pada kasus ini diterapkan 3 model machine learning, yaitu:

1. Logistic Regression
Linear Regression adalah suatu cara permodelan masalah keterhubungan antara suatu variabel independen terhadap variabel dependen. Logistic Regression juga sebuah algoritma klasifikasi untuk mencari hubungan antara fitur (input) diskrit/kontinu dengan probabilitas hasil output diskret tertentu.

3. Random Forest
Random Forest adalah algoritma dalam machine learning yang digunakan untuk pengklasifikasian data set dalam jumlah besar. Karena fungsinya bisa digunakan untuk banyak dimensi dengan berbagai skala dan performa yang tinggi.

4. XGBClassifier
XGBoost (Extreme Gradient Boosting) adalah sebuah algoritma machine learning yang sangat populer dan efektif dalam analisis data, khususnya dalam tugas-tugas seperti klasifikasi, regresi, dan peringkatan.


# Data Understanding
Dataset yang digunakan diperoleh dari platform penyedia dataset, yaitu Kaggle. Berikut dataset yang saya gunakan [Heart Attack Dataset](https://www.kaggle.com/datasets/sukhmandeepsinghbrar/heart-attack-dataset) yang memiliki dimensi 1319 x 9 kolom diantaranya:

* Age : Usia dalam tahun

* Gender : Data normalisasi jenis kelamin dengan hasil, 1 = Laki-laki dan  0 = Perempuan

* Haert Rate : Detak jantung

* Systolic blood pressure : Tekanan darah

* Blood sugar : Gula darah

* CK-MB : Tes untuk mencari jenis enzim tertentu dalam darah untuk mendiagnosis atau menyingkirkan kemungkinan serangan jantung

* Troponin : Jenis protein yang ditemukan di otot jantung

* Result : Hasil diagnosis, 0 = negatif, 1 = positif

# Data Visualization

## Distribusi Data
![Gambar 1. Distribusi Data](https://raw.githubusercontent.com/mufidatuln/Laporan-Proyek-Machine-Learning-1/main/img/Gambar%201.%20Distribusi%20Data.PNG)

1. Age: Data distribusi pada fitur usia memiliki nilai miring ke kanan, artinya nilai pada fitur usia lebih banyak dalam kelompok usia yang lebih tua.
   
2. Denyut jantung, tekanan darah sistolik, tekanan darah diastolik juga memiliki ditribusi miring ke kanan.

3. Hanya fitur Gula darah yang memiliki distribusi relatif normal.

## Perserbaran Jumlah Diagnosis Positif Berdasarkan Gender
![Gambar 2. Perserbaran Jumlah Diagnosis Positif Berdasarkan Gender](https://raw.githubusercontent.com/mufidatuln/Laporan-Proyek-Machine-Learning-1/main/img/Gambar%202.%20Perserbaran%20Jumlah%20Diagnosis%20Positif%20Berdasarkan%20Gender.PNG)

Dari grafik tersebut kita dapat melihat dominan penderita penyakit jantung berjenis kelamin wanita. 

## Jumlah Pasien Positif Memiliki Penyakit Jantung Berdasarkan Segmentasi Umur
![Gambar 3. Jumlah Pasien Positif Memiliki Penyakit Jantung Berdasarkan Segmentasi Umur](https://raw.githubusercontent.com/mufidatuln/Laporan-Proyek-Machine-Learning-1/main/img/Gambar%203.%20Jumlah%20Pasien%20Positif%20Memiliki%20Penyakit%20Jantung%20Berdasarkan%20Segmentasi%20Umur.PNG)

Segmentasi umur yang dilakukan adalah sebagai berikut :

* 0-12 = Anak-Anak
  
* 13-21 = Remaja
  
* 22-60 = Dewasa
  
* 60-100 = Tua

Grafik tersebut menjelaskan bahwa dominan penderita penyakit jantung adalah pasien dengan usia 22 sampai 80 ke atas.

## Korelasi Antar Semua Feature
![Gambar 4. Korelasi Antar Semua Feature](https://raw.githubusercontent.com/mufidatuln/Laporan-Proyek-Machine-Learning-1/main/img/Gambar%204.%20Korelasi%20Antar%20Semua%20Feature.PNG)

Dari 9 feature yang memiliki korelasi cukup tinggi daripada yang lain hanya 3 feature yaitu : Age, Troponin, dan CK-MB.

![Gambar 5](https://raw.githubusercontent.com/mufidatuln/Laporan-Proyek-Machine-Learning-1/main/img/Gambar%205.%20Highlight%20Tiga%20Korelasi%20Tertinggi.PNG)

## Korelasi Usia dengan Gula Darah
![Gambar 6. Korelasi Usia dengan Gula Darah](https://raw.githubusercontent.com/mufidatuln/Laporan-Proyek-Machine-Learning-1/main/img/Gambar%206.%20Korelasi%20Usia%20dengan%20Gula%20Darah.PNG)

Terdapat korelasi positif yang lemah antara usia dan gula darah. Ini berarti bahwa dengan bertambahnya usia, gula darah juga cenderung meningkat. Namun, korelasinya lemah, sehingga ada banyak variabilitas dalam data.

## Korelasi CK-MB dengan Troponin
![Gambar 7. Korelasi CK-MB dengan Troponin](https://raw.githubusercontent.com/mufidatuln/Laporan-Proyek-Machine-Learning-1/main/img/Gambar%207.%20Korelasi%20CK-MB%20denagn%20Troponin.PNG)

Terdapat korelasi positif yang lemah antara kadar CK-MB dan kadar troponin. Ini berarti bahwa dengan meningkatnya kadar CK-MB, kadar troponin juga cenderung meningkat, tetapi korelasinya lemah.

# Data Preposessing

## Handle Missing Value
Pada tahap pra-pemrosesan data, langkah-langkah yang diambil untuk menangani nilai yang hilang (missing value) adalah mengidentifikasi nilai yang hilang. Jika terdapat missing value selanjutya dapat dilakukan penanganan. Namun, dalam proyek ini dataset yang tersedia tidak memiliki missing value.

## Handling Data Duplikat
Data duplikat dapat mengganggu analisis dan pemodelan karena bisa menghasilkan bias dalam hasil. Oleh karena itu, langkah-langkah yang diambil untuk menangani data duplikat adalah mengidentifikasi data duplikat dari dataset. Namun, dalam proyek ini dataset yang tersedia tidak memiliki nilai duplikat.

## Melakuakan Split dataset
Sebelum membuat model, langkah pertama yang penting adalah membagi dataset menjadi dua bagian: data latih (train) dan data uji (test). Biasanya, kita menggunakan rasio 80% untuk data latih dan 20% untuk data uji. Hal ini penting untuk mempertahankan sebagian data yang dapat digunakan untuk menguji seberapa baik model dapat melakukan generalisasi terhadap data baru. Data latih digunakan untuk melatih model machine learning, sementara data uji digunakan untuk mengevaluasi kinerja model tersebut. Teknik yang digunakan untuk membagi data menjadi set pelatihan dan set uji pada proyek ini adalah metode "Train-Test Split".

Pembagian ini berlaku baik untuk masalah regresi maupun klasifikasi. Karena data uji berperan sebagai representasi data baru yang belum pernah dilihat oleh model, semua transformasi perlu dilakukan terlebih dahulu pada data latih. Tujuannya adalah untuk menghindari pencemaran data uji dengan informasi yang diperoleh dari data latih. Oleh karena itu, membagi dataset menjadi bagian latih dan uji adalah langkah awal yang penting sebelum melakukan transformasi apapun.

## Melakukan Standarisasi Data
Standardisasi adalah langkah transformasi yang umum digunakan dalam persiapan pemodelan. Ketika menangani fitur numerik, pendekatan one-hot-encoding tidak diterapkan seperti pada fitur kategorikal. Sebagai gantinya, kita menggunakan StandardScaler dari library Scikit-learn. Proses StandarScaler melibatkan pengurangan mean (nilai rata-rata) dari setiap fitur, diikuti dengan pembagian dengan standar deviasi untuk menggeser distribusi. Hasilnya adalah distribusi dengan standar deviasi 1 dan mean 0. Ini mengakibatkan sekitar 68% dari nilai berada di kisaran -1 hingga 1. Agar tidak terjadi kebocoran informasi saat menggunakan data uji, standarisasi dilakukan hanya pada data pelatihan. Kemudian, saat tahap evaluasi, standarisasi diterapkan pada data uji. Untuk lebih memperjelas konsep ini, mari kita terapkan StandardScaler pada dataset yang tersedia.


## Pemilihan Fitur
Sebelum memasuki tahap modeling, setiap fitur pada dataset akan di perikasa untuk melihat fitur mana yang paling relevan atau penting untuk meningkatkan kinerja model. Pada proyek kali ini dataset memiliki 9 fitur yang akan digunakan sebagai parameter dalam proses pembuatan pemodelan.

## Modeling
Pada proyek ini digunakan 3 algoritma machine learning yaitu :

1. Logistic Regression
*Logistic Regression* adalah salah satu algoritma yang digunakan untuk pemodelan regresi dalam konteks klasifikasi. Tujuannya adalah untuk memprediksi probabilitas bahwa suatu instance/data poin akan termasuk dalam salah satu dari dua kelas yang mungkin. Meskipun disebut "regresi", Logistic Regression sebenarnya digunakan untuk masalah klasifikasi. Keuntungan utama dari *Logistic Regression* adalah kemudahan interpretasi hasilnya dan efisiensi komputasinya. Namun, Logistic Regression juga memiliki beberapa kelemahan, seperti ketidakmampuan menangani hubungan non-linear antara fitur dan target, serta rentan terhadap overfitting jika terdapat fitur yang terlalu banyak atau korelasi tinggi antara fitur-fitur tersebut.

* Kelebihan *Logistic Regression*:
  
- *Interpretabilitas* : Hasil dari Logistic Regression mudah diinterpretasikan. Koefisien dari setiap fitur dapat memberikan informasi tentang hubungan antara fitur-fitur tersebut dan probabilitas kelas target.
  
- Efisien: Logistic Regression membutuhkan waktu pelatihan yang relatif singkat dibandingkan dengan beberapa algoritma yang lebih kompleks. Ini membuatnya cocok untuk digunakan pada dataset besar atau ketika komputasi harus dilakukan dengan sumber daya terbatas.

* Kekurangan *Logistic Regression*:
  
- *Linearitas* : *Logistic Regression* bekerja dengan baik ketika hubungan antara fitur-fitur dan label target dapat dijelaskan secara linear. Jika hubungan tersebut tidak linear, *Logistic Regression* mungkin tidak memberikan performa yang baik.

Pada model ini terdapat beberapa parameter yang digunakan dalam model *logistic regression* adalah `max_iter`. Parameter ini mengatur jumlah iterasi yang akan dieksekusi oleh algoritma optimasi ketika melatih model. Dalam contoh tersebut, nilai max_iter=1000 mengindikasikan bahwa algoritma akan berhenti setelah 1000 iterasi jika konvergensi belum tercapai.

2. Random Forest
   
*Random Forest* adalah algoritma yang digunakan untuk tugas klasifikasi dan regresi dalam machine learning. Ini termasuk dalam kategori algoritma ensemble, yang berarti ia menggabungkan prediksi dari beberapa model (disebut sebagai *decision tree* dalam konteks *Random Forest*) untuk menghasilkan prediksi yang lebih akurat dan stabil. Keuntungan utama dari *Random Forest* adalah kemampuannya untuk mengatasi overfitting dan menangani dataset yang memiliki banyak fitur dengan baik. Ini juga cenderung memberikan kinerja yang baik secara default tanpa perlu penyetelan parameter yang rumit.

* Kelebihan *Random Forest*:
  
- Kinerja yang Tinggi: Random Forest sering menghasilkan kinerja yang sangat baik dalam berbagai macam masalah, termasuk yang kompleks. 
  
- Tahan terhadap *Overfitting* : Dengan menggunakan teknik seperti pengambilan sampel acak dan pemilihan fitur acak, Random Forest cenderung lebih tahan terhadap *overfitting* dibandingkan dengan *decision tree* tunggal.

* Kekurangan *Random Forest* :
  
- Kompleksitas: *Random Forest* cenderung lebih kompleks daripada beberapa model lainnya, seperti *Logistic Regression* atau *Naive Bayes*.

Parameter yang digunakan dalam model ini adalah 'n_estimators', parameter ini mengontrol jumlah *decision tree* yang akan dibangun.

3. *XGBClassifier*
  
*XGBClassifier* adalah singkatan dari *Extreme Gradient Boosting Classifier*, yang merupakan implementasi dari algoritma *gradient boosting* yang sangat efisien dan efektif. *XGBoost* merupakan salah satu algoritma yang sangat populer dalam *machine learning*, terutama dalam kompetisi data dan proyek-proyek industri. *Gradient boosting* adalah proses iteratif di mana model ditambahkan satu per satu ke dalam rangkaian model yang ada. Setiap model ditambahkan dengan mengurangi gradien dari fungsi kerugian (loss function) terhadap prediksi sebelumnya. Dengan cara ini, setiap model berfokus pada bagian data yang tidak diprediksi dengan baik oleh model sebelumnya.

* Kelebihan *XGBClassifier*
  
- Kinerja yang Tinggi: *XGBoost* dikenal memiliki kinerja yang sangat baik dalam berbagai macam masalah klasifikasi dan regresi. Ini karena kemampuannya untuk memodelkan hubungan yang kompleks antara fitur-fitur dan label target.
  
- Regularisasi yang Kuat: *XGBoost* memiliki berbagai opsi regularisasi yang dapat membantu mencegah *overfitting*, termasuk regulasi L1 (Lasso) dan L2 (Ridge).

* Kekurangan *XGBClassifier*
  
- Komputasi yang Intensif: XGBoost bisa memerlukan sumber daya komputasi yang signifikan, terutama jika digunakan dengan parameter yang kompleks atau pada dataset yang besar.
  
- Sensitif terhadap Penyetelan Parameter: XGBoost memiliki banyak parameter yang dapat disesuaikan. Penyetelan parameter yang tepat mungkin memerlukan pengalaman dan pengetahuan yang mendalam tentang algoritma.

Parameter yang digunakan dalam pembuatan model XGBClassifier adalah sebagai berikut:

`use_label_encoder`: Parameter ini adalah boolean yang menentukan apakah label target harus di-encode atau tidak.

`eval_metric` : Parameter ini menentukan metrik evaluasi yang akan digunakan selama proses pelatihan.

# Evaluasi

Model dievaluasi menggunakan set uji yang terpisah. Matrik evaluasi yang digunakan pada proyek adalah sebagai berikut :

|  Model |  Accuarcy | Precision | Recall  |F1-Score   | AUC-ROC  |
|---|---|---|---|---|---|
|  Logistic Regersion | 0.799242  |  0.819767	 | 0.865031  | 0.841791  | 0.884863  |
Tabel 1. Logistic Regersion

|  Model |  Accuarcy | Precision | Recall  |F1-Score   | AUC-ROC  |
|---|---|---|---|---|---|
|  Random Forest | 0.981061  |  0.981707	 | 0.98773  | 0.984709  | 0.989552  |
Tabel 2. Random Forest

|  Model |  Accuarcy | Precision | Recall  |F1-Score   | AUC-ROC  |
|---|---|---|---|---|---|
|  XGBClassifier | 0.981061  |  0.981707 | 0.98773  | 0.984709  | 0.992529  |
Tabel 3. XGBClassifier


## Accuracy
Accuracy mengukur seberapa sering model melakukan prediksi yang benar secara keseluruhan. Dapat dilihat pada Tabel 1, nilai metrix accuracy sebesar 0.799 pada model *Logistic Regersion* hal ini menunjukkan model cukup baik dalam mengklasifikasikan data ke dalam kategori yang benar. Namun hasil tersebut belum dapat dibilang tinggi karena akurasi dapat menjadi bias jika distribusi kelas tidak seimbang dalam dataset. Pada Tabel 2 dan Tabel 3 nilai metrix akurasi sudah mencapai 0.98 yaitu pada model *Random Forest* dan *XGBClassifier*. Nilai akurasi dihitung dari rumus matematika berikut :

$$ x = {TP + TN + FP +FN \over TP+TN} $$

TP (True Positive) adalah jumlah prediksi yang benar positif, TN *(True Negative)* adalah jumlah prediksi yang benar negatif, FP *(False Positive)* adalah jumlah prediksi yang salah positif, dan FN *(False Negative)* adalah jumlah prediksi yang salah negatif. 
​
## Precision
*Precision* mengukur proporsi dari prediksi positif yang benar dari semua prediksi positif yang dilakukan oleh model. Pada Tabel 1 nilai *precision* sebesar 0.818 dengan algoritma *Logistic Regression* menunjukkan seberapa tepat model dalam mengidentifikasi pasien yang benar-benar positif. Nilai presisi yang tinggi menunjukkan bahwa model memiliki kemampuan untuk menghindari memberikan diagnosis positif yang salah kepada pasien yang sebenarnya tidak mengidap penyakit. Pada Tabel 2 dan 3 nilai *precision* sudah menyentuh 0.98 hal itu di nilai cukup tinggi atau sudah memenuhi kriteria dari tujuan atau *goal* di awal.

## Recall:
Recall mengukur proporsi dari data yang relevan yang berhasil diidentifikasi oleh model. Dalam konteks ini, recall menunjukkan seberapa baik model dalam mengidentifikasi semua kasus positif yang sebenarnya ada. Nilai recall yang tinggi menunjukkan bahwa model memiliki kemampuan untuk mengidentifikasi sebagian besar kasus positif yang sebenarnya ada. Pada Tabel 1 *Logistic Regression* nilai matrix recall sebesar 0.86 sedikit lebih baik dari evaluasi *precision* pada algoritama *Logistic Regression*.

## F1-Score
F1-Score adalah rata-rata harmonis dari precision dan recall. F1-Score memberikan keseimbangan antara precision dan recall. F1-Score berguna ketika kelas target tidak seimbang dan kita ingin mendapatkan keseluruhan performa model yang seimbang antara precision dan recall. Pada Tabel 1 Logistic Regression nilai F1-Score lebih rendah dari recall, namun pada Tabel 2 dan Tabel 3 dapat dilihat bahwa nilai evaluasi F1-Score mencapai 0.98.

## AUC-ROC
AUC-ROC (Area Under the Receiver Operating Characteristic Curve) mengukur kinerja model untuk berbagai nilai threshold dalam membedakan antara kelas positif dan negatif. ROC Curve adalah grafik yang menunjukkan trade-off antara sensitivitas (recall) dan 1-specificity. Nilai AUC-ROC berkisar antara 0 hingga 1, di mana nilai yang lebih tinggi menunjukkan kinerja model yang lebih baik. Pada Tabel 3. XGBClassifier nilai matrix evaluasi dengan AUC-ROC mencapai 0.99 sedangkan untuk model *Logistic Regression* dan *Random Forest* hanya mencapai 0.88 dan 0.98.

Kesimpulan dari keberhasilan proyek dan kemampuan model untuk menyelesaikan masalah didasarkan pada evaluasi metrik dan konteks proyek secara keseluruhan. Pada kasus ini model dengan akurasi terbaik diperoleh dari *XGBClassifier* dengan niali matrik evaluasi yang mecapai 0.99 pada *AUC_ROC*.

# Referensi
[1] American Journal of Sociology, “Penyakit Jantung,” J. Chem. Inf. Model., vol. 53, no. 9, pp. 1689–1699, 2019.
