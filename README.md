# Studi-tentang-Fluktuasi-Harga-Cabai-Rawit-Merah-di-Pasar-Tradisional-dan-Modern-Jakarta

```
Tugas           : UAS BIG DATA

Judul Project   : Studi Komprehensif tentang Fluktuasi Harga Cabai Rawit Merah di Pasar 
Tradisional dan Modern Jakarta 

Kelas           : TI.21.A2

Mata Kuliah     : Big Data

Kelompok 1      : • RAVANSA RAHMAN SANTOSA 312110103 
                  • AJIE RAFLI PAMUNGKAS 312110429 
                  • ANINDIA SASI KIRANA 312110268 
                  • MUHAMMAD KHRISNA FAISAL ZUHRI 312110177 
                  • MUFIDA NURIYANA 312110172 
                 
```
<br/>

## Tentang Penelitian

Penelitian ini mengadopsi pendekatan analisis data terdistribusi menggunakan 
PySpark untuk memperoleh pemahaman tentang fluktuasi harga cabai rawit merah di 
pasar tradisional dan modern di Jakarta. 

Data

Kumpulan data harga cabai dari tahun 2020 hingga 2023 dengan periode harian 
diambil dari situs web Info Pangan Jakarta

Import Library : <br>Di sini mengimport library yang diperlukan, seperti yang tercantum di bawah ini:
```
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
from plotly.subplots import make_subplots
import plotly.graph_objects as go
import plotly.express as px

from sklearn.model_selection import train_test_split
from sklearn.preprocessing import MinMaxScaler
from sklearn.pipeline import Pipeline
from sklearn.compose import ColumnTransformer

from jcopml.pipeline import num_pipe, cat_pipe
from jcopml.utils import save_model, load_model
from jcopml.plot import plot_missing_value
from jcopml.feature_importance import mean_score_decrease
from jcopml.time_series.decomposition import additive_decomposition, multiplicative_decomposition, stl_decomposition
from statsmodels.tsa.seasonal import seasonal_decompose
```

Load DataSet : <br>kumpulan data yang telah diambil sebelumnya dengan menggunakan kolom-kolom tertentu, yakni kolom Tanggal, Pasar Induk Kramatjati, Pasar Grogol, Pasar Minggu, dan Pasar Koja Baru. 


Tujuan utama adalah untuk memahami pola, tren, dan mendapatkan wawasan lebih mendalam terkait dengan konteks atau masalah yang sedang dipelajari.

<br/>

## Data
Berikut adalah data harga cabai rawit merah yang diperoleh : 
![image](https://github.com/ravansaa/Studi-tentang-Fluktuasi-Harga-Cabai-Rawit-Merah-di-Pasar-Tradisional-dan-Modern-Jakarta/assets/92682154/e967998e-2971-4203-a599-3f96eb78a625)


<br/>

## Analisis Data
Berikut adalah hasil dari analisis deskriptifnya: 
![image](https://github.com/ravansaa/Studi-tentang-Fluktuasi-Harga-Cabai-Rawit-Merah-di-Pasar-Tradisional-dan-Modern-Jakarta/assets/92682154/61daa4b5-4b82-44b5-b08d-c1adef4a3a27)

<br/>

## Visualisasi

Berikut adalah visualisasi time series harga cabai dari 4 pasar : 
![image](https://github.com/ravansaa/Studi-tentang-Fluktuasi-Harga-Cabai-Rawit-Merah-di-Pasar-Tradisional-dan-Modern-Jakarta/assets/92682154/4009327d-eb7b-4ca8-82ca-1c92672ba019)<br/>
Berdasarkan visualisasi tersebut, dapat disimpulkan bahwa rata-rata nilai transaksi 
pasar di Jakarta mengalami peningkatan dalam kurun waktu 3 tahun terakhir, yaitu dari 
tahun 2020 hingga 2023. Peningkatan ini terlihat dari grafik yang terus naik dari tahun ke 
tahun. 
Peningkatan rata-rata nilai transaksi pasar ini menunjukkan bahwa pasar masih 
menjadi pilihan masyarakat untuk berbelanja. Hal ini dapat disebabkan oleh beberapa 
faktor, antara lain: 
1. Harga barang di pasar tradisional lebih terjangkau dibandingkan dengan harga 
barang di minimarket atau supermarket. 
2. Kualitas barang di pasar tradisional masih terjaga, terutama untuk barang-barang 
segar seperti buah, sayur, dan daging. 
3. Pilihan barang di pasar tradisional lebih beragam dibandingkan dengan 
minimarket atau supermarket. 
<br/>

## Visualisasi
![image](https://github.com/ravansaa/Studi-tentang-Fluktuasi-Harga-Cabai-Rawit-Merah-di-Pasar-Tradisional-dan-Modern-Jakarta/assets/92682154/65e5c353-26cb-4342-b59b-505263fb3db0)

Berdasarkan visualisasi tersebut, dapat disimpulkan bahwa: Trend nilai transaksi pasar tradisional di Jakarta mengalami peningkatan dalam 
kurun waktu 3 tahun terakhir. Hal ini terlihat dari grafik yang terus naik dari tahun 
ke tahun.
<br/>

## Splitting Data
 ![image](https://github.com/ravansaa/Studi-tentang-Fluktuasi-Harga-Cabai-Rawit-Merah-di-Pasar-Tradisional-dan-Modern-Jakarta/assets/92682154/6c19716a-c532-48ca-b8de-ee222bee944a) <br/>
Dari hasil splitting data, kita mendapatkan 896 data untuk train data, dan 257 untuk test 
data 

<br/>

## Model Linear Regression
```
﻿# Define the vector_assembler function
def vector_assembler (dataframe, indep_cols)
assembler - Vector Assembler (inputCols-indep_cols, outputCol=&quot;features&quot;) output assembler.transform(dataframe)
return output

Indep_cols df.columns
Indep_cols.remove('Pasar Minggu') 
indep_cols.remove('Tanggal&') 

df = vector_assembler(df, indep_cols=indep_cols)

Ir = LinearRegression(featuresCol='features', labelCol='Pasar Minggu', predictionCol='prediction')
model = lr.fit(df)

predictions = model.transform(df)
predictions.select('Tanggal', 'Pasar Minggu', 'prediction').show(5)
```
<br/>

## Evaluasi
![image](https://github.com/ravansaa/Studi-tentang-Fluktuasi-Harga-Cabai-Rawit-Merah-di-Pasar-Tradisional-dan-Modern-Jakarta/assets/92682154/887b2552-9e44-40c3-b7f1-d730cfebc095) <br/>
Dari gambar diatas dapat dilihat bahwa kinerja/skor dari model yang kita buat adalah: 
R2: 95% 
MSE: 25372428.2726828837 
MAE: 3768.6794207905455 
Secara keseluruhan, hasil skoring menunjukkan bahwa model memiliki tingkat 
akurasi yang tinggi (R2: 95%) dan tingkat kesalahan prediksi yang rendah (MSE dan 
MAE yang rendah).
<br/>
