# Smart Load Balancer with Failover Using Node.js and Docker

## 📌 Deskripsi Proyek

Proyek ini merupakan implementasi Load Balancer sederhana menggunakan Node.js dan Express yang bertujuan untuk mendistribusikan request ke beberapa backend server secara merata menggunakan algoritma Round Robin.

Selain itu, sistem dilengkapi dengan fitur Failover sehingga apabila salah satu backend server mengalami gangguan atau berhenti berjalan, load balancer akan secara otomatis mengalihkan request ke server yang masih aktif tanpa menyebabkan kegagalan layanan.

Dashboard monitoring berbasis web juga disediakan untuk memantau distribusi request, status server, dan statistik sistem secara real-time.

---

## 🎯 Tujuan Proyek

* Memahami konsep Load Balancing pada Sistem Terdistribusi.
* Mengimplementasikan algoritma Round Robin.
* Mengimplementasikan mekanisme Failover Server.
* Memonitor performa server secara real-time.
* Menggunakan Docker untuk memudahkan deployment dan manajemen container.

---

## 🏗️ Arsitektur Sistem

```text
Client
   |
   v
Load Balancer
   |
   +---------> Backend Server 1
   |
   +---------> Backend Server 2
   |
   +---------> Backend Server 3
```

Load Balancer menerima request dari client kemudian mendistribusikannya ke backend server berdasarkan algoritma yang digunakan.

---

## 📂 Struktur Folder

```text
load-balancer-project
│
├── backend-server
│   ├── Dockerfile
│   ├── package.json
│   └── server.js
│
├── load-balancer
│   ├── public
│   │   └── index.html
│   ├── Dockerfile
│   ├── package.json
│   └── server.js
│
├── screenshots
│   ├── dashboard.png
│   ├── docker-stats.png
│   ├── terminal-round-robin.png
│   └── terminal-failover.png
│
└── docker-compose.yml
```

---

## ⚙️ Teknologi yang Digunakan

* Node.js
* Express.js
* Axios
* Docker
* Docker Compose
* HTML
* CSS
* JavaScript
* Chart.js

---

## 🚀 Fitur Utama

### 1. Round Robin Load Balancing

Request akan dibagikan secara bergantian ke setiap backend server.

Contoh:

```text
Request 1 → SERVER-1
Request 2 → SERVER-2
Request 3 → SERVER-3
Request 4 → SERVER-1
```

---

### 2. Failover Mechanism

Apabila salah satu backend server berhenti, load balancer akan mengabaikan server tersebut dan mengarahkan request ke server yang masih aktif.

Contoh:

```text
SERVER-1 = ONLINE
SERVER-2 = OFFLINE
SERVER-3 = ONLINE
```

Maka request akan menjadi:

```text
SERVER-1
SERVER-3
SERVER-1
SERVER-3
```

---

### 3. Health Check

Load Balancer melakukan pengecekan status backend server secara berkala untuk memastikan ketersediaan layanan.

---

### 4. Real-Time Dashboard

Dashboard monitoring menampilkan:

* Total Requests
* Request per Server
* Status Server
* Active Backend Count
* Pie Chart Distribution
* Request Activity Graph

---

## 🐳 Menjalankan Menggunakan Docker

### Build dan Jalankan Container

```bash
docker compose up --build
```

atau

```bash
docker-compose up --build
```

---

### Melihat Container Aktif

```bash
docker ps
```

---

### Menghentikan Semua Container

```bash
docker compose down
```

---

## 🌐 Endpoint

### Dashboard

```text
http://localhost:8080
```

### Statistik Sistem

```text
http://localhost:8080/api/stats
```

### Mengirim Request Melalui Load Balancer

```text
http://localhost:8080/request
```

---

## 🧪 Pengujian Round Robin

Kirim beberapa request:

```powershell
for ($i=1; $i -le 15; $i++) {
    curl.exe http://localhost:8080/request
}
```

Hasil:

```text
SERVER-1
SERVER-2
SERVER-3
SERVER-1
SERVER-2
SERVER-3
```

---

## 🧪 Pengujian Failover

1. Jalankan seluruh container.
2. Matikan salah satu backend server.

```bash
docker stop server2
```

3. Kirim request kembali.

Load balancer akan secara otomatis mengarahkan request hanya ke backend yang masih aktif.

---

## 📊 Hasil Implementasi

### Dashboard Monitoring

![Dashboard](screenshots/dashboard.png)

### Statistik Docker

![Docker Stats](screenshots/docker-stats.png)

### Round Robin Distribution

![Round Robin](screenshots/terminal-round-robin.png)

### Failover Testing

![Failover](screenshots/terminal-failover.png)

---

## 🔍 Kesimpulan

Proyek ini berhasil mengimplementasikan konsep Load Balancer menggunakan algoritma Round Robin dan mekanisme Failover pada lingkungan Docker. Sistem mampu mendistribusikan request secara merata ke beberapa backend server serta tetap menjaga ketersediaan layanan ketika salah satu server mengalami gangguan.

Implementasi dashboard monitoring juga membantu dalam memvisualisasikan kondisi sistem secara real-time sehingga memudahkan proses observasi dan pengujian.
