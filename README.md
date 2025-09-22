# Flutter Scanner Card App
![image_app](https://github.com/vinntodev/fl_scanner_card_app/blob/613708e33ff8e35c4529d265caeac63cc4714b34/img/ui.png)

Aplikasi Flutter untuk memindai (scan) kartu atau dokumen menggunakan Google ML Kit Document Scanner, menyimpan hasil sebagai gambar, memberi nama dan kategori, lalu menampilkannya dalam daftar/grid. Data metadata disimpan lokal menggunakan SQLite (sqflite).

## Fitur
- Scan dokumen/kartu dengan Google ML Kit (`google_mlkit_document_scanner`).
- Import dari galeri atau kamera (sesuai dukungan plugin).
- Simpan hasil scan sebagai gambar dengan:
  - Nama dokumen
  - Kategori: Kartu, Nota, Surat
  - Tanggal dibuat
- Lihat dokumen terbaru dalam tampilan grid.
- Detail dokumen (pratinjau gambar dan informasi dasar).

## Tech Stack & Dependency
- Flutter SDK
- UI: Material, `google_fonts`
- Scan: `google_mlkit_document_scanner ^0.2.1`
- Database lokal: `sqflite`
- Utilitas: `intl`

Lihat `pubspec.yaml` untuk versi lengkap dependency.

## Struktur Proyek (ringkas)
```
lib/
  core/                # Warna, spacing, komponen teks
  data/
    datasources/       # SQLite datasource (document_local_datasource.dart)
    models/            # Model data (DocumentModel)
  pages/               # Halaman utama, simpan, daftar terbaru, detail, kategori
  main.dart            # Entry point aplikasi
```

## Persyaratan
- Flutter 3.5+ (sesuai `environment: sdk: ^3.5.0`)
- Android: minSdk sesuai ketentuan plugin Google ML Kit (umumnya 21+)
- iOS: iOS 13+ (disarankan), Xcode terbaru

## Setup & Menjalankan
1. Clone atau salin proyek ini.
2. Install dependency:
   ```bash
   flutter pub get
   ```
3. Jalankan di emulator/device:
   ```bash
   flutter run
   ```

### Izin/Permissions
- Kamera & Akses Media/Galeri diperlukan untuk proses scan/import gambar.
- Android: pastikan permission kamera/penyimpanan diberikan saat runtime.
- iOS: tambahkan deskripsi izin di Info.plist bila diperlukan (kamera, foto).

## Alur Penggunaan
1. Buka aplikasi dan tekan tombol "Scan Dokumen" di beranda.
2. Pindai dokumen atau pilih dari galeri.
3. Isi nama dokumen dan pilih kategori (Kartu/Nota/Surat), lalu simpan.
4. Dokumen tersimpan akan muncul pada bagian "Latest Documents".
5. Ketuk item untuk melihat detail.

## Catatan Teknis
- Data metadata (nama, kategori, path gambar, tanggal) disimpan di SQLite (`documents` table) melalui `DocumentLocalDatasource`.
- Gambar disimpan sebagai file pada path yang dikembalikan plugin scanner, dan ditampilkan dengan `Image.file`.

## Build APK/IPA
- Android (debug):
  ```bash
  flutter build apk --debug
  ```
- Android (release):
  ```bash
  flutter build apk --release
  ```
- iOS: buka workspace Xcode atau gunakan `flutter build ios` lalu proses signing sesuai kebutuhan.

## Troubleshooting
- Jika scanner tidak berjalan di Android, pastikan layanan Google Play dan minSdk sesuai.
- Periksa permission kamera/foto sudah disetujui.
- Pastikan perangkat memiliki kamera dan mendukung ML Kit.

## Lisensi
Proyek ini bersifat open untuk penggunaan pribadi/pendidikan. Sesuaikan lisensi sesuai kebutuhan Anda.
