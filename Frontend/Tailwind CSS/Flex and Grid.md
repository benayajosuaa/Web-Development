### unknown

# Flex and Grid 🎨

> berikut dibawah ini adalah penjelasan sederhana mengenai Flex dan Grid dalam Tailwind CSS
> 

<br/>

## Flex

Flexbox menyusun elemen dalam satu arah: **horizontal (`row`) atau vertikal (`column`)**, dan memudahkan penyusunan posisi (tengah, rata kanan, rata bawah, dst).

### Tabel Kelas Flexbox Lengkap:

| Class | Fungsi | Contoh Kode | Penjelasan |
| --- | --- | --- | --- |
| `flex` | Mengaktifkan Flexbox | `<div class="flex">...</div>` | Elemen anak akan diatur dengan sistem flex |
| `flex-row` | Susun anak secara horizontal (default) | `<div class="flex flex-row">...</div>` | Item sejajar ke kanan |
| `flex-col` | Susun anak secara vertikal | `<div class="flex flex-col">...</div>` | Item ditumpuk ke bawah |
| `justify-start` | Rata kiri (default) | `<div class="flex justify-start">A B</div>` | Semua item dirapatkan ke kiri |
| `justify-center` | Pusatkan item secara horizontal | `<div class="flex justify-center">A B</div>` | Semua item di tengah secara horizontal |
| `justify-end` | Rata kanan | `<div class="flex justify-end">A B</div>` | Semua item dirapatkan ke kanan |
| `justify-between` | Spasi di antara item | `<div class="flex justify-between">A B</div>` | Item di ujung kiri dan kanan |
| `items-start` | Posisi vertikal di atas | `<div class="h-32 flex items-start">...</div>` | Cocok untuk item dengan tinggi berbeda |
| `items-center` | Posisi vertikal di tengah | `<div class="h-32 flex items-center">...</div>` | Untuk rata tengah secara vertikal |
| `items-end` | Posisi vertikal di bawah | `<div class="h-32 flex items-end">...</div>` | Item menempel bawah |
| `gap-4` | Jarak antar item | `<div class="flex gap-4">A B C</div>` | Tambahkan jarak antar elemen |
| `basis-1/4` | Ukuran dasar item 25% | `<div class="flex"><div class="basis-1/4">A</div></div>` | Mengatur lebar awal (flex-grow berlaku setelah itu) |
| `flex-grow` | Izinkan item untuk membesar | `<div class="flex"><div class="flex-grow">A</div></div>` | Item akan membesar memenuhi ruang |
| `flex-shrink` | Izinkan item mengecil | `<div class="flex"><div class="flex-shrink">A</div></div>` | Digunakan saat ruang sempit |
| `flex-wrap` | Membungkus item jika overflow | `<div class="flex flex-wrap">...</div>` | Item akan turun ke baris baru jika penuh |

### **Contoh Flex Layout (Header 3 Kolom 1:4:1)**

```html
<div class="flex w-full">
  <div class="basis-1/6 bg-red-200 p-2">Sidebar Kiri</div>
  <div class="basis-4/6 bg-green-200 p-2">Konten Utama</div>
  <div class="basis-1/6 bg-blue-200 p-2">Sidebar Kanan</div>
</div>
```

<br/>

## GRID

Grid menyusun item dalam **baris dan kolom (2 dimensi)** dan sangat cocok untuk:

- Galeri
- Kartu produk
- Admin dashboard

### Tabel Kelas Grid Lengkap:

| Class | Fungsi | Contoh Kode | Penjelasan |
| --- | --- | --- | --- |
| `grid` | Mengaktifkan CSS Grid | `<div class="grid">...</div>` | Elemen anak diatur seperti tabel |
| `grid-cols-2` | Buat 2 kolom sama lebar | `<div class="grid grid-cols-2">...</div>` | Kontainer dipecah jadi 2 kolom |
| `grid-cols-3`, `grid-cols-4`, dst | Tambah jumlah kolom | `<div class="grid grid-cols-4">...</div>` | Berguna untuk galeri atau dashboard |
| `grid-rows-2`, dst | Tentukan jumlah baris | `<div class="grid grid-rows-2">...</div>` | Mengatur banyak baris |
| `col-span-2` | Anak menempati 2 kolom | `<div class="col-span-2">...</div>` | Gunakan jika satu item lebih lebar |
| `row-span-2` | Anak menempati 2 baris | `<div class="row-span-2">...</div>` | Gunakan untuk tile layout |
| `gap-4`, `gap-x-2`, `gap-y-2` | Jarak antar kolom/baris | `<div class="grid gap-4">...</div>` | Tambahkan jarak antar elemen grid |
| `place-items-center` | Posisi tengah vertikal dan horizontal | `<div class="grid place-items-center h-40">...</div>` | Untuk item grid yang simetris |
| `items-start`, `items-end`, `items-center` | Posisi vertikal dari isi | `<div class="grid items-end">...</div>` | Cocok untuk susun item tinggi berbeda |
| `justify-items-start`, `center`, `end` | Posisi horizontal dari isi | `<div class="grid justify-items-center">...</div>` | Cocok untuk isi rata tengah |

### **Contoh Grid Layout (3 kolom, 1 item lebih lebar)**

```html
<div class="grid grid-cols-6 gap-4">
  <div class="col-span-1 bg-gray-300 p-2">Sidebar Kiri</div>
  <div class="col-span-4 bg-gray-400 p-2">Konten Utama</div>
  <div class="col-span-1 bg-gray-300 p-2">Sidebar Kanan</div>
</div>

```

### **Contoh Grid Galeri Foto 3 Kolom**

```html
<div class="grid grid-cols-3 gap-4">
  <img src="img1.jpg" class="w-full h-40 object-cover" />
  <img src="img2.jpg" class="w-full h-40 object-cover" />
  <img src="img3.jpg" class="w-full h-40 object-cover" />
</div>

```

<br/>

## ✨ Tips Penggunaan Tailwind Flex & Grid

| Kebutuhan Umum | Gunakan | Alasan |
| --- | --- | --- |
| Navbar, header, footer | `flex` | Lebih ringan dan simpel |
| Sidebar dan konten utama | `flex` atau `grid` | Flex untuk 1 baris, Grid untuk responsive |
| Galeri, daftar produk | `grid` | Bisa otomatis atur kolom dan responsif |
| Ingin kontrol posisi + ukuran baris dan kolom | `grid` | Punya `row-span`, `col-span`, dsb |
| Ingin elemen sejajar + rata tengah | `flex` + `items-center` | Flex mudah untuk align |

<br/>

📬 [halobenayaa@gmail.com](mailto:halobenayaa@gmail.com)
