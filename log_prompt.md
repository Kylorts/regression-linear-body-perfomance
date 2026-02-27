# Log Prompt dan Modifikasi

| Tujuan Prompt | Prompt (Asli) | Ringkasan Output AI | Perubahan dan Alasan |
| :--- | :--- | :--- | :--- |
| Menentukan batas *outlier* pada *stress test* | "sekarang outlier stress gimana?" | Menggunakan batas berbasis *mean* dan standar deviasi ($mean + 5 * std$). | Diubah menjadi $mean \pm 2 * std$ karena batas $5 * std$ menyebabkan penurunan performa model yang sangat signifikan saat pengujian menjadi $R^2$ negatif saat 5%. |
| Menentukan tingkat *noise* untuk uji *robustness* | "untuk noise stress gimana" | Menyarankan *noise* sebesar 0.05. | Diperluas menjadi $[0, 0.05, 0.10, 0.20, 0.30]$ agar pengujian lebih komprehensif. |
| Menentukan model yang diuji pada *stress test* | "untuk stress test apakah perlu semua model yang diperlukan atau model yang terbaik?" | Menguji seluruh model dan *tuning*-nya. | Dipilih model terbaik saja dari tiga model, yaitu regresi linear, regresi Ridge Alpha (0.01), dan Lasso Regression (0.01) agar analisis fokus pada performa optimal dan tidak redundan. |