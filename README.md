# 🎬 Movie Recommender System

A movie recommender system built using machine learning techniques such as content-based filtering. It suggests movies similar to a user's selected movie based on metadata such as genres, keywords, cast, and crew.

## 🚀 Live Demo

[Try the Movie Recommender System](https://movierecommendorsystemapp.streamlit.app/)

## 📊 Dataset

The system is powered by the **TMDB 5000 Movies and Credits Dataset**, which includes information about approximately 5,000 movies.

The dataset contains:

- `tmdb_5000_movies.csv` — Movie metadata including genres, keywords, overview, and movie ID.
- `tmdb_5000_credits.csv` — Cast and crew information.

Dataset source: [Kaggle - TMDB 5000 Movie Dataset](https://www.kaggle.com/datasets/tmdb/tmdb-movie-metadata)

## ✨ Features

- Content-based movie recommendations
- Recommends the top 10 similar movies
- Uses movie metadata including:
  - Genres
  - Keywords
  - Cast
  - Crew
- TF-IDF based text vectorization
- Cosine similarity for measuring movie similarity
- TMDB API integration for movie posters
- Interactive Streamlit interface

## 🧠 How It Works

### 1. Data Preparation

The movie and credits datasets are merged using the movie title.

The following features are extracted:

- Movie ID
- Title
- Overview
- Genres
- Keywords
- Cast
- Crew

The genres, keywords, cast, and crew information are combined to create a `tags` column.

### 2. Text Vectorization

The `tags` column is converted into numerical vectors using **TF-IDF (Term Frequency-Inverse Document Frequency)**.

```python
from sklearn.feature_extraction.text import TfidfVectorizer

tfidf = TfidfVectorizer(stop_words='english')
tfidf_matrix = tfidf.fit_transform(movies['tags'])
```
3. Cosine Similarity

Cosine similarity is calculated between the TF-IDF vectors of all movies.

from sklearn.metrics.pairwise import cosine_similarity

cosine_sim = cosine_similarity(tfidf_matrix, tfidf_matrix)

This produces a similarity score between movies based on their metadata.

4. Generating Recommendations

When a user selects a movie:

The selected movie is located in the dataset.
Its similarity scores with other movies are retrieved.
The movies are sorted according to their similarity scores.
The top 10 similar movies are returned.
5. Displaying Movie Posters

The TMDB API is used to fetch poster images for the recommended movies.

🛠️ Technologies Used
Python
Pandas
NumPy
Scikit-learn
TF-IDF
Cosine Similarity
Requests
TMDB API
Streamlit
Pickle
📁 Project Structure
movie_recommendor_system/
│
├── app.py
├── movie_data.pkl
├── requirements.txt
├── README.md
└── movie_recommender_system.ipynb
⚙️ Installation

Clone the repository:

git clone https://github.com/medhu07/movie_recommendor_system.git
cd movie_recommendor_system

Install the required dependencies:

pip install -r requirements.txt

Run the Streamlit application:

streamlit run app.py
