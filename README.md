# 🎬 Movie Recommendation System

A content-based Movie Recommendation System built using Python and Machine Learning techniques. The project analyzes movie information from the TMDB 5000 dataset and recommends movies similar to a selected movie.

The project also includes a Streamlit web application that allows users to select a movie and receive personalized movie recommendations.


## 📌 Project Overview

The objective of this project is to build a Movie Recommendation System that can recommend movies based on their similarity to a movie selected by the user.

The project explores different recommendation approaches:

* Weighted Average Rating
* Popularity-Based Recommendation
* Hybrid Recommendation
* Content-Based Recommendation using NLP

The final recommendation system uses **TF-IDF Vectorization** and a **Sigmoid Kernel** to calculate similarity between movie overviews.


## 📂 Dataset

The project uses the **TMDB 5000 Movie Dataset**, consisting of two datasets:

### 1. TMDB 5000 Movies

Contains information such as:

* Movie title
* Budget
* Genres
* Keywords
* Original language
* Overview
* Popularity
* Release date
* Revenue
* Runtime
* Vote average
* Vote count

### 2. TMDB 5000 Credits

Contains information such as:

* Movie ID
* Cast
* Crew
* Director
* Other movie contributors

The two datasets are merged using the movie ID.


## 🔄 Project Workflow

TMDB Movies Dataset
        +
TMDB Credits Dataset
        ↓
Data Cleaning
        ↓
Data Merging
        ↓
Exploratory Data Analysis
        ↓
Weighted Average Rating
        ↓
Popularity-Based Recommendation
        ↓
Normalization
        ↓
Hybrid Recommendation
        ↓
TF-IDF Vectorization
        ↓
Sigmoid Kernel Similarity
        ↓
Content-Based Recommendation
        ↓
Save Model Artifacts
        ↓
Streamlit Application


## 🧹 Data Preprocessing

The two datasets are merged using the movie ID.

Unnecessary columns such as:

* homepage
* title_x
* title_y
* status
* production_countries

are removed during data cleaning.

The cleaned dataset is then used for further analysis and recommendation model development.


## ⭐ Weighted Average Recommendation

A weighted average rating is calculated using:

* Movie's average rating
* Number of votes
* Mean rating across movies
* Minimum vote threshold

This helps identify highly rated movies while considering the number of votes received.

The project uses the 90th percentile of `vote_count` as the threshold for selecting movies for this ranking approach.


## 📈 Popularity-Based Recommendation

Movies are also ranked based on their `popularity` score.

This provides another way of identifying movies that are currently popular within the dataset.


## 🔀 Hybrid Recommendation

The project combines:

* Weighted average rating
* Popularity

Both values are normalized using `MinMaxScaler`.

The hybrid score is calculated as:

```python
score_mix = weighted_avg_scaled * 0.5 + popularity_scaled * 0.5
```

This combines rating quality and popularity into a single score.


## 🧠 Content-Based Recommendation

The final recommendation system uses a **content-based filtering approach**.

The movie `overview` is used as the primary text feature.

### TF-IDF

TF-IDF (Term Frequency-Inverse Document Frequency) converts the movie overview text into numerical vectors.

The project uses:

```python
TfidfVectorizer(
    min_df=3,
    ngram_range=(1,3),
    stop_words="english"
)
```

This allows the model to identify important words and phrases from movie descriptions.

### Sigmoid Kernel

A sigmoid kernel is then applied to the TF-IDF matrix to calculate similarity between movies.

Movies with higher similarity scores are considered more similar.


## 🎯 Recommendation Process

When a user selects a movie:

1. The selected movie is identified.
2. Its similarity scores are retrieved.
3. Movies are sorted based on similarity.
4. The top similar movies are selected.
5. The recommendations are displayed to the user.

The system returns the **top 10 similar movies** excluding the selected movie itself.


## 🖥️ Streamlit Application

The project includes a Streamlit application.

The application provides:

* Movie selection dropdown
* Recommendation button
* List of recommended movies

Example workflow:

Select Movie
     ↓
Click "Get Recommendations"
     ↓
Calculate Similarity
     ↓
Display 10 Similar Movies


## 🛠️ Technologies Used

| Technology     | Purpose                   |
| -------------- | ------------------------- |
| Python         | Programming               |
| Pandas         | Data manipulation         |
| NumPy          | Numerical operations      |
| Matplotlib     | Data visualization        |
| Seaborn        | Data visualization        |
| Plotly         | Interactive visualization |
| Scikit-learn   | Machine Learning & NLP    |
| TF-IDF         | Text vectorization        |
| Sigmoid Kernel | Similarity calculation    |
| Joblib         | Model serialization       |
| Streamlit      | Web application           |


## 📁 Project Structure

Movie-Recommendation-System/
│
├── Movie Recommendation System.ipynb
├── app.py
├── README.md
├── requirements.txt
│
└── dumped_obj/
    ├── movie_data_for_app.xls
    ├── movie_dataframe_for_app.xls
    ├── tfidf_vectorizer.pkl
    └── sigmoid_kernel.pkl
    

## ▶️ How to Run the Project

### 1. Clone the Repository

```bash
git clone <your-github-repository-url>
```

### 2. Navigate to the Project Folder

```bash
cd Movie-Recommendation-System
```

### 3. Install Required Libraries

```bash
pip install pandas numpy matplotlib seaborn plotly scikit-learn streamlit joblib
```

### 4. Run the Streamlit Application

```bash
streamlit run app.py
```

The application will open in your browser.


## 📊 Example

If the user selects:
Avatar

the system analyzes the similarity scores and displays movies with similar content.

The recommendation function sorts similarity scores in descending order and returns the top 10 recommendations.


## 🚀 Key Learning Outcomes

Through this project, I worked with:

* Data cleaning and preprocessing
* Data merging
* Exploratory Data Analysis
* Recommendation systems
* Feature engineering
* Text preprocessing
* NLP
* TF-IDF Vectorization
* Similarity calculation
* Data normalization
* Model serialization
* Streamlit application development


## 🔮 Future Improvements

Potential improvements include:

* Adding collaborative filtering
* Combining content-based and collaborative filtering
* Including genres, cast, crew and keywords as recommendation features
* Adding movie posters and descriptions
* Improving the Streamlit user interface
* Deploying the application online
* Adding user ratings and personalized recommendations
