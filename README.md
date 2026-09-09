# Spotify Music Popularity Analysis

This project analyzes Spotify track data to investigate which musical characteristics are most strongly associated with song popularity.

The analysis combines exploratory data analysis, KMeans clustering, principal component analysis, and logistic regression to examine how playlist genre, musical key, and continuous audio features relate to whether a track exceeds a popularity score of 50.

## Project Objective

The objective is to identify patterns associated with song popularity and evaluate whether those patterns remain consistent across exploratory analysis, clustering, and classification modeling.

## Data

The analysis uses the Spotify Songs dataset published through the R for Data Science TidyTuesday repository.

Source:
https://github.com/rfordatascience/tidytuesday/tree/master/data/2020/2020-01-21

The notebook retrieves the source CSV directly from the public repository, so no separate local data file is required.

The raw dataset contains 32,833 rows and 23 columns. After removing incomplete and duplicate records and selecting the variables used in the analysis, the working dataset contains 28,352 tracks.

## Tools & Methods

**Python • NumPy • Pandas • Matplotlib • Seaborn • scikit-learn**

Methods include:

- Data cleaning and feature preparation
- Exploratory data analysis
- Distribution and correlation analysis
- Binary target engineering
- Feature standardization
- KMeans clustering
- Elbow and silhouette analysis
- Principal component analysis (PCA)
- One-hot encoding
- Logistic regression
- scikit-learn pipelines
- Stratified cross-validation
- Confusion matrices and ROC curves
- Classification metrics
- Model coefficient interpretation

## Analytical Approach

Three binary popularity thresholds were initially evaluated at scores greater than 50, 60, and 70.

The greater-than-50 target was selected for the final classification analysis because it produced the most workable class distribution. The higher thresholds became increasingly imbalanced and produced weaker preliminary classification behavior.

For clustering, multiple values of `k` were evaluated using both the elbow method and silhouette analysis. A two-cluster solution produced the highest silhouette score, but the two groups showed nearly identical observed popularity rates. A four-cluster solution was retained as a more granular exploratory segmentation because it produced more distinct audio profiles and a wider range of observed popularity rates.

## Key Findings

- Playlist genre contributed substantial predictive information and produced the largest coefficients in the final logistic regression model.
- Adding categorical features improved mean cross-validation ROC AUC from **0.603** to **0.659** compared with using the continuous audio features alone.
- The final held-out test model achieved **0.649 accuracy** and **0.663 ROC AUC**.
- Final-model precision was **0.563**, while recall was **0.242**, showing that the model identified only a portion of tracks above the popularity threshold at the default classification cutoff.
- Energy and loudness had the strongest relationship among the continuous audio features, with a correlation of approximately **0.68**.
- The retained four-cluster solution produced observed popularity rates ranging from approximately **29.0% to 41.7%**.
- The available track characteristics contain useful information about popularity, but substantial overlap remains between popular and less-popular tracks.

These results are observational and should not be interpreted as evidence that any particular genre or audio characteristic causes a song to become popular.

## Repository Contents

- `spotify_music_popularity_analysis.ipynb` — complete analysis notebook
- `spotify_music_popularity_analysis.html` — optional read-only HTML export
- `README.md` — project overview, methods, and findings
- `requirements.txt` — Python package dependencies

## Running the Analysis

1. Clone the repository.
2. Install the required Python packages:

```bash
pip install -r requirements.txt
```

3. Open `spotify_music_popularity_analysis.ipynb` in Jupyter.
4. Run the notebook from top to bottom.

The source dataset is retrieved directly from the TidyTuesday repository when the notebook runs.

## Author

**Lynn Ruch**  
M.S. Data Science Candidate, University of Pittsburgh
