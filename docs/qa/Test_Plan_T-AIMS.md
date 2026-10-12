# TEST PLAN — T-AIMS
## Teknolab Asset & Infrastructure Monitoring System

**Versi**     : 1.0
**Tanggal**   : 12 Oktober 2026
**Penulis**   : Reza Tri (QA, Testing & Documentation Engineer)
**Project**   : T-AIMS — PKL 30 Hari PT Teknolab Caraka Internasional
**Status**    : Final

---

## 1. TUJUAN

Dokumen ini menjadi acuan pengujian T-AIMS selama 30 hari PKL.
Memastikan setiap fitur diuji sebelum dinyatakan DONE.

---

## 2. SCOPE PENGUJIAN

### 2.1 Fitur Diuji (12 Fitur Minimum)

| No | Fitur | Prioritas |
|----|-------|-----------|
| 1  | Asset Management | P1 |
| 2  | Device Monitoring | P1 |
| 3  | Last Seen | P1 |
| 4  | Response Time | P2 |
| 5  | Monitoring History | P1 |
| 6  | Uptime / Downtime | P2 |
| 7  | Dashboard | P1 |
| 8  | Location | P2 |
| 9  | Notification | P1 |
| 10 | User Management | P1 |
| 11 | Reporting | P2 |
| 12 | AI Automation | P3 |

### 2.2 Out of Scope
- Load testing skala besar
- Penetration testing profesional
- Mobile native app

---

## 3. JENIS PENGUJIAN

| Jenis | Deskripsi | Kapan |
|-------|-----------|-------|
| Smoke Test | Uji cepat fitur inti | Hari 10, 20 |
| Functional Test | Uji sesuai AC | Setiap hari |
| Regression Test | Uji ulang setelah fix | Hari 16, 28 |
| Negative Test | Uji input tidak valid | Setiap fitur |
| Boundary Test | Uji batas nilai | Setiap fitur |
| Failure Simulation | Skenario gangguan | Hari 27 |
| Acceptance Test | Uji akhir MVP | Hari 20 |
| Security Test | Uji akses & input | Hari 26 |

---

## 4. ENTRY & EXIT CRITERIA

### 4.1 Entry Criteria
- Fitur selesai dikembangkan
- Kode ter-commit di repository
- Environment testing siap
- Test case sudah dibuat
- Data uji tersedia

### 4.2 Exit Criteria
- Semua test case P1 dijalankan
- Bug sudah dilaporkan dengan Bug ID
- Bukti tersimpan (screenshot/log/video)
- Test report diperbarui
- Fitur layak DONE

---

## 5. LINGKUNGAN PENGUJIAN

| Item | Detail |
|------|--------|
| OS | Windows 10/11 |
| Browser | Chrome, Firefox |
| API Tool | Postman |
| Spreadsheet | Microsoft Excel |
| Version Control | Git + GitHub |
| Environment | Dev → Staging → Production |

---

## 6. JADWAL 30 HARI

| Hari | Fokus | Test Type |
|------|-------|-----------|
| 1 | Setup QA & Docs | — |
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
| 20 | MVP RELEASE | Acceptance Test |
| 21 | Notification Offline | Failure |
| 22 | Recovery Alert | Failure |
| 23 | Map/Location | Functional |
| 24 | AI Automation | Functional |
| 25 | Reporting | Functional |
| 26 | Security Test | Security |
| 27 | FAILURE SIMULATION | Failure |
| 28 | Bug Fixing | Regression |
| 29 | Documentation | Review |
| 30 | Final Demo | Acceptance |

---

## 7. TIM & TANGGUNG JAWAB

| Nama | Peran | Hubungan dengan QA |
|------|-------|---------------------|
| Reza Tri | QA Engineer | Test plan, test case, eksekusi, bug, dokumentasi |
| Dzakwan | Shift Lead | Approval release, prioritas bug |
| Ahmad Reza Fahmi | Backend Dev | Fix bug backend, API contract |
| Dika Yoga | Frontend Dev | Fix bug UI |
| Wafian | DevOps | Environment testing |
| Ananda | Monitoring | Fix bug monitoring |
| Ilvina | IoT | Fix bug firmware |
| Arik | Automation | Fix bug notification |
| Damar | Analyst | Acceptance criteria |
| Faida | Database | Data uji |
| Ahmad Aziz | UI/UX | Visual consistency |

---

## 8. DELIVERABLE QA

1. Test Plan
2. Test Case (Excel + template)
3. Bug Report (Excel + template)
4. Test Report Harian
5. Daily Handover
6. User Manual
7. Technical Documentation
8. Video Demo
9. Final Evidence

---

## 9. RISIKO & MITIGASI

| Risiko | Mitigasi |
|--------|----------|
| Backend belum jalan | Catat BLOCKED, kerjakan persiapan |
| Perangkat IoT tidak tersedia | Gunakan simulasi software |
| Akses server terbatas | Koordinasi Wafian |
| Bug mendekati deadline | Prioritas P1 dulu |

---

## 10. TOOLS QA

| Tool | Fungsi |
|------|--------|
| Postman | API testing |
| Excel | Test case, bug report, log |
| OBS Studio | Rekam failure simulation |
| Lightshot | Screenshot bug |
| Chrome DevTools | Inspect UI & network |
| GitHub | Commit bukti |

---

## 11. DEFINITION OF DONE

Fitur dinyatakan DONE jika:
- Requirement/AC jelas
- Kode ter-commit di repository
- Integrasi sesuai kontrak API
- Skenario normal PASS
- Skenario gagal diuji
- Bukti tersimpan
- Dokumentasi diperbarui
- Tidak ada credential di source code
- Handover menyebut next action

---

## 12. PERSETUJUAN

| Peran | Nama | Tanda Tangan |
|-------|------|--------------|
| QA Engineer | Reza Tri | _______ |
| Shift Lead | Dzakwan | _______ |
| Coordinator | Damar | _______ |
| Mentor | _______ | _______ |

---

**Akhir Dokumen — Test Plan T-AIMS v1.0**