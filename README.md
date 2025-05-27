# 🎧 Spotify Tracks Recommender & Exploratory Data Analysis (EDA)

![Spotify Logo](https://upload.wikimedia.org/wikipedia/commons/2/26/Spotify_logo_with_text.svg)

Welcome to the **Spotify Tracks Recommender & EDA** project! This notebook blends **data exploration**, **audio analysis**, and **semantic search** to help users discover similar tracks using song metadata and **natural language-based search**.

Leveraging the power of **Sentence Transformers** and **FAISS**, this project enables fast, content-aware music recommendations — going beyond just genres or popularity.

---

## 🚀 Tech Stack

| Tool / Library        | Badge |
|-----------------------|-------|
| `Python`              | ![Python](https://img.shields.io/badge/Python-3670A0?logo=python&logoColor=ffDD54) |
| `Pandas`              | ![Pandas](https://img.shields.io/badge/Pandas-150458?logo=pandas&logoColor=white) |
| `NumPy`               | ![NumPy](https://img.shields.io/badge/NumPy-013243?logo=numpy&logoColor=white) |
| `Seaborn`             | ![Seaborn](https://img.shields.io/badge/Seaborn-1485C7?logo=seaborn&logoColor=white) |
| `Matplotlib`          | ![Matplotlib](https://img.shields.io/badge/Matplotlib-000000?logo=matplotlib&logoColor=white) |
| `Scikit-Learn`        | ![Scikit-learn](https://img.shields.io/badge/Scikit--Learn-F7931E?logo=scikit-learn&logoColor=white) |
| `SentenceTransformers`| ![SBERT](https://img.shields.io/badge/SBERT-4B8BBE?logo=python&logoColor=white) |
| `FAISS`               | ![FAISS](https://img.shields.io/badge/Faiss-000000?logo=faiss&logoColor=white) |

---

## 📁 Dataset Overview

- **Source**: [maharshipandya/spotify-tracks-dataset](https://huggingface.co/datasets/maharshipandya/spotify-tracks-dataset) on Hugging Face 🤗
- **Size**: ~160,000 unique tracks
- **Format**: CSV
- **Attributes**:
  - Track metadata (name, artist, duration, year)
  - Audio features (acousticness, danceability, energy, tempo, valence, etc.)
  - Genre & popularity indicators
  - Explicit content & release metadata

---

## ✨ Project Features

### 🎧 Music Recommender System
- A **content-aware, hybrid song recommendation engine**.
- Takes a query in the form of **song title + optional artist list**.
- Uses **Sentence-BERT embeddings** + **FAISS vector similarity search**.
- Retrieves songs that are semantically or contextually similar.

### 📊 Exploratory Data Analysis (EDA)
- **Genre-based** trends
- **Audio features** based trends
- Visualizations using **Seaborn**, **Matplotlib**, and **heatmaps**

### 📦 Modularity
- Designed with clean separation of concerns:
  - `data_preprocessing.py`: cleans and normalizes dataset
  - `embed_tracks.py`: generates sentence embeddings
  - `build_index.py`: builds FAISS index
  - `recommend.py`: handles querying and result fetching

---

## 🧠 Recommender System Architecture

```text
+----------------+        +------------------+        +-------------------------+
| User Input     | --->   | Sentence-BERT    | --->   | Query Embedding (384  text embeddings + 113 musical feature embeddings) |
+----------------+        +------------------+        +-------------------------+
                                                             |
                                                             V
                                                 +--------------------------+
                                                 |  FAISS Similarity Search |
                                                 +--------------------------+
                                                             |
                                                             V
                                                +---------------------------+
                                                | Top-k Song Recommendations|
                                                +---------------------------+
````

---

## 💡 How to Use

```python
# Example 1: With both song name and artist
recommend_songs("Hawayein", ["Arijit Singh"])

# Example 2: With only song name (uses popularity to disambiguate)
recommend_songs("At My Worst")
```

---

## 📈 Sample Output

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

---

## 🧪 Performance & Limitations

* ⚡️ **FAISS** ensures fast <1ms retrieval on large vectors.
* 🔍 Query matching works best with correct song names.
* 🎤 Works even if artist names are partially incorrect or missing.
* ⚠️ Can struggle with very rare or misspelled queries (future fix: fuzzy match).


### 🎶 Built with ❤️ by a music lover & ML enthusiast

