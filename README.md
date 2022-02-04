# CodeIgniter 4 Application Starter

## What is CodeIgniter?

CodeIgniter is a PHP full-stack web framework that is light, fast, flexible and secure.
More information can be found at the [official site](http://codeigniter.com).

This repository holds a composer-installable app starter.
It has been built from the
[development repository](https://github.com/codeigniter4/CodeIgniter4).

More information about the plans for version 4 can be found in [the announcement](http://forum.codeigniter.com/thread-62615.html) on the forums.

The user guide corresponding to this version of the framework can be found
[here](https://codeigniter4.github.io/userguide/).

## Installation & updates

`composer create-project codeigniter4/appstarter` then `composer update` whenever
there is a new release of the framework.

When updating, check the release notes to see if there are any changes you might need to apply
to your `app` folder. The affected files can be copied or merged from
`vendor/codeigniter4/framework/app`.

## Setup

Copy `env` to `.env` and tailor for your app, specifically the baseURL
and any database settings.

## Important Change with index.php

`index.php` is no longer in the root of the project! It has been moved inside the *public* folder,
for better security and separation of components.

This means that you should configure your web server to "point" to your project's *public* folder, and
not to the project root. A better practice would be to configure a virtual host to point there. A poor practice would be to point your web server to the project root and expect to enter *public/...*, as the rest of your logic and the
framework are exposed.

**Please** read the user guide for a better explanation of how CI4 works!

## Repository Management

We use GitHub issues, in our main repository, to track **BUGS** and to track approved **DEVELOPMENT** work packages.
We use our [forum](http://forum.codeigniter.com) to provide SUPPORT and to discuss
FEATURE REQUESTS.

This repository is a "distribution" one, built by our release preparation script.
Problems with it can be raised on our forum, or as issues in the main repository.

## Server Requirements

PHP version 7.3 or higher is required, with the following extensions installed:

- [intl](http://php.net/manual/en/intl.requirements.php)
- [libcurl](http://php.net/manual/en/curl.requirements.php) if you plan to use the HTTP\CURLRequest library

Additionally, make sure that the following extensions are enabled in your PHP:

- json (enabled by default - don't turn it off)
- [mbstring](http://php.net/manual/en/mbstring.installation.php)
- [mysqlnd](http://php.net/manual/en/mysqlnd.install.php)
- xml (enabled by default - don't turn it off)

# Tutorial Codeigniter 4 - Cara Membuat CRUD dengan Codeigniter 4

## Install Codeigniter 4
Untuk langkah awal kita perlu menginstall codeigniter 4 terlebih dahulu, dalam contoh ini kita install codeigniter 4 dalam folder dengan nama pegawai.

karena dalam contoh ini kita gunakan `xampp,` dan secara default untuk web direktori `xampp` berada di `C:/xampp/htdocs,` jadi silahkan masuk kedalam folder tersebut, melalui terminal, lalu berikutnya ketikkan perintah seperti gambar dibawah ini :

`composer create-project codeigniter4/appstarter pegawai`

Sehingga gambarnya seperti dibawah ini :

![image](https://user-images.githubusercontent.com/92959023/152554136-7b109e36-9305-43a9-89ac-818adb021a21.png)

lalu tekan enter, tunggu hingga proses instalasi selesai.. 

## Membuat Migration

Berikutnya kita akan membuat bagian migration, karena nantinya kita akan buat `tabel di database,` karena dalam contoh ini kita akan membuat crud untuk data pegawai, maka nantinya kita akan buat tabel didatabase dengan nama pegawai juga, untuk mempermudah pemahaman.

baik langkah – langkah untuk proses pembuatan migration adalah sebagai berikut :

![image](https://user-images.githubusercontent.com/92959023/152555102-7894c0b7-814e-4d69-b5e7-db218b7b6ebc.png)

Silahkan buka terminal dan masuk kedalam direktori : `C:\Xampp\htdocs\pegawai,` lalu tuliskan perintah

`php spark migrate:create Pegawai`

lalu tekan enter

![image](https://user-images.githubusercontent.com/92959023/152555541-fdae61fa-7fa5-48c7-b9e9-a937546a827a.png)

Lalu akan terbuat sebuah file didalam folder `app/Database/Migrations`, nama file tersebut akan diakhiri
dengan nama Pegawai, buka file tersebut, dan isi dengan code seperti berikut ini :

![image](https://user-images.githubusercontent.com/92959023/152558971-714f5f33-4eb4-4a8b-8442-a2a8ddb01c86.png)
![image](https://user-images.githubusercontent.com/92959023/152559087-fdb5efd1-b22b-4b26-9ba2-e9a4b0b5854e.png)

Perintah diatas digunakan untuk membuat sebuah tabel dengan nama `pegawai`, yang berisi kolom antara lain :

`id_pegawai (Integer – Auto Increment – Primary Key)`

`nama (Varchar 255)`

`jenis_kelamin (Enum[‘pria’,’wanita’])`

`no_telp (Varchar 100)`

`email (Varchar 100)`

`alamat (Varchar 255)`

`created_at (Date Time)`

`updated_at (Date Time)`

## Membuat Database

Setelah anda menuliskan perintah didalam migration untuk kebutuhan membuat tabel di database, berikutnya kita akan membuat database, didalam database ini akan kita buat tabel didalamnya dengan menggunakan perintah migration yang baru saja kita buat, langkah – langkahnya adalah sebagai berikut :

Silahkan akses alamat `localhost/phpmyadmin` di browser, tapi sebelum itu jangan lupa untuk mengaktifkan service `apache` dan `MySQL`, lalu berikutnya silahkan klik menu Database untuk membuat database baru.

![image](https://user-images.githubusercontent.com/92959023/152560174-a0a53097-127b-43d1-bf46-52a0737e9c7f.png)

Berikutnya dibagian menu database silahkan `masukkan nama database` yang ingin dibuat.., dalam contoh
ini nama database adalah `pegawai`, lalu kita klik tombol Create

![image](https://user-images.githubusercontent.com/92959023/152560484-1908a381-359d-4dd7-a028-9a355759b47a.png)

## Setting Codeigniter 4 agar dapat terkoneksi dengan database


Setelah kita membuat database, dalam contoh ini adalah database `pagawai`, berikutnya kita akan setting
codeigniter agar dapat terkoneksi dengan database, langkah – langkahnya adalah sebagai berikut :

didalam folder dari project codeigniter4 terdapat file dengan nama `env` silahkan `rename` menjadi `.env`
