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

**Rubrik/Kriteria Tambahan (Opsional)**:
- Melakukan beberapa tahapan yang diperlukan untuk memahami data, contohnya teknik visualisasi data beserta insight atau exploratory data analysis.

## Data Preparation
Pada bagian ini Anda menerapkan dan menyebutkan teknik data preparation yang dilakukan. Teknik yang digunakan pada notebook dan laporan harus berurutan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan proses data preparation yang dilakukan
- Menjelaskan alasan mengapa diperlukan tahapan data preparation tersebut.

## Modeling
Tahapan ini membahas mengenai model sisten rekomendasi yang Anda buat untuk menyelesaikan permasalahan. Sajikan top-N recommendation sebagai output.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menyajikan dua solusi rekomendasi dengan algoritma yang berbeda.
- Menjelaskan kelebihan dan kekurangan dari solusi/pendekatan yang dipilih.

## Evaluation
Pada bagian ini Anda perlu menyebutkan metrik evaluasi yang digunakan. Kemudian, jelaskan hasil proyek berdasarkan metrik evaluasi tersebut.

Ingatlah, metrik evaluasi yang digunakan harus sesuai dengan konteks data, problem statement, dan solusi yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan formula metrik dan bagaimana metrik tersebut bekerja.

**---Ini adalah bagian akhir laporan---**

_Catatan:_
- _Anda dapat menambahkan gambar, kode, atau tabel ke dalam laporan jika diperlukan. Temukan caranya pada contoh dokumen markdown di situs editor [Dillinger](https://dillinger.io/), [Github Guides: Mastering markdown](https://guides.github.com/features/mastering-markdown/), atau sumber lain di internet. Semangat!_
- Jika terdapat penjelasan yang harus menyertakan code snippet, tuliskan dengan sewajarnya. Tidak perlu menuliskan keseluruhan kode project, cukup bagian yang ingin dijelaskan saja.
