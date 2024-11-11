# 📊 Netflix Data Analysis

This project analyzes Netflix's dataset to uncover trends and patterns in content offerings across different countries, genres, ratings, and years. The goal is to gain insights into Netflix’s content strategy and how it caters to different demographics globally.

## 📝 Project Overview

This analysis of Netflix data provides insights into the distribution and growth of movies and TV shows on the platform. The project focuses on understanding content expansion by category and country, analyzing target demographics, and identifying the most popular genres and ratings across different regions. 

This project is part of a series: **Project 9/30**.

## 💡 Analysis Proposal

### Objectives:
1. **Content Categorization**: Identify the most common genres and types (e.g., Comedies, Dramas) on Netflix.
2. **Demographic Targeting**: Analyze if Netflix targets specific age groups and how this varies by country.
3. **Country-Based Analysis**: Compare the content offerings of major Netflix markets, particularly the USA and India.
4. **Growth Trends**: Track content additions over time to examine growth in Netflix’s offerings.

## 📄 Dataset Overview

The dataset includes the following columns:
- `show_id`: Unique identifier for each show
- `type`: Movie or TV Show
- `title`: Title of the show
- `director`: Director's name
- `cast`: Cast list
- `country`: Country of production
- `date_added`: Date added to Netflix
- `release_year`: Original release year
- `rating`: Audience rating
- `duration`: Duration of the content (minutes for movies, seasons for TV shows)
- `listed_in`: Categories/genres
- `description`: Show’s description

### Data Source
Dataset is available on [Kaggle](https://www.kaggle.com/shivamb/netflix-shows).

---

## 🔍 Exploratory Data Analysis (EDA)

1. **Missing Data**  
   - Visualized missing values using a heatmap and handled them by removing rows with essential information missing.

   ```python
   import seaborn as sns
   import matplotlib.pyplot as plt

   plt.figure(figsize=(10,6))
   sns.heatmap(netflix_data.isnull(), cbar=False, cmap="viridis")
   plt.title("Heatmap of Missing Values")
   ```

2. **Content Growth by Country**
   - Analyzed content growth in the USA and India by year.

   ```python
   usa_india_data = netflix_data[netflix_data['country'].isin(['United States', 'India'])]
   sns.lineplot(data=usa_india_data, x='year_added', hue='country', estimator=len)
   ```

3. **Genre Analysis**
   - Counted the number of shows in each genre to identify the most popular genres.

   ```python
   genre_count = netflix_data['listed_in'].str.split(',').explode().value_counts()
   sns.barplot(x=genre_count.values, y=genre_count.index)
   ```

---

## 🧑‍💻 Key Queries and Code

1. **Movies with Type "Comedies" or Country "United Kingdom"**

   ```python
   netflix_data[(netflix_data['type'] == 'Movie') & 
                (netflix_data['listed_in'].str.contains('Comedies')) | 
                (netflix_data['country'] == 'United Kingdom')]
   ```

2. **Movies/Shows Starring "Tom Cruise"**

   ```python
   tom_cruise_count = netflix_data[netflix_data['cast'].str.contains('Tom Cruise', na=False)].shape[0]
   ```

3. **Different Ratings on Netflix**

   ```python
   ratings = netflix_data['rating'].unique()
   ```

4. **Movies with "TV-14" Rating in Canada**

   ```python
   canada_tv14 = netflix_data[(netflix_data['rating'] == 'TV-14') & 
                              (netflix_data['country'] == 'Canada') & 
                              (netflix_data['type'] == 'Movie')].shape[0]
   ```

5. **TV Shows with "R" Rating After 2018**

   ```python
   tv_shows_r = netflix_data[(netflix_data['type'] == 'TV Show') & 
                             (netflix_data['rating'] == 'R') & 
                             (netflix_data['release_year'] > 2018)].shape[0]
   ```

6. **Maximum Duration of a Movie/Show**

   ```python
   max_duration = netflix_data['duration'].max()
   ```

7. **Country with the Most TV Shows**

   ```python
   tv_shows_country = netflix_data[netflix_data['type'] == 'TV Show']['country'].value_counts().idxmax()
   ```

8. **Sorting Dataset by Year**

   ```python
   sorted_data = netflix_data.sort_values(by='release_year')
   ```

---

## 📈 Key Visualizations

1. **Growth of Content in USA vs India**  
   Analyzed the number of movies and shows added to Netflix by year for the USA and India, highlighting Netflix's content expansion in major markets.

2. **Genre Distribution**  
   Visualized the top genres across the entire Netflix library, showing audience preference by genre.

3. **Rating Distribution by Content Type**  
   Created a bar plot to illustrate how ratings vary between movies and TV shows, giving insights into Netflix's target demographics.

4. **Duration Analysis**  
   Displayed a histogram of content duration, highlighting the most common lengths for movies and TV shows on the platform.

---

## ✍️ Conclusion

This Netflix data analysis reveals significant trends, such as the dominance of the USA and India in content volume, popular genres and ratings, and a strategic approach to targeting different demographics across countries. The data indicates that Netflix has grown its library considerably over the years, with substantial expansions in both popular and niche genres. This analysis provides a clearer understanding of Netflix’s content distribution strategy and audience targeting efforts.

---

## 👤 Author

[![GitHub](https://img.shields.io/badge/GitHub-000000?style=for-the-badge&logo=github&logoColor=white)](https://github.com/shaun-mia)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/shaun-mia/)
[![Email](https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:shaunmia.cse@gmail.com)
