# Urai Video Studio

Editor video berbasis browser untuk memotong klip, menambahkan judul/watermark, dan mengekspor hasil WebM. Aplikasi dapat dijalankan sebagai situs statis; tidak ada server aplikasi atau proses build.

## Mulai

- **Editor:** buka [`studio.html`](studio.html).
- **Halaman awal:** `index.html` berisi ringkasan fitur dan tautan ke editor.
- Untuk mencoba di komputer, buka file melalui browser modern. Jika fitur browser membatasi akses file, jalankan server statis lokal, misalnya `python -m http.server 8000`, lalu buka `http://localhost:8000`.

## Gunakan editor

1. Pilih video dari perangkat. Tunggu hingga durasi terbaca.
2. Atur titik masuk/keluar dengan kolom detik, slider pemutaran, atau tombol **Tetapkan masuk/keluar**.
3. Pilih rasio, masukkan judul dan/atau watermark, dan pilih musik latar bila diperlukan.
4. Gunakan **Pratinjau potongan** untuk memeriksa rentang, lalu tekan **Ekspor klip (WebM)**.
5. Tunggu sampai unduhan selesai sebelum menutup halaman.

Ekspor menggunakan `canvas.captureStream`, `MediaRecorder`, dan `Web Audio API` yang tersedia di browser. Hasilnya WebM; dukungan codec, ukuran dan kualitas tergantung browser serta perangkat. Coba video pendek lebih dahulu. File WebM mungkin perlu dikonversi untuk platform yang mengharuskan MP4.

## Fitur Gemini (opsional)

Editor menyediakan dua tindakan AI:

- **Usulkan momen klip:** mengirim sejumlah frame sampel dari video ke Gemini untuk memperoleh saran rentang dan alasan. Waktu saran hanya perkiraan; periksa dan pratinjau sebelum mengekspor.
- **Transkripsikan audio:** memilih file audio terpisah untuk memperoleh teks transkrip. Output tidak berisi timing subtitle dan perlu ditinjau/koreksi.

Untuk menggunakan AI, masukkan Gemini API key pada editor dan dapatkan/kelola key dari [Google AI Studio](https://aistudio.google.com/). Key hanya berada di memori halaman dan tidak disimpan oleh aplikasi; request API mengirim key ke Google melalui header, bukan menyimpannya ke localStorage. Frame/audio yang diminta untuk dianalisis dikirim langsung ke Gemini. API memerlukan internet dan dapat tunduk pada kuota, harga, kebijakan retensi, serta ketentuan Google. Jangan kirim materi sensitif. Gunakan key dengan pembatasan yang sesuai dan hapus/rotasi key bila terpapar.

## Privasi dan batasan

- Video sumber diproses secara lokal di browser dan tidak diunggah oleh editor ke backend aplikasi.
- Hanya ketika Anda menjalankan fitur Gemini, frame yang dipilih atau audio yang dipilih akan dikirim ke layanan Google.
- Fitur transkripsi menerima file audio secara terpisah; editor tidak mengklaim bahwa browser otomatis mentranskripsikan suara video. Batas input aplikasi saat ini 20 MB.
- Tidak tersedia subtitle bertimestamp, ekspor SRT/VTT, atau ekspor MP4 native.
- File panjang/resolusi tinggi dapat lambat, gagal karena memori, atau menghasilkan audio/video yang berbeda antarbrowser. Audio latar dicampur dengan audio asli.
- Pemilihan rasio menggunakan crop tengah. Periksa objek penting pada pratinjau, khususnya saat membuat video vertikal.
- Pustaka UI eksternal tidak digunakan pada editor ini; permintaan AI tetap memakai layanan Google.

## Publikasikan dengan GitHub Pages

1. Pastikan `index.html`, `studio.html`, dan `README.md` berada di root branch publikasi.
2. Di repositori, buka **Settings → Pages**.
3. Pada **Build and deployment**, pilih **Deploy from a branch**, pilih branch yang berisi file (misalnya `main`) dan folder `/ (root)`, kemudian simpan.
4. Tunggu deployment selesai dan buka URL Pages yang ditampilkan di pengaturan. `index.html` menjadi halaman awal; tombol **Mulai mengedit video** membuka editor.
5. Uji tautan, upload, pratinjau, dan ekspor di browser desktop dan mobile. Untuk fitur AI, pastikan koneksi, API key, dan kuota Google tersedia.

Editor sebaiknya disajikan melalui HTTPS (GitHub Pages menyediakan HTTPS) untuk dukungan API browser yang lebih baik. Jangan pernah menaruh API key pemilik di file HTML, repository, atau script publik.

## Pemeriksaan sebelum rilis

Coba video dengan audio dan tanpa audio, rasio 16:9/9:16/1:1, batas awal/akhir, audio latar, ekspor WebM, serta browser desktop/mobile. Cek juga bahwa permintaan AI hanya terjadi setelah pengguna menekan tombolnya. Aplikasi ini belum diuji otomatis lintas browser; hasil produksi perlu diverifikasi manual.

## Kredit dan lisensi

Dikembangkan oleh Urai Ikhsan Fadhilah. Tambahkan file lisensi jika ingin menetapkan syarat penggunaan atau distribusi kode.
