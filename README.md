# Tubes-Sistem-Cerda-Prediksi-Harga-Rumah
# 🏠 Tubes-Sistem-Cerda-Prediksi-Harga-Rumah

Tugas Besar mata kuliah **Pemrograman Sistem Cerdas** — Klasifikasi Harga Rumah menggunakan algoritma K-Nearest Neighbors (KNN) dan Decision Tree Classifier.

---

## 📌 Deskripsi Proyek

Mencari rumah yang sesuai kebutuhan dan kemampuan finansial adalah tantangan nyata di tengah fluktuasi harga properti. Proyek ini memanfaatkan pendekatan **machine learning** untuk mengklasifikasikan rumah berdasarkan harganya — apakah termasuk kategori **mahal** atau **murah** — sehingga proses pencarian rumah menjadi lebih efisien dan berbasis data.

---

## 📂 Dataset

Dataset yang digunakan adalah **King County House Sales** yang bersumber dari King County Assessor's Office. Dataset ini berisi informasi penjualan rumah di King County, Washington, Amerika Serikat (termasuk wilayah Seattle dan sekitarnya).

- **Jumlah data:** 21.613 entri
- **Jumlah fitur:** 21 kolom
- **Format:** CSV (`data.csv`)

### Fitur Dataset

| Fitur | Deskripsi |
|-------|-----------|
| `price` | Harga jual rumah |
| `bedrooms` | Jumlah kamar tidur |
| `bathrooms` | Jumlah kamar mandi |
| `sqft_living` | Luas area hunian (sqft) |
| `sqft_lot` | Luas lahan (sqft) |
| `floors` | Jumlah lantai |
| `waterfront` | Apakah menghadap ke laut |
| `view` | Skor pemandangan |
| `condition` | Kondisi rumah |
| `grade` | Kualitas konstruksi |
| `sqft_above` | Luas di atas permukaan tanah |
| `sqft_basement` | Luas basement |
| `yr_built` | Tahun dibangun |
| `yr_renovated` | Tahun renovasi terakhir |
| `zipcode` | Kode pos |
| `lat`, `long` | Koordinat lokasi |
| `sqft_living15` | Luas hunian rata-rata 15 tetangga terdekat |
| `sqft_lot15` | Luas lahan rata-rata 15 tetangga terdekat |

---

## ⚙️ Preprocessing

1. **Pengecekan missing values** — dataset tidak memiliki nilai kosong
2. **Pembuatan label target** — harga diklasifikasikan berdasarkan median (`0` = murah, `1` = mahal)
3. **Penghapusan kolom tidak relevan** — `id`, `date`, `price`, `price_label`
4. **One-Hot Encoding** untuk fitur kategorikal
5. **Standarisasi fitur** menggunakan `StandardScaler`
6. **Split data** — 80% training, 20% testing

Dataset ini tergolong **balanced** karena distribusi kelas target (0 dan 1) hampir seimbang.

---

## 🤖 Model yang Digunakan

### 1. K-Nearest Neighbors (KNN)
Algoritma yang memprediksi kelas data baru berdasarkan mayoritas kelas dari *k* tetangga terdekat. Sederhana dan mudah dipahami, namun relatif lambat saat prediksi karena harus menghitung jarak ke semua data training.

### 2. Decision Tree Classifier
Algoritma yang membangun model berbentuk pohon keputusan dengan aturan *if-then*. Mudah diinterpretasikan, namun rentan terhadap overfitting.

---

## 🔧 Hyperparameter Tuning

Pencarian hyperparameter optimal dilakukan menggunakan **GridSearchCV** dengan 5-fold cross-validation.

**KNN:**
- `n_neighbors`: [3, 5, 7, 9]
- `weights`: ['uniform', 'distance']

**Decision Tree:**
- `max_depth`: [3, 5, 10, None]
- `criterion`: ['gini', 'entropy']

---

## 📊 Hasil Evaluasi

### Tahap Pelatihan

| Metrik | KNN | Decision Tree |
|--------|-----|---------------|
| Accuracy | 75% | 87% |
| Precision | 76% | 88% |
| Recall | 72% | 86% |
| F1 Score | 0.74 | 0.87 |

### Tahap Pengujian

| Metrik | KNN | Decision Tree |
|--------|-----|---------------|
| Accuracy | 75% | 89% |
| Precision | 77% | 89% |
| Recall | 73% | 89% |
| F1 Score | 0.75 | 0.89 |

---

## 🛠️ Library yang Digunakan

- `pandas` — manipulasi data
- `numpy` — komputasi numerik
- `scikit-learn` — model machine learning dan evaluasi
- `matplotlib` & `seaborn` — visualisasi data
