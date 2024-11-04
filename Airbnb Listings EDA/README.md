# Airbnb Listings Analysis - New York City 2024

## Introduction
This project explores the Airbnb listings dataset for New York City in 2024, focusing on various aspects such as pricing, availability, and guest reviews. The analysis employs exploratory data analysis (EDA) techniques along with geospatial visualization to derive meaningful insights into the short-term rental market.

## Dataset Overview
The dataset consists of **20,770 entries** and **22 columns**, including important features such as:
- `id`: Unique identifier for each listing
- `name`: Name of the listing
- `host_id`: Unique identifier for the host
- `neighbourhood_group`: The borough where the listing is located
- `latitude` and `longitude`: Geographical coordinates of the listing
- `room_type`: Type of room offered (e.g., entire home, private room, shared room)
- `price`: Price per night for the listing
- `number_of_reviews`: Total reviews received
- `availability_365`: Number of days the listing is available per year

### Data Overview
The dataset contains a mix of numerical and categorical data types, providing a comprehensive view of the Airbnb landscape in New York City. It includes missing values in several columns, which were addressed during the cleaning process.

## Purpose of the Analysis
The primary goals of this analysis are:
- To identify pricing trends across different neighborhoods in New York City.
- To understand the impact of availability and guest reviews on pricing.
- To visualize the geographical distribution of Airbnb listings.
- To provide actionable insights for potential hosts and guests.

## Insights and Analysis

### 1. Geographical Distribution of Listings
Using Folium, an interactive map illustrates the distribution of Airbnb listings across New York City, highlighting high-density areas, particularly in popular neighborhoods like Manhattan and Brooklyn.

### 2. Price Variation Across Neighborhoods
Markers on the map represent listings with varying price ranges, allowing for quick visual assessments of local market conditions.

### 3. Correlation Between Price and Number of Reviews
Scatter plots reveal a strong relationship between pricing and the number of reviews, indicating that competitively priced listings tend to receive more guest feedback.

### 4. Outliers in Pricing
The analysis identified outlier listings, helping hosts avoid overpricing and better align with market standards.

### 5. Feature Engineering
Creating a "price per bed" feature enabled a more nuanced comparison of properties, offering insights into competitive pricing strategies.

## Conclusion
The exploratory data analysis and geospatial visualization of Airbnb listings in New York City have provided valuable insights into the dynamics of the short-term rental market. The findings emphasize the importance of location, competitive pricing, and guest satisfaction in maximizing occupancy and profitability for hosts. 

The combination of EDA techniques and interactive visualizations empowers stakeholders to make informed decisions based on data-driven insights, enhancing their strategies within the Airbnb marketplace.

## Author Information
- **Name**: Shaun Mia
- **Email**: shaunmia.cse@gmail.com
- **LinkedIn**: [shaun-mia](https://www.linkedin.com/in/shaun-mia/)
- **GitHub**: [shaun-mia](https://github.com/shaun-mia)

## Acknowledgments
Thanks to the Airbnb data team for providing the dataset and to the open-source community for the libraries and tools used in this analysis.
