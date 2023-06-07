# Lecture Notes Regression Model

* Machine Learning adalah **mesin yang dapat belajar sendiri** dalam memahami pola data hingga mengestimasi apa yang akan terjadi di masa depan.

Kategori pada Machine Learning:

1. **Supervised learning** : memiliki target variabel (y). 
  - Regression : target variabelnya numerik
  - Classification : target variabel kategorik
    
2. **Unsupervised Learning** : tidak memiliki target variabel (y)

* Dalam model regresi linear sederhana, kita akan melakukan prediksi variabel target melalui persamaan:

$$\hat{y}=\beta_0 + \beta_1*x_1$$

* Nilai $\beta_0$ dan $\beta_1$ akan dicari menggunakan **Ordinary Least Square (OLS)** yaitu dengan mencari koefisien tersebut sedemikian sehingga model akan menghasilkan nilai *Sum of Square* (SSE) yang minimun.

$$ SSE = \Sigma{(y-\hat{y})^2} $$

* Workflow membangun model regresi :

  1. Rumuskan business question (Definisikan target dan prediktor)

  2. Read data dan lakukan Exploratory Data Analysis (EDA):
      - Deteksi outlier, karena outlier bisa mempengaruhi performa model.
      - Cek korelasi antara target dengan prediktor. Korelasi yang kuat menjadi prediktor potensial
  
  3. Modeling: `model <- lm(formula, data)`
      - Tanpa prediktor: `formula = target ~ 1`
      - Simple linear regression (satu prediktor): `formula = target ~ predictor`

  4. Interpretasi model: `summary(model)`
     Beberapa nilai yang bisa diperhatikan:
     - **Intercept**: titik awal garis regresi terbentuk, menunjukkan nilai target ketika nilai prediktor = 0
   
     - **Coefficient/Slope**: kenaikan variable target setiap 1 satuan
       + Koefisien positif = korelasi positif, meningkatkan nilai variable target
       + Koefisien negatif = korelasi negatif, menurunkan nilai variable target
  
     - **Signifikansi prediktor**: mengetahui apakah setiap prediktor berpengaruh signifikan terhadap variable targetnya.
      + Sebuah prediktor dikatakan signifikan ketika p-value < 0.05 (alpha)
      + Bisa juga dilihat dari jumlah bintang setiap prediktor
  
     - **R-squared**: ukuran **kebaikan model**. Seberapa baik model dapat menjelaskan target. 
      + rentang nilai 0-1, mendekati 1 semakin baik
  
  5. Prediksi dengan fungsi `predict(model, data)`

  6. Evaluasi Model:
  
    Selain R-squared, untuk evaluasi model bisa cek nilai error:
    - **MAE** (Mean Absolute Error)
      + Lebih mudah dijelaskan ke orang tanpa latar belakang statistik
      - Mengabaikan error yang besar dari outlier

    - **MSE** (Mean Squared Error)
      + Sensitif terhadap error yang besar (karena error dikuadratkan)
      - Tidak bisa diinterpretasi, lebih sulit dijelaskan

    - **RMSE** (Root Mean Squared Error)
      + Karena asalnya dari MSE, maka sensitif terhadap error besar juga
      + Nilai bisa diinterpretasi (satuan sudah sama seperti data awal)
      - Formula lebih sulit dijelaskan

* Leverage vs Influence

- Nilai prediktor yang cukup jauh dengan kerumuman data (outlier) disebut **high leverage**. 
- Ada 2 tipe Leverage:
  + high influence: leverage mempengaruhi model (dari nilai koefisien, signifikansi, dan R-squared)
  + low influence: leverage tidak mempengaruhi model
- Untuk memastikan tipe outlier, cek summary model 
  + Leverage yang meningkatkan nilai R-Squared, maka dapat dipertahankan 
  + Leverage yang menurunkan nilai R-Squared, maka sebaiknya dibuang

* Multiple linear regression adalah model regresi linear dengan **prediktor lebih dari satu**.

  + Formula pembuatan model:
    - Menggunakan semua prediktor: `lm(formula = target ~ ., data)`
    - Hanya menggunakan beberapa prediktor pada data: `lm(formula = target ~ prediktor1 + prediktor2 + prediktor3, data)`

  + Interpretasi untuk model multiple linear regression:

    1. Coef untuk prediktor numerik:
        - Ketika coef positif, maka nilainya menaikkan target
        - Ketika coef negatif, maka nilainya menurunkan target
    2. Coef untuk prediktor kategorik:
        - Menggunakan konsep dummy variable, akan dibentuk n-1 prediktor (n adalah banyaknya level pada prediktor tersebut, 1 kolom akan dijadikan basis)
        - Nilai coef menunjukkan peningkatan/penurunan nilai target apabila kategori tersebut dibandingkan dengan kategori basisnya. Dengan catatan, nilai prediktor lainnya juga tetap.

    3. Signifikansi prediktor: dilihat berdasarkan `Pr(>|t|)` atau simbol bintang (serupa dengan simple linear regression)

    4. Adjusted R-squared: nilai R-squared yang telah disesuaikan. Adjusted R-squared hanya akan meningkat apabila prediktor memang menghasilkan error yang lebih minimal.
        - Apabila model simple linear regression (satu predictor), gunakan **Multiple R-squared**
        - Apabila model multiple linear regression (lebih dari satu predictor), gunakan **Adjusted R-squared**



