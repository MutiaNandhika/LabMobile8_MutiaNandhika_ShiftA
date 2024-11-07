# LabMobile8_MutiaNandhika_ShiftA

## Penjelasan Cara Proses CRUD

### 1. Create Data Mahasiswa
<img src="https://github.com/user-attachments/assets/5c0349ee-2206-46d7-98d7-9638029aba61" alt="Screenshot" width="300"/>
<img src="https://github.com/user-attachments/assets/396d1508-19c6-44c8-aa2c-d7a370d3117a" alt="Screenshot" width="300"/>

Untuk menambahkan data mahasiswa baru, aplikasi membuka modal `Tambah Mahasiswa` melalui fungsi `openModalTambah()`, yang mengaktifkan modal input untuk mengisi nama dan jurusan mahasiswa. Setelah data dimasukkan, fungsi `tambahMahasiswa()` di `mahasiswa.page.ts` akan mengirimkan data tersebut ke API `tambah.php` menggunakan HTTP POST. API ini akan menyimpan data di database dan kemudian menampilkan ulang daftar mahasiswa yang telah diperbarui.

### 2. Read Data Mahasiswa
<img src="https://github.com/user-attachments/assets/f67ce7d7-2b72-4a0d-b9a0-01c8d2816651" alt="Screenshot" width="300"/>

Data mahasiswa ditampilkan dengan memanggil API `tampil.php` melalui fungsi `getMahasiswa()` di Ionic. Data yang diterima dari API ditampilkan dalam bentuk daftar menggunakan komponen `ion-card` dengan perulangan `*ngFor`, sehingga setiap mahasiswa akan ditampilkan dengan nama dan jurusan.

### 3. Update Data Mahasiswa
<img src="https://github.com/user-attachments/assets/e24173e3-1291-4115-a465-1429e00dca0e" alt="Screenshot" width="300"/>
<img src="https://github.com/user-attachments/assets/1f4ec036-f5a4-4d7b-95d4-be7c192120ba" alt="Screenshot" width="300"/>
<img src="https://github.com/user-attachments/assets/9fde26c4-5dd6-4f43-903c-85fec332213b" alt="Screenshot" width="300"/>

Pengguna dapat memperbarui data mahasiswa dengan memilih tombol "Edit" yang tersedia di setiap entri mahasiswa. Modal `Edit Mahasiswa` terbuka dengan data yang sudah terisi sebelumnya, kemudian pengguna dapat memperbarui nama atau jurusan. Setelah perubahan selesai, fungsi `editMahasiswa()` akan mengirim data yang diperbarui ke API `edit.php` yang akan memperbarui data di database.

### 4. Delete Data Mahasiswa
<img src="https://github.com/user-attachments/assets/fa539957-f5e1-47ca-af7c-d4a0a69f7d48" alt="Screenshot" width="300"/>
<img src="https://github.com/user-attachments/assets/f9054ece-c68c-4308-ae76-d028eb413822" alt="Screenshot" width="300"/>

Pengguna dapat menghapus data mahasiswa dengan menekan tombol "Hapus" pada entri mahasiswa yang diinginkan. Fungsi `konfirmasiHapus()` akan menampilkan alert konfirmasi sebelum penghapusan. Jika pengguna memilih "Ya", maka fungsi `hapusMahasiswa()` akan memanggil API `hapus.php` untuk menghapus data dari database.

### Backend (Database dan PHP API)
- **Database**: Dibuat tabel `mahasiswa` pada database `db_mhs` dengan kolom `id` (kunci utama), `nama`, dan `jurusan`.
- **API PHP**:
  - **koneksi.php**: Menghubungkan aplikasi ke database menggunakan `mysqli_connect`. File ini digunakan oleh semua file API untuk akses data di database.
  - **tampil.php**: Mengambil semua data dari tabel `mahasiswa` dan mengembalikannya dalam format JSON.
  - **tambah.php**: Menerima data JSON dari frontend, kemudian menyimpannya ke dalam database jika data valid.
  - **edit.php**: Mengambil data yang diperbarui dari frontend dan memperbarui data di database berdasarkan ID mahasiswa.
  - **hapus.php**: Menghapus data mahasiswa dari database berdasarkan ID yang diterima dari frontend.
 
### Frontend (Ionic)
- **Tambah Data (Create)**:
  - Fungsi `tambahMahasiswa()` di `mahasiswa.page.ts` mengirim data ke `tambah.php`.
  - Modal `Tambah Mahasiswa` berisi form input untuk nama dan jurusan yang muncul saat tombol tambah ditekan.

- **Tampilkan Data (Read)**:
  - Fungsi `getMahasiswa()` di `mahasiswa.page.ts` mengambil data dari `tampil.php` dan menampilkannya dalam daftar.

- **Edit Data (Update)**:
  - Fungsi `editMahasiswa()` mengirim data yang diperbarui ke `edit.php`.
  - Modal `Edit Mahasiswa` menampilkan data saat ini yang dapat diubah sebelum disimpan.

- **Hapus Data (Delete)**:
  - Fungsi `konfirmasiHapus()` menampilkan konfirmasi, dan `hapusMahasiswa()` mengirim permintaan hapus ke `hapus.php` jika pengguna mengonfirmasi.
