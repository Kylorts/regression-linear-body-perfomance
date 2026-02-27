# Implementasi Model Regresi dalam Prediksi Kadar Lemak Tubuh

Proyek ini bertujuan untuk mengembangkan dan membandignkan model linear regresi untuk menentukan persentase lemak tubuh menggunakan data performa fisik.

## Kelompok 5
- **Dessy Nurulita** (2310817220024) 
- **Firda Khoirunisa** (2310817220025) 
- **Galih Aji Sabdaraya** (2310817210005) 

## Latar Belakang
Persentase lemak tubuh merupakan parameter kesehatan yang penting, namun pengukurannya sering kali membutuhkan alat laboratorium yang mahal. Dengan memanfaatkan dataset *Body Performance Data*, proyek ini mengeksplorasi penggunaan regresi linier sebagai solusi alternatif yang lebih efisien untuk memprediksi profil kesehatan berdasarkan performa atletik.

## Dataset
Dataset yang digunakan berasal dari *Korea Sports Promotion Foundation* melalui platform Kaggle.
Link: https://www.kaggle.com/datasets/kukuroo3/body-performance-data
- **Total Data:** 13.393 baris dan 12 kolom.
- **Rentang Usia:** 20–64 tahun.
- **Variabel Target:** `body fat_%`.
- **Fitur Utama:** Usia, jenis kelamin, tinggi badan, berat badan, tekanan darah, kekuatan genggaman, fleksibilitas, jumlah *sit-up*, dan jarak *broad jump*.

## Preprocessing Data
1. **Pembersihan Data:** Tidak ditemukan nilai hilang (*missing values*).
2. **Feature Engineering:** 
   - One-Hot Encoding untuk variabel kategorikal (gender).
   - Analisis multikolinearitas menggunakan *Variance Inflation Factor* (VIF).
3. **Penanganan Outlier:** Menggunakan metode *Interquartile Range* (IQR).
4. **Scaling:** Standarisasi fitur menggunakan *StandardScaler*.
5. **Validasi:** Menggunakan *5-Fold Cross Validation* untuk memastikan stabilitas model.

## Model & Metodologi
Kami membandingkan tiga algoritma regresi:
- **Linear Regression (Baseline):** Sebagai model baseline.
- **Ridge Regression:** Menambahkan penalti L2 untuk mengatasi multikolinearitas.
- **Lasso Regression:** Menggunakan penalti L1 yang mampu melakukan seleksi fitur secara otomatis.

## Ringkasan Hasil Evaluasi
Linear Regression dan Ridge Regression memberikan performa terbaik dan identik berdasarkan hasil eksperimen.

| Metrik Evaluasi | Linear Regression | Ridge Regression(1.0) | Lasso Regression(0.1) |
| :--- | :--- | :--- | :--- |
| **MAE** | 2.9154 | 2.9155 | 2.9708 |
| **RMSE** | 3.7565 | 3.7565 | 3.8120 |
| **R² Score** | 0.7319 | 0.7319 | 0.7239 |
| **MAPE (%)** | 14.51% | 14.51% | 14.73% |

*Data di atas merujuk pada performa  masing-masing model dengan parameter default.*

## Stress Test
Kami menggunakan tiga model terbaik dari masing-masing divisi, yaitu Linear Regression, Ridge Regression(0.01), Lasso Regression(0.01).
Model tiga terbaik diuji melalui tiga skenario untuk melihat batas kemampuannya:
- **Parameter Uji:** [0, 0.05, 0.10, 0.20, 0.30] dan tambahan hingga 0.40.
- **Hasil:** Stabil pada rentang 0.00 - 0.10, namun error melonjak signifikan pada tingkat 0.40.

### 2. Outlier Stress Test

- **Parameter Uji:** Kontaminasi hingga tingkat 5%[cite: 103].
- **Hasil:** Pada tingkat kontaminasi tertentu, nilai $R^2$ anjlok hingga negatif ($\approx -0.07$).

### 3. Covariate Shift
- **Parameter Uji (Faktor Pergeseran):** - **Faktor 0.5:** Pergeseran kecil, model masih cukup robust ($R^2$ turun ke 0.59).
    - **Faktor 1.0:** Kinerja mulai tidak stabil ($R^2 = 0.18$).
    - **Faktor ≥ 1.5:** Model gagal total dengan nilai $R^2$ negatif.

## Link Persentasi Youtube
Link: Youtube: https://youtu.be/4QE2xkgeawM