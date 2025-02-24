<div align="center">
  <h1 style="text-align: center;font-weight: bold">Workshop 1<br>Worskhop Administrasi Jaringan</h1>
  <h4 style="text-align: center;">Dosen Pengampu : Dr. Ferry Astika Saputra, S.T., M.Sc.</h4>
</div>
<br />
<div align="center">
  <img src="https://upload.wikimedia.org/wikipedia/id/4/44/Logo_PENS.png" alt="Logo PENS">
  <h3 style="text-align: center;">Disusun Oleh : <br>Kelompok 4</h3>
  <p style="text-align: center;">
    <strong>Muhammad Yafi Rifdah Zayyan
  </p>

<h3 style="text-align: center;line-height: 1.5">Politeknik Elektronika Negeri Surabaya<br>Departemen Teknik Informatika Dan Komputer<br>Program Studi Teknik Informatika<br>2023/2024</h3>
  <hr><hr>
</div>

# Analisis File http.cap dengan Wireshark

## 1. Versi HTTP yang Digunakan

- Berdasarkan kolom **Info**, terlihat bahwa permintaan **GET /download.html** menggunakan **HTTP/1.1**.
- Respon server juga menggunakan **HTTP/1.1 200 OK**.
- Jadi, versi HTTP yang digunakan dalam komunikasi ini adalah **HTTP/1.1**.

<p align="center">
    <img src="./img/img1.png">  
        </p>

---

## 2. IP Address dari Client dan Server

- **Client IP Address**:
  - Dari paket pertama (baris ke-18), `Source IP` adalah **145.254.160.237**, yang menunjukkan bahwa ini adalah **IP Client**.
- **Server IP Address**:
  - Dari paket ke-38 dan 27 (`HTTP/1.1 200 OK`), `Source IP` adalah **65.208.228.223** dan **216.239.59.99**.
  - Ini menunjukkan bahwa **server memiliki IP 65.208.228.223 dan 216.239.59.99**.

---

## 3. Waktu dari Client Mengirimkan HTTP Request

- Pada baris ke-4 (`GET /download.html`), waktu tercatat di kolom **Time** adalah **0.911310 detik**.

---

## 4. Waktu Server Mengirimkan Response dan Durasi

- Pada baris ke-38 (`HTTP/1.1 200 OK`), server merespons permintaan pada **4.846969 detik**.
- **Durasi antara request dan response** dihitung sebagai berikut:
Jadi, server membutuhkan sekitar **3.94 detik** untuk merespons permintaan ini.

---

## 5. Rangkuman Tahapan Komunikasi Menggunakan TCP
1. **Client menginisiasi koneksi ke server** dengan `GET /download.html HTTP/1.1`.
2. **Server menerima permintaan dan memprosesnya**.
3. **Server mengirimkan response** dengan kode `HTTP/1.1 200 OK`, yang berarti permintaan berhasil diproses.
4. **Data dikirimkan** ke client dalam bentuk halaman HTML atau file yang diminta.

---

**Kesimpulan:**  
Analisis ini menunjukkan bagaimana komunikasi HTTP terjadi dalam sesi ini, termasuk waktu request dan response, IP client dan server, serta versi HTTP yang digunakan.


# Rangkuman Tahapan Komunikasi Menggunakan TCP

## 1. **Pengertian**

Transmission Control Protocol (TCP) adalah protokol transport yang memastikan komunikasi data antara dua perangkat berlangsung secara andal dan berurutan. TCP bekerja dengan membangun koneksi sebelum data dikirim dan memastikan data sampai dengan benar.
<br><br>

<p align="center">
  <img src="./img/img2.png" alt="Diagram TCP" width="400">
</p>
<br><br>

---

## 2. **Tahapan Komunikasi TCP**

TCP menggunakan **model tiga lapisan komunikasi**, yaitu:

- **Node to Node** (Data Link Layer)
- **Host to Host** (Network Layer)
- **Process to Process** (Transport Layer)

Proses komunikasi TCP terdiri dari beberapa tahapan utama:

### **1. Establishing Connection (Three-Way Handshake)**

Sebelum data dikirim, TCP harus membangun koneksi antara pengirim dan penerima melalui **three-way handshake**:

1. **SYN (Synchronize)**: Klien mengirimkan paket SYN ke server untuk memulai koneksi.
2. **SYN-ACK (Synchronize-Acknowledge)**: Server merespons dengan paket SYN-ACK untuk menyetujui koneksi.
3. **ACK (Acknowledge)**: Klien mengirimkan paket ACK sebagai konfirmasi akhir.

Setelah tahap ini selesai, koneksi TCP dianggap terbuka dan siap untuk komunikasi.

---

### **2. Data Transfer**

Setelah koneksi terbentuk, data dikirimkan dengan mekanisme berikut:

- **Segmentasi**: Data dibagi menjadi beberapa segmen.
- **Penomoran Urutan (Sequence Numbering)**: Setiap segmen diberi nomor urut untuk memastikan pengiriman berurutan.
- **Pengakuan (Acknowledgment)**: Setiap segmen yang diterima dengan benar akan dikonfirmasi oleh penerima.
- **Kendali Kemacetan (Congestion Control)**: TCP mengatur jumlah data yang dikirim untuk menghindari kemacetan jaringan.

---

### **3. Connection Termination (Four-Way Handshake)**

Untuk mengakhiri koneksi, TCP menggunakan proses **four-way handshake**:

1. **FIN**: Klien mengirimkan permintaan untuk menutup koneksi.
2. **ACK**: Server mengakui permintaan dan menunggu proses selesai.
3. **FIN**: Server mengirimkan permintaan untuk menutup koneksi.
4. **ACK**: Klien mengakui permintaan dan koneksi ditutup.

---

## 3. **Kesimpulan**

- TCP menjamin komunikasi yang **andalan, berurutan, dan bebas duplikasi**.
- Terdapat tiga tahap utama: **Establishing Connection, Data Transfer, dan Connection Termination**.
- Protokol ini sangat penting dalam layanan seperti **HTTP, FTP, dan Email**.

Gambar di atas menunjukkan bagaimana data dikirimkan dari proses ke proses melalui berbagai lapisan jaringan, mengikuti prinsip TCP.
