# Praktikum 14 - Lanjutan Codeigniter - Pemrograman Web
```
Luro Lumbantoruan
311910210
TI.19.B.1
```

## Langkah 1 - Membuat Pagination
Pagination merupakan proses yang digunakan untuk membatasi tampilan yang panjang
dari data yang banyak pada sebuah website. Fungsi pagination adalah memecah
tampilan menjadi beberapa halaman tergantung banyaknya data yang akan ditampilkan
pada setiap halaman.

Untuk membuat pagination, buka Kembali Controller Artikel `(htdocs\lab11_php_ci\ci4\Controllers\Artikel.php)`, kemudian modifikasi kode pada method `admin_index` seperti berikut.
```

public function admin_index()
{
	 $title = 'Daftar Artikel';
	 $model = new ArtikelModel();
	 $data = [
	 'title' => $title,
	 'artikel' => $model->paginate(10), #data dibatasi 10 record perhalaman
	 'pager' => $model->pager,
	 ];
	 return view('artikel/admin_index', $data);
}
```

![1](https://user-images.githubusercontent.com/82386899/124535780-eec39380-de40-11eb-8c4d-c42eff706252.png)

Kemudian buka file `views/artikel/admin_index.php` dan tambahkan kode berikut dibawah deklarasi tabel data.
```
<?= $pager->links(); ?>
```

![2](https://user-images.githubusercontent.com/82386899/124537032-4e22a300-de43-11eb-897a-39de68138fb4.png)

Kemudian buka file `public/admin.css` tambahkan kode berikut untuk mempercantik tampilan `pagination`
```
/* PAGINATION */
.pagination {
    display: inline-block;
    padding-left: 20px;
    margin-top: 1rem;
    margin-bottom: 1rem;
    border-radius: .25rem;
}
  
.pagination > li {
    display: inline;
}
.pagination > li > a,
.pagination > li > span {
    position: relative;
    float: left;
    padding: .5rem .75rem;
    margin-left: -1px;
    line-height: 1.5;
    color: #0275d8;
    text-decoration: none;
    background-color: #fff;
    border: 1px solid #ddd;
}
.pagination > .active > a,
.pagination > .active > a:focus,
.pagination > .active > a:hover,
.pagination > .active > span,
.pagination > .active > span:focus,
.pagination > .active > span:hover {
    z-index: 2;
    color: #fff;
    cursor: default;
    background-color: #0275d8;
    border-color: #0275d8;
}
```
![3](https://user-images.githubusercontent.com/82386899/124537703-9d1d0800-de44-11eb-9263-d0f09d5a3f9c.png)




