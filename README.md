# Deteksi Wajah Dan Pengenalan Ekspresi Siswa SD Menggunakan Model Yolov8 Dan Resnet50 Untuk Mengukur Ketertarikan Terhadap Mata Pelajaran

**Bahasa:** [🇮🇩 Bahasa Indonesia](README.md) | [🇺🇸 English](README_en.md)

<p align="center">
  <img src="https://raw.githubusercontent.com/mnatasyar/mnatasyar/main/DemoAplikasi.gif" alt="Demo" width="700"/>
</p>

Proyek ini bertujuan untuk mengembangkan sistem berbasis kecerdasan buatan yang mampu mendeteksi wajah dan mengenali ekspresi emosional siswa Sekolah Dasar (SD) menggunakan model **YOLOv8** untuk deteksi wajah dan **ResNet50** untuk pengenalan ekspresi melalui gambar atau video yang diunggah. Sistem ini digunakan untuk membantu guru dalam mengevaluasi tingkat ketertarikan siswa terhadap mata pelajaran yang sedang diajarkan.

---

## Daftar isi

- [Fitur Utama](#fitur-utama)
- [Struktur Proyek](#struktur-proyek)
- [Teknologi yang Digunakan](#teknologi-yang-digunakan)
- [Cara Menjalankan Proyek Secara Lokal](#cara-menjalankan-proyek-secara-lokal)
  - [1. Frontend](#1-frontend)
  - [2. Backend](#2-backend)
- [Hasil Akhir Proyek](#hasil-akhir-proyek)

---

## Fitur Utama

Sistem ini terdiri dari frontend (antarmuka pengguna) dan backend (pemrosesan data & model Deep Learning) yang saling terintegrasi untuk mendeteksi wajah dan mengenali ekspresi siswa. Berikut adalah fitur-fitur utamanya:

- **Deteksi Wajah:** Menerapkan model YOLOv8 yang telah dilatih khusus untuk mendeteksi wajah siswa SD
- **Pengenalan Ekspresi:** Menerapkan model ResNet50 yang telah dilatih untuk mengklasifikasikan ekspresi menjadi tiga kategori tingkat ketertarikan yaitu tertarik, netral dan tidak tertarik.
- **Dukungan Inputan:** Pengolahan data inputan yang dapat menerima berupa inputan foto atau video pada satu form yang sama dan dideteksi oleh sistem
- **Integrasi API:** Menyediakan endpoint melalui FastAPI yang digunakan untuk menerima frame, memproses deteksi wajah & tingkat ketertarikan, lalu mengirimkan hasil ke frontend.
- **Fitur Analisis Mendalam:** Memberikan informasi secara menyeluruh dari hasil yang telah dianalisis
- **Optimasi secara menyeluruh:** Sistem dirancang menggunakan dua model yang digunakan untuk memberikan performa optimal terhadap penggunaan CPU dan GPU.

## Struktur Proyek

```
Tugas_Akhir/
├── frontend/
│ ├── public/
│ ├── src/
│ └── ...
├── backend/
│ ├── app/
│ ├── model/
│ ├── output-video/
│ ├── tmp/
│ └── requirements.txt
├── README.md
└── README_en.md
```

## Teknologi yang Digunakan

### Frontend

Bagian frontend dibangun menggunakan library javascript yaitu **React** dengan dukungan **TailwindCSS** untuk styling yang responsif dan **Axios** untuk komunikasi API dengan backend. Antarmuka ini dirancang agar sederhana, intuituf, dan dapat digunakan oleh setiap orang terutama dan terkhusus oleh guru ataupun tenaga pengajar tanpa membutuhkan keahlian teknis yang mendalam.

### Backend

Bagian backend menggunakan **Python** sebagai bahasa pemrograman utama yang dibangun menggunakan **FastAPI** sebagai kerangka kerja utama dengan dukungan **OpenCV** untuk pengolahan citra/video. Backend ini berperan menerima frame dari frontend, menjalankan model **YOLOv8** (deteksi wajah) dan **ResNet50** (pengenalan ekspresi), lalu mengembalikan hasil deteksi ke frontend.

## Alur Kerja Sistem

1. User mengunggah gambar/video melalui antarmuka web.

2. Frontend mengirim file ke backend melalui API.

3. Backend memproses file:
   - Deteksi wajah dengan YOLOv8
   - Pengenalan ekspresi dengan ResNet50
4. Hasil dikembalikan ke frontend:
   - Gambar/video dengan anotasi bounding box & label
   - Statistik tingkat ketertarikan

## Cara Menjalankan Proyek Secara Lokal

Ikuti langkah-langkah ini secara berurutan untuk menyiapkan dan menjalankan keseluruhan proyek dari awal di komputer lokal kita.

### Prasyarat

- Node.js
- Python 3.10+
- Git

### Clone Repository

Jalankan perintah berikut untuk menyalin repository ini ke komputer lokal:

```
git clone https://github.com/mnatasyar/Tugas_Akhir.git
cd Tugas_Akhir
```

### 1. Frontend

> [!TIP]
> 💡 Ingin langsung mencoba tanpa instalasi lokal?  
> Gunakan versi online di sini: [ai.mnatasyar.com](https://ai.mnatasyar.com)
> Kami menyediakan secara terbatas untuk frontend saja, dan untuk backend hanya dapat diakses secara lokal saja ya!!!

```
# 1. Arahkan ke direktori pengembangan front end utama
cd frontend

# 2. Instal seluruh dependensi/library yang dibutuhkan
npm install

# 3. Jalankan server front end secara lokal
npm run dev
```

Aplikasi akan berjalan di alamat default:

```
http://localhost:5173
```

### 2. Backend

**Langkah 1: Persiapan Lingkungan**

Pertama, membuka tab/terminal baru yang berada di direktori root proyek **Tugas_Akhir** (bukan di dalam folder frontend).

```
# 1. Masuk ke direktori pengembangan backend
cd backend

# [Opsional] 2. Buat virtual environment (boleh venv/conda)
# contoh disini kita menggunakan venv
python -m venv venv
venv\Scripts\activate

# 3. Install semua dependesi backend yang dibutuhkan
pip install -r requirements.txt
```

**Langkah 2: Unduh Model**

Model YOLOv8 dan ResNet50 tidak termasuk dalam repositori ini dikarenakan kebijakan Git/Github untuk penyimpanan file yang terlalu besar tidak diperbolehkan. Jadi dapat diunduh secara mnual melalui tautan berikut:

#### 1. **Buat folder model** jika belum ada:

- `backend/model/`

#### 2. **Unduh file** dan letakkan di folder:

- **File:** `best.pt`

  - **Link Unduh:** https://drive.google.com/file/d/1GDi7h0_C4_BqWuBh4gWlS30CahQ7EsZH/view?usp=sharing
  - **Lokasi:** `backend/models/best.pt`

- **File:** `resnet50v2_finetuned_tingkat_ketertarikan.h5`
  - **Link Unduh:** https://drive.google.com/file/d/1hxz-XOdy39ZvUj33uDoQ5ezn5ruTk_Ca/view?usp=sharing
  - **Lokasi:** `backend/models/resnet50v2_finetuned_tingkat_ketertarikan.h5`

Setelah diunduh, simpan file model di direktori berikut:

```
Tugas_Akhir/
└── backend/
    └── model/
        ├── best.pt
        └── resnet50v2_finetuned_tingkat_ketertarikan.h5
```

**Langkah 3: Menjalankan Server Backend**

Jalankan perintah berikut untuk memulai server backend:

```
# Jika membuka file melalui folder backend
uvicorn app.main:app --reload --host 0.0.0.0 --port=8000

# Jika membuka file melalui folder utama
uvicorn backend.app.main:app --reload --host 0.0.0.0 --port 8000
```

Server backend akan berjalan di:

```
http://localhost:8000
```

> [!NOTE]
> dapat sesuaikan server dan port yang digunakan pada frontend di bagian `src/lib/constants.js` sesuai yang dijalankan pada sisi backend untuk dapat terhubung dengan frontend

## Hasil Akhir Proyek

Proyek ini menghasilkan sebuah sistem deteksi wajah dan pengenalan ekspresi siswa SD yang mampu menganalisis tingkat ketertarikan siswa terhadap mata pelajaran berdasarkan input berupa gambar atau video.

Secara keseluruhan, sistem dapat:

1. Mendeteksi wajah siswa dari media yang diunggah menggunakan model YOLOv8.
2. Mengklasifikasikan ekspresi wajah menjadi tiga kategori tingkat ketertarikan (Tertarik, Netral, dan Tidak Tertarik) menggunakan model ResNet50 yang telah di-fine-tune.
3. Menyajikan hasil analisis dalam bentuk visualisasi dan informasi deskriptif melalui antarmuka web yang sederhana, intuitif, dan ramah bagi pengguna non-teknis seperti guru atau tenaga pengajar.
4. Memproses input secara offline/lokal untuk backend, dengan frontend yang dapat diakses secara online maupun lokal.
