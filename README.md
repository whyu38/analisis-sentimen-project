# Sentiment Analysis: Google Play Store App Reviews

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-orange)
![Scikit-Learn](https://img.shields.io/badge/Library-Scikit--Learn-yellow)
![Status](https://img.shields.io/badge/Status-Completed-success)

## 📌 Project Overview
Proyek ini bertujuan untuk melakukan Analisis Sentimen pada ulasan aplikasi dari Google Play Store. Proyek ini dibangun menggunakan **Deep Learning** dengan arsitektur **LSTM (Long Short-Term Memory)** dan **GRU (Gated Recurrent Unit)**.

Model dilatih untuk mengklasifikasikan ulasan ke dalam 3 kelas sentimen:
1.  **Positif**
2.  **Netral**
3.  **Negatif**

Proyek ini merupakan bagian dari submission akhir dengan kriteria "Nilai Tinggi" (High Distinction).

## 📂 Dataset
Data diperoleh melalui proses **Web Scraping** mandiri menggunakan library `google-play-scraper`.
* **Sumber:** Google Play Store
* **Total Data Mentah:** 12.000+ ulasan
* **Pembagian Data:** 80% Training, 20% Validation
* **Fitur:** Teks ulasan (*content*)
* **Target:** Skor Sentimen (Dikonversi dari Rating Bintang 1-5)

## 🛠️ Data Pipeline
1.  **Data Acquisition:** Scraping data ulasan (Bintang 1-5) secara real-time.
2.  **Labeling:**
    * Score 1-2 $\rightarrow$ `Negatif`
    * Score 3 $\rightarrow$ `Netral`
    * Score 4-5 $\rightarrow$ `Positif`
3.  **Preprocessing:**
    * Case Folding (Lowercase)
    * Cleaning (Menghapus tanda baca, angka, emoji)
    * Stopwords Removal & Stemming (Opsional)
4.  **Feature Extraction:** Tokenization & Padding (Sequencing).

## 🧠 Model Architecture & Experiments
Untuk mendapatkan performa terbaik, dilakukan 3 percobaan skema pelatihan menggunakan **TensorFlow/Keras**:

| Experiment | Architecture | Optimizer | Details |
| :--- | :--- | :--- | :--- |
| **Model 1** | **LSTM** | Adam | Embedding + LSTM Layer + Dense Output |
| **Model 2** | **GRU** | Adam | Embedding + GRU Layer + Dense Output |
| **Model 3** | **Bi-LSTM** | Adam | Embedding + Bidirectional LSTM + Dense Output |

> **Catatan:** Semua model menggunakan teknik **Callback** untuk menghentikan pelatihan secara otomatis jika akurasi training dan validasi mencapai >92%.

## 🚀 How to Run
Ikuti langkah-langkah berikut untuk menjalankan proyek ini di mesin lokal atau Google Colab:

1.  **Clone Repository**
    ```bash
    git clone [https://github.com/](https://github.com/)[USERNAME_KAMU]/[NAMA_REPO].git
    ```

2.  **Install Dependencies**
    Pastikan Python sudah terinstal, lalu jalankan:
    ```bash
    pip install -r requirements.txt
    ```

3.  **Run Scraping (Optional)**
    Jika ingin mengambil data terbaru:
    ```bash
    python scraping.py
    ```

4.  **Train & Evaluate Model**
    Buka file notebook `Sentiment_Analysis_Project.ipynb` menggunakan Jupyter Notebook atau Google Colab dan jalankan semua sel.

## 📂 File Structure
* `Sentiment_Analysis_Project.ipynb`: Notebook utama (Preprocessing, Modeling, Evaluasi).
* `scraping.py`: Skrip Python untuk mengambil data dari Play Store.
* `hasil_scraping.csv`: Dataset hasil scraping (format CSV).
* `requirements.txt`: Daftar library yang digunakan.
* `README.md`: Dokumentasi proyek.

## 👤 Author
**Wahyu Sukma J**

---
*Disclaimer: Dataset yang digunakan hanya untuk tujuan edukasi dan penelitian.*
