# Model Klasifikasi Bunga

Proyek ini melibatkan pelatihan Convolutional Neural Network (CNN) untuk mengklasifikasikan gambar bunga. Dataset yang digunakan diambil dari Kaggle dan mencakup berbagai jenis bunga.

## Dataset

Dataset diunduh dari Kaggle menggunakan token API dan mencakup gambar berbagai kelas bunga. Untuk keperluan proyek ini, kelas 'sunflower' dihapus dari dataset.

## Arsitektur Model

Model ini menggunakan transfer learning dengan arsitektur Xception, tanpa lapisan klasifikasi akhirnya. Lapisan klasifikasi kustom ditambahkan di atas model untuk klasifikasi bunga.

### Detail Model:
- **Model Dasar**: Xception (pre-trained pada ImageNet)
- **Lapisan Kustom**:
  - Flatten
  - Dense (512 unit, aktivasi ReLU)
  - Dropout (0.5)
  - Dense (4 unit, aktivasi Softmax)

### Konfigurasi Pelatihan:
- **Optimizer**: Adam dengan learning rate 1e-5
- **Fungsi Kerugian**: Categorical Crossentropy
- **Metode Evaluasi**: Akurasi
- **Bobot Kelas**: Diterapkan untuk menangani ketidakseimbangan kelas
- **Callback**:
  - `EarlyStopping`: Menghentikan pelatihan jika tidak ada perbaikan pada kerugian validasi selama 15 epoch
  - `ModelCheckpoint`: Menyimpan model terbaik berdasarkan akurasi validasi
  - `AccuracyThresholdStopping`: Menghentikan pelatihan ketika akurasi validasi mencapai 90%

## Hasil

- **Loss Validasi**: 0.3749
- **Akurasi Validasi**: 0.8515

Model mencapai akurasi 86.30% pada data pelatihan.

## Penggunaan

Untuk menjalankan kode:
1. **Unduh dataset** menggunakan API Kaggle.
2. **Praberkas** dataset dengan menghapus kelas 'sunflower' jika diperlukan.
3. **Latih model** menggunakan kode yang disediakan.
4. **Evaluasi dan Simpan** model terbaik.

### Konversi Model

Model yang telah dilatih dikonversi ke berbagai format:
- **TensorFlow SavedModel**
- **TensorFlow Lite**
- **TensorFlow.js**

## Kode

Kode lengkap untuk pelatihan dan evaluasi dapat ditemukan dalam Jupyter Notebook yang disediakan.

## Penulis

**DWI KRISNANDI**

Silakan hubungi jika memiliki pertanyaan atau membutuhkan bantuan lebih lanjut.