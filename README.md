# 🩺 Laporan Capstone Project : *DiaMate*

## 1. Deskripsi Proyek

Proyek ini bertujuan untuk mengembangkan sistem prediksi risiko diabetes secara kuantitatif dalam bentuk nilai rentang (0.00 – 1.00), yang mencerminkan tingkat probabilitas seseorang terkena diabetes berdasarkan data indikator kesehatan. Pendekatan utama yang digunakan adalah pemodelan menggunakan Artificial Neural Network (ANN), yang memiliki kemampuan tinggi dalam menangkap hubungan non-linear antar fitur.

Tidak hanya berhenti pada klasifikasi atau probabilitas risiko, sistem ini juga dirancang untuk memberikan rekomendasi gaya hidup personalisasi berdasarkan hasil prediksi. Rekomendasi ini diformulasikan secara natural dan manusiawi menggunakan Gemini API, yaitu model bahasa yang memungkinkan penyajian saran yang bersifat empatik, konkret, dan dapat langsung diimplementasikan dalam kehidupan sehari-hari.

### 1.1 Gambaran Proyek (Project Overview)

Diabetes merupakan penyakit kronis yang terjadi ketika pankreas tidak menghasilkan cukup insulin atau tubuh tidak dapat menggunakan insulin yang diproduksi secara efektif. Sebagai hormon pengatur glukosa darah, insulin yang tidak terkontrol dapat menyebabkan hiperglikemia yang dalam jangka panjang merusak berbagai sistem tubuh, terutama saraf dan pembuluh darah. Berdasarkan sumber dari WHO Jumlah penderita diabetes mengalami peningkatan drastis dari 200 juta pada tahun 1990 menjadi 830 juta pada tahun 2022, dengan prevalensi yang meningkat lebih cepat di negara-negara berpenghasilan rendah dan menengah dibandingkan negara berpenghasilan tinggi.

Pada tahun 2022, 14% orang dewasa berusia 18 tahun ke atas hidup dengan diabetes, meningkat dari 7% pada tahun 1990. Yang memprihatinkan, lebih dari setengah (59%) orang dewasa berusia 30 tahun ke atas yang hidup dengan diabetes tidak mengkonsumsi obat untuk kondisi mereka, dengan cakupan pengobatan terendah di negara-negara berpenghasilan rendah dan menengah. Diabetes secara langsung menyebabkan 1,6 juta kematian pada tahun 2021, dengan 47% kematian akibat diabetes terjadi sebelum usia 70 tahun. Selain itu, 530.000 kematian akibat penyakit ginjal disebabkan oleh diabetes, dan glukosa darah tinggi menyebabkan sekitar 11% kematian akibat penyakit kardiovaskular[1].

Proyek ini bertujuan untuk menciptakan sebuah platform berbasis web yang dapat mendeteksi tingkat diabetes pada pengguna (0.00 – 1.00) dengan pendekatan inovatif berbasis teknologi. Latar belakang proyek ini adalah :
- Peningkatan aksesibilitas layanan kesehatan melalui screening awal berbasis gejala.
- Penyediaan edukasi kesehatan inklusif, sehingga pengguna dapat memahami risiko diabetes mereka secara lebih baik.
- Pemanfaatan machine learning untuk memberikan analisis risiko yang akurat serta rekomendasi personal untuk mengurangi risiko diabetes[2].

### 1.2 Mengapa Masalah Ini Harus Diselesaikan?

- Sebagian besar sistem prediksi diabetes saat ini masih bersifat biner (ya/tidak), yang kurang informatif untuk tindakan pencegahan personal
- Pasien membutuhkan pemahaman tidak hanya mengenai risiko, tetapi juga mengapa mereka memiliki risiko tersebut (feature attribution).
- Rekomendasi gaya hidup yang generik sering kali tidak efektif; dibutuhkan pendekatan yang disesuaikan dengan karakteristik unik masing-masing individu.

### 1.3 Bagaimana Masalah Ini Harus Diselesaikan?

Solusi dikembangkan melalui pendekatan sebagai berikut:

- Model ANN digunakan untuk memetakan indikator kesehatan masyarakat (seperti BMI, tekanan darah, pola makan, aktivitas fisik) menjadi skor risiko diabetes kontinu.
- SHAP digunakan untuk mengidentifikasi fitur mana yang paling memengaruhi hasil prediksi, sehingga pengguna dapat melihat apa yang perlu diperbaiki.
- Hasil prediksi dan interpretasi SHAP diterjemahkan menjadi rekomendasi gaya hidup melalui Gemini API, yang memberikan saran dalam bentuk narasi alami dan mudah dipahami.

### 1.4 State of the Art Penelitian Sebelumnya

Penelitian terdahulu dalam prediksi diabetes banyak menggunakan pendekatan klasifikasi konvensional seperti Logistic Regression, SVM, dan Random Forest. Namun, hanya sedikit yang menggunakan prediksi probabilistik atau rentang risiko. Selain itu, pendekatan explainable AI seperti SHAP baru mulai banyak diadopsi, dan integrasi dengan LLM (seperti Gemini) untuk memberikan saran personal masih tergolong baru. Oleh karena itu, proyek ini bersifat inovatif karena menggabungkan:

- Prediksi risiko berbasis rentang dengan ANN.
- Penjelasan transparan menggunakan SHAP.
- Rekomendasi naratif berbasis LLM.

## 2. Business Understanding

### 2.1 Problem Statement

- Prediksi risiko diabetes secara biner (ya/tidak) tidak memberikan informasi mendalam bagi pengambilan keputusan preventif.
- Pasien dan tenaga kesehatan sering kali tidak memahami faktor utama yang menyebabkan risiko diabetes secara individual.
- Rekomendasi gaya hidup yang tersedia masih terlalu umum, tidak kontekstual dengan kondisi dan data kesehatan pengguna.

### 2.2 Goals

- Mengembangkan model prediksi risiko diabetes berbasis range probabilistik (0.00–1.00) menggunakan Artificial Neural Network (ANN).
- Menyediakan interpretasi yang transparan dan personal mengenai faktor risiko diabetes melalui SHAP.
- Menghasilkan rekomendasi gaya hidup yang spesifik, empatik, dan mudah dipahami dengan bantuan Gemini API.

### 2.3 Solution Statements

- Membangun dan melatih model ANN pada dataset indikator kesehatan masyarakat untuk memprediksi probabilitas diabetes secara kuantitatif.
- Mengintegrasikan SHAP untuk mengevaluasi kontribusi masing-masing fitur terhadap prediksi model, baik secara individu maupun populasi.
- Menyusun sistem otomatis yang menggabungkan hasil prediksi dan interpretasi ke dalam prompt untuk menghasilkan rekomendasi natural melalui Gemini API.

## 3. Data Understanding

### 3.1 Dataset Overview

| Jenis       | Keterangan                                                                 |
|-------------|----------------------------------------------------------------------------|
| Title       | Diabetes Health Indicators Dataset                                         |
| Source      | [Kaggle](https://www.kaggle.com/datasets/alexteboul/diabetes-health-indicators-dataset) |
| Maintainer  | [Alex Teboul](https://www.kaggle.com/alexteboul)                           |
| Visibility  | Publik                                                                     |
| Tags        | Diabetes, Kesehatan, Indikator, Nutrisi, Prediksi                         |

### 3.2 Data Description

| **Nama Kolom**            | **Tipe Data** | **Deskripsi**                                                                                   |
|---------------------------|---------------|--------------------------------------------------------------------------------------------------|
| `Diabetes_binary`         | Numerik       | Target variabel biner (1: memiliki diabetes, 0: tidak).                                          |
| `HighBP`                  | Numerik       | Riwayat tekanan darah tinggi (1: ya, 0: tidak).                                                  |
| `HighChol`                | Numerik       | Riwayat kadar kolesterol tinggi (1: ya, 0: tidak).                                               |
| `BMI`                     | Numerik       | Indeks Massa Tubuh, indikator umum obesitas yang berisiko terhadap diabetes.                    |
| `HeartDiseaseorAttack`   | Numerik       | Riwayat penyakit jantung atau serangan jantung (1: ya, 0: tidak).                                |
| `GenHlth`                 | Kategorikal   | Penilaian umum kesehatan oleh individu (skala 1–5; 1 = sangat baik, 5 = sangat buruk).           |
| `PhysHlth`                | Numerik       | Jumlah hari dalam 30 hari terakhir ketika kesehatan fisik kurang baik.                          |
| `DiffWalk`                | Numerik       | Kesulitan berjalan atau naik tangga (1: ya, 0: tidak).                                           |
| `Age`                     | Kategorikal   | Kategori usia (misal: 1 = 18–24, 2 = 25–29, ..., 13 = 80+).                                      |
| `Education`               | Kategorikal   | Tingkat pendidikan (1 = tidak tamat SD, 6 = sarjana atau lebih).                                 |
| `Income`                  | Kategorikal   | Tingkat pendapatan tahunan rumah tangga (1 = <\$10k, 8 = >\$75k).                               |

### 3.3 Struktur Data

- Jumlah data : 70,692 baris & 22 kolom
- Jumlah fitur: 22 (termaasuk target)
- Target: `Diabetes_binary` (0: tidak diabetes, 1: diabetes)
- Format: CSV
- Observasi: seimbang (balanced 50/50 split)

## 4. Data Preparation

- Seleksi fitur menggunakan `SelectKBest` dengan fungsi `f_classif`
![image](https://github.com/user-attachments/assets/2e892595-fb74-4956-830f-4b0f98ea07c1)
1. fitur `education` berdasarkan informasi dataset dengan referensi  BRFSS 2015
| Kode | Tingkat Pendidikan                                                                  |   |
| ---- | ----------------------------------------------------------------------------------- | - |
| 1    | Tidak menyelesaikan sekolah dasar (kurang dari kelas 9)                             |   |
| 2    | Menyelesaikan sekolah dasar (kelas 9–11, tanpa ijazah SMA)                          |   |
| 3    | Lulus SMA atau memiliki GED (General Educational Development)                       |   |
| 4    | Beberapa kuliah atau sekolah kejuruan, tanpa gelar                                  |   |
| 5    | Lulus dari perguruan tinggi dua tahun (Associate degree)                            |   |
| 6    | Lulus dari perguruan tinggi empat tahun atau lebih (Sarjana, Magister, atau Doktor) |   |
3. fitur `income` berdasarkan informasi dataset dengan referensi  BRFSS 2015 namun disesuaikan dengan demografis indonesia
| BRFSS Income Code | Kategori Sosial Ekonomi (Indonesia)     | Keterangan Lokal                            | Kode |
| ----------------- | --------------------------------------- | ------------------------------------------- |-------------------|
| 1 – 2             | **Rendah (Lower Class)**                | Rentan miskin, pekerjaan informal           | 1
| 3 – 5             | **Menengah (Middle Class)**             | Gaji UMR ke atas, pekerja tetap/karyawan    | 2
| 6 – 8             | **Tinggi (Upper-Middle to High Class)** | Profesional, pengusaha, ekspatriat, pejabat | 3
- Korelasi visual menggunakan heatmap seaborn
![image](https://github.com/user-attachments/assets/232e1ae5-719b-468a-934a-d51448044644)

- Pemisahan Data dan Standarisasi Data
![image](https://github.com/user-attachments/assets/f63c27e6-b2d5-403d-9d81-c1169a1e7f4f)


## 5. Modeling
![image](https://github.com/user-attachments/assets/0c3b18f1-0835-41ca-91e0-ca6ca83503ab)
Setiap model dilatih pada data latih dan dievaluasi pada data uji menggunakan metrik akurasi, precision, recall, dan F1-score. Model disimpan dengan nama model_diabetes.h5, scaler_diabetes.pkl, X_reference_scaled.pkl

### Fungsi Prediksi
![image](https://github.com/user-attachments/assets/21a8a20e-54ef-431f-91eb-241ae9b312ca)

### Fungsi SHAP ke Bahasa Alami
Mengubah nilai kontribusi fitur SHAP menjadi penjelasan bahasa manusia
![image](https://github.com/user-attachments/assets/9c0cb702-c69b-451b-aed9-4bfaa0e25e46)


## 6. Evaluation

Evaluasi dilakukan dengan menggunakan metrik klasifikasi:
- Confusion Matrix
![image](https://github.com/user-attachments/assets/8b50e70a-f548-4fd9-89db-eaaa3bf3ec63)
- Accuracy Score
![image](https://github.com/user-attachments/assets/a8d7f4ba-97ef-4102-828d-9caae91d38f2)
- AUC Score
![image](https://github.com/user-attachments/assets/703b1979-b58d-4059-96e9-e8f4f6d45372)


## 7. Kesimpulan

Proyek ini berhasil mengembangkan sistem prediksi risiko diabetes menggunakan model Artificial Neural Network (ANN) berbasis data indikator kesehatan. Model ini tidak hanya memberikan estimasi probabilitas risiko seseorang terkena diabetes, tetapi juga menginterpretasikan hasilnya dengan bantuan SHAP (SHapley Additive exPlanations) untuk menunjukkan kontribusi masing-masing fitur terhadap prediksi.

Selain itu, sistem ini diperkuat dengan integrasi Google Gemini API (Gemini) yang menghasilkan rekomendasi gaya hidup preventif dan adaptif berdasarkan input dan hasil prediksi model. Dengan pendekatan ini, pengguna tidak hanya menerima hasil klasifikasi, tetapi juga penjelasan dalam bahasa alami serta saran yang dapat diambil untuk mengurangi risiko kesehatan mereka secara personal.

Secara keseluruhan, proyek ini menyatukan tiga komponen penting:
- Prediksi medis berbasis machine learning (ANN)
- Penjelasan model (explainable AI) melalui SHAP
- Rekomendasi berbasis bahasa alami dengan bantuan model generatif (Gemini API)

Dengan kombinasi ini, sistem menjadi lebih responsif, dapat dijelaskan, dan bermanfaat langsung untuk pengambilan keputusan gaya hidup yang lebih sehat—khususnya bagi individu dengan risiko tinggi terhadap diabetes.

## 8. Kesimpulan Dampak terhadap Business Understanding

Penerapan model prediksi risiko diabetes berbasis Artificial Neural Network (ANN) yang dilengkapi dengan interpretasi SHAP dan rekomendasi gaya hidup berbasis Gemini API membawa dampak signifikan terhadap pemahaman dan pengambilan keputusan dalam konteks bisnis, khususnya di sektor kesehatan digital dan layanan preventif.

Dampak Utama terhadap Business Understanding:
1. Transformasi Data Menjadi Wawasan yang Dapat Ditindaklanjuti
Sistem ini mampu mengubah data indikator kesehatan mentah menjadi wawasan yang bermakna. Dengan penjelasan SHAP dan rekomendasi berbasis AI, pengguna tidak hanya tahu bahwa mereka berisiko, tetapi juga mengapa dan apa yang harus dilakukan. Hal ini meningkatkan nilai informasi dari sekadar klasifikasi menjadi pengetahuan yang actionable.

2. Peningkatan Kepercayaan dan Keterlibatan Pengguna
Penambahan elemen explainable AI (XAI) meningkatkan transparansi dan kepercayaan pengguna terhadap hasil prediksi. Rekomendasi gaya hidup yang disampaikan dalam bahasa alami memperkuat hubungan emosional dan keterlibatan pengguna terhadap sistem.

3. Potensi Monetisasi dan Integrasi dalam Ekosistem Kesehatan Digital
Model ini memiliki potensi tinggi untuk diintegrasikan dalam aplikasi layanan kesehatan digital, seperti telemedisin, asuransi kesehatan, atau platform wellness. Insight prediktif dan personalisasi gaya hidup dapat digunakan sebagai fitur premium atau sebagai dasar untuk pengambilan keputusan klinis, pemasaran produk kesehatan, atau pengelolaan risiko pasien.

## 9. Daftar Pustaka
- [1] Munir, M. M., Pujianto, A., Aulia, H., & Lamuru, M. (2023). Optimisasi Algoritma Genetika dengan Particle Swarm Optimization (PSO) untuk Sistem Rekomendasi Diet Gizi bagi Penderita Diabetes. *Jurnal RESTIA*, 1(2), 38–48. [https://doi.org/10.30787/restia.v1i2.1289](https://doi.org/10.30787/restia.v1i2.1289)
- [2] Kaggle Dataset: [Diabetes Health Indicators Dataset](https://www.kaggle.com/datasets/alexteboul/diabetes-health-indicators-dataset)
