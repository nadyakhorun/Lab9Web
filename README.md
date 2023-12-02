# PHP Modular

Nama              : Nadya Khairunnisa

NIM               : 312210133

Kelas             : TI.22.A.1

Mata Kuliah       : Pemrograman Web 1

Dosen Pengampu    : Agung Nugroho, S.Kom., M.Kom.

# Instruksi Praktikum

1. Persiapkan text editor misalnya VSCode.

2. Buat folder baru dengan nama lab9_php_modular pada docroot webserver (htdocs)
   
3. Ikuti langkah-langkah praktikum yang akan dijelaskan berikutnya.

# Langkah-Langkah Praktikum

1. Buat file baru dengan nama header.php

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

2. Buat File baru dengan nama footer.php

               <footer>
                  <p>&copy; 2021, Informatika, Universitas Pelita Bangsa</p>
               </footer>
            </div>
         </body>
         </html>

3. Buat file baru dengan nama home.php

         <?php require('header.php'); ?>
         <div class="content">
            <h2>Ini Halaman Home</h2>
            <p>Ini adalah bagian content dari halaman.</p>
         </div>
         <?php require('footer.php'); ?>

4. Buat file baru dengan nama about.php

         <?php require('header.php'); ?>
         <div class="content">
            <h2>Ini Halaman About</h2>
            <p>Ini adalah bagian content dari halaman.</p>
         </div>
         <?php require('footer.php'); ?>

![lab9 header](https://github.com/nadyakhorun/Lab9Web/assets/115801823/2bae2f2d-818f-4f87-ab42-d3510e703758)

# Pertanyaan dan Tugas

Implementasikan konsep modularisasi pada kode program praktikum 8 tentang database, sehingga setiap halamannya memiliki template tampilan yang sama.

# Sekian dan Terima Kasih
