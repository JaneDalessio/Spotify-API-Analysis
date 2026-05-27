# Spotify API Data Pipeline & Analysis
 
**Data 200 — Introduction to Data Analytics | Dickinson College**  
Jane Dalessio · May 2025
 
---
 
## Overview
 
This project uses the **Spotify Web API** to enrich an existing dataset of the [Top Spotify Songs of 2023](https://www.kaggle.com/datasets/nelgiriyewithana/top-spotify-songs-2023) with two new variables: **track popularity** and **song duration**, both pulled live from the API. The enriched dataset is then merged with the original and used to explore how popularity and song length relate to streaming performance and release trends over time.
 
This project builds directly on an earlier EDA of the same dataset, using the API to revisit and extend those findings.
 
---
 
## Key Features
 
- **Live API integration** via the [Spotipy](https://spotipy.readthedocs.io/) library and the Spotify Web API
- **Two-function pipeline**: a single-track lookup function composed into a batch function that processes an entire DataFrame row by row
- **Dataset merging** with `pd.merge()` to align API results with the original 2023 dataset
- **Tidy data principles** maintained throughout — each variable has its own column, each song its own row
- **Four original visualizations** exploring popularity distribution, song duration trends, and chart performance
---
 
## Key Findings
 
- **Popularity histogram** reveals a strong left skew — while all songs were top-streamed in 2023, many have since faded, with a notable cluster of single-digit popularity scores revealing clear one-hit wonders.
- **Popularity vs. duration** scatter plot shows most sustained hits cluster tightly around 3–4 minutes in length.
- **Average duration over time** line plot shows song lengths peaked in the 1980s and dipped sharply in the 1990s–early 2000s, defying the expectation that modern songs would be significantly shorter.
- **Popularity vs. Spotify chart appearances** shows higher-popularity songs appear on charts more frequently, while a notable cluster of top-streamed songs never charted at all.
- **Revisited hypothesis**: an earlier finding linking speechiness to the rise of rap and hip-hop could not be directly tested here, as the Spotify API does not expose a genre variable for tracks — a limitation noted for future work.
---
 
## Project Structure
 
```
spotify-api-analysis/
│
├── Spotify_Data_Final.ipynb    ← Main notebook: API pipeline, merge, and visualizations
├── spotify-2023.csv            ← Source dataset (download separately, see below)
├── merged_spotify_data.csv     ← Output: original dataset merged with API results
└── .gitignore                  ← Keeps credentials and outputs out of version control
```
 
---
 
## Setup & How to Run
 
### 1. Clone the repository
```bash
git clone https://github.com/JaneDalessio/spotify-api-analysis.git
cd spotify-api-analysis
```
 
### 2. Install dependencies
```bash
pip install spotipy pandas matplotlib
```
 
### 3. Download the dataset
Download [spotify-2023.csv](https://www.kaggle.com/datasets/nelgiriyewithana/top-spotify-songs-2023) from Kaggle and place it in the project root.
 
### 4. Add your Spotify credentials
⚠️ **Note:** As of February 2026, Spotify requires a **Spotify Premium account** to access the Developer Dashboard and obtain API credentials. Free accounts can no longer create apps or generate a Client ID/Secret.
1. Create an app at the [Spotify Developer Dashboard](https://developer.spotify.com/dashboard) to get a **Client ID** and **Client Secret**
2. In the first cell of the notebook, set your credentials as environment variables:
```python
import os
os.environ["SPOTIPY_CLIENT_ID"] = "your_client_id_here"
os.environ["SPOTIPY_CLIENT_SECRET"] = "your_client_secret_here"
```
> ⚠️ Do not commit this cell with real credentials. Clear or delete it before pushing to GitHub.
 
### 5. Run the notebook
```bash
jupyter notebook Spotify_Data_Final.ipynb
```
 
---
 
## Tools & Libraries
 
- **Python** — spotipy, pandas, matplotlib
- **Spotify Web API**
- **Jupyter Notebook**
---
 
## Limitations & Future Work
 
- 8 songs from the original 846-row dataset were not found by the API (likely due to naming mismatches), resulting in 838 rows in the merged output
- Genre data is not available through the Spotify track endpoint, which prevented directly testing the speechiness/hip-hop hypothesis from the earlier project
- A more comprehensive multi-decade dataset would strengthen the song duration over time analysis
---
 
## Topics
`python` `spotify` `api` `data-analysis` `data-pipeline` `pandas` `matplotlib` `jupyter-notebook` `spotipy` `data-200`
 
