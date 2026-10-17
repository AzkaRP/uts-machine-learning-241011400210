# Tugas UTS Machine Learning

## Identitas Mahasiswa

- **Nama:** Azka Radhitya Pratama
- **NIM:** 241011400210
- **Kelas:** 05TPLM005 (REG B)
- **Mata Kuliah:** Machine Learning
- **RANDOM_STATE:** 10 (dua digit terakhir NIM)

## Deskripsi

Tugas UTS ini menerapkan dua algoritma Machine Learning utama menggunakan NumPy:

1. **Simple Linear Regression** untuk memprediksi penjualan berdasarkan biaya iklan (`Ads_Data.csv`, 40 data).
2. **Simple Logistic Regression** untuk mengklasifikasikan email menjadi spam atau bukan spam (`Email_Data.csv`, 60 data).

Model dan metrik evaluasi diimplementasikan secara manual dengan NumPy. `scikit-learn` hanya digunakan pada bagian bonus.

## File Proyek

- `tugas_UTS.ipynb` — Implementasi algoritma manual NumPy, evaluasi, visualisasi, analisis, dan jawaban pemahaman konsep.
- `Ads_Data.csv` — Dataset regresi linear (Biaya Iklan vs Penjualan).
- `Email_Data.csv` — Dataset klasifikasi email (Jumlah Link & Kata Promo vs Spam).

## Teknologi

- Python
- NumPy
- pandas
- Matplotlib
- Jupyter Notebook
- scikit-learn (khusus bagian bonus perbandingan)

## Ringkasan Hasil

### 1. Linear Regression

Persamaan regresi (Normal Equation): **ŷ = 29.3864 + 9.0711 · X**
Artinya, setiap kenaikan biaya iklan 1 juta Rp, penjualan naik rata-rata sekitar 9,07 juta Rp.

Evaluasi pada data training dan testing:

| Metrik | Training | Testing |
|---|---|---|
| MAE | 3.79 | 7.20 |
| MSE | 24.44 | 87.13 |
| RMSE | 4.94 | 9.33 |
| R² Score | 0.96 | 0.85 |

Eksperimen *Gradient Descent* (5000 iterasi):
- Learning rate **0.001**: terlalu lambat, belum mencapai solusi normal equation.
- Learning rate **0.02**: konvergen, hasil identik dengan normal equation.
- Learning rate **0.1**: divergen (loss meledak hingga overflow).

Prediksi penjualan: biaya iklan 4,5 juta → 70,21 juta; 7 juta → 92,88 juta; 12 juta → 138,24 juta
(12 juta berada di luar rentang data sehingga merupakan ekstrapolasi dan kurang dapat dipercaya).

### 2. Logistic Regression

Persamaan model: **P(Spam) = σ(−11.1911 + 1.0264 · JumlahLink + 0.8778 · KataPromo)**

Hasil evaluasi pada data testing (threshold 0.5):

- **Accuracy:** 93.33%
- **Precision:** 100.00%
- **Recall:** 90.00%
- **F1-score:** 94.74%
- **Confusion matrix:** TN = 5, FP = 0, FN = 1, TP = 9

Eksperimen threshold 0.3, 0.5, dan 0.7 menghasilkan metrik yang sama pada data testing.
Threshold yang dipilih adalah **0.7**, karena kesalahan *false positive* (email normal masuk spam)
dianggap lebih merugikan pengguna dibanding *false negative*.

### 3. Bonus: Perbandingan dengan scikit-learn

- **Linear Regression:** hasil identik dengan implementasi manual.
- **Logistic Regression:** koefisien scikit-learn lebih kecil karena secara default memakai
  regularisasi L2 (`C=1.0`), sedangkan implementasi manual tidak memakai regularisasi.

## Cara Menjalankan

1. Pastikan dependensi pustaka terinstal:

```bash
   python -m pip install numpy pandas matplotlib jupyter scikit-learn
```
2. Letakkan file notebook dan kedua dataset dalam direktori yang sama.
3. Buka `tugas_UTS.ipynb` menggunakan Jupyter Notebook.
4. Jalankan seluruh cell dari awal hingga akhir (**Run All**).

## Kesimpulan

Linear Regression berhasil memodelkan hubungan linear biaya iklan terhadap penjualan dengan
baik (R² testing 0.85), meskipun error testing lebih besar dari training karena data testing
hanya 8 titik. Logistic Regression berbasis NumPy mampu mengklasifikasikan spam dengan
akurasi 93.33% dan tanpa false positive. Keterbatasan: dataset kecil (40 dan 60 data) dengan
satu kali pembagian data, sehingga hasil dapat berubah jika `random_state` berbeda.