### unknown - kredibilitasnya 

# 📠 psql - **PostgreSQL interactive terminal**

- `psql` adalah **PostgreSQL interactive terminal** (command line tool resmi untuk PostgreSQL).
- Fungsinya untuk:
    - Tes koneksi database
    - Eksekusi query SQL manual
    - Mengecek struktur tabel, schema, function, dll
    - Debugging masalah koneksi (misalnya credential salah atau DB tidak bisa diakses)

<br/>

## a. Instalasi `psql`

Tergantung OS kamu:

### **MacOS (pakai Homebrew)**

```bash
brew install postgresql
```

> Setelah install, kamu bisa cek versi dengan:
> 

```bash
psql --version
```

### **Ubuntu/Debian**

```bash
sudo apt update
sudo apt install postgresql-client -y

```

### **Windows**

1. Download installer PostgreSQL dari:
    
    👉 https://www.postgresql.org/download/windows/
    
2. Saat install, centang **Command Line Tools**
3. Setelah selesai, pastikan `psql` bisa dipanggil dari PowerShell atau CMD

<br/>

## b. Tes Koneksi Manual ke Supabase

Gunakan `psql` dengan connection string yang kamu dapat dari Supabase:

```bash
psql 'postgresql://postgres.ztzcqmoubwsnmucqqhta:LokaCoffeshop2025!@aws-1-ap-southeast-1.pooler.supabase.com:5432/postgres?sslmode=require'
```

> ⚠️ Gunakan tanda ' (single quote) biar password yang ada karakter spesial tidak error di terminal.
> 

Kalau berhasil → akan masuk prompt:

```sql
psql (17.6, server 17.4)
SSL connection (protocol: TLSv1.3, cipher: TLS_AES_256_GCM_SHA384, compression: off, ALPN: none)
Type "help" for help.

postgres=>
```

<br/>

## c. Navigasi Dasar di `psql`

Beberapa command penting:

- `\dt` → lihat daftar tabel di schema saat ini.
- `\c dbname` → ganti database.
- `\dn` → lihat daftar schema.
- `\d tablename` → lihat detail struktur tabel.
- `\q` → keluar dari `psql`.

<br/>

## Summary

👉 Jadi alurnya:

1. Install `psql`.
2. Tes koneksi manual → bisa login ke database.
3. Baru lanjut ke `npx prisma db pull` untuk sync schema.
