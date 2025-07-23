# Satria Data: Big Data Challenge 2024
## Satria Data
Penyelenggaraan kegiatan Statistika Ria dan Festival Sains Data (SATRIA DATA) merupakan wujud dari dukungan Kementerian Pendidikan, Kebudayaan, Riset, dan Teknologi terhadap perkembangan keilmuan statistika dan sains data secara umum. Tidak hanya itu, kegiatan ini diharapkan juga mampu menjadi trigger bagi terjalinnya jejaring kerjasama antara perguruan tinggi dan industri terapannya.

## Big Data Challenge
Big Data Challenge (BDC) merupakan kompetisi untuk memperoleh rekomendasi penyelesaian terhadap masalah nyata secara analitik, matematis, dan statistis. Permasalahan yang digunakan dalam kompetisi merupakan masalah bisnis/operasional/strategis yang dihadapi oleh mitra penyelenggara. Mitra penyelenggara kompetisi ini dapat berasal dari lembaga pemerintahan, lembaga penelitian, perusahaan swasta, Non Goverment Organization (NGO), lembaga akademik, atau organisasi lainnya yang bersepakat untuk terlibat dalam kompetisi ini. Penyelesaian permasalahan dilakukan menggunakan teknik statistika, analitik, dan machine learning berdasarkan data. Meskipun tidak terbatas pada ini, bentuk permasalahan analitik yang dilombakan antara lain meliputi:
a. Prediksi kejadian dan atau peramalan (forecast)
b. Optimasi
c. Clustering

Di tahun 2024, Big Data Challenge mengangkat permasalahan Natural Language Processing (NLP) untuk menganalisis data cuitan (tweet) di platform media sosial Twitter. Data teks yang diolah memiliki satu topik utama: Pemilu Indonesia 2024. Peserta diminta untuk mengklasifikaikan cuitan pengguna mengenai pemilu Indonesia 2024 ke dalam 8 kelas, yakni: 
1. Sumber Daya Alam
2. Politik
3. Demografi
4. Pertahanan dan Keamanan
5. Ideologi
6. Sosial Budaya
7. Ekonomi
8. Geografi

---

## Metodologi
### 1. Preprocessing Data
Pembersihan data dilakukan dengan cara-cara berikut:
- Standarisasi teks: lowercase, hapus tanda baca, dan emoji (pakai library emoji).
- Hapus stopwords bahasa Indonesia (dari Sastrawi).
- Gunakan TweetTokenizer dari NLTK untuk tokenisasi khusus media sosial.
- Regex digunakan untuk menghapus username, hyperlink, dan kata seperti “RT”/“retweet”.
- IndoNLP digunakan untuk menangani slang dan kata yang dipanjang-panjangin (replace_word_elongation).
- Manual filtering: hapus nama tokoh politik (Anies, Ganjar, Prabowo, dst) karena tidak memberi informasi klasifikasi topik.
Setelah data bersih, diterapkan stemming & lemmatization pada data. Digunakan library Sastrawi untuk stemming kata-kata dalam bahasa Indonesia.

### 2. Modelling
Dataset dibagi menjadi training dan testing, lalu dikonversi ke TensorDataset. Model yang digunakan: BERT (indobenchmark/indobert-base-p1) dengan arsitektur BertForSequenceClassification. Masalah imbalanced class ditangani dengan class_weight dan evaluasi menggunakan balanced accuracy score. DistilBERT sempat dicoba dan menunjukkan hasil lebih baik karena arsitekturnya lebih ringan sehingga meminimalisir risiko overfitting.

## Hasil
Hasil akhir menunjukkan akurasi 41% pada saat diujikan di portal kompetisi Satria Data Big Data Challenge
