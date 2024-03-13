# ALFIAH KHALIMAHTULLOH - 220102027

## Selamat Datang Di CI
CI adalah sebuah framework aplikasi berbasis PHP bersifat open source. Framework ini dipakai untuk mempermudah pembuatan website cepat dan mudah, juga bersifat dinamis. CodeIgniter memberikan beragam fitur yang mempermudah proses pengembangan aplikasi, seperti sistem manajemen database yang kuat, pembuatan URL yang mudah dibaca, sistem templating, dan banyak lagi.
Singkatnya, CodeIgniter adalah kerangka kerja lunak yang mencoba menyediakan alat yang Anda butuhkan tanpa mengganggu.
## Persyaratan Server
- PHP and Required Extensions
- Optional PHP Extensions
- Supported Databases
### PHP dan Extension Yang diperlukan
- intl
- mbstring
- json

### Optional PHP Extensions
1. Ekstensi PHP berikut harus diaktifkan di server Anda:
- mysqlind. MySQL digunakan untuk menyimpan dan mengelola data dalam sebuah basis data, yang nantinya dapat diakses, dimanipulasi, dan diambil informasinya oleh aplikasi-aplikasi yang terhubung. 
- Crul atau Client URL. Sebuah software yang dipakai untuk mentransfer data dengan menggunakan protokol seperti HTTP ( Hypertext Transfer Protocol), HTTPS ( Hypertext Tranfer Protocol Secure), FTP ( File Transfer Protocol), dll.
- Imagick. Ekstensi dari php yang memungkinkan untuk memanipulasi gambar secara dinamis.
- gd. Sebuah library grafis yang menyediakan fungsi-fungsi untuk membuat dan memanipulasi gambar secara dinamis dalam PHP
- Simplexml. sebuah ekstensi PHP yang menyediakan fungsi-fungsi untuk mempermudah pengolahan dokumen berformat XML.
2. Ekstensi PHP berikut diperlukan saat Anda menggunakan server Cache:
- memcache adalah sebuah sistem caching yang cepat dan efisien yang digunakan untuk meningkatkan kinerja aplikasi web dengan menyimpan data yang sering diakses dalam memori.
- memcached adalah sebuah sistem caching berbasis memori yang terdistribusi dan open source
- Redis adalah ebuah sistem penyimpanan data berkinerja tinggi yang bersifat open-source dan berbasis memori.
### Basis Data Yang Didukung
- Mysql melalui mysql driver https://www.mysql.com/products/connector/
- PostrgreSQL melalui postgre driver https://jdbc.postgresql.org/download/
- SQLite 3 adalah sebuah perpustakaan perangkat lunak yang menyediakan basis data relasional (RDBMS) yang ringan, self-contained, dan bekerja tanpa server. Ini adalah sistem basis data yang berbasis berkas, yang berarti basis data disimpan dalam sebuah berkas tunggal yang dapat diakses dan diolah oleh program-program aplikasi. https://www.sqlite.org/
- Microsoft SQL Server https://www.microsoft.com/en-us/sql-server/sql-server-downloads
- Oracle DB https://www.oracle.com/id/database/
## Instalasi
### Melalui Composer
#### Kelebihan
Instalasi sederhana; mudah untuk diperbarui.

#### Kontra
Anda masih perlu memeriksa perubahan file di ruang proyek (root, aplikasi, publik, dapat ditulisi) dan menggabungkannya setelah memperbarui.

#### Struktur
Folder di proyek Anda setelah pengaturan : aplikasi, publik, tes, dapat ditulis vendor/codeigniter4/framework/system

1. Ketikkan perintah ini di terminal pc masing-masing.
```shell
   composer create-project codeigniter4/appstarter project-root
 ```
2. Ketikkan perintah di terminal untuk masuk ke dalam  direktori untuk mengerucut direktori project-root
 ```shell
cd C:\laragon\www\project-root
```
3. Upgrade
```shell
composer update
```
4. Upgrade untuk versi terbaru
```shell
php builds development
```
5. Kembalikan ke Rilis Stabil
Untuk mengembalikan perubahan.
```shell
php builds release
````

### Instalasi Manual
#### Kelebihan
Tinggal Unduh dan jalankan.

#### Kontra
Anda perlu memeriksa perubahan file di ruang proyek (root, aplikasi, publik, pengujian, dapat ditulisi) dan menggabungkannya sendiri.

#### Struktur
Folder di proyek Anda setelah pengaturan : aplikasi, publik, tes, dapat ditulis, sistem

1. Unduh [versi terbaru] (https://github.com/codeigniter4/framework/archive/v4.0.4.zip)
2. Setelah folder selesai di unduh, ekstrak folder dan letakan sesuai yang diinginkan

#### Server Pengembangan Lokal
dengan baris perintah berikut di cmd kita dapat meluncurkan server lokal kita dan sekarang  dapat melihat aplikasi kita di browser default di http://localhost:8080 .
````shell
php spark serve
```

Jika kita perlu menjalankan situs di host selain localhost, Anda harus menambahkan host ke file host terlebih dahulu . Lokasi pasti file berbeda-beda di setiap sistem operasi utama, meskipun semua sistem tipe unix (termasuk macOS) biasanya menyimpan file di /etc/hosts .
Server pengembangan lokal dapat dikustomisasi dengan tiga opsi baris perintah:

1. Anda dapat menggunakan --hostopsi CLI untuk menentukan host berbeda untuk menjalankan aplikasi di:
``` shell
php spark serve --host example.dev
```
2. Secara default, server berjalan pada port 8080 tetapi Anda mungkin menjalankan lebih dari satu situs, atau sudah memiliki aplikasi lain yang menggunakan port tersebut. Anda dapat menggunakan --portopsi CLI untuk menentukan opsi lain:
``` shell
php spark serve --port 8081
```
3. Anda juga dapat menentukan versi PHP tertentu yang akan digunakan, dengan --phpopsi CLI, dengan nilainya disetel ke jalur eksekusi PHP yang ingin Anda gunakan:
``` shell
php spark serve --php /usr/bin/php7.6.5.4
```

## Membuat aplikasi sederhana
### Static Pages
1. Menetapkan aturan perutean
Mari kita siapkan aturan perutean. Buka file rute yang terletak di app/Config/Routes.php .
```shell
<?php

use CodeIgniter\Router\RouteCollection;

/**
 * @var RouteCollection $routes
 */
$routes->get('/', 'Home::index');
```

Tambahkan baris berikut, setelah arahan rute untuk '/'.
```shell
use App\Controllers\Pages;

$routes->get('pages', [Pages::class, 'index']);
$routes->get('(:segment)', [Pages::class, 'view']);
```
2. Buat controller pages
Buat file di app/Controllers/Pages.php dengan kode berikut.
```shell
<?php

namespace App\Controllers;

class Pages extends BaseController
{
    public function index()
    {
        return view('welcome_message');
    }

    public function view($page = 'home')
    {
        // ...
    }
}
```
3. Buat tampilan
kita akan membuat dua "tampilan" (templat halaman) yang bertindak sebagai footer dan header halaman kita.

Buat header di app/Views/templates/header.php dan tambahkan kode berikut:
``` shell
<!doctype html>
<html>
<head>
    <title>CodeIgniter Tutorial</title>
</head>
<body>

    <h1><?= esc($title) ?></h1>
```

Header berisi kode HTML dasar yang ingin Anda tampilkan sebelum memuat tampilan utama, bersama dengan judul. Ini juga akan menampilkan $titlevariabel, yang akan kita definisikan nanti di pengontrol. Sekarang, buat footer di app/Views/templates/footer.php yang menyertakan kode berikut:
```shell
 <em>&copy; 2022</em>
</body>
</html>
```
4. Menambahkan Logika ke Controller
Badan halaman statis akan ditempatkan di direktori app/Views/pages. Di direktori itu, buat dua file bernama home.php dan about.php . Di dalam file tersebut, ketikkan beberapa teks - apa pun yang Anda suka - dan simpan.
Halaman Lengkap::view() Metode
Untuk memuat halaman tersebut, Anda harus memeriksa apakah halaman yang diminta benar-benar ada. Ini akan menjadi isi metode view()pada Pagespengontrol yang dibuat di atas:
```shell
<?php

namespace App\Controllers;

use CodeIgniter\Exceptions\PageNotFoundException; // Add this line

class Pages extends BaseController
{
    // ...

    public function view($page = 'home')
    {
        if (! is_file(APPPATH . 'Views/pages/' . $page . '.php')) {
            // Whoops, we don't have a page for that!
            throw new PageNotFoundException($page);
        }

        $data['title'] = ucfirst($page); // Capitalize the first letter

        return view('templates/header', $data)
            . view('pages/' . $page)
            . view('templates/footer');
    }
}
```
Sekarang, ketika halaman yang diminta memang ada, halaman tersebut dimuat, termasuk header dan footer, dan dikembalikan ke pengguna. Jika pengontrol mengembalikan string, string tersebut akan ditampilkan kepada pengguna.

5. Menjalankan Aplikasi
tidak dapat menjalankan aplikasi menggunakan server bawaan PHP, karena aplikasi tersebut tidak akan memproses aturan .htaccess yang disediakan di public dengan benar , sehingga menghilangkan kebutuhan untuk menentukan “ index.php/ ” sebagai bagian dari URL. CodeIgniter memiliki perintahnya sendiri yang dapat kita gunakan.

Dari baris perintah, di root proyek kita:
```shell
php spark serve
```
akan memulai server web, dapat diakses pada port 8080. Jika Anda mengatur field lokasi di browser Anda ke localhost:8080 , Anda akan melihat halaman selamat datang CodeIgniter.

Sekarang kunjungi localhost:8080/home . Jika berhasil halaman akan muncul dan jika tidak maka akan ada kode 404(not found).

### News Section 
1. Buat Database untuk Digunakan
Disini menyediakan kode SQL untuk database MySQL, klien database yang digunakan (mysql, MySQL Workbench, atau phpMyAdmin).
Buat database ci4tutorial yang dapat digunakan untuk tutorial ini, dan kemudian mengkonfigurasi CodeIgniter untuk menggunakannya.
Menggunakan klien database, sambungkan ke database Anda dan jalankan perintah SQL di bawah ini (MySQL):
```shell
CREATE TABLE news (
    id INT UNSIGNED NOT NULL AUTO_INCREMENT,
    title VARCHAR(128) NOT NULL,
    slug VARCHAR(128) NOT NULL,
    body TEXT NOT NULL,
    PRIMARY KEY (id),
    UNIQUE slug (slug)
);
//Perintah untuk membuat table dalam databse ci4tutorial.
```
2. Menyambungkan ke database
Buka pada file .env(pastikan ada titik di depan nama file), cari dan matikan komentar pada bagian perintah berikut :
```shell
database.default.hostname = localhost
database.default.database = ci4tutorial
database.default.username = root
database.default.password = root
database.default.DBDriver = MySQLi
```
3. Membuat NewsModel
Buka direktori app/Models dan buat file baru bernama NewsModel.php dan tambahkan kode berikut.
```shell
<?php

namespace App\Models;

use CodeIgniter\Model;

class NewsModel extends Model
{
    protected $table = 'news';
}
```
Ini akan membuat kelas database tersedia melalui objek.CodeIgniter\Model$this->db.
4. Tambahkan Metode NewsModel::getNews()
Tambahkan mengikuti kode ke model
```shell
public function getNews($slug = false)
    {
        if ($slug === false) {
            return $this->findAll();
        }

        return $this->where(['slug' => $slug])->first();
    }
```
5. Tampilkan Berita
Sekarang setelah kueri ditulis, model harus dikaitkan dengan tampilan yang akan menampilkan item berita kepada pengguna. Ini bisa dilakukan dalam pengontrol kami yang dibuat sebelumnya, tetapi demi kejelasan, Pengontrol baru didefinisikan.PagesNews
6. Menambahkan Aturan Perutean
Ubah file app/Config/Routes.php, sehingga terlihat sebagai berikut:
```shell
<?php

// ...

use App\Controllers\News; // Add this line
use App\Controllers\Pages;

$routes->get('news', [News::class, 'index']);           // Add this line
$routes->get('news/(:segment)', [News::class, 'show']); // Add this line

$routes->get('pages', [Pages::class, 'index']);
$routes->get('(:segment)', [Pages::class, 'view']);
```
6. Membuat News Controller
Buat pengontrol baru di app/Controllers/News.php.
```shell
<?php

namespace App\Controllers;

use App\Models\NewsModel;

class News extends BaseController
{
    public function index()
    {
        $model = model(NewsModel::class);

        $data['news'] = $model->getNews();
    }

    public function show($slug = null)
    {
        $model = model(NewsModel::class);

        $data['news'] = $model->getNews($slug);
    }
}
```
7. Berita Lengkap::index() Metode
Dta sudah berhasil di ambil namunn belum ada yang ditampilkan, selanjutkan kita akan meneruskan data ini ke views. Ubah metode agar terlihat seperti ini:index()
```shell
<?php

namespace App\Controllers;

use App\Models\NewsModel;

class News extends BaseController
{
    public function index()
    {
        $model = model(NewsModel::class);

        $data = [
            'news'  => $model->getNews(),
            'title' => 'News archive',
        ];

        return view('templates/header', $data)
            . view('news/index')
            . view('templates/footer');
    }

    // ...
}
```
8. Membuat berita/indeks Lihat File
Buat app/Views/news/index.php dan tambahkan potongan kode berikutnya.
```shell
<h2><?= esc($title) ?></h2>

<?php if (! empty($news) && is_array($news)): ?>

    <?php foreach ($news as $news_item): ?>

        <h3><?= esc($news_item['title']) ?></h3>

        <div class="main">
            <?= esc($news_item['body']) ?>
        </div>
        <p><a href="/news/<?= esc($news_item['slug'], 'url') ?>">View article</a></p>

    <?php endforeach ?>

<?php else: ?>

    <h3>No News</h3>

    <p>Unable to find any news for you.</p>

<?php endif ?>
```
9. Berita Lengkap::show() Metode
Tambahkan beberapa kode ke controller dan buat view baru. Kembali ke controller dan perbarui methode dengan yang berikut:News show()
```shell
<?php

namespace App\Controllers;

use App\Models\NewsModel;
use CodeIgniter\Exceptions\PageNotFoundException;

class News extends BaseController
{
    // ...

    public function show($slug = null)
    {
        $model = model(NewsModel::class);

        $data['news'] = $model->getNews($slug);

        if (empty($data['news'])) {
            throw new PageNotFoundException('Cannot find the news item: ' . $slug);
        }

        $data['title'] = $data['news']['title'];

        return view('templates/header', $data)
            . view('news/view')
            . view('templates/footer');
    }
}
```
Jangan lupa tambahkan untuk import the class 
use CodeIgniter\Exceptions\PageNotFoundException;PageNotFoundException

10. Buat berita/lihat Lihat File
membuat tampilan yang sesuai di app/Views/news/view.php. Masukkan kode berikut dalam file ini.
```shell
<h2><?= esc($news['title']) ?></h2>
<p><?= esc($news['body']) ?></p>
```
Arahkan browser Anda ke halaman "berita" Anda, yaitu, localhost:8080/news.
Kita akan melihat daftar item berita, yang masing-masing memiliki tautan untuk menampilkan hanya satu artikel.


## CodeIgniter4 Overview
### Models, Views, and Controllers
1. Apa itu MVC?
MVC atau Model View Controller adalah sebuah pola desain arsitektur dalam sistem pengembangan website yang terdiri dari tiga bagian :
  a. Model, bagian yang mengelola dan berhubungan langsung dengan database;
  b. View, bagian yang akan menyajikan tampilan informasi kepada pengguna;
  c. Controller, bagian yang menghubungkan model dan view dalam setiap proses request       dari user.
Dengan konsep MVC ini, website seakan memiliki bagian yang terpisah dan bisa dikembangkan masing-masing. Maka, proses pembuatan website bisa dilakukan lebih cepat karena developer akan lebih fokus pada pengerjaan salah satu bagian saja. 
2. komponen
  a. View, Biasanya disimpan dalam app/views.
  b. Model, Model biasanya disimpan dalam app/Models.
  c. Controller, Controller biasanya disimpan dalam app/Controllers.

## General Topics
### Helper Functions
1. Apa itu 


