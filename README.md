# Urai Video Studio

**Urai Studio Pro** adalah editor video berbasis browser untuk kreator yang ingin memotong klip, mengatur format sosial media, menambahkan teks, dan mengekspor video secara lokal.

## Halaman

- [`index.html`](index.html) — halaman produk dan navigasi.
- [`studio-pro.html`](studio-pro.html) — editor Pro dengan template gaya, trim, musik, ekspor WebM, serta simpan/muat pengaturan proyek JSON.
- [`studio.html`](studio.html) — alat Gemini opsional untuk rekomendasi momen dan transkripsi audio.

## Memulai

Repositori berupa situs statis, tanpa proses build atau backend aplikasi.

1. Buka halaman situs atau `studio-pro.html` di browser modern.
2. Jika browser membatasi akses file, jalankan server lokal di folder repo: `python -m http.server 8000`, lalu buka `http://localhost:8000`.
3. Pilih video, tetapkan titik masuk/keluar, pilih rasio/template, tambahkan teks atau audio, dan pratinjau klip.
4. Tekan **Ekspor klip · WebM**. Tunggu hingga download selesai sebelum menutup tab.
5. Untuk menyimpan pengaturan edit, gunakan **Simpan pengaturan**. File proyek tidak menyertakan video, audio, maupun API key. Muat proyek dan pilih ulang media bila diperlukan.

## Fitur Pro

- Trim manual berbasis waktu, playhead, dan pratinjau rentang.
- Rasio kanvas 16:9, 9:16, dan 1:1 dengan crop tengah.
- Template Clean, Hook, dan Creator yang dapat disesuaikan.
- Judul, watermark, pilihan audio asli, musik latar, dan pengaturan volume.
- Ekspor WebM menggunakan kemampuan browser (`canvas.captureStream`, `MediaRecorder`, dan Web Audio API).
- Simpan/muat pengaturan proyek JSON secara lokal.

## Alat Gemini opsional

`studio.html` dapat mengirim frame sampel video untuk saran momen klip dan file audio terpisah untuk transkripsi teks. Penggunaan memerlukan koneksi internet dan Gemini API key milik pengguna. Key dipakai dari memori halaman, tidak disimpan aplikasi. Request AI mengirim materi yang dipilih ke Google Gemini. Hasil AI hanyalah saran dan perlu diperiksa/koreksi. Periksa kuota, harga, kebijakan data, serta ketentuan Google. Jangan kirim materi sensitif atau materi yang Anda tidak berhak kirim.

## Privasi dan keterbatasan

- Editor Pro memproses file video lokal di browser dan tidak mengunggahnya ke server aplikasi.
- File proyek hanya berisi pengaturan editor; media sumber tidak termasuk.
- Audio untuk AI dikirim hanya saat fitur transkripsi dipicu. Alat transkripsi mengembalikan teks, bukan subtitle bertimestamp.
- Ekspor saat ini WebM, bukan MP4 native. Codec dan hasilnya bergantung browser, perangkat, memori, dan izin. Uji klip pendek lebih dahulu.
- Crop rasio terpusat; periksa objek penting sebelum mengekspor.
- Belum ada sinkronisasi cloud, akun pengguna, ekspor SRT/VTT, atau pengujian otomatis lintas browser.

## Publikasikan dengan GitHub Pages

1. Buka **Settings → Pages** pada repositori.
2. Pilih **Deploy from a branch**, pilih branch `main` dan folder root `/`, lalu simpan.
3. Tunggu proses deployment dan buka URL Pages yang ditampilkan GitHub.
4. Pastikan halaman awal, editor, dan tautan panduan berfungsi di desktop serta perangkat mobile.

Sajikan melalui HTTPS untuk kompatibilitas API browser yang lebih baik. Jangan menaruh API key pribadi di source HTML atau commit repository.

## Pemeriksaan sebelum dipakai

Uji file dengan audio dan tanpa audio, ketiga rasio, batas rentang, musik latar, simpan/muat proyek, dan ekspor pada browser yang akan digunakan. Pastikan ada hak penggunaan atas video dan musik. Periksa hasil WebM sebelum publikasi.

## Kredit dan lisensi

Dikembangkan oleh Urai Ikhsan Fadhilah. Tambahkan file LICENSE jika ingin menetapkan syarat penggunaan/distribusi.
