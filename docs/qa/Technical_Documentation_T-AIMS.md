# TECHNICAL DOCUMENTATION — T-AIMS
## Teknolab Asset & Infrastructure Monitoring System

**Versi**   : 1.0
**Tanggal** : 12 Oktober 2026
**Penulis** : Reza Tri (QA & Documentation Engineer)
**Untuk**   : Tim Developer & Mentor

---

## 1. ARSITEKTUR SISTEM

T-AIMS terdiri dari 6 layer:

| Layer | Komponen | PIC |
|-------|----------|-----|
| 1 | Device / Asset | Semua perangkat Teknolab |
| 2 | Network & Monitoring Engine | Ananda |
| 3 | Database & Backend API | Faida, Ahmad Reza |
| 4 | Web Dashboard | Dika, Ahmad Aziz |
| 5 | Alert, History & Report | Arik |
| 6 | AI Automation | Arik |

---

## 2. TEKNOLOGI YANG DIGUNAKAN

| Komponen | Teknologi |
|----------|-----------|
| Backend | (sesuai implementasi Ahmad Reza) |
| Database | (sesuai implementasi Faida) |
| Frontend | (sesuai implementasi Dika) |
| IoT | ESP32, Raspberry Pi |
| Monitoring | Ping, HTTP, TCP, SNMP, MQTT |
| Automation | n8n |
| AI | LLM API |

---

## 3. STRUKTUR DATABASE

### 3.1 Tabel Minimum

| Tabel | Fungsi |
|-------|--------|
| assets | Data aset/perangkat |
| monitoring_logs | Log hasil monitoring |
| incidents | Catatan insiden/gangguan |
| locations | Data lokasi |
| users | Data pengguna |
| notifications | Data notifikasi |
| maintenance | Data maintenance |

### 3.2 Field Aset Minimum

Asset Code, Asset Name, Category, IP Address, MAC Address, Location, PIC, Monitoring Method, Status, Last Seen, Installation Date, Description.

---

## 4. API ENDPOINTS

### 4.1 Asset Management

| Method | Endpoint | Fungsi |
|--------|----------|--------|
| GET | /api/assets | List aset |
| GET | /api/assets/{id} | Detail aset |
| POST | /api/assets | Tambah aset |
| PUT | /api/assets/{id} | Update aset |
| DELETE | /api/assets/{id} | Hapus aset |

### 4.2 Heartbeat

| Method | Endpoint | Fungsi |
|--------|----------|--------|
| POST | /api/heartbeat | Kirim heartbeat IoT |

### 4.3 Status & Monitoring

| Method | Endpoint | Fungsi |
|--------|----------|--------|
| GET | /api/status | Status semua device |
| GET | /api/history | History monitoring |
| GET | /api/statistics | Statistik dashboard |

### 4.4 Notification

| Method | Endpoint | Fungsi |
|--------|----------|--------|
| POST | /api/notification | Test notifikasi |

**Catatan:** URL final menyesuaikan API Contract dari Ahmad Reza.

---

## 5. METODE MONITORING

| Jenis Device | Metode |
|--------------|--------|
| Server | Ping + TCP Port + HTTP/API |
| Raspberry Pi | Ping + Heartbeat |
| MikroTik | Ping / SNMP |
| Switch Manageable | Ping / SNMP |
| Access Point | Ping / SNMP |
| Website/API | HTTP Health Check |
| MQTT Broker | TCP / MQTT Health Check |
| ESP32 | HTTP/MQTT Heartbeat |
| PC / Mini PC | Ping + Agent |
| Non-network | Asset Registry / Manual |

---

## 6. ATURAN STATUS DEVICE

Status ditentukan oleh **rule teknis**, bukan warna dashboard:

| Status | Kondisi |
|--------|---------|
| Online | Heartbeat/ping terakhir < threshold |
| Offline | Heartbeat/ping terakhir > threshold |
| Warning | Response time tinggi / heartbeat delay |
| Unknown | Belum pernah terdeteksi |

**Threshold default:** 3× interval heartbeat (contoh: heartbeat 30 detik → offline setelah 90 detik).

---

## 7. ALUR DATA
