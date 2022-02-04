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

`<?php`
 
`namespace App\Database\Migrations;`
 
`use CodeIgniter\Database\Migration;`
 
`class Pegawai extends Migration`
`{`
	`public function up()`
	`{`
		`$this->forge->addField([`
			'id_pegawai'          => [
				'type'           => 'INT',
				'constraint'     => 11,
				'unsigned'       => true,
				'auto_increment' => true,
			],
			'nama'       => [
				'type'           => 'VARCHAR',
				'constraint'     => '255',
			],
			'jenis_kelamin'       => [
				'type'              => 'ENUM',
				'constraint'        => "'pria','wanita'",
			],
			'no_telp' => [
				'type'           => 'VARCHAR',
				'constraint'     => '100',
			],
			'email' => [
				'type'           => 'VARCHAR',
				'constraint'     => '100',
			],
			'alamat' => [
				'type'           => 'VARCHAR',
				'constraint'     => '255',
			],
			'created_at' => [
				'type'           => 'DATETIME',
				'null'           => true,
			],
			'updated_at' => [
				'type'           => 'DATETIME',
				'null'           => true,
			]
		]);
		$this->forge->addPrimaryKey('id_pegawai');
		$this->forge->createTable('pegawai');
	}
 
	//--------------------------------------------------------------------
 
	public function down()
	{
		$this->forge->dropTable('pegawai');
	}
}
