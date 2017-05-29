---
layout: post
title:  "Metodologi Information Extraction dari Berbagai Tipe Dokumen"
date:   2017-05-29 20:47:33 +0700
---

!https://github.com/IftitakhulZakiah/iftitakhulzakiah.github.io/blob/master/picture/1.png!

p<>. Information Extraction merupakan salah satu topik dari Natural Language Processing atau biasa disebut NLP yang secara otomatis mengekstraksi informasi yang tidak berstruktur / semi-struktur. Sebagai contohnya adalah memproses dokumen multimedia seperti menambahkan keterangan secara otomatis dan mengekstraksi konten dari gambar/suara/video kemudian diambil informasi penting dari media tersebut. Selain itu, information extraction juga bisa diaplikasikan pada web/aplikasi yang berbasis teks misalnya untuk menggabungkan informasi produk dari berbagai website, menjawab pertanyaan, mencari kontak infomasi, mencari artikel yang membahas tentang protein dari jurnal biomedis, maupun menghapus the noisy data.

p<>. Ada banyak metodologi yang digunakan untuk berbagai tipe dokumen(termasuk plain text, halaman web, email, dll). Akan tetapi  yang menjadi fokus hanya tiga metodologi yaitu rule learning based method, classification model based method, dan sequential labeling based method. Semua metode ini terdiri dari dua tahap yaitu ekstraksi dan pelatihan.

##1.Rule Learning Based Extraction Methods
p<>. Secara umum, metode ini dibagi menjadi tiga kategori, yaitu :
#a.Dictionary based method
p<>. Sistem information extraction yang pertama dikonstruksi dengan pola/template dictionary (kamus) yang kemudian dari dictionary tersebut didapatkan ekstraksi informasi dari teks yang tidak ditandai. Key point dari sistem ini adalah bagaimana sistem belajar dari pola dictionary yang kemudian dapat digunakan untuk mengidentifikasi informasi yang relevan dari teks.
AutoSlog merupakan sistem pertama yang mempelajari kamus ektraksi teks dari contoh-contoh pelatihan. AutoSlog membangun kamus pola ekstraksi dengan menggunakan concept nodes.
#b.Rule based method
p<>. Berbeda dengan dictionary based method, metode ini menggunakan beberapa aturan umum sebagai pengganti dictionary untuk mengekstrak informasi dari teks dan kebanyakan digunakan untuk website yang semi-struktur. Dua algoritma utama yang digunakan untuk mempelajari aturan yaitu bottom-up method dan top-down method. Bottom-up method mempelajari aturan dari kasus yang khusus ke umum. Sedangkan top-down method mempelajari aturan dari yang umum ke yang lebih spesifik. Ada beberapa jenis algoritma yang digunakan, seperti (LP)^2^,  iASA, Whisk, Rapier, dan SRV. 
p<>. Misalnya pada (LP)^2^, algoritma ini merupakan salah satu yang bertipe bottom-up method dengan mempelajari dua jenis aturan identifikasi batas awal dan batas akhir teks yang akan diekstraksi. Tiga tipe aturan yang terdapat pada (LP)^2^ : tagging rules, contextual rules, dan correction rules. Tagging rules terbentuk dari pola kondisi yang terhubung dari serangkaian kata dan sebuah aksi yang menjelaskan apakah posisi saat ini berada pada batas atau tidak. Contextual rules diaplikasikan untuk mengembangkan efektifisitas sistem. Dan correction rules digunakan untuk mengurangi ketidakpresisian dari tagging rules.
Setelah semua tipe aturan sudah ada, langkah information extraction ialah :
* Tagging rules digunakan untuk menandai teks.
* Contextual rules diaplikasikan di tag konteks awal pada langkah pertama.
* Correction rules digunakan untuk mengoreksi kesalahan ekstraksi.
* Semua batasan yang telah teridentifikasi kemudian divalidasi. 
#c.Wrapper induction
p<>. Metode ini digunakan untuk halaman web yang terstruktur dan semi-struktur. Wrapper adalah sebuah prosedur ekstraksi yang terdiri dari himpunan aturan ekstraksi dan juga kode program yang digunakan untuk mengaplikasikan aturan tersebut. Sedangkan wrapper induction adalah teknik  yang otomatis dipelajari oleh wrapper. Ada beberapa contoh sistem wrapper induction, misalnya  WIEN dan BWI. WIEN merupakan sistem wrapper induction yang pertama. Pada sistem Boosted Wrapper Induction (BWI) , teknik yang digunakan untuk wrapper induction dibuat agar cocok bagi teks yang menggunakan boosting untuk menggeneralisasi dan mengombinasi prediksi dari pola ekstraksi numerik.


##2.Classification based extraction methods
#a.Classification model
p<>. Sebuah classification model biasanya terdiri dari dua tahap yaitu mempelajari dan memprediksi. Support Vector Machines(SVM) merupakan metode yang paling popular untuk klasifikasi. 
#b.Boundary detection menggunakan classification model
p<>. Pendekatan information extraction secara sederhana belajar untuk mendeteksi awal dan akhir dari potongan teks yang diekstraksi. Menggunakan information extraction sebagai standard classification task, ditambah dengan mekanisme yang sederhana untuk mengombinasikan prediksi mulai dan tag akhir. Percobaan ini mengindikasikan bahwa pendekatan seperti ini memiliki tingkat presisi yang tinggi tapi rendah recall.
p<>. Selain itu, classification based extraction methods juga dapat ditingkatkan lagi dengan two-level boundary classification model dan juga unbalance classification model.


##3.Sequential Labeling based Extraction Methods
p<>. Dalam sequential labeling, sebuah dokumen dilihat sebagai sekumpulan token yang terurut dan sebuah urutan dari label-label ditugaskan untuk masing-masing token untuk mengindikasi sifat token tersebut.
Berbeda dengan kedua metodologi disebelumnya, sequential labeling dapat menjelaskan hubungan ketergantungan antar target informasi. Keterhubungan ini dapat digunakan untuk mengembangkan akurasi dari ekstraksi. Hidden Markov Model, Maximum Entropy Markov Model, dan Conditional Random Field digunakan untuk model sequential labeling.
#a.Generative Model
p<>. Generative model didefinisikan sebagai peluang distribusi gabungan p(X,Y) dimana X dan Y merupakan variabel random yang menunjukkan urutan pengamatan dan urutan corresponding label. Hidden Markov Model (HMMs) adalah salah satu model yang biasa digunakan untuk generative model. Pada HMMs, setiap urutan pengamatan mempertimbangkan agar dapat digeneralisasi oleh urutan state transitions, dimulai dari start state, dan berakhir saat beberapa state final dicapai.
#b.Discriminative models
p<>. Didefinisikan sebagai sebuah distribusi kondisional yang menggunakan pengamatan dan urutan label. Maknanya adalah saat mengidentifikasi, hampir semua urutan label digunakan untuk memberikan urutan pengamatan, discriminative models menggunakan distribusi kondisional secara langsung, tanpa mengganggu ketergantungan asumsi pada pengamatan atau menghitung semua kemungkinan urutan pengamatan untuk menjumlahkan peluang marginal.  Maximum Entropy Markov Model(MEMMs) merupakan salah satu bentuk discriminative models untuk sequential labeling.
#c.Conditional Random Fields (CRFs)
p<>. CRFs adalah model grahic yang secara tidak langsung dilatih untuk memaksimalkan sebuah peluang kondisional.

!https://github.com/IftitakhulZakiah/iftitakhulzakiah.github.io/blob/master/picture/3.png!

Referensi :
[Wikipedia – Information Extraction](https://en.wikipedia.org/wiki/Information_extraction)
[Information extraction (Tang et al)](http://keg.cs.tsinghua.edu.cn/jietang/publications/Tang-et-al-Information_Extraction.pdf) 
