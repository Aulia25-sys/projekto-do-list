# SIPINDA – Sistem Informasi Pengaduan Infrastruktur Daerah

Tugas Besar PPW — Kelompok 29

## Deskripsi Proyek
Sistem SIPINDA berfungsi sebagai platform pelaporan kerusakan infrastruktur oleh masyarakat dan memastikan setiap laporan ditangani dengan alur kerja yang jelas:

1. Warga melaporkan pengaduan.
2. Admin memverifikasi dan menugaskan petugas.
3. Petugas menangani laporan di lapangan dan mengunggah bukti.
4. Admin melakukan validasi akhir.
5. Warga dapat melihat status akhir secara transparan.
---

## Identitas Kelompok 29

| No | Nama                 | NIM        | Peran                             |
| -- | -------------------- | ---------- | --------------------------------- |
| 1  | Ramayuda Mahardika   | 2315061126 | Ketua Kelompok, Backend Developer |
| 2  | Arianti Kartika Dewi | 2315061047 | Frontend Admin            |
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

Berisi halaman dashboard pelapor, form pengaduan, filter berdasarkan status, profil pelapor, dan halaman detail tiket.
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

<img width="2291" height="1721" alt="erd-tubes-ppw drawio" src="https://github.com/user-attachments/assets/610183c0-ff47-41b1-8d8b-8506d09de511" />


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

<img width="684" height="614" alt="image" src="https://github.com/user-attachments/assets/2ec66e89-47fc-4ba0-9b88-4aff8e7a3eda" />

Digunakan warga untuk masuk ke sistem.
Berisi input username/email, password, dan tombol menuju register.


## 2. Halaman Register Pelapor

<img width="241" height="332" alt="image" src="https://github.com/user-attachments/assets/d2b40ac8-8572-4f11-a763-5c4917db8612" />

Berisi form pendaftaran akun warga:

* Nama
* Username
* Password
* Alamat
* Kontak

Setelah berhasil, diarahkan ke halaman login.

## 3. Halaman Dashboard Warga

<img width="679" height="608" alt="image" src="https://github.com/user-attachments/assets/4fb820ac-c485-4150-aeff-72f4371c8e55" />


Menampilkan:

* Ringkasan jumlah laporan
* Status laporan
* Menu menuju halaman pengaduan baru
* Profil singkat

## 4. Halaman Buat Pengaduan Baru

<img width="337" height="586" alt="image" src="https://github.com/user-attachments/assets/7ecd3618-8384-496b-921b-2d33f434e9c4" />

Form pengajuan laporan baru:

* Judul laporan
* Deskripsi
* Lokasi
* Foto sebelum pengerjaan
* Tombol submit

## 5. Halaman Riwayat Pengaduan Warga

<img width="320" height="353" alt="image" src="https://github.com/user-attachments/assets/a67182ee-d37d-47f2-94cb-49e72fd342fc" />


Daftar seluruh pengaduan milik warga dalam bentuk tabel.

## 6. Halaman Detail Pengaduan

Berisi:

* Detail laporan
* Status terkini
* Progres pengerjaan
* Tanggapan petugas
* Foto sebelum dan sesudah (jika sudah tersedia)

## 7. Halaman Profil Pelapor

<img width="319" height="367" alt="image" src="https://github.com/user-attachments/assets/d459ef19-8778-447b-953b-57d09f9bfb93" />

Berisi:

* Foto Profil
* Nama
* E-mail
* No.Telp
* NIK
* Alamat
* Indormasi Akun
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

