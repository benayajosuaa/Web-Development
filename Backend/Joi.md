### unknown

# joi

**Joi** adalah **library JavaScript** (npm package) yang digunakan untuk **memvalidasi data** dengan cara **membuat aturan (schema)**

Fungsinya seperti **penjaga gerbang** di server

- Kalau **data user benar** → data diteruskan ke proses berikutnya.
- Kalau **data salah** → proses dihentikan dan server kirim pesan error.

> **simpelnya** 🔦
Kalau datanya**tidak sesuai**, kita bisa **mengembalikan error** ke user. Kalau datanya **sesuai**, kita **lanjutkan proses** ke tahap berikutnya
> 

<br/>

## a. Fungsi Joi

Tanpa validasi, user bisa mengirim data sembarangan ke server.

Contoh masalahnya:

- Email tidak valid → `"benaya.com"`
- Password terlalu pendek → `"123"`
- Username kosong → `""`
- Format data salah → kirim angka padahal harus string

Kalau tidak divalidasi, ini bisa menyebabkan:

- **Error di server**
- **Bug** pada aplikasi
- **Masalah keamanan** (user bisa mengirim data berbahaya)

Nah, **Joi** membantu mencegah itu 

<br/>

## b. Alur Kerja Joi

Secara umum kodingan Joi akan mempunyai 3 bagian utama

1. **Buat aturan validasi (schema)**
2. **Periksa data user**
3. **Tolak atau lanjutkan proses**

bayangkan ada suatu  **form register** di frontend, dan diminta kirim ke server:

**Case 1 — Data valid** ✅

```
POST /register
{
  "username": "benaya",
  "email": "benaya@example.com",
  "password": "rahasia123"
}
```

- Joi memeriksa → ✅ Lolos
- `next()` dijalankan → Data masuk database.

**Case 2 — Data tidak valid** ❌

```
POST /register
{
  "username": "be",
  "email": "salah",
  "password": "123"
}

```

- Joi memeriksa → ❌ Gagal
- Server mengirim respon:
    
    ```json
    {
      "message": "\"username\" length must be at least 3 characters long"
    }
    ```
    
    - Proses **berhenti** → Data tidak masuk database.

<br/>

## c. Implementasi Joi

berikut ini adalah tahapan implementasi Joi pada codingan backend

1. **Import Joi** 
    
    ```tsx
    import Joi from "joi";
    ```
    
    → Artinya, kita mengambil library Joi untuk digunakan membuat **schema validasi**
    
2. **Aturan Validasi (Schema)**
    
    contoh kasus : schema untuk register dan login 
    
    ```tsx
    // schema Register
    const registerSchema = Joi.object({
        username : Joi.string().min(3).max(40).required(),
        email: Joi.string().email().required(),
        password: Joi.string().min(6).required()
    })
    
    // schema Login
    const loginSchema = Joi.object({
        email: Joi.string().email().required(),
        password: Joi.string().required()
    });
    
    ```
    
    Ini adalah **aturan validasi** untuk **pendaftaran akun**:
    
    - **username** → Harus string, minimal 3 karakter, maksimal 40, dan wajib diisi
    - **email** → Harus string, berbentuk email yang valid, dan wajib diisi
    - **password** → Harus string, minimal 6 karakter, dan wajib diisi
        
        **contoh data valid :** 
        
        ```tsx
        {
          "username": "benaya",
          "email": "benaya@example.com",
          "password": "passwordku"
        }
        ```
        
        **contoh data tidak valid :** 
        
        ```tsx
        {
          "username": "be", 
          "email": "salahformat",  
          "password": "123"
        }
        ```
        
        Hasilnya, Joi akan **mengembalikan error**
        
3. **Middleware Validasi**
    
    Pada bagian ini, diminta untuk membuat  aturan yaitu membuat **middleware** untuk memeriksa data
    
    **Cara Kerjannya**
    
    - Ambil data dari `req.body` (input user).
    - Periksa apakah sesuai **registerSchema**.
    - Kalau ada error → kirim pesan error.
    - Kalau **tidak ada error** → jalankan `next()` → lanjut proses berikutnya (misalnya simpan ke database)
    
    ```tsx
    // contoh Middleware Register
    export const validateRegister = (req, res, next) => {
        const { error } = registerSchema.validate(req.body);
        if (error) {
            res.status(400).json({ message: error.details[0].message });
            return;
        }
        next();
    };
    
    // contoh Middleware Login
    export const validateLogin = (req, res, next) => {
        const { error } = loginSchema.validate(req.body);
        if (error) {
            res.status(400).json({ message: error.details[0].message });
            return;
        }
        next();
    };
    
    ```
    
    Untuk login, aturannya lebih sederhana:
    
    - Email harus valid dan wajib diisi
    - Password wajib diisi

<br/>

## d. syntax dan struktur Joi

dalam membuat joi, terdapat beberapa struktur atau syntax yang perlu di perhatikan yaitu : 

**Syntax umum:**

```tsx
const schema = Joi.object({
    fieldName: Joi.type().rules()
});
```

Jadi setiap field punya **tipe data** + **aturan**

**Contoh:**

```tsx
const schema = Joi.object({
    username: Joi.string().min(3).max(20).required(),
    age: Joi.number().min(18).max(60)
});
```

Artinya:

- `username` → String, minimal 3 karakter, maksimal 20, wajib diisi.
- `age` → Number, minimal 18, maksimal 60, **boleh kosong**

dan nantinnya untuk **memanggil validasi** kita bisa menggunakan **`.validate()`**

**Validasi Joi:**

```tsx
const { error, value } = schema.validate(req.body);

if (error) {
    return res.status(400).json({ message: error.details[0].message });
}

console.log(value); // Data valid
```

<br/>

## e. built in method Joi

### [1] Data Type

| **Method** | **Kegunaan** | **Contoh** |
| --- | --- | --- |
| `Joi.string()` | Hanya menerima **string** | `Joi.string()` |
| `Joi.number()` | Hanya menerima **angka** | `Joi.number()` |
| `Joi.boolean()` | Hanya menerima **true/false** | `Joi.boolean()` |
| `Joi.date()` | Hanya menerima **tanggal** | `Joi.date()` |
| `Joi.array()` | Hanya menerima **array** | `Joi.array()` |
| `Joi.object()` | Hanya menerima **object** | `Joi.object()` |
| `Joi.any()` | Bisa menerima **tipe apapun** | `Joi.any()` |

### [2] Aturan untuk String

| **Method** | **Kegunaan** | **Contoh** |
| --- | --- | --- |
| `.min(n)` | Minimal panjang karakter | `Joi.string().min(3)` |
| `.max(n)` | Maksimal panjang karakter | `Joi.string().max(30)` |
| `.length(n)` | Harus **tepat** n karakter | `Joi.string().length(10)` |
| `.email()` | Harus format email valid | `Joi.string().email()` |
| `.pattern(regex)` | Cocok dengan **regex tertentu** | `Joi.string().pattern(/^[A-Z]/)` |
| `.alphanum()` | Hanya huruf & angka | `Joi.string().alphanum()` |
| `.valid(...values)` | Hanya boleh beberapa nilai tertentu | `Joi.string().valid("admin", "user")` |

### [3] Aturan untuk Number

| **Method** | **Kegunaan** | **Contoh** |
| --- | --- | --- |
| `.min(n)` | Angka minimal | `Joi.number().min(18)` |
| `.max(n)` | Angka maksimal | `Joi.number().max(100)` |
| `.greater(n)` | Harus lebih besar dari n | `Joi.number().greater(0)` |
| `.less(n)` | Harus lebih kecil dari n | `Joi.number().less(100)` |
| `.integer()` | Harus bilangan bulat | `Joi.number().integer()` |
| `.positive()` | Harus angka positif | `Joi.number().positive()` |
| `.negative()` | Harus angka negatif | `Joi.number().negative()` |

### [4] Aturan untuk General

| **Method** | **Kegunaan** | **Contoh** |
| --- | --- | --- |
| `.required()` | Wajib diisi | `Joi.string().required()` |
| `.optional()` | Boleh kosong | `Joi.string().optional()` |
| `.default(value)` | Beri nilai default jika kosong | `Joi.string().default("guest")` |
| `.valid(...values)` | Harus sesuai pilihan | `Joi.string().valid("admin","user")` |
| `.invalid(...values)` | Tidak boleh sesuai nilai tertentu | `Joi.string().invalid("banned")` |

<br/>

## f. contoh implementasi

### [1] Validasi Email

**Impelementasi Code**

```tsx
const schema = Joi.object({
    email: Joi.string().email().required()
});
```

**Luaran Code**

```tsx
// output valid: 
{ "email": "benaya@example.com" }

// output tidak valid:
{ "email": "salah-email" }
```

### [2] Validasi Password

**Impelementasi Code**

```tsx
// variasi pertama
const schema = Joi.object({
    password: Joi.string().min(6).required()
});

// variasi kedua
//  -> kalau mau password harus huruf besar, huruf kecil, angka, dan simbol, bisa pakai regex
const schema = Joi.object({
    password: Joi.string()
      .pattern(new RegExp("^(?=.*[a-z])(?=.*[A-Z])(?=.*[0-9])(?=.*[!@#\\$%\\^&\\*])"))
      .min(8)
      .required()
});
```

**Luaran Code**

```tsx
// output valid: 
{ "email": "benaya@example.com" }

// output tidak valid:
{ "email": "salah-email" }
```

### [3] Validasi Array

**Impelementasi Code**

```tsx
const schema = Joi.object({
    hobbies: Joi.array().items(Joi.string().min(3)).min(1).required()
});
```

**Luaran Code**

```tsx
{
  "hobbies": ["makan", "coding"]
}
```

<br/>

## g. summary

- **Joi** adalah **alat validasi data** untuk Node.js + Express.
- Kodingan kamu membuat **dua schema** → `registerSchema` dan `loginSchema`.
- Lalu membuat **dua middleware** → `validateRegister` dan `validateLogin`.
- Middleware itu akan dipakai di **route** Express.
- Fungsinya **memfilter data user** sebelum disimpan ke database
