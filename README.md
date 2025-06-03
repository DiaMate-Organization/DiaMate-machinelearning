# 🩺 Perancangan Model Prediksi Diabetes Berdasarkan Indikator Kesehatan

## 1. Deskripsi Proyek

### 1.1 Gambaran Proyek (Project Overview)

Diabetes merupakan penyakit kronis yang terjadi ketika pankreas tidak menghasilkan cukup insulin atau tubuh tidak dapat menggunakan insulin yang diproduksi secara efektif. Sebagai hormon pengatur glukosa darah, insulin yang tidak terkontrol dapat menyebabkan hiperglikemia yang dalam jangka panjang merusak berbagai sistem tubuh, terutama saraf dan pembuluh darah. Berdasarkan sumber dari WHO Jumlah penderita diabetes mengalami peningkatan drastis dari 200 juta pada tahun 1990 menjadi 830 juta pada tahun 2022, dengan prevalensi yang meningkat lebih cepat di negara-negara berpenghasilan rendah dan menengah dibandingkan negara berpenghasilan tinggi.
Pada tahun 2022, 14% orang dewasa berusia 18 tahun ke atas hidup dengan diabetes, meningkat dari 7% pada tahun 1990. Yang memprihatinkan, lebih dari setengah (59%) orang dewasa berusia 30 tahun ke atas yang hidup dengan diabetes tidak mengkonsumsi obat untuk kondisi mereka, dengan cakupan pengobatan terendah di negara-negara berpenghasilan rendah dan menengah. Diabetes secara langsung menyebabkan 1,6 juta kematian pada tahun 2021, dengan 47% kematian akibat diabetes terjadi sebelum usia 70 tahun. Selain itu, 530.000 kematian akibat penyakit ginjal disebabkan oleh diabetes, dan glukosa darah tinggi menyebabkan sekitar 11% kematian akibat penyakit kardiovaskular.
Proyek ini bertujuan untuk menciptakan sebuah platform berbasis web yang dapat mendeteksi tingkat diabetes pada pengguna (0-3) dengan pendekatan inovatif berbasis teknologi. Latar belakang proyek ini adalah :
- Peningkatan aksesibilitas layanan kesehatan melalui screening awal berbasis gejala.
- Penyediaan edukasi kesehatan inklusif, sehingga pengguna dapat memahami risiko diabetes mereka secara lebih baik.
- Pemanfaatan machine learning untuk memberikan analisis risiko yang akurat serta rekomendasi personal untuk mengurangi risiko diabetes.

### 1.2 Mengapa Masalah Ini Harus Diselesaikan?

Deteksi dini diabetes dapat menurunkan angka komplikasi dan kematian. Dengan analisis data kesehatan masyarakat, kita bisa memberikan peringatan awal bagi individu berisiko tinggi tanpa harus melalui pemeriksaan medis yang mahal dan invasif.

### 1.3 Bagaimana Masalah Ini Harus Diselesaikan?

Masalah ini diselesaikan dengan memanfaatkan teknik pembelajaran mesin (machine learning) berbasis klasifikasi. Dataset yang digunakan dianalisis, disiapkan, dan dimodelkan menggunakan algoritma yang relevan untuk mengidentifikasi individu dengan risiko diabetes.

### 1.4 State of the Art Penelitian Sebelumnya

Penelitian sebelumnya banyak menggunakan pendekatan seperti Logistic Regression, Decision Tree, dan Random Forest untuk prediksi diabetes. Beberapa juga mengaplikasikan deep learning atau teknik ensemble untuk meningkatkan akurasi. Penelitian ini melanjutkan pendekatan tersebut dengan membandingkan beberapa model dan memilih yang terbaik berdasarkan evaluasi performa.

## 2. Business Understanding

### 2.1 Problem Statement

- Sulitnya melakukan deteksi dini risiko diabetes pada populasi umum tanpa pemeriksaan medis langsung.
- Kurangnya sistem berbasis data yang dapat membantu tenaga kesehatan mengidentifikasi individu berisiko tinggi.
- Belum adanya pemanfaatan indikator kesehatan survei (seperti BRFSS) secara optimal untuk prediksi penyakit kronis.

### 2.2 Goals

- Mengembangkan model machine learning yang mampu mengklasifikasikan status risiko diabetes dengan akurasi tinggi.
- Menentukan fitur-fitur kesehatan masyarakat yang paling signifikan terhadap status diabetes.
- Menyediakan rekomendasi gaya hidup yang dapat dimanfaatkan oleh pengguna di sektor kesehatan.

### 2.3 Solution Statements

- Melakukan eksplorasi dan pembersihan data dari dataset BRFSS 2015 yang mencakup indikator kesehatan.
- Menerapkan teknik seleksi fitur dan membuat model Artificial Neural Network.
- Mengevaluasi model terbaik untuk diimplementasikan dalam sistem deteksi risiko diabetes yang memberikan rekomendasi gaya hidup.

## 3. Data Understanding

### 3.1 Dataset Overview

Kaggle Dataset: [Diabetes Health Indicators Dataset](https://www.kaggle.com/datasets/alexteboul/diabetes-health-indicators-dataset)

### 3.2 Data Description

Dataset merupakan hasil survei BRFSS (Behavioral Risk Factor Surveillance System) tahun 2015, mencakup indikator kesehatan masyarakat seperti:

- HighBP, HighChol, BMI
- Smoker, Stroke, HeartDiseaseorAttack
- PhysActivity, Fruits, Veggies, HvyAlcoholConsump
- Education, Income
- Diabetes_binary (target variable)

### 3.3 Struktur Data

- Jumlah fitur: 22 (termasuk target)
- Target: `Diabetes_binary` (0: tidak diabetes, 1: diabetes)
- Format: CSV
- Observasi: seimbang (balanced 50/50 split)

## 4. Data Preparation

- Pemisahan fitur dan label (`X`, `y`)
- Seleksi fitur menggunakan `SelectKBest` dengan fungsi `f_classif`
- Korelasi visual menggunakan heatmap seaborn
- Tidak ditemukan missing values yang signifikan

## 5. Modeling

Model yang digunakan antara lain:

- Logistic Regression
- Random Forest Classifier
- Decision Tree Classifier
- Gradient Boosting Classifier

Setiap model dilatih pada data latih dan dievaluasi pada data uji menggunakan metrik akurasi, precision, recall, dan F1-score.

## 6. Evaluation

Evaluasi dilakukan dengan menggunakan metrik klasifikasi:

- Confusion Matrix
- Accuracy Score
- Classification Report

Model Gradient Boosting menunjukkan performa terbaik secara keseluruhan, dengan nilai F1-score dan akurasi tertinggi pada data uji.

## 7. Kesimpulan

Proyek ini berhasil membangun model klasifikasi risiko diabetes berdasarkan indikator kesehatan masyarakat. Hasil menunjukkan bahwa fitur-fitur seperti `HighBP`, `BMI`, `CholCheck`, dan `PhysActivity` sangat berkorelasi terhadap status diabetes. Model terbaik dapat digunakan sebagai sistem pendukung keputusan dalam kebijakan kesehatan.

## 8. Kesimpulan Dampak terhadap Business Understanding

Model prediksi ini memiliki potensi besar dalam sistem kesehatan publik untuk mengidentifikasi individu berisiko tinggi sebelum menjalani tes laboratorium, sehingga dapat mengurangi beban biaya dan meningkatkan tindakan pencegahan lebih awal.

## 9. Daftar Pustaka

1. Centers for Disease Control and Prevention (CDC). Behavioral Risk Factor Surveillance System (BRFSS) 2015.
2. Kaggle Dataset: [Diabetes Health Indicators Dataset](https://www.kaggle.com/datasets/alexteboul/diabetes-health-indicators-dataset)
3. Pedregosa et al., "Scikit-learn: Machine Learning in Python", Journal of Machine Learning Research, 2011.
4. Hastie, Tibshirani, Friedman. *The Elements of Statistical Learning*, Springer, 2009.
