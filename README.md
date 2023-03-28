# Lab4Web

#### Modul Praktikum Pemrograman Web 2

#                         Praktikum 4 : PHP Modular

#### Tujuan
1. Mahasiswa mampu memahami konsep dasar Modularisasi Program.
2. Mahasiswa mampu memahami konsep dasar Fungsi pada PHP.
3. Mahasiswa mampu membuat program Modular sederhana menggunakan PHP.
4. Mahasiswa mampu mengimplementasikan penggunaan fungsi pada PHP

#### Instruksi Praktikum
1. Persiapkan text editor misalnya VSCode.
2. Buat folder baru dengan nama lab4_php_modular pada docroot webserver (htdocs)
3. Ikuti langkah-langkah praktikum yang akan dijelaskan berikutnya.

#### Langkah-langkah Praktikum

#### Buat file baru dengan nama header.php
````
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Contoh Modularisasi</title>
    <link href="style.css" rel="stylesheet" type="text/stylesheet"
media="screen" />
</head>
<body>
    <div class="container">
        <header>
            <h1>Modularisasi Menggunakan Require</h1>
        </header>
        <nav>
            <a href="home.php">Home</a>
            <a href="about.php">Tentang</a>
            <a href="kontak.php">Kontak</a>
        </nav>
````

#### Buat file baru dengan nama footer.php
````
        <footer>
            <p>&copy; 2021, Informatika, Universitas Pelita Bangsa</p>
        </footer>
    </div>
</body>
</html>
````
#### Buat file baru dengan nama home.php
````
<?php require('header.php'); ?>

<div class="content">
    <h2>Ini Halaman Home</h2>
    <p>Ini adalah bagian content dari halaman.</p>
</div>

<?php require('footer.php'); ?>
````
#### Buat file baru dengan nama about.php
````
<?php require('header.php'); ?>

<div class="content">
    <h2>Ini Halaman About</h2>
    <p>Ini adalah bagian content dari halaman.</p>
</div>

<?php require('footer.php'); ?>
````

Membuat Routing
Routing digunakan untuk mempermudah akses halaman web agar SEO Friendly.
Langkah awal adalah menyiapkan file utama (index.php) yang berisi routing untuk mengakses banyak halaman.
Contohnya:
•	Halaman Home ( http://localhost/lab4/index.php?mod=home )
•	Halaman About ( http://localhost/lab4/index.php?mod=about )

#### Buat file baru dengan nama index.php
````
<?php

$mod = $_REQUEST['mod'];

switch ($mod) {
case "home":
        require("home.php");
        break;
case "about":
        require("about.php");
        break;
else:
        require("home.php");
}
?>
````
### Aktivasi mod_rewrite (.htaccess)
Mod_rewrite digunakan untuk mengubah URL dari query string menjadi SEO Friendly.
Langkah awal yang harus disiapkan adalah aktivasi mod_rewrite pada webserver Apache2 pada configurasi httpd.conf.
![image](https://user-images.githubusercontent.com/129153472/228179251-1c213617-eeda-4054-aea1-4b96d15b9c89.png)
Aktifkan LoadModule mod_rewrite dengan cara melakukan un-comment pada baris tersebut, kemudian restart Apache2.
#### Langkah berikutnya adalah membuat file .htaccess
````
<IfModule mod_rewrite.c>
    RewriteEngine On
    RewriteBase /lab4/

    RewriteCond %{REQUEST_FILENAME} !-f
    RewriteCond %{REQUEST_FILENAME} !-d
    RewriteRule ^(.*)$ index.php?mod=$1 [L]
</IfModule>

````
### Cara aksesnya menjadi:
#### • Halaman Home ( http://localhost/lab4/home )
#### • Halaman About ( http://localhost/lab4/about )




















