# Sentiment Analysis: Google Play Store App Reviews

![Python](https://img.shields.io/badge/Python-3.10%2B-blue)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-orange)
![Scikit-Learn](https://img.shields.io/badge/Library-Scikit--Learn-yellow)
![Status](https://img.shields.io/badge/Status-Completed-success)

## 📌 Project Overview
Proyek ini bertujuan untuk melakukan Analisis Sentimen pada ulasan aplikasi **Gojek** dari Google Play Store. Proyek ini dibangun menggunakan teknik **Deep Learning** dan **Natural Language Processing (NLP)**.

Model dilatih untuk mengklasifikasikan ulasan ke dalam 3 kelas sentimen:
1.  **Positif** (Rating 4-5)
2.  **Netral** (Rating 3)
3.  **Negatif** (Rating 1-2)

Proyek ini dikembangkan untuk memenuhi submission akhir dengan kriteria **"Nilai Tinggi"** (High Distinction), mencakup penggunaan dataset >10.000 sampel, arsitektur Deep Learning, dan akurasi di atas 85%.

## 📂 Dataset
Data diperoleh melalui proses **Web Scraping** mandiri menggunakan library `google-play-scraper`.
* **Sumber:** Google Play Store (Aplikasi Gojek)
* **Total Data Mentah:** 12.000 ulasan
* **Pembagian Data:** * 80% Training
    * 20% Validation & Test
* **Fitur:** Teks ulasan (*content*)
* **Target:** Skor Sentimen (Negatif, Netral, Positif)

## 🛠️ Data Pipeline
1.  **Data Acquisition:** Scraping 12.000 data ulasan terbaru.
2.  **Labeling:** Mengonversi rating bintang menjadi kelas sentimen.
3.  **Preprocessing:**
    * Case Folding (Lowercase)
    * Cleaning (Menghapus tanda baca, angka, karakter non-alfanumerik)
4.  **Feature Extraction:** * Tokenization (Membahsa kosa kata menjadi angka)
    * Padding & Sequencing (Menyamakan panjang input sequence)

## 🧠 Model Architecture & Experiments
Dilakukan 3 percobaan skema pelatihan menggunakan framework **TensorFlow/Keras** untuk membandingkan performa arsitektur RNN yang berbeda:

| Experiment | Architecture | Optimizer | Accuracy (Test Set) |
| :--- | :--- | :--- | :--- |
| **Model 1** | **LSTM** | Adam | ~63% |
| **Model 2** | **GRU** | Adam | ~87% |
| **Model 3** | **Bi-LSTM** | Adam | **~98% (Best)** |

> **Catatan:** > * Semua model menggunakan **Embedding Layer** sebagai input layer.
> * Menggunakan **Callback** untuk menghentikan pelatihan otomatis jika akurasi training dan validasi mencapai >92%.
> * Model terbaik (Bidirectional LSTM) dipilih untuk tahap deployment/inference.

## 📊 Results
Model terbaik (**Bidirectional LSTM**) berhasil mencapai performa yang sangat baik dengan detail evaluasi:
* **Training Accuracy:** >95%
* **Validation Accuracy:** >86%
* **Testing Accuracy (Unseen Data):** 87.46%

## 🚀 How to Run
Ikuti langkah-langkah berikut untuk menjalankan proyek ini di Google Colab atau Jupyter Notebook:

1.  **Clone Repository** (Jika ada)
    ```bash
    git clone [https://github.com/USERNAME_KAMU/NAMA_REPO.git](https://github.com/USERNAME_KAMU/NAMA_REPO.git)
    ```

2.  **Install Dependencies**
    Jalankan perintah berikut untuk menginstal library yang dibutuhkan:
    ```bash
    pip install -r requirements.txt
    ```

3.  **Run Scraping (Optional)**
    Jika ingin mengambil data terbaru dari Play Store:
    ```bash
    python scraping.py
    ```

4.  **Train & Evaluate Model**
    Buka file notebook `Sentiment_Analysis_Project.ipynb` dan jalankan semua sel (Run All). Pastikan file `hasil_scraping.csv` sudah tersedia.

## 📂 File Structure
* `Dicoding_Analisis_Sentimen.ipynb`: Notebook utama (Preprocessing, Modeling, Evaluasi).
* `Scraping_Proyek_Analisis_Sentimen.ipynb`: Notebook khusus untuk proses scraping data.
* `hasil_scraping.csv`: Dataset hasil scraping (format CSV).
* `requirements.txt`: Daftar versi library yang digunakan.
* `README.md`: Dokumentasi proyek.

## 👤 Author
**Wahyu Sukma J**

---
*Disclaimer: Dataset yang digunakan hanya untuk tujuan edukasi dan penelitian.*
