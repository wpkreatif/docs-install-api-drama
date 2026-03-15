# 🚀 Panduan Instalasi & Integrasi API Drama (Vercel)

Dokumentasi ini berisi langkah-langkah deploy API ke Vercel dan cara menghubungkannya dengan script Laravel.

---

## 📂 1. Persiapan Repositori GitHub
Siapkan 3 repositori berbeda untuk masing-masing source drama.

* **Login/Register**: Masuk ke akun [GitHub](https://github.com).
* **Buat Repository**: Klik **New Repository**.
    * **Repository Name**: Bebas (Contoh: `api-dramabox`, `api-netshort`, `api-melolo`).
    * **Description**: Opsional (Contoh: `API Source for Dramabox`).
    * **Visibility**: Ubah ke **Private** 🔒 (Penting: Agar API tidak dicuri/dipakai orang lain).
    * **Add README**: Bebas (On/Off).
* **Ulangi**: Lakukan langkah ini sampai kamu memiliki **3 repositori**.

> [!NOTE]
> Di masa mendatang, update akan dikombinasikan menjadi **1 Full Source Script** (1 repository saja).

---

## ⚡ 2. Deployment ke Vercel
Menjalankan script dari GitHub ke server Vercel secara gratis.

1.  **Akses Vercel**: Buka [vercel.com](https://vercel.com) dan login menggunakan akun GitHub kamu.
2.  **Import Project**:
    * Klik tombol **Add New** > **Project**.
    * Pilih repositori yang tadi dibuat (Contoh: `api-dramabox`) lalu klik **Import**.
3.  **Konfigurasi**:
    * **Project Name**: Sesuaikan atau biarkan default.
    * **Settings**: Biarkan semua pada pengaturan default.
    * Klik **Deploy**.
4.  **Selesai**: Tunggu proses build hingga muncul kembang api. Kamu akan mendapatkan domain seperti `https://api-dramabox.vercel.app`.
5.  **Ulangi**: Lakukan hal yang sama untuk `netshort` dan `melolo`.

---

## 🛠️ 3. Integrasi ke Script Laravel
Hubungkan backend Laravel kamu dengan URL API baru dari Vercel.

### A. Update Base URL
Buka folder projek Laravel kamu, lalu edit file-file berikut:

| Nama File | Path |
| :--- | :--- |
| **DramaBox** | `app/Services/DramaBoxService.php` |
| **Melolo** | `app/Services/MeloloService.php` |
| **Netshort** | `app/Services/NetshortService.php` |

**Cari baris kode berikut dan ganti dengan URL Vercel kamu:**

```php
// Contoh pada DramaBoxService.php
private string $baseApiUrl = 'https://api-dramabox.vercel.app';
```

### B. Pembersihan Cache
Setelah file di-save, jalankan langkah berikut agar sistem mengenali API baru:

1.  **Login Admin: Masuk ke**: `domainanda.com/admin/login`
2.  **Clear Cache: Akses URL berikut di browser:**: `domainanda.com/admin/clear-cache`
3.  **Verifikasi**: Cek apakah data drama sudah muncul menggunakan API baru.

### ✅ Selesai
API sekarang sudah berjalan di infrastruktur milikmu sendiri.
