# Laporan Proyek Machine Learning - Surya Yusuf Nugroho

## Domain Proyek

Diabetes merupakan penyakit kronis yang mempengaruhi cara tubuh memproses gula darah (glukosa). Ada dua jenis utama diabetes, yaitu diabetes tipe 1 dan diabetes tipe 2. Diabetes tipe 2 adalah bentuk yang lebih umum, di mana tubuh tidak dapat menggunakan insulin dengan efektif, atau tidak cukup memproduksi insulin. Hal ini dapat menyebabkan kadar glukosa darah tinggi yang berbahaya. Untuk menangani masalah ini, deteksi dini diabetes sangat penting untuk mengurangi risiko komplikasi jangka panjang, seperti penyakit jantung, stroke, dan gangren. Oleh karena itu, klasifikasi diabetes berdasarkan data medis menjadi langkah penting dalam mengurangi dampak penyakit ini.

Sumber referensi:  
- [World Health Organization (WHO) - Diabetes Fact Sheet](http://who.int/news-room/fact-sheets/detail/diabetes)  
- [NHLBI - What is Diabetes? Fact Sheet](https://www.nhlbi.nih.gov/resources/what-diabetes-fact-sheet)

## Business Understanding

### Problem Statements

- Bagaimana cara mendeteksi pasien yang berisiko tinggi mengidap diabetes berdasarkan data medis?
- Bagaimana kita bisa menggunakan model machine learning untuk memprediksi kemungkinan seseorang mengidap diabetes?

### Goals

- Membangun model machine learning yang dapat mengklasifikasikan apakah seseorang mengidap diabetes atau tidak berdasarkan data medis.
- Meningkatkan akurasi prediksi dengan model yang terlatih.

### Solution Statements

- Menggunakan algoritma klasifikasi seperti Logistic Regression, Decision Tree, atau Random Forest untuk membangun model prediksi.
- Melakukan hyperparameter tuning untuk meningkatkan kinerja model dan akurasi prediksi.

## Data Understanding

Dataset yang digunakan dalam proyek ini adalah dataset diabetes yang memuat informasi medis pasien, termasuk beberapa parameter penting seperti kadar glukosa, tekanan darah, BMI, dan lainnya. Dataset ini mengandung data tentang apakah seseorang mengidap diabetes (Outcome 1) atau tidak (Outcome 0).

Link dataset: [Diabetes Dataset](https://www.kaggle.com/datasets/whenamancodes/predict-diabities)

### Variabel-variabel pada dataset adalah sebagai berikut:
| Kolom                        | Deskripsi                                                           |
| ---------------------------- | ------------------------------------------------------------------- |
| **Pregnancies**              | Jumlah kehamilan yang pernah dialami                                |
| **Glucose**                  | Tingkat glukosa dalam darah                                         |
| **BloodPressure**            | Tekanan darah (dalam mm Hg)                                         |
| **SkinThickness**            | Ketebalan lipatan kulit (dalam mm)                                  |
| **Insulin**                  | Kadar insulin dalam darah (dalam mu U/ml)                           |
| **BMI**                      | Indeks massa tubuh (Body Mass Index)                                |
| **DiabetesPedigreeFunction** | Skor riwayat keturunan diabetes                                     |
| **Age**                      | Usia pasien (dalam tahun)                                           |
| **Outcome**                  | Hasil diagnosa (1 = Mengidap diabetes, 0 = Tidak mengidap diabetes) |

## Data Preparation

Pada tahap ini, data yang digunakan telah diproses melalui beberapa tahapan, termasuk:
- Mengatasi nilai yang hilang (missing values).
- Melakukan normalisasi pada beberapa fitur numerik seperti Glucose, BloodPressure, BMI, dll.
- Pembagian data menjadi set pelatihan (training set) dan set pengujian (test set).

## Modeling

Model machine learning yang digunakan pada proyek ini adalah Random Forest, yang merupakan algoritma ensemble yang kuat untuk masalah klasifikasi. Beberapa parameter yang digunakan dalam pembuatan model antara lain jumlah pohon keputusan (n_estimators) dan kedalaman pohon (max_depth).

### Hasil Model:
- **Train Accuracy Score**: 98.70%
- **Test Accuracy Score**: 75.32%

## Evaluation

Metrik yang digunakan untuk mengevaluasi model adalah **Akurasi**. Berdasarkan hasil evaluasi model, model menunjukkan hasil yang baik pada data pelatihan, tetapi performanya sedikit menurun pada data pengujian. 

- **Akurasi Pelatihan**: 98.70%
- **Akurasi Pengujian**: 75.32%

Namun, meskipun model menunjukkan akurasi yang cukup tinggi pada data pelatihan, model perlu disesuaikan lebih lanjut untuk meningkatkan hasil pada data pengujian.

## Kesimpulan

Berdasarkan hasil evaluasi model, model ini cukup baik dalam memprediksi diabetes pada dataset ini. Namun, ada ruang untuk perbaikan dalam hal generalisasi pada data yang lebih luas atau data yang belum pernah dilihat sebelumnya.

