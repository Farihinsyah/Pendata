---
title: Data Preparation

---

# Data Preparation

Data Preparation merupakan tahap ketiga dalam CRISP-DM yang berfokus pada proses menyiapkan data agar siap digunakan untuk pembuatan model. Setelah data dipahami pada tahap sebelumnya, langkah berikutnya adalah membersihkan, memperbaiki, dan mengubah data sesuai kebutuhan analisis.

Tahap ini biasanya memerlukan waktu yang cukup lama karena kualitas model sangat bergantung pada kualitas data yang telah dipersiapkan.

Beberapa proses utama dalam Data Preparation antara lain:

---

## 1. Pembersihan Data (Data Cleaning)

Pada tahap ini dilakukan perbaikan terhadap data yang bermasalah agar tidak mengganggu proses analisis.

Beberapa kegiatan yang dilakukan:

- Mengatasi data yang kosong (missing value)  
- Menghapus data yang terduplikasi  
- Memperbaiki kesalahan penulisan atau format  
- Mengatasi nilai yang tidak wajar atau ekstrem  

Tujuan dari pembersihan data adalah memastikan data dalam kondisi rapi, konsisten, dan layak digunakan.

---

## 2. Integrasi Data (Data Integration)

Jika data berasal dari beberapa sumber, maka perlu dilakukan penggabungan data menjadi satu kesatuan yang utuh.

Hal-hal yang perlu diperhatikan:

- Kesamaan format antar sumber data  
- Konsistensi nama atribut  
- Penyamaan struktur data  

Proses ini penting agar data dapat dianalisis secara menyeluruh tanpa terjadi konflik antar sumber.

---

## 3. Transformasi Data (Data Transformation)

Transformasi dilakukan untuk menyesuaikan bentuk data dengan kebutuhan model.

Contoh kegiatan:

- Mengubah data kategorikal menjadi bentuk numerik  
- Menyederhanakan kategori yang terlalu banyak  
- Menyesuaikan skala data  
- Membuat variabel baru dari data yang sudah ada  

Transformasi membantu meningkatkan kinerja algoritma dan mempermudah proses analisis.

---

## 4. Seleksi Fitur (Feature Selection)

Tidak semua atribut dalam data selalu relevan. Oleh karena itu, dilakukan pemilihan fitur yang benar-benar berpengaruh terhadap tujuan analisis.

Manfaat seleksi fitur:

- Mengurangi kompleksitas model  
- Mempercepat proses pelatihan  
- Mengurangi risiko overfitting  
- Meningkatkan interpretasi hasil  

Pemilihan fitur dilakukan berdasarkan pertimbangan teknis dan kebutuhan bisnis.

---

## 5. Pembagian Data (Data Splitting)

Sebelum masuk ke tahap modeling, data biasanya dibagi menjadi beberapa bagian, seperti:

- Data pelatihan (training data)  
- Data pengujian (testing data)  

Tujuan pembagian ini adalah untuk menguji kemampuan model dalam memprediksi data baru yang belum pernah dilihat sebelumnya.

---

## Kesimpulan

Data Preparation adalah tahap penting yang bertujuan untuk menyiapkan data agar siap digunakan dalam proses pemodelan.

Melalui proses pembersihan, penggabungan, transformasi, dan pemilihan fitur, data menjadi lebih terstruktur dan sesuai untuk dianalisis. Tahap ini sangat menentukan kualitas hasil model yang akan dibangun pada langkah selanjutnya.
