# TEMPLATE TEST CASE — T-AIMS

**Test Case ID** : TC-[MODUL]-[NOMOR] (contoh: TC-API-001)  
**Hari ke-**     : [1–30]  
**Modul**        : [Asset / API / Monitoring / Heartbeat / Dashboard / Notif / AI]  
**Fitur**        : [Nama fitur yang diuji]  
**Jenis Uji**    : Normal / Negatif / Boundary / Failure  
**Prioritas**    : P1 / P2 / P3  

---

## PRASYARAT
[Kondisi awal sebelum test dijalankan]
Contoh: Backend jalan, Postman siap, ada user login

---

## DATA UJI
| Input | Value |
|---|---|
| [Field 1] | [Value 1] |
| [Field 2] | [Value 2] |

---

## LANGKAH UJI

1. [Langkah 1]
2. [Langkah 2]
3. [Langkah 3]
4. Amati response / hasil

---

## EXPECTED RESULT
[Hasil yang diharapkan]

---

## ACTUAL RESULT
[Hasil aktual saat test dijalankan — diisi setelah test]

---

## STATUS
☐ PASS  
☐ FAIL  
☐ BLOCKED  
☐ SKIP  

---

## SEVERITY (Jika FAIL)
☐ Critical  
☐ High  
☐ Medium  
☐ Low  

---

## BUG ID (Jika FAIL)
[Link ke Bug Report — contoh: BUG-001]

---

## BUKTI
- Screenshot : `docs/qa/evidence/screenshots/YYYY-MM-DD_TC-XXX.png`
- Log        : `docs/qa/evidence/logs/YYYY-MM-DD_TC-XXX.log`
- Video      : `docs/qa/evidence/videos/YYYY-MM-DD_TC-XXX.mp4`

---

## PENGUJI
**Nama**    : Reza Tri  
**Tanggal** : dd/mm/yyyy  
**Commit**  : [hash commit]  

---

## CATATAN
[Catatan tambahan — kendala, asumsi, next action]

---

## CONTOH TERISI — TC-API-001

**Test Case ID** : TC-API-001  
**Hari ke-**     : 8  
**Modul**        : API  
**Fitur**        : GET List Assets  
**Jenis Uji**    : Normal  
**Prioritas**    : P1  

**Prasyarat**    : Backend jalan, Postman siap, ada data aset  

**Data Uji**     : -  

**Langkah Uji**  :
1. Buka Postman
2. Pilih collection T-AIMS API
3. Pilih request "GET List Assets"
4. Klik Send
5. Amati response

**Expected Result** : HTTP 200, response JSON berisi list aset  
**Actual Result**   : HTTP 200, list aset tampil lengkap  
**Status**          : ☑ PASS  
**Severity**        : -  
**Bug ID**          : -  
**Bukti**           : `screenshots/2026-10-18_TC-API-001_pass.png`  
**Penguji**         : Reza Tri  
**Tanggal**         : 18/10/2026  
**Commit**          : abc1234  
**Catatan**         : Berjalan lancar  