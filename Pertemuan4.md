## 🔑 Konsep Kunci Berikutnya: State dan Props

Jika komponen adalah blok bangunan UI, maka **State** dan **Props** adalah mekanisme yang menghidupkan UI tersebut dengan data dan interaktivitas.

### 1\. Props (Properties): Komunikasi *Parent* ke *Child*

**Props** adalah cara standar untuk meneruskan data dari komponen induk (*parent*) ke komponen anak (*child*).

  * **Apa itu Props?** Props adalah objek JavaScript yang berisi atribut data yang dikirim ke komponen anak. Pikirkan props sebagai **argumen** yang Anda berikan ke fungsi komponen.
  * **Sifatnya *Immutable* (Tidak Dapat Diubah):** Komponen anak hanya dapat **membaca** props, bukan mengubahnya. Ini memastikan aliran data satu arah (*unidirectional data flow*) yang membuat aplikasi lebih mudah diprediksi dan di-debug.
  * **Relevansi Proyek Portal Berita:** Anda akan menggunakan props untuk:
      * Meneruskan detail artikel (judul, konten, kategori) dari daftar berita induk ke komponen `NewsCard`.
      * Mengatur teks tombol navigasi di komponen `Header`.

#### Contoh Penerapan Props:

```jsx
// Komponen Induk
function NewsList() {
  const article = { title: "Berita Utama Hari Ini", date: "28/11/2025" };
  // Mengirim data 'article' sebagai props ke NewsCard
  return <NewsCard data={article} />; 
}

// Komponen Anak
function NewsCard(props) {
  // Mengakses data dari props
  return (
    <div>
      <h3>{props.data.title}</h3> 
      <p>Tanggal: {props.data.date}</p>
    </div>
  );
}
```

-----

### 2\. State: Data Internal yang Dapat Berubah (Interaktivitas)

**State** adalah data yang dimiliki dan dikelola oleh suatu komponen dan **dapat berubah** seiring waktu, biasanya karena interaksi pengguna (misalnya, klik tombol, input data).

  * **Apa itu State?** State adalah struktur data internal komponen yang, ketika diubah, akan memicu **proses *Reconciliation* VDOM** dan me-render ulang UI komponen tersebut.
  * **Sifatnya *Mutable* (Dapat Diubah):** State hanya dapat diubah menggunakan fungsi *setter* khusus (misalnya `useState` di React Hooks).
  * **Relevansi Proyek Portal Berita:** Anda akan menggunakan state untuk:
      * Mengelola status *Login* pengguna (apakah pengguna sudah masuk atau belum).
      * Mengontrol nilai yang diketik pengguna di *form* pendaftaran atau input komentar.
      * Mengubah tampilan halaman (misalnya, membuka/menutup *sidebar* navigasi).

#### Contoh Penerapan State (dengan React Hooks):

```jsx
import React, { useState } from 'react';

function LikeButton() {
  // Deklarasi state: 'count' adalah nilai, 'setCount' adalah fungsi untuk mengubahnya
  const [count, setCount] = useState(0); 
  
  return (
    <div>
      <p>Jumlah Suka: {count}</p>
      {/* Ketika di-klik, panggil setCount untuk mengubah state */}
      <button onClick={() => setCount(count + 1)}>
        Suka
      </button>
    </div> 
  );
}
```
