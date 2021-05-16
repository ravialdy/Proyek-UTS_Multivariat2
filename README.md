# Proyek UTS Multivariat 2 : 

## Analisis Klaster Dengan Metode K-Means++ untuk Mengelompokkan Universitas Negeri Pilihan Pertama Berdasarkan Skor UTBK 2019 Pada Rumpun Saintek.

### Latar Belakang :

   Ujian Tulis Berbasis Komputer (UTBK) adalah ajang penyeleksian berbasis komputer untuk lulusan SMA sederajat yang berencana melanjutkan pendidikan ke jenjang Perguruan Tinggi Negeri (PTN). Setelah ujian ini dilaksanakan dan nilainya diumumkan, proses pemilihan PTN pun dilakukan. Proses pemilihan ini berkaitan erat dengan minat, kemampuan peserta, dan kuota yang disediakan PTN untuk tiap-tiap jurusan. Masalah yang sering muncul adalah kebingungan dalam memilih PTN dan ketidakpastian (apakah akan masuk kuota bila mendaftar di PTN impian peserta atau tidak) yang dirasakan peserta ketika menentukan PTN.

### Tujuan Penelitian :

   Oleh karena itu, kami ingin mengelompokkan PTN pilihan pertama berdasarkan skor UTBK saintek yang meliputi kemampuan ipa dan kemampuan dasar. Pengelompokkan didasarkan oleh nilai-nilai yang diujikan tersebut dapat menunjukkan kelompok PTN dengan rata-rata skor tertinggi, sedang, maupun rendah. Hasil dari penelitian ini bisa menjadi bahan pertimbangan dalam pemilihan PTN sehingga diharapkan para peserta UTBK dapat lebih realistis dan dapat memaksimalkan pilihan PTN impian sesuai dengan kemampauan dan kebutuhan peserta UTBK tahun berikutnya.
   
### Metode Penelitian : 

  *K-Means++*. Alasan utama digunakannya metode ini adalah karena metode tersebut dapat menghilangkan salah satu kelemahan dari metode *K-Means* yang dimulai dengan pengacakan centroid di awal sehingga mengakibatkan keluaran yang berbeda-beda jika dijalankan berkali-kali. (Sumber Referensi :  http://ilpubs.stanford.edu:8090/778/1/2006-13.pdf)

#### Link Dataset : https://www.kaggle.com/ekojsalim/indonesia-college-entrance-examination-utbk-2019?select=

#### Bahasa pemrograman : Python dengan platform yang digunakan adalah Google Colaboratory.

### Hasil Penelitian : 

**Penentuan nilai K dengan menggunakan *Elbow Method* dan *Silhouette Score***

Sebelum menggunakan metode unsupervised learning clustering KMeans++, perlu ditentukan suatu nilai K yang tepat. Pertama-tama perlu dihitung skor dari Silhouette untuk tiap nilai K dimulai dari 2 hingga 10. Akan diperoleh hasil sebagai berikut,

![image](https://user-images.githubusercontent.com/68768305/118393857-77a52680-b66b-11eb-9dd1-32ae5c041192.png)

  Perhatikan bahwa PTN dengan rata-rata skor UTBK 2019 tertinggi memiliki rentang skor antara 550 - 600. Rata-rata skor yang dimaksud adalah penjumlahan dari semua skor, baik skor yang berkaitan dengan ipa (Fisika, Matematika Saintek, Kimia, dan Biologi) maupun dasar (Kuantitatif, Penalaran Umum, dan Pengetahuan Umum), kemudian dibagi dengan total pelajaran yang diujikan.Cermati pula bahwa semua PTN dengan rata-rata skor yang tinggi berlokasi di Pulau Jawa atau dengan kata lain tidak ada satu pun PTN luar Pulau Jawa yang termasuk pada kategori ini. Untuk lebih detailnya, akan dijelaskan pada bahasan selanjutnya di tulisan ini. 
 
![image](https://user-images.githubusercontent.com/68768305/118395336-0158f200-b674-11eb-8c05-367dfab1a052.png)

Dapat dilihat dari gambar diatas bahwa *Silhouette score* untuk nilai klaster K = 4 memiliki nilai tertinggi dibandingkan dengan nilai-nilai klaster lainnya. Selain itu, bisa digunakan juga *Elbow Method* dalam menentukan nilai terbaik dari klaster pada kasus ini. Dengan menggunakan bahasa pemrograman python, dapat diperoleh hasil sebagai berikut, 

![image](https://user-images.githubusercontent.com/68768305/118395387-6b719700-b674-11eb-9deb-5f41d8af4858.png)

Cermati gambar diatas. Perhatikan bahwa belokan yang paling tajam pada grafik terjadi ketika nilai dari suatu K atau banyaknya klaster adalah 3. Oleh karena itu, dapat disimpulkan bahwa baik metode *Silhouette score* maupun *Elbow Method* menganjurkan nilai K = 3 atau banyaknya klaster dalam kasus ini sebaiknya 3 buah saja. 

### Analisis Klaster dengan menggunakan KMeans++

Setelah mendapatkan nilai K terbaik, maka dapat dimulai penggunaan metode *Kmeans++* pada data. Pada kasus kali ini, iterasi maksimal yang ditetapkan adalah 100, tingkat toleransi dengan nilai 0.0001, dan nilai *random_state* adalah 42. Dengan menggunakan bahasa pemrograman python, maka akan diperoleh 3 klaster, yakni klaster ke-0 atau kelompok PTN dengan rata-rata skor UTBK rendah, klaster ke-1 atau kelompok PTN dengan rata-rata skor UTBK sedang, dan klaster ke-2 atau kelompok PTN dengan rata-rata skor UTBK tinggi. Daftar PTN pilihan pertama yang termasuk pada klaster ke-0 dapat ditunjukkan oleh gambar di bawah ini, 

![image](https://user-images.githubusercontent.com/68768305/118395529-197d4100-b675-11eb-9217-d2be113aacbc.png)

Sedangkan untuk daftar PTN yang termasuk klaster ke-1 atau kelompok PTN dengan rata-rata skor UTBK sedang dapat dilihat pada gambar di bawah,

![image](https://user-images.githubusercontent.com/68768305/118395579-59dcbf00-b675-11eb-8fc0-9e7ba5ac7963.png)

![image](https://user-images.githubusercontent.com/68768305/118395594-6b25cb80-b675-11eb-9dd2-5d69cc550675.png)

Lalu, untuk daftar PTN yang termasuk klaster ke-2 atau kelompok PTN dengan rata-rata skor UTBK tinggi dapat dilihat pada gambar berikut, 

![image](https://user-images.githubusercontent.com/68768305/118395622-8264b900-b675-11eb-9d19-fe40fd04c8cd.png)

Untuk lebih jelasnya, cermati visualisasi klaster PTN dengan rata-rata skor cukup kurang (klaster ke-0), sedang (klaster ke-1), dan tinggi (klaster ke-2) sebagai berikut, 

![image](https://user-images.githubusercontent.com/68768305/118395637-9a3c3d00-b675-11eb-8885-4b695daf909b.png)

Dapat dilihat pada grafik diatas bahwa untuk klaster ke-2 memiliki rata-rata skor kemampuan dasar dan kemampuan ipa yang tinggi, klaster ke-1 memiliki rata-rata skor kemampuan dasar dan kemampuan ipa yang sedang, sedangkan klaster ke-0 memiliki rata-rata skor kemampuan dasar dan ipa yang cukup rendah dibanding klaster-klaster lainnya. 

### Kesimpulan dan Saran

**Kesimpulan**

* Terdapat kesenjangan yang cukup tinggi antara PTN yang berlokasi di Pulau Jawa dengan yang di luar Pulau Jawa. Hal ini dibuktikan dengan tidak adanya PTN yang berlokasi di luar Pulau Jawa berhasil masuk ke kategori klaster ke-2.
* Proses klasterisasi dengan menggunakan metode KMeans++ didasarkan oleh rata-rata skor UTBK 2019 secara keseluruhan, yakni  penjumlahan dari semua skor, baik skor yang berkaitan dengan ipa (Fisika, Matematika Saintek, Kimia, dan Biologi) maupun dasar (Kuantitatif, Penalaran Umum, dan Pengetahuan Umum), lalu dibagi dengan total pelajaran yang diujikan.

**Saran**

* Pemerintah dapat berfokus pada pembuatan kebijakan-kebijakan yang sekiranya dapat menyetarakan kualitas pendidikan tinggi di luar Pulau Jawa.
* Peneliti lain dapat memperbaiki hasil penelitian ini dengan menggunakan metode-metode clustering yang jauh lebih tepat dan canggih dengan dataset yang kualitasnya baik pula sehingga diharapkan dapat memperoleh suatu hasil klasterisasi yang optimal. 

### Referensi :

* Arthur, D., & Vassilvitskii, S. (2006). k-means++: The advantages of careful seeding. Stanford.
* Rencher, A. C., & Christensen, W. F. (2012). Methods of multivariate analysis. Wiley. Cluster analysis. Ch.15
* Bangun, R. H. (2016). ANALISIS KLASTER NON-HIERARKI DALAM PENGELOMPOKKAN KABUPATEN/KOTA DI SUMATRA UTARA BERDASARKAN FAKTOR PRODUKSI. Agrica Jurnal Agribisnis Sumatra Utara, 4, 54–61. 
* Harususilo, Y. E. (2019, April 10). 8 Fakta UTBK 2019, Cek Jumlah Persaingan Soshum dan Saintek di Sini. KOMPAS.com. https://edukasi.kompas.com/read/2019/04/10/17344491/8 -fakta-utbk-2019-cek-jumlah-persaingan-soshum-dan-saintek-di-sini. [Accessed 16 May 2021].

### Anggota Kelompok 13 Mata Kuliah Multivariat 2: 

* Ravialdy Hidayat (1806232093). E-mail : ravialdy.hidayat@ui.ac.id
* Muhammad Yunus (1806232130). E-mail : muhammad.yunus82@ui.ac.id










