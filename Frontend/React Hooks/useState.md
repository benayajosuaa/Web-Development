### unknown

# React Hooks - useState

`useState` adalah salah satu **React Hook** yang digunakan untuk:

- Menyimpan data (state) di dalam function component
- Mengatur nilai yang bisa berubah secara dinamis
- Memicu *re-render* komponen saat data berubah

> Hook adalah fungsi khusus yang hanya bisa digunakan di dalam komponen React berbasis fungsi (function component), dan useState adalah yang paling sering digunakan
> 

<br/>

### Format Dasar `useState`

```tsx
const [state, setState] = useState(initialValue);
```

| Elemen | Penjelasan |
| --- | --- |
| `state` | Variabel untuk menyimpan nilai sekarang |
| `setState` | Fungsi untuk mengubah nilai state |
| `initialValue` | Nilai awal (default) dari state |

> Konvensi penamaan: state = nama, setState = setNama
> 

<br/>

### Contoh Sederhana

```tsx
import { useState } from "react";

export default function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>Nilai: {count}</p>
      <button onClick={() => setCount(count + 1)}>Tambah</button>
    </div>
  );
}
```

> Setiap kali tombol ditekan, nilai count akan bertambah, dan komponen akan re-render dengan nilai terbaru
> 

<br/>

### Jenis Data yang Bisa Disimpan

| Tipe Data | Contoh |
| --- | --- |
| String | `useState("halo")` |
| Number | `useState(0)` |
| Boolean | `useState(true)` |
| Array | `useState([])` |
| Object | `useState({})` |
| Array of Object | `useState([{...}])` |

**Contoh dengan Object:**

```tsx
const [user, setUser] = useState({ nama: "", umur: 0 });
```

**Contoh dengan Array of Object:**

```tsx
const [kontak, setKontak] = useState<{ nama: string; nomor: string }[]>([]);
```

<br/>

### Cara Mengubah State

State di React bersifat **immutable**, jadi untuk mengubahnya:

- **Tidak boleh langsung diubah**: `state.nama = "Benaya"` ❌
- Harus gunakan fungsi `setState` ✅

**✅ Contoh perubahan string:**

```tsx
setNama("Benaya");
```

**✅ Contoh perubahan array:**

```tsx
setList([...list, itemBaru]);
```

**✅ Contoh perubahan object:**

```tsx
setUser({ ...user, nama: "Benaya" });
```

<br/>

### 🧱 Struktur dan Alur

```
Input ➜ (onChange) ➜ setState ➜ state baru ➜ render ulang komponen

```

**Contoh alurnya:**

1. User ketik "Benaya" di input ➜ `setNama("Benaya")`
2. React update state ➜ `nama = "Benaya"`
3. Komponen re-render ➜ nilai baru muncul di input

<br/>

### Contoh Real: Form Input Kontak

```tsx
const [nama, setNama] = useState("");
const [nomor, setNomor] = useState("");
const [kontak, setKontak] = useState<{ nama: string; nomor: string }[]>([]);

const handleTambah = () => {
  if (nama && nomor) {
    setKontak([...kontak, { nama, nomor }]);
    setNama("");
    setNomor("");
  }
};

```

> Input akan disimpan dalam state, lalu dikumpulkan dalam array kontak
> 

<br/>

### Kesalahan Umum

| Kesalahan | Penjelasan |
| --- | --- |
| Mengubah state langsung | `state.push(...)` atau `state.nama = ...` |
| Tidak re-render | Karena tidak pakai `setState` |
| State campur aduk | Lebih baik pisahkan state sesuai fungsinya |
| Tidak memberi initial value yang sesuai | Bisa menyebabkan error saat render pertama |

<br/>

### Kesimpulan

`useState` adalah fondasi dalam React yang memungkinkan:

- Data disimpan di dalam komponen
- UI merespons perubahan data
- Komponen tetap fungsional dan deklaratif

> Tanpa useState, React hanya bisa merender tampilan statis tanpa interaksi.
>
