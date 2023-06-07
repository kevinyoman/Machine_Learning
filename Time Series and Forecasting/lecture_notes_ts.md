# Lecture Notes Time Series Forecasting

1. Time series adalah suatu data yang berhubungan dengan runtun waktu dimana periode waktu berurutan dan intervalnya sama.
2. Analisis time series adalah analisis data runtun waktu dimana yang akan kita prediksi adalah data time series itu sendiri dengan data historicalnya.
3. Untuk membuat object time series dapat menggunakan fungsi `ts(data, start, frequency)`

* `data` : data yang ingin di forecast
* `start` : awal mula dari data time series
* `frequency` : pola berulang yang ingin diamati

4. Komponen data time series :

* trend : pola naik atau turun pada time series
* seasonal : pola berulang yang memiliki interval waktu yang konsisten (musiman)
* error : pola yang tidak tertangkap oleh trend dan seasonal

5. Tipe pola data time series :

* additive : intervalnya mendekati sama atau tidak tambah besar

$X = T+S+E$

* multiplicative : intervalnya makin besar

$X = T*S*E$

6. Apabila data time series yang kita miliki terdapat pola multiplicative, maka ada beberapa cara yang bisa kita gunakan yaitu :

* melakukan transformasi menggunakan `log()` atau `sqrt()` agar pola datanya menjadi additive. Hal ini akan sangat berguna apabila kita memiliki data yang kurang tertangkap pola multiplicativenya
* tetap menjadikan multiplicative dan melanjutkan ke pemodelan time series

Kedua cara diatas dapat digunakan sebagai salah satu cara untuk tunning model dalam analisis time series. 

7. Manfaat melakukan decompose:

* menemukan pola trend, seasonal, dan random pada data time series
* bisa melakukan analisis seasonal untuk melihat pola seasonalnya pada data yang nantinya akan berguna untuk pembuatan keputusan yang berdasarkan pola seasonal yang diperoleh
* bisa melakukan analisis trend yang dapat digunakan untuk mengetahui pola data yang sesungguhnya pada data tanpa adanya efek seasonal pada data

8. Forecasting model :

* SMA(Single moving average) : cocok untuk data yang hanya ada error
* Simple exponential smoothing (SES) : cocok untuk data yang hanya ada error Parameter smoothing didalamnya yaitu alpha,
* Holt Exponential : cocok untuk data yang trend dan error. Parameter smoothing didalamnya yaitu Beta
* Holt Winters Exponential : cocok untuk data yang ada error trend dan seasonal Parameter smoothing didalamnya yaitu gamma

9. Untuk membuat model exponential smoothing bisa menggunakan dua fungsi yaitu `ets()` dan `HoltWinters()`.

* fungsi `ets(object_ts, model = "ZZZ")`
* fungsi `HoltWinters(object_ts, alpha = NULL/FALSE, beta = NULL/FALSE, gamma = NULL/FALSE, seasonal = "additive/multiplicative")`

10. Untuk melakukan evalusi model bisa menggunakan nilai error :

* RMSE(Root Mean Square Error) : range nilainya cenderung seperti data aslinya
* MAPE(Mean Absolute Percentage Error) : range nilainya 0%-100% makin kecil makin bagus

11. Workflow analysis time series:

a. read data
b. cleansing data 
  - cek urutan data `arrange()`
  - pastikan datanya memiliki periode yang lengkap `pad()` + `anyNA()` 
  - isi missing value berdasarkan bisnis knowledge
c. buat object ts `ts(data, frequency)`
d. visualisasikan 
  - cek tipe time series -> multiplicative/additive
e. decompose -> cek apakah ada trend? ada seasonal? 
f. splitting data
g. model fitting
  - SMA / SES -> no trend no seasonal
  - Holt explonential smoothing -> no seaonal
  - Holt Winters -> ada trend ada seasonal
h. forecast berapa periode kedepan `forecast(model, h)`
i. model evaluation `accuracy(hasil_forecast, data_actual)`
        


     
     
     
     
     
     
     
     
     
     
     
     