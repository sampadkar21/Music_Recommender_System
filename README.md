````markdown
<!-- PROJECT TITLE WITH SPOTIFY LOGO -->
<p align="center">
  <img src="https://upload.wikimedia.org/wikipedia/commons/2/26/Spotify_logo_with_text.svg" alt="Spotify Logo" width="300"/>
</p>

# Spotify Tracks Recommender & EDA  

A full exploratory analysis of the [Spotify Tracks Dataset](https://www.kaggle.com/datasets/zaheenhamidani/ultimate-spotify-tracks-db) combined with a semantic-embedding based recommendation engine.

---

## 🚀 Tech Stack

<p align="center">
  <a href="https://www.python.org/">
    <img src="https://img.shields.io/badge/Python-3670A0?logo=python&logoColor=ffDD54" alt="Python"/>
  </a>
  <a href="https://pytorch.org/">
    <img src="https://img.shields.io/badge/PyTorch-EE4C2C?logo=pytorch&logoColor=white" alt="PyTorch"/>
  </a>
  <a href="https://pandas.pydata.org/">
    <img src="https://img.shields.io/badge/Pandas-150458?logo=pandas&logoColor=white" alt="Pandas"/>
  </a>
  <a href="https://numpy.org/">
    <img src="https://img.shields.io/badge/NumPy-013243?logo=numpy&logoColor=white" alt="NumPy"/>
  </a>
  <a href="https://github.com/facebookresearch/faiss">
    <img src="https://img.shields.io/badge/Faiss-000000?logo=faiss&logoColor=white" alt="Faiss"/>
  </a>
  <a href="https://jupyter.org/">
    <img src="https://img.shields.io/badge/Jupyter-F37626?logo=jupyter&logoColor=white" alt="Jupyter"/>
  </a>
</p>

---

## 📁 Dataset

- **Source**: Kaggle – Ultimate Spotify Tracks DB  
- **Contents**: Track metadata, audio features, popularity, and embeddings  
- **Size**: ~180k tracks (1.2 GB)

---

## ⚙️ Installation

```bash
git clone https://github.com/yourusername/spotify-track-recommender.git
cd spotify-track-recommender
conda create -n spotify_rec python=3.9
conda activate spotify_rec
pip install -r requirements.txt
````

---

## 🛠️ Usage

1. **Load & preprocess**

   ```bash
   python src/data_preprocessing.py --input data/raw/spotify.csv \
                                    --output data/processed/spotify_cleaned.csv
   ```
2. **Generate embeddings**

   ```bash
   python src/embed_tracks.py --model-id sentence-transformers/all-MiniLM-L6-v2 \
                              --input data/processed/spotify_cleaned.csv \
                              --output data/embeddings/song_embeds.npy
   ```
3. **Build FAISS index**

   ```bash
   python src/build_index.py --embeds data/embeddings/song_embeds.npy \
                             --index data/index/faiss.index
   ```
4. **Run recommendation demo**

   ```bash
   python src/recommend.py
   ```

---

## 📊 EDA Highlights

* **Popularity vs. Danceability**: More popular tracks trend toward higher danceability
* **Genre Distribution**: Pop, Hip-Hop, and Rock dominate the top 10% popularity
* **Temporal Trends**: Increase in acoustic-style songs since 2018

*(Full Jupyter notebooks in `notebooks/eda`)*

---

## 💡 Recommendation Engine

We use a two-stage approach:

1. **Semantic embedding**
   Use a Sentence-Transformer to encode `"song by artist"` queries.
2. **K-NN search with FAISS**
   Retrieve the top–k most similar items in embedding space.

```python
from src.recommend import recommend_songs

# Single argument (song only)
recommend_songs("At My Worst")

# Song + artist hint
recommend_songs("Hawayein", ["Arijit Singh"])
```

---

## 🎬 Demo Output

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

*(Your actual recommendations may vary based on your trained embeddings.)*

---

## 📜 License

This project is licensed under the MIT License – see the [LICENSE](LICENSE) file for details.

---

*Crafted with \:heart: for music lovers & data geeks!*

```
```
