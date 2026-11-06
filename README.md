# Urai Video Studio

**Urai Studio Pro** adalah editor video statis berbasis browser untuk kreator. Versi Pro membantu trim klip, membentuk video sosial media, menyusun subtitle, menyimpan pengaturan proyek, dan mengekspor WebM secara lokal.

## Halaman

- [`index.html`](index.html) — halaman produk premium dan navigasi.
- [`studio-pro.html`](studio-pro.html) — editor Pro: trim, template, overlay, audio, subtitle bertimestamp, SRT, proyek JSON, dan WebM.
- [`compress.html`](compress.html) — kompresi/re-encode lokal untuk bitrate dan resolusi lebih rendah.
- [`studio.html`](studio.html) — alat Gemini opsional untuk rekomendasi momen dan transkripsi audio.

## Alur yang disarankan

1. Buka `studio-pro.html`, pilih video, atur rentang, lalu ekspor klip WebM.
2. Jika ukuran file masih besar, buka [`compress.html`](compress.html), pilih file hasil ekspor, turunkan bitrate/resolusi, lalu jalankan kompresi.
3. Periksa ukuran estimasi, format yang didukung browser, dan hasil kualitas sebelum memakai file.

Kompresor menyediakan bitrate video 0.7–5 Mbps, resolusi hingga 37.5%, bitrate audio sekitar 96 kbps, estimasi ukuran, serta deteksi format. Estimasi ukuran bukan jaminan; konten, audio, dan container memengaruhi hasil. Bitrate/resolusi lebih rendah mengurangi ukuran dengan trade-off kualitas. Kompresi ulang dapat memerlukan waktu setidaknya sepanjang video.

## Format MP4 dan browser

`MediaRecorder` hanya dapat menulis codec/container yang benar-benar didukung browser. Kompresor memeriksa dukungan MP4 dan WebM, dan tidak mengganti ekstensi untuk berpura-pura MP4. Bila MP4 tidak tersedia, pilih WebM atau gunakan konverter desktop tepercaya (misalnya HandBrake). MP4 yang konsisten lintas browser memerlukan encoder/transcoder khusus.

## Memulai

Situs ini statis: tidak ada proses build atau backend aplikasi.

1. Buka situs atau `studio-pro.html` di browser modern.
2. Jika browser membatasi akses file, jalankan `python -m http.server 8000` di folder repository dan buka `http://localhost:8000`.
3. Pilih video dan atur rentang IN/OUT. Gunakan template atau sesuaikan kanvas, judul, watermark, serta musik.
4. Untuk subtitle, pindahkan playhead, masukkan teks, pilih durasi lalu tekan **Tambah di playhead**. Cue dapat diedit satu per satu, di-burn-in pada ekspor, atau diunduh sebagai SRT.
5. Simpan pengaturan proyek JSON untuk melanjutkan edit nanti. Proyek tidak menyertakan video atau audio—pilih ulang media saat sesi baru.

## Gemini AI opsional

`studio.html` dapat mengirim frame sampel video untuk saran momen klip, atau file audio terpisah untuk transkripsi teks. Fitur ini butuh internet dan Gemini API key milik pengguna. Key dipakai di memori halaman dan tidak disimpan aplikasi. Materi yang dipilih dikirim ke Google saat pengguna memulai analisis. Hasil AI hanyalah saran dan perlu diperiksa. Periksa kuota, harga, kebijakan data, dan ketentuan Google; jangan kirim materi sensitif atau materi yang tidak berhak Anda kirim.

## Privasi dan batasan

- Editor dan kompresor memproses video lokal di browser; tidak ada backend upload video aplikasi.
- File proyek hanya berisi pengaturan/cue subtitle. Sumber video/audio dan API key tidak disertakan.
- Ekspor editor saat ini WebM, bukan MP4 native. Codec dan hasil bergantung browser, perangkat, memori, dan izin.
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
