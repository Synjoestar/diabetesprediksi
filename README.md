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
*Data preparation* adalah proses mempersiapkan data mentah menjadi format yang sesuai untuk analisis atau pemrosesan lebih lanjut. Berikut adalah beberapa teknik atau metode yang digunakan dalam persiapan data pada proyek ini:

1. **Handling missing value** 
	- *Missing value* merupakan salah satu masalah yang paling sering dijumpai dalam proyek analisis data di industri. Masalah ini muncul karena adanya nilai yang hilang dari sebuah data dan biasanya direpresentasikan sebagai nilai NaN dalam library pandas. Hal ini biasanya terjadi karena adanya *human error*, masalah privasi, proses *merging/join*, dll. 
	- Tujuan dari langkah ini adalah untuk memastikan keakuratan dan keandalan data yang digunakan untuk analisis atau pemodelan. *Missing value* dapat menyebabkan bias dan kesalahan dalam analisis data, sehingga penting untuk mengidentifikasi dan mengatasi nilai yang hilang ini agar hasil analisis menjadi lebih akurat dan dapat diandalkan.
	- Terdapat beberapa cara atau metode yang dapat digunakan  untuk menangani *missing value*, yaitu *Dropping*, *Imputation*, *Interpolation*, dan lainnya. 
		
2. **Handling duplicated data**
	- *Duplicated data* adalah masalah lain yang umum dijumpai di industri. Ia terjadi ketika terdapat sebuah observasi (semua nilai dalam satu unit baris) yang memiliki nilai yang sama persis pada setiap kolomnya. 
	-  Tujuan dari langkah ini adalah untuk memastikan integritas data. *Duplicated data* dapat mempengaruhi analisis data dan membuat hasil yang tidak akurat. Oleh karena itu, dengan mengidentifikasi dan menghapus data yang terduplikat, dapat memastikan bahwa data yang digunakan untuk analisis atau pemodelan adalah data yang valid dan representatif.
	-  Salah satu teknik yang dapat digunakan dalam mengatasi *duplicated data* adalah dengan menghapus data yang terduplikat (*dropping*).

3. **Handling outliers**
	- *Outliers* adalah nilai yang jauh berbeda dari nilai lainnya dalam kumpulan data. Nilai ini muncul sebagai pengecualian dalam pola data yang ada. Nilai yang ada di *outlier* bisa jauh lebih tinggi maupun lebih rendah dibandingkan dengan nilai-nilai lain dalam dataset. Outlier bisa terjadi karena berbagai alasan, termasuk kesalahan pengukuran, kejadian langka, atau karena faktor lain yang tidak terduga. 
	- Tujuan dari langkah ini  adalah untuk memastikan bahwa *outlier* tidak mempengaruhi analisis statistik yang dilakukan atau model machine learning yang dibangun. Outliers memiliki potensi untuk memberikan informasi yang salah atau mengganggu hasil analisis, sehingga penting untuk mengatasi mereka agar hasil analisis menjadi lebih akurat dan dapat dipercaya.
	- Terdapat beberapa cara atau langkah yang dapat diterapkan dalam menangani outliers, yaitu meliputi identifikasi *outliers*, transformasi data, menghapus *outliers*, dan *imputation*. Pada proyek ini penanganan *outliers* dilakukan dengan menggunakan metode *imputation*, dengan menggunakan *IQR method*. Hasil dari metode *imputation* pada proyek ini  dapat dilihat pada gambar 5 berikut : 

		

4. **Standardization**
	- Standardisasi adalah proses mengubah data sehingga memiliki rata-rata (*mean*) nol dan varians (*variance*) satu. 
	-  Tujuan dari standardisasi adalah untuk membuat distribusi data lebih terpusat di sekitar nilai nol dengan variabilitas yang seragam, yang dapat membantu algoritma machine learning memahami dan memproses data dengan lebih baik.
	-  Teknik yang digunakan adalah dengan mengurangi nilai setiap fitur dengan rerata dari fitur tersebut, dan kemudian membaginya dengan standar deviasi dari fitur tersebut. Dalam kasus ini, *StandardScaler scikit-learn* digunakan untuk menstandarisasi *skor z*.

5. **Handling imbalanced data**
	- *Imbalanced data* merupakan sebuah kondisi di mana distribusi dari kelas yang terdapat pada dataset tidak seimbang jumlahnya. 
	- Tujuan dari menangani imbalanced data adalah untuk meningkatkan performa model dalam memprediksi kelas minoritas.
	- Terdapat beberapa cara atau metode yang dapat digunakan untuk menangani *imbalanced data*. Pertama, *oversampling* yaitu memperbanyak sampel dari kelas minoritas sehingga jumlahnya seimbang dengan kelas mayoritas. Ini dapat dilakukan dengan menggandakan sampel yang ada atau dengan membuat sampel sintetis baru. Cara lainnya, *undersampling* yaitu mengurangi jumlah sampel dari kelas mayoritas sehingga jumlahnya seimbang dengan kelas minoritas. Ini dapat dilakukan dengan menghapus sebagian sampel dari kelas mayoritas. Pada proyek ini penanganan *imbalanced data* dilakukan dengan metode *SMOTE* (*Synthetic Minority Over-sampling Technique*): *SMOTE* digunakan untuk membuat sampel sintetis dari kelas minoritas (dalam hal ini, kelas "1" dari kolom '*Outcome*') sehingga jumlahnya seimbang dengan kelas mayoritas. Hal ini membantu mencegah bias pada model machine learning ke kelas mayoritas dan meningkatkan kinerja model untuk kelas minoritas.  

	

6. **Data Splitting**
	- Data Splitting  adalah proses membagi *dataset* menjadi dua atau lebih bagian yang berbeda untuk digunakan dalam tahapan tertentu dari proses analisis data, seperti pelatihan model, validasi model, dan pengujian model.	
	- Tujuan dari langkah ini adalah pembagian data menjadi menjadi dua bagian: satu untuk melatih model (set pelatihan) dan yang lainnya untuk menguji model (set pengujian).
	-  Teknik yang digunakan adalah dengan menggunakan metode *Train-test split*.

## Modeling

Pada proyek ini algoritma machine learning yang digunakan di antaranya yaitu *`Random forest classification`* dan *`Hyperparameter Tuning Grid Search`.*

### Random Forest Classification
*Random Forest Classification* termasuk algoritma *supervised learning* yang dapat digunakan untuk permasalahan *classification*. *Random forest* termasuk dalam salah satu kategori *ensemble* (group) *learning*, yang terdiri dari banyak pohon keputusan (*decision* *tree*) yang bekerja bersama untuk meningkatkan kinerja dan akurasi prediksi. Pada model *machine learning ensemble*, setiap model harus membuat prediksi secara independen. Kemudian, prediksi dari setiap *model ensemble* ini digabungkan untuk membuat prediksi akhir. *Algoritma Random Forest* mengkombinasikan hasil prediksi dari berbagai *model decision tree* yang dibuat secara acak. 


  
**Kelebihan** : 
- *Random forest* merupakan algoritma yang sering digunakan karena cukup sederhana tetapi memiliki stabilitas yang mumpuni.
- Random forest dapat mencegah terjadinya *overfitting* apabila dibandingkan dengan *algoritma Decision Tree*. Selain itu, algoritma ini dapat menangani dataset besar dengan banyak fitur. 

**Kekurangan** : 
- *Random Forest* memerlukan waktu pelatihan yang lebih lama dibanding *Decision Tree* karena kompleksitas modelnya

### Implementasi  
Proses modelling menggunakan algoritma *Random Forest* pada proyek ini (permasalahan klasifikasi) menggunakan *`RandomForestClassifier()`* yang telah disediakan oleh *scikit learn*. Pada proyek ini parameter yang digunakan yaitu *`n_estimators=50`*, *`max_depth=5`*, dan *`max_features='auto`*. *`n_estimators`* adalah *hyperparameter* yang menentukan jumlah pohon (*trees*) yang digunakan dalam *random forest*, pada proyek ini *`n_estimators`* yang digunakan yaitu 50. Parameter selanjutnya adalah *`max_depth`*, yang merupakan kedalaman atau panjang pohon. Parameter ini merupakan ukuran seberapa banyak pohon dapat membelah (*splitting*) untuk membagi setiap node ke dalam jumlah pengamatan yang diinginkan. Pada proyeki ini *`max_depth`* yang digunakan adalah 5. Parameter selanjutnya adalah *`max_features`*, yaitu *hyperparameter* yang mengatur jumlah maksimum *feature* yang digunakan untuk mencari percabangan terbaik. Pada proyek ini, *`max_features`* yang digunakan adalah auto.

###  Hyperparameter Tuning
*Hyperparameters* digunakan untuk meng-*custom* model dan mengontrol proses *training* sesuai dengan *dataset* atau permasalahan yang ingin diselesaikan. Sementara *hyperparameter* *tuning* dilakukan dengan tujuan untuk memperoleh konfigurasi yang paling optimal untuk melatih model *machine* *learning*. Pada praktiknya, proses *hyperparameter* *tuning* ini dapat dijalankan secara manual dengan mencoba berbagai konfigurasi *hyperparameter* yang ada hingga diperoleh konfigurasi yang paling optimal. Cara lainnya yaitu dengan melakukan *hyperparameter tuning* secara otomatis dengan bantuan beberapa algoritma salah satunya adalah *grid search*. 

*Grid search* merupakan algoritma yang dapat digunakan untuk melakukan proses *hyperparameter tuning* secara otomatis. Pada prosesnya, algoritma ini akan membuat sebuah *_n-dimensional search space_* yang terbentuk dari n *hyperparameter* dari sebuah model. Setiap titik yang terdapat pada *search space* mewakili satu konfigurasi atau perpaduan dari n *hyperparameter*. Algoritma ini bekerja dengan mengevaluasi setiap titik yang terdapat dalam search space untuk memperoleh konfigurasi *hyperparameter* yang paling optimal.

Pada proyek ini akan dilakukan *Hyperparameter Tuning* dengan *Grid Search* untuk meningkatkan performa dari model *Random Forest* yang telah dikembangkan sebelumnya. Parameter yang digunakan pada *Hyperparamter Tuning* adalah sebagai berikut : 
-   *random_state*: digunakan untuk mengontrol *random number generator* yang digunakan oleh model.
-   *max_depth*: *hyperparameter* yang mengatur kedalaman atau panjang pohon keputusan.
-   *max_features*:  *hyperparameter* yang mengatur jumlah *maksimum feature* yang digunakan untuk mencari percabangan terbaik.
-   *criterion*: metrik yang digunakan untuk mengukur kualitas dari sebuah percabangan.
-   *n_estimators*:  *hyperparameter* yang menentukan jumlah *trees* (pohon) yang digunakan dalam algoritma *random forest*.
 
 Berdasarkan *Hyperparameters Tuning* dengan *Grid Search* yang telah dilakukan, maka dapat diketahui *best parameter* yang dapat digunakan pada model *Random Forest* untuk meningkatkan performa model. Paramter yang digunakan tersebut di antaranya `criterion : gini`; `max_depth : 8`; `max_features : auto`; dan `n_estimators : 50`. 
 
### Pemilihan model : 
Berdasarkan eksperimen yang telah dilakukan pada tahapan pengembangan model, diperoleh model machine learning terbaik yaitu *Random Forest Classification* dengan *Hyperparameter Tuning Grid Search*. Hal ini berdasarkan hasil dari *confussion matrix* dan *classification report* yang menunjukkan bahwa hasil dari model ini lebih baik dari hasil model *Random Forest Classification* yang tidak menerapkan *hyperparameter tuning*. Sehingga hasil dari model *machine learing* yang dikembangkan telah memenuhi tujuan dari *solution statements* yang telah ditentukan sebelumnya. 

## Evaluation

Pada proyek machine learning ini evaluasi model akan menggunakan **confusion matrix**. Confusion matrix memberi gambaran bagaimana performa model pada berbagai kelas. Ia menunjukkan berapa banyak jumlah prediksi yang benar (True) dan salah (False) untuk setiap label.

Dengan menggunakan confusion matrix, maka dapat diketahui seberapa baik performa dari model machine learning yang dikembangkan. Hasil dari confusion matrix ini akan digunakan untuk menghitung berbagai metrik lainnya, seperti accuracy, precision, recall, dan F1-score.

- **Accuracy** — metrik evaluasi yang mengukur seberapa baik model membuat prediksi yang benar dari total prediksi yang dilakukan.
- **Precision** — metrik evaluasi yang digunakan untuk mengukur berapa banyak model menghasilkan prediksi yang benar untuk suatu kelas tertentu. Precision didefinisikan sebagai perbandingan antara jumlah hasil prediksi yang benar untuk kelas tertentu dengan jumlah total prediksi untuk kelas tersebut.
- **Recall** — metrik yang digunakan untuk mengukur seberapa baik model dalam memprediksi suatu kelas tertentu. Recall didefinisikan sebagai perbandingan antara jumlah hasil prediksi yang benar untuk kelas tertentu dengan jumlah total sampel pada kelas tersebut.
- **F1-score** — merupakan kombinasi antara nilai precision dan recall dari suatu kelas tertentu.

Berdasarkan dengan konteks data, problem statement, dan solusi yang diimplementasikan, metrik evaluasi yang akan digunakan pada proyek machine learning ini adalah **Recall**. Recall adalah metrik yang digunakan untuk mengukur seberapa baik model dalam memprediksi suatu kelas tertentu. Recall dipilih dengan alasan bahwa algoritma machine learning / model memprediksi seseorang mengalami diabetes tetapi sebenarnya non-diabetes, daripada model salah memprediksi bahwa seseorang non-diabetes padahal sebenarnya dia adalah penderita diabetes.

### 🏋️‍♂️ Training Set Performance
**Accuracy Score:** 98.70%

**Classification Report:**
```
              precision    recall  f1-score   support

           0       0.98      1.00      0.99       349
           1       1.00      0.96      0.98       188

    accuracy                           0.99       537
   macro avg       0.99      0.98      0.99       537
weighted avg       0.99      0.99      0.99       537
```

---

### 🧪 Test Set Performance
**Accuracy Score:** 75.32%

**Classification Report:**
```
              precision    recall  f1-score   support

           0       0.82      0.79      0.81       151
           1       0.64      0.68      0.65        80

    accuracy                           0.75       231
   macro avg       0.73      0.73      0.73       231
weighted avg       0.76      0.75      0.75       231
```
