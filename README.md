# Airbnb Listing Bangkok

#Background
Airbnb adalah platform global yang menghubungkan orang yang mencari tempat tinggal sementara dengan tuan rumah yang menyewakan properti mereka. Di Bangkok, yang merupakan salah satu destinasi wisata populer di dunia, Airbnb memainkan peran penting dalam menyediakan akomodasi alternatif bagi wisatawan. Dengan ribuan tempat penginapan yang tersedia, pemahaman mendalam tentang faktor-faktor yang mempengaruhi harga, ketersediaan, dan popularitas tempat penginapan sangat penting bagi tuan rumah untuk mengoptimalkan pendapatan mereka, serta bagi perusahaan untuk meningkatkan layanan mereka.

Dataset yang digunakan dalam analisis ini berisi informasi tentang listing Airbnb di Bangkok, termasuk detail seperti harga per malam, tipe kamar, jumlah ulasan, tanggal ulasan terakhir, dan ketersediaan. Memahami data ini dapat memberikan wawasan berharga mengenai faktor-faktor yang mempengaruhi kinerja tempat penginapan, dan dapat digunakan untuk memberikan rekomendasi bisnis kepada tuan rumah atau bahkan untuk meningkatkan algoritma penentuan harga dinamis Airbnb.

#Problem Statment
Seorang pengusaha baru ingin membuat sebuah penginapan di daerah Bangkon, Thailand. Namun sebelum pengusaha ini membuat sebuah penginapannya, pengusaha ini ingin mecari tahu tentang tipe kamar apa saja yang paling populer didaerah Bangkok, Thailand. Serta pengusaha ini ingin mengetahui terlebih dahulu sebaran kompetitor lainnya yang ada pada Bangkok, Thailand. Tidak hanya disitu, pengusaha ini ingin mengetahui juga apakah harga Airbnb di daerah Bangkok, Thailand ini berpengaruh dalam popularitas penginapan yang ada.

# Instal Library yang dibutuhkan
1. instal matplotlib: %pip install matplotlib
2. Instal seaborn: %pip install seaborn
3. Instal missingno: %pip install missingno
4. Instal pandas: %pip install pandas
5. Instal numpy: %pip install numpy
6. Install scipy: %pip install scipy

# Import Library Yang Dibutuhkan
1. import matplotlib.pyplot as plt #Lebih basic untuk customisasi
2. import seaborn as sns #library baru yang dibuat oleh matplotlib --> Banyak yang sudah otomasi
3. import missingno #library untuk menampilkan matriks yang menunjukkan pola data yang hilang di dataset
4. import pandas as pd 
5. import numpy as np
6. import matplotlib.pyplot as plt #menyediakan serangkaian fungsi yang mirip dengan MATLAB untuk membuat berbagai jenis visualisasi data, seperti grafik, plot, histogram
7. import seaborn as sns #memudahkan pembuatan visualisasi statistik
8. from scipy.stats import kstest # Uji Statistika Kolmogorov Smirnov
9. from scipy.stats import shapiro # Uji Statistika Shapiro Wilk
10. from statsmodels.stats.diagnostic import lilliefors #Uji Statistika lilliefors
11. from scipy.stats import normaltest # Uji Statistika D'Agustino Pearson
12. from scipy import stats # Z-score

# Dictionary
| Coloum | Description |
|------|--------------|
| id | Identifikasi unik untuk setiap listing di Airbnb. |
| name | Nama dari listing tersebut. |
| host_id | Identifikasi unik untuk setiap host atau pengguna di Airbnb. |
| host_name | Nama dari host, biasanya hanya nama depan. |
| neighborhood | Nama lingkungan berdasarkan geocode dari latitude dan longitude yang sesuai dengan bentuk digital publik. |
| latitude & longitude | Koordinat geografis menggunakan sistem World Geodetic System (WGS84). |
| room_type | Tipe ruangan, seperti Entire home/apt, Private room, Shared room, atau Hotel. |
| | **Entire home/apt** : pilihan terbaik jika mencari suasana seperti di rumah sendiri. Akan mendapatkan seluruh ruang untuk diri sendiri, termasuk kamar tidur, kamar mandi, dapur, dan pintu masuk terpisah. Host harus mencantumkan di deskripsi apakah mereka tinggal di properti atau tidak, dan memberikan detail lebih lanjut dalam listing. |
| | **Private rooms** : Private rooms cocok jika menginginkan privasi namun tetap ingin terhubung dengan penduduk lokal. Dengan memesan Private rooms, akan mendapatkan kamar tidur pribadi dan mungkin harus berbagi beberapa ruang dengan orang lain. Anda mungkin perlu melewati ruang bersama yang bisa ditempati oleh host atau tamu lain untuk mencapai kamar. |
| | **Shared rooms** : Kamar ini dibuat dengan konsep berbagi ruang dengan orang lain. Dengan memesan Shared rooms, kita akan tidur di ruang yang dibagi dengan orang lain dan berbagi seluruh ruang dengan orang lain. Shared rooms populer di kalangan pelancong yang fleksibel, mencari teman baru, dan penginapan yang ramah anggaran |
| | **Hotel rooms** kamar hotel memberikan level layanan dan keramahtamahan layaknya hotel konvensional. Kamar ini tersedia di hotel butik atau hotel gaya hidup, hostel, bed and breakfast, atau properti serupa. Tipe kamar ini biasanya menyertakan area bersama yang semarak dan ruangan dengan sentuhan unik. (source: [Airbnb](https://www.airbnb.co.id/help/article/5))|
| price | Harga harian dalam mata uang lokal. |
| minimum_nights | Jumlah minimal malam yang harus diambil untuk listing tersebut. |
| number_of_reviews | Jumlah total ulasan yang telah diterima oleh listing tersebut. |
| last_review | Tanggal ulasan terakhir yang diterima oleh listing tersebut. |
| reviews_per_month | review yang diberikan setiap bulannya atau  Rata-rata ulasan per bulan. |
| calculated_host_listings_count |  listing yang dimiliki oleh host di wilayah tersebut pada waktu pengambilan data.|
| availability_365 | Ketersediaan listing selama 365 hari ke depan. |
| number_of_reviews_ltm | Jumlah ulasan yang diterima listing dalam 12 bulan terakhir.|

# Tahapan Memecahkan Masalah
1. Data Understanding
3. Data Cleaning
4. Data Analysis
