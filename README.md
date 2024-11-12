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


![{2534709A-7324-44B5-AC85-A9DF9D0CEDF7}](https://github.com/user-attachments/assets/d1f88ec3-3330-4217-86ba-f22040fd68e3)
 
**Kelebihan:**
- Sederhana dan Efisien: Mudah dihitung dan sangat efisien secara komputasi, terutama untuk vektor berdimensi tinggi yang tipikal dalam data teks dan rekomendasi.
- Tidak Bergantung pada Panjang Vektor: Menghitung sudut antar vektor membuat cosine similarity menjadi robust terhadap panjang vektor yang berbeda, ideal untuk data teks atau preferensi pengguna.
- Cocok untuk Data Sparsity: Bekerja baik pada data yang sparse (jarang terisi), seperti dalam kasus profil pengguna dan data rekomendasi.

**Kekurangan:**
- Tidak Memperhitungkan Bobot Fitur Secara Absolut: Hanya mempertimbangkan arah vektor, bukan besarnya. Dua vektor dengan arah yang sama tapi panjang yang berbeda akan tetap dianggap serupa.
- Tidak Cocok untuk Data Negatif: Untuk kasus yang memiliki data negatif (misalnya preferensi negatif atau sentimen negatif), cosine similarity mungkin tidak menghasilkan hasil yang akurat.
- Tidak Berbasis Non-Linear: Sebagai pengukuran linear, cosine similarity tidak menangkap pola kesamaan non-linear antara data, yang bisa mengurangi akurasi rekomendasi.

### Top-N Recomendation Content-Based Filltering
![{A72DF3AA-FD37-4CBC-90C6-394A031417AD}](https://github.com/user-attachments/assets/4d000746-55d1-4141-a82f-87d7649a82bc)

### Collaborative Filtering
Collaborative filtering adalah metode sistem rekomendasi yang didasarkan pada data preferensi pengguna lainnya. Algoritma ini bekerja dengan asumsi bahwa jika sekelompok pengguna memiliki minat yang serupa, maka mereka cenderung menyukai item yang serupa juga. Collaborative filtering menggunakan data interaksi antar pengguna dan item untuk menemukan pola kesukaan. Terdapat dua jenis pendekatan utama:

**Kelebihan:**
- Rekomendasi yang Lebih Bervariasi: Dapat menemukan preferensi item yang berbeda dari item-item yang sudah pernah dilihat atau disukai pengguna, memungkinkan penemuan konten baru.
- Tidak Memerlukan Data Atribut: Tidak membutuhkan informasi tentang fitur item; cukup dengan data interaksi antar pengguna dan item.
- Menangani Preferensi Implisit: Bisa menggunakan data seperti rating, pembelian, atau waktu menonton sebagai preferensi, tanpa memerlukan pengaturan eksplisit dari pengguna.

**Kekurangan:**
- Masalah Cold Start: Memerlukan data interaksi awal dari pengguna atau item. Pengguna baru atau item baru akan sulit direkomendasikan karena kurangnya data.
- Data Sparsity: Dalam sistem besar, banyak pengguna dan item yang memiliki sedikit atau bahkan tidak ada data interaksi, membuat pola rekomendasi sulit ditemukan.
- Skalabilitas: Memerlukan komputasi yang cukup intensif terutama jika terdapat jutaan pengguna atau item, sehingga membutuhkan pengelolaan data dan pemrosesan yang efisien.

### RecommenderNet
RecommenderNet adalah pendekatan sistem rekomendasi berbasis neural network (jaringan saraf) yang dapat dikustomisasi sesuai dengan data dan kebutuhan sistem rekomendasi tertentu. Algoritma ini menggunakan jaringan saraf untuk menemukan pola preferensi dalam data pengguna dan item. Dengan memanfaatkan model deep learning, seperti embedding untuk pengguna dan item, RecommenderNet dapat menangkap pola kompleks yang ada dalam data.

Biasanya, model RecommenderNet diimplementasikan dengan lapisan embedding untuk mewakili pengguna dan item, yang dilatih menggunakan data interaksi (misalnya rating atau klik). Model ini akan memprediksi skor relevansi antara pengguna dan item yang kemudian dapat digunakan untuk rekomendasi. Karena menggunakan deep learning, RecommenderNet dapat dioptimalkan dengan teknik backpropagation untuk meningkatkan akurasi rekomendasi.

![{92288106-5E22-42C6-A95B-1F3B5DFA259C}](https://github.com/user-attachments/assets/067d90a4-d3d0-43c7-90fd-bb63db79a85b)

**Kelebihan:**
- Dapat Menangkap Pola Non-Linear: Berbeda dengan pendekatan konvensional seperti collaborative filtering, RecommenderNet mampu menangkap pola kompleks dalam data, sehingga menghasilkan rekomendasi yang lebih akurat.
- Kustomisasi Tinggi: RecommenderNet dapat disesuaikan dengan berbagai jenis data dan tipe interaksi, serta memungkinkan integrasi atribut tambahan dari pengguna atau item.
- Mengatasi Masalah Cold Start Lebih Baik: Dengan menggunakan fitur tambahan dari pengguna dan item (seperti embedding yang dikustomisasi), RecommenderNet dapat memberikan rekomendasi bahkan untuk pengguna atau item baru, dengan hasil yang lebih baik daripada collaborative filtering klasik.

**Kekurangan:**
- Kebutuhan Data Latihan Besar: RecommenderNet bekerja dengan baik pada data berukuran besar, sehingga sulit diimplementasikan pada sistem dengan data terbatas.
- Komputasi Intensif: Karena menggunakan deep learning, model ini memerlukan sumber daya komputasi yang tinggi baik dalam hal waktu maupun kebutuhan memori untuk pelatihan model.
- Tuning Model yang Kompleks: Memerlukan keterampilan dan waktu untuk mengatur serta men-tune hyperparameter, arsitektur model, dan proses pelatihan agar mendapatkan hasil optimal.

## Top-N Recomendation Colaborative Filltering
```
Menampilkan rekomendasi untuk pengguna: 5904
=============================================
Film dengan rating tertinggi dari pengguna
---------------------------------------------
Silence of the Lambs, The (1991)  :  Crime|Horror|Thriller
Cool Hand Luke (1967)  :  Drama
Young Frankenstein (1974)  :  Comedy|Fantasy
Indiana Jones and the Last Crusade (1989)  :  Action|Adventure
For a Few Dollars More (Per qualche dollaro in più) (1965)  :  Action|Drama|Thriller|Western
---------------------------------------------
Rekomendasi 10 film teratas
---------------------------------------------
Dr. Strangelove or: How I Learned to Stop Worrying and Love the Bomb (1964) : Comedy|War
Twelfth Night (1996) : Comedy|Drama|Romance
It Happened One Night (1934) : Comedy|Romance
Cinema Paradiso (Nuovo cinema Paradiso) (1989) : Drama
Wings of Desire (Himmel über Berlin, Der) (1987) : Drama|Fantasy|Romance
Godfather: Part II, The (1974) : Crime|Drama
Bull Durham (1988) : Comedy|Drama|Romance
Eraserhead (1977) : Drama|Horror
Spy Game (2001) : Action|Crime|Drama|Thriller
Walk the Line (2005) : Drama|Musical|Romance
```

## Evaluation

Pada project ini ada 2 matrix yang digunakan untuk mengevaluasi model yaitu Precision dan RMSE (Root Mean Squared Error) dengan penjelasan seeperti berikut

### Evaluasi Cosine Similiarity
Model ini hanya menggunakan metrik Precision untuk mengetahui seberapa baik perforam model tersebut. Presisi adalah metrik yang biasa digunakan untuk mengevaluasi kinerja model pengelompokan. Metrik ini menghitung rasio antara nilai ground truth (nilai sebenarnya) dengan nilai prediksi yang positf. Perhitungan rasio ini dijabarkan melalui rumus di bawah ini:

$$Precision= \frac{TP}{TP+FP}$$

**Dimana:**
- TP (True Positive), jumlah kejadian positif yang diprediksi dengan benar.
- FP (False Positive), jumlah kejadian positif yang diprediksi dengan salah.

Berdasarkan hasil yang terdapat pada tahap Model and Result dapat dilihat bahwasanya besar presisi jika dihitung adalah 10/10 untuk rekomendasi Top-10. Ini menunjukan sistem mampu memberikan rekomendasi sesuai dengan Genres Filmnya.

### Evaluasi Model RecommenderNet

Root Mean Squared Error (RMSE) adalah akar kuadrat dari rata-rata kuadrat kesalahan. Ini memberikan gambaran seberapa jauh prediksi model berbeda dari nilai sebenarnya dalam satuan yang sama dengan variabel yang diprediksi. RMSE sangat berguna karena memberikan penalti lebih besar untuk kesalahan yang lebih besar.

$$
\text{RMSE} = \sqrt{\frac{1}{n} \sum_{i=1}^{n} (y_i - \hat{y}_i)^2}
$$

**Di mana:**
- $y_i$ adalah nilai sebenarnya
- $y_i$ adalah nilai prediksi
- $n$ adalah jumlah observasi
- RMSE yang kecil mengindikasikan bahwa model memiliki performa yang baik karena kesalahan antara prediksi dan nilai aktual rendah.
- RMSE yang besar mengindikasikan bahwa model memiliki performa yang buruk karena kesalahan antara prediksi dan nilai aktual tinggi.

![{57606E97-35D7-41FB-90A4-2CF490083E37}](https://github.com/user-attachments/assets/8a0a4d37-0a3c-4f87-b480-7abbc6129fd6)

**Hasil Proyek**
|            | Train  | Test  |
|------------|------- |-------|
| RMSE       | 0.105 | 0.270|

RMSE yang dihitung memberikan indikasi bahwa model prediksi rating memiliki tingkat kesalahan yang dapat diterima, sehingga memadai untuk tujuan rekomendasi.

## Kesimpulan
Dari hasil evaluasi, solusi sistem rekomendasi dengan pendekatan Content-Based Filtering dengan model Cosine Similarity dan Collaborative Filtering menggunakan model RecommenderNet menunjukkan bahwa kedua pendekatan ini berhasil mencapai tujuan proyek. Content-Based Filtering dengan model Cosine Similiarity memberikan rekomendasi film yang relevan berdasarkan kesamaan genre dengan presisi tinggi, mencapai rekomendasi Top-10 yang sesuai kategori. Sementara itu, pendekatan Collaborative Filtering dengan model RecommenderNet menghasilkan rekomendasi film berdasarkan pola rating pengguna dengan error yang rendah (RMSE sekitar 0.105 untuk data training dan 0.270 untuk data validasi), menunjukkan kemampuannya dalam memprediksi preferensi pengguna dengan akurat. Secara keseluruhan, kedua pendekatan ini berhasil memberikan rekomendasi yang relevan dan sesuai dengan tujuan utama, yaitu menyediakan rekomendasi film yang sesuai dengan preferensi genre dan pola rating pengguna.
