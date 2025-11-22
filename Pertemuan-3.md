
# ⚛️ Cara Kerja React *Low-Level*

### **Dari Kode Komponen ke Antarmuka Pengguna yang Efisien**

* **Fokus:** Memahami mekanisme *rendering*, komponen, dan Virtual DOM.
* **Relevansi:** Dasar pemahaman mengapa aplikasi modern seperti **Next.js** memiliki performa yang sangat tinggi.

---

## Pilar 1 - Komponen: Blok Bangunan UI 🧱

### **Komponen: Fungsi JavaScript dengan Tugas Spesifik**

* Dalam React (dan Next.js), UI dipecah menjadi unit independen yang disebut **Komponen**.
* **Definisi:** Komponen pada dasarnya adalah **fungsi JavaScript** yang:
    1.  Menerima *input* (**props**).
    2.  Mengembalikan (*return*) deskripsi tentang apa yang seharusnya muncul di layar (**JSX**).
* **Keuntungan:** Mendorong **Modularitas** dan **Reusabilitas** (*Reusability*).
    * Contoh: Tombol, *Sidebar*, *News Card*, atau bahkan seluruh halaman adalah komponen.

---

## Pilar 2 - Rendering & Mengapa *return* Mirip HTML? (JSX)

### **JSX: Jembatan antara Developer dan JavaScript Objek**

* Komponen tidak mengembalikan HTML, melainkan **JSX** (JavaScript XML).
* #### **Apa itu JSX?**
    * Ekstensi sintaksis untuk JavaScript yang **terlihat seperti HTML**.
    * Tujuannya adalah untuk menulis struktur UI dengan cara yang **mudah dibaca** oleh *developer*.

* #### **Proses *Transpilation***
    * Alat *build* (seperti **Babel** yang digunakan Next.js) **mengubah (transpile)** JSX menjadi panggilan fungsi JavaScript murni.

> **Contoh Sederhana:**
>
> ```jsx
> // Kode yang Anda Tulis (JSX)
> return (
>   <h1 className="title">Halo Next.js</h1>
> );
> ```
>
> **Kode yang Sebenarnya Dijalankan (JavaScript):**
>
> ```javascript
> // Hasil Transpilation
> return React.createElement(
>   "h1", 
>   { className: "title" }, 
>   "Halo Next.js"
> );
> ```

* **Kesimpulan:** Komponen mengembalikan JSX, yang kemudian diubah menjadi **objek JavaScript** yang mendeskripsikan struktur UI.

---

## Pilar 3 - Mekanisme Low-Level: Virtual DOM (VDOM) ⚡

### **Kunci Performa: Lapisan Abstraksi Cepat**

* React tidak langsung memanipulasi *Real DOM* (Document Object Model) *browser*.
* Ia menggunakan lapisan perantara yang disebut **Virtual DOM (VDOM)**.

#### **A. Konsep VDOM**

1.  **Representasi Ringan:** VDOM adalah **objek JavaScript** ringan, *blueprint* dari *Real DOM*.
2.  **Kecepatan:** Manipulasi objek JavaScript di memori jauh **lebih cepat** daripada memanipulasi *Real DOM* (yang memicu pembaruan visual yang mahal).



---

## Proses *Reconciliation* (Pencocokan)

### **Hanya Memperbarui Bagian yang Diperlukan (Diffing)**

Ketika **state** atau **props** (data) berubah, proses *reconciliation* terjadi:

1.  **Render VDOM Baru:** Fungsi komponen dijalankan ulang, menciptakan **pohon VDOM baru** (New VDOM Tree).
2.  **Proses *Diffing*:** React membandingkan VDOM baru dengan VDOM lama (**The Diffing Algorithm**).
    * React tahu secara presisi **elemen mana saja yang berubah**.
3.  **Pembaruan *Real DOM* (Patching):**
    * Alih-alih mengganti seluruh DOM, React hanya mengirimkan **patch** (perbedaan minimal) ke *Real DOM* di *browser*.

### **Hasil Akhir**

* React hanya memperbarui **bagian terkecil** dari UI yang benar-benar berubah.
* **Performa tinggi** dan **pengalaman pengguna yang mulus** (tidak ada *repaint* DOM yang tidak perlu).

---

## Penutup & Langkah Selanjutnya

# Ringkasan Kunci

1.  **Komponen** adalah fungsi yang mendeskripsikan UI.
2.  **JSX** diubah menjadi panggilan `React.createElement()` yang menghasilkan **Objek VDOM**.
3.  **Virtual DOM** memungkinkan perbandingan perubahan data (**Diffing**) secara cepat di memori.
4.  Hanya perbedaan minimal (The **Patch**) yang dikirim ke **Real DOM**.
