# KOMPARASI KINERJA ARSITEKTUR TRANSFORMER (IndoBERT) DAN RNN (BiLSTM) PADA ANALISIS SENTIMEN PUBLIK TERHADAP PEMBERHENTIAN PURBAYA YUDHI SADEWA SEBAGAI MENTERI KEUANGAN DI PLATFORM X

<img width="1672" height="941" alt="39fb33d9-4995-492d-9a6b-d480cd6ee41b" src="https://github.com/user-attachments/assets/d051bffa-4fd2-4945-9136-903888df3bbf" />


<p align="center">
  <b>Exploratory Data Analysis (EDA) – Twitter/X Dataset</b>
  <br>
  Analisis Percakapan Publik Mengenai Purbaya Yudhi Sadewa
</p>

---

## 📌 Deskripsi Proyek

Repository ini merupakan bagian dari penelitian yang bertujuan untuk membandingkan kinerja dua arsitektur deep learning, yaitu **Transformer (IndoBERT)** dan **Recurrent Neural Network (RNN) menggunakan BiLSTM**, dalam melakukan analisis sentimen publik terhadap isu pemberhentian Purbaya Yudhi Sadewa sebagai Menteri Keuangan di platform X (Twitter).

Tahapan awal penelitian dilakukan melalui **Exploratory Data Analysis (EDA)** untuk memahami karakteristik dataset, memeriksa kualitas data, mengidentifikasi pola aktivitas pengguna, serta mengeksplorasi isi percakapan publik.

Data diperoleh dari hasil crawling platform X dan diolah menggunakan Python melalui Google Colab.

## 🎯 Tujuan Penelitian

1. Mengeksplorasi karakteristik dataset hasil crawling dari platform X.
2. Mengidentifikasi kualitas data berdasarkan struktur, tipe data, nilai kosong, dan duplikasi.
3. Menganalisis distribusi bahasa pada data percakapan.
4. Mengidentifikasi aktivitas tweet berdasarkan waktu publikasi.
5. Menganalisis tingkat interaksi pengguna melalui like, retweet, reply, quote, dan view.
6. Mengidentifikasi kata-kata yang sering muncul dalam percakapan publik.
7. Menyiapkan dataset untuk tahapan anotasi dan analisis sentimen.
8. Menyediakan data awal untuk komparasi model IndoBERT dan BiLSTM.

## 📂 Dataset

Dataset yang digunakan merupakan data hasil crawling dari platform X (Twitter) dalam format CSV.

**Informasi dataset berdasarkan hasil EDA:**

| Keterangan | Jumlah |
|---|---:|
| Total data awal | 3.613 baris |
| Total kolom | 33 |
| Data setelah deduplikasi ID | 1.862 baris |
| Data pada periode penelitian | 883 tweet |
| Tweet berbahasa Indonesia | 872 tweet |
| Tweet gagal dibaca tanggalnya | 0 |

**Periode data penelitian:**

14 September 2026 – 12 November 2026.

**Beberapa atribut dataset:**

| Kolom | Keterangan |
|---|---|
| `id` | ID unik tweet |
| `text` | Isi atau teks tweet |
| `createdAt` | Waktu publikasi tweet |
| `lang` | Kode bahasa |
| `likeCount` | Jumlah like |
| `retweetCount` | Jumlah retweet |
| `replyCount` | Jumlah balasan |
| `quoteCount` | Jumlah kutipan |
| `viewCount` | Jumlah tayangan |
| `bookmarkCount` | Jumlah bookmark |
| `author` | Informasi penulis tweet |
| `url` | Tautan tweet |

Dataset mentah tidak disertakan dalam repository ini karena merupakan data hasil pengumpulan tersendiri.

## 🔍 Tahapan Exploratory Data Analysis (EDA)

EDA dilakukan melalui beberapa tahapan berikut:

### 1. Import Library

Menggunakan beberapa library Python untuk pengolahan data dan visualisasi:

- Pandas
- NumPy
- Matplotlib
- Seaborn
- WordCloud
- Collections
- Regular Expression (re)

### 2. Memuat Dataset

Membaca dataset CSV menggunakan Pandas dengan beberapa alternatif encoding, yaitu UTF-8, UTF-8-SIG, CP1252, dan Latin1.

### 3. Memahami Struktur Dataset

Melakukan pemeriksaan terhadap:

- Jumlah baris dan kolom.
- Nama atribut.
- Tipe data setiap kolom.
- Informasi struktur dataset.
- Statistik deskriptif.

### 4. Pemeriksaan Missing Values

Mengidentifikasi jumlah dan persentase nilai kosong pada setiap atribut serta menampilkan visualisasi kolom dengan nilai kosong terbanyak.

### 5. Pemeriksaan Duplikasi

Melakukan pemeriksaan duplikasi berdasarkan keseluruhan baris, ID tweet, dan isi teks.

Untuk analisis selanjutnya, data dideduplikasi berdasarkan ID tweet dengan mempertahankan satu baris pada setiap ID.

### 6. Pengolahan Tanggal

Mengonversi atribut `createdAt` menjadi format datetime, kemudian menyesuaikan zona waktu ke Asia/Jakarta (WIB).

Data selanjutnya difilter berdasarkan periode penelitian, yaitu 14 September 2026 sampai 12 November 2026.

### 7. Distribusi Bahasa

Menganalisis persebaran bahasa berdasarkan atribut `lang` untuk mengetahui karakteristik bahasa yang digunakan dalam percakapan.

### 8. Distribusi Jenis Interaksi

Menganalisis jenis interaksi tweet berdasarkan atribut:

- `isReply`
- `isRetweet`
- `isQuote`
- `isPinned`

### 9. Analisis Aktivitas Tweet

Menganalisis jumlah tweet yang dipublikasikan setiap hari untuk mengetahui pola aktivitas percakapan selama periode penelitian.

### 10. Statistik Interaksi

Mengeksplorasi tingkat interaksi tweet berdasarkan:

- Retweet
- Reply
- Like
- Quote
- View
- Bookmark

Analisis menggunakan statistik deskriptif dan median untuk melihat karakteristik interaksi.

### 11. Analisis Panjang Teks

Menghitung panjang karakter dan jumlah kata pada setiap tweet untuk memahami karakteristik teks yang akan digunakan dalam analisis sentimen.

### 12. Frekuensi Kata

Melakukan pembersihan teks secara ringan menggunakan regular expression dan stopwords bahasa Indonesia untuk memperoleh 25 kata yang paling sering muncul.

### 13. WordCloud

Membuat visualisasi WordCloud untuk menggambarkan kata-kata yang dominan dalam percakapan publik.

### 14. Tweet dengan Interaksi Tertinggi

Mengidentifikasi 10 tweet dengan jumlah like tertinggi dan 10 tweet dengan jumlah view tertinggi.

### 15. Ekspor Dataset

Melakukan penyaringan data berdasarkan bahasa Indonesia dan periode penelitian, kemudian mengekspor hasilnya ke dalam format CSV untuk digunakan pada tahapan berikutnya.

## 📊 Hasil Sementara EDA

Berdasarkan hasil pengolahan notebook, diperoleh beberapa informasi utama:

| Indikator | Hasil |
|---|---:|
| Dataset awal | 3.613 |
| Dataset unik berdasarkan ID | 1.862 |
| Dataset sesuai periode penelitian | 883 |
| Dataset bahasa Indonesia | 872 |
| Data gagal dikonversi tanggal | 0 |

Dari total 883 tweet unik dalam periode penelitian, sebanyak 872 tweet teridentifikasi menggunakan bahasa Indonesia.

Dengan demikian, dataset hasil penyaringan bahasa Indonesia menjadi data awal untuk proses anotasi dan analisis sentimen.

**Catatan:** Tahapan EDA ini merupakan eksplorasi awal. Pembersihan teks yang dilakukan untuk analisis frekuensi kata dan WordCloud belum merupakan preprocessing final untuk model IndoBERT maupun BiLSTM.

## 🧠 Metode Penelitian

Penelitian ini berfokus pada komparasi dua arsitektur deep learning:

### 1. IndoBERT (Transformer)

IndoBERT merupakan model berbasis Transformer yang telah dilatih menggunakan korpus bahasa Indonesia. Model ini digunakan untuk memahami konteks dan representasi teks dalam proses klasifikasi sentimen.

### 2. BiLSTM (Bidirectional Long Short-Term Memory)

BiLSTM merupakan pengembangan arsitektur LSTM yang memproses urutan teks melalui dua arah, yaitu maju dan mundur, sehingga dapat mempelajari informasi kontekstual dari kedua arah.

### 3. Komparasi Kinerja

Kedua model akan dibandingkan berdasarkan metrik evaluasi klasifikasi, meliputi:

- Accuracy
- Precision
- Recall
- F1-Score
- Confusion Matrix

Hasil komparasi digunakan untuk mengetahui perbedaan kinerja kedua arsitektur dalam mengklasifikasikan sentimen publik.

## 🛠️ Teknologi dan Tools

| Teknologi | Kegunaan |
|---|---|
| Python | Bahasa pemrograman |
| Google Colab | Lingkungan pengembangan |
| Pandas | Pengolahan dataset |
| NumPy | Komputasi numerik |
| Matplotlib | Visualisasi data |
| Seaborn | Visualisasi statistik |
| WordCloud | Visualisasi frekuensi kata |
| IndoBERT | Model Transformer |
| BiLSTM | Model RNN |

## 📁 Struktur Repository

```text
KOMPARASI-INDOBERT-BILSTM/
│
├── assets/
│   └── cover.png
│
├── EDA_PENCOPOTAN_MENKEU_PURBAYA.ipynb
│
├── data/
│   └── README.md
│
├── README.md
│
└── requirements.txt
```

Keterangan:

- `assets/cover.png` : Gambar sampul penelitian.
- `EDA_PENCOPOTAN_MENKEU_PURBAYA.ipynb` : Notebook untuk proses Exploratory Data Analysis.
- `data/` : Direktori penyimpanan dataset penelitian.
- `README.md` : Dokumentasi utama repository.
- `requirements.txt` : Daftar library Python yang digunakan.

## 🚀 Cara Menjalankan Notebook

1. Buka notebook `EDA_PENCOPOTAN_MENKEU_PURBAYA.ipynb`.
2. Jalankan melalui Google Colab.
3. Siapkan dataset hasil crawling dalam format CSV.
4. Sesuaikan variabel `file_path` dengan lokasi dataset di Google Drive.
5. Jalankan seluruh cell notebook secara berurutan.
6. Tunggu proses eksplorasi dan visualisasi selesai.
7. Unduh hasil dataset yang telah difilter untuk digunakan pada tahapan penelitian selanjutnya.

## 📌 Output Penelitian

Hasil dari tahapan EDA berupa:

- Informasi struktur dan karakteristik dataset.
- Informasi missing values dan duplikasi.
- Distribusi bahasa tweet.
- Tren aktivitas tweet berdasarkan tanggal.
- Statistik interaksi pengguna.
- Distribusi panjang teks dan jumlah kata.
- Frekuensi 25 kata paling sering muncul.
- Visualisasi WordCloud.
- Daftar tweet dengan interaksi tertinggi.
- Dataset berbahasa Indonesia yang telah difilter dalam format CSV.

**Nama file hasil ekspor:**

`data_twitter_eda_periode_indonesia.csv`

## 📖 Kesimpulan

Tahapan Exploratory Data Analysis menjadi proses awal yang penting dalam penelitian komparasi IndoBERT dan BiLSTM. Melalui EDA, karakteristik dataset dapat dipahami sebelum memasuki tahapan preprocessing lanjutan, anotasi sentimen, pembagian data, pelatihan model, dan evaluasi.

Dataset yang telah melalui proses deduplikasi, penyaringan periode, dan seleksi bahasa Indonesia selanjutnya dipersiapkan sebagai data penelitian untuk membandingkan kemampuan model IndoBERT dan BiLSTM dalam analisis sentimen publik di platform X.

---

<p align="center">
  <b>Penelitian Analisis Sentimen Publik</b>
  <br>
  Komparasi IndoBERT dan BiLSTM pada Platform X
</p>
