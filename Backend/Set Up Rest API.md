
### 1
# set up REST-API 🔧


> cara set up REST API pada visual studio code

<br/>

### **a. buat Direktori Proyek**

buka terminal dan jalankan perintah berikut → untuk membuat folder dan mengubah directory kedalam file tersebut

```bash
mkdir my-api
cd my-api
npm init -y
```

**penjelasan**

- `mkdir` membuat direktori projek
- `cd` masuk ke dalamnya
- `npm init -y` menghasilkan file **`package.json`** secara otomatis, yang penting untuk mencatat semua dependensi dan skrip proyek

### b. install dependecies

install dependencies utama

```bash
npm install express cors dotenv
```

**penjelasan**

- `express` → framework backend minimalis untuk membuat server HTTP
- `cors` → mengizinkan komunikasi lintas domain (penting saat frontend dan backend di domain berbeda).
- `dotenv` → untuk mengatur konfigurasi environment (`.env`), seperti `PORT`, `DB_URI`, `JWT_SECRET`, dll.

### **c. install Dev Dependencies**

instal dependencies untuk pengembangan:

```bash
	npm install --save-dev typescript ts-node @types/node @types/express nodemon
```

**penjelasan**

- `typescript` → bahasa pemrograman berbasis JavaScript + tipe data statis
- `ts-node` → menjalankan file `.ts` langsung tanpa perlu compile dulu
- `@types/...` → definisi tipe untuk Node.js & Express
- `nodemon` → otomatis restart server saat file berubah

## Set Up Typescript :ts:

### **d. konfigurasi TypeScript**

inisialisasi TypeScript:

```bash
npx tsc --init
```

### **e. edit File `tsconfig.json`**

buka `tsconfig.json`, lalu ubah baris berikut:

- **Uncomment** dan atur `outDir`
- **Uncomment** dan atur `rootDir`
    
    ```json
    "rootDir": "./src",
    "outDir": "./dist",
    "esModuleInterop": true,
    ```
    
    **penjelasan**
    
    - `rootDir` → agar semua file `.ts` disimpan di `src`
    - `outDir` → hasil build TypeScript akan dikompilasi ke `dist`
    - `esModuleInterop` → memungkinkan kita menggunakan `import express from 'express'` tanpa error.

### **f. buat File `nodemon.json`**

buat file `nodemon.json` di direktori root proyek, lalu isi dengan:

```bash
touch nodemon.json
```

kemudian edit seperti dibawah ini

```json
{
    "watch": ["src"],
    "ext": "ts",
    "exec": "ts-node src/index.ts"
}
```

**penjelasan**

- `watch` → memantau perubahan dalam folder `src`
- `ext` → hanya file dengan ekstensi `.ts`
- `exec` → perintah untuk menjalankan project

**kegunaan**

installasi library **`nodemon`**

fungsinya untuk mengubah otomatis melakukan perubahan code dengan merestart terminal 

contoh : mengganti port yang di ubah (tanpa **`npm run dev`** lagi)

### **g. Tambahkan Skrip di `package.json`**

buka `package.json`, lalu tambahkan skrip berikut:

```json
"scripts": {
    "dev": "nodemon",
    "build": "tsc",
    "start": "node dist/index.js"
}
```

**penjelasan**

- `dev` → digunakan saat pengembangan (hot reload)
- `build` → meng-compile TypeScript ke JavaScript
- `start` → menjalankan hasil build (`dist`)

<br/>

## Folder 📑

### **h. Buat Folder dan File Utama**

buat folder `src` dan file `index.ts`:

```bash
mkdir -p src/{controllers,service,routes,middleware,models,validation,interface,utils}
touch src/index.ts
```

**kegunaan**

men-create server rest api dengan express

> Ini penting agar proyek kamu modular, terorganisir, dan mudah untuk dikembangkan saat tim bertambah besar atau fitur bertambah.
> 
- `controllers` → untuk fungsi yang menangani request & response HTTP
- `service` → ogika bisnis (misal, hitung harga diskon, akses database)
- `routes` → endpoint seperti `GET /users`, `POST /login`
- `middleware` → proses request sebelum controller (auth, error logging)
- `models` →model data untuk database (kalau pakai ORM/ODM)
- `validation` → validasi input user (pakai zod/joi/manual)
- `interface` → menjaga konsistensi tipe data antar file
- `utils` → helper function seperti hash password, generate token, format date

isi `src/index.ts` dengan kode dasar:

```tsx
import express from 'express';
import { Request, Response } from 'express';
import dotenv from 'dotenv';

dotenv.config();

const app = express();
const PORT = process.env.PORT || 8080;

app.use(express.json());
app.use(express.urlencoded({ extended: true }));

app.get('/', (req: Request, res: Response)=> {
    res.status(200).send("Welcome to Express API")
    
})

app.listen(PORT, () => {
    console.log(`Server running at http://localhost:${PORT}`);
});
```

**penjelasan**

- `dotenv.config()` → baca konfigurasi dari file `.env`
- `express.json()` → parse body request dengan format JSON
- `urlencoded()` → untuk menerima data dari form
- `router` → mengarahkan endpoint `/api/...` ke handler masing-masing

### **i. Jalankan Proyek**

untuk menjalankan server dalam mode pengembangan:

```bash
npm run dev
```

untuk membangun proyek:

```bash
npm run build
```

untuk menjalankan hasil build:

```bash
npm start
```
