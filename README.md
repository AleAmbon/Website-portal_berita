Untuk mengaktifkan ekstentsi tersebut, melalu XAMPP Control Panel, pada bagian Apache klik Config -> PHP.ini
Screenshot 2025-03-21 123847

Pada bagian extention, hilangkan tanda ; (titik koma) pada ekstensi yang akan diaktifkan. Kemudian simpan kembali filenya dan restart Apache web server.
Screenshot 2025-03-21 124027

Instalasi Codeigniter 4 Untuk melakukan instalasi Codeigniter 4 dapat dilakukan dengan dua cara, yaitu cara manual dan menggunakan composer.
Screenshot 2025-03-21 124734

Menjalankan CLI (Command Line Interface) Codeigniter 4 menyediakan CLI untuk mempermudah proses development. Untuk mengakses CLI buka terminal/command prompt.
Screenshot 2025-03-21 124930

Arahkan lokasi direktori sesuai dengan direktori kerja project dibuat (xampp/htdocs/lab11_ci/ci4/)

Perintah yang dapat dijalankan untuk memanggil CLI Codeigniter adalah: PHP SPARK
image

Mengaktifkan Mode Debugging Codeigniter 4 menyediakan fitur debugging untuk memudahkan developer untuk mengetahui pesan error apabila terjadi kesalahan dalam membuat kode program. Secara default fitur ini belum aktif. Ketika terjadi error pada aplikasi akan ditampilkan pesan kesalahan seperti berikut.
image

Semua jenis error akan ditampilkan sama. Untuk memudahkan mengetahui jenis errornya, maka perlu diaktifkan mode debugging dengan mengubah nilai konfigurasi pada environment variable CI_ENVIRINMENT menjadi development.
image

Ubah nama file env menjadi .env kemudian buka file tersebut dan ubah nilai variable CI_ENVIRINMENT menjadi development.

image

Contoh error yang terjadi. Untuk mencoba error tersebut, ubah kode pada file app/Controller/Home.php hilangkan titik koma pada akhir kode.

image

Pada Codeigniter, request yang diterima oleh file index.php akan diarahkan ke Router untuk meudian oleh router tesebut diarahkan ke Controller. Router terletak pada file app/config/Routes.php
image

Membuat Route Baru. Tambahkan kode berikut di dalam Routes.php
$routes->get('/about', 'Page::about'); $routes->get('/contact', 'Page::contact'); $routes->get('/faqs', 'Page::faqs');

image

Untuk mengetahui route yang ditambahkan sudah benar, buka CLI dan jalankan perintah berikut.

image

Selanjutnya coba akses route yang telah dibuat dengan mengakses alamat url http://localhost:8080/about

Screenshot 2025-03-21 131531

Ketika diakses akan mucul tampilan error 404 file not found, itu artinya file/page tersebut tidak ada. Untuk dapat mengakses halaman tersebut, harus dibuat terlebih dahulu Contoller yang sesuai dengan routing yang dibuat yaitu Contoller Page.

Membuat Controller Selanjutnya adalah membuat Controller Page. Buat file baru dengan nama page.php pada direktori Controller kemudian isi kodenya seperti berikut.
image

Selanjutnya refresh Kembali browser, maka akan ditampilkan hasilnya yaotu halaman sudah dapat diakses.

Screenshot 2025-03-21 132900

Auto Routing Secara default fitur autoroute pada Codeiginiter sudah aktif. Untuk mengubah status autoroute dapat mengubah nilai variabelnya. Untuk menonaktifkan ubah nilai true menjadi false.
Method ini belum ada pada routing, sehingga cara mengaksesnya dengan menggunakan alamat: http://localhost:8080/page/tos

image

Membuat View Selanjutnya dalam membuat view untuk tampilan web agar lebih menarik. Buat file baru dengan nama about.php pada direktori view (app/view/about.php) kemudian isi kodenya seperti berikut.
image

Ubah method about pada class Controller Page menjadi seperti berikut:

image
Kemudian lakukan refresh pada halaman tersebut.

image

Membuat Layout Web dengan CSS Pada dasarnya layout web dengan css dapat diimplamentasikan dengan mudah pada codeigniter. Yang perlu diketahui adalah, pada Codeigniter 4 file yang menyimpan asset css dan javascript terletak pada direktori public. Buat file css pada direktori public dengan nama style.css
image

Kemudian buat folder template pada direktori view kemudian buat file header.phph dan footer.php

image

File app/view/template/footer.php

Screenshot 2025-03-21 134623

Kemudian ubah file app/view/about.php seperti berikut.

image

Selanjutnya refresh tampilan pada alamat http://localhost:8080/about

image

Membuat database di my sql dengan nama lab_ci4
image

setelah membuat data base, lalu membuat tablenya dengan nama artikel

image

Konfigurasi koneksi database Selanjutnya membuat konfigurasi untuk menghubungkan dengan database server. Konfigurasi dapat dilakukan dengan du acara, yaitu pada file app/config/database.php atau menggunakan file .env. Pada praktikum ini kita gunakan konfigurasi pada file .env.
image

Membuat Model Selanjutnya adalah membuat Model untuk memproses data Artikel. Buat file baru pada direktori app/Models dengan nama **ArtikelModel.php
image

Membuat Controller Buat Controller baru dengan nama Artikel.php pada direktori app/Controllers.
image

Membuat View Buat direktori baru dengan nama artikel pada direktori app/views, kemudian buat file baru dengan nama index.php.
image

Selanjutnya buka browser kembali, dengan mengakses url http://localhost:8080/artikel

image

Belum ada data yang diampilkan. Kemudian coba tambahkan beberapa data pada database agar dapat ditampilkan datanya.

INSERT INTO artikel (judul, isi, slug) VALUE ('Artikel pertama', 'Lorem Ipsum adalah contoh teks atau dummy dalam industri percetakan dan penataan huruf atau typesetting. Lorem Ipsum telah menjadi standar contoh teks sejak tahun 1500an, saat seorang tukang cetak yang tidak dikenal mengambil sebuah kumpulan teks dan mengacaknya untuk menjadi sebuah buku contoh huruf.', 'artikel-pertama'), ('Artikel kedua', 'Tidak seperti anggapan banyak orang, Lorem Ipsum bukanlah teks-teks yang diacak. Ia berakar dari sebuah naskah sastra latin klasik dari era 45 sebelum masehi, hingga bisa dipastikan usianya telah mencapai lebih dari 2000 tahun.', 'artikel-kedua');

Refresh kembali browser, sehingga akan ditampilkan hasilnya.

image

Membuat Tampilan Detail Artikel Tampilan pada saat judul berita di klik maka akan diarahkan ke halaman yang berbeda. Tambahkan fungsi baru pada Controller Artikel dengan nama view().
image

Membuat View Detail Buat view baru untuk halaman detail dengan nama app/views/artikel/detail.php.
image

Membuat Routing untuk artikel detail Buka Kembali file app/config/Routes.php, kemudian tambahkan routing untuk artikel detail.
image

image

Membuat Menu Admin Menu admin adalah untuk proses CRUD data artikel. Buat method baru pada Controller Artikel dengan nama admin_index().
image

Selanjutnya buat view untuk tampilan admin dengan nama admin_index.php

Screenshot 2025-03-23 135513

Screenshot 2025-03-23 135534

Screenshot 2025-03-23 135750

Screenshot 2025-03-23 135806

Tambahkan routing untuk menu admin seperti berikut:

image

Akses menu admin dengan url http://localhost:8080/admin/artikel

Screenshot 2025-03-23 140106

Menambah Data Artikel Tambahkan fungsi/method baru pada Controller Artikel dengan nama add().
image

Kemudian buat view untuk form tambah dengan nama form_add.php

Screenshot 2025-03-23 140417

image

Mengubah Data Tambahkan fungsi/method baru pada Controller Artikel dengan nama edit().
image

Kemudian buat view untuk form tambah dengan nama form_edit.php

image

image

Menghapus Data Tambahkan fungsi/method baru pada Controller Artikel dengan nama delete().
image

Membuat Layout Utama Buat folder layout di dalam app/Views/ Buat file main.php di dalam folder layout dengan kode berikut:
image

image

Modifikasi File View Ubah app/Views/home.php agar sesuai dengan layout baru:
image

Membuat Class View Cell Buat folder Cells di dalam app/ Buat file ArtikelTerkini.php di dalam app/Cells/ dengan kode berikut:
image

Membuat View untuk View Cell Buat folder components di dalam app/Views/ Buat file artikel_terkini.php di dalam app/Views/components/ dengan kode berikut:
image

Menambahkan tanggal tujuanya agar mendapatkan data aertikel yang baru di ubah
image

contohnya seperti ini :

image

Apa manfaat utama dari penggunaan View Layout dalam pengembangan aplikasi? jawab :

Struktur yang Terorganisir
Memudahkan pengaturan elemen UI dengan tata letak yang rapi dan terstruktur.
Responsivitas yang Lebih Baik
Memastikan tampilan UI menyesuaikan dengan berbagai ukuran layar dan orientasi perangkat.
Pemeliharaan Kode yang Lebih Mudah
Dengan pemisahan tata letak dan logika bisnis, perubahan UI lebih mudah dilakukan tanpa mengganggu fungsionalitas aplikasi.
Penggunaan Ulang Komponen
Layout dapat digunakan kembali di berbagai bagian aplikasi, mengurangi redundansi kode.
Kinerja yang Lebih Optimal
Beberapa jenis layout dioptimalkan untuk performa yang lebih baik, seperti ConstraintLayout di Android yang mengurangi jumlah view hierarchy.
Jelaskan perbedaan antara View Cell dan View biasa. jawab : image

Membuat tabel database dengan nama Tabel Login
image

Selanjutnya membuat Tabel User di dalam database yang bernama Tabel Login
image

Membuat Model User Selanjutnya adalah membuat Model untuk memproses data Login. Buat file baru pada direktori app/Models dengan nama UserModel.php
image

Membuat Controller User Buat Controller baru dengan nama User.php pada direktori app/Controllers. Kemudian tambahkan method index() untuk menampilkan daftar user, dan method login() untuk proses login.
image image

Membuat View Login Buat direktori baru dengan nama user pada direktori app/views, kemudian buat file baru dengan nama login.php.
image
image

image

Membuat Database Seeder Database seeder digunakan untuk membuat data dummy. Untuk keperluan ujicoba modul login, kita perlu memasukkan data user dan password kedaalam database. Untuk itu buat database seeder untuk tabel user. Buka CLI, kemudian tulis perintah berikut:
image

Selanjutnya, buka file UserSeeder.php yang berada di lokasi direktori /app/Database/Seeds/UserSeeder.php kemudian isi dengan kode berikut:

image

Selanjutnya buka kembali CLI dan ketik perintah berikut: image

Uji Coba Login Selanjutnya buka url http://localhost:8080/user/login seperti berikut:
image

Menambahkan Auth Filter Selanjutnya membuat filer untuk halaman admin. Buat file baru dengan nama Auth.php pada direktori app/Filters.
image

Selanjutnya buka file app/Config/Filters.php tambahkan kode berikut:
image

Selanjutnya buka file app/Config/Routes.php dan sesuaikan kodenya.
image

Percobaan Akses Menu Admin Buka url dengan alamat http://localhost:8080/admin/artikel ketika alamat tersebut diakses maka, akan dimuculkan halaman login.
image

Fungsi Logout Tambahkan method logout pada Controller User seperti berikut:
image

Untuk membuat pagination, buka Kembali Controller Artikel, kemudian modifikasi kode pada method admin_index seperti berikut.
image

Kemudian buka file views/artikel/admin_index.php dan tambahkan kode berikut dibawah deklarasi tabel data.
image

Selanjutnya buka kembali menu daftar artikel, tambahkan data lagi untuk melihat hasilnya.
image
Membuat Pencarian Pencarian data digunakan untuk memfilter data. Untuk membuat pencarian data, buka kembali Controller Artikel, pada method admin_index ubah kodenya seperti berikut:
image

Kemudian buka kembali file views/artikel/admin_index.php dan tambahkan form pencarian sebelum deklarasi tabel seperti berikut:
image

Dan pada link pager ubah seperti berikut.

image

Selanjutnya ujicoba dengan membuka kembali halaman admin artikel, masukkan kata kunci tertentu pada form pencarian.
Screenshot 2025-04-22 134919

Upload Gambar pada Artikel Menambahkan fungsi unggah gambar pada tambah artikel. Buka kembali Controller Artikel pada project sebelumnya, sesuaikan kode pada method add seperti berikut:
image

Kemudian pada file views/artikel/form_add.php tambahkan field input file seperti berikut.
image

Dan sesuaikan tag form dengan menambahkan ecrypt type seperti berikut.
image

Ujicoba file upload dengan mengakses menu tambah artikel.
image
