# Tugas 3 PCD: Segmentasi Otsu dan Operasi Morfologi

Eksperimen segmentasi citra dengan thresholding Otsu serta perbaikan hasilnya lewat operasi morfologi (erosi, dilatasi, opening, dan closing) untuk mata kuliah Pengolahan Citra Digital.

## Struktur folder

```
.
├── images/
│   └── 23560e97ad.jpg
├── PCD_Assignment03.ipynb
├── Laporan_PCD_Segmentation_Morphological_Jundan.pdf
└── README.md
```

`images/` berisi satu citra koin yang dipakai sebagai input. Notebook berisi seluruh kode eksperimen, dan laporan PDF berisi hasil serta analisisnya.

## Isi eksperimen

Citra dimuat berwarna lewat `cv2.imread`, lalu diubah ke grayscale dengan `cv2.cvtColor`, tanpa tahap resize atau crop tambahan. Citra koin berukuran 500x314 piksel dan berisi 15 koin di atas permukaan meja.

Dua eksperimen utama dijalankan:

1. **Segmentasi Otsu**, citra grayscale dibinarisasi dengan algoritma Otsu yang ditulis manual (histogram 256 tingkat keabuan dan variansi antar-kelas). Polaritas citra biner disesuaikan otomatis lewat pemeriksaan piksel tepi, supaya koin bernilai 1 dan meja bernilai 0. Pada citra ini threshold yang terpilih adalah 133.
2. **Operasi morfologi**, hasil Otsu diproses dengan erosi, dilatasi, opening, dan closing memakai jendela persegi 5x5 yang dibangun manual lewat sliding window dan padding. Dua urutan gabungan juga dibandingkan: closing lalu opening, dan opening lalu closing.

Catatan cakupan pengujian: seluruh eksperimen hanya memakai satu citra, satu ukuran kernel (5x5 persegi), dan satu kali jalan untuk tiap operasi. Tidak ada citra acuan berupa hasil segmentasi yang benar dan tidak ada metrik kuantitatif, sehingga penilaian hasil bersifat visual. Waktu proses pada dua urutan gabungan hanya mencakup langkah keduanya, karena hasil langkah pertama dipakai ulang dari proses sebelumnya. Detail dan alasan pembatasan ini ada di laporan.

Rincian lengkap desain eksperimen, hasil, dan analisis (termasuk waktu eksekusi tiap operasi) ada di `Laporan_PCD_Segmentation_Morphological_Jundan.pdf`.

## Menjalankan notebook

Notebook ditulis untuk Google Colab dan memakai Google Drive sebagai sumber citra (lihat sel `drive.mount` dan `DRIVE_IMG_DIR`). Untuk menjalankan di luar Colab, ganti bagian mount drive dan `DRIVE_IMG_DIR` dengan path lokal ke folder `images/`.

Dependencies:

```
opencv-python
numpy
matplotlib
```

## Penulis

Jundan Saiful Haq
NIM 25/560768/PA/23633
