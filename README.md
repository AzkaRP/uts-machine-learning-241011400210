# Tugas UTS Machine Learning

## Identitas Mahasiswa

- **Nama:** Azka Radhitya Pratama
- **NIM:** 241011400210
- **Kelas:** 05TPLM005 (REG B)
- **Mata Kuliah:** Machine Learning
- **RANDOM_STATE:** 10 (dua digit terakhir NIM)

## Deskripsi

Tugas UTS ini menerapkan dua algoritma Machine Learning utama menggunakan NumPy:

1. **Simple Linear Regression** untuk memprediksi penjualan berdasarkan biaya iklan.
2. **Simple Logistic Regression** untuk mengklasifikasikan email menjadi spam atau bukan spam.

## File Proyek

- `tugas_UTS.ipynb` — Implementasi algoritma manual NumPy, evaluasi, visualisasi, dan kesimpulan.
- `Ads_Data.csv` — Dataset regresi linear (Biaya Iklan vs Penjualan).
- `Email_Data.csv` — Dataset klasifikasi email (Jumlah Link & Kata Promo vs Spam).

## Teknologi

- Python
- NumPy
- pandas
- Matplotlib
- Jupyter Notebook
- scikit-learn (digunakan khusus pada bagian bonus perbandingan)

## Ringkasan Hasil

### 1. Linear Regression

Model digunakan untuk memprediksi penjualan berdasarkan biaya iklan menggunakan *Normal Equation* dan *Gradient Descent* (dengan eksperimen *Learning Rate*). Evaluasi metrik pada data testing:
- **MAE:** 7.20
- **MSE:** 87.13
- **RMSE:** 9.33
- **R² Score:** 0.85

Hasil implementasi manual menunjukkan kecocokan bobot dan parameter yang identik saat dibandingkan dengan model Linear Regression dari `scikit-learn`.

### 2. Logistic Regression

Model digunakan untuk mengklasifikasikan email sebagai spam atau bukan spam berdasarkan jumlah tautan dan kata promosi. 

Hasil evaluasi pada data pengujian (dengan threshold default 0.5):
- **Accuracy:** 86.67%
- **Precision:** 83.33%
- **Recall:** 83.33%
- **F1-score:** 83.33%

Model berhasil mengklasifikasikan data dengan baik dan seimbang pada data testing.

## Cara Menjalankan

1. Pastikan dependensi pustaka terinstal:

   ```bash
   python -m pip install numpy pandas matplotlib jupyter scikit-learn
   ```
2. Letakkan file notebook dan kedua dataset dalam direktori yang sama.
3. Buka `tugas_UTS.ipynb` menggunakan Jupyter Notebook.
4. Jalankan seluruh cell dari awal hingga akhir.


## Kesimpulan

Linear Regression berhasil memodelkan hubungan linier biaya iklan terhadap penjualan dengan akurasi yang baik. Sementara itu, Logistic Regression berbasis NumPy mampu melakukan klasifikasi spam email dengan performa metrik evaluasi pengujian yang optimal.