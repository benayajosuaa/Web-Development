### unknown

# Event - “e”

event dalam implementasinya pada suatu frontend adalah **“event”** atau suatu **interaksi pengguna** contoh interaksi seperti :

1. klik tombol (click) → **`onClik`**
2. isi input teks (change) → **`onChange`**
3. submit form (submit) → **`onSubmit`**
4. saat mouse diarahkah (mouse) → **`onMouseOver`** 

**contoh tamplate event / e pada umumnya :**

```tsx
<button onClick={...}>Klik</button>
```

<br/>

### “e”

e atau event adalah objek event yang otomatis dikirim oleh browser saatu suatu event terjadi 

**contoh sederhana :** 

```tsx
<input onChange={(e) => console.log(e)} />
```

**arti dari code diatas :**

fungsi **`(e) => console.log(e)`** akan diajalankan, dan e akan berisi semua info tentang input yang sedang kamu ketik

<br/>

### Jenis-Jenis Event

dibawah ini adalaah jenis-jenis event yang sering digunakan dalam implementasinya di dalam React :

| Event | Kapan Terjadi | Contoh |
| --- | --- | --- |
| `onClick` | Ketika elemen diklik | `<button onClick={...}>` |
| `onChange` | Saat isi input berubah | `<input onChange={...}>` |
| `onSubmit` | Saat form disubmit | `<form onSubmit={...}>` |
| `onKeyDown` | Saat tombol keyboard ditekan | `<input onKeyDown={...}>` |
| `onMouseEnter` | Saat kursor masuk elemen | `<div onMouseEnter={...}>` |
| `onBlur` | Saat input kehilangan fokus | `<input onBlur={...}>` |
| `onFocus` | Saat input mendapatkan fokus | `<input onFocus={...}>` |

<br/>

### Tipe-tipe Event dalam React

berikut ini adalah event yang biasa digunakan berdasarkan elementnnya :

| **Elemen** | **Event Umum** |
| --- | --- |
| `<input />` | `onChange`, `onFocus`, `onBlur` |
| `<form>` | `onSubmit` |
| `<button>` | `onClick` |
| Seluruh elemen | `onMouseEnter`, `onMouseLeave`, `onKeyDown` |

<br/>

### Properti “e”

dalam event atau e, terdapat beberapa properti yang mendukung fungsionalitas dari event tersebut. properti adalah nilai/data dalam objek. isi dari properti tersebut meliputi seperti dibawah ini : 

| `e` Properti | Artinya |
| --- | --- |
| `e.type` | Jenis event-nya: `"click"`, `"change"`, dll |
| `e.target` | Elemen HTML yang dipakai user |
| `e.target.value` | Nilai (isi) yang ada di elemen itu (misal input) |
| `e.preventDefault()` | Fungsi untuk mencegah aksi default |
| `e.stopPropagation()` | Fungsi untuk menghentikan event menyebar |

<br/>

### Event Handling React

**Event Handling** adalah cara menangani **aksi dari pengguna**, seperti:

- klik tombol (click)
- mengetik di input (change)
- mengirim form (submit)
- hover mouse (mouseEnter)
- tekan keyboard (keyDown)
    
    dll.
    

React menggunakan **camelCase** untuk nama event dan menggunakan fungsi sebagai handler-nya

<br/>

### 📌 Struktur Umum Penulisan Event

```jsx
<elementName eventName={functionHandler} />

```

Contoh:

```jsx
<button onClick={handleKlik}>Klik Saya</button>

```

> Di React, tidak menggunakan onclick="..." seperti di HTML biasa, tapi pakai {} dan camelCase: onClick, onChange, onSubmit, dst.
> 

<br/>

### 🔧 Template Umum: `onChange={(e) => setState(e.target.value)}`

**fungsinya :**

Mengambil **nilai input** dari user, dan menyimpannya ke state.

```jsx
<input
  value={state}
  onChange={(e) => setState(e.target.value)}
/>
```

**Penjelasan:**

- `e` adalah **event object** otomatis yang dikirim saat ada event
- `e.target` adalah **elemen HTML** tempat event terjadi (misal `<input>`)
- `e.target.value` adalah **isi/nilai** yang diketik user ke input itu
- `setState(...)` adalah React hook untuk menyimpan nilai input ke state

**💡 Contoh Skenario Real (Input Nama)**

```jsx
import { useState } from "react";

export default function InputNama() {
  const [nama, setNama] = useState("");

  return (
    <div>
      <input
        placeholder="Ketik nama..."
        value={nama}
        onChange={(e) => setNama(e.target.value)}
      />
      <p>Halo, {nama}</p>
    </div>
  );
}

```

**Alur Kerjanya:**

1. User ketik "Benaya"
2. `e.target.value = "Benaya"`
3. `setNama("Benaya")`
4. State `nama` jadi "Benaya"
5. Komponen render ulang dan menampilkan: `Halo, Benaya`

<br/>

### 📌 Daftar Event React yang Sering Digunakan

| Event | Kapan Terjadi | Contoh |
| --- | --- | --- |
| `onClick` | Ketika elemen diklik | `<button onClick={...}>` |
| `onChange` | Saat isi input berubah | `<input onChange={...}>` |
| `onSubmit` | Saat form disubmit | `<form onSubmit={...}>` |
| `onKeyDown` | Saat tombol keyboard ditekan | `<input onKeyDown={...}>` |
| `onMouseEnter` | Saat kursor masuk elemen | `<div onMouseEnter={...}>` |
| `onBlur` | Saat input kehilangan fokus | `<input onBlur={...}>` |
| `onFocus` | Saat input mendapatkan fokus | `<input onFocus={...}>` |

<br/>

### 🧩 Template Lain yang Berguna

**🎯 Checkbox (e.target.checked)**

```jsx
<input
  type="checkbox"
  checked={isChecked}
  onChange={(e) => setIsChecked(e.target.checked)}
/>

```

**🧩 Select Dropdown**

```jsx
<select
  value={selectedValue}
  onChange={(e) => setSelectedValue(e.target.value)}
>
  <option value="apple">Apple</option>
  <option value="banana">Banana</option>
</select>

```

**✍️ Textarea**

```jsx
<textarea
  value={message}
  onChange={(e) => setMessage(e.target.value)}
/>

```

**Form Submit**

```jsx
<form onSubmit={(e) => {
  e.preventDefault(); // Mencegah reload halaman
  handleSubmit(); // Jalankan fungsi submit
}}>
  <input ... />
  <button type="submit">Kirim</button>
</form>
```

<br/>

### 🛡️ Tips Penting

| Tips | Penjelasan |
| --- | --- |
| Gunakan `value={state}` | Agar input jadi controlled component |
| Selalu handle event dengan `e => ...` | Untuk akses properti seperti `.value`, `.checked`, dll |
| Pakai `e.preventDefault()` | Untuk mencegah perilaku default seperti reload halaman |
| Jangan lupa reset input | Gunakan `setState("")` setelah submit jika perlu |

<br/>

### Kesimpulan Utama

| Konsep | Penjelasan |
| --- | --- |
| `e` | Objek event (berisi info tentang interaksi user) |
| `e.target` | Elemen HTML tempat event terjadi |
| `e.target.value` | Nilai input yang diketik |
| `onChange` | Digunakan untuk input teks, textarea, select |
| `setState(...)` | Menyimpan nilai ke state React |
| `value={...}` | Menghubungkan nilai input dengan state (Controlled Component) |
