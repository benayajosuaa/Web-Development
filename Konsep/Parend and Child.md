### unknown

# Parent & Child 👪

<br/>

### **PARENT dan CHILD**

secara harafiah Parent dan Child dapat dikatakan sebagai berikut ini

- **Parent (induk)** = Komponen induk. Dialah yang **membungkus** atau **memanggil** komponen lain
- **Child (anak)** = Komponen anak. Komponen ini **dipanggil dari dalam komponen parent**.

analogi sederhanannya:

> Orang tua (parent) bisa punya 1 atau banyak anak (child), dan anak tinggal di dalam rumah orang tuanya (ditampilkan di dalam).
> 

### 📦 Contoh visual:

```html
<div>         <!-- Ini parent -->
  <p>...</p>  <!-- Ini child -->
</div>
```

### Implementasi Parent and Child

```tsx
export default function Page() {
  return (
    <div className="bg-blue-200 p-6">
      <h1>Ini Parent</h1>

      <div className="bg-red-200 p-4">
        <h1>Ini Child di dalam Parent</h1>
      </div>
    </div>
  );
}

```

**hasil :** 

<img width="546" height="170" alt="image" src="https://github.com/user-attachments/assets/91a57d5b-1091-47e9-a012-1c2533c234c1" />


### Penjelasan

| Fakta | Penjelasan Sederhana |
| --- | --- |
| Parent bisa punya banyak child | Di dalam 1 parent bisa ada banyak elemen anak. |
| Style bisa diwariskan | Misalnya `text-center` di parent, maka isi child ikut center juga (kecuali diubah). |
| Layout ditentukan parent | Parent bisa atur child pakai `flex`, `grid`, `gap`, dsb. |
| Parent bisa kirim data ke child | Pakai `props`, contohnya `<Child title="Halo" />`. |
| Child bisa kirim event ke parent | Misalnya saat tombol diklik, parent bisa tahu lewat fungsi yang dikirim. |
| Div dalam div = juga parent-child | Gak harus selalu komponen, bahkan `div` biasa pun bisa punya child di dalamnya. |

<br/>

## Fungsionalitas

| Aspek | Parent | Child |
| --- | --- | --- |
| Struktur | Pembungkus | Isi di dalam parent |
| Styling | Menentukan layout umum | Menentukan konten / tampilan detail |
| Data | Mengirim data via props | Menerima props, trigger callback |
| DOM Behavior | Mengontrol ukuran/posisi | Tergantung layout parent |
| Tailwind Role | `flex`, `grid`, `container`, `p-___`, `gap-____` | `w-____`, `h-_____`, `bg-____`, `text-_____` |

<br/>

### 📦 Contoh Case Parent and Child lainnya

1. **Struktur File**

```tsx
src/
├── App.tsx          ← ini parent
└── components/
    └── ChildBox.tsx ← ini child

```

2. **Event**

```tsx
function Child({ onClick }: { onClick: () => void }) {
  return <button onClick={onClick}>Klik aku</button>;
}

export default function Page() {
  const handleClick = () => alert("Diklik dari child!");
  return <Child onClick={handleClick} />;
}
```

3. **Data**

```tsx
function Child({ name }: { name: string }) {
  return <p>Halo, {name}</p>;
}

export default function Page() {
  return <Child name="Benaya" />;
}

```
<br/>

📬 [halobenayaa@gmail.com](mailto:halobenayaa@gmail.com)
