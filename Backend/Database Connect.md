### unknown

# 🖇️ Link Database

Koneksi Supabase(Database-nya) dengan Prisma

<br/>

## a. **Setup Project**

1. Buka project backend (Node.js / Next.js).
2. Pastikan sudah ada Prisma:
    
    ```bash
    npm install prisma --save-dev
    npm install @prisma/client
    ```
    
3. Inisialisasi Prisma (kalau belum ada):
    
    ```bash
    npx prisma init
    ```
    
    dari command tersebut nantinya akan membuat folder `/prisma/schema.prisma` + file `.env`.
    

<br/>

## b. **Ambil Credential dari Supabase**

Dari **Supabase Dashboard → Project → Settings → Database**, catat:

- **Supabase URL** → contoh:
    
    ```
    https://ztzcqmoubwsnmucqqhta.supabase.co
    
    ```
    
- **Anon Key** (untuk frontend, bukan DB langsung).
- **Connection String (Pooler / Direct)**:
    - Pooler (PgBouncer, default port `6543`)
    - Direct connection (Postgres asli, port `5432`)

**contoh sederhana :**

```tsx
# Supabase Anon Key
SUPABASE_ANON_KEY="eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..........."
# Supabase Url
SUPABASE_URL="https://ztzcqmoubwsnmucqqhta.supabase.co"

# Connect to Supabase via connection pooling
DATABASE_URL="postgresql://postgres.ztzcqmoubwsnmucqqhta:[password-database]@aws-1-ap-southeast-1.pooler.supabase.com:6543/postgres?pgbouncer=true"
# Direct connection to the database. Used for migrations
DIRECT_URL="postgresql://postgres.ztzcqmoubwsnmucqqhta:[password-database]@aws-1-ap-southeast-1.pooler.supabase.com:5432/postgres"
```

<br/>

## c. **Tes Koneksi Manual ke Supabase**

Cek dulu database bisa diakses dari terminal:

```bash
psql 'postgresql://postgres.ztzcqmoubwsnmucqqhta:LokaCoffeshop2025!@aws-1-ap-southeast-1.pooler.supabase.com:5432/postgres?sslmode=require'
```

kalau berhasil → akan masuk prompt `postgres=>`

ketik `\dt` untuk lihat daftar tabel

ketik `\q` untuk keluar

<br/>

## d. **Prisma Pull Schema dari Supabase**

1. Pastikan `.env` berisi `DATABASE_URL` yang benar
2. Jalankan:
    
    ```bash
    npx prisma db pull
    ```
    
    👉 Prisma akan membaca struktur tabel di Supabase dan update `schema.prisma`
    

<br/>

## e. **Generate Prisma Client**

Agar bisa dipakai di kode JS/TS:

```bash
npx prisma generate
```

<br/>

## f. **Cek & Gunakan Schema**

- Buka `prisma/schema.prisma`.
- Kalau di DB ada tabel (misalnya `users`), Prisma akan buat:
    
    ```tsx
    model users {
      id        Int     @id @default(autoincrement())
      email     String  @unique
      created_at DateTime @default(now())
    }
    ```
