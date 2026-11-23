# Spotify Music Analysis

An exploratory data analysis of Spotify track metadata and audio features. This project examines how popularity varies across tracks, how audio characteristics differ across genres, how audio features relate to one another, and whether popularity differs by audio features or explicit-content status.

The analysis is descriptive and specific to the dataset used. It is not intended to establish causes or universal rules about music popularity.

## Project objectives

The notebook investigates:

- How does popularity vary across tracks?
- How do audio characteristics differ across genres?
- How are audio features related to one another?
- Are audio characteristics associated with popularity?
- Do explicit and non-explicit tracks differ in popularity?

## Dataset

The analysis uses the [Spotify Tracks Dataset on Kaggle](https://www.kaggle.com/datasets/maharshipandya/-spotify-tracks-dataset). The downloaded dataset contains approximately **114,000 tracks**, **114 genres**, and **21 columns**. This copy has 1,000 tracks per genre.

The data includes track metadata, popularity, explicit-content status, genre, and audio features such as danceability, energy, acousticness, valence, tempo, and loudness. Initial inspection found one row with missing artist, album, and track names. The `Unnamed: 0` field appears to be an original row index.

The dataset is not included in this repository. Download the CSV from Kaggle and place it at `data/dataset.csv`; that local file is excluded by `.gitignore`.

## Key findings

These results describe the dataset analyzed in the notebook and should not be generalized to all Spotify tracks.

- **Popularity:** The mean score was 33.24 and the median was 35. A total of 16,020 tracks (14.05%) had a score of zero. Jazz had the largest proportion of zero-score tracks (68.1%), followed by Iranian (65.6%) and Romance (63.6%). A zero score does not establish that a track has never been listened to.
- **Genre differences:** Death metal had the highest average energy (0.931), while classical had the lowest (0.190). Salsa had the highest average valence (0.815), while sleep had the lowest (0.058). The notebook also compares genre averages for danceability and acousticness.
- **Relationships between audio features:** Energy and loudness had a positive Pearson correlation of about +0.76; energy and acousticness had a negative correlation of about -0.73. Danceability and valence were moderately positively correlated (+0.48), while energy and danceability had a weak positive correlation (+0.13).
- **Audio features and popularity:** Each selected feature had a very weak linear correlation with popularity. Loudness had the strongest positive correlation (+0.050) and instrumentalness the strongest negative correlation (-0.095). This does not rule out non-linear or combined relationships.
- **Explicit content:** Explicit tracks had a higher average popularity score (36.45) than non-explicit tracks (32.94); their medians were 37 and 34, respectively. The groups differed substantially in size: 9,747 explicit tracks and 104,253 non-explicit tracks. This comparison does not show that explicit content causes higher popularity.

## Visualisations

The executed notebook contains embedded charts, including the popularity distribution, genre-average comparisons, energy-versus-acousticness scatterplot, audio-feature correlation heatmap, popularity correlation chart, and explicit versus non-explicit popularity boxplot. There are no separate chart image files in the repository. Open the notebook to view the charts and their surrounding analysis.

## Technologies

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Jupyter Notebook

## Repository structure

```text
spotify-music-analysis/
├── .gitignore
├── README.md
├── requirements.txt
└── notebooks/
    └── spotify_analysis.ipynb
```

## Run the project

1. Clone the repository and enter its folder:

   ```bash
   git clone https://github.com/DanielC34/spotify-data-analysis.git
   cd spotify-data-analysis
   ```

2. Create and activate a virtual environment. In Windows PowerShell:

   ```powershell
   py -m venv .venv
   .\.venv\Scripts\Activate.ps1
   ```

   On macOS or Linux:

   ```bash
   python3 -m venv .venv
   source .venv/bin/activate
   ```

3. Install the project dependencies:

   ```bash
   python -m pip install --upgrade pip
   python -m pip install -r requirements.txt
   ```

4. Download the dataset CSV from [Kaggle](https://www.kaggle.com/datasets/maharshipandya/-spotify-tracks-dataset) and save it as `data/dataset.csv`. The CSV is intentionally not tracked by Git.

5. From the project root, launch Jupyter with the notebook directory as the working directory so the notebook's `../data/dataset.csv` path resolves:

   ```bash
   cd notebooks
   jupyter notebook spotify_analysis.ipynb
   ```

   Alternatively, open `notebooks/spotify_analysis.ipynb` in VS Code, select the `.venv` Python kernel, and run all cells. Ensure the notebook's working directory is `notebooks/`.

## Limitations

- This dataset may not represent Spotify's entire catalogue, and it is a snapshot rather than a live view.
- Popularity is a Spotify-specific score and should not be treated as a general measure of music quality or success on other platforms.
- Pearson correlation measures linear association only; correlation does not establish causation.
- Group averages do not control for other factors, such as genre or artist popularity, and the explicit/non-explicit groups are unequal in size.
- One record is missing artist, album, and track names. The analysis is exploratory and does not apply a complete cleaning process.
- Genre averages summarize groups and do not describe every track within a genre.

## Future improvements

- Explore possible non-linear relationships between audio features and popularity.
- Compare explicit and non-explicit tracks while accounting for genre and artist popularity.
- Document and apply a consistent strategy for missing metadata and the apparent index column.
- Repeat the analysis with a newer or broader dataset to assess how stable these patterns are.
