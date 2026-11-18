# Spotify Music Analysis

An exploratory data analysis project using Spotify track metadata and audio features. The objective is to describe patterns in popularity and audio characteristics across genres, and later investigate relationships among those features. This is a work in progress, not a finished analysis.

## Dataset

The project uses the [Spotify Tracks Dataset on Kaggle](https://www.kaggle.com/datasets/maharshipandya/-spotify-tracks-dataset). It contains **114,000 rows and 21 columns**. Initial inspection found 1,000 tracks per genre.

Download the CSV from Kaggle and place it locally at `data/dataset.csv`. The dataset is excluded from Git and is not included in this repository.

## Technologies

- Python
- Pandas and NumPy
- Matplotlib and Seaborn
- Jupyter Notebook
- Visual Studio Code (VS Code)

## Investigations completed

The exploratory notebook at [`notebooks/spotify_analysis.ipynb`](notebooks/spotify_analysis.ipynb) contains the analysis code, saved outputs, and visualisations.

### Initial dataset inspection

- The dataset has 114,000 rows and 21 columns, with 1,000 tracks in each genre.
- There is one missing value in each of `artists`, `album_name`, and `track_name`; all three are on the same row.
- There are no exact duplicate rows.
- `Unnamed: 0` has 114,000 unique values and appears to be a redundant original index column. Whether to remove it remains undecided.

These are data-quality checks, not a claim that the dataset has been fully cleaned. Decisions about missing values and the apparent index column are still outstanding.

### Popularity

| Statistic | Value |
| --- | ---: |
| Mean | 33.24 |
| Median | 35 |
| Standard deviation | 22.31 |
| Minimum | 0 |
| Maximum | 100 |

There are **16,020 tracks (14.05%)** with a popularity score of zero. Jazz has the largest share of zero-score tracks (68.1%), followed by Iranian (65.6%) and Romance (63.6%).

**Limitation:** a zero popularity score does not establish that a track has never been listened to, and this analysis does not explain why a score is zero. Popularity summaries and charts are descriptive; they do not establish what causes a track's score.

### Average energy by genre

The highest averages are Death metal (0.931), Grindcore (0.924), Metalcore (0.914), Happy (0.911), and Hardstyle (0.901). The lowest are Classical (0.190), New-age (0.215), Ambient (0.237), Romance (0.294), and Disney (0.303).

Metal-related genres appear prominently among the highest-energy genres, while classical, ambient, and new-age appear among the lowest.

### Average danceability by genre

The highest averages are Kids (0.779), Chicago-house (0.766), Reggaeton (0.759), Latino (0.757), and Reggae (0.745). The lowest are Sleep (0.168), Grindcore (0.272), Black metal (0.296), Iranian (0.301), and Opera (0.314).

Grindcore and black metal are among the highest-energy genres but among the lowest in danceability; death metal also combines high average energy with low average danceability. This illustrates that high energy does not necessarily mean high danceability in these genre averages.

### Average acousticness by genre

The highest averages are Classical (0.920), Romance (0.869), Tango (0.846), New-age (0.824), and Opera (0.795). The lowest are Death metal (0.007), Grindcore (0.009), Metalcore (0.010), Heavy metal (0.015), and Drum and bass (0.026).

Classical, new-age, and ambient have high average acousticness, while several metal and electronic genres have very low average acousticness.

## Limitations and project status

The findings above describe averages and counts in this dataset; they do not demonstrate causation or explain why Spotify assigned a popularity score. Genre-level averages also do not describe every track in a genre. The dataset has been inspected for several data-quality issues, but cleaning decisions have not been completed.

The project is ongoing. **Valence analysis and further relationship analysis are still outstanding**, including investigating relationships among popularity and audio features. Explicit versus non-explicit tracks have also not yet been compared.

## Setup

1. Install Python 3 and [Visual Studio Code](https://code.visualstudio.com/). In VS Code, install the Python and Jupyter extensions.
2. Clone or open this project folder, then create and activate a virtual environment from the project root:

   ```powershell
   python -m venv .venv
   .\.venv\Scripts\Activate.ps1
   ```

   On macOS or Linux, activate it with `source .venv/bin/activate`.
3. Install the libraries used by the notebook:

   ```powershell
   python -m pip install pandas numpy matplotlib seaborn jupyter
   ```

4. Download the dataset as a CSV from Kaggle and save it as `data/dataset.csv`. The CSV is intentionally ignored by Git.
5. Open `notebooks/spotify_analysis.ipynb` in VS Code, or start Jupyter from the `notebooks` directory so the notebook's existing `../data/dataset.csv` path resolves:

   ```powershell
   Set-Location notebooks
   jupyter notebook spotify_analysis.ipynb
   ```

## Project layout

```text
spotify-music-analysis/
├── data/
│   └── dataset.csv                 # Download locally; not tracked by Git
└── notebooks/
    └── spotify_analysis.ipynb      # Exploratory notebook
```
