### unknown

# Array

**Array** adalah struktur data yang menyimpan beberapa nilai dalam satu variabel tunggal. nilai-nilai tersebut disimpan dalam urutan tertentu dan diakses menggunakan indeks (dimulai dari 0)

**contoh dalam JavaScript:**

```jsx
const angka = [1, 2, 3, 4, 5];
console.log(angka[0]);
```

maka outputnya adalah → 1

<br/>

### Operation Array

dalam implementasi array dalam software development, khususnya pada bagian backend terdapat beberapa operasi khusus yang harus diketahui karena bisa saja menjadi acuan dasar dalam melakukan suatu pembentukan logika

| Operasi | Penjelasan | Contoh |
| --- | --- | --- |
| **Akses** | Mengakses elemen dengan indeks | `arr[2]` |
| **Update** | Mengubah nilai elemen | `arr[0] = 10` |
| **Add** | Menambah item | `arr.push(99)` |
| **Delete** | Menghapus item | `arr.pop()` atau `arr.splice()` |
| **Length** | Mengetahui panjang array | `arr.length` |

<br/>

### Built in Method Javascript

Metode bawaan (**built-in method**) adalah fungsi yang sudah tersedia secara otomatis untuk tipe data atau objek tertentu dalam suatu bahasa pemrograman dan enggak perlu membuat atau mendefinisikannya sendiri

dalam javascript terdapat 2 jenis built in method yang biasa digunakan :

1. mutating → **mengubah** array

| Method | Keterangan | Contoh |
| --- | --- | --- |
| `push()` | Tambah elemen ke akhir | `arr.push(4)` |
| `pop()` | Hapus elemen terakhir | `arr.pop()` |
| `unshift()` | Tambah elemen di awal | `arr.unshift(0)` |
| `shift()` | Hapus elemen pertama | `arr.shift()` |
| `splice(i, n)` | Hapus/tambah elemen dari posisi tertentu | `arr.splice(2, 1)` |
| `reverse()` | Membalik array | `arr.reverse()` |
| `sort()` | Mengurutkan elemen | `arr.sort()` |
2. non mutating → **tidak mengubah** array

| Method | Keterangan | Contoh |
| --- | --- | --- |
| `map()` | Membuat array baru berdasarkan transformasi | `arr.map(x => x * 2)` |
| `filter()` | Mengambil elemen tertentu | `arr.filter(x => x > 3)` |
| `find()` | Mencari elemen pertama yang sesuai | `arr.find(x => x > 3)` |
| `reduce()` | Mengakumulasi jadi 1 nilai | `arr.reduce((a,b) => a+b)` |
| `slice(i, j)` | Mengambil sebagian array | `arr.slice(1,3)` |
| `includes()` | Cek apakah array mengandung nilai | `arr.includes(4)` |
| `indexOf()` | Cari indeks dari elemen tertentu | `arr.indexOf(5)` |
| `join()` | Gabungkan elemen jadi string | `arr.join(", ")` |

<br/>

### Implementasi Array

berikut ini beberapa implementasi array dalam dunia software development :

1. **Data dari database**: Mengambil hasil query SQL (misal `SELECT * FROM users`) akan jadi array of objects.
2. **Pengolahan batch data**: Array digunakan untuk loop data user, validasi, dan mapping response.
3. **Middleware processing**: Beberapa framework seperti Express.js menggunakan array dalam middleware chains.
4. **REST API response**: Format response REST biasanya array of JSON (misalnya list of products).

```jsx
// Contoh array response dari backend
[
  { id: 1, name: "Laptop" },
  { id: 2, name: "Keyboard" }
]
```

5. **Queue processing**: Dalam job processing seperti Redis Queue, RabbitMQ, antrean task bisa berupa array.
6. **Authorization list**: Array untuk menyimpan list role/permission.
7. **File uploads**: File yang diupload multipart bisa dikumpulkan dalam array untuk diproses batch.

<br/>

### Simbol dalam Array Javascript

berikut ini adalah beberapa simbol yang sering muncul ketika implementasi langsung dalam permainan Array javascript

| Simbol | Nama | Fungsi |
| --- | --- | --- |
| `...` | Spread / Rest | Menyebar atau mengumpulkan elemen |
| `[]` | Array Literal | Untuk membuat array baru |
| `==` / `===` | Perbandingan | Mengecek nilai (dan tipe untuk `===`) |
| `=>` | Arrow Function | Membuat function singkat |
| ` |  | `/`??` |
| `?.` | Optional chaining | Cek properti aman (undefined-safe) |

<br/>

### Impelementasi Array

1. **menjumlahkan seluruh Array**

```jsx
const arr = [1, 2, 3, 4];
const total = arr.reduce((acc, val) => acc + val, 0);
console.log(total); // 10
```

2. **memfilter user aktif**

```jsx
const users = [
  { name: "Ben", active: true },
  { name: "Ana", active: false }
];

const activeUsers = users.filter(u => u.active);
```

3. **mengubah format array data**

```jsx
const names = ["Ali", "Budi", "Citra"];
const greetings = names.map(name => `Hello, ${name}!`);
```

4. **menggabungkan 2 Array**

```jsx
const a = [1,2]; const b = [3,4];
const combined = [...a, ...b]; // [1,2,3,4]
```

5. **mencari element tertentu**

```jsx
const angka = [5, 7, 9];
const hasil = angka.find(x => x > 6); // 7

```
