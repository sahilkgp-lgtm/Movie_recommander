# movie-recommender-system-tmdb-dataset
A content based movie recommender system using cosine similarity
# 🎬 Movie Recommendation System

A Content-Based Movie Recommendation System built using Python, Pandas, Scikit-learn, Streamlit, and TMDB API. The system recommends movies similar to the selected movie by analyzing their metadata such as genres, keywords, cast, crew, and overview using Natural Language Processing (NLP) techniques.

# Features
🎬 Content-Based Movie Recommendations
Recommends the Top-5 most similar movies based on movie metadata instead of user ratings.
🔍 Intelligent Similarity Search
Uses Cosine Similarity on feature vectors generated from genres, keywords, overview, cast, and director.
🧠 NLP-Based Feature Engineering
Combines multiple textual attributes into a single feature representation and converts them into numerical vectors using CountVectorizer.
⚡ Fast Recommendations
Precomputes and serializes the similarity matrix using Pickle, enabling near-instant recommendation retrieval.
🖼️ Dynamic Movie Posters
Fetches high-quality movie posters in real time using the TMDB API.
🎨 Interactive Web Interface
Built with Streamlit, allowing users to select movies from a searchable dropdown and instantly view recommendations.
📚 Large Movie Database
Processes 4,800+ movies from the TMDB 5000 Movies Dataset.
📊 Optimized Feature Representation
Encodes movie information into 5,000-dimensional Bag-of-Words vectors after removing English stop words.
🔄 Automatic Ranking
Sorts similarity scores and returns the Top-5 most relevant movies while excluding the selected movie itself.
🧩 Modular Design
Separates model generation (Jupyter Notebook) from application deployment (Streamlit app), making the project easier to maintain and extend.
