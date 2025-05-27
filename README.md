# Music_Recommender_System

Music Recommender System

Tech Stacks
This project leverages a variety of powerful Python libraries and tools to build a robust music recommender system. Below are the key technologies used, along with their logos:

Python 
NumPy 
Pandas 
Matplotlib 
Seaborn 
Scikit-learn 
Sentence Transformers (No official logo available)
FAISS (No official logo available)

Overview
This music recommender system is built using a dataset of Spotify tracks, available at Spotify Tracks Dataset. It employs machine learning and data processing techniques to recommend songs based on artist similarity and audio features. The system processes track metadata and audio characteristics, generates embeddings using Sentence Transformers, and uses FAISS for efficient similarity searches to provide personalized song recommendations.
The project is structured into five main steps:

Data Loading and Cleaning: Preparing the Spotify dataset for analysis.
Exploratory Data Analysis (EDA): Visualizing data to uncover patterns and insights.
Preprocessing: Transforming features for model compatibility.
Building the Recommendation Model: Creating FAISS indices for similarity search.
Generating Recommendations: Providing song recommendations based on user input.

Project Details
1. Data Loading and Cleaning
The dataset is loaded from a CSV file containing Spotify track information, including track name, artist, album, popularity, duration, explicit content, and audio features like danceability, energy, liveness, and valence. Cleaning steps include:

Removing Missing Values: Dropping rows with null values to ensure data integrity.
Standardizing Strings: Converting string columns (track name, album name, artists) to lowercase for consistency.
Removing Non-English Characters: Using regex to filter out non-English characters and parentheses content.
Dropping Duplicates: Removing duplicate tracks based on track name and artist.
Splitting Artists: Converting the artists column into a list of individual artists.
Converting Duration: Transforming duration_ms from milliseconds to seconds and renaming the column to duration.
Dropping Unnecessary Columns: Removing Unnamed: 0 and track_id columns.

2. Exploratory Data Analysis (EDA)
EDA provides insights into the dataset's characteristics through visualizations created using Matplotlib and Seaborn. Key analyses include:

Popularity Analysis: Bar plots of the top 25 songs by popularity score.
Artist Statistics: Grouping tracks by artist to compute mean popularity and track count, visualized as bar plots.
Bayesian Average Popularity: Calculating a balanced popularity score for artists using a global mean and a prior of 100.
Audio Features Distribution: Histograms and boxplots for features like duration, danceability, energy, liveness, and valence.
Radar Charts: Comparing the top 25 artists' audio features (danceability, energy, liveness, valence) to highlight their musical profiles.
Musical Key and Mode: Heatmaps showing the distribution of musical keys and modes (major/minor) for top artists.
Music Scores: Radar charts for speechiness, acousticness, and instrumentalness, revealing artists' audio signatures.
Loudness and Tempo: Bar plots comparing artists' average loudness and tempo against dataset means.
Genre Analysis: Bar plots of top genres by track and artist count, and a heatmap of genre distribution for top artists.
Time Signature: Bar plots showing the average time signature for top artists, typically 4/4 for most modern music.

These visualizations help understand the dataset's structure and inform feature selection for the recommendation model.
3. Preprocessing
Preprocessing prepares the data for modeling:

Scaling Numerical Features: Using MinMaxScaler to normalize features like loudness, tempo, popularity, and duration to a [0, 1] range.
Encoding Categorical Features: Applying OneHotEncoder to categorical columns (key, time_signature, mode, explicit, track_genre) to create binary features.
Dimensionality Reduction: Reducing the high-dimensional encoded features to 100 components using TruncatedSVD, retaining significant variance.
Generating Embeddings: Using the SentenceTransformer model (all-MiniLM-L6-v2) to create dense vector embeddings for track names and artist names, stored as song_embeds and song_artist_embeds.

4. Building the Recommendation Model
The recommendation model uses FAISS for efficient similarity search:

Artist Similarity: A FAISS IndexHNSWFlat index is built using artist feature vectors (mean values of popularity, danceability, energy, etc.). The get_similar_artists function retrieves the top-k similar artists based on a query artist's features.
Song Similarity: Two FAISS indices are created:
One combining song embeddings (song_embeds) with numerical features.
One combining artist embeddings (song_artist_embeds) with numerical features.


FAISS Configuration: Indices use HNSW (Hierarchical Navigable Small World) graphs with parameters efSearch and efConstruction set for a balance of speed and accuracy.

5. Generating Recommendations
The recommend_songs function provides song recommendations:

Input: A song name and an optional artist name, with k specifying the number of recommendations (default is 5).
Process:
If an artist is provided, it constructs a query string (e.g., "song_name by artist_name"), encodes it, and finds the best matching song using cosine similarity.
If no artist is provided, it selects the most popular song matching the song name.
The function queries the appropriate FAISS index to retrieve the top-k similar songs, excluding the query song.


Output: Prints the best matching song and a list of recommended songs with their artists.

Example usage:
from recommend import recommend_songs
recommend_songs("Hawayein", ["Arijit Singh"])
recommend_songs("at my worst")

Installation
To run this project, ensure Python 3.8+ is installed, along with the required libraries. Install them using pip:
pip install numpy pandas matplotlib seaborn scikit-learn sentence-transformers faiss-cpu

For GPU support with FAISS, install faiss-gpu instead of faiss-cpu, but note that this requires a compatible CUDA setup.
Usage
After setting up the environment, you can use the recommendation system by running the provided Python script. Ensure the dataset CSV is available and the script is configured to load it. Example:
from recommend import recommend_songs

# Recommend songs for "Hawayein" by Arijit Singh
recommend_songs("Hawayein", ["Arijit Singh"])

# Recommend songs for "at my worst" (no artist specified)
recommend_songs("at my worst")

This will output the best matching song and the top 5 recommended songs based on similarity.
Results
The system provides accurate and relevant song recommendations by leveraging embeddings and audio features. It effectively captures similarities in musical style and artist profiles. Potential improvements include:

Fine-Tuning Embeddings: Training the Sentence Transformer model on music-specific data to enhance embedding quality.
Incorporating User Data: Adding user listening history or preferences for personalized recommendations.
Hybrid Approaches: Combining content-based and collaborative filtering methods for more robust recommendations.

Limitations

Dataset Dependency: The quality and diversity of recommendations depend on the Spotify dataset's coverage.
Static Features: The system uses static audio features and may not adapt to evolving user tastes without additional data.
Logo Availability: No official logos were found for Sentence Transformers and FAISS, which may affect branding consistency in documentation.

Example Visualizations
Below is a table summarizing key visualizations from the EDA phase:



Visualization Type
Description
Purpose



Top 25 Songs Bar Plot
Popularity scores of top 25 songs
Identify most popular tracks


Artist Track Count
Number of tracks per artist
Highlight prolific artists


Bayesian Average Popularity
Balanced popularity scores for artists
Rank artists with stable popularity metrics


Audio Feature Distributions
Histograms and boxplots for danceability, etc.
Understand feature distributions


Radar Charts
Audio feature profiles for top artists
Compare artists' musical characteristics


Musical Key Heatmap
Key distribution for top artists
Analyze tonal preferences


Genre Heatmap
Genre distribution for top artists
Explore genre preferences


These visualizations provide a comprehensive view of the dataset, aiding in feature selection and model validation.
