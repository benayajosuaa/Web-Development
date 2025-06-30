# Database 📦

Database → digunakan untuk menyimpan semua data agar bisa diolah kemudian nantinya 

Database sendiri memiliki banyak jenis :

- **Centralized**: Semua data disimpan di satu tempat
- **Distributed**: Data tersebar di banyak tempat
- **Relational (RDBMS)**: Data tersimpan dalam tabel yang saling berhubungan
- **NoSQL**: Cocok untuk data tidak berstruktur (misalnya JSON)
- **Object-oriented**: Data disimpan sebagai objek

## RDBMS - Relational Database Management Systems

> RDMS adalah salah satu jenis database yang menggunakan konsep SQL (structured Query Language) dalam penerapan database yang dianut 
Secara konsep RDBMS memiliki konsep penyimpanan yang mirip dengan “Excel”
> 

Tabel terdiri dari:

- **Kolom (attribute)**: jenis data (contoh: nama, umur)
- **Baris (row/record/tuple)**: satu data lengkap (misal: data satu orang)

RDBMS sendiri tadi sempat disinggung dimana menggunakan bahasa SQL, dimana bahasa tersebut merupakan bahasa standard untuk mengakses dan menanipulasi database, 

**🔑 Fungsi utama SQL :**

- **Create**: membuat database atau tabel baru
- **Read**: mengambil data
- **Update**: mengubah data
- **Delete**: menghapus data

## Data Type SQL 🚪

Setiap kolom dalam tabel memiliki **jenis data (data type)**, untuk memberi tahu jenis nilai apa yang bisa disimpan.

a. **Karakter/Text**

| Tipe | Deskripsi |
| --- | --- |
| `CHAR(n)` | Teks dengan panjang tetap n |
| `VARCHAR(n)` | Teks dengan panjang maksimal n |
| `TEXT` | Teks panjang, tidak terbatas |

**b. Angka/Numeric**

| Tipe | Deskripsi |
| --- | --- |
| `SERIAL` | Membuat **angka unik bertambah sendiri** |
| `SMALLINT` | Bilangan bulat kecil (±32.000) |
| `INTEGER` | Bilangan bulat sedang (±2 miliar) |
| `BIGINT` | Bilangan bulat besar (±9 triliun) |
| `NUMERIC(p, s)` | Angka presisi tinggi (misal untuk uang) |
| `DECIMAL(p, s)` | Sama seperti NUMERIC |
| `REAL` | Angka pecahan presisi tunggal (float 32 bit) |
| `DOUBLE PRECISION` | Pecahan presisi ganda (float 64 bit) |

 c. **Tanggal dan Waktu**

| Tipe | Deskripsi |
| --- | --- |
| `DATE` | Format: YYYY-MM-DD |
| `TIME` | Format: HH:MM:SS |
| `TIMESTAMP` | Gabungan tanggal + waktu |
| `TIMESTAMPTZ` | Timestamp + zona waktu |
| `INTERVAL` | Selisih waktu |

 **d. Lainnya**

| Tipe | Deskripsi |
| --- | --- |
| `BOOLEAN` | TRUE/FALSE |
| `JSON` | Menyimpan data JSON |
| `ARRAY` | Menyimpan array (misal: INTEGER[]) |
| `UUID` | ID unik global |
| `BYTEA` | Data biner (gambar/file) |

by : halobenayaa@gmail.com
