# Spotify Music Analysis

An exploratory data analysis project using Spotify track metadata and audio features. The goal is to understand how track popularity is distributed and explore how it may relate to genre and measurable audio characteristics.

## Why explore Spotify music data?

Spotify's dataset combines popularity scores, genre labels, and audio features for a large collection of tracks. Exploring these fields can help us ask data-driven questions about patterns in music without assuming that any single feature explains a track's success.

## Questions to investigate

- How is track popularity distributed across the dataset?
- Does popularity vary across track genres?
- Which audio features, such as danceability, energy, valence, or acousticness, appear related to popularity?
- Do combinations of audio features show different patterns from individual features?
- Are there meaningful differences between explicit and non-explicit tracks?

These are investigation goals; they have not yet been answered by the current analysis.

## Technology

- Python
- Pandas and NumPy
- Matplotlib and Seaborn
- Jupyter Notebook
- Visual Studio Code (VS Code)

## Dataset

The project uses the [Spotify Tracks Dataset on Kaggle](https://www.kaggle.com/datasets/maharshipandya/-spotify-tracks-dataset). It contains **114,000 rows and 21 columns**.

The dataset is not included in this repository. Download it from Kaggle and place the CSV at `data/dataset.csv` locally.

### Initial data-quality checks

The initial notebook inspection found:

- One missing value in each of `artists`, `album_name`, and `track_name` (all three occur on the same row).
- Zero exact duplicate rows.
- `Unnamed: 0` has 114,000 unique values and appears to be an original row-index column.

These are initial checks only; data cleaning and decisions about the index column are still pending.

### Initial popularity summary

| Statistic | Value |
| --- | ---: |
| Mean | 33.238535 |
| Median | 35 |
| Standard deviation | 22.305078 |
| Minimum | 0 |
| Maximum | 100 |

### First visualisation

The notebook's first chart is a histogram of track popularity, shown with 20 bins and a KDE curve. It gives an initial view of scores across the 0–100 range: values are unevenly distributed, with many tracks in the lower-to-middle part of the scale and relatively few at the high end. This is a descriptive first look, not an explanation of what drives popularity.

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

## Progress and next steps

The current notebook loads the dataset, inspects its dimensions and columns, checks missing values and exact duplicates, summarizes popularity, and displays the first popularity histogram. Deeper investigations and data-cleaning decisions are still pending.

Planned next steps:

1. Decide how to handle the three missing text fields and the apparent original index column.
2. Explore popularity across genres and audio-feature ranges.
3. Examine relationships among audio features and compare explicit/non-explicit tracks.
4. Add clear visualisations and document findings as each investigation is completed.
