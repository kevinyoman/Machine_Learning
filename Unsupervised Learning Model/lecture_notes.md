---
title: "Summary UL"
output: html_notebook
---

# Summary Day 1

**Supervised vs Unsupervised**

1. Ciri dari metode Supervised:
- Memiliki target variabel.
- Model dapat dievaluasi dengan data test.
- Digunakan untuk menyelesaikan permasalahan regresi dan klasifikasi.

2. Ciri dari metode Unsupervised?
- Tidak memiliki target variabel.
- Model tidak dapat dilakukan evaluasi, karena tidak memiliki "ground truth" atau label aktual.
- Digunakan untuk mengidentifikasi kemungkinan untuk melakukan reduksi dimensi, clustering, atau untuk menemukan pola anomali atau yang tidak sesuai dengan data/pengamatan lainnya.

Note:
- Digunakan pada tahap Pre-processing maupun Exploratory Data Analysis (EDA)
karena berkaitan terutama dengan identifikasi pola pada data.

**Dimensionality Reduction dengan PCA**

3. Dimensionality Reduction adalah metode yang bertujuan untuk mereduksi/mengurangi jumlah dimensi pada data, tapi mempertahankan informasi sebanyak mungkin.
- Banyaknya jumlah PC/sumbu baru yang terbentuk sama dengan jumlah dimensi/kolom/fitur/variabel data awal. Misalnya: Kita memiliki 5 kolom di data awal, maka jumlah sumbu baru/PC yang terbentuk jumlahnya 5 -> PC1, PC2, PC3, PC4, dan PC5.
- PC1 **pasti** menangkap variance/keberagaman data yang lebih besar dibandingkan PC2, PC3, dst. PC1 > PC2 > PC3 > DST.
- Antara PC1 dan PC2 saling tegak lurus, artinya tidak berkorelasi.
- Metode PCA akan cocok untuk data numerik yang saling berkorelasi (multicollinearity).
- PCA baik digunakan untuk tipe data numerik yang saling berkorelasi, dan akan menghasilkan nilai PC yang saling tidak berkorelasi

Keunggulan menggunakan metode PCA:

- Beban komputasi apabila dilakukan pemodelan relatif lebih rendah.
- Bisa menjadi salah satu teknik untuk improve model, namun tidak selalu menjadi lebih baik.
- Mengurangi resiko terjadinya multikolinearitas, karena nilai antar PC sudah tidak saling berkorelasi.

Kelemahan dari PCA:
- Model sulit diinterpretasikan, karena nilai PC merupakan campuran dari beberapa variabel.

**PCA Workflow**

1. Business question
2. Read data
3. Data cleansing: menyesuaikan tipe data, cek dan handle NA
4. EDA: cek satuan data
5. Preprocessing: scaling apabila satuan berbeda
6. PCA dengan `prcomp()`
7. Reduksi dimensi: menentukan berapa PC yang sebaiknya digunakan dengan melihat cumulative proportion pada `summary(pca_object)` (untuk fungsi `prcomp()`).
8. Pemilihan PC dapat digunakan untuk analisis selanjutnya, misal untuk supervised learning ataupun visualisasi.


# Summary Day 2

**Biplot**

1. Untuk melakukan visualisasi high-dimensional data dari PCA dapat menggunakan visualisasi **biplot**.

Visualisasi menggunakan **biplot** dapat yang menampilkan  **Individual factor map** dan **Variables factor map**.

2. Tujuan dari Individual Factor Map adalah sebagai berikut:

- Observasi data yang outliers (jauh dari gerombolan data).
- Mengetahui observasi mana saja yang mirip.

3. Tujuan dari Variables Factor Map adalah sebagai berikut:

- Untuk melihat kontribusi tiap variable ke PCnya, panjangnya menggambarkan besar kontribusi.
- Melihat korelasi antara variabel.
- Melihat hubungan observasi terhadap variabel. Observasi yang searah panah dan letaknya jauh dari pusat data (titik nol) maka memiliki nilai yang besar di variable panah tersebut. Sedangkan, Observasi yang berlawanan arah panah, maka nilainya kecil di variable tersebut.

4. Dilihat dari sudut antar panah kita dapat mengetahui korelasi antar variable, berikut adalah pertanyaan yang benar, kecuali:
- < 90 derajat = berkorelasi positif
- 90 derajat = tidak berkorelasi
- > 90 atau mendekati 180 derajat = berkorelasi negatif

**Fungsi-fungsi pada topik PCA**
- `prcomp()`: membuat objek PCA dengan base R
- `biplot(prcomp())`: membuat biplot dengan base R
- `PCA()`: membuat objek PCA dari package `FactoMineR`
- `plot.PCA()`: membuat biplot dari object `PCA()`:
  + `choix = "ind"`: visualisasi sebaran data (individual factor map), terdapat parameter `habillage` untuk mewarnai observasi berdasarkan index kolom
  + `choix = "var"`: visualisasi variable factor map (panah)
- `fviz_contrib()`: melihat urutan kontribusi tiap variable ke tiap PC, dari package `factoextra`
- `dimdesc()`: dimension description, untuk melihat kontribusi variable ke tiap PC

# Summary Day 3

* Clustering: pengelompokan data berdasarkan karakteristiknya

* Algotima: k-mean clustering, punya titik pusat cluster (centroid)

* Proses k-means: 
  - Step 1: iterasi dari random inizialitation
  - Step 2: cluster assignment
  - Step 3: cluster update sampai cluster stabil

* Kriteria clustering yang "baik":
  - Within sum of squares mendekati nilai 0 (sekecil mungkin)
  - Rasio between sum of squares dengan total sum of squares mendekati nilai 1

* Memilih k optimum:
  - Kebutuhan bisnis
  - Elbow method
	~ Fungsi `fviz_nbclust()`
	~ Parameter x (data yang digunakan), FUNcluster (metode clustering yang digunakan), method (perhitungan nilai wss)

* Clustering - K-Means

Kita bisa melakukan K-means Clustering menggunakan fungsi `kmeans()`.

Parameter:
  - `x`: dataset
  - `centers`: banyaknya centroid (nilai k)














