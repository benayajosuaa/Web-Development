### unknown

# ⏰ async/await

**`async`** digunakan untuk mendefinisikan function asynchronous.

- Function `async` **selalu mengembalikan Promise**.

**`await`** hanya bisa digunakan di dalam function `async`.

- `await` digunakan untuk **menunggu** Promise selesai sebelum melanjutkan eksekusi.

🏹 Tujuannya : membuat kode asynchronous **terlihat seperti synchronous**, sehingga lebih mudah dibaca

### Analogi

**Bayangkan saat masak mie instan 🍜**

1. rebus air → butuh waktu 5 menit
2. Kalau kamu *nungguin terus* di depan kompor (kayak kode synchronous), kamu **nggak bisa ngapa-ngapain** selama air belum mendidih

Nah, dengan **asynchronous**, bisa dijalankan dengan : 

1. Nyalain kompor (mulai rebus air)
2. Sambil nunggu air mendidih, kamu bisa siapin bumbu, buka bungkus mie, dll.

➡️ Jadi: **async = kita nggak perlu berhenti kerja, bisa lanjut sambil nunggu proses lama selesai**

<br/>

## apa itu `asycn` ?

- Kalau function dikasih keyword `async`, otomatis dia **selalu balikin janji (Promise)**.
- Artinya: "Tenang, saya janji bakal kasih hasilnya nanti”

**contoh code :** 

```tsx
async function sapa() {
  return "Halo!";
}

console.log(sapa()); 
// Output: Promise { 'Halo!' }
```

Walaupun kita return string `"Halo!"`, karena ada `async`, hasilnya dibungkus dalam **Promise**

<br/>

## apa itu `await` ?

- `await` = “tolong tunggu janji ini selesai, baru lanjut kerja”
- Jadi, kalau punya janji (Promise), bisa paksa nunggu hasilnya keluar dulu.

**Analogi :**

1. pesen kopi di kafe ☕
2. Kalau nggak pakai `await`, kamu langsung jalan pergi → kopinya datang belakangan (nggak jelas siapa yang ambil)
3. Kalau pakai `await`, kamu **nunggu sebentar** sampai barista kasih kopi, baru kamu pergi

**contoh code :** 

```tsx
// simulasi bikin kopi (butuh waktu 3 detik)
function bikinKopi() {
  return new Promise((resolve) => {
    setTimeout(() => {
      resolve("☕ Kopi sudah jadi!");
    }, 3000);
  });
}

// pakai async/await
async function pesanKopi() {
  console.log("Pesan kopi...");
  const kopi = await bikinKopi(); // tunggu kopi selesai
  console.log(kopi);
  console.log("Minum kopi dan kerja lagi 🍪");
}

pesanKopi();
```

**output :** 

```tsx
Pesan kopi...
---- jeda dulu berapa saat -----
☕ Kopi sudah jadi!
Minum kopi dan kerja lagi 🍪

=== Code Execution Successful ===
```

**urutan output yang keluar :** 

1. Pesan kopi...
2. kemudian jeda waktu sesuai function **`bikinKopi`**
3. ☕ Kopi sudah jadi!
4. Minum kopi dan kerja lagi 🍪
