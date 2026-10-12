# TEST PLAN — T-AIMS
## Teknolab Asset & Infrastructure Monitoring System

**Versi**        : 1.0  
**Tanggal**      : 12 Oktober 2026  
**Penulis**      : Reza Tri (QA, Testing & Documentation Engineer)  
**Project**      : T-AIMS — PKL 30 Hari di PT Teknolab Caraka Internasional  
**Status**       : Draft untuk direview Dzakwan & Damar  

---

## 1. TUJUAN TEST PLAN

Dokumen ini menjelaskan strategi, scope, pendekatan, sumber daya, dan jadwal
pengujian sistem T-AIMS. Test plan ini menjadi acuan QA selama 30 hari PKL
dan memastikan setiap fitur diuji sebelum dinyatakan DONE.

---

## 2. SCOPE PENGUJIAN

### 2.1 Fitur yang Diuji (12 Fitur Minimum)

| No | Fitur | Prioritas |
|---|---|---|
| 1 | Asset Management | P1 |
| 2 | Device Monitoring | P1 |
| 3 | Last Seen | P1 |
| 4 | Response Time | P2 |
| 5 | Monitoring History | P1 |
| 6 | Uptime / Downtime | P2 |
| 7 | Dashboard | P1 |
| 8 | Location | P2 |
| 9 | Notification | P1 |
| 10 | User Management | P1 |
| 11 | Reporting | P2 |
| 12 | AI Automation | P3 |

### 2.2 Yang TIDAK Diuji (Out of Scope)

- Performance testing skala besar (load testing 1000+ user)
- Security penetration testing profesional
- Mobile app native (T-AIMS berbasis web)
- Integrasi dengan sistem eksternal di luar T-AIMS

---

## 3. PENDEKATAN PENGUJIAN

### 3.1 Jenis Pengujian

| Jenis | Deskripsi | Kapan |
|---|---|---|
| **Smoke Test** | Uji cepat fitur inti | Hari 10, 20 |
| **Functional Test** | Uji fungsi sesuai AC | Setiap hari |
| **Regression Test** | Uji ulang setelah fix | Hari 16, 28 |
| **Negative Test** | Uji input tidak valid | Setiap fitur |
| **Boundary Test** | Uji batas nilai | Setiap fitur |
| **Failure Simulation** | Uji skenario gangguan | Hari 27 (wajib) |
| **Acceptance Test** | Uji akhir MVP | Hari 20 |
| **Security Test** | Uji akses & input | Hari 26 |

### 3.2 Metode Pengujian

- **Manual Testing** — untuk UI, UX, dashboard
- **API Testing (Postman)** — untuk backend endpoint
- **Database Validation** — untuk konsistensi data
- **Failure Simulation** — untuk skenario offline/recovery

---

## 4. KRITERIA MASUK & KELUAR

### 4.1 Entry Criteria (Sebelum Uji)

- ✅ Fitur selesai dikembangkan
- ✅ Kode ter-commit di repository dengan hash jelas
- ✅ Environment testing siap (backend jalan)
- ✅ Test case sudah dibuat
- ✅ Data uji tersedia

### 4.2 Exit Criteria (Setelah Uji)

- ✅ Semua test case P1 dijalankan (PASS/FAIL/BLOCKED jelas)
- ✅ Bug ditemukan sudah dilaporkan dengan Bug ID
- ✅ Bukti tersimpan (screenshot/log/video)
- ✅ Test report diperbarui
- ✅ Fitur layak DONE (semua DoD terpenuhi)

---

## 5. LINGKUNGAN PENGUJIAN

| Item | Detail |
|---|---|
| OS | Windows 10/11 |
| Browser | Chrome, Firefox |
| API Tool | Postman |
| Spreadsheet | Microsoft Excel |
| Version Control | Git + GitHub |
| Environment | Dev → Staging → Production |
| Backend | (TBD — dari Ahmad Reza) |
| Database | (TBD — dari Faida) |

---

## 6. JADWAL PENGUJIAN (30 HARI)

| Hari | Fokus | Test Type |
|---|---|---|
| 1 | Setup QA & Docs | - |
| 2–3 | Asset Survey | Data validation |
| 4 | Requirement | AC review |
| 5 | Architecture | Design review |
| 6 | Database Design | Schema test |
| 7 | UI Wireframe | UX review |
| 8–10 | Backend/API | API testing |
| 11–12 | Monitoring Engine | Functional |
| 13–14 | Device Heartbeat | Functional + Failure |
| 15–16 | Frontend Dashboard | UI/UX + Regression |
| 17 | Device Detail | Functional |
| 18 | History | Functional |
| 19 | Uptime/Downtime | Functional |
| **20** | **MVP RELEASE** | **Acceptance Test** |
| 21 | Notification Offline | Failure |
| 22 | Recovery Alert | Failure |
| 23 | Map/Location | Functional |
| 24 | AI Automation | Functional |
| 25 | Reporting | Functional |
| 26 | Security Test | Security |
| **27** | **FAILURE SIMULATION** | **Failure (WAJIB)** |
| 28 | Bug Fixing | Regression |
| 29 | Documentation | Review |
| 30 | Final Demo | Acceptance |

---

## 7. TIM & TANGGUNG JAWAB

| Nama | Peran | Tanggung Jawab QA |
|---|---|---|
| Reza Tri | QA Engineer | Test plan, test case, eksekusi, bug report, dokumentasi |
| Dzakwan | Shift Lead | Approval release, prioritas bug |
| Ahmad Reza | Backend Dev | Fix bug backend, API contract |
| Dika Yoga | Frontend Dev | Fix bug UI |
| Wafian | DevOps | Environment testing, backup |
| Ananda | Monitoring | Fix bug monitoring |
| Ilvina | IoT | Fix bug firmware |
| Arik | Automation | Fix bug notification |
| Damar | Analyst | Acceptance criteria |
| Faida | Database | Data uji, backup |
| Ahmad Aziz | UI/UX | Visual consistency |

---

## 8. DELIVERABLE QA

- ✅ Test Plan (dokumen ini)
- ✅ Test Case (Excel + template)
- ✅ Bug Report (Excel + template)
- ✅ Test Report Harian
- ✅ Daily Handover
- ✅ User Manual
- ✅ Technical Documentation
- ✅ Video Demo
- ✅ Final Evidence

---

## 9. RISIKO & MITIGASI

| Risiko | Dampak | Mitigasi |
|---|---|---|
| Backend belum jalan | Test BLOCKED | Catat sebagai blocker, kerjakan test case persiapan |
| Perangkat IoT tidak tersedia | Failure simulation tertunda | Gunakan simulasi software |
| Akses server terbatas | Deployment test gagal | Koordinasi dengan Wafian |
| Bug ditemukan mendekati deadline | Rilis tertunda | Prioritas P1 dulu |
| Data uji tidak lengkap | Test tidak realistis | Pakai data dummy yang jelas |

---

## 10. TOOLS QA

| Tool | Fungsi |
|---|---|
| Postman | API testing |
| Excel | Master test case, bug report, log |
| OBS Studio | Rekam failure simulation & demo |
| Lightshot / ShareX | Screenshot + anotasi |
| Chrome DevTools | Inspect UI & network |
| GitHub | Commit bukti & dokumentasi |

---

## 11. DEFINITION OF DONE (DoD)

Sebuah fitur dinyatakan DONE jika:

- [ ] Requirement / AC jelas & sesuai scope
- [ ] Kode/config ter-commit di repository
- [ ] Integrasi sesuai kontrak API/payload/schema
- [ ] Skenario normal diuji & PASS
- [ ] Skenario gagal diuji (timeout, offline, reconnect)
- [ ] Hasil test + screenshot/log tersimpan
- [ ] Dokumentasi diperbarui
- [ ] Tidak ada credential di source code
- [ ] Handover menyebut next action & PIC

---

## 12. PERSETUJUAN

| Peran | Nama | Tanda Tangan |
|---|---|---|
| QA Engineer | Reza Tri | __________ |
| Shift Lead | Dzakwan | __________ |
| Project Coordinator | Damar | __________ |
| Mentor | __________ | __________ |

---

**Akhir Dokumen — Test Plan T-AIMS v1.0**