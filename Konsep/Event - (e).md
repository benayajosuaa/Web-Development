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

| Event | Kapan Terjadi |
| --- | --- |
| `onClick` | Saat diklik (tombol, div, dll) |
| `onChange` | Saat isi input berubah |
| `onSubmit` | Saat form dikirim |
| `onKeyDown` | Saat tombol keyboard ditekan |
| `onFocus` | Saat input aktif/fokus |
| `onBlur` | Saat input kehilangan fokus |
| `onMouseEnter` | Saat mouse diarahkan ke elemen |

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

halobenayaa@gmail.com
