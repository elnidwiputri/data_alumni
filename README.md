# 📚 Sistem Data Alumni Mahasiswa Fakultas Sainstek

## 1. Nama Kelompok & Anggota
- **Elni Dwi Putri** (701230196)  
- **Zalma Nabila Putri** (701230194)  
- **Hayatun Nufus** (701230096)  

---

## 2. Deskripsi Singkat Aplikasi
Aplikasi web-based untuk mengelola data alumni mahasiswa Fakultas Sains dan Teknologi. Sistem ini memiliki dua role akses:
- **Admin**: Dapat mengelola data alumni (Create, Read, Update, Delete) dan melihat.
- **Mahasiswa**: Dapat melihat profil pribadi mereka secara digital.

**Fitur Utama:**
- ✅ Dashboard admin dengan statistik lengkap
- ✅ Manajemen data alumni (CRUD)
- ✅ Pencarian dan filter data
- ✅ Portal mahasiswa untuk melihat profil
- ✅ Autentikasi berbasis role (Admin & Mahasiswa)

---

## 3. Tujuan Sistem / Permasalahan yang Diselesaikan
**Permasalahan:**
- Pengelolaan data alumni masih manual menggunakan dokumen fisik
- Kesulitan dalam mencari dan mengakses data alumni
- Tidak ada sistem terintegrasi untuk tracking alumni

**Solusi yang Ditawarkan:**
- ✅ Digitalisasi data alumni dalam database cloud
- ✅ Sistem pencarian dan filter yang cepat
- ✅ Akses data real-time dari mana saja
- ✅ Portal self-service untuk mahasiswa melihat profil mereka

---

## 4. Teknologi yang Digunakan

| Kategori | Teknologi |
|----------|-----------|
| **Frontend** | HTML5, CSS3, JavaScript (ES6+) |
| **CSS Framework** | Tailwind CSS (via CDN) |
| **Icons** | Font Awesome 6.4.0 |
| **Database** | Firebase Firestore (NoSQL) |
| **Authentication** | Firebase Authentication (Collection-based) |
| **Hosting** | Firebase Hosting |
| **Version Control** | Git & GitHub |
| **Code Editor** | Visual Studio Code |

**Alasan Pemilihan Teknologi:**
- **Firebase Firestore**: Real-time database, scalable, dan mudah diintegrasikan
- **Tailwind CSS**: Rapid UI development dengan utility-first approach
- **Vanilla JavaScript**: Performa optimal tanpa dependency library besar

---

## 5. Cara Menjalankan Aplikasi

### 5.1 Prerequisites (Prasyarat)
Pastikan sudah terinstall:
- ✅ Web Browser modern (Chrome, Firefox, Edge)
- ✅ Text Editor (VS Code recommended)
- ✅ Git (opsional, untuk clone)
- ✅ Akun Firebase (gratis)

### 5.2 Instalasi

#### Opsi 1: Clone dari GitHub
```bash
# Clone repository
git clone https://github.com/username/data-alumni.git

# Masuk ke folder project
cd data-alumni
```

#### Opsi 2: Download ZIP
1. Download project dari GitHub
2. Extract ke folder pilihan Anda

### 5.3 Konfigurasi Firebase

#### A. Setup Firebase Project
1. Buka [Firebase Console](https://console.firebase.google.com/)
2. Klik **"Add project"** / **"Tambah project"**
3. Beri nama: `data-alumni`
4. Ikuti wizard hingga selesai

#### B. Aktifkan Firestore Database
1. Di sidebar, klik **"Firestore Database"**
2. Klik **"Create database"**
3. Pilih **"Start in production mode"**
4. Pilih lokasi: **asia-southeast2 (Jakarta)**
5. Klik **"Enable"**

#### C. Setup Firestore Rules
1. Buka tab **"Rules"**
2. Ganti dengan rules berikut:
```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /users/{document=**} {
      allow read, write: if true;
    }
    match /mahasiswa/{document=**} {
      allow read, write: if true;
    }
    match /login_mahasiswa/{document=**} {
      allow read, write: if true;
    }
  }
}
```
3. Klik **"Publish"**

#### D. Dapatkan Config Firebase
1. Klik ⚙️ **Settings** → **Project settings**
2. Scroll ke **"Your apps"**
3. Klik icon **Web** `</>`
4. Daftarkan app dengan nama: `web-app`
5. **Copy konfigurasi** yang muncul

#### E. Update Konfigurasi di Project
Buka file berikut dan ganti `firebaseConfig`:
- `login-admin.html`
- `login-mahasiswa.html`
- `admin-dashboard.html`
- `mahasiswa-dashboard.html`
- `tambah.html`
- `edit.html`

```javascript
const firebaseConfig = {
  apiKey: "YOUR_API_KEY",
  authDomain: "data-alumni-.firebaseapp.com",
  projectId: "data-alumni-,
  storageBucket: "data-alumni.appspot.com",
  messagingSenderId: "YOUR_SENDER_ID",
  appId: "YOUR_APP_ID",
  measurementId: "YOUR_MEASUREMENT_ID"
};
```

#### F. Setup Data Awal

**1. Collection: `users` (untuk Admin)**
```javascript
{
  email: "admin@gmail.com",
  nama: "admin",
  role: "admin"
}
```

**2. Collection: `login_mahasiswa`**
```javascript
{
  nim: "701230196",
  password: "701230196",
  role: "mahasiswa",
  username: "Elni Dwi Putri",
  uid: "user001"
}
```

**3. Collection: `mahasiswa`**
```javascript
{
  nim: "701230196",
  nama: "Elni Dwi Putri",
  email: "elni@example.com",
  tempatLahir: "Jambi",
  tanggalLahir: "2002-01-15",
  jenisKelamin: "Perempuan",
  jurusan: "Teknik Informatika",
  noHp: "081234567890",
  alamat: "Jl. Example No. 123, Jambi",
  tahunKeluar: "2024",
  pekerjaan: "Software Engineer",
  judulSkripsi: "Sistem Informasi Data Alumni Berbasis Web",
  pengujiSkripsi: "Dr. John Doe, M.Kom",
  createdAt: [Timestamp],
  updatedAt: [Timestamp]
}
```

### 5.4 Menjalankan / Run Project

#### Metode 1: Live Server (Recommended)
1. Install extension **"Live Server"** di VS Code
2. Klik kanan pada `index.html`
3. Pilih **"Open with Live Server"**
4. Browser otomatis terbuka di `http://localhost:5500`

#### Metode 2: Direct Browser
1. Buka file `index.html` dengan double-click
2. Atau drag & drop ke browser

#### Metode 3: Python HTTP Server
```bash
# Python 3
python -m http.server 8000

# Akses: http://localhost:8000
```

#### Metode 4: Node.js HTTP Server
```bash
# Install
npm install -g http-server

# Run
http-server

# Akses: http://localhost:8080
```

---

## 6. Akun Demo (Login)

### 🔐 Akun Admin
| Field | Value |
|-------|-------|
| **Email** | admin@gmail.com |
| **Password** | admin |
| **Role** | Admin |

**Akses:**
- Dashboard 
- Kelola semua data mahasiswa (CRUD)
- Pencarian dan filter data


### 👨‍🎓 Akun Mahasiswa

| NIM | Password | Nama |
|-----|----------|------|
| 701230196 | 701230196 | Elni Dwi Putri |
| 701230194 | 701230194 | Zalma Nabila Putri |
| 701230096 | 701230096 | Hayatun Nufus |

**Akses:**
- Lihat profil pribadi
- Informasi akademik lengkap

---

## 7. Link Deployment / Demo

### 🌐 Live Demo
- **URL Production**: [https://data-alumni-b0381.web.app](https://data-alumni-b0381.web.app)  
- **URL Alternative**: [https://data-alumni-b0381.firebaseapp.com](https://data-alumni-b0381.firebaseapp.com)

### 📹 Video Demo
- **YouTube**: [Link Video Demo](https://youtube.com/watch?v=xxxxx) *(upcoming)*
- **Google Drive**: [Link Video Demo](https://drive.google.com/xxxxx) *(upcoming)*

### 📦 Repository
- **GitHub**: [https://github.com/username/data-alumni](https://github.com/username/data-alumni)

---

## 8. Screenshot Aplikasi

### 📱 Halaman Login
![Login Page](./screenshots/login.png)

### 👨‍💼 Dashboard Admin
![Dashboard Admin](./screenshots/dashboard-admin.png)

### ➕ Form Tambah Data
![Form Tambah](./screenshots/form-tambah.png)

### ✏️ Form Edit Data
![Form Edit](./screenshots/form-edit.png)

### 👨‍🎓 Dashboard Mahasiswa
![Dashboard Mahasiswa](./screenshots/dashboard-mahasiswa.png)

**Catatan**: Silakan tambahkan screenshot asli ke folder `screenshots/` di project Anda.

---

## 9. Struktur Project

```
📦 data-alumni/
├── 📄 index.html                  # Landing page (pilih role)
├── 📄 login-admin.html            # Halaman login admin
├── 📄 login-mahasiswa.html        # Halaman login mahasiswa
├── 📄 admin-dashboard.html        # Dashboard admin (tabel data)
├── 📄 mahasiswa-dashboard.html    # Dashboard mahasiswa (profil)
├── 📄 tambah.html                 # Form tambah data mahasiswa
├── 📄 edit.html                   # Form edit data mahasiswa
├── 📄 logout.admin.html           # Script logout
├── 📄 README.md                   # Dokumentasi project
├── 📁 screenshots/                # Folder screenshot
│   ├── login.png
│   ├── dashboard-admin.png
│   └── ...
└── 📁 .git/                       # Git repository (jika pakai git)
```

---

## 10. Fitur Aplikasi

### ✨ Fitur Admin
- ✅ Login dengan email & password
- ✅ Dashboard dengan 3 statistik cards:
  - Total Mahasiswa
  - Alumni Bekerja
  - Lulusan Tahun Ini
- ✅ Tabel data mahasiswa lengkap dengan:
  - 13 kolom informasi
  - Sticky header saat scroll
  - Responsive design
- ✅ **CRUD Operations**:
  - Create: Tambah data mahasiswa baru
  - Read: Lihat semua data
  - Update: Edit data mahasiswa
  - Delete: Hapus data dengan konfirmasi
- ✅ Pencarian real-time (NIM, Nama, Email, Jurusan)
- ✅ Refresh data manual
- ✅ Logout dengan konfirmasi

### 👨‍🎓 Fitur Mahasiswa
- ✅ Login dengan NIM & password
- ✅ Dashboard profil pribadi
- ✅ Informasi lengkap:
  - Data pribadi (NIM, Nama, TTL, Gender)
  - Kontak (Email, No HP, Alamat)
  - Akademik (Jurusan, Tahun Keluar)
  - Skripsi (Judul & Penguji)
  - Pekerjaan saat ini
- ✅ Logout

---

## 11. Catatan Tambahan

### ⚠️ Keterbatasan Sistem
- Fitur export data (Excel/PDF) belum tersedia
- Upload foto profil mahasiswa belum ada
- Email notification belum diimplementasikan
- Reset password harus manual via admin
- Tidak ada fitur statistik grafik/chart

### 📝 Petunjuk Penggunaan Khusus
- ✅ **Koneksi Internet Wajib**: Karena menggunakan Firebase cloud database
- ✅ **Browser Modern**: Chrome 90+, Firefox 88+, Edge 90+
- ✅ **JavaScript Harus Aktif**: Aplikasi tidak berjalan jika JS dimatikan
- ✅ **Clear Cache**: Jika ada masalah, coba clear browser cache

### 🔒 Keamanan
⚠️ **PERHATIAN**: 
- Rules Firestore saat ini terbuka untuk development
- Untuk production, implementasikan authentication yang lebih ketat
- Jangan expose Firebase config di repository public
- Gunakan environment variables untuk production

### 🐛 Troubleshooting

#### Problem: "Permission Denied"
**Solusi**: 
- Periksa Firestore Rules sudah benar
- Pastikan sudah di-publish
- Tunggu 1-2 menit untuk propagasi

#### Problem: "Data tidak muncul"
**Solusi**:
- Buka Console Browser (F12)
- Periksa tab Console untuk error
- Pastikan collection name benar: `mahasiswa`, `users`, `login_mahasiswa`

#### Problem: "Login gagal"
**Solusi**:
- Cek data di Firestore collection
- Pastikan email/NIM dan password sesuai
- Case-sensitive untuk semua field

---

## 12. Roadmap / Pengembangan Selanjutnya

### 🚀 Phase 2 (Future Updates)
- [ ] Export data ke Excel
- [ ] Export data ke PDF
- [ ] Upload foto profil mahasiswa
- [ ] Grafik statistik alumni (Chart.js)
- [ ] Email notification
- [ ] Forgot password feature
- [ ] Filter data berdasarkan jurusan & tahun
- [ ] Pagination untuk tabel
- [ ] Dark mode

### 🎯 Phase 3 (Advanced Features)
- [ ] Multi-role: Super Admin, Admin, Mahasiswa
- [ ] Log activity / audit trail
- [ ] Backup & restore database
- [ ] API endpoint untuk integrasi
- [ ] Mobile app (React Native)

---

## 13. Keterangan Tugas

### 📚 Informasi Akademik
- **Mata Kuliah**: Rekayasa Perangkat Lunak
- **Kode MK**: [Kode Mata Kuliah]
- **Semester**: [Semester/Tahun Akademik]
- **Dosen Pengampu**: [Nama Dosen]
- **Institusi**: Fakultas Sains dan Teknologi

### 📅 Timeline Pengerjaan
- **Mulai**: [Tanggal Mulai]
- **Selesai**: [Tanggal Selesai]
- **Durasi**: [X minggu/bulan]

### 📊 Pembagian Tugas

| Anggota | Tugas Utama |
|---------|-------------|
| **Elni Dwi Putri** | Frontend (Admin Dashboard, Form CRUD) |
| **Zalma Nabila Putri** | Backend (Firebase Integration, Auth) |
| **Hayatun Nufus** | UI/UX Design, Testing, Documentation |

---

## 14. Lisensi & Kontak

### 📜 Lisensi
Project ini dibuat untuk keperluan akademik dan dapat digunakan untuk pembelajaran.

### 📧 Kontak Tim
- **Email Kelompok**: kelompok@example.com
- **GitHub**: [@username](https://github.com/username)

---

## 15. Referensi

### 📖 Dokumentasi Teknis
- [Firebase Documentation](https://firebase.google.com/docs)
- [Tailwind CSS Documentation](https://tailwindcss.com/docs)
- [MDN Web Docs](https://developer.mozilla.org/)

### 🎓 Sumber Belajar
- [Firebase Firestore Tutorial](https://firebase.google.com/docs/firestore)
- [JavaScript ES6+ Features](https://es6-features.org/)
- [Responsive Web Design](https://web.dev/responsive-web-design-basics/)

---

**⭐ Terima kasih telah menggunakan Sistem Data Alumni Mahasiswa!**

---


**© 2024 Kelompok [Kelompok 3] - Fakultas Sains dan Teknologi**
