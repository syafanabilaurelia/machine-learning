#  F1 Podium Finish Prediction

Proyek Machine Learning untuk memprediksi apakah seorang pembalap Formula 1 akan berhasil finis di podium (posisi 1–3) berdasarkan posisi start (grid), nama pembalap, tim/konstruktor, dan lokasi sirkuit.

---

##  Kenapa Proyek Ini Dibuat?
Di Formula 1, hanya 3 dari 20 pembalap (sekitar 15%) yang bisa naik podium di setiap balapan. Proyek ini dibuat untuk mempelajari:
1. Cara menangani **Imbalanced Data** pada klasifikasi biner.
2. Penggabungan (*merging*) beberapa tabel relational data F1 historis.
3. *One-Hot Encoding* pada variabel kategorikal (pembalap, tim, dan sirkuit).

---

##  Tools & Library
- **Bahasa**: Python
- **Data Source**: Kaggle - Formula 1 World Championship (2010 - Present)
- **Library**: Pandas, NumPy, Scikit-Learn, Seaborn, Matplotlib, Kagglehub

---

##  Tahapan Pengerjaan

### Step 1: Penggabungan Dataset
Menggabungkan 4 tabel F1 utama (`results`, `races`, `drivers`, `constructors`) dan menyaring data balapan dari era modern (tahun 2010 ke atas).

### Step 2: Membuat Variabel Target
Membuat kolom baru `is_podium`:
- `1` = Finis di posisi 1, 2, atau 3.
- `0` = Finis di luar posisi 3 (posisi 4–20).

### Step 3: Encoding & Scaling
- Variabel kategorikal (`driverRef`, `team_name`, `race_name`) diubah menjadi angka menggunakan *One-Hot Encoding*.
- Variabel posisi start (`grid`) diselaraskan skalanya menggunakan `StandardScaler`.

### Step 4: Menangani Imbalanced Data & Pemodelan
Menggunakan parameter `class_weight='balanced'` pada model agar algoritma memberikan perhatian seimbang pada prediksi posisi podium. Tiga algoritma yang diuji:
- **Logistic Regression**
- **Decision Tree**
- **Random Forest**

---

## Hasil Evaluasi

Hasil akurasi pada *test set* (20% data uji):

- **Random Forest**: **88.04%**
- **Decision Tree**: 86.41%
- **Logistic Regression**: 83.07%

> **Kesimpulan**: Model **Random Forest** meraih akurasi tertinggi sebesar **88.04%**. 

---

## Key Insights
Berdasarkan analisis *Feature Importance*, **Posisi Start (`grid`)** dan **Dominasi Tim/Konstruktor** menjadi dua faktor paling vital dalam memprediksi peluang seorang pembalap meraih podium.

---

## Cara Menjalankan Notebook
1. Download file `f1_podium_prediction.ipynb`.
2. Buka di Google Colab.
3. Jalankan sel kode secara berurutan.
