# Movie Recommender System 🎬

A content-based movie recommendation system built using Python, Scikit-learn, and Streamlit. The application suggests top 5 similar movies along with their posters based on metadata analysis (overview, genres, keywords, cast, and crew) from the TMDB 5000 dataset.

---

## 📌 Project Overview
This project processes movie metadata to extract tags for each movie, converts textual data into numerical vectors using `CountVectorizer`, and calculates similarity scores using **Cosine Similarity**. A user-friendly web interface built with **Streamlit** lets users select a movie and instantly receive recommendations along with official poster images fetched from **The Movie Database (TMDB) API**.

---

## 🛠️ Features
- **Content-Based Filtering**: Recommends movies based on structural similarity of overview, genres, keywords, top cast, and director.
- **TMDB API Integration**: Dynamically fetches and displays high-quality movie posters.
- **Interactive UI**: Built using Streamlit for seamless user experience.

---

## 📂 Project Structure
```text
.
├── model/
│   ├── movie_list.pkl        # Pickle file containing processed movie DataFrame
│   └── similarity.pkl        # Pickle file containing Cosine Similarity matrix
├── app.py                    # Streamlit web application script
├── model_building.ipynb      # Jupyter Notebook for EDA, data cleaning, & modeling
├── README.md                 # Project documentation
└── requirements.txt          # Python dependencies
```

---

## ⚙️ How It Works

1. **Data Preprocessing**:
   - Merges `tmdb_5000_movies.csv` and `tmdb_5000_credits.csv` on movie title.
   - Extracts relevant attributes: `movie_id`, `title`, `overview`, `genres`, `keywords`, `cast`, and `crew`.
   - Normalizes data by removing spaces (e.g., "Sam Worthington" -> "SamWorthington").
   - Concatenates attributes into a single string column named `tags`.

2. **Vectorization & Similarity**:
   - Uses `CountVectorizer(max_features=5000, stop_words='english')` to convert text tags into feature vectors.
   - Applies **Cosine Similarity** (`cosine_similarity(vector)`) to create a similarity matrix across all movies.

3. **Web Application**:
   - Loads serialized `movie_list.pkl` and `similarity.pkl`.
   - Fetches poster images using TMDB API endpoint `https://api.themoviedb.org/3/movie/{movie_id}`.
   - Displays recommendations in a responsive 5-column layout.

---

## 🚀 Installation & Setup

### 1. Prerequisites
Ensure you have Python 3.7+ installed on your system.

### 2. Clone the Repository
```bash
git clone https://github.com/your-username/movie-recommender-system.git
cd movie-recommender-system
```

### 3. Install Dependencies
```bash
pip install -r requirements.txt
```

*Required libraries:*
- `pandas`
- `numpy`
- `scikit-learn`
- `streamlit`
- `requests`

### 4. Run the Model Notebook (Optional)
If you want to train or regenerate the pickle files:
- Run `model_building.ipynb` using Jupyter Notebook or Kaggle.
- Place the generated `movie_list.pkl` and `similarity.pkl` inside a `model/` folder.

### 5. Run the Streamlit App
```bash
streamlit run app.py
```

---

## 📸 Usage
1. Open the application in your browser (usually at `http://localhost:8501`).
2. Select or search for a movie from the dropdown menu.
3. Click on the **Show Recommendation** button.
4. View top 5 recommended movies with poster previews!

---

## 📊 Dataset
- Dataset Source: [TMDB 5000 Movie Dataset on Kaggle](https://www.kaggle.com/datasets/tmdb/tmdb-movie-metadata)
  - `tmdb_5000_movies.csv`
  - `tmdb_5000_credits.csv`
