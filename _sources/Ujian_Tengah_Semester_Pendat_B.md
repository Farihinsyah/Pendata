---
title: Ujian Tengah Semester Pendat B

---

# Ujian Tengah Semester Pendat B
Nama : Ahmad Syahrul Farihin  
Nim : 240411100031  
Kelas : Penambangan Data B  

---
## Analisa Data Kesuburan Tanah
### 1. Lakukan analisis data dengan menggunakan
- K-Nearest Neighbors (KNN)
### 2. Lakukan Pemrosesan Data tersebut
### 3. Hitung Metrik Evaluasi
---
| Metrik | Keterangan |
|--------|-----------|
| Accuracy | Persentase prediksi benar dari total data |
| Precision | Ketepatan prediksi kelas positif |
| Recall | Kemampuan mendeteksi seluruh kelas positif |
| F1-Score | Harmonic mean antara Precision dan Recall |
---
## Dataset
Dataset yang digunakan merupakan data kesuburan tanah yang berisi beberapa atribut seperti pH tanah, kandungan unsur hara (N, P, K), serta tekstur tanah. Selain itu, terdapat juga label yang menunjukkan tingkat kesuburan.

Pada dataset ini ditemukan beberapa nilai yang kosong (missing value), sehingga perlu dilakukan preprocessing sebelum data digunakan untuk pemodelan.

---
## Preprocessing Data

![Screenshot 2026-04-22 114611](https://hackmd.io/_uploads/ryEsGRrTbx.png)

### 1. Missing Value

![image](https://hackmd.io/_uploads/Bk1Af0Ba-x.png)

Pada tahap ini dilakukan penanganan data yang kosong.  
Untuk kolom numerik seperti pH, N, P, dan K, nilai kosong diisi menggunakan rata-rata (mean).  
Sedangkan untuk data kategorikal seperti tekstur tanah, digunakan nilai yang paling sering muncul (modus).

Tujuannya supaya data tetap bisa digunakan tanpa harus menghapus baris.

---
### 2. One to Many (Encoding)

![image](https://hackmd.io/_uploads/rykzQ0r6Wl.png)

Kolom tekstur tanah yang masih berupa teks diubah menjadi bentuk numerik menggunakan metode one-hot encoding.
Contohnya:
- Liat → 1,0,0  
- Pasir → 0,1,0  
Hal ini dilakukan karena algoritma KNN hanya bisa memproses data numerik.
---
### 3. Column Filter

![image](https://hackmd.io/_uploads/SJJY70S6Wl.png)

Pada tahap ini dilakukan penghapusan kolom yang tidak diperlukan, seperti ID.

Kolom ID tidak memiliki pengaruh terhadap proses klasifikasi, sehingga lebih baik dihapus agar tidak mengganggu model.

---
### 4. Normalisasi
Data numerik kemudian dinormalisasi menggunakan metode Min-Max.
Tujuannya agar semua fitur berada dalam skala yang sama, sehingga tidak ada nilai yang terlalu dominan.  
Langkah ini penting terutama untuk algoritma KNN yang berbasis jarak.

---
## Pembagian Data
Data dibagi menjadi dua bagian:
- 70% data training  
- 30% data testing  
Pembagian dilakukan menggunakan metode stratified sampling agar distribusi kelas tetap seimbang antara data training dan testing.
---
## Metode K-Nearest Neighbor (KNN)

![image](https://hackmd.io/_uploads/SynsmAHaWx.png)

KNN merupakan metode klasifikasi yang bekerja dengan cara mencari sejumlah tetangga terdekat dari suatu data.
Pada tugas ini digunakan:
- Nilai k = 3  
- Menggunakan pembobotan jarak (distance weighting)
Artinya, data akan diklasifikasikan berdasarkan mayoritas dari 3 tetangga terdekat, dengan mempertimbangkan jarak masing-masing tetangga.
---
## Evaluasi Model
Evaluasi dilakukan menggunakan node Scorer di KNIME.
Metrik yang digunakan adalah:
- Accuracy  
- Precision  
- Recall  
- F1-Score  
Selain itu juga ditampilkan confusion matrix untuk melihat detail hasil klasifikasi.
---
## Hasil dan Pembahasan

Berikut adalah hasil evaluasi model KNN berdasarkan output node **Accuracy Statistics** pada KNIME:

### Tabel Hasil Evaluasi Per Kelas

| Kelas        | True Positive | False Positive | True Negative | False Negative | Recall | Precision | Sensitivity | Specificity | F-Measure | Accuracy | Cohen's |
|--------------|:-------------:|:--------------:|:-------------:|:--------------:|:------:|:---------:|:-----------:|:-----------:|:---------:|:--------:|:--------:|
| Tidak Subur  | 307           | 0              | 293           | 0              | 1.0    | 1.0       | 1.0         | 1.0         | 1.0       | —         |—         |
| Subur        | 293           | 0              | 307           | 0              | 1.0    | 1.0       | 1.0         | 1.0         | 1.0       | —         |—         |
| **Overall**  | —             | —              | —             | —              | —      | —         | —           | —           | —         | 1.0  |1.0    |

### Ringkasan Metrik Evaluasi

| Metrik      | Nilai  |
|-------------|--------|
| Accuracy    | 1.0 (100%) |
| Precision   | 1.0 (100%) |
| Recall      | 1.0 (100%) |
| F1-Score    | 1.0 (100%) |
| Sensitivity | 1.0 (100%) |
| Specificity | 1.0 (100%) |

### Pembahasan

Berdasarkan hasil evaluasi di atas, model KNN dengan nilai **k = 3** dan pembobotan jarak menunjukkan performa yang **sangat baik**, bahkan mencapai nilai sempurna (1.0) pada seluruh metrik evaluasi.

Rincian hasil per kelas:
- **Kelas "Tidak Subur"**: Dari 307 data yang diprediksi, seluruhnya benar (True Positive = 307, False Positive = 0, False Negative = 0). Artinya tidak ada satu pun data yang salah diklasifikasikan.
- **Kelas "Subur"**: Sama halnya, dari 293 data, seluruhnya berhasil diklasifikasikan dengan benar tanpa ada kesalahan prediksi.

Nilai **Accuracy = 1.0** berarti 100% dari seluruh data testing berhasil diklasifikasikan dengan tepat. Nilai **Precision = Recall = F1-Score = 1.0** menunjukkan bahwa model tidak menghasilkan False Positive maupun False Negative sama sekali.

Hasil ini menunjukkan bahwa:
1. Proses **preprocessing** (penanganan missing value, encoding, normalisasi) berjalan dengan baik dan menghasilkan data yang bersih untuk dilatih.
2. Algoritma **KNN dengan k=3** sangat cocok diterapkan pada dataset kesuburan tanah ini.
3. **Pembagian data 70:30** dengan stratified sampling menghasilkan distribusi yang representatif, sehingga model mampu menggeneralisasi dengan sempurna.

---
## Kesimpulan
Dari proses yang telah dilakukan, dapat disimpulkan bahwa:
- **Preprocessing** sangat penting untuk memastikan kualitas data sebelum digunakan dalam model. Langkah seperti penanganan missing value, encoding, dan normalisasi terbukti meningkatkan kualitas input model.
- Algoritma **KNN (k=3)** dapat digunakan secara efektif untuk mengklasifikasikan data kesuburan tanah menjadi dua kelas: *Subur* dan *Tidak Subur*.
- Hasil evaluasi menunjukkan bahwa model memiliki **performa sempurna** dengan Accuracy, Precision, Recall, dan F1-Score masing-masing sebesar **1.0 (100%)**, yang berarti seluruh data testing berhasil diklasifikasikan dengan benar.
- Model ini layak digunakan sebagai alat bantu klasifikasi kesuburan tanah, namun tetap perlu diuji lebih lanjut dengan data yang lebih bervariasi.