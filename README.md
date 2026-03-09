Digital
### dengan Algoritma Naïve Bayes Classifier

![Python](https://img.shields.io/badge/Python-3.x-blue?style=flat-square&logo=python)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-MultinomialNB-orange?style=flat-square&logo=scikit-learn)
![Accuracy](https://img.shields.io/badge/Accuracy-84.6%25-brightgreen?style=flat-square)
![License](https://img.shields.io/badge/License-MIT-lightgrey?style=flat-square)

> Skripsi Program Studi Informatika — Universitas Teknologi Digital Indonesia (UTDI), Yogyakarta  
> **Reinardus Guesta Derazio** — NIM 245410096

---

## 📋 Deskripsi

Penelitian ini membangun sistem klasifikasi sentimen otomatis untuk mendeteksi dampak konten digital berbahasa Indonesia, khususnya konten yang berpotensi membahayakan anak di bawah umur. Model menggunakan algoritma **Naïve Bayes Classifier** yang dikombinasikan dengan metode ekstraksi fitur **TF-IDF** untuk mengklasifikasikan teks ke dalam tiga kategori sentimen:

| Kelas | Deskripsi | Proporsi Dataset |
|-------|-----------|-----------------|
| 🔴 **Negatif** | Konten toksik, cyberbullying, hoaks | 38% (1.877 data) |
| 🟢 **Positif** | Konten edukatif, bermanfaat, aman | 35% (1.729 data) |
| 🟡 **Netral** | Konten informatif tanpa muatan emosi | 27% (1.335 data) |

---

## 📁 Struktur Repository

```
📦 analisis-sentimen-konten-digital
 ┣ 📂 demo
 ┃ ┗ 📄 demo_sentimen.html       # Demo interaktif berbasis browser
 ┣ 📂 notebook
 ┃ ┗ 📓 sentiment_analysis.ipynb # Notebook Google Colaboratory
 ┣ 📂 data
 ┃ ┗ 📄 dataset_info.md          # Info dataset (sumber: Kaggle)
 ┣ 📄 README.md
 ┗ 📄 requirements.txt
```

---

## ⚙️ Pipeline Sistem

```
Input Teks
    │
    ▼
┌─────────────────────┐
│   Text Preprocessing │
│  ① Case Folding      │  → huruf kecil semua
│  ② Tokenizing        │  → pisahkan per kata
│  ③ Stopword Removal  │  → hapus kata tidak bermakna
│  ④ Stemming (ECS)    │  → bentuk dasar kata (Sastrawi)
└─────────┬───────────┘
          │
          ▼
┌─────────────────────┐
│   Ekstraksi Fitur    │
│   TF-IDF Vectorizer  │  → max_features = 5.000
└─────────┬───────────┘
          │
          ▼
┌─────────────────────┐
│  Naïve Bayes (MNB)  │  → MultinomialNB (Scikit-learn)
└─────────┬───────────┘
          │
          ▼
   Sentimen: Positif / Negatif / Netral
```

---

## 📊 Hasil Evaluasi Model

| Kelas | Precision | Recall | F1-Score | Support |
|-------|-----------|--------|----------|---------|
| Negatif | 0.85 | 0.86 | 0.85 | 376 |
| Positif | 0.86 | 0.87 | 0.87 | 346 |
| Netral  | 0.78 | 0.79 | 0.79 | 267 |
| **Macro Avg** | **0.83** | **0.84** | **0.84** | **989** |

**Akurasi Keseluruhan: 84.6%** (836/989 data uji benar)

---

## 🚀 Cara Menjalankan

### 1. Clone Repository
```bash
git clone https://github.com/username/analisis-sentimen-konten-digital.git
cd analisis-sentimen-konten-digital
```

### 2. Install Dependencies
```bash
pip install -r requirements.txt
```

### 3. Jalankan di Google Colaboratory
Buka file `notebook/sentiment_analysis.ipynb` di [Google Colab](https://colab.research.google.com) atau klik badge berikut:

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/username/analisis-sentimen-konten-digital/blob/main/notebook/sentiment_analysis.ipynb)

### 4. Jalankan Demo Interaktif
Buka file `demo/demo_sentimen.html` langsung di browser — tidak perlu instalasi apapun.

---

## 🛠️ Tech Stack

| Komponen | Library / Tool |
|----------|---------------|
| Bahasa Pemrograman | Python 3.x |
| Environment | Google Colaboratory |
| Preprocessing | `NLTK`, `Sastrawi` |
| Ekstraksi Fitur | `Scikit-learn` TfidfVectorizer |
| Model | `Scikit-learn` MultinomialNB |
| Visualisasi | `Matplotlib`, `Seaborn` |
| Data Processing | `Pandas`, `NumPy` |

---

## 📦 Requirements

```txt
pandas>=1.3.0
numpy>=1.21.0
scikit-learn>=0.24.0
nltk>=3.6.0
PySastrawi>=1.2.0
matplotlib>=3.4.0
seaborn>=0.11.0
```

---

## 📂 Dataset

- **Sumber:** [Indonesian Sentiment Analysis Dataset — Kaggle](https://www.kaggle.com)
- **Jumlah awal:** 5.000 baris
- **Setelah pembersihan:** 4.941 baris (47 duplikat + 12 kosong dihapus)
- **Atribut:** `text` (komentar teks), `label` (positif/negatif/netral)
- **Split:** 80% data latih (3.952) / 20% data uji (989)

---

## 🔑 Contoh Penggunaan (Python)

```python
from sklearn.naive_bayes import MultinomialNB
from sklearn.feature_extraction.text import TfidfVectorizer
from sklearn.model_selection import train_test_split
from sklearn.metrics import classification_report, accuracy_score
import pandas as pd

# Load dataset
df = pd.read_csv('data/dataset.csv')

# Split data
X_train, X_test, y_train, y_test = train_test_split(
    df['text_clean'], df['label'],
    test_size=0.2, random_state=42
)

# Ekstraksi fitur TF-IDF
vectorizer = TfidfVectorizer(max_features=5000)
X_train_vec = vectorizer.fit_transform(X_train)
X_test_vec  = vectorizer.transform(X_test)

# Training model
model = MultinomialNB()
model.fit(X_train_vec, y_train)

# Evaluasi
y_pred = model.predict(X_test_vec)
print(f"Accuracy: {accuracy_score(y_test, y_pred):.4f}")
print(classification_report(y_test, y_pred))

# Prediksi teks baru
def predict_sentiment(text):
    vec = vectorizer.transform([text])
    return model.predict(vec)[0]

print(predict_sentiment("Konten ini sangat edukatif dan bermanfaat!"))
# Output: positif
```

---

## 📌 Temuan Utama

- Model **Naïve Bayes + TF-IDF** efektif untuk klasifikasi sentimen bahasa Indonesia informal
- **38% konten** bersentimen negatif → mengkonfirmasi urgensi sistem deteksi otomatis
- Recall kelas **netral (79.3%)** lebih rendah dibanding negatif (86.2%) dan positif (87.5%) — karena komentar netral bersifat ambigu
- Tahap **preprocessing** signifikan mengurangi rata-rata token dari **18 → 9 token** per kalimat

---

## 🔭 Pengembangan Lanjutan

- [ ] Implementasi **IndoBERT** untuk meningkatkan recall kelas netral
- [ ] Perluasan dataset dari Instagram, TikTok, Twitter/X
- [ ] Deployment antarmuka web menggunakan **Flask** atau **Streamlit**
- [ ] Klasifikasi **multi-label** (cyberbullying, hoaks, konten toksik)

---

## 👤 Author

**Reinardus Guesta Derazio**  
Program Studi Informatika — Universitas Teknologi Digital Indonesia  
📧 NIM: 245410096

---

## 📄 Lisensi

Proyek ini dibuat untuk keperluan akademik. Bebas digunakan sebagai referensi dengan menyertakan atribusi yang sesuai.
