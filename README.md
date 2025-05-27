# Music Recommender System

# ![Spotify Logo](https://upload.wikimedia.org/wikipedia/commons/2/26/Spotify_logo_with_text.svg)

A comprehensive music recommendation system built using Spotify's dataset, leveraging advanced data processing, exploratory data analysis, and machine learning techniques to recommend tracks based on various audio features and artist profiles.

---

## Tech Stack

Here are the main technologies and libraries used in this project, represented by their logos:

| Technology        | Logo                                                                                      |
|-------------------|-------------------------------------------------------------------------------------------|
| Python            | ![Python](https://www.python.org/static/community_logos/python-logo.png)                 |
| NumPy             | ![NumPy](https://numpy.org/images/logo.svg)                                              |
| Pandas            | ![Pandas](https://pandas.pydata.org/static/img/pandas_mark.svg)                          |
| Matplotlib        | ![Matplotlib](https://matplotlib.org/_static/images/logo2.svg)                           |
| Seaborn           | ![Seaborn](https://seaborn.pydata.org/_static/logo-wide-lightbg.svg)                     |
| scikit-learn      | ![scikit-learn](https://scikit-learn.org/stable/_static/scikit-learn-logo-small.png)     |
| SentenceTransformers | ![SentenceTransformers](https://www.sbert.net/img/logo.png)                             |
| FAISS             | ![FAISS](https://faiss.ai/img/faiss_logo.png)                                           |

---

## Project Overview

This project involves:

- Loading and cleaning a large Spotify tracks dataset.
- Preprocessing textual data (e.g., track names, artist names) by normalizing case and removing non-English characters.
- Handling missing values and duplicates.
- Exploratory Data Analysis (EDA) on track popularity, artist statistics, audio features (danceability, energy, valence, etc.), and genre distributions.
- Visualizing data using bar charts, histograms, boxplots, radar charts, and heatmaps.
- Implementing similarity measures using cosine similarity and vector embeddings for music recommendation.

---

## Dataset

- The dataset consists of Spotify tracks with features such as track name, artists, duration, popularity, explicit content flag, audio features (danceability, energy, liveness, valence), musical key and mode, loudness, tempo, and genre.
- Data cleaning steps include dropping nulls, removing duplicates, and splitting artist strings into lists.

---

## Usage

1. Clone the repository.
2. Install dependencies using pip:

