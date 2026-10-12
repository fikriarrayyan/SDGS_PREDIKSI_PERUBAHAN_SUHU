# 🌍 Klasifikasi Kategori Perubahan Suhu Menggunakan Machine Learning

<p align="center">
  <b>Decision Tree & Random Forest</b><br>
  Mendukung Sustainable Development Goal (SDG) 13: Penanganan Perubahan Iklim
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python">
  <img src="https://img.shields.io/badge/Scikit--learn-F7931E?style=for-the-badge&logo=scikitlearn&logoColor=white" alt="Scikit-learn">
  <img src="https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white" alt="Pandas">
  <img src="https://img.shields.io/badge/SDG-13-green?style=for-the-badge" alt="SDG 13">
</p>

---

## 📌 Deskripsi Proyek

Proyek ini merupakan penerapan **Machine Learning** untuk mengklasifikasikan kategori perubahan suhu menjadi tiga kelas, yaitu **Rendah, Sedang, dan Tinggi**, menggunakan algoritma Decision Tree dan Random Forest.

Kedua algoritma dilatih dan dievaluasi untuk mengetahui perbandingan kinerjanya dalam mengklasifikasikan data perubahan suhu. Hasil evaluasi digunakan untuk menentukan model yang memberikan performa lebih baik pada dataset yang digunakan.

Proyek ini berkaitan dengan **Sustainable Development Goal (SDG) 13: Climate Action**, yaitu tujuan pembangunan berkelanjutan yang berfokus pada penanganan perubahan iklim dan dampaknya.

## 🎯 Tujuan Proyek

- Menerapkan algoritma Decision Tree untuk klasifikasi kategori perubahan suhu.
- Menerapkan algoritma Random Forest sebagai model pembanding.
- Membandingkan performa kedua model menggunakan metrik evaluasi.
- Menguji model melalui confusion matrix dan inference.
- Mempelajari penerapan Machine Learning dalam analisis data yang berkaitan dengan SDG 13.

## 📊 Dataset

Dataset yang digunakan adalah data perubahan suhu yang diperoleh dari Kaggle.

| Informasi | Keterangan |
|---|---|
| Nama file | `FAOSTAT_data_en_11-1-2024.csv` |
| Format | CSV |
| Jumlah data setelah cleaning | 231.633 baris |
| Fitur masukan | `Area`, `Months`, `Year` |
| Target klasifikasi | `Kategori` |
| Jumlah kategori | 3 |

Kolom `Value` digunakan untuk membentuk kategori target berdasarkan kuantil, tetapi tidak digunakan sebagai fitur masukan model.

### Kategori Perubahan Suhu

- **Rendah:** nilai `Value` di bawah kuantil sepertiga.
- **Sedang:** nilai `Value` mulai dari kuantil sepertiga hingga sebelum kuantil dua pertiga.
- **Tinggi:** nilai `Value` sama dengan atau lebih besar dari kuantil dua pertiga.

## ⚙️ Tahapan Pengerjaan

### 1. Data Cleaning

Membersihkan dataset dengan menghapus baris yang memiliki nilai kosong pada kolom `Value`. Setelah proses ini, tersisa 231.633 baris data.

### 2. Pembentukan Kategori

Nilai pada kolom `Value` dikelompokkan menjadi tiga kategori, yaitu Rendah, Sedang, dan Tinggi, menggunakan kuantil sepertiga dan dua pertiga.

### 3. Pemilihan Fitur dan Encoding

Fitur yang digunakan sebagai masukan model adalah `Area`, `Months`, dan `Year`, sedangkan `Kategori` menjadi target prediksi.

- `Area` dan `Months` diproses menggunakan **One-Hot Encoding**.
- `Year` dipertahankan sebagai fitur numerik.
- Kolom `Value` tidak dimasukkan sebagai fitur agar model tidak menggunakan nilai yang menjadi dasar pembentukan target secara langsung.

### 4. Pembagian Data

Dataset dibagi menjadi 80% data pelatihan (*training data*) dan 20% data pengujian (*testing data*).

Pembagian menggunakan `random_state=42` dan `stratify=y` agar hasil pembagian dapat direproduksi serta proporsi kategori tetap terjaga.

### 5. Pemodelan Decision Tree

Decision Tree digunakan untuk mempelajari pola data melalui struktur percabangan berdasarkan fitur yang tersedia.

Parameter utama:
- `max_depth=10`
- `random_state=42`

### 6. Pemodelan Random Forest

Random Forest menggabungkan sejumlah pohon keputusan untuk menghasilkan prediksi. Algoritma ini digunakan sebagai pembanding terhadap Decision Tree.

Parameter utama:
- `n_estimators=100`
- `random_state=42`
- `n_jobs=-1`

Kedua model menggunakan pipeline preprocessing dan pelatihan dari Scikit-learn.

### 7. Evaluasi Model

Evaluasi dilakukan menggunakan empat metrik:

- **Accuracy:** proporsi seluruh prediksi yang benar.
- **Precision:** ketepatan prediksi untuk suatu kategori.
- **Recall:** kemampuan model mengenali data yang termasuk dalam suatu kategori.
- **F1-score:** ukuran yang menggabungkan precision dan recall.

Precision, recall, dan F1-score dihitung menggunakan pendekatan *macro average*.

### 8. Confusion Matrix

Confusion matrix digunakan untuk membandingkan kategori sebenarnya dengan hasil prediksi model. Hasilnya membantu mengidentifikasi kategori yang berhasil diprediksi dan kategori yang masih sering tertukar.

### 9. Inference

Inference merupakan tahap penggunaan model yang telah dilatih untuk menghasilkan prediksi kategori perubahan suhu berdasarkan fitur masukan berupa wilayah, bulan, dan tahun.

Hasil prediksi ditampilkan dalam kategori Rendah, Sedang, atau Tinggi.

## 📈 Hasil Evaluasi Model

Berikut adalah hasil evaluasi Decision Tree dan Random Forest pada data pengujian.

| Metrik Evaluasi | Decision Tree | Random Forest |
|---|---:|---:|
| Accuracy | 56,44% | **58,05%** |
| Precision (Macro) | 55,28% | **57,60%** |
| Recall (Macro) | 56,45% | **58,05%** |
| F1-score (Macro) | 55,36% | **57,69%** |

### 🏆 Perbandingan Akurasi

Decision Tree memperoleh akurasi sebesar **56,44%**, sedangkan Random Forest memperoleh akurasi sebesar **58,05%**.

Random Forest memiliki selisih akurasi sebesar **1,61 poin persentase** lebih tinggi dibandingkan Decision Tree. Model Random Forest juga memperoleh nilai precision, recall, dan F1-score yang lebih tinggi pada pengujian ini.

Meskipun Random Forest menunjukkan hasil yang lebih baik, performa kedua model masih dapat ditingkatkan.

## 🛠️ Teknologi yang Digunakan

- **Python** — bahasa pemrograman untuk pengembangan model.
- **Google Colab** — lingkungan untuk menjalankan kode dan eksperimen.
- **Pandas** — pengolahan dan pembersihan dataset.
- **Scikit-learn** — preprocessing, pelatihan, dan evaluasi model Machine Learning.
- **Matplotlib** — visualisasi perbandingan akurasi model.

## 🌱 Kaitan dengan SDG 13

**SDG 13: Climate Action** bertujuan mengambil tindakan untuk menangani perubahan iklim dan dampaknya.

Proyek ini menunjukkan pemanfaatan Machine Learning untuk mengolah dan mengklasifikasikan data perubahan suhu. Penerapan ini dapat menjadi langkah awal dalam mempelajari pola data lingkungan dan mendukung eksplorasi analisis perubahan suhu berbasis teknologi.

Namun, model ini masih merupakan eksperimen klasifikasi awal dan belum dapat dianggap sebagai sistem prediksi iklim yang akurat atau sebagai dasar pengambilan keputusan lingkungan.

## 📝 Kesimpulan

Berdasarkan hasil pengujian, algoritma Decision Tree dan Random Forest dapat digunakan untuk mengklasifikasikan kategori perubahan suhu menjadi Rendah, Sedang, dan Tinggi.

Random Forest memberikan hasil evaluasi yang lebih baik dibandingkan Decision Tree, dengan akurasi sebesar **58,05%**, sementara Decision Tree memperoleh akurasi sebesar **56,44%**.

Walaupun demikian, hasil tersebut menunjukkan bahwa performa model masih perlu ditingkatkan. Pengembangan berikutnya dapat dilakukan melalui perbaikan pemilihan fitur, pengujian algoritma lain, dan evaluasi tambahan.

Proyek ini merupakan penerapan awal Machine Learning yang relevan dengan SDG 13 dalam konteks analisis data perubahan suhu.

---

<p align="center">
  🌍 <b>Machine Learning for Climate Action</b><br>
  <i>Proyek pembelajaran dan eksplorasi data perubahan suhu.</i>
</p>
