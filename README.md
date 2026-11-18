# Movie Recommendation System

A Jupyter Notebook that demonstrates several movie recommendation techniques on a small MovieLens-style dataset:

- **User-based collaborative filtering**: recommends movies from users with similar rating patterns.
- **Item-based collaborative filtering**: recommends movies whose ratings are similar to movies a user has rated.
- **Content-based filtering**: uses TF-IDF and cosine similarity over movie genres.
- **Hybrid recommendations**: combines collaborative and content-based scores.
- **Cold-start recommendations**: recommends movies from genre preferences without requiring ratings.
- **Evaluation**: compares methods using RMSE, MAE, coverage, and precision at 5.

The notebook includes a synthetic sample dataset with 40 movies, 42 users, and 674 ratings. It can also load MovieLens-style CSV files.

## Requirements

- Python 3.9+
- NumPy
- pandas
- scikit-learn
- Jupyter Notebook or JupyterLab

Install the dependencies with:

```bash
pip install numpy pandas scikit-learn jupyter
```

## Getting started

Clone the repository and open the notebook:

```bash
git clone https://github.com/faalaaann/Movie-Recommendation-System.git
cd Movie-Recommendation-System
jupyter notebook "movie recomendation system.ipynb"
```

Run the notebook cells from top to bottom. The final cell runs a demonstration using the built-in sample data and shows:

- A user's highest-rated movies
- Hybrid, user-CF, item-CF, and content-based recommendations
- Movies similar to *Inception*
- Genre-based recommendations for a cold-start user
- Hold-out evaluation results

## Using your own data

The recommender accepts MovieLens-style dataframes:

### `movies.csv`

```text
movieId,title,genres
1,Toy Story (1995),Animation|Children|Comedy
```

### `ratings.csv`

```text
userId,movieId,rating,timestamp
1,1,5.0,964982703
```

Load the files in a notebook cell:

```python
import pandas as pd

movies = pd.read_csv("movies.csv")
ratings = pd.read_csv("ratings.csv")
rec = Recommender(movies, ratings)
```

Then request recommendations:

```python
rec.recommend(user_id=1, method="hybrid", n=10)
```

Supported methods are `user_cf`, `item_cf`, `content`, and `hybrid`.

Other useful operations include:

```python
rec.similar_movies(movie_id=6, n=5, by="content")
rec.by_genres(["Sci-Fi", "Thriller"], n=10)
rec.history(user_id=1, n=5)
evaluate(movies, ratings)
```

## Project structure

```text
.
├── movie recomendation system.ipynb
└── README.md
```

## License

No license has been specified for this repository.
