
# HTML Dinamis (DOM)


Buatlah sebuah halaman HTML yang berisi sebuah form untuk menambahkan tugas baru, sebuah tombol "Tambah Tugas", dan sebuah daftar (unordered list) untuk menampilkan daftar tugas. Setiap kali tombol "Tambah Tugas" diklik, ambil nilai dari input tugas dan tambahkan tugas tersebut sebagai elemen baru ke dalam daftar menggunakan manipulasi DOM dengan JavaScript. Selain itu, setiap tugas pada daftar akan memiliki tombol "Selesai" dan tombol "Hapus". Ketika tombol "Selesai" pada suatu tugas diklik, tandai tugas tersebut sebagai selesai dengan mengubah warna teksnya menjadi abu-abu. Ketika tombol "Hapus" pada suatu tugas diklik, hapus tugas tersebut dari daftar.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tugas Anchor DOM - Daftar Tugas</title>
</head>
<body>
    <h1>Tugas Anchor DOM - Daftar Tugas</h1>
    <form id="taskForm">
        <label for="taskInput">Tambahkan Tugas:</label>
        <input type="text" id="taskInput">
        <button type="submit">Tambah Tugas</button>
    </form>

    <ul id="taskList">
        <li><span class="task-item">Tugas 1</span> <button class="complete-btn">Selesai</button> <button class="delete-btn">Hapus</button></li>
        <li><span class="task-item">Tugas 2</span> <button class="complete-btn">Selesai</button> <button class="delete-btn">Hapus</button></li>
        <li><span class="task-item">Tugas 3</span> <button class="complete-btn">Selesai</button> <button class="delete-btn">Hapus</button></li>
    </ul>

    <script src="script.js"></script>
</body>
</html>

```



- Pada halaman HTML, kita memiliki sebuah form dengan ID taskForm untuk menambahkan tugas baru, sebuah input teks dengan ID taskInput, dan sebuah tombol "Tambah Tugas" dengan tipe submit. Selain itu, kita juga memiliki sebuah daftar (unordered list) dengan ID taskList yang sudah berisi beberapa tugas dan tombol "Selesai" dan "Hapus" di setiap tugasnya.
- Pada file script.js, kita menggunakan document.getElementById() untuk mendapatkan referensi form, input teks, dan daftar dari halaman HTML
- Selanjutnya, kita menambahkan event listener pada form menggunakan .addEventListener('submit', ...). Ketika form disubmit (tombol "Tambah Tugas" diklik atau Enter ditekan), fungsi arrow akan dieksekusi.
- Di dalam fungsi arrow tersebut, kita menggunakan event.preventDefault() untuk mencegah halaman refreshing saat form disubmit.
- Selanjutnya, kita menggunakan taskInput.value untuk mengambil nilai dari input tugas yang dimasukkan oleh pengguna dan document.createElement('li') untuk membuat elemen daftar baru (<li>).
- Kemudian, kita mengatur innerHTML elemen daftar baru dengan menambahkan tugas yang dimasukkan oleh pengguna dan tombol "Selesai" serta tombol "Hapus".
- Setelah elemen daftar baru siap, kita tambahkan elemen tersebut ke dalam daftar dengan ID taskList menggunakan taskList.appendChild(newTaskItem). Selain itu, kita juga mengosongkan nilai input tugas agar pengguna dapat memasukkan tugas baru dengan mudah.
- Selanjutnya, kita menambahkan event listener pada daftar (taskList) menggunakan .addEventListener('click', ...). Ketika ada tombol di dalam daftar yang diklik, fungsi arrow akan dieksekusi.
- Dalam fungsi arrow tersebut, kita menggunakan event.target untuk mendapatkan elemen yang memicu event klik (tombol yang diklik).
- tombol "Selesai" diklik (clickedElement.classList.contains('complete-btn')), maka kita mencari elemen <span> yang berisi teks tugas dengan clickedElement.previousElementSibling. Selanjutnya, kita mengubah warna teksnya menjadi abu-abu dengan taskItem.style.color = "gray".
- Jika tombol "Hapus" diklik (clickedElement.classList.contains('delete-btn')), maka kita mencari elemen <li> yang berisi tugas beserta tombol-tombolnya dengan clickedElement.parentNode. Selanjutnya, kita menghapus elemen <li> tersebut dari daftar dengan taskList.removeChild(taskItem).


Ketika halaman HTML dibuka, Anda akan melihat form untuk menambahkan tugas, sebuah tombol "Tambah Tugas", dan sebuah daftar tugas dengan tombol "Selesai" dan "Hapus" di setiap tugasnya. Setiap kali tombol "Tambah Tugas" diklik dan tugas dimasukkan, tugas tersebut akan ditambahkan sebagai elemen baru ke dalam daftar. Selain itu, ketika tombol "Selesai" pada suatu tugas diklik, tugas tersebut akan ditandai sebagai selesai dengan warna teks abu-abu. Dan jika tombol "Hapus" pada suatu tugas diklik, tugas tersebut akan dihapus dari daftar.







