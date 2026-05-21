# Analisis Autokorelasi Spasial (Global Moran's I) dengan ArcPy

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python)
![ArcGIS Pro](https://img.shields.io/badge/ArcGIS_Pro-ArcPy-2073C4)
![License](https://img.shields.io/badge/License-MIT-green)
![Status](https://img.shields.io/badge/Status-Geocomputation-orange)

## Deskripsi Proyek

Repositori ini memuat skrip otomatisasi berbasis **Jupyter Notebook (.ipynb)** yang dijalankan di dalam lingkungan Python **ArcGIS Pro**. Skrip ini dirancang untuk mengevaluasi autokorelasi spasial dari kejadian kebakaran hutan dan lahan (titik panas/hotspot) di Provinsi Jambi selama periode 2010–2020.

Analisis dilakukan menggunakan algoritma **Global Moran's I** untuk melihat apakah distribusi spasial titik panas bersifat mengelompok (*clustered*), menyebar (*dispersed*), atau acak (*random*).

## Fitur Otomatisasi (Pipeline)

1.  **Iterasi Temporal & Kategorikal:** Mengeksekusi alat *Spatial Autocorrelation* secara otomatis untuk keseluruhan data tahunan dan per kategori (Hotspot & Coldspot berdasarkan signifikansi `Gi_Bin`).
2.  **HTML to PDF Engine:** ArcGIS Pro secara bawaan menghasilkan laporan Moran's I dalam format HTML yang tersembunyi di *scratch folder*. Skrip ini menggunakan *Regular Expression* (RegEx) untuk melacak file tersebut dan mengonversinya menjadi dokumen `.pdf` menggunakan `pdfkit`.
3.  **Ekstraksi Metrik Cerdas:** Menambang nilai *Moran's Index*, *Z-Score*, dan *P-Value* langsung dari teks dokumen HTML.
4.  **Laporan Tabular Excel:** Mengompilasi seluruh metrik statistik ke dalam format *spreadsheet* multi-lembar (`.xlsx`) dengan format sel berstandar akademis.

## Prasyarat Lingkungan Kerja (Environment)

Skrip ini tidak dapat dijalankan di Python reguler atau Google Colab. Anda **wajib** menjalankannya di mesin yang memiliki lisensi ArcGIS Pro.

### 1. Perangkat Lunak & Pustaka Python
Buka **Python Command Prompt** bawaan ArcGIS Pro, lalu instal pustaka pendukung berikut:
```cmd
pip install pdfkit openpyxl

```

### 2. PDF Engine (wkhtmltopdf)

Skrip ini membutuhkan *engine* eksternal untuk merender HTML menjadi PDF.

1. Unduh dan instal [wkhtmltopdf](https://wkhtmltopdf.org/downloads.html) untuk Windows.
2. Pastikan direktori instalasi sesuai dengan *path* di dalam skrip (biasanya di `C:\Program Files\wkhtmltopdf\bin\wkhtmltopdf.exe`).

## 📂 Struktur Direktori Lokal

Skrip mengasumsikan struktur folder di direktori lokal Anda (misal: `D:\`) sebagai berikut:

```text
D:\Skripsi\03_Data_Hasil\Titik Panas (Hotspot)\
├── Hotspot Clean Jambi\
│   ├── Hotspot_2010_03_Gi.shp      <-- (Input Shapefile per tahun)
│   ├── Hotspot_2011_03_Gi.shp
│   └── ...
└── Morans Index\                   <-- (Folder Output: Auto-generated)
    ├── Moran's - 2010 - Keseluruhan.pdf
    ├── Moran's - 2010 - Hotspot.pdf
    └── Rekapitulasi_Indeks_Moran_2010_2020.xlsx

```

## Cara Penggunaan

1. Buka **ArcGIS Pro**.
2. Buka antarmuka Jupyter Notebook melalui menu *Analysis > Python Notebook*.
3. Muat file `Spatial_Autocorrelation_Jambi_2010_2020.ipynb`.
4. Sesuaikan variabel `base_dir` jika lokasi penyimpanan data Anda berbeda.
5. Jalankan seluruh sel (*Run All*).

## Penulis

**Jariyan Arifudin** Mahasiswa Geografi Lingkungan

Universitas Gadjah Mada (UGM)

## Lisensi & Sitasi

Kode ini didistribusikan di bawah **MIT License**.
Jika Anda menggunakan metode ini untuk penelitian, silakan sitasi repositori ini:

> Arifudin, J. (2026). *Analisis Autokorelasi Spasial (Global Moran's I) dengan ArcPy*. GitHub Repository.
