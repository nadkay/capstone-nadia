# capstone-nadia

# Dataset link
https://www.kaggle.com/datasets/anggapurnama/twitter-dataset-ppkm?select=INA_TweetsPPKM_Labeled_Pure.csv

# Insight & findings
1. Distribusi Sentimen Awal Tidak Seimbang
Dataset asli memiliki distribusi sentimen yang tidak merata (sentimen netral jauh lebih banyak dari positif dan negatif).
Langkah: dilakukan undersampling untuk menyamakan jumlah data tiap kelas (positif, negatif, netral).
Insight: Distribusi sentimen netral mendominasi, mencerminkan bahwa sebagian besar masyarakat mungkin menyampaikan opini secara informatif atau tidak memihak.

2. Preprocessing Berhasil Mengurangi Noise dalam Data
Langkah preprocessing meliputi:
Casefolding (huruf kecil semua)
Penghapusan link & tanda baca
Normalisasi slangword dan penghapusan stopword
Stemming menggunakan Sastrawi
Insight: Proses ini berhasil menstandarkan teks dan membuat fitur menjadi lebih relevan untuk proses pelatihan model.

3. Jumlah Kata Unik yang Signifikan
Ditemukan jumlah kata unik yang besar pada data training.
Histogram distribusi kata menunjukkan variasi besar antar tweet.
Insight: Tweet memiliki keragaman tinggi, sehingga model perlu fitur yang mampu menangkap konteks secara akurat.

4. Visualisasi Word Cloud Menunjukkan Kata-kata Populer
Beberapa kata yang sering muncul antara lain: “ppkm”, “covid”, “aturan”, “masyarakat”, “prokes”.
Insight: Kata-kata ini menunjukkan fokus publik pada kebijakan dan kondisi pandemi saat itu, relevan terhadap topik sentimen yang dianalisis.

5. TF-IDF Vectorizer Efektif Menangkap Pola N-Gram
Digunakan ngram_range=(1,3) dengan 50.000 fitur maksimum.
Insight: N-gram memberikan konteks tambahan dalam mendeteksi sentimen (contoh: “tidak setuju”, “sangat mendukung”).

6. Model SVM Mengungguli Decision Tree
SVM menunjukkan akurasi dan f1-score lebih tinggi dibanding Decision Tree.
Insight: SVM lebih cocok untuk data teks berdimensi tinggi karena tidak mudah overfitting dan bekerja optimal dengan data sparse (seperti hasil TF-IDF).

# AI support explanation
1. Mengapa Preprocessing Penting dalam NLP
AI seperti model NLP memerlukan data bersih dan konsisten. Teks mentah mengandung banyak noise (seperti emotikon, link, slang) yang dapat mengganggu akurasi.
Dengan stopword removal dan stemming, model dapat fokus hanya pada kata-kata bermakna.

2. Mengapa Menggunakan TF-IDF Vectorizer
TF-IDF menyeimbangkan antara frekuensi kata dan pentingnya kata dalam dokumen secara keseluruhan.
Ini membantu model fokus pada kata-kata unik yang benar-benar membedakan satu tweet dari yang lain (misal: “marah”, “puas”, “dukung”).

3. Mengapa SVM Lebih Baik untuk Data Teks
AI explanation: Dalam data teks, fitur yang digunakan (kata, frasa) sangat banyak dan jarang muncul berulang secara eksak. SVM dirancang untuk mengatasi dimensi tinggi dan dapat membentuk hyperplane optimal bahkan dalam data sparse.
Decision Tree, sebaliknya, cenderung “menghafal” pola lokal dan mudah overfitting jika data tidak linier atau terlalu kompleks.
