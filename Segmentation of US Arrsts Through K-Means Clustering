## "UNDERSTANDING CRIME DYNAMICS: SEGMENTATION OF US ARRESTS THROUGH K-MEANS CLUSTERING"

USArrests dataset yang tersedia di Kaggle adalah dataset yang berisi data kejahatan di Amerika Serikat pada tahun 1973. Dataset ini terdiri dari 50 negara bagian di Amerika Serikat dan memiliki empat variable :
~ Murder: Tingkat pembunuhan per 100.000 penduduk.
~ Assault: Tingkat serangan (serangan fisik) per 100.000 penduduk.
~ UrbanPop: Persentase populasi perkotaan di setiap negara bagian
~ Rape: Tingkat pemerkosaan per 100.000 penduduk.

 ```R
arrests <- read.csv("~/DAP/arrests/USArrests.csv")
View(arrests)
# Checking the rows and columns
dim(arrests)
# Checking the type of data
str(arrests)
# Check on each feature for missing data
colSums(is.na(arrests))
```


arrests <- read.csv("~/DAP/arrests/USArrests.csv"): Membaca file CSV dan menyimpannya ke dalam variabel arrests.
View(arrests): Menampilkan dataset arrests dalam format tabular untuk memberikan gambaran umum tentang data yang terbaca.
dim(arrests): Menampilkan jumlah baris dan kolom dalam dataset. Hasilnya menunjukkan bahwa dataset memiliki 50 baris dan 5 kolom.
str(arrests): Menampilkan struktur dataset, yaitu tipe data dan struktur variabel. Output menunjukkan ada 5 variabel: X (nama negara bagian), Murder, Assault, UrbanPop, dan Rape. Variabel X adalah karakter, sementara yang lainnya adalah numerik.
colSums(is.na(arrests)): Melakukan pengecekan pada setiap variabel untuk melihat apakah terdapat nilai yang hilang (NA). Hasilnya menunjukkan bahwa tidak ada nilai yang hilang dalam setiap variabel, karena semua nilai adalah 0.


 
arrests$Assault <- as.numeric(arrests$Assault): Mengubah tipe data kolom "Assault" menjadi numerik dengan fungsi as.numeric(). Hal ini mungkin diperlukan jika kolom tersebut dianggap sebagai karakter atau faktor, dan perlu diubah menjadi tipe numerik untuk analisis data.
arrests$UrbanPop <- as.numeric(arrests$UrbanPop): Sama seperti baris sebelumnya, mengubah tipe data kolom "UrbanPop" menjadi numerik dengan fungsi as.numeric().
str(arrests): Menampilkan struktur dataset setelah perubahan dilakukan. Output menunjukkan bahwa variabel Assault dan UrbanPop sekarang memiliki tipe data numerik (num), berbeda dengan sebelumnya yang merupakan tipe data integer (int).

 
install.packages("factoextra"): Perintah ini digunakan untuk mengunduh dan menginstal paket "factoextra" dari repositori CRAN ke dalam lingkungan R Anda. Paket "factoextra" menyediakan berbagai fungsi visualisasi untuk analisis faktor dan analisis clustering dalam R.
library(factoextra): Setelah menginstal paket "factoextra", perintah library() digunakan untuk memuat paket tersebut ke dalam sesi R Anda. Dengan memuat paket, Anda dapat mengakses semua fungsi dan fitur yang disediakan oleh paket "factoextra", termasuk fungsi-fungsi visualisasi seperti fviz_nbclust() untuk menemukan jumlah cluster optimal dan fviz_cluster() untuk visualisasi hasil clustering.
install.packages("cluster") digunakan untuk mengunduh dan menginstal paket R yang disebut "cluster". Paket "cluster" adalah paket dasar yang menyediakan berbagai fungsi dan algoritma untuk analisis clustering dalam R, termasuk algoritma K-Means, hierarchical clustering, fuzzy clustering, dan lainnya.
library(cluster): Paket "cluster" adalah paket dasar untuk analisis clustering di R. Menggunakan perintah library() untuk memuat paket "cluster" memungkinkan akses ke berbagai fungsi dan metode clustering, termasuk fungsi kmeans() yang digunakan untuk melakukan algoritma K-Means clustering pada dataset Anda. Dengan memuat paket ini, Anda dapat memanfaatkan berbagai alat dan metode yang tersedia untuk melakukan analisis clustering di R.

 
 
arrests_km <- scale(arrests[2:5]) bertujuan untuk melakukan standarisasi atau scaling pada data dari kolom kedua hingga kelima (kolom Murder, Assault, UrbanPop, Rape). Scaling data adalah proses mengubah variabel sehingga memiliki mean 0 dan standar deviasi 1. Ini membantu dalam menjaga skala yang konsisten antar variabel, yang penting saat menggunakan algoritma yang sensitif terhadap skala, seperti K-Means.
Hasil yang ditampilkan adalah data yang sudah diubah (standarisasi) dengan setiap nilai pada kolom diubah relatif terhadap mean dan standar deviasi dari kolom tersebut. Pada hasilnya, Anda melihat angka-angka yang menunjukkan nilai-nilai dari masing-masing observasi (baris) yang telah diubah ke dalam skala yang baru.
Di bagian bawah hasil, terdapat atribut dari skala yang telah dilakukan (attr("scaled:center") dan attr("scaled:scale")). Ini menunjukkan nilai mean dan standar deviasi yang digunakan untuk melakukan transformasi data. Mean dan standar deviasi ini digunakan untuk menghitung nilai-nilai yang ada dalam data dan menyesuaikannya ke skala yang baru.

 
 
kita mencari “siku” di mana jumlah kotak mulai “membungkuk” atau mendatar. Ini biasanya merupakan jumlah cluster yang optimal. Untuk plot ini terlihat ada sedikit siku atau “tikungan” pada k = 4 cluster.
 

Penentuan nilai K pada metode silhouette , dilihat dari garis tertinggi atau melihatnya dengan melihat garis yang paling optimum. Dari gambar diatas , diketahui nilai K yang optimum adalah 2, namun ada opsional lain yaitu menentukan nilai K dengan menggunakan grafik paling tinggi berikutnya setelah grafik paling tinggi pertama yakni grafik tertingi kedua , yaitu di angka 3, berarti nilai K optimum metode silhouette adalah 3 . 
 
Dari plot kita dapat melihat bahwa statistik gap paling tinggi pada k = 4 cluster, yang sesuai dengan metode siku yang kita gunakan sebelumnya

 
set.seed(123): Fungsi ini mengatur benih (seed) yang digunakan untuk menghasilkan bilangan acak. Menggunakan benih yang sama akan menghasilkan hasil yang konsisten dalam pemodelan.
km <- kmeans(arrests_km, 4, nstart = 25): Melakukan k-means clustering pada data arrests_km dengan 4 klaster. Argumen nstart = 25 menunjukkan bahwa algoritma akan diinisialisasi sebanyak 25 kali dengan pusat klaster yang berbeda untuk menghindari hasil yang dipengaruhi oleh inisialisasi awal.
print(km): Menampilkan hasil dari proses k-means clustering.

Hasil menunjukkan bahwa terdapat 4 klaster dengan ukuran masing-masing klaster adalah 8, 13, 16, dan 13.
Terdapat rata-rata dari tiap fitur (variabel) dalam setiap klaster.
Vektor pengelompokan menunjukkan klaster mana yang setiap observasi (baris data) termasuk di dalamnya.
Nilai Within cluster sum of squares menunjukkan seberapa kompak atau seberapa dekat titik-titik dalam satu klaster. Nilai yang lebih rendah menunjukkan klaster yang lebih padat.
Komponen lain yang tersedia seperti centers, totss, withinss, betweenss, size, iter, dan ifault memberikan informasi tambahan terkait hasil dari algoritma k-means clustering tersebut. Misalnya, centers berisi nilai pusat dari tiap klaster, iter menunjukkan iterasi yang diperlukan untuk konvergensi, dan totss, withinss, betweenss adalah jumlah kuadrat yang menggambarkan variabilitas dalam data.
Dari hasilnya kita dapat melihat bahwa:
8 negara bagian ditugaskan ke cluster pertama
13 negara bagian ditugaskan ke cluster kedua
16 negara bagian ditugaskan ke cluster ketiga
13 negara bagian ditugaskan ke cluster keempat

 
aggregate(USArrests, by=list(cluster=km$cluster), mean): Fungsi ini menghasilkan rata-rata dari variabel dalam dataset USArrests berdasarkan klaster yang dihasilkan dari km$cluster.
cluster=km$cluster mengelompokkan data berdasarkan klaster yang dihasilkan sebelumnya.
mean menunjukkan bahwa fungsi aggregate akan menghitung rata-rata setiap variabel dalam masing-masing klaster.
	Jumlah rata-rata pembunuhan per 100.000 warga di negara-negara bagian dalam kelompok 1 adalah 13,9 .
	Jumlah rata-rata penyerangan per 100.000 warga di negara-negara bagian dalam kelompok 1 adalah 243,6 .
	Persentase rata-rata penduduk yang tinggal di daerah perkotaan di antara negara-negara bagian dalam kelompok 1 adalah 53,7% .
	Jumlah rata-rata perkosaan per 100.000 warga di negara-negara bagian dalam kelompok 1 adalah 21,4 .
	Dan seterusnya.
 
cbind(USArrests, cluster = km$cluster): Fungsi cbind menggabungkan kolom klaster yang dihasilkan dari k-means (km$cluster) ke dataset USArrests.
Hasilnya adalah variabel baru dengan nama cluster, yang menunjukkan klaster mana yang ditugaskan untuk setiap baris dalam dataset USArrests. head(dk) menampilkan 6 baris pertama dari dataset baru ini (dk), menunjukkan dataset USArrests dengan tambahan kolom klaster yang menunjukkan klaster yang sesuai untuk setiap barisnya.


 
ggplot(dk, aes(x = Murder, y = Assault, color = factor(cluster))) + geom_point() + labs(title = "Klaster Data USArrests"): Membuat scatter plot dengan Murder di sumbu x, Assault di sumbu y, dan mewarnai titik-titik berdasarkan klaster (cluster). Ini membantu dalam visualisasi hubungan antara Murder dan Assault sambil membedakan klaster berbeda.
fviz_cluster(km, data = arrests_km): Ini digunakan untuk membuat visualisasi dari hasil k-means model (km) menggunakan paket factoextra. Biasanya, ini akan menampilkan centroid dari setiap klaster yang dihasilkan dari k-means. Namun, dalam code yang diberikan, terdapat kebingungan antara objek yang digunakan (km) dan data yang dipakai (arrests_km). Pemanggilan fungsi fviz_cluster biasanya menggunakan model k-means (km) beserta data yang telah di-scaled sebelumnya untuk visualisasi yang tepat.






 . 
 

