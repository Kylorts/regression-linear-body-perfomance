# Experiment Log

|        Model       |        Fitur       |   Parameter  |  MAE   |  RMSE  |    R²  | MAPE (%) |            Catatan                    |
|--------------------|:------------------:|:------------:|:------:|:------:|:------:|:--------:|---------------------------------------|
| Linear Regression  | Semua fitur + OHE  | Default      | 2.9154 | 3.7566 | 0.7319 | 14.51    | Baseline model tanpa regularisasi     |
| Ridge              | Semua fitur + OHE  | alpha = 0.01 | 2.9154 | 3.7566 | 0.7319 | 14.51    | Tidak ada perubahan signifikan        |
| Ridge              | Semua fitur + OHE  | alpha = 0.1  | 2.9154 | 3.7566 | 0.7319 | 14.51    | Regularisasi sangat kecil             |
| Ridge              | Semua fitur + OHE  | alpha = 1.0  | 2.9155 | 3.7566 | 0.7319 | 14.51    | Masih stabil                          |
| Ridge              | Semua fitur + OHE  | alpha = 10   | 2.9163 | 3.7569 | 0.7319 | 14.51    | Performa mulai sedikit turun          |
| Ridge              | Semua fitur + OHE  | alpha = 100  | 2.9308 | 3.7686 | 0.7302 | 14.57    | Regulasi mulai Berdampak              |
| Ridge              | Semua fitur + OHE  | alpha = 500  | 3.0547 | 3.9072 | 0.7098 | 15.10    | Regulasi terlalu kuat                 |
| Lasso              | Semua fitur + OHE  | alpha = 0.01 | 2.9174 | 3.7572 | 0.7318 | 14.51    | Hampir sama dengan baseline           |
| Lasso              | Semua fitur + OHE  | alpha = 0.1  | 2.9708 | 3.8121 | 0.7239 | 14.73    | Mulai kehilangan informasi            |
| Lasso              | Semua fitur + OHE  | alpha = 1.0  | 4.1260 | 5.2321 | 0.4765 | 20.24    | Banyak koefisien menjadi nol          |
| Lasso              | Semua fitur + OHE  | alpha = 10   | 5.8637 | 7.3504 | -0.0264| 29.06    | Model gagal belajar (underfitting)    |
| Lasso              | Semua fitur + OHE  | alpha = 100  | 5.8637 | 7.3504 | -0.0264| 29.06    | Koefisien hampir semua nol            |
| Lasso              | Semua fitur + OHE  | alpha = 500  | 5.8637 | 7.3504 | -0.0264| 29.06    | Underfitting ekstrem                  |

*Catatan: OHE = One-hot Encoding*

---


# Noise Stress Experiment Log
## Linear Regression Noise Stress Results:

| Noise_Level | MAE | RMSE | R2 | MAPE |
| :---: | :---: | :---: | :---: | :---: |
| 0.00 | 2.915433 | 3.756560 | 0.731936 | 14.51% |
| 0.05 | 2.924935 | 3.765646 | 0.730639 | 14.55% |
| 0.10 | 2.938070 | 3.780874 | 0.728461 | 14.63% |
| 0.20 | 3.029047 | 3.882372 | 0.713685 | 15.00% |
| 0.40 | 3.334315 | 4.250753 | 0.656755 | 16.51% |

## Ridge Regression Best Alpha (0.01) Noise Stress Results:

| Noise_Level | MAE | RMSE | R2 | MAPE |
| :---: | :---: | :---: | :---: | :---: |
| 0.00 | 2.915434 | 3.756560 | 0.731936 | 14.51% |
| 0.05 | 2.923016 | 3.765446 | 0.730667 | 14.54% |
| 0.10 | 2.946833 | 3.792695 | 0.726758 | 14.65% |
| 0.20 | 3.027760 | 3.893147 | 0.712097 | 15.01% |
| 0.40 | 3.363370 | 4.278662 | 0.652233 | 16.58% |

## Lasso Regression Best Alpha (0.01) Noise Stress Results:

| Noise_Level | MAE | RMSE | R2 | MAPE |
| :--- | :--- | :--- | :--- | :--- |
| 0.00 | 2.917414 | 3.757223 | 0.731844 | 14.51% |
| 0.05 | 2.923565 | 3.766906 | 0.730459 | 14.54% |
| 0.10 | 2.951049 | 3.795088 | 0.726411 | 14.68% |
| 0.20 | 3.035153 | 3.898331 | 0.711332 | 15.08% |
| 0.40 | 3.344227 | 4.273892 | 0.653005 | 16.55% |
---
# Outlier Stress Experiment Log
## Linear Regression Outlier Stress
| Outlier_Percent | MAE | RMSE | R2 | MAPE |
| :--- | :--- | :--- | :--- | :--- |
| 0.00 | 2.915433 | 3.756560 | 0.731936 | 14.51% |
| 0.05 | 3.965507 | 6.579736 | 0.273869 | 16.97% |
| 0.10 | 4.927578 | 8.367656 | -0.074014 | 19.22% |
| 0.20 | 6.611022 | 10.806385 | -0.598610 | 23.17% |
| 0.30 | 8.035297 | 12.503543 | -1.009215 | 26.50% |

## Ridge Regression Best Alpha (0.01) Outlier Stress
| Outlier_Percent | MAE | RMSE | R2 | MAPE |
| :--- | :--- | :--- | :--- | :--- |
| 0.00 | 2.915434 | 3.756560 | 0.731936 | 14.51% |
| 0.05 | 3.965506 | 6.579729 | 0.273870 | 16.97% |
| 0.10 | 4.927575 | 8.367646 | -0.074012 | 19.22% |
| 0.20 | 6.611017 | 10.806371 | -0.598606 | 23.17% |
| 0.10 | 8.035289 | 12.503525 | -1.009210 | 26.50% |

## Lasso Regression Best Alpha (0.01) Outlier Stress
| Outlier_Percent | MAE | RMSE | R2 | MAPE |
| :--- | :--- | :--- | :--- | :--- |
| 0.00 | 2.917414 | 3.757223 | 0.731844 | 14.51% |
| 0.05 | 3.961191 | 6.556349 | 0.279039 | 16.96% |
| 0.10 | 4.917492 | 8.332190 | -0.064887 | 19.20% |
| 0.20 | 6.590841 | 10.755794 | -0.583598 | 23.11% |
| 0.30 | 8.006575 | 12.442908 | -0.989667 | 26.43% |
---
# Covariate Shift Log
## Linear Regression Results
| Shift Factor | MAE | RMSE | R2 | MAPE |
| :--- | :--- | :--- | :--- | :--- |
| 0.0 | 2.915433 | 3.756560 | 0.731936 | 14.51% |
| 0.5 | 3.736988 | 4.641295 | 0.590514 | 16.60% |
| 1.0 | 5.665740 | 6.555483 | 0.181224 | 24.66% |
| 1.5 | 8.091622 | 8.854341 | -0.495936 | 35.79% |
| 2.0 | 10.680798 | 11.306114 | -1.440964 | 48.07% |

## Ridge Regression Results (Alpha: 0.01)
| Shift Factor | MAE | RMSE | R2 | MAPE |
| :--- | :--- | :--- | :--- | :--- |
| 0.0 | 2.915434 | 3.756560 | 0.731936 | 14.51% |
| 0.5 | 3.736986 | 4.641293 | 0.590515 | 16.60% |
| 1.0 | 5.665726 | 6.555470 | 0.181227 | 24.66% |
| 1.5 | 8.091594 | 8.854315 | -0.495927 | 35.79% |
| 2.0 | 10.680756 | 11.306075 | -1.440947 | 48.07% |

## Lasso Regression Results (Alpha: 0.01)
| Shift Factor | MAE | RMSE | R2 | MAPE |
| :--- | :--- | :--- | :--- | :--- |
| 0.0 | 2.917414 | 3.757223 | 0.731844 | 14.51% |
| 0.5 | 3.727546 | 4.631663 | 0.592193 | 16.54% |
| 1.0 | 5.619220 | 6.511538 | 0.192191 | 24.40% |
| 1.5 | 8.004157 | 8.772306 | -0.468161 | 35.33% |
| 2.0 | 10.554322 | 11.185849 | -1.388864 | 47.41% |