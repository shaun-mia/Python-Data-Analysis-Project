### **Google Play Store Apps Analysis Proposal**

#### **1. Introduction**
The purpose of this analysis is to explore, clean, and analyze the Google Play Store dataset to gain insights into app ratings, categories, reviews, and pricing. This project aims to answer various queries about the dataset and provide statistical insights and visualizations to help understand trends and patterns.

#### **2. Dataset Overview**
The dataset consists of 13 columns and 10,841 rows with information on app names, categories, ratings, reviews, installation count, price, content rating, and more.

#### **3. Dataset Information**
- ** Dataset**: [Kaggle](https://www.kaggle.com/datasets/lava18/google-play-store-apps?select=googleplaystore.csv)
- **Columns in the Dataset**:
  - `App`: Name of the app
  - `Category`: App category
  - `Rating`: User rating
  - `Reviews`: Number of reviews
  - `Size`: Size of the app
  - `Installs`: Number of installations
  - `Type`: Free or Paid
  - `Price`: Price of the app
  - `Content Rating`: Age group the app is suited for
  - `Genres`: App genre
  - `Last Updated`: Date of the last update
  - `Current Ver`: Current version
  - `Android Ver`: Required Android version

#### **4. Data Preprocessing & Cleaning Steps**
1. Convert data types for `Reviews`, `Installs`, and `Price` columns.
2. Handle missing values in `Rating`, `Type`, `Content Rating`, `Current Ver`, and `Android Ver`.
3. Remove outliers in the `Rating` column (keeping ratings between 1 and 5).

---

#### **5. Analysis Queries**
Here's the list of analysis queries, followed by code implementation.

#### **6. Code Implementation and Analysis**

```python
# Importing Libraries
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

# Loading Dataset
file_path = '/content/drive/MyDrive/Data Analysis/Python Project/Google Play Store Apps Analysis/googleplaystore.csv'
df = pd.read_csv(file_path)

# Displaying First 5 Rows
df.head()
```

---

#### **Query 1: Display the First 5 Rows of the Dataset**

```python
# Displaying First 5 Rows
df.head()
```

#### **Query 2: Check the Last 3 Rows of the Dataset**

```python
# Displaying Last 3 Rows
df.tail(3)
```

#### **Query 3: Find the Shape of the Dataset**

```python
# Shape of the Dataset
df.shape
```

#### **Query 4: Get Dataset Information**

```python
# Dataset Information
df.info()
```

#### **Query 5: Get Overall Statistics About the Dataframe**

```python
# Overall Statistics
df.describe()
```

#### **Query 6: Total Number of App Titles Containing "Astrology"**

```python
# Apps with "Astrology" in Title
astrology_apps = df[df['App'].str.contains('Astrology', case=False, na=False)]
astrology_apps_count = len(astrology_apps)
```

#### **Query 7: Find Average App Rating**

```python
# Average Rating
average_rating = df['Rating'].mean()
```

#### **Query 8: Find Total Number of Unique Categories**

```python
# Unique Categories
unique_categories = df['Category'].nunique()
```

#### **Query 9: Which Category Has the Highest Average Rating?**

```python
# Category with Highest Average Rating
highest_avg_rating_category = df.groupby('Category')['Rating'].mean().idxmax()
highest_avg_rating = df.groupby('Category')['Rating'].mean().max()
```

#### **Query 10: Total Number of Apps Having 5-Star Rating**

```python
# Total Apps with 5-Star Rating
five_star_apps = len(df[df['Rating'] == 5])
```

#### **Query 11: Find the Average Value of Reviews**

```python
# Convert Reviews to Numeric Type
df['Reviews'] = pd.to_numeric(df['Reviews'], errors='coerce')
average_reviews = df['Reviews'].mean()
```

#### **Query 12: Find Total Number of Free and Paid Apps**

```python
# Total Number of Free and Paid Apps
free_paid_counts = df['Type'].value_counts()
```

#### **Query 13: Which App Has the Maximum Reviews?**

```python
# App with Maximum Reviews
max_reviews_app = df.loc[df['Reviews'].idxmax()]['App']
max_reviews_count = df['Reviews'].max()
```

#### **Query 14: Display the Top 5 Apps with the Highest Reviews**

```python
# Top 5 Apps with Highest Reviews
top_5_reviews = df.nlargest(5, 'Reviews')[['App', 'Reviews']]
```

#### **Query 15: Find Average Rating of Free and Paid Apps**

```python
# Average Rating for Free and Paid Apps
free_paid_avg_rating = df.groupby('Type')['Rating'].mean()
```

#### **Query 16: Display Top 5 Apps with Maximum Installs**

```python
# Remove non-numeric values in 'Installs' column (e.g., 'Free')
df = df[df['Installs'] != 'Free']

# Convert 'Installs' to numeric by removing commas and '+' signs
df['Installs'] = df['Installs'].str.replace('[+,]', '', regex=True).astype(float)

# Now, get the top 5 apps with maximum installs
top_5_installs = df.nlargest(5, 'Installs')[['App', 'Installs']]
top_5_installs

```

---

#### **Additional Queries and Visualizations**

**1. Distribution of App Ratings**

```python
# Distribution of Ratings
plt.figure(figsize=(10,6))
sns.histplot(df['Rating'].dropna(), bins=20, kde=True)
plt.title("Distribution of App Ratings")
plt.xlabel("Rating")
plt.ylabel("Frequency")
plt.show()
```

**2. Average Rating by Category (Bar Plot)**

```python
# Average Rating by Category
plt.figure(figsize=(15,8))
category_ratings = df.groupby('Category')['Rating'].mean().sort_values(ascending=False)
sns.barplot(x=category_ratings.index, y=category_ratings.values)
plt.xticks(rotation=90)
plt.title("Average Rating by Category")
plt.xlabel("Category")
plt.ylabel("Average Rating")
plt.show()
```

**3. Total Number of Apps by Content Rating**

```python
# Total Number of Apps by Content Rating
plt.figure(figsize=(10,6))
sns.countplot(x='Content Rating', data=df)
plt.title("Total Number of Apps by Content Rating")
plt.xlabel("Content Rating")
plt.ylabel("Count")
plt.show()
```

---

#### **7. Conclusion**
This analysis provided valuable insights into Google Play Store apps, such as:
- Average rating of apps and variations across categories
- Distribution and trends in free vs. paid apps
- Reviews and installs associated with the most popular apps

---

## 👤 Author

[![GitHub](https://img.shields.io/badge/GitHub-000000?style=for-the-badge&logo=github&logoColor=white)](https://github.com/shaun-mia)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/shaun-mia/)
[![Email](https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:shaunmia.cse@gmail.com)
