---
layout: post
title:  "Rangkuman Desain dan Anlisis Algoritma"
date:   2025-06-09 15:00:00 +0800
categories: [Algoritma, Struktur Data]
tags: [DSA, Algoritma, Backtracking, Greedy, Graph, Dynamic Programming]
---

Rangkuman Materi kelompok 1 sampai 10 Desain dan Analisis Algoritma

---

### 1. Activity Selection Problem

**Apa itu?**
Ini adalah masalah optimasi di mana kita memiliki serangkaian aktivitas, masing-masing dengan waktu mulai dan waktu selesai. Tujuan kita adalah memilih jumlah aktivitas maksimum yang tidak tumpang tindih (non-overlapping).

**Bagaimana cara kerjanya (Pendekatan Greedy)?**
Pendekatan paling umum adalah strategi *greedy*:
1.  Urutkan semua aktivitas berdasarkan waktu selesai yang paling awal.
2.  Pilih aktivitas pertama yang selesai paling awal.
3.  Dari aktivitas yang tersisa, pilih aktivitas berikutnya yang waktu mulainya lebih besar atau sama dengan waktu selesai aktivitas yang terakhir dipilih.
4.  Ulangi hingga tidak ada aktivitas lagi yang bisa dipilih.

**Karakteristik & Penggunaan:**
* **Greedy Algorithm:** Membuat pilihan optimal secara lokal dengan harapan mencapai solusi optimal global.
* Digunakan dalam penjadwalan, alokasi sumber daya, dan masalah pemilihan interval.

---

### 2. Fractional Knapsack

**Apa itu?**
Masalah optimasi di mana kita memiliki tas (knapsack) dengan kapasitas terbatas dan sejumlah item, masing-masing dengan nilai dan beratnya. Tujuannya adalah untuk mengisi tas dengan item sehingga nilai totalnya maksimum, dan kita diizinkan untuk mengambil *fraksi* (bagian) dari item.

**Bagaimana cara kerjanya (Pendekatan Greedy)?**
Karena kita bisa mengambil fraksi, strategi *greedy* bekerja dengan baik:
1.  Untuk setiap item, hitung rasio nilai per berat (value/weight).
2.  Urutkan item dalam urutan menurun berdasarkan rasio nilai per berat ini.
3.  Ambil item dari yang memiliki rasio tertinggi. Jika item tidak muat sepenuhnya, ambil sebagiannya hingga tas penuh.

**Karakteristik & Penggunaan:**
* **Greedy Algorithm:** Memilih item yang paling efisien per unit berat terlebih dahulu.
* Berbeda dengan 0/1 Knapsack (tidak boleh mengambil fraksi), di mana pendekatan *greedy* tidak selalu optimal.
* Digunakan dalam alokasi sumber daya, pengiriman barang, dan masalah investasi.

---

### 3. Huffman Coding

**Apa itu?**
Huffman Coding adalah algoritma kompresi data lossless yang populer. Ini menghasilkan kode prefix untuk setiap karakter sedemikian rupa sehingga karakter yang paling sering muncul memiliki kode biner yang paling pendek, dan karakter yang jarang muncul memiliki kode yang lebih panjang.

**Bagaimana cara kerjanya (Pendekatan Greedy)?**
1.  Hitung frekuensi kemunculan setiap karakter dalam data input.
2.  Buat node daun (leaf node) untuk setiap karakter dengan frekuensinya.
3.  Ambil dua node dengan frekuensi terendah, gabungkan mereka menjadi node induk baru dengan frekuensi gabungan, dan tambahkan node induk ini kembali ke daftar.
4.  Ulangi langkah 3 hingga hanya ada satu node tersisa (akar pohon Huffman).
5.  Traverse pohon dari akar ke daun untuk mendapatkan kode biner untuk setiap karakter.

**Karakteristik & Penggunaan:**
* **Greedy Algorithm:** Pada setiap langkah, menggabungkan dua node dengan frekuensi terendah.
* Digunakan secara luas dalam format kompresi file (misalnya, JPEG, MP3, ZIP) dan protokol jaringan.

---

### 4. N-Queens Problem

**Apa itu?**
Ini adalah masalah klasik dalam pemrograman di mana tujuan kita adalah menempatkan *N* ratu (queens) di papan catur berukuran *N x N* sedemikian rupa sehingga tidak ada dua ratu yang saling menyerang (yaitu, tidak ada dua ratu yang berada di baris, kolom, atau diagonal yang sama).

**Bagaimana cara kerjanya (Pendekatan Backtracking)?**
Pendekatan terbaik adalah menggunakan **backtracking**:
1.  Mulai dari baris pertama, coba tempatkan ratu di setiap kolom yang memungkinkan.
2.  Untuk setiap penempatan, periksa apakah ratu tersebut menyerang ratu yang sudah ada.
3.  Jika aman, lanjutkan ke baris berikutnya dan ulangi prosesnya.
4.  Jika tidak ada tempat yang aman di baris saat ini, "mundur" (backtrack) ke baris sebelumnya dan coba posisi ratu yang berbeda.
5.  Ulangi hingga semua *N* ratu ditempatkan atau semua kemungkinan telah dieksplorasi.

**Karakteristik & Penggunaan:**
* **Backtracking Algorithm:** Mencari solusi dengan membangun solusi secara inkremental dan membuang solusi yang tidak valid saat menemukannya.
* Contoh sempurna untuk memahami konsep backtracking. Digunakan dalam masalah kombinatorial dan pencarian solusi dalam ruang masalah yang besar.

---

### 5. Subset Sum Problem

**Apa itu?**
Diberikan sebuah himpunan bilangan bulat dan nilai target, masalah Subset Sum adalah menentukan apakah ada subset dari himpunan tersebut yang elemen-elemennya berjumlah tepat sama dengan nilai target.

**Bagaimana cara kerjanya (Pendekatan Dynamic Programming / Backtracking)?**
1.  **Dynamic Programming:** Membangun tabel (biasanya 2D) di mana `dp[i][j]` menunjukkan apakah jumlah `j` dapat dibentuk menggunakan `i` elemen pertama dari himpunan.
    * `dp[i][j] = dp[i-1][j]` (tanpa memasukkan elemen ke-i)
    * `dp[i][j] = dp[i-1][j - arr[i-1]]` (jika memasukkan elemen ke-i)
2.  **Backtracking:** Rekursif mencoba setiap elemen: apakah elemen saat ini disertakan dalam subset atau tidak.

**Karakteristik & Penggunaan:**
* **NP-Complete:** Tidak ada algoritma *polynomial-time* yang diketahui untuk masalah ini.
* Digunakan dalam kriptografi, optimasi keuangan, dan masalah partisi.

---

### 6. Rat in a Maze

**Apa itu?**
Masalah klasik di mana seekor tikus harus menemukan jalan dari titik awal ke titik tujuan dalam labirin yang diberikan, yang direpresentasikan sebagai matriks biner (0 untuk blokir, 1 untuk jalan).

**Bagaimana cara kerjanya (Pendekatan Backtracking)?**
1.  Mulai dari posisi awal tikus.
2.  Coba bergerak ke empat arah (atas, bawah, kiri, kanan) dari posisi saat ini.
3.  Untuk setiap langkah yang valid (di dalam batas labirin dan bukan blokir):
    * Tandai sel tersebut sebagai bagian dari jalur solusi.
    * Rekursif panggil fungsi untuk bergerak dari sel baru ini.
4.  Jika rekursi kembali tanpa menemukan jalur (jalan buntu), "mundur" (backtrack) dengan menghapus penanda dari sel saat ini dan mencoba arah lain.
5.  Jika tujuan tercapai, cetak jalur solusi.

**Karakteristik & Penggunaan:**
* **Backtracking Algorithm:** Mirip dengan N-Queens, ia mengeksplorasi semua kemungkinan jalur dan mundur jika menemui jalan buntu.
* Digunakan dalam navigasi robot, game AI, dan masalah pencarian jalur.

---

### 7. Breadth-First Search (BFS)

**Apa itu?**
BFS adalah algoritma penelusuran (traversal) atau pencarian graf yang menjelajahi graf atau struktur pohon secara *level-by-level* atau *layer-by-layer*. Dimulai dari node sumber, ia mengunjungi semua tetangga node tersebut, kemudian semua tetangga dari tetangga tersebut, dan seterusnya.

**Bagaimana cara kerjanya?**
1.  Gunakan antrean (queue) untuk menyimpan node yang akan dikunjungi.
2.  Masukkan node sumber ke antrean dan tandai sebagai dikunjungi.
3.  Selama antrean tidak kosong:
    * Keluarkan node dari antrean.
    * Kunjungi semua tetangga yang belum dikunjungi dari node yang dikeluarkan.
    * Tambahkan tetangga tersebut ke antrean dan tandai sebagai dikunjungi.

**Karakteristik & Penggunaan:**
* **Graph Traversal:** Menjamin menemukan jalur terpendek dalam graf yang tidak berbobot (unweighted graph).
* Digunakan dalam:
    * Menemukan jalur terpendek dalam graf tidak berbobot.
    * Mencari semua node yang terhubung.
    * Algoritma *web crawler*.
    * Pencarian jalur di game (misalnya, mencari sel terdekat).

---

### 8. Depth-First Search (DFS)

**Apa itu?**
DFS adalah algoritma penelusuran (traversal) atau pencarian graf yang menjelajahi sejauh mungkin di sepanjang setiap cabang sebelum melakukan *backtracking*. Ini seperti menjelajahi labirin dengan selalu mengambil satu arah hingga buntu, lalu kembali dan mencoba arah lain.

**Bagaimana cara kerjanya?**
1.  Gunakan tumpukan (stack) atau rekursi (yang secara implisit menggunakan tumpukan panggilan).
2.  Mulai dari node sumber, tandai sebagai dikunjungi.
3.  Jika menggunakan rekursi:
    * Kunjungi node saat ini.
    * Untuk setiap tetangga yang belum dikunjungi, panggil DFS secara rekursif pada tetangga tersebut.
4.  Jika menggunakan tumpukan:
    * Masukkan node sumber ke tumpukan.
    * Selama tumpukan tidak kosong:
        * Keluarkan node dari tumpukan.
        * Jika node belum dikunjungi, kunjungi dan tandai sebagai dikunjungi.
        * Masukkan semua tetangga yang belum dikunjungi ke tumpukan.

**Karakteristik & Penggunaan:**
* **Graph Traversal:** Cocok untuk menemukan jalur atau memeriksa konektivitas.
* Digunakan dalam:
    * Menemukan komponen yang terhubung.
    * Mendeteksi siklus (cycles) dalam graf.
    * Pencarian solusi dalam masalah seperti labirin atau puzzle (mirip dengan backtracking).
    * Pohon (tree) traversal (pre-order, in-order, post-order).

---

### 9. Kahn’s Algorithm (untuk Topological Sort)

**Apa itu?**
Algoritma Kahn adalah salah satu metode untuk melakukan *Topological Sort* (pengurutan topologis) pada Directed Acyclic Graph (DAG). Pengurutan topologis adalah urutan linier dari vertex-vertex dalam DAG sedemikian rupa sehingga untuk setiap edge terarah `u -> v`, vertex `u` selalu datang sebelum vertex `v` dalam urutan tersebut.

**Bagaimana cara kerjanya?**
1.  Hitung *in-degree* (jumlah edge yang masuk) untuk setiap vertex.
2.  Inisialisasi antrean (queue) dengan semua vertex yang memiliki *in-degree* 0.
3.  Selama antrean tidak kosong:
    * Keluarkan vertex `u` dari antrean dan tambahkan ke daftar pengurutan topologis.
    * Untuk setiap tetangga `v` dari `u`:
        * Kurangi *in-degree* `v` sebesar 1.
        * Jika *in-degree* `v` menjadi 0, tambahkan `v` ke antrean.
4.  Jika jumlah vertex dalam daftar pengurutan topologis tidak sama dengan total vertex di graf, berarti ada siklus (cycle) dalam graf (dan itu bukan DAG).

**Karakteristik & Penggunaan:**
* **Graph Algorithm:** Khusus untuk DAGs.
* Digunakan dalam:
    * Penjadwalan tugas (misalnya, dependensi antar tugas di proyek).
    * Urutan kompilasi modul.
    * Resolusi dependensi paket.

---

### 10. Dijkstra’s Algorithm

**Apa itu?**
Dijkstra's Algorithm adalah algoritma untuk menemukan jalur terpendek dari satu vertex sumber ke semua vertex lainnya dalam graf berbobot (weighted graph), di mana semua bobot edge adalah non-negatif.

**Bagaimana cara kerjanya?**
1.  Inisialisasi jarak ke vertex sumber menjadi 0 dan jarak ke semua vertex lain menjadi tak hingga (infinity).
2.  Gunakan struktur data *min-priority queue* untuk menyimpan vertex yang akan dieksplorasi, diurutkan berdasarkan jarak terpendek yang diketahui.
3.  Masukkan vertex sumber ke priority queue.
4.  Selama priority queue tidak kosong:
    * Keluarkan vertex `u` dengan jarak terpendek dari priority queue.
    * Jika `u` sudah dikunjungi, lanjutkan.
    * Tandai `u` sebagai dikunjungi.
    * Untuk setiap tetangga `v` dari `u`:
        * Jika `jarak[u] + bobot_edge(u,v) < jarak[v]`, maka perbarui `jarak[v]` dan tambahkan/perbarui `v` di priority queue.

**Karakteristik & Penggunaan:**
* **Graph Algorithm:** Solusi *single-source shortest path* (SSSP) untuk graf dengan bobot non-negatif.
* Jika ada bobot negatif, algoritma seperti Bellman-Ford atau SPFA harus digunakan.
* Digunakan dalam:
    * Aplikasi pemetaan dan navigasi (misalnya, Google Maps).
    * Routing jaringan.
    * Mencari jalur optimal dalam berbagai sistem.

---