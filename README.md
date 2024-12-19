# Evaluasi Model CLIP pada Klasifikasi Gambar-Teks

## Deskripsi Proyek
Proyek ini mengimplementasikan dan mengevaluasi performa model multimodal CLIP dalam klasifikasi gambar-teks, khususnya untuk spesies, perilaku, lokasi, dan waktu hewan ternak. Evaluasi dilakukan pada empat varian model CLIP:
- RN50 (ResNet-50)
- ViT-B/16 (Vision Transformer - Base, Patch 16)
- ViT-B/32 (Vision Transformer - Base, Patch 32)
- ViT-L/14 (Vision Transformer - Large, Patch 14)

Studi ini menggunakan pendekatan zero-shot learning, di mana model tidak dilatih secara eksplisit pada domain ternak. Prediksi dilakukan dengan menghitung kesamaan kosinus antara fitur gambar dan teks deskripsi.

## Tujuan
Proyek bertujuan untuk:
1. Mengevaluasi performa model CLIP pada klasifikasi gambar-teks di kategori spesies, perilaku, lokasi, dan waktu.
2. Membandingkan keakuratan keempat varian model CLIP.
3. Mengidentifikasi kekuatan dan kelemahan masing-masing model dalam klasifikasi berbasis gambar-teks.

## Dataset
Dataset terdiri dari 279 gambar ternak yang mewakili tiga spesies:
- **Sapi** (cow): 71 gambar
- **Kambing** (goat): 92 gambar
- **Domba** (sheep): 116 gambar

### Augmentasi Gambar
Agar lebih bervariasi, dataset diproses dengan teknik augmentasi:
- **Rotasi acak**: -30 hingga +30 derajat.
- **Penyesuaian kecerahan dan kontras**: Rentang 0.5 hingga 1.5.
- **Horizontal flipping**: Membalik gambar secara horizontal.

## Implementasi
### Arsitektur CLIP
Model CLIP terdiri dari dua encoder:
1. **Encoder Gambar**: Menggunakan ResNet atau Vision Transformer untuk menghasilkan representasi visual gambar.
2. **Encoder Teks**: Memanfaatkan arsitektur Transformer untuk menghasilkan representasi teks deskripsi.

### Kombinasi Teks untuk Prediksi
Kombinasi teks dibuat dari empat kategori:
- **Spesies (animals)**: cow, goat, sheep.
- **Perilaku (behaviors)**: eating, moving, resting.
- **Lokasi (places)**: in the field, on the hill, in the forest.
- **Waktu (times)**: day, night.

### Proses Prediksi
1. Gambar dan teks diubah menjadi vektor numerik oleh encoder CLIP.
2. Kesamaan kosinus dihitung untuk membandingkan kemiripan antara gambar dan teks.
3. Prediksi dengan nilai kesamaan tertinggi dipilih sebagai hasil akhir.

## Hasil Evaluasi
### Akurasi Model
| Model     | Spesies (%) | Perilaku (%) | Lokasi (%) | Waktu (%) |
|-----------|-------------|--------------|------------|-----------|
| **RN50**  | 77          | 52           | 62         | 33        |
| **ViT-B/16** | 79       | 57           | 66         | 72        |
| **ViT-B/32** | 73       | 51           | 68         | 56        |
| **ViT-L/14** | 84       | 73           | 55         | 77        |

## Kesimpulan
- Model **ViT-L/14** memberikan akurasi tertinggi di kategori spesies (84%) dan perilaku (73%).
- Model **ViT-B/16** menunjukkan performa paling seimbang dengan akurasi konsisten di semua kategori.
- Model **RN50** dan **ViT-B/32** unggul di kategori tertentu, namun memiliki kelemahan pada prediksi waktu dan perilaku.

### Rekomendasi
Penelitian ini merekomendasikan:
1. Fine-tuning model CLIP dengan dataset ternak spesifik untuk meningkatkan akurasi.
2. Penggunaan dataset yang lebih besar dan kompleks.
3. Eksplorasi pendekatan few-shot learning untuk meningkatkan performa model pada domain baru.

**Kontributor:**
- Wahyudiyanto
- Nadilla Andhara Putri
- Yunaena Maratul Kirom
- Revaldo Dafa Fahmindo
- Shula Talitha Ardhya Putri
- Ibnu Farhan Al-Ghifari