# SDGS_PREDIKSI_PERUBAHAN_SUHU
# Penggunaan Decision Tree dan Random Forest untuk Memprediksi Kategori Perubahan Suhu Berbasis Machine Learning dalam Mendukung SDG 13

## Deskripsi Project

Project ini merupakan penerapan Machine Learning untuk mengklasifikasikan kategori perubahan suhu berdasarkan wilayah, bulan, dan tahun.

Dataset yang digunakan adalah **Temperature Change** yang diperoleh dari Kaggle. Pada project ini digunakan dua algoritma klasifikasi, yaitu **Decision Tree** dan **Random Forest**.

Hasil klasifikasi dibagi menjadi tiga kategori, yaitu:

- Rendah
- Sedang
- Tinggi

Project ini dibuat sebagai salah satu penerapan Machine Learning yang berkaitan dengan **Sustainable Development Goal (SDG) 13: Climate Action**.

---

## Latar Belakang

Perubahan suhu merupakan salah satu data yang berkaitan dengan perubahan iklim. Data perubahan suhu yang memiliki jumlah data cukup besar membutuhkan proses pengolahan agar dapat digunakan untuk menemukan pola tertentu.

Machine Learning dapat digunakan untuk membantu mengolah data dan melakukan klasifikasi berdasarkan pola yang terdapat pada dataset. Oleh karena itu, pada project ini digunakan algoritma Decision Tree dan Random Forest untuk mengklasifikasikan kategori perubahan suhu.

Project ini memiliki keterkaitan dengan **SDG 13 (Climate Action)** karena menggunakan data perubahan suhu sebagai salah satu informasi yang berkaitan dengan perubahan iklim.

---

## Rumusan Masalah

1. Bagaimana melakukan preprocessing pada dataset perubahan suhu agar dapat digunakan dalam proses Machine Learning?
2. Bagaimana menerapkan algoritma Decision Tree dan Random Forest untuk mengklasifikasikan kategori perubahan suhu?
3. Bagaimana membandingkan performa algoritma Decision Tree dan Random Forest berdasarkan hasil evaluasi model?

---

## Tujuan

Project ini bertujuan untuk:

1. Melakukan preprocessing pada dataset perubahan suhu.
2. Membangun model klasifikasi menggunakan algoritma Decision Tree dan Random Forest.
3. Mengklasifikasikan perubahan suhu ke dalam kategori Rendah, Sedang, dan Tinggi.
4. Membandingkan performa kedua algoritma berdasarkan Accuracy, Precision, Recall, dan F1-Score.

---

## Solusi

Solusi yang digunakan adalah membangun model Machine Learning dengan pendekatan **Supervised Learning - Classification**.

Model menggunakan informasi:

- `Area`
- `Months`
- `Year`

untuk menghasilkan kategori perubahan suhu:

- `Rendah`
- `Sedang`
- `Tinggi`

Dua algoritma digunakan dalam project ini, yaitu:

1. **Decision Tree Classifier**
2. **Random Forest Classifier**

Kedua model kemudian diuji dan dibandingkan berdasarkan hasil evaluasinya.

---

## Relevansi dengan SDG 13

Project ini berkaitan dengan **SDG 13: Climate Action (Penanganan Perubahan Iklim)**.

Dataset yang digunakan berisi data perubahan suhu berdasarkan wilayah, bulan, dan tahun. Data tersebut digunakan untuk melakukan klasifikasi kategori perubahan suhu menggunakan Machine Learning.

Penerapan Machine Learning pada data perubahan suhu dapat membantu dalam melakukan pengolahan dan klasifikasi data berdasarkan pola yang terdapat pada dataset.

---

## Dataset

Dataset yang digunakan adalah:

**Temperature Change**

Sumber dataset:

**Kaggle**

File dataset:

`FAOSTAT_data_en_11-1-2024.csv`

### Profil Dataset

| Keterangan | Jumlah |
|---|---:|
| Data awal | 241.893 baris |
| Jumlah kolom | 14 |
| Missing Value | 10.260 |
| Data duplikat | 0 |
| Data setelah cleaning | 231.633 baris |

### Variabel Dataset

Beberapa variabel utama yang digunakan dalam project:

| Variabel | Keterangan |
|---|---|
| `Area` | Wilayah atau negara |
| `Months` | Bulan |
| `Year` | Tahun |
| `Value` | Nilai perubahan suhu |

---

## Input dan Output

### Input

Fitur yang digunakan sebagai input model:

- `Area`
- `Months`
- `Year`

### Output

Output model berupa kategori perubahan suhu:

- **Rendah**
- **Sedang**
- **Tinggi**

> Kolom `Value` digunakan dalam proses pembentukan kategori target dan tidak digunakan sebagai fitur input model.

---

## Metode

Project ini menggunakan pendekatan:

**Supervised Learning - Classification**

### 1. Decision Tree

Decision Tree merupakan algoritma klasifikasi yang membuat serangkaian keputusan berdasarkan fitur pada data hingga menghasilkan suatu kategori.

Pada project ini, Decision Tree digunakan untuk menentukan kategori perubahan suhu berdasarkan `Area`, `Months`, dan `Year`.

### 2. Random Forest

Random Forest merupakan algoritma yang menggunakan beberapa Decision Tree dan menggabungkan hasil prediksi dari setiap pohon untuk menentukan kategori akhir.

Pada project ini digunakan **100 Decision Tree** dalam model Random Forest.

---

## Preprocessing Data

Tahapan preprocessing yang dilakukan pada dataset adalah:

1. Membaca dataset.
2. Menampilkan data awal.
3. Mengecek missing value.
4. Mengecek data duplikat.
5. Melakukan cleaning terhadap missing value.
6. Membentuk kategori perubahan suhu.
7. Menentukan fitur dan target.
8. Melakukan encoding pada data kategorikal.
9. Membagi dataset menjadi data training dan testing.

### Pembentukan Kategori

Nilai `Value` dikelompokkan menjadi tiga kategori:

| Kategori | Rentang Nilai |
|---|---|
| Rendah | `Value < 0.134` |
| Sedang | `0.134 <= Value < 0.835` |
| Tinggi | `Value >= 0.835` |

Setelah pembentukan kategori:

| Kategori | Jumlah |
|---|---:|
| Rendah | 77.080 |
| Sedang | 77.264 |
| Tinggi | 77.289 |

---

## Pembagian Data

Dataset dibagi menjadi data training dan testing dengan perbandingan:

- **80% Data Training:** 185.306 data
- **20% Data Testing:** 46.327 data

Pembagian data menggunakan `random_state = 42` dan `stratify`.

---

## Evaluasi Model

Model dievaluasi menggunakan beberapa metrik:

- Accuracy
- Precision
- Recall
- F1-Score

### Hasil Evaluasi

| Metrik | Decision Tree | Random Forest |
|---|---:|---:|
| Accuracy | 56,44% | 58,05% |
| Precision (Macro) | 55,28% | 57,60% |
| Recall (Macro) | 56,45% | 58,05% |
| F1-Score (Macro) | 55,36% | 57,69% |

Berdasarkan hasil pengujian pada dataset dan pembagian data yang digunakan, Random Forest memperoleh nilai evaluasi yang lebih tinggi dibandingkan Decision Tree.

---

## Confusion Matrix

Confusion Matrix digunakan untuk melihat perbandingan antara kategori sebenarnya dengan kategori hasil prediksi model.

### Decision Tree

```text
[[10162, 3208, 2046],
 [ 5133, 5262, 5058],
 [ 1944, 2790,10724]]
