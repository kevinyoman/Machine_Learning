
# Naive Bayes Classifier

- Naive Bayes adalah model machine learning yang memanfaatkan Bayes' Theorem dalam melakukan klasifikasi.
- Hubungan antara prediktor dengan target variabel dianggap saling dependen.
- Dikatakan "Naive" karena tiap prediktor diasumsikan saling **independent** (tidak berhubungan satu sama lain) dan **memiliki bobot yang sama** (memiliki kepentingan atau pengaruh yang sama) dalam melakukan prediksi. Hal ini untuk memudahkan kalkulasi (rumus menjadi lebih simpel) dan mengurangi beban komputasi.

## Laplace Smoothing
Dari keterbatasannya Naive Bayes “skewness due to scarcity”, ada beberapa pendekatan yang dapat dilakukan yaitu:

1. Membuang prediktor yang mengandung scarcity
resiko : Jika prediktor secara business sense sangat berpengaruh, maka kita akan kehilangan prediktor tersebut

2. Melakukan laplace smoothing -> menambahkan semua frekuensi data pada prediktor dengan angka tertentu (biasanya 1)

## Pemodelan Naive Bayes

1. Model Fitting / Training
- Dapat dilakukan dengan fungsi `naiveBayes()`
- Model fitting menggunakan data training

2. Predict data
- Dapat dilakukan dengan fungsi `predict()`
- Predicting dijalankan pada data testing

# Text Mining

Text Mining adalah salah satu metode analisis data yang fokus utamanya adalah mencari informasi dan pola-pola dari data yang **tidak terstruktur, yaitu data teks**. Data teks disebut tidak terstruktur karena:

- Satu kalimat terdiri dari beberapa kata yang jumlahnya berbeda-beda.
- Adanya *typo* (salah ketik), penyingkatan kata (you menjadi u), ataupun simbol-simbol tidak bermakna sehingga perlu dilakukan cleansing.
- Adanya perbedaan bahasa yang digunakan.

Langkah-langkah text mining dengan library `tm`: 

Step 1. Mengubah data text menjadi corpus 
  * library `tm` hanya menerima bentuk corpus untuk pengolahan datanya

Step 2. Data cleaning 
  * Proses penyeragaman setiap kata yang terdapat pada data kita, dengan tujuan untuk membuat format yang dimengerti oleh model kita

Step 3. Mengubah corpus menjadi documentTermMatrix (tokenizing)
  * Tahapan membuat data menjadi `Document Term Matrix` adalah tahapan untuk memecah setiap unik kata yang terdapat pada kalimat pada data teks kita, sehingga setiap kata tersebut menjadi kolom ataupun variabel.
  
Step 4. Menghilangkan infrequent words
  * Menentukan berapa banyak kata yang dianggap penting dengan melihat jumlah kemunculannya pada keseluruhan observasi data kita

Step 5. Bernoulli Converter
  * Mengubah jumlah frekuensi kemunculan menjadi 1 (jika pernah muncul) dan 0 (tidak muncul)

Step 6. Data Splitting (cross-validation)

Step 7. Model fitting / training

Step 8. Model evaluation

## Fungsi Data Cleaning

Beberapa proses data cleaning yang umum dilakukan antara lain:

- Case-folding -> Untuk mengubah huruf kapital menjadi huruf kecil
  * Syntax: `tm_map(x = data.corpus, FUN = content_transformer(tolower))`

- Remove numbers -> Menghilangkan angka
  * Syntax: `tm_map(x = data.corpus, FUN = removeNumbers)`

- Remove stopwords -> Menghilangkan kata sambung
  * Syntax: `tm_map(x = sms.corpus, FUN = removeWords, stopwords("english"))`

- Remove punctuation -> Menghilangkan tanda baca
  * Untuk menghilangkan tanda baca kita bisa menggunakan fungsi DIY yang sudah disediakan dan menerapkannya ke syntax, seperti di bawah ini.
  * Syntax: `tm_map(data.corpus, fungsi DIY, "simbol")`

- Stemming -> Mengembalikan sebuah kata ke kata dasar
  * Syntax: `tm_map(x = data.corpus, FUN = stemDocument)`

- Remove white space -> Untuk menghilangkan spasi berlebih
  * Syntax: `tm_map(x = sms.corpus, FUN = stripWhitespace)`

# ROC-AUC untuk model evaluation

- ROC (Receiver-Operating Curve) dan AUC (Area Under Curve) sebagai alat evaluasi tambahan selain confusion matrix.
- ROC menggambarkan True Positive Rate (Recall) vs False Positive Rate. Kurva yang baik adalah kurva yang mendekati pojok kiri atas (Recall = 1, FPR = 0).
- AUC adalah luas area di bawah kurva ROC. Semakin mendekati nilai 1, model semakin baik dalam memisahkan kelas positif dan negatif.

# Data Manipulation

-**upsample**: menduplikat kelas minoritas hingga seimbang dengan mayoritas

* Kita bisa menggunakan *UpSample* ketika data kita tidak terlalu banyak

Contoh: kita hanya memiliki 1000 observasi

- Kelas mayoritasnya 900 obs
- Kelas minoritasnya 100 obs -> datanya akan ditambah 800
- Sehingga total data kita menjadi 1800

- **downsample**: mengurangi kelas mayoritas hingga seimbang dengan minoritas

* Kita bisa menggunakan *DownSample* ketika data kita banyak

Contoh: kita memiliki 1juta observasi

- Kelas mayoritasnya 850rb obs -> akan direduksi menjadi 150rb
- Kelas minoritas 150rb obs

* Metode *SMOTE* -> intuisu dari metode itu -+ sama dengan *UpSample*

Ref SMOTE: https://rpubs.com/VicNP/UBL-SmoteClassif

# Decision Tree

Struktur Decision Tree:
- **Root Node**: Percabangan pertama dalam menentukan nilai target, biasa disebut sebagai predictor utama.
- **Interior Node**: Percabangan selanjutnya yang menggunakan predictor lain apabila root node tidak cukup dalam menentukan target.
- **Terminal/Leaf Node**: Keputusan akhir berupa nilai target yang diprediksi.

Decision Tree membuat sebuah pohon keputusan dengan memilih prediktor yang menghasilkan splitting data yang homogen atau **entropy**nya kecil Dengan kata lain, prediktor tersebut menghasilkan **information gain** yang besar.

**Note**: Decision Tree tidak hanya terbatas pada kasus Classification, namun dapat digunakan pada kasus Regression.















