# Laporan Proyek Machine Learning - Mufidatul Ngazizah
## Domain Proyek
Domain proyek yang digunakan adalah dalam bidang kesehatan, menurut WHO (World Health Organization) penyakit jantung merupakan penyebab kematian beberapa negara termasuk Indonesia, Inggris Raya, Autralia, Kanada, Amerika dan beberapa negara lain [1]. Penyakit jantung menyebabakn kematian karena tekanan darah, stres dan terlalu banyak bekerja, gula darah, dan banyak alasan lain. Dengan berkembangnya teknologi, banyak hal yan dapat dilakukan untuk meningkatkan kemudahan masyarakat untuk mendeteksi penyakit dengan bantaun Machine Learning yang menggunakan informasi yang relevan untuk prediksi penyalit jantung.nSetiap catatan dalam dataset ini berhubungan dengan masing-masing pasien, dan hasil diagnostik juga disediakan. Dataset ini dapat bermanfaat untuk penelitian dalam kesehatan jantung, pemodelan prediktif kondisi jantung, serta pengembangan alat diagnostik dan intervensi yang bertujuan untuk meningkatkan hasil kesehatan jantung.

# Bussines Understanding
Pada kasus ini sebuah rumah sakit ingin mengembangkan alat pendeteksi penyakit jantung. Mereka memiliki data rekam medis terkait pasien yang berresiko dan terdiagnosis memiliki penyakit jantung. Beberapa parameter yang akan digunakan untuk memaksimalkan pembuatan alat pendeteksi penyakit jantung.

## Problem Statemen
1. Dari berbeagai parameter yang ada. Variabel manakah yang sangat mempengaruhi seseorang mengalami penyakit jantung?
   
2. Dari 3 Model Machine Learning yaitu Logistic Regression, Random Forest, XGBClassifier manakah yang memiliki akurasi paling tinggi
   
## Goal
1. Mengetahui variabel karakteristik apa yang paling berpengaruh terhadap diagnosis penyakit jantung.
   
2. Membuat model machine learning terbaik untuk memprediksi penyakit jantung.

## Solution Statemen
Pada kasus kali ini saya menggunakan 3 model machine learning yaitu:
* Logistic Regression
Linear Regression adalah suatu cara permodelan masalah keterhubungan antara suatu variabel independen terhadap variabel dependen. Logistic Regression juga sebuah algoritma klasifikasi untuk mencari hubungan antara fitur (input) diskrit/kontinu dengan probabilitas hasil output diskrit tertentu.
* Random Forest
Random Forest adalah algoritma dalam machine learning yang digunakan untuk pengklasifikasian data set dalam jumlah besar. Karena fungsinya bisa digunakan untuk banyak dimensi dengan berbagai skala dan performa yang tinggi.
* XGBClassifier
XGBoost (Extreme Gradient Boosting) adalah sebuah algoritma machine learning yang sangat populer dan efektif dalam analisis data, khususnya dalam tugas-tugas seperti klasifikasi, regresi, dan peringkatan.


# Data Understanding
Dataset yang digunakan diperoleh dari platform penyedia dataset yaitu Kaggle. Berikut dataset yang saya gunakan [Heart Attack Dataset](https://www.kaggle.com/datasets/sukhmandeepsinghbrar/heart-attack-dataset) yang memiliki dimensi 1319 x 9 kolom diantaranya :
Berikut adalah penjelasan dari variable/ kolom pada dataset:

Age : Usia dalam Tahun

Gender : Data normalisasi jenis kelamin dengan hasil 1 = Laki-laki, 0 = Perempuan

Haert Rate : Detak Jantung

Systolic blood pressure : Tekanan Darah

Blood sugar : Gula Darah

CK-MB : Tes untuk mencari jenis enzim tertentu dalam darah untuk mendiagnosis atau menyingkirkan kemungkinan serangan jantung

Troponin : Jenis Protein yang ditemukan di otot jantung

Result : Hasil diagnosis, 0 = negatif, 1 = positif

# Data Visualization

## Distribusi Data
![Distribusi Data Setiap Fitur](https://github.com/mufidatuln/Laporan-Proyek-Machine-Learning-1/blob/main/distribusi_data.PNG)

1. Age: Data distribusi pada fitur usia memiliki nilai miring ke kanan, artinya nilai pada fitur usia lebih banyak dalam kelompok usia yang lebih tua.
   
2. Denyut jantung, tekanan darah sistolik, tekanan darah diastolik juga memiliki ditribusi miring ke kanan.

3. Hanya fitur Gula darah yang memiliki distribusi relatif normal.

## Perserbaran Jumlah Diagnosis Berdasarkan Gender
![Result Vs Gender](https://github.com/mufidatuln/Laporan-Proyek-Machine-Learning-1/blob/main/result%20vs%20gender.PNG)

Dari grafik tersebut kita dapat melihat dominan penderita penyakit jantung berjenis kelamin wanita. 

## Jumlah Pasien Positif Memiliki Penyakit Jantung Berdasarkan Segmentasi Umur
![Segemntasi Umur](https://github.com/mufidatuln/Laporan-Proyek-Machine-Learning-1/blob/main/jumlah%20positif%20berdasarkan%20usia.PNG)

Segmentasi umur yang dilakukan adalah sebagai berikut :

0-12 = Anak-Anak
13-21 = Remaja
22-60 = Dewasa
60-100 = Tua

Grafik tersebut menjelaskan bahwa dominan penderita penyakit jantung adalah pasien dengan usia 22 sampai 80 ke atas.

## Korelasi Antar Semua Feature
![Heat Map](https://raw.githubusercontent.com/mufidatuln/Laporan-Proyek-Machine-Learning-1/main/korelasi%20all.PNG)

Dari 9 feature yang memiliki korelasi cukup tinggi daripada yang lain hanya 3 feature yaitu : Age, Troponin, dan CK-MB.

![3 Fitur](https://raw.githubusercontent.com/mufidatuln/Laporan-Proyek-Machine-Learning-1/main/korelasi%203.PNG)

## Korelasi Usia dengan Gula Darah
![Usia vs Gula Darah](https://raw.githubusercontent.com/mufidatuln/Laporan-Proyek-Machine-Learning-1/main/usia%20gula%20darah.PNG)

Terdapat korelasi positif yang lemah antara usia dan gula darah. Ini berarti bahwa dengan bertambahnya usia, gula darah juga cenderung meningkat. Namun, korelasinya lemah, sehingga ada banyak variabilitas dalam data.

## Korelasi CK-MB denagn Troponin
![CK-MB vs Gula Darah](https://raw.githubusercontent.com/mufidatuln/Laporan-Proyek-Machine-Learning-1/main/CK-MB%20dan%20Tropin.PNG)

Terdapat korelasi positif yang lemah antara kadar CK-MB dan kadar troponin. Ini berarti bahwa dengan meningkatnya kadar CK-MB, kadar troponin juga cenderung meningkat, tetapi korelasinya lemah.

# Data Preposessing
## Melakuakan Split dataset
Sebelum membuat model, langkah pertama yang penting adalah membagi dataset menjadi dua bagian: data latih (train) dan data uji (test). Biasanya, kita menggunakan rasio 80% untuk data latih dan 20% untuk data uji. Hal ini penting untuk mempertahankan sebagian data yang dapat digunakan untuk menguji seberapa baik model dapat melakukan generalisasi terhadap data baru. Data latih digunakan untuk melatih model machine learning, sementara data uji digunakan untuk mengevaluasi kinerja model tersebut.

Pembagian ini berlaku baik untuk masalah regresi maupun klasifikasi. Karena data uji berperan sebagai representasi data baru yang belum pernah dilihat oleh model, semua transformasi perlu dilakukan terlebih dahulu pada data latih. Tujuannya adalah untuk menghindari pencemaran data uji dengan informasi yang diperoleh dari data latih. Oleh karena itu, membagi dataset menjadi bagian latih dan uji adalah langkah awal yang penting sebelum melakukan transformasi apapun.

## Melakukan standarisasi data
Standardisasi adalah langkah transformasi yang umum digunakan dalam persiapan pemodelan. Ketika menangani fitur numerik, pendekatan one-hot-encoding tidak diterapkan seperti pada fitur kategorikal. Sebagai gantinya, kita menggunakan StandardScaler dari library Scikit-learn. Proses StandarScaler melibatkan pengurangan mean (nilai rata-rata) dari setiap fitur, diikuti dengan pembagian dengan standar deviasi untuk menggeser distribusi. Hasilnya adalah distribusi dengan standar deviasi 1 dan mean 0. Ini mengakibatkan sekitar 68% dari nilai berada di kisaran -1 hingga 1. Agar tidak terjadi kebocoran informasi saat menggunakan data uji, standarisasi dilakukan hanya pada data pelatihan. Kemudian, saat tahap evaluasi, standarisasi diterapkan pada data uji. Untuk lebih memperjelas konsep ini, mari kita terapkan StandardScaler pada dataset yang tersedia.

# Modeling
## Logistic Regersion
Logistic Regression adalah salah satu algoritma yang digunakan untuk pemodelan regresi dalam konteks klasifikasi. Tujuannya adalah untuk memprediksi probabilitas bahwa suatu instance/data poin akan termasuk dalam salah satu dari dua kelas yang mungkin. Meskipun disebut "regresi", Logistic Regression sebenarnya digunakan untuk masalah klasifikasi. Keuntungan utama dari Logistic Regression adalah kemudahan interpretasi hasilnya dan efisiensi komputasinya. Namun, Logistic Regression juga memiliki beberapa kelemahan, seperti ketidakmampuan menangani hubungan non-linear antara fitur dan target, serta rentan terhadap overfitting jika terdapat fitur yang terlalu banyak atau korelasi tinggi antara fitur-fitur tersebut.

![Logistic Regeresion](https://raw.githubusercontent.com/mufidatuln/Laporan-Proyek-Machine-Learning-1/main/Logistic%20Regresion.PNG)

## Random Forest
Random Forest adalah algoritma yang digunakan untuk tugas klasifikasi dan regresi dalam machine learning. Ini termasuk dalam kategori algoritma ensemble, yang berarti ia menggabungkan prediksi dari beberapa model (disebut sebagai pohon keputusan dalam konteks Random Forest) untuk menghasilkan prediksi yang lebih akurat dan stabil. Keuntungan utama dari Random Forest adalah kemampuannya untuk mengatasi overfitting dan menangani dataset yang memiliki banyak fitur dengan baik. Ini juga cenderung memberikan kinerja yang baik secara default tanpa perlu penyetelan parameter yang rumit.

![Random Forest](https://raw.githubusercontent.com/mufidatuln/Laporan-Proyek-Machine-Learning-1/main/Random%20Forest.PNG)

## XGBClassifier
XGBClassifier adalah singkatan dari Extreme Gradient Boosting Classifier, yang merupakan implementasi dari algoritma gradient boosting yang sangat efisien dan efektif. XGBoost merupakan salah satu algoritma yang sangat populer dalam machine learning, terutama dalam kompetisi data dan proyek-proyek industri. Gradient boosting adalah proses iteratif di mana model ditambahkan satu per satu ke dalam rangkaian model yang ada. Setiap model ditambahkan dengan mengurangi gradien dari fungsi kerugian (loss function) terhadap prediksi sebelumnya. Dengan cara ini, setiap model berfokus pada bagian data yang tidak diprediksi dengan baik oleh model sebelumnya.

![XGBClassifier](https://raw.githubusercontent.com/mufidatuln/Laporan-Proyek-Machine-Learning-1/main/XGBClasifier.PNG)

# Evaluasi
## Accuracy
Accuracy (Akurasi) adalah rasio antara jumlah prediksi yang benar dengan total jumlah prediksi

​Accuracy= 
TP+TN+FP+FN/
TP+TN

TP (True Positive) adalah jumlah prediksi yang benar positif, TN (True Negative) adalah jumlah prediksi yang benar negatif, FP (False Positive) adalah jumlah prediksi yang salah positif, dan FN (False Negative) adalah jumlah prediksi yang salah negatif. 
​
## Precision
Precision (Presisi) adalah rasio antara jumlah prediksi yang benar positif dengan total jumlah prediksi positif. Dalam konteks klasifikasi, presisi mengukur seberapa banyak prediksi positif yang benar dari semua prediksi positif yang dilakukan.

## Recall
Recall (Recall atau Sensitivitas) adalah rasio antara jumlah prediksi yang benar positif dengan total jumlah kasus yang sebenarnya positif dalam data. Recall memberikan informasi tentang seberapa baik model dapat mengidentifikasi semua kasus positif yang sebenarnya.

## F1-Score
F1-Score adalah rata-rata harmonis dari precision dan recall. F1-Score memberikan keseimbangan antara precision dan recall. F1-Score berguna ketika kelas target tidak seimbang dan kita ingin mendapatkan keseluruhan performa model yang seimbang antara precision dan recall.

## AUC-ROC
AUC-ROC (Area Under the Receiver Operating Characteristic Curve) mengukur kinerja model untuk berbagai nilai threshold dalam membedakan antara kelas positif dan negatif. ROC Curve adalah grafik yang menunjukkan trade-off antara sensitivitas (recall) dan 1-specificity. Nilai AUC-ROC berkisar antara 0 hingga 1, di mana nilai yang lebih tinggi menunjukkan kinerja model yang lebih baik.

Pada kasus ini model dengan akurasi terbaik diperoleh dari **XGBClassifier** dengan matrik evaluasi yaitu **AUC_ROC**

# Referensi
[1] American Journal of Sociology, “Penyakit Jantung,” J. Chem. Inf. Model., vol. 53, no. 9, pp. 1689–1699, 2019.
