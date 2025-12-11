# Sistem Pengaduan Warga Terintegrasi

Tugas Besar PPW — Kelompok 29

Dokumen ini merupakan README resmi dari proyek Sistem Pengaduan Warga Terintegrasi. Sistem ini dirancang agar warga dapat melapor dengan mudah, petugas dapat menindaklanjuti secara terarah, dan admin dapat mengelola seluruh alur dengan lebih transparan.

---

## Identitas Kelompok 29

| No | Nama                 | NIM        | Peran                             |
| -- | -------------------- | ---------- | --------------------------------- |
| 1  | Ramayuda Mahardika   | 2315061126 | Ketua Kelompok, Backend Developer |
| 2  | Arianti Kartika Dewi | 2315061047 | Admin Portal Developer            |
| 3  | Aulia Rahmi Shakira  | 2315061104 | Frontend Pelapor                  |
| 4  | Recky Valerian       | 2315061057 | Frontend Petugas                  |

---

# Struktur Project

Pada folder **kelompok_29**, terdapat struktur utama:

```
src/
│── backend/        → dikembangkan oleh Ramayuda
│── frontend/
       │── pelapor/ → dikembangkan oleh Aulia
       │── admin/   → dikembangkan oleh Arianti
       │── petugas/ → dikembangkan oleh Recky
```

Penjelasan:

## Backend (Developer: Ramayuda)

Berisi:

* API autentikasi (warga, admin, petugas)
* API pengaduan
* API assign tugas
* API bukti/progres pengerjaan
* Validasi input, autentikasi, manajemen token
* CRUD untuk warga, petugas, dan laporan

## Frontend Pelapor (Developer: Aulia)

Berisi seluruh halaman warga/pelapor menggunakan:

* HTML
* CSS3 (Native)
* Bootstrap
* TailwindCSS
* JavaScript manual

## Frontend Admin (Developer: Arianti)

Berisi halaman dashboard admin, pengelolaan petugas, serta manajemen pengaduan.

## Frontend Petugas (Developer: Recky)

Berisi tampilan daftar tugas petugas, form progres pengerjaan, dan halaman detail tugas.

---

# Alur Kerja Pengembangan

Untuk menjaga ketertiban dan kolaborasi:

1. Ketua kelompok melakukan fork atau membuat repository.
2. Ketua mengundang seluruh anggota.
3. Setiap anggota membuat branch sesuai peran:

   * `backend-ramayuda`
   * `frontend-pelapor-aulia`
   * `frontend-admin-arianti`
   * `frontend-petugas-recky`
4. Semua pekerjaan dilakukan pada branch masing-masing.
5. Ketika fitur selesai:

   * commit
   * push
   * pull request
6. Pull request direview sebelum di-merge ke branch utama.

Dengan cara ini, pekerjaan tiap anggota tidak saling bertabrakan.

---

# Penjelasan ERD Sistem

ERD menggambarkan hubungan antar entitas utama: warga, pengaduan, petugas, dan tanggapan/progres.

## 1. Warga

* Penyedia laporan/pengaduan.
* Satu warga dapat membuat banyak pengaduan.
* Menyimpan data identitas dan akun pelapor.

## 2. Pengaduan

* Laporan infrastruktur yang diajukan warga.
* Memiliki status: menunggu, diproses, ditugaskan, selesai.
* Terhubung ke warga (pembuat laporan).
* Dapat berisi foto sebelum kejadian.
* Dapat menghasilkan banyak progres dari petugas.

## 3. Petugas

* Penerima tugas dari admin.
* Satu petugas dapat menangani banyak pengaduan.
* Menambahkan progres/pengerjaan dan bukti penyelesaian.

## 4. Tugas / Penugasan

* Relasi antara petugas dan pengaduan.
* Dibuat oleh admin ketika laporan diverifikasi.
* Menandai bahwa satu petugas bertanggung jawab terhadap satu pengaduan pada periode tertentu.

## 5. Progres / Bukti Penyelesaian

* Berisi:

  * Foto setelah pengerjaan
  * Catatan pengerjaan
  * Tanggal update
* Dipakai admin untuk validasi penyelesaian.

Keseluruhan ERD mencerminkan alur:
warga membuat pengaduan → admin verifikasi → admin menugaskan petugas → petugas mengerjakan → admin validasi → status menjadi selesai.

---

# Penjelasan Halaman Frontend

Berikut halaman yang dibuat, sesuai pembagian tim.

---

# Bagian A — Frontend Pelapor (Developer: Aulia)

## 1. Halaman Login Pelapor

Digunakan warga untuk masuk ke sistem.
Berisi input username/email, password, dan tombol menuju register.

(Gambar halaman ditempatkan di bawah header ini dalam README final Anda)

## 2. Halaman Register Pelapor

Berisi form pendaftaran akun warga:

* Nama
* Username
* Password
* Alamat
* Kontak

Setelah berhasil, diarahkan ke halaman login.

## 3. Halaman Dashboard Warga

Menampilkan:

* Ringkasan jumlah laporan
* Status laporan
* Menu menuju halaman pengaduan baru
* Profil singkat

## 4. Halaman Buat Pengaduan Baru

Form pengajuan laporan baru:

* Judul laporan
* Deskripsi
* Lokasi
* Foto sebelum pengerjaan
* Tombol submit

## 5. Halaman Riwayat Pengaduan Warga

Daftar seluruh pengaduan milik warga dalam bentuk tabel.

## 6. Halaman Detail Pengaduan

Berisi:

* Detail laporan
* Status terkini
* Progres pengerjaan
* Tanggapan petugas
* Foto sebelum dan sesudah (jika sudah tersedia)

---

# Bagian B — Frontend Admin (Developer: Arianti)

## 1. Halaman Login Admin

Autentikasi admin ke dalam sistem.

## 2. Dashboard Admin

Berisi:

* Statistik pengaduan
* Jumlah laporan baru, diproses, dan selesai
* Aktivitas terbaru petugas

## 3. Halaman Verifikasi Pengaduan

Admin dapat:

* Melihat detail laporan
* Menyetujui verifikasi
* Menugaskan petugas

## 4. Halaman Penugasan Petugas

Admin memilih satu petugas untuk menangani pengaduan.

## 5. Halaman Validasi Penyelesaian

Admin menilai bukti pengerjaan:

* Dapat menyetujui sebagai "Selesai"
* Dapat menolak dan meminta revisi

## 6. Pengelolaan Data Petugas

Admin dapat:

* Menambah petugas
* Mengedit data petugas
* Menghapus petugas
* Melihat daftar petugas aktif dan tugas mereka

---

# Bagian C — Frontend Petugas (Developer: Recky)

## 1. Halaman Login Petugas

Petugas masuk menggunakan akun yang dibuat admin.

## 2. Halaman Daftar Tugas

Berisi daftar pengaduan yang ditugaskan kepada petugas:

* Tugas aktif
* Tugas selesai

## 3. Halaman Detail Tugas

Berisi:

* Detail pengaduan
* Lokasi
* Status pekerjaan
* Tombol mulai pengerjaan

## 4. Halaman Unggah Bukti Penyelesaian

Berisi:

* Upload foto sesudah pengerjaan
* Catatan pengerjaan
* Tombol kirim ke admin untuk validasi

---

# Tujuan Pengembangan Sistem

Sistem ini dibuat untuk:

* Mempermudah pelaporan dari warga
* Memperjelas alur penanganan pengaduan
* Menyediakan dokumentasi digital yang konsisten
* Mengatur pendistribusian tugas petugas secara terstruktur
* Memudahkan admin dalam memantau dan mengevaluasi laporan

---

Jika Anda ingin menambahkan:
– Gambar setiap halaman
– Penjelasan tabel database berdasarkan ERD
– Contoh endpoint backend

Cukup beri tahu dan akan saya lengkapi.
