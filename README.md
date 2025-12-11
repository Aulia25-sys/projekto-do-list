# 🏛️ SIPINDA – Sistem Informasi Pengaduan Infrastruktur Daerah

SIPINDA adalah sistem terpadu untuk pelaporan, manajemen, dan penyelesaian pengaduan infrastruktur publik di tingkat daerah. Sistem ini dirancang untuk menciptakan alur kerja digital yang transparan dan efisien antara masyarakat, administrator, dan petugas lapangan. Setiap pengaduan dapat dilacak secara real-time dari proses pengajuan hingga validasi penyelesaian, sehingga mendorong akuntabilitas pemerintah daerah.

---

## 📝 Deskripsi Proyek
Sistem SIPINDA berfungsi sebagai platform pelaporan kerusakan infrastruktur oleh masyarakat dan memastikan setiap laporan ditangani dengan alur kerja yang jelas:

1. Warga melaporkan pengaduan.
2. Admin memverifikasi dan menugaskan petugas.
3. Petugas menangani laporan di lapangan dan mengunggah bukti.
4. Admin melakukan validasi akhir.
5. Warga dapat melihat status akhir secara transparan.

---

# 🏗️ Arsitektur Sistem (Multi-Portal)

SIPINDA terdiri dari tiga portal yang saling terintegrasi, masing-masing memiliki peran dan antarmuka penggunaan yang berbeda.

---

## 👨‍👩‍👦 1. Portal Warga (Pelapor)

Portal untuk masyarakat yang digunakan untuk mengajukan dan memantau pengaduan.

### **Fungsionalitas**
| Fitur | File | Deskripsi |
|------|------|-----------|
| Autentikasi & Registrasi | `CitizenLogin.tsx`, `Register.tsx` | Login dan pendaftaran akun warga. |
| Pengajuan Pengaduan | `NewComplaintForm.tsx` | Formulir pelaporan dengan upload foto dan penentuan lokasi. |
| Dashboard Warga | `CitizenDashboard.tsx` | Ringkasan status pengaduan pengguna. |
| Riwayat & Pelacakan | `ComplaintHistory.tsx`, `ComplaintDetail.tsx` | Melihat riwayat pengaduan dan linimasa progres. |
| Manajemen Profil | `EditProfile.tsx` | Edit data diri warga (Nama, Email, NIK, Alamat). |

---

## 🛠️ 2. Portal Admin

Portal pusat kontrol untuk memverifikasi pengaduan, menugaskan petugas, dan melakukan validasi akhir.

### **Fungsionalitas**
| Fitur | File | Deskripsi |
|------|------|-----------|
| Dashboard Kontrol | `AdminDashboard.tsx` | Statistik real-time pengaduan. |
| Manajemen Tiket | `TicketManagement.tsx` | Daftar pengaduan lengkap dengan pencarian & filter. |
| Verifikasi & Penugasan | `TicketDetail.tsx`, `OfficerSelectionModal.tsx` | Verifikasi laporan dan penugasan ke petugas. |
| Validasi Akhir | `CompletionValidation.tsx` | Meninjau bukti penyelesaian dari petugas. |
| Manajemen Petugas | `OfficerManagement.tsx`, `CreateOfficer.tsx` | Mengelola data petugas lapangan. |

---

## 👷 3. Portal Petugas Lapangan

Portal untuk petugas yang mengerjakan laporan di lapangan dan memperbarui status pengerjaan.

### **Fungsionalitas**
| Fitur | File | Deskripsi |
|------|------|-----------|
| Autentikasi Petugas | `OfficerLogin.tsx` | Login khusus untuk petugas. |
| Daftar Tugas | `TaskList.tsx` | Daftar tugas aktif dan selesai. |
| Detail Tugas | `TaskDetail.tsx` | Detail pengaduan + update status pengerjaan. |
| Pelaporan Penyelesaian | `UploadProof.tsx` | Upload foto bukti pengerjaan. |
| Manajemen Profil | `EditProfile.tsx` | Edit data pegawai/ petugas. |

---

# ⚙️ Teknologi yang Digunakan

- **Front-end:** React + TypeScript (TSX)
- **Styling:** Tailwind CSS
- **UI Components:** lucide-react (ikon), sonner (toast notification)
- **Data Mock:** `mockData`, `users`, `officersData` (akan diganti dengan API backend pada tahap selanjutnya)

---

# 🚀 Instalasi & Setup Proyek

## **Prasyarat**
- Node.js (versi terbaru)
- npm atau yarn

---

## **Langkah Instalasi**

### 1. Clone Repositori
```bash
git clone [URL_REPOSITORI_ANDA]
cd SIPINDA-Project
