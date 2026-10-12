# TEMPLATE BUG REPORT — T-AIMS

**Bug ID**        : BUG-[NOMOR] (contoh: BUG-001)  
**Judul**         : [Ringkas & spesifik]  
**Dilaporkan oleh**: Reza Tri  
**Tanggal**       : dd/mm/yyyy  
**Modul**         : [Asset / API / Monitoring / dsb]  
**Severity**      : Critical / High / Medium / Low  
**Priority**      : P1 / P2 / P3  
**Environment**   : Dev / Staging / Production  
**Commit/Build**  : [hash]  

---

## PRASYARAT
[Kondisi awal sebelum bug muncul]

---

## LANGKAH REPRODUKSI

1. [Langkah 1]
2. [Langkah 2]
3. [Langkah 3]
4. Amati hasil

---

## EXPECTED RESULT
[Hasil yang seharusnya muncul]

---

## ACTUAL RESULT
[Hasil aktual yang salah]

---

## FREKUENSI
☐ Selalu  
☐ Sering  
☐ Kadang  
☐ Sekali  

---

## DAMPAK
[Jelaskan dampak ke pengguna/sistem]

---

## BUKTI
- Screenshot : `docs/qa/evidence/screenshots/YYYY-MM-DD_BUG-XXX.png`
- Log        : `docs/qa/evidence/logs/YYYY-MM-DD_BUG-XXX.log`
- Video      : `docs/qa/evidence/videos/YYYY-MM-DD_BUG-XXX.mp4`

---

## STATUS
☐ Open  
☐ In Progress  
☐ Fixed  
☐ Verified  
☐ Closed  
☐ Reopened  

---

## PIC PERBAIKAN
[Nama developer yang fix bug]

---

## VERIFIKASI

**Verified oleh** : Reza Tri  
**Tanggal**       : dd/mm/yyyy  
**Catatan**       : [Catatan hasil verifikasi]  

---

## CONTOH TERISI — BUG-001

**Bug ID**        : BUG-001  
**Judul**         : Status device tetap "Online" padahal ESP32 sudah dimatikan >5 menit  
**Dilaporkan oleh**: Reza Tri  
**Tanggal**       : 27/10/2026  
**Modul**         : Device Monitoring  
**Severity**      : Critical  
**Priority**      : P1  
**Environment**   : Staging  
**Commit/Build**  : abc1234  

**Prasyarat**     : ESP32 dalam kondisi online & terdaftar  

**Langkah Reproduksi** :
1. Pastikan ESP32 dalam kondisi online
2. Matikan ESP32
3. Tunggu 6 menit
4. Refresh dashboard
5. Cek status di API `/api/devices`

**Expected Result** : Status berubah menjadi Offline, Last Seen tidak bertambah  
**Actual Result**   : Status masih Online, Last Seen masih update  
**Frekuensi**       : ☑ Selalu  
**Dampak**          : Monitoring tidak akurat, alert offline tidak terkirim  
**Bukti**           : `screenshots/2026-10-27_BUG-001.png`, `logs/BUG-001_api.json`  
**Status**          : ☑ Open  
**PIC Perbaikan**   : Ananda (Monitoring Engineer)  
**Verified oleh**   : -  
**Catatan**         : Menunggu perbaikan dari Ananda  