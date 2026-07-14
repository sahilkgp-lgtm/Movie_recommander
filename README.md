# movie-recommender-system-tmdb-dataset
A content based movie recommender system using cosine similarity
# 🎬 Movie Recommendation System

A Content-Based Movie Recommendation System built using Python, Pandas, Scikit-learn, Streamlit, and TMDB API. The system recommends movies similar to the selected movie by analyzing their metadata such as genres, keywords, cast, crew, and overview using Natural Language Processing (NLP) techniques.

# ✨ Features

- 🎬 Top-5 content-based movie recommendations
- 🧠 NLP-based feature engineering using movie metadata
- 📊 5,000-dimensional Bag-of-Words representation
- 📐 Cosine Similarity for recommendation ranking
- ⚡ Fast recommendations using precomputed Pickle models
- 🖼️ Real-time movie posters fetched via TMDB API
- 🎨 Interactive Streamlit web interface
- 📚 Supports 4,800+ movies from the TMDB dataset
- 🔄 Automatic ranking of the most similar movies
- 🧩 Modular architecture separating model building and deployment

# Tech Stack
-Python
-Pandas
-NumPy
-Scikit-learn
-NLTK
-Streamlit
-Pickle
-TMDB API
-Requests

# Project Architecture / Workflow
### Data Loading
movies = pd.read_csv("tmdb_5000_movies.csv")
credits = pd.read_csv("tmdb_5000_credits.csv")
movies = movies.merge(credits, on="title")

### Feature Engineering
movies = movies[
    ['movie_id','title','overview','genres',
     'keywords','cast','crew']
]

### Combining Features
movies["tags"] = (
    movies["overview"] +
    movies["genres"] +
    movies["keywords"] +
    movies["cast"] +
    movies["crew"]
)

### Vectorizatoin
cv = CountVectorizer(
    max_features=5000,
    stop_words='english'
)

vectors = cv.fit_transform(
    movies['tags']
).toarray()

### Cosine Similarity
similarity = cosine_similarity(vectors)

### Saving model
pickle.dump(movies,
            open('movie_list.pkl','wb'))

pickle.dump(similarity,
            open('similarity.pkl','wb'))
### Installation
git clone https://github.com/username/movie-recommendation-system.git

cd movie-recommendation-system

pip install -r requirements.txt

### How to run
streamlit run app.py

# Deployment (Streamlit)
### Loading the model
movies = pickle.load(
    open('model/movie_list.pkl','rb')
)

similarity = pickle.load(
    open('model/similarity.pkl','rb')
)

### Recommendation Function
def recommend(movie):
    index = movies[movies['title']==movie].index[0]

    distances = sorted(
        list(enumerate(similarity[index])),
        reverse=True,
        key=lambda x:x[1]
    )

    return distances[1:6]

Fetch Poster
