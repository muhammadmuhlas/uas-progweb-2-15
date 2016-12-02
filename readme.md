# Jawaban UAS II - Pemrograman Web - 2015/2016

## 1. Pengaruh Sifat `HTTP Protocol` yang `Stateless`
* Pengaruh nya adalah setiap `request` yang dikirimkan harus memuat semua detail untuk mendapatkan `response` yang diinginkan, karena `Stateless HTTP` tidak menganggap `request` yang sebelumnya.
* Selain itu pengaruh yang lain adalah, keamanan dari `request` itu sendiri, karena dapat dipastikan setiap `request` yang dikirim benar benar dari pihak `Client-side` bukan dari `Bot`, `malware`, atau semacamnya.
* Dengan sifat `HTTP` yang `Stateless`, memungkinkan kemudahan bagi `developer` di `Server-side` untuk menganalisa setiap `request` dari `Client-side`.

## 2. Kelebihan Validasi dan Verifikasi `HTML` pada `Client-side`
* Kelebihan yang pertama adalah dapat memberitahu kepada `User` yang sedang melakukan `Input Data`, bahwa terdapat kode `HTML` di `text` yang dia tulis.
* Kemudian, untuk mengurangi beban dari `Server-side` (yang biasanya) mem-verifikasi ulang `request input data` dari `Client-side`.
* Kemudian, juga dapat membuat pengecekan tertentu misal, tidak diperbolehkan menggunakan kata kata tertentu, atau hanya dibolehkan maksimal `30 character` atau sebagainya.

### 2.1 Contoh `function` untuk `handling HTML` menggunakan `Javascript`:
```javascript
// untuk mengganti symbol HTML menjadi entity mereka
function replaceHTMLsymbol(string) {

	return String(string).replace(/&/g, '&amp;').replace(/</g, '&lt;').replace(/>/g, '&gt;').replace(/"/g, '&quot;');
}

// untuk menghapus tag HTML
function removeHTMLsymbol(string) {

	return strip(string);
}
```

## 3. Kelebihan Validasi dan Verifikasi `HTML` pada `Server-side`
* Kelebihan yang utama atau bisa juga disebut kepentingan dari validasi `HTML` di `Server-side` adalah ketika memasukkan Data yang di `input` dari `Client-side` menuju ke `variable`, ketika input nya mengandung `"`, `<`, `>`, `&`, akan membuat `error` di `Server-side`, oleh karena itu, hal ini dapat diatasi dengan `code` ini, dan tentu saja penyimpanan tidak dilakukan, dan menampilkan `status` tersebut ke `Client-side`.
* Kemudian, juga dapat membuat pengecekan tertentu misal, tidak diperbolehkan menggunakan kata kata tertentu, atau hanya dibolehkan maksimal `30 character` atau sebagainya.

### 3.1 Contoh `function` untuk `handling HTML` menggunakan `PHP`:
```php
<?php

// untuk mengganti symbol HTML menjadi entity mereka
function replaceHTMLsymbol($string = 'null'){

	return htmlentities($string);
}

// untuk menghapus tag HTML
function removeHTMLsymbol($string = 'null'){

	return strip_tags($string);
}
?>
```

## 4. Perbedaan `Web Service` dan `Web API`, Hambatan Masing Masing dalam Pengembangan Sebuah `Web`
### 4.1 `Web Service`
`Web Service` merupakan sebuah jalan untuk mendapatkan data tertentu sesuai dengan `request`, Contoh dari `Web Service` adalah `Zend Framework`, yang digunakan oleh `PHP`. `Web Service` mempunyai ketentuan untuk setiap `request` yang dikirimkan, yaitu :

* diakses melalui alamat `URL`; misal `https://localhost/web-service`.
* `Service Provider` mengirimkan sebuah list berupa `WSDL` menuju `UDDI`.
* Kemudian, untuk setiap `request` yang dikirimkan dari `Service Requester` dilakukan pengecekan terlebih dahulu oleh `UDDI` untuk diarahkan ke `Service Provider` mana data tersebut akan dikirimkan.
* `Service Requester` mendapatkan `Service Provider` yang dituju dan mengirimkannya menggunakan `SOAP Protocol`.
* Setelah itu, `Service Provider` menerima data tersebut, melakukan proses tertentu, dan mengirim data `response` ke `Service Requester` menggunakan `SOAP Protocol` dalam bentuk `XML`.

### 4.1.1 Hambatan menggunakan `Web Service` dalam pengembangan `Web`
* Harus berada di jaringan yang sama dengan `Web Service`.
* Harus mengetahui dokumentasi dari `Web Service` tersebut.
* Lebih cocok jika diakses untuk `pengguna` yang tidak banyak, sehingga lebih mungkin terjadi `overload` `request`.

### 4.2 `Web API`
`Web API` biasanya berupa sebuah alamat URL yang dapat menghubungkan ke `Database`, dan atau melakukan proses tertentu. `Web API` hampir sama seperti `Web Service`, Setiap `Web Service` dapat dikembangkan menjadi `Web API`, tapi setiap `Web API` belum tentu berasal dari `Web Service`, tergantung dari bahasa pemrograman yang digunakan. Berikut ini adalah cara untuk mengkases `Web API`:

* diakses melalui alamat `URL`; misal `https://api.github.com`.
* untuk setiap `request`, dan `response` terdapat `Header` yang berisi `Authentication`, `User-Agent`, dan lain sebagainya sebagai identifikasi untuk setiap `request` atau `response`.
* untuk setiap `request`, di validasi oleh `Web API` dari identitas `requester`, dan alamat yang diakses.
* setiap `request`, dan `response` lebih sering menggunakan `JSON`, karena lebih efisien dibandingkan `XML`, namun bisa juga jika dikirim menggunakan `XML`, tergantung dari konfigurasi `response` `Web API` yang dituju.

### 4.2.1 Hambatan menggunakan `Web API` dalam pengembangan `Web`
* Harus berada di jaringan yang sama dengan `Web API`.
* Harus mengetahui dokumentasi dari `Web API` tersebut.
