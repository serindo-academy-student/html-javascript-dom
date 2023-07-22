# Intro Document Object Model (DOM)

### 1. Mengenal DOM

Document Object Model (DOM) merupakan antarmuka pemrograman untuk dokumen HTML dan XML (juga SVG) terkait. Dengan DOM, kita bisa mengetahui dan mengatur struktur representasi dokumen melalui program terutama JavaScript. Program dapat mengolah struktur, style, dan isi dari dokumen tersebut. Maka dari itu DOM membutuhkan dan menghubungkan antara dokumen dan kode pemrograman.

Seperti yang telah diketahui sebelumnya bahwa hampir semua hal di JavaScript adalah objek, maka begitupun pada HTML yang kita ketahui melalui DOM. Kombinasi interaksi antarmuka antara DOM dan JavaScript ini juga dapat dilakukan karena adanya Application Programming Interface (API). API memungkinkan sebuah program berkomunikasi dengan program yang lain dengan cara tertentu. Dengan API, bahasa selain JavaScript seperti Python dan Ruby jadi bisa juga mengakses dokumen HTML dan XML.

### 2. Seleksi DOM pada HTML

Sebelum mencoba melakukan seleksi dan manipulasi, kita coba asumsikan penggunaan Kita bisa melakukan seleksi terhadap DOM dengan mengunakan beberapa sintaks berikut:

#### - untuk contoh praktek buatlah file berikut

- simple-dom.html
- simple-dom.js

**simple-dom.html**

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Manipulasi DOM Sederhana</title>
  </head>
  <body>
    <button id="changeTextBtn">Klik untuk Ubah Teks</button>
    <div id="displayText"></div>

    <script src="simple-dom.js"></script>
  </body>
</html>
```

**simple-dom.js**

```js
// Ambil referensi elemen tombol dan elemen div dengan ID tertentu
const changeTextBtn = document.getElementById('changeTextBtn');
const displayText = document.getElementById('displayText');

// Tambahkan event listener untuk tombol ketika diklik
changeTextBtn.addEventListener('click', () => {
    // Ubah teks dalam elemen div menjadi "Hello, World!"
    displayText.textContent = "Hello, World!";
});

```


### Penjelasan :


- Kita membuat sebuah tombol dengan ID changeTextBtn dan sebuah elemen div dengan ID displayText.
- Pada file simple-dom.js, kita menggunakan document.getElementById() untuk mendapatkan referensi elemen tombol dan elemen div dari halaman HTML.
- Kemudian, kita menambahkan event listener menggunakan .addEventListener() pada tombol dengan tipe event 'click'. Ketika tombol diklik, fungsi arrow akan dieksekusi.
- Di dalam fungsi arrow tersebut, kita mengubah konten teks dari elemen div dengan menggunakan properti .textContent, sehingga teks dalam elemen div berubah menjadi "Hello, World!" ketika tombol diklik.

Ketika halaman HTML dibuka, Anda akan melihat tombol "Klik untuk Ubah Teks". Setelah Anda mengklik tombol tersebut, teks dalam elemen div di bawahnya akan berubah menjadi "Hello, World!" sesuai dengan manipulasi DOM yang dilakukan menggunakan JavaScript.



## 3 Menjelajah DOM
Kita akan membuat sebuah halaman HTML dan js dengan beberapa elemen div secara berurutan. Setiap elemen div memiliki tombol di dalamnya. Ketika tombol di dalam elemen div diklik, elemen div tersebut akan dihapus dari halaman. Selain itu, ketika tombol di dalam elemen div diklik, teks "Item dihapus" akan ditambahkan di bawah elemen div yang dihapus sebagai pemberitahuan menggunakan manipulasi DOM dengan memanfaatkan konsep parent, child, dan sibling.

buatlah code Berikut dengan code HTML :

**index.html**
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Manipulasi DOM dengan Parent, Child, dan Sibling</title>
    <style>
        .item {
            border: 1px solid #ccc;
            padding: 10px;
            margin-bottom: 10px;
        }
    </style>
</head>
<body>
    <div class="item">
        <button class="delete-btn">Hapus</button>
        Item 1
    </div>
    <div class="item">
        <button class="delete-btn">Hapus</button>
        Item 2
    </div>
    <div class="item">
        <button class="delete-btn">Hapus</button>
        Item 3
    </div>

    <script src="script.js"></script>
</body>
</html>
```

**script.js**
```js
// Ambil referensi tombol-tombol delete
const deleteButtons = document.querySelectorAll('.delete-btn');

// Tambahkan event listener untuk setiap tombol delete
deleteButtons.forEach(button => {
    button.addEventListener('click', () => {
        // Ambil referensi elemen div yang berisi tombol delete yang diklik
        const divItem = button.parentElement;

        // Buat teks "Item dihapus"
        const message = document.createElement('p');
        message.textContent = "Item dihapus";

        // Sisipkan teks "Item dihapus" setelah elemen div yang dihapus
        divItem.insertAdjacentElement('afterend', message);

        // Hapus elemen div dari halaman
        divItem.remove();
    });
});

```

### Penjelasan

- Kita membuat beberapa elemen div dengan kelas .item dan sebuah tombol dengan kelas .delete-btn di dalam setiap elemen div.
- Pada file script.js, kita menggunakan document.querySelectorAll() untuk mendapatkan referensi semua tombol delete pada halaman HTML.
- Kemudian, kita menggunakan .forEach() untuk menambahkan event listener pada setiap tombol delete.
- Di dalam fungsi arrow dari event listener, kita menggunakan button.parentElement untuk mendapatkan referensi elemen div yang berisi tombol delete yang diklik. (Parent dari tombol adalah elemen div).
- Selanjutnya, kita membuat sebuah elemen paragraf (<p>) yang berisi teks "Item dihapus" menggunakan document.createElement().
- Setelah itu, kita menggunakan divItem.insertAdjacentElement('afterend', message) untuk menambahkan elemen paragraf tersebut di bawah elemen div yang dihapus (Sibling setelah elemen div).
- Terakhir, kita menggunakan divItem.remove() untuk menghapus elemen div dari halaman.

Ketika halaman HTML dibuka, Anda akan melihat beberapa elemen div dengan tombol "Hapus". Ketika tombol "Hapus" di dalam elemen div diklik, elemen div tersebut akan dihapus dari halaman, dan teks "Item dihapus" akan ditambahkan di bawah elemen div yang dihapus sebagai pemberitahuan.


### Membuat Website Dinamis Dengan Js


mari kita membuat halaman HTML dengan dua elemen div yang berbeda. Satu elemen div memiliki ID tertentu, misalnya "div1", dan elemen div lainnya memiliki kelas tertentu, misalnya "div-class". Selanjutnya kita dapat membuat dua tombol, masing-masing tombol akan mengubah warna latar belakang dari elemen div yang berbeda menggunakan manipulasi DOM dengan memanfaatkan getElementById dan getElementsByClassName.


contoh html yang kita buat seperti berikut :

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Perbedaan Penggunaan getElementById dan getElementsByClassName</title>
    <style>
        .div-class {
            width: 150px;
            height: 100px;
            background-color: #f0f0f0;
            margin: 10px;
        }

        #div1 {
            width: 150px;
            height: 100px;
            background-color: #f0f0f0;
            margin: 10px;
        }
    </style>
</head>
<body>
    <div id="div1"></div>
    <div class="div-class"></div>
    <br>
    <button id="changeByIdBtn">Ubah Warna (getElementById)</button>
    <button id="changeByClassBtn">Ubah Warna (getElementsByClassName)</button>

    <script src="script.js"></script>
</body>
</html>
```


berikut script js yang akan menerapkan perubahan data :

```js
const div1 = document.getElementById('div1');
const divClass = document.getElementsByClassName('div-class');

const changeByIdBtn = document.getElementById('changeByIdBtn');
const changeByClassBtn = document.getElementById('changeByClassBtn');

changeByIdBtn.addEventListener('click', () => {
    div1.style.backgroundColor = getRandomColor();
});

changeByClassBtn.addEventListener('click', () => {
    for (let i = 0; i < divClass.length; i++) {
        divClass[i].style.backgroundColor = getRandomColor();
    }
});

function getRandomColor() {
    const letters = '0123456789ABCDEF';
    let color = '#';
    for (let i = 0; i < 6; i++) {
        color += letters[Math.floor(Math.random() * 16)];
    }
    return color;
}
```

Penjelasan:

- Pada halaman HTML, kita membuat dua elemen div dengan warna latar belakang awal berwarna abu-abu (#f0f0f0). Salah satunya memiliki ID div1, dan yang lainnya memiliki kelas .div-class.
- Selain itu, kita membuat dua tombol dengan teks "Ubah Warna (getElementById)" dan "Ubah Warna (getElementsByClassName)".
-  file script.js, kita menggunakan document.getElementById('div1') untuk mendapatkan referensi elemen div dengan ID div1 dan document.getElementsByClassName('div-class') untuk mendapatkan referensi semua elemen div dengan kelas .div-class.
- Kita menambahkan event listener pada kedua tombol menggunakan .addEventListener() untuk merespons klik tombol.
- Ketika tombol "Ubah Warna (getElementById)" diklik, kita langsung mengubah warna latar belakang elemen div dengan ID div1 menggunakan div1.style.backgroundColor.
- Namun, ketika tombol "Ubah Warna (getElementsByClassName)" diklik, kita menggunakan loop for untuk mengubah warna latar belakang semua elemen div dengan kelas .div-class menggunakan divClass[i].style.backgroundColor.
- Fungsi getRandomColor() digunakan untuk menghasilkan warna acak dalam format hex (#RRGGBB).

Perbedaan Penggunaan getElementById &  getElementsByClassName :

- getElementById : Digunakan untuk mengambil referensi elemen berdasarkan ID unik yang diberikan. Jika halaman HTML hanya memiliki satu elemen dengan ID tersebut, maka hasilnya adalah referensi langsung ke elemen tersebut. Jika terdapat lebih dari satu elemen dengan ID yang sama (tidak valid dalam HTML), maka hanya elemen pertama yang akan dipilih.
- getElementsByClassName : Digunakan untuk mengambil referensi semua elemen yang memiliki kelas tertentu. Hasilnya berupa koleksi HTML (HTMLCollection), dan Anda harus menggunakan loop atau indeks untuk mengakses elemen individual dari koleksi tersebut.

Pada contoh di atas, kita menggunakan getElementById untuk elemen div dengan ID div1 karena hanya ada satu elemen dengan ID tersebut. Sedangkan, kita menggunakan getElementsByClassName untuk elemen div dengan kelas .div-class karena ada lebih dari satu elemen dengan kelas tersebut.

Dengan demikian, ketika tombol "Ubah Warna (getElementById)" diklik, hanya elemen div dengan ID div1 yang akan berubah warna latar belakangnya. Sementara itu, ketika tombol "Ubah Warna (getElementsByClassName)" diklik, semua elemen div dengan kelas .div-class akan berubah warna latar belakangnya.




