# Spotify Tracks Data Analysis – Skill Lab CIE 1 (Milestone 1)

Hi! This repository contains my submission for **Skill Lab CIE-1 (Milestone 1)**. 

For this assignment, I chose a **Spotify Tracks Dataset (`spotify_tracks_dataset.csv`)** with 500 songs to explore how audio qualities like tempo, energy, and danceability connect with streaming numbers and song popularity across different genres.

## Files in This Repository

| File Name | Description |
| :--- | :--- |
| `Spotify_Data_Analysis_CIE1.ipynb` | Main Jupyter Notebook with all Python/Pandas code, outputs, and charts |
| `spotify_tracks_dataset.csv` | The 500-row CSV dataset used for the analysis |
| `README.md` | Project overview and summary of steps performed |

## What I Did in the Notebook

### 1. Dataset Selection and Reading
- Loaded `spotify_tracks_dataset.csv` using `pd.read_csv()`.
- Checked the first few rows with `df.head()` to make sure all columns read properly.

### 2. Data Understanding
- Inspected the dataset shape (`500 rows × 14 columns`), column names, and data types using `df.info()` and `df.describe()`.
- Checked the unique music genres (`Pop`, `Bollywood`, `Hip-Hop`, `Indie Pop`, `Electronic`, `Rock`, `R&B`, `Lo-Fi`) and artist counts.

### 3. Data Transformation
- **Dropped unnecessary columns:** Removed `Album_Internal_Code` and `Record_Label_Notes` since they were just internal catalog tags and not useful for analysis.
- **Converted data types:** Ensured `Duration_ms` and `Release_Year` are stored as clean integer (`int64`) types.
- **Added new columns:**
  - `Duration_Minutes`: Converted track length from milliseconds into minutes so it is much easier to read.
  - `Release_Era`: Categorized songs into `2016-2020` and `2021-2025`.
  - `Popularity_Tier`: Grouped songs into `Hit (80+)`, `Medium (65-79)`, and `Low (<65)` based on their popularity score.

### 4. Handling Null Values (Mean Imputation)
- Checked missing values across all columns using `df.isnull().sum()`.
- Found missing (`NaN`) values in five numeric columns: `Tempo_BPM`, `Danceability`, `Energy`, `Streams_Millions`, and `Popularity_Score`.
- Filled the missing values in each of these columns with their respective **column mean** (`df[col].fillna(df[col].mean())`) and verified that zero null values remained afterward.

### 5. Insights Generated
- **Genre-wise Summary:** Grouped the data by `Genre` to compare track counts, average streams (in millions), average popularity, and danceability.
- **Top 10 Artists:** Aggregated total streams and average popularity per artist to see which artists had the highest overall reach in the dataset.
- **Year-wise Trends (2016–2025):** Looked at how average track length and streaming numbers changed across release years, finding that song durations stay fairly steady around 3.4 to 3.6 minutes.

### 6. Visualizations Created
- **Bar Chart:** Average streams (in millions) across different music genres.
- **Horizontal Bar Chart:** Top 10 most streamed artists in the dataset.
- **Line Chart:** Year-by-year trend of average streams from 2016 to 2025.
- **Scatter Plot:** Danceability vs. Popularity Score colored by Popularity Tier, showing that more danceable tracks tend to score higher in popularity.

## How to Run This Project Locally

1. Clone or download this repository.
2. Make sure `spotify_tracks_dataset.csv` and `Spotify_Data_Analysis_CIE1.ipynb` are in the same folder.
3. Install the required libraries if you don't already have them:
   ```bash
   pip install pandas numpy matplotlib seaborn jupyter
   ```
4. Open `Spotify_Data_Analysis_CIE1.ipynb` in **VS Code** or **Jupyter Notebook** and run all cells.
