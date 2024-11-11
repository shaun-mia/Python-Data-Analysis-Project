

# Heart Disease Analysis 📊

### Python Data Analysis Project

This project analyzes a heart disease dataset to identify factors that influence the likelihood of heart disease. Using Python, we explore data patterns, visualize important features, and highlight the relationships between different health indicators.

## Project Overview

This analysis project includes:
- **Data Collection**: Obtained the heart disease dataset from [Kaggle](https://www.kaggle.com/datasets/johnsmith88/heart-disease-dataset)
- **Data Cleaning & Exploration**: Handled duplicates, performed descriptive analysis, and visualized important correlations.
- **Key Findings**: Insights into age, sex, cholesterol levels, and other health metrics as they relate to heart disease.

## Libraries Used
- **Pandas** for data manipulation
- **Matplotlib** and **Seaborn** for data visualization

---

## Project Workflow

1. **Data Import**  
   Import essential libraries and the heart disease dataset.
   ```python
   import pandas as pd
   import matplotlib.pyplot as plt
   import seaborn as sns
   data = pd.read_csv("heart.csv")
   ```

2. **Data Cleaning**  
   - Checked for missing values and duplicates.
   - Summary of the cleaned data:
     - **Shape**: 302 records, 14 features after duplicate removal.

3. **Data Analysis**  
   - **Descriptive Statistics**:
     - Average Age: 54
     - Blood Pressure Range: 94–200 mmHg
   - **Gender Distribution**:
     - Males make up the majority of records, providing insights into gender-related heart disease patterns.

   ![Gender Distribution by Heart Disease Status](https://github.com/user-attachments/assets/b1dad54f-10ec-43e8-8c49-528718f4ce0a)


4. **Visualizations**  
   - **Correlation Heatmap**: Displays relationships between features.
     ![Correlation Heatmap](https://github.com/user-attachments/assets/fac218e4-69d8-4c58-914c-f6104137807c)

   - **Distribution of Heart Disease**:
     - Shows the count of patients with and without heart disease.
       ![Heart Disease Count](https://github.com/user-attachments/assets/7c4d8ba2-fd16-496e-9410-67650010eacc)


5. **Additional Findings**  
   - **Age Distribution**: Analyzed the age group distribution among patients.
     ![Age Distribution](https://github.com/user-attachments/assets/0c6245b1-61a8-415d-978d-0c3a0d5a8db6)

   - **Cholesterol Levels**: High cholesterol levels correlate with higher heart disease risk.
   - **Blood Pressure and Heart Disease**:
     - Blood pressure trends with age and sex, providing clues about blood pressure management.
       ![image](https://github.com/user-attachments/assets/3310aec1-bbf2-4d7e-92d4-d17b6b840be7)


---

## Summary and Next Steps

- This project highlighted several health indicators that may influence heart disease.
- Future Steps:
  - **Feature Engineering**: Enhance data quality by creating additional features.
  - **Machine Learning**: Build predictive models to estimate heart disease risk.
  - **Model Evaluation**: Assess model accuracy for real-world applications.

--- 

## Contact

Created by Shaun Mia  
[LinkedIn](https://www.linkedin.com/in/shaun-mia/) | [GitHub](https://github.com/shaun-mia/)

---
