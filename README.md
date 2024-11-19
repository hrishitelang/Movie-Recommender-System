# Movie-Recommender-System

The objective of the project is to show customers content that they would like best based on their historical activity. I applied the knowledge of Data Wrangling, Data Visualization and Item-based Collaborative Filtering to get the desired output.
I developed a robust and scalable Movie Recommender System that leverages Item-Based Collaborative Filtering to provide personalized movie recommendations based on user preferences and past ratings. The system aims to enhance user experience by suggesting relevant and high-quality movie options while addressing challenges such as data sparsity and cold start issues.

## Problem Statement

Recommender systems help users find relevant items, such as movies, based on their preferences or usage history. For example, Netflix suggests movies based on what users have previously watched. This project implements a movie recommender system using **Item-based Collaborative Filtering** to recommend movies based on user ratings.

---

## Dataset

- **Source**: [MovieLens 100k dataset](https://grouplens.org/datasets/movielens/100k/)
- The dataset contains:
  - User IDs
  - Movie IDs
  - Ratings (on a scale of 1 to 5)
  - Movie Titles
- Movie titles are mapped to IDs via a provided file.

---

## Project Workflow

### 1. **Importing Libraries**
   The following libraries are used:
   - `pandas` and `numpy`: For data manipulation.
   - `matplotlib` and `seaborn`: For data visualization.

### 2. **Loading Datasets**
   - The dataset is split into two files:
     - **`Movie_Id_Titles.csv`**: Maps movie IDs to titles.
     - **`u.data`**: Contains user-item ratings.
   - Read the datasets and merge them to include movie titles in the rating data.

### 3. **Data Preprocessing**
   - Dropped irrelevant columns like `timestamp`.
   - Merged the movie titles into the user ratings data to create a unified dataframe for analysis.

---

## Steps to Build the Recommender System

### **Step 1: Data Exploration and Visualization**
   - Explored user ratings to understand distribution patterns.
   - Aggregated ratings for each movie to calculate:
     - **Mean Rating**: Average rating for a movie.
     - **Rating Count**: Number of times a movie was rated.
   - Visualized the distribution of mean ratings and rating counts using histograms.

### **Step 2: Pivot Table for User-Movie Ratings**
   - Created a pivot table (`userid_movietitle_matrix`) where:
     - Rows represent users.
     - Columns represent movies.
     - Values are the corresponding user ratings.
   - This matrix serves as the foundation for collaborative filtering.

### **Step 3: Correlation-Based Recommendations**
   - Selected a target movie (e.g., *Titanic (1997)* or *Star Wars (1977)*) to compute correlations.
   - Calculated the correlation of the target movie with all other movies using **Pearson’s correlation coefficient**.
   - Filtered movies with a minimum number of ratings to ensure reliability.

---

## Final Implementation: Recommender System Logic

### Item-Based Collaborative Filtering
1. **Define Ratings**:
   - Used the pivot table to extract user ratings for specific movies (e.g., *Titanic (1997)*).
2. **Calculate Similarity**:
   - Computed correlations for all movies with the selected movie.
   - Weighted the correlation values by the number of ratings to prioritize popular movies.
3. **Generate Recommendations**:
   - Sorted the movies by correlation to recommend the top items similar to the target movie.

### User-Specific Recommendations
1. Created a custom ratings file (`My_Ratings.csv`) for an individual user.
2. For each rated movie:
   - Found movies similar to the rated movie.
   - Weighted the similarity score by the user's rating for the movie.
3. Aggregated and ranked similar movies to generate personalized recommendations.

---

## Tools and Technologies

- **Programming Language**: Python
- **Libraries**:
  - `pandas`, `numpy`: Data processing and matrix operations.
  - `matplotlib`, `seaborn`: Visualizations.
- **Dataset**: MovieLens 100k.

---

## Challenges Faced

- **Handling NaN Values**: Missing data in the user-movie matrix required careful handling to avoid skewed correlation scores.
- **Sparsity of Data**: Many movies had few ratings, making correlations less reliable.
- **Cold Start Problem**: New users or movies without ratings posed challenges for recommendations.

---

## Outcome

- Successfully implemented an **Item-Based Collaborative Filtering** recommender system.
- Recommended movies based on:
  - Correlation with a target movie.
  - Personalized ratings using a custom input file.
- Identified popular movies with high correlations for reliable recommendations.

---

## What I Learned

- How to preprocess and explore real-world datasets.
- Implementing collaborative filtering techniques for recommendations.
- Handling sparse datasets and designing reliable recommender systems.
- Importance of weighting correlations by rating counts to improve recommendation accuracy.

---

## Future Scope

- **Hybrid Model**: Combine collaborative filtering with content-based recommendations for improved accuracy.
- **Scalability**: Apply distributed frameworks like Apache Spark to handle larger datasets.
- **Real-Time Predictions**: Deploy the model as an API for integration with web or mobile applications.

