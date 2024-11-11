# Spotify Audio Data Analysis

## Overview
This project explores Spotify's audio data to uncover trends in song popularity, duration, and genre characteristics over time. Through data cleaning, analysis, and visualization, we aim to gain insights into listener preferences and the evolution of music.

## Table of Contents
- [Overview](#overview)
- [Project Setup](#project-setup)
- [Data Cleaning](#data-cleaning)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Visualizations](#visualizations)
- [Conclusions](#conclusions)
- [License](#license)

## Project Setup
### Import Libraries
```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Set plot style
sns.set_style("whitegrid")
```

### Load Data
```python
# Upload files
from google.colab import files
uploaded = files.upload()

# Load datasets
df_tracks = pd.read_csv('tracks.csv')
df_genre = pd.read_csv('SpotifyFeatures.csv')
```

## Data Cleaning
1. **Handle Missing Values**: Dropped rows with missing values in essential columns.
2. **Convert Data Types**: Converted release dates to datetime and created binary encoding for the mode column.
3. **Convert Duration**: Transformed durations from milliseconds to seconds.

## Exploratory Data Analysis
This section includes summary statistics and visualizations of the data.

### Summary Statistics
```python
print(df_tracks.describe())
print(df_genre.describe())
```

## Visualizations
Here are some key visualizations derived from the analysis:

1. **Distribution of Track Popularity**
  ![image](https://github.com/user-attachments/assets/c9dde152-363c-40e9-b26e-30d5aff0c5dd)

   
2. **Average Song Duration Over Time**
 ![image](https://github.com/user-attachments/assets/46d64bde-4553-486c-862c-3b5d6d7c3cfa)


3. **Top Genres by Popularity**
![image](https://github.com/user-attachments/assets/50d9881f-dd42-4274-bcf5-655611fd553b)


4. **Average Danceability Over Time**
![image](https://github.com/user-attachments/assets/3a0c2dde-1226-48bb-87d5-1b26a60768c6)


   ![image](https://github.com/user-attachments/assets/b59ea379-91b0-4b2b-86c9-8f48856ac76f)


## Conclusions
This analysis provides valuable insights into the trends and patterns within Spotify’s audio catalog. Key findings include:

- An upward trend in average track popularity suggests growing engagement with the platform's offerings.
- Recent music tends to exhibit higher danceability and shorter average durations, indicating a shift toward rhythm-driven tracks.
- Popular genres show distinct characteristics in terms of energy and duration, guiding music recommendation systems and playlist curation.

## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
```

### Instructions
- Replace `path/to/...` with the actual paths to your images in your project directory.
- You can add more sections or modify the existing ones to better fit your project's needs. 

Feel free to let me know if you need any more changes or additions!
