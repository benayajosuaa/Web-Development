### unknown

# 📘 Asinkronus

- **Sinkronus** → kode dijalankan baris demi baris, satu selesai baru lanjut
- **Asinkronus** → kode bisa “menunggu” operasi tertentu (misalnya ambil data dari server, baca file, hashing password), sementara program lain tetap jalan

Berguna untuk **task yang butuh waktu lama**, supaya aplikasi tidak crash

<br/>

## a. Perbandingan Asinkronus vs Sinkronus

### Sinkronus

```tsx
// urutan code [1]
console.log("[urutan output 1] Mulai");
for (let i = 0; i < 1e9; i++) {} // simulasi proses lama
// urutan code [2]
console.log("[urutan output 2] Selesai");
```

**output :** 

luaran code langsung di eksekusi sesuai urutannya

```tsx
[urutan output 1] Mulai
// jeda waktu disini 
[urutan output 2] Selesai

=== Code Execution Successful ===
```

### Asinkronus

```tsx
// urutan code [1]
console.log("[urutan output 1] Mulai");
// urutan code [2]
setTimeout(() => {
  console.log("[urutan output 2] Proses selesai setelah 2 detik");
}, 2000);
// urutan code [3]
console.log("[urutan output 3] Kode lain tetap jalan");
```

**output :** 

```tsx
[urutan output 1] Mulai
[urutan output 3] Kode lain tetap jalan
// jeda waktu disini
[urutan output 2] Proses selesai setelah 2 detik

=== Code Execution Successful ===
```

<br/>

## b. Asinkronus Javascript

cara kerja asinkronus javascript dengan cara : 

- JS pakai **Event Loop** dan **Callback Queue**
- Operasi lama (I/O, timer, HTTP request) “dilempar” ke background
- Kalau sudah selesai, hasilnya dikirim balik ke antrian untuk dieksekusi

### bentu-bentuk asinkronus js

1. **Callback**
    
    prinsipnya → fungsi dipanggil lagi setelah selesai
    
    ```tsx
    setTimeout(() => {
      console.log("Selesai dengan callback");
    }, 1000);
    ```
    
    Bisa bikin **callback hell** kalau bersarang terlalu dalam
    
2. Promise
    
    prinsipnya → erepresentasikan nilai **yang akan ada** (entah sukses atau gagal)
    
    ```tsx
    const task = new Promise((resolve, reject) => {
      setTimeout(() => resolve("Berhasil!"), 1000);
    });
    
    task.then(result => console.log(result))  // sukses
        .catch(err => console.error(err));    // gagal
    ```
    
3. Async/Await (cara modern)
    
    jenis asinkronus yang paling terbaru dan umum digunakan 
    
    ```tsx
    async function run() {
      try {
        const result = await task; // tunggu Promise selesai
        console.log(result);
      } catch (err) {
        console.error(err);
      }
    }
    run();
    
    ```

<br/>


## c. Implementasi

contoh implementasi dari konsep asinkronus adalah di **bcrypt**. hal itu diterapkan pada konsep bcrypt karna dalam proses hashing itu berat dan jika menggunakan sinkronus maka apps bisa crash sementara dengan konsep asinkronus itu dia bisa tetap berjalan

**contoh code :**

```tsx
import bcrypt from "bcrypt";

export async function comparePassword(password: string, hash: string): Promise<boolean> {
  return await bcrypt.compare(password, hash);
}

async function login() {
  const hash = await bcrypt.hash("rahasia", 10);

  const isMatch = await comparePassword("rahasia", hash);
  if (isMatch) {
    console.log("✅ Password cocok");
  } else {
    console.log("❌ Password salah");
  }
}
login();

```
