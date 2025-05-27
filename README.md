# 🎧 Spotify Tracks Recommender & EDA

![Spotify Logo](https://upload.wikimedia.org/wikipedia/commons/2/26/Spotify_logo_with_text.svg)

A music recommendation and analysis project built using the **Spotify Tracks Dataset** hosted on Hugging Face.  
We explore musical attributes, genres, and popularity while also building a powerful **semantic recommendation engine** using Sentence Transformers and FAISS.

---

## 🚀 Tech Stack

| Tool / Library | Badge |
|----------------|-------|
| `Python` | ![Python](https://img.shields.io/badge/Python-3670A0?logo=python&logoColor=ffDD54) |
| `Pandas` | ![Pandas](https://img.shields.io/badge/Pandas-150458?logo=pandas&logoColor=white) |
| `NumPy` | ![NumPy](https://img.shields.io/badge/NumPy-013243?logo=numpy&logoColor=white) |
| `Seaborn` | ![Seaborn](https://img.shields.io/badge/Seaborn-1485C7?logo=seaborn&logoColor=white) |
| `Matplotlib` | ![Matplotlib](https://img.shields.io/badge/Matplotlib-000000?logo=matplotlib&logoColor=white) |
| `SentenceTransformers` | ![SentenceTransformers](https://img.shields.io/badge/SBERT-4B8BBE?logo=python&logoColor=white) |
| `FAISS` | ![FAISS](https://img.shields.io/badge/Faiss-000000?logo=faiss&logoColor=white) |
| `Scikit-Learn` | ![Scikit-learn](https://img.shields.io/badge/Scikit--Learn-F7931E?logo=scikit-learn&logoColor=white) |

---

## 📁 Dataset

- **Source**: [Hugging Face – maharshipandya/spotify-tracks-dataset](https://huggingface.co/datasets/maharshipandya/spotify-tracks-dataset)
- **Contents**:  
  - ~160K tracks  
  - Audio features (e.g. acousticness, energy, valence, tempo)  
  - Artist metadata, track names, release years  
- **Format**: `.csv` format loaded via `datasets` or `pandas`

---

## 🧪 Main Features

- 📊 **In-depth EDA** on audio and genre attributes
- 🧠 **Semantic Recommendations** using:
  - `SentenceTransformer` for query embedding
  - `FAISS` for fast similarity search in high-dimensional space
- 📅 Year-wise analysis, genre trends, and feature correlations

---

## 💡 Example Usage

```python

# Recommend using full song title and artist
recommend_songs("Hawayein", ["Arijit Singh"])

# Or just the song name
recommend_songs("At My Worst")
````

---

## Demo Output

```text
best match: 'hawayein by pritam, arijit singh'

Recommendations for 'Hawayein' by Arijit Singh:
1. 'daayre' by ['pritam', 'arijit singh']
2. 'shaayraana' by ['pritam', 'arijit singh']
3. 'hawayein - lofi flip' by ['vibie', 'arijit singh', 'pritam']
4. 'lehra do' by ['pritam', 'arijit singh']
5. 'kabira' by ['pritam', 'harshdeep kaur', 'arijit singh']

Found multiple songs. Selecting most popular: 'at my worst by pink sweat'

Recommendations for 'at my worst':
1. 'at my worst' by ['pink sweat', 'nikhita gandhi']
2. 'at my worst' by ['pink sweat', 'gustixa']
3. 'in your arms' by ['saib']
4. 'felt' by ['nate traveller']
5. 'better with you' by ['gentle bones', 'benjamin kheng']
```

**Built with ❤️ for music lovers & data explorers**
