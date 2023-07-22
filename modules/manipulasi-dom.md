# manipulasi (DOM)

Buatlah sebuah halaman HTML sederhana sebagai berikut :

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Manipulasi dan Menjelajah DOM</title>
  </head>
  <body>
    <label for="inputText">Input teks:</label>
    <input type="text" id="inputText" />
    <button id="addItemBtn">Tambahkan</button>

    <ul id="itemList"></ul>

    <button id="resetBtn">Reset</button>

    <script src="script.js"></script>
  </body>
</html>
```

HTML sederhana tersebut yang berisi sebuah kotak input teks dan sebuah tombol "Tambahkan". Di bawahnya, terdapat sebuah daftar (unordered list) yang awalnya kosong. Setiap kali tombol "Tambahkan" diklik, ambil nilai dari input teks dan tambahkan teks tersebut sebagai elemen baru ke dalam daftar menggunakan manipulasi DOM. Selain itu, tambahkan juga sebuah tombol "Reset" di bawah daftar. Ketika tombol "Reset" diklik, hapus semua item dalam daftar dan kembalikan input teks ke keadaan kosong.

- Pada halaman HTML, kita memiliki sebuah kotak input teks dengan ID inputText, sebuah tombol "Tambahkan" dengan ID addItemBtn, sebuah daftar (unordered list) dengan ID itemList, dan sebuah tombol "Reset" dengan ID resetBtn.
- Pada file script.js yang akan kalian buat, anda akan menggunakan document.getElementById() untuk mendapatkan referensi elemen input teks, tombol "Tambahkan", daftar, dan tombol "Reset" dari halaman HTML.
- Ketika tombol "Tambahkan" diklik, menggunakan inputText.value untuk mengambil nilai dari input teks dan itemList.appendChild(newItem) untuk menambahkan elemen baru (item baru) ke dalam daftar dengan ID itemList. Selain itu, anda dapat membuat fungsi mengosongkan nilai input teks agar pengguna dapat memasukkan teks baru dengan mudah.
- Ketika tombol "Reset" diklik, anda dapat menggunakan while (itemList.firstChild) untuk menghapus semua item dalam daftar. Kita menggunakan itemList.removeChild(itemList.firstChild) untuk menghapus item pertama dalam daftar secara berulang sampai daftar menjadi kosong.
