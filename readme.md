# Movie Recommendation System using NLP

This project implements a content-based movie recommendation system using Natural Language Processing (NLP) techniques. The system analyzes movie descriptions to find similar movies based on their plot summaries.

## Overview

The recommendation system uses TF-IDF (Term Frequency-Inverse Document Frequency) vectorization to analyze combined movie information (including plot descriptions, genres, and keywords) and calculates similarity scores between movies using cosine similarity. The system comes in two versions:
1. Basic version (NLP_MovieRecommender.ipynb): Uses only movie overviews
2. Enhanced version (NLP_MovieRecommender_WithMoreEntries.ipynb): Combines overview, genres, and keywords for better recommendations

## Features

- Processes movie data from the TMDB 5000 movies dataset
- Uses TF-IDF vectorization for text analysis
- Implements cosine similarity for finding movie similarities
- Returns top 5 similar movies based on:
  - Basic version: Plot descriptions only
  - Enhanced version: Combined analysis of plot descriptions, genres, and keywords
- Provides more accurate recommendations by considering multiple movie attributes

## Dependencies

- pandas
- numpy
- scikit-learn
- pickle

## Dataset

The project uses the TMDB 5000 movies dataset which includes:
- Movie titles
- Plot overviews
- Release dates
- Genres
- Other metadata

## Implementation Details

1. **Data Preprocessing**
   - Loads movie data from CSV
   - Handles missing values in overview column
   - Processes text data for analysis

2. **TF-IDF Vectorization**
   ```python
   vectorizer = TfidfVectorizer(
       stop_words="english",
       min_df=2,
       max_df=.95
   )
   ```

3. **Similarity Calculation**
   - Uses cosine similarity to calculate movie similarities
   - Creates a similarity matrix for all movies

4. **Movie Recommendation Function**
   ```python
   def get_suggested_5_movies(movie_name):
       try:
           user_movie_idx = df.loc[df["original_title"] == movie_name].index[0]
           movies = df.iloc[a[user_movie_idx]]["original_title"]
           return movies
       except IndexError as e:
           print("Movie cannot found also here its a formal error key:", e)
   ```

## Usage

1. Load the required libraries and dataset
2. Run the recommendation function with a movie title:
   ```python
   movie = input("Type a Movie: ")
   get_suggested_5_movies(movie)
   ```

## Example Output

```
Input: "The Dark Knight"
Output:
- The Dark Knight Rises
- Batman Returns
- Batman Forever
- Batman: The Dark Knight Returns, Part 2
- Batman
```

## Error Handling

The system includes basic error handling for:
- Movies not found in the database
- Invalid input formats

## Versions

### Basic Version (NLP_MovieRecommender.ipynb)
- Uses movie overviews only
- Provides basic content-based recommendations
- Lighter and faster processing

### Enhanced Version (NLP_MovieRecommender_WithMoreEntries.ipynb)
- Combines overview, genres, and keywords
- Creates a more comprehensive similarity analysis
- Provides more contextually relevant recommendations

## Future Improvements

Potential enhancements could include:
- Implementing user ratings in similarity calculations
- Adding more sophisticated NLP techniques
- Including weighted calculations for different features
- Adding collaborative filtering
- Implementing a hybrid recommendation system