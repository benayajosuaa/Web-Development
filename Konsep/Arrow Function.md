### unknown

# Arrow Function

Arrow Function (`=>`) adalah **cara ringkas** untuk menulis fungsi anonim (tanpa nama) di JavaScript

**struktur umum function :**

```jsx
(parameter1, parameter2, ...) => {
  // isi fungsi
  return hasil;
}
```

**struktur umum arrow function :**

```jsx
// Fungsi biasa
function tambah(parameter1, parameter2) {
  return parameter1 + parameter2;
}

// Arrow function
const tambah = (parameter1, parameter2) => parameter1 + parameter2;
```

**yang perlu di notes adalah :**

1. Kalau **hanya 1 parameter**, kurung bisa dihapus
    
    ```jsx
    const cetak = nama => console.log(nama);
    ```
    
2. Kalau **tidak ada parameter**, tetap harus pakai `()`

<br/>

### Ringkasan Arrow Function

| Bentuk | Contoh | Penjelasan |
| --- | --- | --- |
| 1 parameter | `x => x + 1` | Jika hanya 1 parameter, kurung bisa dihapus |
| >1 parameter | `(x, y) => x + y` | Harus pakai kurung |
| Tanpa parameter | `() => 42` | Harus pakai kurung kosong |
| Body 1 baris | `x => x * 2` | Return otomatis |
| Body lebih dari 1 baris | `(x, y) => { let z = x + y; return z; }` | Harus pakai `{}` dan `return` |

<br/>

### Kesimpulan

| Hal yang Perlu Diingat |
| --- |
| Arrow function = fungsi singkat |
| Cocok untuk callback ringan |
| Tidak punya `this`, `arguments`, dan `constructor` |
| Punya bentuk pendek dan ekspresif |

<br/>

### Contoh Implementasi Arrow Function

1. **API Backend**

```jsx
const express = require('express');
const app = express();

const users = ['Ben', 'Ani', 'Caca'];

app.get('/users', (req, res) => {
  const panjang = users.filter(u => u.length > 3); // arrow
  res.json(panjang);
});

app.listen(3000, () => console.log('Server jalan di port 3000'));
```

2. **Manipulasi Database / API**

```jsx
const users = [
  { name: 'Ben', aktif: true },
  { name: 'Ani', aktif: false }
];

const aktifUser = users.filter(u => u.aktif); // pakai arrow function
```
