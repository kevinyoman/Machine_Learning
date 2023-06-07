
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
emiliki makna)
- Satu kalimat terdiri dari beberapa kata yang jumlahnya berbeda-beda tiap kalimat.
- Adanya *typo* (salah ketik), penyingkatan kata (you menjadi u), ataupun simbol-simbol tidak bermakna sehingga perlu dilakukan cleansing.
- Adanya perbedaan bahasa yang digunakan sehingga perlu mencari kosa kata yang cocok.

## Data Cleaning

Beberapa proses data cleaning yang umum dilakukan antara lain:

- Case-folding -> Untuk mengubah huruf kapital menjadi huruf kecil
- Remove numbers -> Menghilangkan angka
- Remove stopwords -> Menghilangkan kata sambung
- Remove punctuation -> Menghilangkan tanda baca
- Stemming -> Mengembalikan sebuah kata ke kata dasar
- Remove white space -> Untuk menghilangkan spasi berlebih

## Additional Note: Kevin

1. FUN: content_transformer()
dipakai bila menggunakan function diluar library `tm`

e.g. tm_map(x = sms.corpus, 
                     FUN = content_transformer(tolower))
                     
2. remove tanda \\ dan " menggunakan fungsi custom transformer
sms.corpus <- tm_map(sms.corpus, transformer, "\\\\")
sms.corpus <- tm_map(sms.corpus, transformer, "\\\"")

3. remove slang words, pakai library `textclean`
contoh https://askalgo.netlify.app/#text-cleansing

4. ROC / AUC hanya untuk target variable binary class
bila multi class, bisa menggunakan F-1 score

5. Cara menggunakan SMOTE: https://rpubs.com/VicNP/UBL-SmoteClassif
* select multiple: alt+shift+ bawah
* copas: alt+shift+ bawah / ctrl+shift+D

6. upsampling / downsampling hanya untuk data train saja

# 7. zoom out plot dt: 
# fig.width=12
# plot(model_dt, type="simple") 
```