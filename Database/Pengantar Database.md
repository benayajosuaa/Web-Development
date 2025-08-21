### unknown

# Pengantar Sistem Basis Data

**database management systems** : hierarki database → vector → ….. sampai seterusnya

ecosystem database terbagi 2 jenis : 

1. **SQL** = postgreSQL, mySQL, oracle
2. **nonSQL** = mongoDB, vector

<br/>

### apa itu database ?

> database adalah digital repositori untuk bisa menyimpan, memanage, dan memastikan keamanan organisasi dari pengumpulan data
> 

model penyimpanan database terdapat 2 jensi : 

1. **relational**
    1. penyimpanannya menggunakan kolom dan baris 
    2. terdapat index / key sebagai patokan utama
2. **non relational**
    1. penggunaan database menggunakan sistem / konsep data data structure
    2. non retaional meliputi dari key-value, atau graphs

biasannya koneksi database bisa menggunakan **API** atau mungkin bisa melebih ke **MCP** (?)

<br/>

### apa yang bukan bagian database ?

database banyak diasumsikan sebagai tempat penyimpanan data, namun semua yang menyimpan data belum tentu database. contoh yang bukan database yaitu :

1. **excel**
    
    excel tidak termasuk kedalam database karena excel hanya spreadsheet yang sistemnya tidak terpusat dengan kontrol access dan tidak querynya tidak kompleks 

<br/>

### bagiamana database bekerja ?

secara sederhana database itu bekerja dengan cara : 

1. Kita kasih perintah (query)
    1. memberikan perintah 
    2. contohnya : “tolong cari buku dengan indeks ….”, “apa rekomendasi tempat liburan di tangerang ?”, dll
2. DBMS terjemahkan & optimalkan
    1. query user diperiksa dulu, apakah syntaxnya benar ? 
    2. DBMS mikir dan mencari cara atas query yang diberikan user
3. DBMS ambil data lewat index/katalog
    1. database akan memeriksa index (katalog)
    2. DBMS akan mengambil data yang sesuai 
4. Data dikembalikan ke kita
    1. data yang sudah ditemukan akan dimembalikan kembali ke user
5. Semua dijaga aman & konsisten lewat **ACID**
    
    database harus bisa memasikan 4 point utama dalam proses cara kerjannya : 
    
    - **A (Atomicity):** Semua perintah jalan semua, atau gagal semua
        
        (Kayak kalau pinjam 3 buku, harus dicatat semua atau batal semua)
        
    - **C (Consistency):** Data tetap konsisten (nggak ada yang “hilang” atau ganda)
    - **I (Isolation):** Kalau banyak orang akses, hasilnya tetap benar
    - **D (Durability):** Data tetap aman walau listrik mati

<br/>

### perlu di ingat !

perlu menjadi konsentrasi utama untuk bisa mengetahui apa itu **database** dan **DBMS (database management system)**

| Aspek | **Database** | **DBMS** |
| --- | --- | --- |
| **Isi** | **Kumpulan** data | Software **pengelola** data |
| **Fungsi** | **Menyimpan** data | **Mengelola**, **mengakses**, **mengamankan data** |
| **Contoh** | Tabel mahasiswa, tabel transaksi | MySQL, PostgreSQL, MongoDB, Oracle |
| **Analogi** | Rak buku | Pustakawan |

<br/>

### seberapa penting database itu ?

database itu sangat penting karena dilakukan sebagai perilaku untuk menyimpan suatu data atau informasi yang akan diakses sesuai kebutuhannya, contoh kasusnya : 

- **Perbankan & Keuangan** → data transaksi disimpan di **relational database** untuk keamanan & akurasi.
- **AI & Asisten Cerdas** → pakai **vector database** supaya bisa mencari informasi mirip/terkait.
- **Aplikasi sehari-hari** → dari e-commerce, media sosial, sampai transportasi online, semua pakai database untuk menyimpan & memproses data.

kenapa database menjadi suatu hal yang penting itu ?

1. **Data usability** → data bisa dipakai dengan mudah.
2. **Data integrity** → data tetap konsisten & benar.
3. **Data security & compliance** → data terlindungi dari akses ilegal + sesuai regulasi

<br/>

### kapan & bagaimana menggunakan database ?

kapan menggunakan dan bagaimana menggunakan database yang baik dan bisa memaksimalkan fungsionalitasnya ? 

berikut ini adalah aspek pertimbangannya : 

1. **Jenis Data** 
    - Kalau data **relasional** (ada baris & kolom) → pakai **RDBMS** (MySQL, PostgreSQL)
    - Kalau data **tidak terstruktur** (dokumen JSON, log, pesan) → pakai **NoSQL** (MongoDB, Cassandra)
    - Kalau data berupa **embedding/vektor** (AI, NLP, gambar) → pakai **Vector DB** (Qdrant, Pinecone)
2. **Tujuan Aplikasi** 
    - **Banking/ERP** → butuh akurasi tinggi → RDBMS
    - **Chatbot RAG / AI** → butuh pencarian mirip → Vector DB
    - **Rekomendasi produk / media** → bisa kombinasikan RDBMS + Vector DB
3. **Kebutuhan Performa** 
    - Kalau aplikasi **real-time** (misalnya stock trading, sensor IoT) → pilih DB dengan **kecepatan query tinggi** (misalnya Kinetica)
    - Kalau hanya laporan bulanan → RDBMS standar sudah cukup
4. **Biaya**
    - Data besar & format kompleks → biaya naik (penyimpanan + query)
    - Kadang lebih murah pakai **cloud database** ketimbang server sendiri
5. **scalability** 
    - **Scale-up (vertical):** tambah RAM/CPU di 1 server → cocok untuk RDBMS tradisional
    - **Scale-out (horizontal):** tambah banyak server (cluster) → cocok untuk NoSQL & vector DB

<br/>

### revolusi dari Database

1. **era awal - fs / file system (1950 - 1960an)**
    - Data disimpan sebagai **file flat** (teks/biner)
    - Aplikasi langsung akses file → sulit berbagi data antar program
    - Masalah: duplikasi data, rawan inkonsistensi
2. **era navigational database (1960 - 1970an)**
    - Model **hierarchical (IMS)** dan **network (CODASYL)**
    - Data diakses dengan pointer, seperti struktur pohon
    - Cepat tapi **kompleks** untuk diprogram
3. **era rational database (1970 - 2000an)**
    - Diperkenalkan oleh **E. F. Codd** (IBM, 1970).
    - Data disimpan dalam **tabel (baris & kolom)**.
    - Bahasa standar: **SQL**.
    - Keunggulan: mudah dipahami, konsisten, mendukung transaksi (ACID)
4. **era data warehouse & OLAP (1990 - 2000an)**
    - Fokus pada **analitik skala besar** (business intelligence)
    - Data dari banyak sumber dikumpulkan & diproses dalam **data warehouse**
    - Mendukung OLAP (Online Analytical Processing)
5. **era noSQL & Big Data (2005 - sekarang)**
    - Muncul karena kebutuhan **skala internet** (Facebook, Google, Amazon).
    - Jenis: **Key-Value, Document, Columnar, Graph**.
    - Cocok untuk **data tidak terstruktur** & **scalable (horizontal scaling)**
6. **era Cloud Database (2010 - sekarang)**
    - Database dikelola di **cloud** (AWS RDS, Firebase, Azure Cosmos DB).
    - Fleksibel, bayar sesuai pemakaian, bisa auto-scale
7. **era AI & Vector Database (2020 - sekarang)**
    - Fokus pada **high-dimensional data** (embedding teks, gambar, audio).
    - Mendukung **similarity search** (misalnya untuk RAG di ChatGPT, image search).
    - Contoh: **Qdrant, Pinecone, Weaviate**.
    - Digunakan untuk **rekomendasi, deteksi anomali, AI assistant, cybersecurity**
