# Urai Video Studio

**Urai Studio Pro** adalah editor video statis berbasis browser untuk kreator. Versi Pro membantu trim klip, membentuk video sosial media, menyusun subtitle, menyimpan pengaturan proyek, dan mengekspor WebM secara lokal.

## Halaman

- [`index.html`](index.html) — halaman produk premium dan navigasi.
- [`studio-pro.html`](studio-pro.html) — editor Pro: trim, template, overlay, audio, subtitle bertimestamp, SRT, proyek JSON, dan WebM.
- [`compress.html`](compress.html) — utilitas kompresi/re-encode lokal untuk mengatur bitrate dan resolusi.
- [`studio.html`](studio.html) — alat Gemini opsional untuk rekomendasi momen dan transkripsi audio.

## Memulai

Situs ini statis: tidak ada proses build atau backend aplikasi.

1. Buka situs atau `studio-pro.html` di browser modern.
2. Jika browser membatasi akses file, jalankan `python -m http.server 8000` di folder repository dan buka `http://localhost:8000`.
3. Pilih video dan atur rentang IN/OUT. Gunakan template atau sesuaikan kanvas, judul, watermark, serta musik.
4. Untuk subtitle, pindahkan playhead, masukkan teks, pilih durasi lalu tekan **Tambah di playhead**. Cue dapat diedit satu per satu, di-burn-in pada ekspor, atau diunduh sebagai SRT.
5. Simpan pengaturan proyek JSON untuk melanjutkan edit nanti. Proyek tidak menyertakan video atau audio—pilih ulang media saat sesi baru.
6. Ekspor WebM dan tunggu hingga file terunduh sebelum menutup tab.
7. Bila ukuran terlalu besar, buka `compress.html`, pilih file WebM hasil ekspor, dan atur bitrate atau resolusi lebih rendah. MP4 hanya tersedia jika browser melaporkan encoder MP4 MediaRecorder yang kompatibel.

## Fitur Pro

- Trim manual dengan timeline, titik masuk/keluar dan pratinjau.
- Kanvas 16:9, 9:16, dan 1:1 dengan crop tengah.
- Template Clean, Hook, Creator; kontrol teks, warna, posisi, dan watermark.
- Musik latar dan pilihan menyertakan audio sumber.
- Subtitle bertimestamp: tambah, ubah waktu/teks, hapus, tampilkan di kanvas, ekspor SRT.
- Simpan/muat proyek JSON lokal (pengaturan serta subtitle, bukan file media/key).
- Pintasan keyboard: Space untuk putar/jeda, tombol panah kiri/kanan untuk mundur/maju 5 detik saat fokus tidak berada pada input.
- Kompresi lokal di `compress.html` dengan pilihan bitrate, resolusi, dan deteksi format browser.

## Batasan format dan kompresi

`MediaRecorder` hanya dapat menulis codec/container yang benar-benar didukung browser. Utilitas kompresi memeriksa dukungan MP4 dan WebM saat dibuka. Pada browser yang tidak menyediakan MP4, pilih WebM; alat ini tidak mengganti ekstensi untuk berpura-pura MP4. Untuk MP4 yang konsisten lintas browser diperlukan encoder/transcoder khusus, yang biasanya menambah unduhan besar, penggunaan CPU/memori, dan waktu proses. Bitrate lebih kecil umumnya membuat file lebih kecil tetapi dapat menurunkan kualitas. Kompresi ulang juga memerlukan waktu real-time atau lebih lama.

## Gemini AI opsional

`studio.html` dapat mengirim frame sampel video untuk saran momen klip, atau file audio terpisah untuk transkripsi teks. Fitur ini butuh internet dan Gemini API key milik pengguna. Key dipakai di memori halaman dan tidak disimpan aplikasi. Materi yang dipilih dikirim ke Google saat pengguna memulai analisis. Hasil AI hanyalah saran dan perlu diperiksa. Periksa kuota, harga, kebijakan data, dan ketentuan Google; jangan kirim materi sensitif atau materi yang tidak berhak Anda kirim.

## Privasi dan keterbatasan lain

- Video editor Pro diproses lokal di browser; tidak ada backend upload video.
- File proyek hanya berisi pengaturan/cue subtitle. Sumber video/audio dan API key tidak disertakan.
- Ekspor editor saat ini WebM, bukan MP4 native. Codec dan hasil bergantung browser, perangkat, memori, dan izin. Uji klip pendek dahulu.
- Crop dilakukan dari tengah; pastikan objek penting tetap terlihat pada pratinjau.
- Subtitle SRT dibuat dari cue yang dimasukkan pengguna. Alat AI transkripsi menghasilkan teks tanpa timestamp dan bukan subtitle otomatis bertiming.
- Belum ada sinkronisasi cloud, akun pengguna, ekspor batch, atau tes otomatis lintas browser.

## GitHub Pages

1. Buka **Settings → Pages** pada repository.
2. Pilih **Deploy from a branch**, pilih `main` dan folder root `/`, lalu simpan.
3. Tunggu deployment dan kunjungi URL Pages yang ditampilkan GitHub.
4. Uji tautan, upload lokal, subtitle, simpan/muat proyek, dan ekspor di desktop serta mobile.

Sajikan melalui HTTPS untuk kompatibilitas API browser yang lebih baik. Jangan commit API key pribadi atau menaruhnya di HTML publik.

## Kredit dan lisensi

Dikembangkan oleh Urai Ikhsan Fadhilah. Tambahkan file `LICENSE` bila ingin menetapkan syarat penggunaan atau distribusi.
