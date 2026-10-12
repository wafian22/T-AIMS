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

**Base URL:** `http://localhost:3000/api`
**Auth:** JWT Bearer Token (header: `Authorization: Bearer <token>`)
**Content-Type:** `application/json`

### 4.1 Authentication

| Method | Endpoint | Auth | Role |
|---|---|---|---|
| POST | /auth/login | Public | Semua |
| GET | /auth/me | Bearer | Semua |
| POST | /auth/logout | Bearer | Semua |
| POST | /auth/change-password | Bearer | Semua |

### 4.2 Users

| Method | Endpoint | Role |
|---|---|---|
| GET | /users | admin, super_admin |
| GET | /users/:id | admin, super_admin |
| POST | /users | admin, super_admin |
| PUT | /users/:id | admin, super_admin |
| DELETE | /users/:id | super_admin only |
| PUT | /users/:id/role | super_admin only |

### 4.3 Assets

| Method | Endpoint | Role |
|---|---|---|
| GET | /assets | Semua |
| GET | /assets/:id | Semua |
| POST | /assets | admin, super_admin |
| PUT | /assets/:id | admin, super_admin |
| DELETE | /assets/:id | super_admin only |
| GET | /assets/:id/history | Semua |
| GET | /assets/by-category | Semua |

### 4.4 Locations

| Method | Endpoint | Role |
|---|---|---|
| GET | /locations | Semua |
| GET | /locations/:id | Semua |
| POST | /locations | admin, super_admin |
| PUT | /locations/:id | admin, super_admin |
| DELETE | /locations/:id | super_admin only |

### 4.5 Monitoring

| Method | Endpoint | Auth | Role |
|---|---|---|---|
| POST | /monitoring/ping | Internal | Ananda |
| POST | /monitoring/http | Internal | Ananda |
| POST | /monitoring/tcp | Internal | Ananda |
| POST | /monitoring/ping-http | Internal | Ananda |
| GET | /monitoring/logs | Bearer | Semua |
| GET | /monitoring/status/:assetId | Bearer | Semua |
| GET | /monitoring/summary | Bearer | Semua |

### 4.6 Heartbeat (IoT)

| Method | Endpoint | Auth |
|---|---|---|
| POST | /heartbeat | Public (device) |
| GET | /heartbeat/:assetCode/latest | Bearer |

### 4.7 Incidents

| Method | Endpoint | Role |
|---|---|---|
| GET | /incidents | Semua |
| GET | /incidents/:id | Semua |
| POST | /incidents | admin, super_admin |
| PUT | /incidents/:id | admin, super_admin |
| DELETE | /incidents/:id | super_admin only |

### 4.8 Maintenance

| Method | Endpoint | Role |
|---|---|---|
| GET | /maintenance | Semua |
| POST | /maintenance | admin, super_admin |
| PUT | /maintenance/:id | admin, super_admin |
| DELETE | /maintenance/:id | super_admin only |

### 4.9 Notifications

| Method | Endpoint | Role |
|---|---|---|
| GET | /notifications | Semua |
| GET | /notifications/:id | Semua |
| PUT | /notifications/:id/read | Semua |
| POST | /notifications | admin, super_admin |
| DELETE | /notifications/:id | super_admin only |

### 4.10 Dashboard

| Method | Endpoint | Role |
|---|---|---|
| GET | /dashboard/stats | Semua |
| GET | /dashboard/uptime | Semua |
| GET | /dashboard/top-issues | Semua |
| GET | /dashboard/charts | Semua |
| GET | /dashboard/ai-report | Semua |

### 4.11 Format Response

**Sukses:**
```json
{ "success": true, "data": {}, "message": "Optional" }

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

---

## 8. SECURITY

- Credential disimpan di `.env` / secret config
- Tidak ada password di source code
- Authentication untuk endpoint
- SSL untuk production
- Backup rutin

---

## 9. DEPLOYMENT

| Environment | Fungsi |
|-------------|--------|
| Dev | Development lokal |
| Staging | Testing QA |
| Production | Live Teknolab |

**Deployment PIC:** Wafian (DevOps)

---

## 10. FAILURE SIMULATION

| Skenario | Expected |
|----------|----------|
| Matikan ESP32 | Status Offline, Last Seen stop |
| Cabut kabel LAN | Deteksi gangguan jaringan |
| Stop MQTT Broker | Health check gagal |
| Matikan Raspberry Pi | Status Offline |
| Stop web/API | HTTP health check gagal |
| Nyalakan kembali | Recovery + notifikasi |

---

## 11. TOOLS DEVELOPMENT

| Tool | Fungsi |
|------|--------|
| Git + GitHub | Version control |
| Postman | API testing |
| VS Code | Code editor |
| n8n | Automation workflow |
| OBS Studio | Screen recording |

---

## 12. KONTAK TEKNIS

| Peran | Nama | Kontak |
|-------|------|--------|
| QA | Reza Tri | rezatriwardana7@gmail.com |
| Backend | Ahmad Reza Fahmi | rzafahmi351@gmail.com |
| DevOps | Wafian | wafianzaidan@gmail.com |

---

**Akhir Dokumen — Technical Documentation T-AIMS v1.0**