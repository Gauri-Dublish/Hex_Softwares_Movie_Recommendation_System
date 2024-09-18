# Hex_Softwares_Movie_Recommendation_System
# README

## Movie Recommendation System using Cosine Similarity

### Overview:
This Python script implements a basic movie recommendation system using **Natural Language Processing (NLP)** techniques. The system computes the similarity between movies based on their **genre** and **overview**, and suggests movies that are similar to a given movie. The recommendations are generated using **cosine similarity** on a **bag-of-words** representation of the movie metadata.

### Prerequisites:
- **Google Colab** or a local Python environment
- The dataset should be a CSV file stored on Google Drive or locally, containing at least the following columns: `id`, `title`, `genre`, and `overview`.

### Dependencies:
Make sure to install the following Python libraries before running the code:
- **numpy**
- **pandas**
- **scikit-learn** (for CountVectorizer and cosine_similarity)

Install these libraries using pip if required:
```bash
pip install numpy pandas scikit-learn
```

### Code Breakdown:

1. **Importing Libraries:**
   The script imports essential libraries such as `numpy`, `pandas`, and `scikit-learn` for handling data and vectorization.

2. **Loading Dataset:**
   The dataset is loaded using `pandas.read_csv()` from Google Drive (in the case of Google Colab). Ensure the dataset is accessible via the specified file path.

3. **Data Preprocessing:**
   - A new column `tags` is created by combining the `genre` and `overview` columns.
   - The `tags` column is a critical component for generating movie similarity.
   - The columns `genre` and `overview` are dropped after creating the `tags` column to keep the data concise.

4. **Vectorization:**
   The **CountVectorizer** from `sklearn.feature_extraction.text` is used to convert the text in the `tags` column into a vectorized form. It limits the number of features to 10,000 words and removes common English stop words.

5. **Cosine Similarity Calculation:**
   The **cosine_similarity** function calculates the similarity between each movie in the dataset based on their `tags`. This results in a similarity matrix where each entry corresponds to the similarity between two movies.

6. **Movie Recommendation:**
   A simple recommendation function, `recommend()`, is defined. Given a movie title, it retrieves the most similar movies by finding the closest vectors in the similarity matrix.

### Functions:

#### `recommend(movie_title)`
- **Input:** The title of the movie for which recommendations are needed.
- **Output:** Prints the top 5 most similar movies.
- **Working:** It locates the index of the input movie, sorts the similarity matrix by cosine similarity, and displays the titles of the most similar movies.

### Example Usage:

```python
# Example: Get recommendations for 'Iron Man'
recommend("Iron Man")
```

### Output:

The function will output the top 5 movies similar to "Iron Man" based on the content of their `tags`.

### Important Notes:
- **Dataset Requirements:** The dataset should have at least the following columns: `id`, `title`, `genre`, and `overview`. The `tags` column is created by concatenating the `genre` and `overview` columns.
- **Model Assumptions:** This model assumes that movies with similar genres and overviews are closely related. It works best for datasets with meaningful textual descriptions in the `overview`.

### How to Extend:
- The current implementation only uses genre and overview for recommendation. You can extend it by adding other metadata such as cast, directors, or user reviews.
- You can also tune the number of features or use other NLP techniques such as TF-IDF to improve recommendation quality.

