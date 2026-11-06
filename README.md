# Urai Video Studio

Aplikasi web satu halaman untuk meninjau video lokal, memilih rentang klip, menambahkan overlay sederhana, meminta rekomendasi momen dari Gemini, dan mengekspor hasil melalui browser.

> **Status:** prototipe sisi-klien. Fitur dan format ekspor bergantung pada browser/perangkat; selalu tinjau hasil sebelum dipublikasikan.

## Fitur

- Memuat video dari perangkat (MP4, WebM, MOV yang didukung browser).
- Memutar, mengatur kecepatan, memilih titik masuk/keluar, dan melihat pratinjau klip.
- Mengatur rasio pratinjau 16:9, 9:16, atau 1:1.
- Menambahkan banner, watermark, subtitle, dan audio latar pada pratinjau.
- Meminta rekomendasi momen klip dan caption dari Gemini berdasarkan cuplikan frame.
- Menyimpan pilihan klip dan mengekspor melalui kemampuan perekaman browser.

## Menjalankan aplikasi

Aplikasi ini berupa HTML statis dan tidak memerlukan proses build:

1. Buka `index.html` di browser modern, atau sajikan folder ini melalui hosting statis seperti GitHub Pages.
2. Pilih video dari perangkat.
3. Atur titik **In/Out**, rasio, dan overlay sesuai kebutuhan.
4. Simpan klip pilihan. Untuk rekomendasi AI, masukkan Gemini API key milik sendiri melalui tombol **Gemini API Key**, lalu jalankan analisis.
5. Pilih klip yang akan diekspor dan ikuti dialog browser.

Koneksi internet diperlukan untuk memuat pustaka/font dari CDN dan menggunakan Gemini. Izin atau dukungan browser tambahan mungkin dibutuhkan untuk ekspor.

## Gemini API key dan privasi

- Buat dan kelola key melalui [Google AI Studio](https://aistudio.google.com/). Penggunaan tunduk pada kuota, harga, dan ketentuan Google; aplikasi tidak menyediakan API gratis.
- Key disimpan di `localStorage` browser. Itu **bukan penyimpanan rahasia yang aman**: jangan gunakan key berhak akses luas pada perangkat bersama, dan hapus key setelah selesai.
- Analisis AI mengirim gambar keyframe yang diambil dari video ke layanan Google Gemini. Jangan analisis video yang memuat informasi sensitif atau materi yang tidak berhak Anda kirim.
- Transkripsi menggunakan Web Speech API jika tersedia. Implementasi dan pemrosesan audio mengikuti dukungan serta kebijakan browser; jangan menganggap audio selalu diproses sepenuhnya offline.
- File video dipilih dari perangkat, tetapi pustaka pihak ketiga dimuat dari CDN. Untuk penggunaan sensitif, tinjau kode dan dependensi terlebih dahulu.

## Batasan yang perlu diketahui

- Speech recognition tidak tersedia di semua browser dan hasil Bahasa Indonesia dapat memerlukan koreksi manual.
- Rekomendasi Gemini hanya berdasarkan sejumlah frame sampel, bukan pemahaman penuh atas setiap frame atau transkrip. Periksa kembali waktu klip, konteks, caption, dan hashtag.
- Rasio yang dipilih memengaruhi pratinjau; periksa hasil ekspor untuk memastikan crop, audio, overlay, dan codec sesuai kebutuhan.
- Ekspor berbasis browser dapat gagal atau terbatas oleh codec, memori, durasi video, izin folder, dan dukungan `MediaRecorder`/File System Access API. Coba klip pendek terlebih dahulu.
- Jangan menutup atau memuat ulang halaman selama pekerjaan penting belum selesai. Simpan hasil akhir ke perangkat dan buat salinan cadangan.

## Pemeriksaan sebelum rilis

Sebelum menggunakan hasil secara publik, uji setidaknya: video pendek dan panjang, tiap rasio, rentang In/Out dekat batas durasi, video tanpa audio, BGM aktif/nonaktif, browser desktop dan mobile, serta unduhan/ekspor dengan format yang dihasilkan browser. Pastikan juga Anda memiliki hak atas video, musik, dan materi yang digunakan.

## Pengembangan selanjutnya

Prioritas yang akan membuat aplikasi lebih andal: validasi ukuran/format dan batas durasi input; penanganan kegagalan ekspor yang jelas; kontrol untuk membatalkan proses; editor subtitle bertimestamp dan ekspor SRT/VTT; opsi kualitas/codec dengan deteksi dukungan browser; serta pengujian otomatis untuk pemotongan dan overlay.

## Kredit

Dikembangkan oleh Urai Ikhsan Fadhilah.
