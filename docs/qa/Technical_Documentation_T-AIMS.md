# TECHNICAL DOCUMENTATION — T-AIMS
## Teknolab Asset & Infrastructure Monitoring System

**Versi**   : 1.1
**Tanggal** : 12 Oktober 2026
**Penulis** : Reza Tri (QA & Documentation Engineer)
**Untuk**   : Tim Developer & Mentor
**Sumber**  : API Contract v0.5 oleh Ahmad Reza Fahmi

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
| Backend | Node.js (Express) — API Contract v0.5 |
| Database | MySQL (sesuai implementasi Faida) |
| Frontend | (sesuai implementasi Dika) |
| IoT | ESP32, Raspberry Pi |
| Monitoring | Ping, HTTP, TCP, MQTT |
| Automation | n8n |
| AI | LLM API |
| Auth | JWT Bearer Token |

---

## 3. STRUKTUR DATABASE

### 3.1 Tabel Utama

| Tabel | Fungsi |
|-------|--------|
| users | Data pengguna |
| assets | Data aset/perangkat |
| locations | Data lokasi |
| monitoring_logs | Log hasil monitoring |
| incidents | Catatan insiden/gangguan |
| maintenance | Data maintenance |
| notifications | Data notifikasi |

### 3.2 Field Tabel assets

- asset_id (INT AUTO_INCREMENT PK)
- asset_code (VARCHAR 50 UNIQUE)
- asset_name (VARCHAR 150)
- category (VARCHAR 80)
- ip_address (VARCHAR 45 NULL)
- mac_address (VARCHAR 17 NULL)
- location_id (INT FK locations)
- pic_user_id (INT FK users)
- monitoring_method (VARCHAR 100)
- monitoring_config (LONGTEXT JSON)
- current_status (ENUM unknown, online, offline, maintenance)
- priority (INT DEFAULT 2)
- last_seen (DATETIME NULL)
- installation_date (DATE NULL)
- description (TEXT NULL)
- check_interval_seconds (INT DEFAULT 60)
- timeout_seconds (INT DEFAULT 5)
- retry_count (INT DEFAULT 3)
- created_at (TIMESTAMP)
- updated_at (TIMESTAMP)

### 3.3 Field Tabel monitoring_logs

- log_id (INT AUTO_INCREMENT PK)
- asset_id (INT FK assets)
- check_time (DATETIME)
- status (ENUM unknown, online, offline, error)
- method (VARCHAR 20 NULL)
- source (VARCHAR 20 DEFAULT monitoring_engine)
- response_time_ms (INT)
- details (TEXT)
- created_at (TIMESTAMP)

### 3.4 Kategori Device (Final)

| Kategori | Device |
|----------|--------|
| Router | MikroTik RB4011, Router Marketing |
| Switch Manageable | Core Switch Cisco 2960, Distribution D-Link, Access TP-Link |
| Access Point | UniFi U6-Lite, UniFi AC-LR |
| Server | Server T-AIMS Ubuntu, Pi-hole |
| Firewall | pfSense |
| Storage | Synology DS220+ |
| IoT Node | ESP32, Raspberry Pi |
| CCTV | CCTV Head Office, CCTV Marketing |
| TV | Smart TV Xiaomi |
| PC | PC Head Office 01, PC Head Office 02 |

---

## 4. API ENDPOINTS

**Base URL:** http://localhost:3000/api
**Auth:** JWT Bearer Token (header: Authorization: Bearer token)
**Content-Type:** application/json

### 4.1 Authentication

| Method | Endpoint | Auth | Role |
|--------|----------|------|------|
| POST | /auth/login | Public | Semua |
| GET | /auth/me | Bearer | Semua |
| POST | /auth/logout | Bearer | Semua |
| POST | /auth/change-password | Bearer | Semua |

### 4.2 Users

| Method | Endpoint | Role |
|--------|----------|------|
| GET | /users | admin, super_admin |
| GET | /users/:id | admin, super_admin |
| POST | /users | admin, super_admin |
| PUT | /users/:id | admin, super_admin |
| DELETE | /users/:id | super_admin only |
| PUT | /users/:id/role | super_admin only |

### 4.3 Assets

| Method | Endpoint | Role |
|--------|----------|------|
| GET | /assets | Semua |
| GET | /assets/:id | Semua |
| POST | /assets | admin, super_admin |
| PUT | /assets/:id | admin, super_admin |
| DELETE | /assets/:id | super_admin only |
| GET | /assets/:id/history | Semua |
| GET | /assets/by-category | Semua |

### 4.4 Locations

| Method | Endpoint | Role |
|--------|----------|------|
| GET | /locations | Semua |
| GET | /locations/:id | Semua |
| POST | /locations | admin, super_admin |
| PUT | /locations/:id | admin, super_admin |
| DELETE | /locations/:id | super_admin only |

### 4.5 Monitoring

| Method | Endpoint | Auth | Role |
|--------|----------|------|------|
| POST | /monitoring/ping | Internal | Ananda |
| POST | /monitoring/http | Internal | Ananda |
| POST | /monitoring/tcp | Internal | Ananda |
| POST | /monitoring/ping-http | Internal | Ananda |
| GET | /monitoring/logs | Bearer | Semua |
| GET | /monitoring/status/:assetId | Bearer | Semua |
| GET | /monitoring/summary | Bearer | Semua |

### 4.6 Heartbeat (IoT)

| Method | Endpoint | Auth |
|--------|----------|------|
| POST | /heartbeat | Public (device) |
| GET | /heartbeat/:assetCode/latest | Bearer |

### 4.7 Incidents

| Method | Endpoint | Role |
|--------|----------|------|
| GET | /incidents | Semua |
| GET | /incidents/:id | Semua |
| POST | /incidents | admin, super_admin |
| PUT | /incidents/:id | admin, super_admin |
| DELETE | /incidents/:id | super_admin only |

### 4.8 Maintenance

| Method | Endpoint | Role |
|--------|----------|------|
| GET | /maintenance | Semua |
| POST | /maintenance | admin, super_admin |
| PUT | /maintenance/:id | admin, super_admin |
| DELETE | /maintenance/:id | super_admin only |

### 4.9 Notifications

| Method | Endpoint | Role |
|--------|----------|------|
| GET | /notifications | Semua |
| GET | /notifications/:id | Semua |
| PUT | /notifications/:id/read | Semua |
| POST | /notifications | admin, super_admin |
| DELETE | /notifications/:id | super_admin only |

### 4.10 Dashboard

| Method | Endpoint | Role |
|--------|----------|------|
| GET | /dashboard/stats | Semua |
| GET | /dashboard/uptime | Semua |
| GET | /dashboard/top-issues | Semua |
| GET | /dashboard/charts | Semua |
| GET | /dashboard/ai-report | Semua |

### 4.11 Format Response

Sukses: success true, data object, message opsional.

Error: success false, error pesan.

### 4.12 Status Code

| Code | Arti |
|------|------|
| 200 | OK |
| 201 | Created |
| 204 | No Content |
| 400 | Bad Request |
| 401 | Unauthorized |
| 403 | Forbidden |
| 404 | Not Found |
| 409 | Conflict |
| 500 | Internal Server Error |

### 4.13 MQTT Topics

**Broker:** broker.teknolab.id:1883 (prod) / localhost:1883 (dev)
**QoS:** 1
**Retain:** false

| Topic | Arah | Fungsi |
|-------|------|--------|
| taims/heartbeat/{asset_code} | Device ke Backend | Kirim heartbeat |
| taims/alert/offline/{asset_code} | Backend ke Arik | Alert offline |
| taims/alert/recovery/{asset_code} | Backend ke Arik | Alert recovery |

---

## 5. METODE MONITORING

| Jenis Device | Metode |
|--------------|--------|
| Router | Ping |
| Switch Manageable | Ping / SNMP |
| Access Point | Ping / SNMP |
| Server | HTTP |
| Firewall | Ping |
| Storage | Ping |
| IoT Node | Heartbeat |
| CCTV | Ping + HTTP |
| TV | Ping |
| PC / Mini PC | Ping |

---

## 6. ATURAN STATUS DEVICE

Status ditentukan oleh rule teknis, bukan warna dashboard:

| Status | Kondisi |
|--------|---------|
| Online | Heartbeat/ping terakhir kurang dari threshold |
| Offline | Heartbeat/ping terakhir lebih dari threshold |
| Warning | Response time tinggi / heartbeat delay |
| Unknown | Belum pernah terdeteksi |
| Maintenance | Dalam perbaikan |

Threshold default: 3x interval heartbeat (contoh: heartbeat 30 detik, offline setelah 90 detik).

---

## 7. ALUR DATA

### 7.1 Alur Input Device (Admin)

Admin login, POST /api/assets, Database, Monitoring Engine.

### 7.2 Alur Monitoring (Ananda)

Monitoring Engine, cek device, POST /api/monitoring, Database, Dashboard.

### 7.3 Alur Heartbeat (Ilvina)

ESP32/RPi, MQTT topic, Backend subscribe, Database, Dashboard.

### 7.4 Alur Notifikasi (Arik)

Backend deteksi offline, publish MQTT, Arik subscribe, Telegram/Email.

---

## 8. SECURITY

- Credential disimpan di .env atau secret config
- Tidak ada password di source code
- Authentication: JWT Bearer Token
- Authorization: role-based (super_admin, admin, user)
- SSL untuk production
- Backup rutin

### Permission Matrix

| Endpoint | super_admin | admin | user |
|----------|:-----------:|:-----:|:----:|
| /auth/* | OK | OK | OK |
| /users GET POST PUT | OK | OK | X |
| /users/:id DELETE PUT role | OK | X | X |
| /assets GET | OK | OK | OK |
| /assets POST PUT | OK | OK | X |
| /assets/:id DELETE | OK | X | X |
| /monitoring/* GET | OK | OK | OK |
| /monitoring/* POST | OK | OK | X |
| /heartbeat POST | OK | OK | OK (device) |

---

## 9. DEPLOYMENT

| Environment | Fungsi | URL |
|-------------|--------|-----|
| Dev | Development lokal | http://localhost:3000 |
| Staging | Testing QA | (menunggu Wafian) |
| Production | Live Teknolab | (menunggu Wafian) |

Deployment PIC: Wafian (DevOps)

---

## 10. FAILURE SIMULATION

| Skenario | Expected Result |
|----------|-----------------|
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
| MySQL Workbench | Database management |

---

## 12. KONTAK TEKNIS

| Peran | Nama | Kontak |
|-------|------|--------|
| QA | Reza Tri | rezatriwardana@gmail.com / 0851-3681-1164 |
| Backend | Ahmad Reza Fahmi | rzafahmi351@gmail.com / 0857-0724-8435 |
| DevOps | Wafian | wafianzaidan@gmail.com / 0858-0421-4958 |
| PIC Teknolab | Elga Aris Prastyo | admin@office-teknolab.biz.id / (0342) 8178833 |

---

## 13. CHANGELOG

| Versi | Tanggal | Perubahan |
|-------|---------|-----------|
| 1.0 | 12/10/2026 | Draft awal |
| 1.1 | 12/10/2026 | Sync dengan API Contract v0.5 Ahmad Reza Fahmi |

---

Akhir Dokumen - Technical Documentation T-AIMS v1.1