# USER MANUAL — T-AIMS
## Teknolab Asset & Infrastructure Monitoring System

**Versi**     : 1.1  
**Tanggal**   : 12 Oktober 2026  
**Penulis**   : Reza Tri (QA & Documentation Engineer)  
**Untuk**     : Pengguna T-AIMS (Administrator & Viewer)  

---

## 1. PENDAHULUAN

### 1.1 Tentang T-AIMS

T-AIMS (Teknolab Asset & Infrastructure Monitoring System) adalah sistem web
untuk:
- Mendata aset & infrastruktur Teknolab
- Memonitor kondisi perangkat secara real-time
- Menyimpan histori gangguan
- Mengirim notifikasi otomatis
- Menghasilkan analisis AI

### 1.2 Target Pengguna

- **Administrator** — full akses (tambah/edit/hapus aset, atur user)
- **Viewer** — hanya lihat dashboard & status

---

## 2. PERSYARATAN SISTEM

### 2.1 Perangkat

- Laptop / PC dengan browser modern
- Koneksi internet (untuk akses server T-AIMS)

### 2.2 Browser yang Didukung

- Google Chrome (versi terbaru)
- Mozilla Firefox (versi terbaru)
- Microsoft Edge (versi terbaru)

---

## 3. CARA MASUK (LOGIN)

### Langkah:

1. Buka browser
2. Ketik URL T-AIMS: `http://[URL-T-AIMS]`
3. Masukkan **username** dan **password** yang diberikan Administrator
4. Klik tombol **Login**

### Jika Lupa Password:

1. Klik **Lupa Password?** di halaman login
2. Masukkan email terdaftar
3. Cek email untuk link reset password

---

## 4. HALAMAN DASHBOARD

Setelah login, Anda akan melihat Dashboard dengan informasi:

| Bagian | Isi |
|---|---|
| Total Device | Jumlah semua aset |
| Online | Perangkat aktif |
| Offline | Perangkat mati |
| Warning | Perangkat bermasalah |
| Unknown | Perangkat belum terdeteksi |
| Grafik | Uptime / downtime |
| Lokasi | Peta / floorplan |

### Cara Membaca Status

| Warna | Status | Arti |
|---|---|---|
| 🟢 Hijau | Online | Perangkat aktif |
| 🔴 Merah | Offline | Perangkat mati / tidak terdeteksi |
| 🟡 Kuning | Warning | Perangkat bermasalah |
| ⚪ Abu | Unknown | Belum terdeteksi |

---

## 5. HALAMAN ASSET MANAGEMENT

### 5.1 Lihat Daftar Aset

1. Klik menu **Assets** di sidebar
2. Daftar semua aset akan tampil
3. Filter berdasarkan kategori / lokasi

### 5.2 Tambah Aset Baru (Administrator)

1. Klik tombol **+ Tambah Aset**
2. Isi form:
   - Asset Code (wajib, unik)
   - Asset Name
   - Category
   - IP Address
   - Location
   - PIC
   - Monitoring Method
3. Klik **Simpan**

### 5.3 Edit Aset

1. Klik ikon ✏️ di baris aset
2. Ubah data
3. Klik **Simpan**

### 5.4 Hapus Aset

1. Klik ikon 🗑️ di baris aset
2. Konfirmasi **Ya, Hapus**

---

## 6. HALAMAN DEVICE DETAIL

Klik salah satu aset untuk melihat detail:

- Informasi aset lengkap
- Status terkini
- Last Seen (terakhir aktif)
- Response time
- History monitoring
- Lokasi

---

## 7. HALAMAN MONITORING HISTORY

### Cara Lihat History:

1. Klik menu **History** di sidebar
2. Pilih device
3. Pilih rentang waktu
4. Lihat timeline perubahan status

---

## 8. HALAMAN LOCATION

### Cara Lihat Lokasi:

1. Klik menu **Location**
2. Peta / floorplan tampil
3. Klik device untuk lihat detail

---

## 9. NOTIFIKASI

### Notifikasi Otomatis Dikirim:

- **Offline Alert** — saat device mati
- **Recovery Alert** — saat device kembali online

### Kanal Notifikasi:

- Telegram
- Email
- (sesuai konfigurasi tim)

---

## 10. LAPORAN (REPORTING)

### Cara Export Laporan:

1. Klik menu **Reports**
2. Pilih periode
3. Pilih format: PDF / Excel
4. Klik **Export**

---

## 11. AI INFRASTRUCTURE ASSISTANT

Fitur AI memberikan:
- Analisis kondisi infrastruktur
- Rekomendasi tindakan
- Deteksi anomali

⚠️ **Catatan:** Rekomendasi AI bersifat saran, bukan fakta. Selalu verifikasi dengan data.

---

## 12. TROUBLESHOOTING

| Masalah | Solusi |
|---|---|
| Tidak bisa login | Cek username/password, hubungi Admin |
| Dashboard tidak update | Refresh browser, cek koneksi |
| Data tidak tampil | Cek koneksi backend, hubungi tim IT |
| Notifikasi tidak masuk | Cek konfigurasi kanal notifikasi |

---

## 13. KONTAK BANTUAN

| Peran | Nama | Kontak |
|---|---|---|
| QA | Reza Tri | rezatriwardana7@gmail.com / 0851-3681-1164 |
| Backend | Ahmad Reza Fahmi | rzafahmi351@gmail.com / 0857-0724-8435 |
| DevOps | Wafian | wafianzaidan@gmail.com / 0858-0421-4958 |
| PIC Teknolab | Elga Aris Prastyo | admin@office-teknolab.biz.id / (0342) 8178833 / WhatsApp: 0815-1588-9939 |

---

## 14. RIWAYAT VERSI

| Versi | Tanggal | Perubahan |
|---|---|---|
| 1.0 | 12/10/2026 | Draft awal |
| 1.1 | 12/10/2026 | Update kontak PIC Teknolab |

---

**Akhir Dokumen — User Manual T-AIMS v1.1**