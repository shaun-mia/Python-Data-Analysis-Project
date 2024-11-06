### **Police Vehicle Checking Analysis**

---

### **Purpose of Analysis**
The purpose of this project is to analyze police vehicle stop data to uncover trends and insights, particularly focusing on gender disparities, violation types, search rates, and other factors that may affect the outcome of stops. Using Python for data analysis allows us to perform detailed data cleaning, filtering, grouping, and visualization, helping to understand how various factors influence police stops.

---

### **Dataset Overview**
The dataset used in this project includes records of police stops with the following columns:

- **stop_date** and **stop_time**: Date and time of each stop
- **country_name**: Name of the country (all null in this dataset)
- **driver_gender**: Gender of the driver (with some missing values)
- **driver_age**: Age of the driver
- **driver_race**: Race of the driver
- **violation** and **violation_raw**: Specific violation committed
- **search_conducted** and **search_type**: If a search was conducted and the type of search
- **stop_outcome**: Outcome of the stop
- **is_arrested**: Indicates if an arrest was made
- **stop_duration**: Duration of the stop (categorized)
- **drugs_related_stop**: Indicates if the stop was related to drugs

**Dataset Shape**: 65535 rows and 15 columns.

---

### **Data Cleaning and Preparation**

**Step 1: Remove Columns with Only Missing Values**

```python
import pandas as pd

# Load data
df = pd.read_csv('/content/drive/MyDrive/Data Analysis/Python Project/Police Vehicle Checking Analysis/Police Vehicle Checking Dataset.csv')

# Drop columns with all missing values
df = df.dropna(axis=1, how='all')
print(df.info())  # to confirm the column has been removed
```

**Step 2: Handle Missing Data**

Some columns, like `driver_gender`, `driver_age`, `driver_race`, and `stop_outcome`, contain missing values. We can use selective filtering or aggregation techniques to handle these missing values in the analyses.

---

### **Questions and Queries**

#### **Q1: Data Cleaning - Remove Columns with Only Missing Values**

- **Query**: Drop any columns that contain only missing values.
  
  ```python
  # Drop columns with only missing values
  df = df.dropna(axis=1, how='all')
  ```

#### **Q2: For Speeding, Were Men or Women Stopped More Often?**

- **Query**: For speeding violations, determine if men or women were stopped more frequently.

  ```python
  # Filter for speeding violations
  speeding_data = df[df['violation'] == 'Speeding']

  # Count stops by gender
  gender_counts = speeding_data['driver_gender'].value_counts()
  print(gender_counts)
  ```

- **Visualization**:

  ```python
  import matplotlib.pyplot as plt

  gender_counts.plot(kind='bar', title='Speeding Violations by Gender')
  plt.xlabel('Gender')
  plt.ylabel('Count')
  plt.show()
  ```

#### **Q3: Does Gender Affect Who Gets Searched During a Stop?**

- **Query**: Analyze if gender influences the likelihood of a search being conducted during a stop.

  ```python
  # Calculate search rate by gender
  search_rate_by_gender = df.groupby('driver_gender')['search_conducted'].mean()
  print(search_rate_by_gender)
  ```

- **Visualization**:

  ```python
  search_rate_by_gender.plot(kind='bar', title='Search Rate by Gender')
  plt.xlabel('Gender')
  plt.ylabel('Search Rate')
  plt.show()
  ```

#### **Q4: What is the Mean Stop Duration?**

- **Query**: Calculate the mean stop duration after mapping categorical stop durations to numeric values.

  ```python
  # Map stop_duration categories to numeric values
  stop_duration_mapping = {'0-15 Min': 7.5, '16-30 Min': 22.5, '30+ Min': 45}
  df['stop_duration_mapped'] = df['stop_duration'].map(stop_duration_mapping)

  # Calculate mean stop duration
  mean_stop_duration = df['stop_duration_mapped'].mean()
  print(f"Mean Stop Duration: {mean_stop_duration} minutes")
  ```

#### **Q5: Compare Age Distributions for Each Violation**

- **Query**: Compare the age distribution of drivers for each type of violation.

  ```python
  # Group by violation and describe age distribution
  age_distribution = df.groupby('violation')['driver_age'].describe()
  print(age_distribution)
  ```

- **Visualization**:

  ```python
  import seaborn as sns

  plt.figure(figsize=(10, 6))
  sns.boxplot(x='violation', y='driver_age', data=df)
  plt.title('Age Distribution by Violation')
  plt.xticks(rotation=45)
  plt.show()
  ```

---

### **Additional Queries**

#### **1. Correlation Analysis**

- **Query**: Examine correlations between numerical features (e.g., `driver_age`, `stop_duration_mapped`).

  ```python
  # Calculate correlation matrix
  correlation_matrix = df[['driver_age', 'stop_duration_mapped']].corr()
  print(correlation_matrix)
  ```

- **Visualization**:

  ```python
  import seaborn as sns

  sns.heatmap(correlation_matrix, annot=True, cmap='coolwarm')
  plt.title('Correlation Matrix')
  plt.show()
  ```

#### **2. Search Rate Based on Violation Type**

- **Query**: Analyze which types of violations lead to searches most often.

  ```python
  # Calculate search rate by violation
  search_rate_by_violation = df.groupby('violation')['search_conducted'].mean()
  print(search_rate_by_violation)
  ```

- **Visualization**:

  ```python
  search_rate_by_violation.plot(kind='bar', title='Search Rate by Violation Type')
  plt.xlabel('Violation')
  plt.ylabel('Search Rate')
  plt.xticks(rotation=45)
  plt.show()
  ```

#### **3. Stop Outcomes by Driver Race**

- **Query**: Determine if the stop outcome varies significantly by driver race.

  ```python
  # Group by race and stop outcome
  outcomes_by_race = df.groupby(['driver_race', 'stop_outcome']).size().unstack()
  print(outcomes_by_race)
  ```

- **Visualization**:

  ```python
  outcomes_by_race.plot(kind='bar', stacked=True, title='Stop Outcomes by Driver Race')
  plt.xlabel('Driver Race')
  plt.ylabel('Count')
  plt.xticks(rotation=45)
  plt.show()
  ```

---

### **Conclusion**

This project provided insights into how gender, age, and race may influence various aspects of police stops, such as search rates and stop outcomes. The findings were visualized to make trends and differences more interpretable. The analysis revealed significant insights into police stops based on gender, age distributions across violations, and variations in search rates and stop outcomes based on demographic factors.
---

## About the Author

For questions or further information:

- **Name**: Shaun Mia
- **Email**: shaunmia.cse@gmail.com
- **LinkedIn**: [Shaun Mia](https://www.linkedin.com/in/shaun-mia/)
- **GitHub**: [shaun-mia](https://github.com/shaun-mia)
