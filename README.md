#  Titanic Survival Prediction

Proyek Machine Learning sederhana untuk memprediksi apakah seorang penumpang kapal Titanic bakal selamat atau tidak, berdasarkan data diri dan tiket mereka.

---

##  Kenapa Bikin Proyek Ini?
Proyek ini dibuat untuk mempelajari alur kerja (*pipeline*) Machine Learning dari awal sampai akhir. Lewat dataset Titanic ini, fokus utamanya adalah belajar:
1. Cara menangani data yang kosong (*missing values*).
2. Mengubah data teks menjadi angka (*encoding*).
3. Membandingkan performa beberapa algoritma klasifikasi.

---

## Tools & Library yang Dipakai
- **Bahasa**: Python
- **Olah Data**: Pandas, NumPy
- **Visualisasi**: Seaborn, Matplotlib
- **Machine Learning**: Scikit-Learn

---

## Step-by-Step

### Step 1: Ambil Data
Dataset diambil langsung pakai library Seaborn (`sns.load_dataset('titanic')`). Total ada **891 data penumpang** dengan 15 kolom informasi.

### Step 2: Cek & Bersihkan Data (Data Cleaning)
Saat dicek, ada beberapa kolom yang datanya bolong/kosong:
- **`age` (Umur)**: Diisi menggunakan nilai tengah (median) umur penumpang.
- **`embarked` (Pelabuhan Asal)**: Diisi menggunakan nilai yang paling sering muncul (modus).
- **Kolom Duplikat & Sampah**: Kolom `deck` dihapus karena 75%+ datanya kosong. Kolom seperti `embark_town`, `class`, dan `alive` juga dihapus karena informsinya sama persis dengan kolom lain.

### Step 3: Ubah Teks Jadi Angka (Encoding)
Komputer cuma bisa ngitung angka, jadi data berupa teks wajib diubah:
- Kolom `sex`: `female` diubah jadi `0`, `male` diubah jadi `1`.
- Kolom `embarked`: Diubah pakai teknik *One-Hot Encoding* (`pd.get_dummies()`).

### Step 4: Bagi Data & Scaling (Train-Test Split)
- Data dipisah jadi **Fitur ($X$)** yaitu data diri penumpang, dan **Target ($y$)** yaitu status selamat/tidaknya (`survived`).
- Data dibagi dua: **80% buat latihan (Train)** dan **20% buat ujian (Test)**.
- Nilai angka disamakan skalanya pakai `StandardScaler` supaya angka yang gede (seperti harga tiket) enggak mendominasi variabel lain.

### Step 5: Latih Model Machine Learning
Ada 3 algoritma yang dicoba untuk dibandingin hasilnya:
1. **Logistic Regression**: Nyari garis batas matematis yang pas.
2. **Decision Tree**: Bikin pohon keputusan berdasarkan aturan ya/tidak.
3. **Random Forest**: Gabungan dari banyak pohon keputusan yang voting hasil akhir.

### Step 6: Evaluasi & Hasil
Setelah diuji ke 20% data tes, ini tingkat akurasi masing-masing model:

- **Logistic Regression**: 81.01%
- **Random Forest**: 81.01%
- **Decision Tree**: 78.77%

> **Kesimpulan Hasil**: Logistic Regression dan Random Forest dapet skor tertinggi dan sama-sama berhasil nebak dengan akurasi **81.01%**.

---

## Insight 
Dari grafik *Feature Importance* model Random Forest, faktor paling berpengaruh yang menentukan keselamatan penumpang adalah:
1. **Jenis Kelamin (`sex`)**
2. **Kelas Tiket (`pclass`)**

Ini cocok banget sama fakta sejarah evakuasi Titanic yang mendahulukan wanita & anak-anak (*"women and children first"*), serta penumpang kelas atas yang posisi kamarnya lebih dekat ke dek sekoci.

---

##  Cara Menjalankan Kode
1. Clone repo ini atau download file `notebook.ipynb`.
2. Buka di Google Colab atau Jupyter Notebook.
3. Run sel dari paling atas sampai bawah.
