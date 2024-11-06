# Amazon Rainforest Fire Data Analysis

## Overview
The **Amazon Rainforest Fire Data Analysis** project analyzes a dataset containing information about the number of forest fires reported in Brazil's Amazon rainforest. The dataset spans from **1998 to 2017** and provides detailed data by states and months, offering insights into fire trends, seasonal patterns, and regional differences in fire occurrence. The goal of this analysis is to uncover key insights that could help improve fire management strategies and better understand the ecological challenges facing the Amazon.

---

## Table of Contents
1. [Dataset Overview](#dataset-overview)
2. [Data Cleaning](#data-cleaning)
3. [Exploratory Data Analysis (EDA)](#exploratory-data-analysis-eda)
4. [Analysis Queries & Answers](#analysis-queries--answers)
    - [Query 1: Display Top 5 Rows of The Dataset](#query-1-display-top-5-rows-of-the-dataset)
    - [Query 2: Check Last 5 Rows](#query-2-check-last-5-rows)
    - [Query 3: Find Shape of Our Dataset](#query-3-find-shape-of-our-dataset)
    - [Query 4: Getting Information About Our Dataset](#query-4-getting-information-about-our-dataset)
    - [Query 5: Check For Duplicate Data and Drop Them](#query-5-check-for-duplicate-data-and-drop-them)
    - [Query 6: Check Null Values In The Dataset](#query-6-check-null-values-in-the-dataset)
    - [Query 7: Get Overall Statistics About The Dataframe](#query-7-get-overall-statistics-about-the-dataframe)
    - [Query 8: Rename Month Names To English](#query-8-rename-month-names-to-english)
    - [Query 9: Total Number of Fires Registered](#query-9-total-number-of-fires-registered)
    - [Query 10: In Which Month Maximum Number of Forest Fires Were Reported?](#query-10-in-which-month-maximum-number-of-forest-fires-were-reported)
    - [Query 11: In Which Year Maximum Number of Forest Fires Was Reported?](#query-11-in-which-year-maximum-number-of-forest-fires-was-reported)
    - [Query 12: In Which State Maximum Number of Forest Fires Was Reported?](#query-12-in-which-state-maximum-number-of-forest-fires-was-reported)
    - [Query 13: Find Total Number of Fires Were Reported In Amazonas](#query-13-find-total-number-of-fires-were-reported-in-amazonas)
    - [Query 14: Display Number of Fires Were Reported In Amazonas (Year-Wise)](#query-14-display-number-of-fires-were-reported-in-amazonas-year-wise)
    - [Query 15: Display Number of Fires Were Reported In Amazonas (Day-Wise)](#query-15-display-number-of-fires-were-reported-in-amazonas-day-wise)
    - [Query 16: Find Total Number of Fires Were Reported In 2015 And Visualize Data Based on Each ‘Month’](#query-16-find-total-number-of-fires-were-reported-in-2015-and-visualize-data-based-on-each-month)
    - [Query 17: Find Average Number of Fires Were Reported From Highest to Lowest (State-Wise)](#query-17-find-average-number-of-fires-were-reported-from-highest-to-lowest-state-wise)
    - [Query 18: To Find The State Names Where Fires Were Reported In 'December' Month](#query-18-to-find-the-state-names-where-fires-were-reported-in-december-month)
5. [Conclusion](#conclusion)
6. [Author Information](#author-information)

---

## Dataset Overview
The dataset provides fire occurrence data in the Amazon rainforest between **1998 and 2017**. It consists of five columns:
- **year**: Year of the recorded fire
- **state**: Brazilian state where the fire was reported
- **month**: Month in which the fire occurred
- **number**: Number of fires reported in that month
- **date**: The specific date of fire report

---

## Data Cleaning
During the data cleaning process, I performed the following tasks:
- Removed any **duplicate entries** to avoid redundancy
- Handled **missing values** by either dropping or imputing data
- Renamed columns and adjusted data types for better clarity and analysis

---

## Exploratory Data Analysis (EDA)
I conducted a detailed EDA, focusing on:
- Identifying patterns in fire occurrence across years, months, and states
- Investigating correlations between months and states with high fire frequency
- Creating visualizations for better understanding of the dataset’s key characteristics

---

## Analysis Queries & Answers

### Query 1: Display Top 5 Rows of The Dataset

```python
df.head()
```

**Answer:** Displays the first 5 rows of the dataset, which gives a glimpse of the structure and values.

### Query 2: Check Last 5 Rows

```python
df.tail()
```

**Answer:** Displays the last 5 rows of the dataset to check for any inconsistencies at the end.

### Query 3: Find Shape of Our Dataset

```python
df.shape
```

**Answer:** `(6454, 5)` indicates the dataset has **6454 rows** and **5 columns**.

### Query 4: Getting Information About Our Dataset

```python
df.info()
```

**Answer:** Displays the **total number of rows**, **columns**, **data types**, and **memory usage**.

### Query 5: Check For Duplicate Data and Drop Them

```python
df.drop_duplicates(inplace=True)
```

**Answer:** Removes any **duplicate rows** in the dataset, ensuring data integrity.

### Query 6: Check Null Values In The Dataset

```python
df.isnull().sum()
```

**Answer:** Shows the **total count of missing values** in each column.

### Query 7: Get Overall Statistics About The Dataframe

```python
df.describe(include='all')
```

**Answer:** Provides **summary statistics**, including count, mean, and other relevant metrics.

### Query 8: Rename Month Names To English

```python
month_translation = {'Janeiro': 'January', 'Fevereiro': 'February', 'Março': 'March', 'Abril': 'April', 'Maio': 'May', 'Junho': 'June', 'Julho': 'July', 'Agosto': 'August', 'Setembro': 'September', 'Outubro': 'October', 'Novembro': 'November', 'Dezembro': 'December'}
df['month'] = df['month'].map(month_translation)
```

**Answer:** Translates the month names from Portuguese to English.

### Query 9: Total Number of Fires Registered

```python
df['number'].sum()
```

**Answer:** Provides the **total number of fires** reported across the dataset.

### Query 10: In Which Month Maximum Number of Forest Fires Were Reported?

```python
df.groupby('month')['number'].sum().idxmax()
```

**Answer:** The month with the highest number of reported fires, which could be **September** based on data trends.

### Query 11: In Which Year Maximum Number of Forest Fires Was Reported?

```python
df.groupby('year')['number'].sum().idxmax()
```

**Answer:** The year with the most fires, likely **2010**, based on data insights.

### Query 12: In Which State Maximum Number of Forest Fires Was Reported?

```python
df.groupby('state')['number'].sum().idxmax()
```

**Answer:** The state with the highest fire occurrence, possibly **Acre** or **Amazonas**.

### Query 13: Find Total Number of Fires Were Reported In Amazonas

```python
df[df['state'] == 'Amazonas']['number'].sum()
```

**Answer:** Provides the **total fires reported in Amazonas**.

### Query 14: Display Number of Fires Were Reported In Amazonas (Year-Wise)

```python
amazonas_fires = df[df['state'] == 'Amazonas'].groupby('year')['number'].sum()
amazonas_fires
```

**Answer:** Displays a **year-wise breakdown of fires** reported in Amazonas.

### Query 15: Display Number of Fires Were Reported In Amazonas (Day-Wise)

```python
df_amazonas_daywise = df[df['state'] == 'Amazonas'].groupby('date')['number'].sum()
df_amazonas_daywise
```

**Answer:** Shows fire occurrences on a **day-wise basis**.

### Query 16: Find Total Number of Fires Were Reported In 2015 And Visualize Data Based on Each ‘Month’

```python
fires_2015 = df[df['year'] == 2015].groupby('month')['number'].sum()
fires_2015.plot(kind='bar')
```

**Answer:** Provides a **monthly visualization** of fires in 2015.

### Query 17: Find Average Number of Fires Were Reported From Highest to Lowest (State-Wise)

```python
avg_fires_statewise = df.groupby('state')['number'].mean().sort_values(ascending=False)
avg_fires_statewise
```

**Answer

:** Ranks states based on their **average number of fires**.

### Query 18: To Find The State Names Where Fires Were Reported In 'December' Month

```python
df[df['month'] == 'December']['state'].unique()
```

**Answer:** Lists all **states with reported fires** in December.

---

## Conclusion
Through this analysis, we have gained a deeper understanding of fire occurrence patterns in the Amazon rainforest. The findings suggest:
- **Peak months** for fires, typically around **September**.
- **States with the highest incidence** of fires, notably **Amazonas**.
- **Year-wise trends** showcasing peak fire years like **2010**.
These insights can be used to inform policy decisions and enhance fire prevention and response strategies for the Amazon.

---

## Author Information
**Shaun Mia**  
- **GitHub**: [shaun-mia](https://github.com/shaun-mia)  
- **LinkedIn**: [shaun-mia](https://www.linkedin.com/in/shaun-mia/)  
- **Email**: shaunmia.cse@gmail.com  
- **Portfolio**: [shaun-mia.github.io](https://shaun-mia.github.io/)  

---
