### unknown

# Image with Tailwind

berikut ini akan menjelaskan mengenai penerapan tailwind dalam set-up image dalam dunia frontend

<br/>

### Contoh Dasar

```html
<img src="loka.jpg" alt="Kopi Loka" className="w-64 h-auto" />
```

**penjelasan :**

- `src`: lokasi gambar
- `alt`: deskripsi gambar untuk SEO & aksesibilitas
- `class`: utility Tailwind

<br/>

### Ukuran Gambar 📏

1. **mengatur lebar dan tinggi**

| Utility | Fungsi |
| --- | --- |
| `w-...` | Lebar gambar |
| `h-...` | Tinggi gambar |

**Contoh:**

```html
<img src="kopi.jpg" className="w-48 h-48" />

```

- `w-48` → Lebar 12rem (192px)
- `h-auto` → Tinggi mengikuti rasio asli gambar

**b. Ukuran Custom**

```html
<img src="kopi.jpg" className="w-[300px] h-[200px]" />

```

biasanya dalam ukuran custom digunakan px yang di inginkan dan dibungkus dengan tanda kurung siku `[]`

<br/>

### 🧰 Responsive Image

menggunakan `max-w-full` dan `h-auto`

```html
<img src="kopi.jpg" className="max-w-full h-auto" />

```

Artinya:

- `max-w-full`: lebar maksimum mengikuti container (parent)
- `h-auto`: tinggi menyesuaikan rasio asli

<br/>

### 🧱 Object Fit

object fit biasanya digunakan untuk Memotong & Menyesuaikan Isi,  Kelas Tailwind untuk gaya `object-fit`:

| Utility | Fungsi |
| --- | --- |
| `object-contain` | Gambar *menyesuaikan penuh* tanpa terpotong |
| `object-cover` | Gambar *mengisi penuh* dan bisa terpotong |
| `object-fill` | Gambar *mengisi seluruh kontainer* bahkan distorsi |
| `object-none` | Tidak ada penyesuaian ukuran |
| `object-scale-down` | Gabungan antara `none` dan `contain` |

**Contoh:**

```html
<img src="kopi.jpg" className="w-64 h-64 object-cover" />

```

Gambar akan memenuhi kotak 64x64 **dengan cropping**

<br/>

### 🎯 Object Position

Atur bagian gambar mana yang ditampilkan saat `object-cover` digunakan.

```html
<img src="kopi.jpg" className="w-64 h-64 object-cover object-center" />

```

| Utility | Posisi |
| --- | --- |
| `object-center` | Tengah |
| `object-top` | Atas |
| `object-bottom` | Bawah |
| `object-left` | Kiri |
| `object-right` | Kanan |

<br/>

### 🖼️  Border & Rounded Corner

```html
<img src="kopi.jpg" className="rounded-lg border-4 border-gray-300" />

```

- `rounded-lg`: sudut melengkung → **`rounded-____`**  untuk sudut kelengkungan
- `border-4`: ketebalan border → **`border-____`**  untuk ketebalan border
- `border-gray-300`: warna border

<br/>

### 💡 Shadow & Opacity

```html
<img src="kopi.jpg" className="shadow-lg opacity-80" />

```

- `shadow-lg`: bayangan besar
- `opacity-80`: transparansi 80%

<br/>

### 🪞 Hover Effect pada Gambar

```html
<img src="kopi.jpg" className="w-64 h-64 object-cover hover:scale-105 transition duration-300" />

```

- `hover:scale-105`: membesar saat hover
- `transition duration-300`: animasi halus 300ms

<br/>

### Parent-Child Logic (Contoh `group`)

Tailwind pakai `group` class untuk membuat **parent bisa memengaruhi child**, cocok untuk hover.

**Contoh:**

```html
<div class="group">
  <img src="kopi.jpg" className="w-48 group-hover:opacity-50 transition" />
</div>

```

📝 Artinya:

- Parent `div` punya `group`
- Saat `div` di-*hover*, gambar anak (`img`) jadi `opacity-50`

<br/>

### 🖼️  Aspect Ratio (Perbandingan ukuran)

```html
<div class="aspect-w-16 aspect-h-9">
  <img src="kopi.jpg" className="object-cover" />
</div>

```

- `aspect-w-16 aspect-h-9`: rasio 16:9 (seperti YouTube)
- `object-cover`: gambar mengisi penuh

📌 Note: Pastikan `@tailwindcss/aspect-ratio` plugin diaktifkan.

<br/>

### ✂️ Crop Gambar (dengan div pembungkus)

Tailwind tidak secara langsung "crop", tapi kita bisa **membungkus `img` dengan div** dan pakai `overflow-hidden`.

```html
<div class="w-32 h-32 overflow-hidden rounded-xl">
  <img src="kopi.jpg" className="object-cover w-full h-full" />
</div>

```

Gambar akan "terpotong" karena keluar dari area `div` yang dibatas

<br/>

### 🧼  Menangani Gambar Pecah (HD)

**tips:**

- Gunakan `h-auto`, `w-auto`, `object-contain`
- Jangan pakai `w-... h-...` berlebihan jika gambar perlu skalabilitas
- Gunakan format gambar yang tepat (WebP, SVG jika memungkinkan)
- Gunakan `srcset` untuk gambar responsive HD (opsional non-Tailwind)

<br/>

### 🧪  Efek-Efek Lainnya

- `blur-sm` → gambar blur ringan
- `grayscale` → ubah jadi hitam putih
- `contrast-150` → kontras lebih tinggi
- `brightness-75` → brightness lebih rendah

```html
<img src="kopi.jpg" className="grayscale hover:grayscale-0 transition" />
```

<br/>

### 🔄  Responsive Breakpoints

Tailwind pakai breakpoint seperti:

- `sm:` (min-width 640px)
- `md:` (768px)
- `lg:` (1024px)
- `xl:`, `2xl:`

**contoh :**

```html
<img src="kopi.jpg" className="w-32 sm:w-48 md:w-64 lg:w-96" />

```

Gambar akan:

- `w-32` default
- `w-48` saat layar ≥ 640px
- `w-64` saat layar ≥ 768px

<br/>

## Summary

| Fitur | Kelas Tailwind |
| --- | --- |
| Ukuran | `w-...`, `h-...`, `max-w-full`, `h-auto` |
| Responsif | `sm:`, `md:`, `lg:`, dll |
| Posisi | `object-cover`, `object-center` |
| Efek | `shadow`, `rounded`, `hover:`, `transition` |
| Crop | Bungkus dengan `overflow-hidden` |
| Parent-Child | Gunakan `group` & `group-hover` |
| Aspect Ratio | `aspect-w`, `aspect-h` + plugin |
| Efek gambar | `blur`, `grayscale`, `brightness` |

<br/>

📬 halobenayaa@gmail.com
