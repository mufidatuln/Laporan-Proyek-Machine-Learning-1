# Laporan Proyek Machine Learning - Mufidatul Ngazizah
## Domain Proyek
Domain proyek yang digunakan adalah dalam bidang kesehatan, menurut WHO (World Health Organization) penyakit jantung merupakan penyebab kematian beberapa negara termasuk Indonesia, Inggris Raya, Autralia, Kanada, Amerika dan beberapa negara lain[1]. Penyakit jantung menyebabakn kematian karena tekanan darah, stres dan terlalu banyak bekerja, gula darah, dan banyak alasan lain. Dengan berkembangnya teknologi, banyak hal yan dapat dilakukan untuk meningkatkan kemudahan masyarakat untuk mendeteksi penyakit dengan bantaun Machine Learning yang menggunakan informasi yang relevan untuk prediksi penyalit jantung.nSetiap catatan dalam dataset ini berhubungan dengan masing-masing pasien, dan hasil diagnostik juga disediakan. Dataset ini dapat bermanfaat untuk penelitian dalam kesehatan jantung, pemodelan prediktif kondisi jantung, serta pengembangan alat diagnostik dan intervensi yang bertujuan untuk meningkatkan hasil kesehatan jantung.

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
Dataset yang digunakan diperoleh dari platform penyedia dataset yaitu Kaggle. Berikut dataset yang saya gunakan [Heart Attack Dataset (https://www.kaggle.com/datasets/sukhmandeepsinghbrar/heart-attack-dataset)] yang memiliki dimensi 1319 x 9 kolom diantaranya :
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

# Referensi
[1] American Journal of Sociology, “Penyakit Jantung,” J. Chem. Inf. Model., vol. 53, no. 9, pp. 1689–1699, 2019.
