
Berikut adalah alternatif lain menggunakan CSS untuk mengelola gaya cetak dan JavaScript untuk mengelola proses pencetakan:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Cetak Data Tabel dengan JavaScript</title>

  <style id="print-style">
    @media print {
      body * {
        visibility: hidden;
      }

      #data-table, #data-table * {
        visibility: visible !important;
      }
    }
  </style>
</head>
<body>

  <h2>Data Tabel</h2>

  <table border="1" id="data-table">
    <tr>
      <th>Nama</th>
      <th>Usia</th>
      <th>Kota</th>
    </tr>
    <tr>
      <td>John Doe</td>
      <td>25</td>
      <td>Jakarta</td>
    </tr>
    <tr>
      <td>Jane Smith</td>
      <td>30</td>
      <td>Surabaya</td>
    </tr>
  </table>

  <button onclick="cetakData()">Cetak Tabel</button>

  <script>
    function cetakData() {
      // Menambahkan gaya cetak ke head
      var printStyle = document.getElementById("print-style").innerHTML;
      var head = document.head || document.getElementsByTagName('head')[0];
      var style = document.createElement('style');
      style.type = 'text/css';
      style.media = 'print';
      style.appendChild(document.createTextNode(printStyle));
      head.appendChild(style);

      // Melakukan pencetakan
      window.print();

      // Menghapus gaya cetak setelah pencetakan selesai
      head.removeChild(style);
    }
  </script>

</body>
</html>
```

Dalam contoh ini, gaya cetak ditambahkan dinamis ke elemen `<head>` menggunakan JavaScript. Setelah pencetakan selesai, gaya cetak dihapus untuk mengembalikan tampilan halaman seperti semula.