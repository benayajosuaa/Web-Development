# Syntax SQL 📝

> berikut ini adalah kumpulan syntax SQL yang dibuat dalam postgreSQL
> 

### a. **CREATE**

Digunakan untuk membuat **database** atau **tabel baru**.

```sql
-- Membuat database baru
CREATE DATABASE nama_database;

```

```sql
-- Membuat tabel baru
CREATE TABLE nama_tabel (
    id SERIAL PRIMARY KEY,
    nama VARCHAR(100) NOT NULL,
    umur INTEGER
);
```


### b. **INSERT**

Digunakan untuk **menambahkan data ke dalam tabel**.

```sql
INSERT INTO nama_tabel (nama, umur)
VALUES ('Benaya', 20);
```


### c. **SELECT**

Digunakan untuk **mengambil data dari tabel**.

```sql
-- Ambil semua data
SELECT * FROM nama_tabel;

-- Ambil kolom tertentu
SELECT nama, umur FROM nama_tabel;

-- Ambil data dengan syarat tertentu
SELECT * FROM nama_tabel WHERE umur > 18;
```


### d. **UPDATE**

Untuk **mengubah data** di dalam tabel.

```sql
UPDATE nama_tabel
SET umur = 21
WHERE nama = 'Benaya';
```


### e. **DELETE**

Untuk **menghapus data** dari tabel.

```sql
DELETE FROM nama_tabel WHERE nama = 'Benaya';
```


### f. **DROP**

Untuk **menghapus** tabel atau database.

```sql
DROP TABLE nama_tabel;
DROP DATABASE nama_database;
```


### g. **WHERE, ORDER BY, GROUP BY, HAVING, LIMIT**

Digunakan untuk menyaring dan mengelompokkan data.

```sql
-- Ambil semua data dengan umur > 18 dan urutkan berdasarkan umur
SELECT * FROM nama_tabel WHERE umur > 18 ORDER BY umur ASC;

-- Mengelompokkan dan menghitung jumlah berdasarkan kota
SELECT kota, COUNT(*) FROM pelanggan GROUP BY kota HAVING COUNT(*) > 3;

-- Batasi hanya tampilkan 10 data
SELECT * FROM produk LIMIT 10;

```
