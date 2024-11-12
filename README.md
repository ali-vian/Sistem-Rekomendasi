# Laporan Proyek Machine Learning - Muhammad Alivian Sidiq

## Project Overview

Dalam era digital saat ini, jumlah konten film yang tersedia di platform streaming dan bioskop sangat besar. Pengguna sering merasa kesulitan untuk menemukan film yang sesuai dengan selera dan preferensi mereka di tengah beragamnya pilihan yang ada [[1]](https://j-ptiik.ub.ac.id/index.php/j-ptiik/article/view/9163/4159). Di sinilah peran sistem rekomendasi film menjadi penting untuk membantu pengguna menyaring dan menemukan film yang paling relevan dan menarik bagi mereka[[2]](https://citisee.amikompurwokerto.ac.id/assets/proceedings/2017/TI08.pdf).

Sistem rekomendasi film dirancang untuk memberikan rekomendasi yang dipersonalisasi berdasarkan data dan preferensi pengguna. Dengan menggunakan teknik-teknik seperti Collaborative Filtering, Content-Based Filtering, dan hybrid approach, sistem ini dapat mengidentifikasi pola-pola dalam perilaku dan preferensi pengguna, sehingga mampu memberikan rekomendasi yang lebih akurat dan relevan [[3]](https://doi.org/10.1016/j.eij.2015.06.005). Collaborative Filtering, misalnya, bekerja dengan cara mengidentifikasi pengguna dengan preferensi serupa dan merekomendasikan film yang disukai oleh pengguna-pengguna serupa tersebut. Sementara itu, Content-Based Filtering memberikan rekomendasi berdasarkan karakteristik dari film yang sudah disukai pengguna, seperti genre, sutradara, atau aktor.[[4]](https://ejournal.unsrat.ac.id/v3/index.php/decartesian/article/view/28274/31235)

Dengan adanya sistem rekomendasi film, pengguna dapat menikmati pengalaman menonton yang lebih efisien dan memuaskan. Sistem ini tidak hanya meningkatkan kenyamanan pengguna, tetapi juga membantu penyedia layanan streaming untuk mempertahankan pelanggan mereka dengan menyediakan konten yang sesuai dengan minat pengguna[[5]](https://www.journal.mediapublikasi.id/index.php/logic/article/view/4299/2851).

**Mengapa proyek ini penting untuk diselesaikan ?**
- Dengan memberikan rekomendasi yang sesuai dengan preferensi, pengguna tidak perlu membuang banyak waktu mencari film yang menarik bagi mereka.
- Platform dapat mengarahkan pengguna ke konten yang jarang ditonton tetapi berkualitas, sehingga mengoptimalkan pemanfaatan seluruh koleksi film
  
**Referensi**

[[1]](https://j-ptiik.ub.ac.id/index.php/j-ptiik/article/view/9163/4159) M. Fajriansyah, P. P. Adikara, and A. W. Widodo, “Sistem Rekomendasi Film Menggunakan Content Based Filtering,” 2021. [Online]. Available: http://j-ptiik.ub.ac.id

[[2]](https://citisee.amikompurwokerto.ac.id/assets/proceedings/2017/TI08.pdf) A. Halim, H. Gohzali, D. Maria Panjaitan, and I. Maulana, "Sistem Rekomendasi Film menggunakan Bisecting
K-Means dan Collaborative Filtering," 2017. [Online] Availeble: https://citisee.amikompurwokerto.ac.id/assets/proceedings

[[3]](https://doi.org/10.1016/j.eij.2015.06.005) F. O. Isinkaye, Y. O. Folajimi, and B. A. Ojokoh, “Recommendation systems: Principles, methods and evaluation,” Nov. 01, 2015, Elsevier B.V. doi: 10.1016/j.eij.2015.06.005.

[[4]](https://ejournal.unsrat.ac.id/v3/index.php/decartesian/article/view/28274/31235) Y. Visher Laja Jaja, B. Susanto, L. Ricky Sasongko, and K. Kunci, “Penerapan Metode Item-Based Collaborative Filtering Untuk Sistem Rekomendasi Data MovieLens,” 2020. [Online]. Available: https://ejournal.unsrat.ac.id/index.php/decartesian

[[5]](https://www.journal.mediapublikasi.id/index.php/logic/article/view/4299/2851) A. Zakharia et al., “Sistem Rekomendasi Film Indonesia Menggunakan Metode Content-Based Filtering”, [Online]. Available: https://journal.mediapublikasi.id/index.php/logic

## Business Understanding

### Problem Statements

- Bagaimana cara membangun model rekomendasi yang dapat mengidentifikasi film yang paling relevan berdasarkan genre film ?
- Dengan menggunakan data rating, bagaimana cara merekomendasikan film yang belum pernah ditonton pengguna ?
- Bagaimana cara membangun model sistem rekomendasi menggunakan pendekatan content-based filtering dan Collaborative Filtering ?

### Goals

Menjelaskan tujuan proyek yang menjawab pernyataan masalah:
- Mendapatkan rekomendasi film sebanyak top-N rekomendasi kepada penguna berdasarkan genre film yang pernah di tonton
- Mendapatkan rekomendasi filem yang sesuai berdasarkan rating dan belum perah ditonton 
- Membangun model sistem rekomendasi menggunakan pendekatan (content-based filtering) dengan Cosine Similiarity dan (Collaborative Filtering) model based Deep learning

### Solution statements
- Pendekatan Content-Based Filtering menggunakan Cosine Similarity algoritma ini akan merekomendasikan film kepada pengguna berdasarkan kesamaan fitur genre. Cosine Similarity akan digunakan untuk mengukur seberapa mirip satu film dengan film lain berdasarkan representasi vektornya
- Pendekatan Collaborative Filtering menggunakan model Deep learning ini akan memanfaatkan data rating dari pengguna lain untuk memberikan rekomendasi film. Dengan menggunakan Deep Learning, sistem akan mencari pengguna dengan pola rating yang mirip dan merekomendasikan film yang disukai oleh pengguna-pengguna tersebut.

## Data Understanding
Pada proyek ini dataset yang digunakan diambil dari repository terbuka GrubLens yaitu [MovieLens 20M Dataset](https://grouplens.org/datasets/movielens/20m/)

Dataset tersebut kumpulan dari rating dan tag dari MovieLens, sebuah layanan rekomendasi film. Kumpulan data tersebut berisi 20000263 peringkat dan 465564 aplikasi penandaan pada 27278 film. Data ini dibuat oleh 138493 pengguna antara 09 Januari 1995 dan 31 Maret 2015. Kumpulan data ini dibuat pada 17 Oktober 2016. Pengguna dipilih secara acak untuk diikutsertakan. Semua pengguna yang dipilih telah menilai sedikitnya 20 film. Terdapat 5 file dalam dataset tersebut yaitu genome_scores.csv, genome_tags.csv, link.csv, movie.csv, rating.csv, tag.csv namun pada proyek ini hanya mengunakan movie.csv dan rating.csv saja untuk sistem rekomendasi.

## Deskripsi Variabel

Variabel-variabel yang digunakan pada MovieLens 20M Dataset  adalah sebagai berikut:

**movie.csv**
- movieId : id unik untuk setiap film
- title : judul/nama film dan terdapat tahun
- genres : genre dari film yang dipisahkan dengan "|"

**rating.csv**
- userId : id unik dari user
- movieId : id unik dari film yang diberi rating
- rating : nilai/score yang diberikan user untuk film
- timestamp : waktu dan tanggal user memberikan rating 

## Exploratory Data Analysis

**Informasi Dataset**

Setelah memahami deskripsi variabel pada data, langkah selanjutnya adalah mengecek informasi pada dataset dengan fungsi info() berikut.

![{6578159A-38A3-4526-A2CD-0357D8A1874E}](https://github.com/user-attachments/assets/48bf254c-0d98-4192-befd-f928288468d8)
- Jumlah Data
  
  | Baris | Kolom | Data Null |
  |-------|-------|-----------|
  | 27278 | 3    | 0 |
- Terdapat 1 kolom dengan tipe data int64 yaitu movieId
- Terdapat 2 kolom dengan tipe object, yaitu: title dan genres
  
![{D80EF645-9423-462C-A0F1-4B2ADBD32016}](https://github.com/user-attachments/assets/d8f90dd9-17c8-42ef-a9b4-9e98fd6de369)
- Jumlah Data
  
  | Baris | Kolom | Data Null |
  |---------|------|----------|
  | 1075214 | 4    | 0 |
- Terdapat 2 kolom dengan tipe data float64 yaitu movieId dan UserId
- Terdapat 1 kolom dengan tipe data int64 yaitu rating
- Terdapat 1 kolom dengan tipe object, yaitu: timestamp

**Statistik Deskripsi**

Uraian di atas menunjukkan bahwa setiap kolom telah memiliki tipe data yang sesuai. Selanjutnya, Anda perlu mengecek deskripsi statistik data dengan fitur describe()

![{A72060BA-6BAC-4228-A0D3-3AC8AD8A4E6C}](https://github.com/user-attachments/assets/352d4f51-3337-440d-82ea-5d465bb3cac8)
![{0B3FEE15-BB55-48A9-9543-A50190EE06E0}](https://github.com/user-attachments/assets/4ec49683-4d57-455c-8d95-0a36a7520d98)

Fungsi describe() memberikan informasi statistik pada masing-masing kolom, antara lain:

- Count adalah jumlah sampel pada data.
- Mean adalah nilai rata-rata.
- Std adalah standar deviasi.
- Min yaitu nilai minimum setiap kolom.
- 25% adalah kuartil pertama. Kuartil adalah nilai yang menandai batas interval dalam empat bagian sebaran yang sama.
- 50% adalah kuartil kedua, atau biasa juga disebut median (nilai tengah).
- 75% adalah kuartil ketiga.
- Max adalah nilai maksimum.

**Data Duplikat**
| Nama Dataset | Data Duplikat |
|--------------|---------------|
| movie.csv | 0 |

| Nama Dataset | Data Duplikat |
|--------------|---------------|
| rating.csv | 0 |

**Distribusi Rating**

Visualisasi ini digunakan untuk menunjukkan distribusi pada variabel rating dalam bentuk bar. grafik ini memberikan gambaran yang jelas tentang proporsi rating dalam dataset

![{0473247A-88E3-40B9-9161-79EA6FF2265E}](https://github.com/user-attachments/assets/c658c38a-6198-4203-bae7-908513d90248)

Dari grafik tersebut diketahui bahwa paling banyak user meberikan rating mendekati 4 dan disusul mendekati 3.

**Correlation Analysis**

Membuat HeatMap untuk menampilkan korelasi matrik antar kolom pada dataset

![image](https://github.com/user-attachments/assets/409ad036-f038-48b4-8191-283ef153cf20)

Tidak ada hubungan yang signifikan antara variabel-variabel ini dalam hal pola linear yang dapat diprediksi. Korelasi yang rendah di antara semua pasangan variabel menunjukkan bahwa variabel-variabel tersebut tidak berhubungan secara langsung satu sama lain dalam konteks linier

## Data Preparation

**Teknik Data Preparation**

- Menghapus kolom yang tidak perlu
- Encoding Genres
- Train-Test-Split Data user rating

### Menghapus kolom yang tidak perlu

Pada tahap ini, kolom-kolom yang tidak relevan dengan analisis atau tidak berkontribusi langsung pada model dibuang. Pada proyek ini timestap tidak diperlukan oleh karena itu kita dapat menghapusnya dengan perintah drop().
```python
#menghapus kolom yang tidak digunakan
ratings.drop('timestamp', axis=1, inplace=True)
```
Alasan: Kolom yang tidak relevan atau tidak berguna hanya akan menambah kompleksitas data dan bisa menyebabkan noise yang menurunkan kualitas model.

### Encoding Genres

Genre film sering kali dalam bentuk teks atau string (misalnya, "Action", "Comedy", atau "Drama") atau bahkan dalam bentuk gabungan genre (misalnya, "Action|Adventure|Sci-Fi"). Encoding genre berarti mengonversi teks ini menjadi format numerik yang dapat dipahami oleh algoritma pembelajaran mesin. Salah satu cara encoding genre adalah menggunakan one-hot encoding, di mana setiap genre direpresentasikan sebagai kolom, dan film ditandai dengan "1" jika memiliki genre tersebut, atau "0" jika tidak.

![{C7677066-19F7-4471-85EA-5C2674B87117}](https://github.com/user-attachments/assets/85be709c-9c13-4dbb-b6ac-03df51ad46d7)

Alasan: Algoritma machine learning hanya bekerja dengan data numerik. Encoding genre memungkinkan kita menggunakan informasi kategori ini dalam bentuk numerik yang dapat dipahami model. Selain itu, One-Hot Encoding membantu menghindari kesalahan interpretasi jarak antar kategori yang bisa terjadi dengan Label Encoding (misalnya, jika genre diberi label sebagai 1, 2, atau 3, model mungkin menyalahartikan urutan ini sebagai urutan numerik).
Contoh: Sebuah film dengan genre "Action" dan "Comedy" akan direpresentasikan dengan kolom "Action" dan "Comedy" bernilai 1, sementara kolom genre lain seperti "Drama" dan "Horror" bernilai 0.

### Train-Test-Split Data ID User Rating

Data dibagi menjadi dua bagian train 80% dan test 20%. Data train adalah bagian data yang digunakan untuk melatih model, sementara data test digunakan untuk menguji seberapa baik model melakukan prediksi pada data yang belum pernah dilihatnya
```python
x = fix_rating[['user', 'movie']].values

# Membuat variabel y untuk membuat rating dari hasil
y = fix_rating['rating'].apply(lambda x: (x - min_rating) / (max_rating - min_rating)).values

# Membagi menjadi 80% data train dan 20% data validasi
train_indices = int(0.8 * fix_rating.shape[0])
x_train, x_val, y_train, y_val = (
    x[:train_indices],
    x[train_indices:],
    y[:train_indices],
    y[train_indices:]
)

print(x, y)
```

Alasan: Pembagian data dilakukan untuk mengevaluasi model di data yang tidak digunakan selama pelatihan, dan memastikan bahwa model tersebut memiliki kemampuan generalisasi dan tidak hanya menghafal data training.
Train-test split membantu memeriksa apakah model terlalu cocok dengan data pelatihan (overfitting) atau tidak cukup cocok (underfitting).
Dengan menguji model pada data test, kita dapat memperkirakan seberapa akurat sistem rekomendasi ini jika digunakan dalam situasi nyata, yaitu memberikan rekomendasi kepada pengguna baru atau film baru yang tidak terlihat oleh model selama pelatihan.



## Modeling
Pada tahapan model yang digunakan terdiri dari:
- Content-Based Filltering (Cosine Similarity)
- Colaborative Filltering (RecomenderNet)

### Content-Based Filtering

Content-based filtering adalah metode rekomendasi yang didasarkan pada atribut atau karakteristik dari item yang diinginkan. Sistem ini menganalisis konten atau karakteristik item (misalnya, genre film, penulis buku, atau topik artikel) dan mencocokkannya dengan preferensi pengguna yang sebelumnya ditetapkan. Setiap item akan diwakili dalam bentuk vektor fitur, dan sistem akan mencoba merekomendasikan item yang memiliki kesamaan fitur yang tinggi dengan item yang disukai oleh pengguna sebelumnya.

**Kelebihan:**

- Personalisasi: Setiap pengguna menerima rekomendasi unik berdasarkan preferensi pribadinya.
- Kemandirian Data: Tidak memerlukan data dari pengguna lain, sehingga cocok untuk konteks di mana interaksi antar pengguna terbatas.
- Tidak Terkena Cold Start: Tidak terpengaruh oleh masalah cold start karena rekomendasi dibuat berdasarkan atribut item, bukan riwayat pengguna.

**Kekurangan:**

- Overspecialization: Sering kali hanya merekomendasikan item yang terlalu mirip, sehingga pengguna mungkin tidak akan menemukan hal-hal baru di luar preferensi mereka yang jelas.
- Kesulitan Menangani Atribut Kompleks: Ketika item tidak memiliki atribut yang mudah diidentifikasi (misalnya, rasa dalam makanan atau preferensi seni abstrak), sulit bagi sistem untuk memberikan rekomendasi yang tepat.
- Pengekangan pada Data Fitur: Performa tergantung pada ketersediaan dan kualitas atribut yang telah ditetapkan untuk setiap item.

### Cosine Similarity

Cosine similarity adalah metode pengukuran kesamaan antara dua vektor dalam ruang multidimensi, dengan menghitung sudut kosinus di antara keduanya. Pada kasus sistem rekomendasi, dua vektor ini biasanya mewakili profil pengguna dan item, atau dua item yang ingin dibandingkan. Semakin kecil sudut antara dua vektor, semakin tinggi nilai cosine similarity (mendekati 1), yang menunjukkan bahwa kedua vektor memiliki arah yang hampir sama.
​

$$cosine(A,B) = \frac{A.B}{|A||B|}$$
 
**Kelebihan:**
- Sederhana dan Efisien: Mudah dihitung dan sangat efisien secara komputasi, terutama untuk vektor berdimensi tinggi yang tipikal dalam data teks dan rekomendasi.
- Tidak Bergantung pada Panjang Vektor: Menghitung sudut antar vektor membuat cosine similarity menjadi robust terhadap panjang vektor yang berbeda, ideal untuk data teks atau preferensi pengguna.
- Cocok untuk Data Sparsity: Bekerja baik pada data yang sparse (jarang terisi), seperti dalam kasus profil pengguna dan data rekomendasi.

**Kekurangan:**
- Tidak Memperhitungkan Bobot Fitur Secara Absolut: Hanya mempertimbangkan arah vektor, bukan besarnya. Dua vektor dengan arah yang sama tapi panjang yang berbeda akan tetap dianggap serupa.
- Tidak Cocok untuk Data Negatif: Untuk kasus yang memiliki data negatif (misalnya preferensi negatif atau sentimen negatif), cosine similarity mungkin tidak menghasilkan hasil yang akurat.
- Tidak Berbasis Non-Linear: Sebagai pengukuran linear, cosine similarity tidak menangkap pola kesamaan non-linear antara data, yang bisa mengurangi akurasi rekomendasi.

## Evaluation
Pada bagian ini Anda perlu menyebutkan metrik evaluasi yang digunakan. Kemudian, jelaskan hasil proyek berdasarkan metrik evaluasi tersebut.

Ingatlah, metrik evaluasi yang digunakan harus sesuai dengan konteks data, problem statement, dan solusi yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan formula metrik dan bagaimana metrik tersebut bekerja.

**---Ini adalah bagian akhir laporan---**

_Catatan:_
- _Anda dapat menambahkan gambar, kode, atau tabel ke dalam laporan jika diperlukan. Temukan caranya pada contoh dokumen markdown di situs editor [Dillinger](https://dillinger.io/), [Github Guides: Mastering markdown](https://guides.github.com/features/mastering-markdown/), atau sumber lain di internet. Semangat!_
- Jika terdapat penjelasan yang harus menyertakan code snippet, tuliskan dengan sewajarnya. Tidak perlu menuliskan keseluruhan kode project, cukup bagian yang ingin dijelaskan saja.
