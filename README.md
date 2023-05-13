ROBIYANTO (312210098)
Teknik Informatika Ti.21.A1

Berikut adalah langkah-langkah untuk membuat OOP lanjutan dengan menggunakan database beserta penjelasan struktur database:

Langkah 1: Rancang Skema Database
- Identifikasi entitas utama yang terlibat dalam sistem Anda, misalnya, Produk, Pelanggan, dan Pesanan.
- Tentukan atribut-atribut yang relevan untuk setiap entitas, misalnya, atribut Produk dapat mencakup ID, Nama, Harga, dan atribut Pelanggan dapat mencakup ID, Nama, Alamat.
- Buat tabel-tabel dalam database Anda dan tetapkan hubungan antara tabel-tabel tersebut menggunakan kunci primer dan kunci asing. Misalnya, setiap Pesanan dapat terkait dengan satu Produk dan satu Pelanggan, dan Anda dapat menggunakan kunci asing untuk menghubungkannya.

Berikut adalah contoh struktur database yang dapat digunakan untuk sistem ini:

Tabel Produk:
```
CREATE TABLE produk (
  id INT PRIMARY KEY,
  nama VARCHAR(255),
  harga DECIMAL(10,2)
);
```

Tabel Pelanggan:
```
CREATE TABLE pelanggan (
  id INT PRIMARY KEY,
  nama VARCHAR(255),
  alamat VARCHAR(255)
);
```

Tabel Pesanan:
```
CREATE TABLE pesanan (
  id INT PRIMARY KEY,
  produk_id INT,
  pelanggan_id INT,
  tanggal DATE,
  jumlah INT,
  FOREIGN KEY (produk_id) REFERENCES produk(id),
  FOREIGN KEY (pelanggan_id) REFERENCES pelanggan(id)
);
```

Langkah 2: Buat Kelas-Kelas dalam OOP
- Buat kelas-kelas yang mewakili entitas-entitas dalam sistem, seperti kelas Produk, Pelanggan, dan Pesanan.
- Atur atribut-atribut yang sesuai untuk setiap kelas, seperti atribut ID, Nama, Harga, dan sebagainya.
- Tentukan metode-metode yang relevan untuk setiap kelas, misalnya, metode untuk menampilkan informasi produk, menambahkan pesanan baru, atau menghapus pesanan.

Berikut adalah contoh implementasi kelas Produk dalam bahasa Python:

```python
class Produk:
    def __init__(self, id, nama, harga):
        self.id = id
        self.nama = nama
        self.harga = harga
    
    def tampilkan_informasi(self):
        print(f"Produk: {self.nama}, Harga: {self.harga}")
    
    # Metode lainnya seperti menyimpan produk ke database, menghapus produk, dan sebagainya
```

Langkah 3: Interaksi dengan Database
- Buat koneksi ke database menggunakan bahasa pemrograman dan library yang sesuai, seperti menggunakan modul `sqlite3` di Python.
- Implementasikan metode-metode dalam kelas-kelas Anda untuk berinteraksi dengan database, seperti mengambil data produk dari database, menyimpan data pesanan baru, atau menghapus pesanan.

Berikut adalah contoh implementasi metode `get_all()` dalam kelas Produk untuk mengambil semua data produk dari database:

```python
import sqlite3

class Produk:
    # ...
    
    @staticmethod
    def get_all():
        conn = sqlite3.connect('nama_database.db')
        cursor = conn.cursor()
        cursor.execute("SELECT * FROM produk")
        rows = cursor.fetchall()
        result = []
        for row in rows:
            produk = Produk(row[0], row[1], row[2])
            result.append(produk)
        return result
```


```bash
Lab6Web
│
├───.htaccess
├───config.php
├───index.php
├───README.md
├───route.php
│
├───class
│    ├───database.php
│    └───form.php
│
├───module
│    ├───home.php
│    └───artikel
│        ├───create.php
│        ├───delete.php
│        ├───error.php
│        └───update.php
│
└───template
     ├───footer.php
     ├───form_insert.php
     ├───form_update.php
     ├───header.php
     └───navbar.php
     
    ------db-------
```
