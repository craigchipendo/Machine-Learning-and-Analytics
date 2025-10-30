# Movie Clustering Analysis Notebook

## Overview

This Jupyter Notebook performs unsupervised clustering on a large database of Netflix movie and TV show metadata. The primary goal is to **group movies/shows by similarity in their textual descriptions and listed genres** using **text feature engineering** and the **K-Means clustering algorithm**.

## Key Steps and Workflow

- **Data Loading:** Loads and previews records from `netflixtitles.csv`, which includes fields like title, director, cast, country, genre(s), release dates, ratings, duration, and detailed description.
- **Exploratory Data Analysis (EDA):** Inspects nulls, unique values, content distribution, and previews genres for initial data understanding.
- **Data Preprocessing:**
  - Cleans and standardizes textual descriptions (lowercasing, removing non-letters).
  - Utilizes TF-IDF vectorization to transform descriptions into numerical features for clustering.
  - Optionally processes genre columns for additional grouping.
- **Text Tokenization:** Tokenizes genres and removes stopwords to identify and count frequent phrases or bigrams/trigrams across all titles.
- **Clustering (K-Means):**
  - Runs the K-Means algorithm on the TF-IDF matrix.
  - Assigns cluster labels to all records.
  - The number of clusters (k) is adjustable; default is k=8.
- **Cluster Analysis:**
  - Displays the movies in each cluster, sorted by a criterion such as genre, rating, or popularity.
  - Outputs the top 5 movies per cluster (title and description) for manual inspection and validation.
  - Includes printed summaries and interactive Gradio visualizations to explore clusters.
  - Provides examples showing movie similarities within clusters using both title and description.


## Outputs

- Clustered groups of movies and TV shows based on textual and semantic similarity.
- Text-based analytic summaries and frequency distributions of genres and phrases.
- Cluster-wise listings of movies with descriptions to validate the clustering results.

## Purpose

This notebook provides:
- **A workflow for unsupervised movie grouping** using text feature engineering and clustering.
- **Tools for genre and description-based exploration** of large streaming media datasets.
- **A template for exploratory analysis** of media content databases, helpful for recommender systems and information retrieval projects.

---



