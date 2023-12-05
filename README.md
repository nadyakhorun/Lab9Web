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

a. header.php

            <!DOCTYPE html>
            <html lang="en">
            <head>
            <meta charset="UTF-8">
            <title>Contoh Modularisasi</title>
            <link href="style.css" rel="stylesheet" type="text/stylesheet"
            media="screen" />
            <style>
            body {
                        font-family: Arial, sans-serif;
                        background-color: #f4f4f4;
                        margin: 0;
                        padding: 0;
                    }
            
                    .container {
              border-radius: 5px;
              background-color: #f2f2f2;
              padding: 5px;
            }
            h1 {
              text-align: center;
            }
            
            header {
                background-color: #d3d3d3;
                padding: 20px;
                text-align: center;
              }
            
            ul {
              list-style-type: none;
              margin: 0;
              padding: 0;
              overflow: hidden;
              background-color: #333;
            }
            
            li {
              float: left;
            }
            
            li a {
              display: block;
              color: white;
              text-align: center;
              padding: 14px 16px;
              text-decoration: none;
            }
            
            li a:hover {
              background-color: #111;
            }
            footer {
              background-color: #333;
              padding: 5px;
              color: #eee;
              text-align: center;
            }
            </style>
            </head>
            <body>
            <div class="container">
            <header>
            <h1>Modularisasi Menggunakan Require</h1>
            </header>
            <nav>
                <ul>
            <li><a href="home.php">Home</a></li>
            <li><a href="about.php">Tentang</a></li>
            <li><a href="kontak.php">Kontak</a></li>
            <li><a href="tambah.php">Tambah Data</a></li>
            <li><a href="index.php">Lihat Data</a></li>
            <li><a href="ubah.php">Ubah Data</a></li>
            </ul>
            </nav>

b. tambah.php

            <?php require('header.php'); ?>
            <?php
            error_reporting(E_ALL);
            include_once 'koneksi.php';
            
            if (isset($_POST['submit']))
            {
                $nama = $_POST['nama'];
                $kategori = $_POST['kategori'];
                $harga_jual = $_POST['harga_jual'];
                $harga_beli = $_POST['harga_beli'];
                $stok = $_POST['stok'];
                $file_gambar = $_FILES['file_gambar'];
                $gambar = null;
                if ($file_gambar['error'] == 0)
                {
                    $filename = str_replace(' ', '_',$file_gambar['name']);
                    $destination = dirname(_FILE_) .'/gambar/' . $filename;
                    if(move_uploaded_file($file_gambar['tmp_name'], $destination))
                    {
                        $gambar = 'gambar/' . $filename;;
                    }
                }
                $sql = 'INSERT INTO data_barang (nama, kategori,harga_jual, harga_beli,
            stok, gambar) ';
                $sql .= "VALUE ('{$nama}', '{$kategori}','{$harga_jual}',
            '{$harga_beli}', '{$stok}', '{$gambar}')";
                $result = mysqli_query($conn, $sql);
                header('location: index.php');
            }
            ?>
            <!DOCTYPE html>
            <html lang="en">
            <head>
                <meta charset="UTF-8">
                <link href="style.css" rel="stylesheet" type="text/css" />
                <title>Tambah Barang</title>
            <style>
             body {
                        font-family: Arial, sans-serif;
                        background-color: #d3d3d3;
                        margin: 0;
                        padding: 0;
                    }
            
                    h1 {
              text-align: center;
            }
            
            input[type=text], select, textarea {
              width: 99%;
              padding: 8px;
              border: 1px solid #ccc;
              box-sizing: border-box;
            }
            
            label {
              padding: 12px 12px 12px 0;
              display: inline-block;
            }
            
            input[type=submit] {
              background-color: #0000FF;
              color: white;
              padding: 12px 20px;
              border: none;
              border-radius: 4px;
              cursor: pointer;
            }
            
            input[type=submit]:hover {
              background-color: #4169E1;
            }
            
            .container {
              border-radius: 5px;
              background-color: #f2f2f2;
              padding: 5px;
            }
            </style>
            </head>
            <body>
            <div class="container">
                <h1>Tambah Barang</h1>
                <div class="main">
                    <form method="post" action="tambah.php"
            enctype="multipart/form-data">
                        <div class="input">
                            <label>Nama Barang</label>
                            <input type="text" name="nama" />
                        </div>
                        <div class="input">
                            <label>Kategori</label>
                            <select name="kategori">
                                <option value="Komputer">Komputer</option>
                                <option value="Elektronik">Elektronik</option>
                                <option value="Hand Phone">Hand Phone</option>
                            </select>
                        </div>
                        <div class="input">
                            <label>Harga Jual</label>
                            <input type="text" name="harga_jual" />
                        </div>
                        <div class="input">
                            <label>Harga Beli</label>
                            <input type="text" name="harga_beli" />
                        </div>
                        <div class="input">
                            <label>Stok</label>
                            <input type="text" name="stok" />
                        </div>
                        <div class="input">
                            <label>File Gambar</label>
                            <input type="file" name="file_gambar" />
                        </div>
                        <div class="submit">
                            <input type="submit" name="submit" value="Simpan" />
                        </div>
                    </form>
                </div>
            </div>
            </body>
            </html>
            
            <?php require('footer.php'); ?>

c. ubah.php

         <?php require('header.php'); ?>
         <?php
         error_reporting(E_ALL);
         include_once 'koneksi.php';
         
         if (isset($_POST['submit']))
         {
             $id = $_POST['id'];
             $nama = $_POST['nama'];
             $kategori = $_POST['kategori'];
             $harga_jual = $_POST['harga_jual'];
             $harga_beli = $_POST['harga_beli'];
             $stok = $_POST['stok'];
             $file_gambar = $_FILES['file_gambar'];
             $gambar = null;
         
             if ($file_gambar['error'] == 0)
             {
                 $filename = str_replace(' ', '_', $file_gambar['name']);
                 $destination = dirname(_FILE_) . '/gambar/' . $filename;
                 if (move_uploaded_file($file_gambar['tmp_name'], $destination))
                 {
                     $gambar = 'gambar/' . $filename;;
                 }
             }
         
             $sql = 'UPDATE data_barang SET ';
             $sql .= "nama = '{$nama}', kategori = '{$kategori}', ";
             $sql .= "harga_jual = '{$harga_jual}', harga_beli = '{$harga_beli}', stok
         = '{$stok}' ";
             if (!empty($gambar))
                 $sql .= ", gambar = '{$gambar}' ";
             $sql .= "WHERE id_barang = '{$id}'";
             $result = mysqli_query($conn, $sql);
         if (!$result) {
             die('Error: ' . mysqli_error($conn));
         } else {
             header('location: index.php');
         }
         }
         $id = $_GET['id'];
         $sql = "SELECT * FROM data_barang WHERE id_barang = '{$id}'";
         $result = mysqli_query($conn, $sql);
         if (!$result) die('Error: Data tidak tersedia');
         $data = mysqli_fetch_array($result);
         function is_select($var, $val) {
             if ($var == $val) return 'selected="selected"';
             return false;
         }
         
         ?>
         <!DOCTYPE html>
         <html lang="en">
         <head>
             <meta charset="UTF-8">
             <link href="style.css" rel="stylesheet" type="text/css" />
             <title>Ubah Barang</title>
         <style>
         body {
                     font-family: Arial, sans-serif;
                     background-color: #f4f4f4;
                     margin: 0;
                     padding: 0;
                 }
         
         input[type=text], select, textarea {
           width: 100%;
           padding: 8px;
           border: 1px solid #ccc;
           box-sizing: border-box;
         }
         
         h1 {
           text-align: center;
         }
         label {
           padding: 12px 12px 12px 0;
           display: inline-block;
         }
         
         input[type=submit] {
           background-color: #0000FF;
           color: white;
           padding: 12px 20px;
           border: none;
           border-radius: 4px;
           cursor: pointer;
         }
         
         input[type=submit]:hover {
           background-color: #4169E1;
         }
         
         .container {
           border-radius: 5px;
           background-color: #f2f2f2;
           padding: 5px;
         }
         </style>
         </head>
         <body>
         <div class="container">
             <h1>Ubah Barang</h1>
             <div class="main">
                 <form method="post" action="ubah.php"
         enctype="multipart/form-data">
                     <div class="input">
                         <label>Nama Barang</label>
                         <input type="text" name="nama" value="<?php echo
         $data['nama'];?>" />
                     </div>
                     <div class="input">
                         <label>Kategori</label>
                         <select name="kategori">
                             <option <?php echo is_select
         ('Komputer', $data['kategori']);?> value="Komputer">Komputer</option>
                             <option <?php echo is_select
         ('Komputer', $data['kategori']);?> value="Elektronik">Elektronik</option>
                             <option <?php echo is_select
         ('Komputer', $data['kategori']);?> value="Hand Phone">Hand Phone</option>
                         </select>
                     </div>
                     <div class="input">
                         <label>Harga Jual</label>
                         <input type="text" name="harga_jual" value="<?php echo
         $data['harga_jual'];?>" />
                     </div>
                     <div class="input">
                         <label>Harga Beli</label>
                         <input type="text" name="harga_beli" value="<?php echo
         $data['harga_beli'];?>" />
                     </div>
                     <div class="input">
                         <label>Stok</label>
                         <input type="text" name="stok" value="<?php echo
         $data['stok'];?>" />
                     </div>
                     <div class="input">
                         <label>File Gambar</label>
                         <input type="file" name="file_gambar" />
                     </div>
                     <div class="submit">
                         <input type="hidden" name="id" value="<?php echo
         $data['id_barang'];?>" />
                         <input type="submit" name="submit" value="Simpan" />
                     </div>
                 </form>
             </div>
         </div>
         </body>
         </html>
         
         <?php require('footer.php'); ?>

# Sekian dan Terima Kasih
