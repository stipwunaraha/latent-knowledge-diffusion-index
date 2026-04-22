<!-- latent-knowledge-diffusion-index/README.md -->

# 👻 L-KDI: Latent Knowledge Diffusion Index

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.9+](https://img.shields.io/badge/python-3.9+-blue.svg)](https://www.python.org/downloads/)
[![NetworkX](https://img.shields.io/badge/NetworkX-3.0+-green.svg)](https://networkx.org/)

> *"Melacak hantu ide: Ketika pemikiran dari masa lalu tiba-tiba menjadi solusi masa depan."*

**L-KDI** adalah algoritma untuk mendeteksi **Revival Impact Factor (RIF)**—fenomena ketika sebuah ide dari disertasi doktoral tahun 1970-an tiba-tiba muncul kembali sebagai solusi utama untuk masalah AI modern. Kita menyebutnya "hantu" ide, dan proyek ini melacaknya di korpus teks ilmiah yang sangat besar.

### 💡 Ide Utama
Banyak terobosan ilmiah yang sebenarnya merupakan *rediscovery* dari konsep lama. Contoh klasik: *Backpropagation* dan *Convolutional Neural Networks* sudah ada sejak puluhan tahun sebelum menjadi dominan. Metrik saat ini tidak menghargai *delayed impact* ini.

L-KDI mengukur "jarak difusi" (`diffusion distance`) dan "waktu latensi" (`latency time`) dengan:
1.  **Diffusion Meme Score**: Mengevaluasi jarak difusi pengetahuan dalam jaringan sitasi makalah menggunakan *network embedding space*.
2.  **Knowledge Diffusion Breakthrough**: Mengukur seberapa besar sebuah karya mendobrak batasan bidang ilmunya.

### 📐 Metodologi

Kami mengusulkan tiga komponen utama:

1.  **Pembangkit Graf Sitasi Temporal**: Membangun jaringan sitasi dengan bobot berdasarkan waktu dan kesamaan konten.
2.  **Kalkulasi "Jarak Difusi"**: Menggunakan *random walk with restart* atau metrik berbasis *embedding* untuk mengukur seberapa jauh sebuah konsep bergerak melintasi ruang dan waktu.
3.  **Skor RIF (Revival Impact Factor)**: Formula untuk mengkuantifikasi lonjakan perhatian setelah periode dormansi panjang.

```python
# Pseudocode konsep L-KDI
def calculate_rif(paper):
    # 1. Dapatkan semua sitasi ke paper ini, kelompokkan per tahun
    citation_timeline = get_citations_per_year(paper)
    
    # 2. Deteksi "periode dormansi" (min 10 tahun tanpa sitasi signifikan)
    dormant_start, dormant_end = detect_dormancy(citation_timeline)
    
    # 3. Jika ada lonjakan sitasi > threshold setelah dormansi
    if has_revival_spike(citation_timeline, dormant_end):
        # 4. Hitung RIF = (Tinggi Lonjakan) * (Faktor Kelangkaan)
        return spike_magnitude * rarity_factor
    
    return 0.0
```

### 📦 Instalasi & Penggunaan

```bash
git clone https://github.com/stipwunaraha/latent-knowledge-diffusion-index.git
cd latent-knowledge-diffusion-index
pip install -r requirements.txt
```

**Contoh:** Menganalisis "hantu" ide *Backpropagation*:

```python
from lkdi import RevivalDetector

detector = RevivalDetector(data_source="openalex")

# Analisis makalah seminal Rumelhart et al. (1986)
result = detector.analyze(doi="10.1038/323533a0")

print(f"Revival Impact Factor (RIF): {result.rif_score}")
print(f"Periode Dormansi: {result.dormant_period}")
print(f"Konsep yang di-revive: {result.key_concepts}")
```

### 🚧 Roadmap
- [ ] Implementasi *graph builder* dari OpenAlex.
- [ ] Algoritma deteksi dormansi berbasis statistik.
- [ ] Visualisasi *timeline* kebangkitan ide (streamlit).
- [ ] Studi kasus: *Attention Mechanism* (dari Bahdanau 2014 ke Transformer 2017).

### 🤝 Kontribusi
Lihat [Issues](https://github.com/stipwunaraha/latent-knowledge-diffusion-index/issues) untuk tugas-tugas yang bisa dikerjakan.

### 📄 Lisensi
MIT License.
