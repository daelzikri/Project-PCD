# Klasifikasi Citra Tulang Belakang Normal dan Skoliosis

## Nama Anggota
### 1. DANANG ADIWIJAYA : F1D02310044
### 2. MUHAMMAD ABIYYU RAMADHAN : F1D02310076
### 3. PUDAEL ZIKRI : F1D02310088
### 4. M. WAHYU HILAL ABROOR : F1D02310123

# Project Overview

<p align = justify>Skoliosis adalah kelainan pada tulang belakang sehingga tulang belakang melengkung ke sisi kiri atau kanan. Biasanya skoliosis ini terdeteksi ketika pasien/penderita melakukan pemeriksaan dengan Rontgen atau alat medis lainnya saat MCU, terjadi kecelakaan, dan saat tulang belakang terasa tidak nyaman atau berbeda. Proyek ini
bertujuan untuk membangun sebuah sistem yang mampu mendeteksi kelainan tulang belakang pada manusia pada hasil Rontgen, sehingga sistem dapat secara otomatis memilah skoliosis menurut arah kemiringannya.
Proyek ini bertujuan untuk membangun model klasifikasi citra digital yang mampu membedakan antara citra tulang belakang normal dan citra tulang belakang dengan skoliosis. Dengan pendekatan ini, diharapkan proses identifikasi dapat dilakukan secara otomatis dan efisien menggunakan metode-metode ekstraksi fitur dan algoritma machine learning</p>

### Dataset
Dataset yang digunakan dalam proyek ini terdiri dari citra rontgen (X-ray) tulang belakang manusia yang dikategorikan ke dalam dua kelas utama, yaitu:
1. **Normal** : menunjukkan struktur tulang belakang tanpa kelengkungan abnormal.
2. **Skoliosis** : menunjukkan kelainan melengkung pada tulang belakang.

Dataset diperoleh dari https://www.kaggle.com/datasets/yasserhessein/the-vertebrae-xray-images dan telah melalui proses preprocessing sebelum digunakan dalam pelatihan model.

# Metodologi
Proyek ini dilakukan melalui beberapa tahapan utama sebagai berikut:

## 1. Load Data
Membaca citra dari folder dataset, mengubah ke grayscale, dan resize ke ukuran seragam (256x700 piksel).

## 2. Preprocessing
Terdapat beberapa metode yang di terapkan dalam preprocessing proyek ini, yaitu:
- Histogram Equalization: Menyamakan distribusi intensitas piksel.
- Median Filter: Mengurangi noise pada citra.
- Dilation: Menonjolkan fitur pada citra.
- Thresholding: Mengubah citra grayscale menjadi citra biner (hitam-putih).
#### Berdasarkan Metode yang sudah di sebutkan, terdapat 3 percobaan berbeda yang telah di lakukan untuk tahap preprocessing;
- Percobaan pertama : histogram_equalization --> median_filter --> dilation
- Percobaan kedua : histogram_equalization --> median_filter --> thresholding --> dilation
- Percobaan ketiga : median_filter --> dilation --> histogram_equalization

## 3. Ekstraksi Fitur
- Menggunakan metode GLCM (Gray-Level Co-occurrence Matrix) pada 4 sudut (0°, 45°, 90°, 135°).
- Fitur yang diekstrak: contrast, correlation, energy, homogeneity, ASM, entropy, dan dissimilarity.

## 4. Penyimpanan Fitur
- Hasil ekstraksi fitur disimpan dalam file CSV untuk memudahkan analisis dan pelatihan model.

## 5. Seleksi Fitur
- Menggunakan analisis korelasi untuk mengurangi fitur yang redundant (korelasi tinggi).

## 6. Split Dataset
- Membagi data menjadi data latih dan data uji (misal 80% training, 20% testing).

## 7. Normalisasi Fitur
- Menggunakan standardisasi (Z-score) agar fitur memiliki skala yang seragam.

## 8. Model Training
- Melatih tiga model klasifikasi: Random Forest, SVM, dan KNN.

## 9. Evaluasi Model
- Menggunakan metrik akurasi, precision, recall, classification report, dan confusion matrix untuk mengukur performa model.
