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

Pada bagian ini, Anda perlu menjelaskan proses klarifikasi masalah.

Bagian laporan ini mencakup:

### Problem Statements

Menjelaskan pernyataan masalah:
- Pernyataan Masalah 1
- Pernyataan Masalah 2
- Pernyataan Masalah n

### Goals

Menjelaskan tujuan proyek yang menjawab pernyataan masalah:
- Jawaban pernyataan masalah 1
- Jawaban pernyataan masalah 2
- Jawaban pernyataan masalah n

Semua poin di atas harus diuraikan dengan jelas. Anda bebas menuliskan berapa pernyataan masalah dan juga goals yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**:
- Menambahkan bagian “Solution Approach” yang menguraikan cara untuk meraih goals. Bagian ini dibuat dengan ketentuan sebagai berikut: 

    ### Solution statements
    - Mengajukan 2 atau lebih solution approach (algoritma atau pendekatan sistem rekomendasi).

## Data Understanding
Paragraf awal bagian ini menjelaskan informasi mengenai jumlah data, kondisi data, dan informasi mengenai data yang digunakan. Sertakan juga sumber atau tautan untuk mengunduh dataset. Contoh: [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/Restaurant+%26+consumer+data).

Selanjutnya, uraikanlah seluruh variabel atau fitur pada data. Sebagai contoh:  

Variabel-variabel pada Restaurant UCI dataset adalah sebagai berikut:
- accepts : merupakan jenis pembayaran yang diterima pada restoran tertentu.
- cuisine : merupakan jenis masakan yang disajikan pada restoran.
- dst

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
