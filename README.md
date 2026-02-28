# DSI Cohort 8 Team Project - DS Team 05 - Topic: Infrastructure and Transportation <br>
## Bike Sharing Trends

### Project Objective

The objective of this project is to develop predictive models that accurately forecast and categorize bike rental demand using historical data from the Capital Bikeshare system (2011–2012).
Our Data Science team will develop a regression model, we aim to predict the number of bike rentals at specific times based on variables such as time of day, day of the week, weather conditions, and seasonal patterns.

To communicate insights clearly, we will design three visualizations that highlight demand trends, key drivers, and model performance. Together, these tools aim to improve decision-making, optimize bike distribution, and enhance system efficiency.

This project mirrors real-world data science applications in:
- Demand forecasting systems
- Operational decision-support systems
- Inventory optimization and resource allocation models
- Context-aware analytics

Overall, the project seeks to transform historical rental and weather data into data-driven decision tools that enhance service reliability, resource allocation, and customer satisfaction.

### Members

* Afroz Popatiya
* Andres Rojas
* Hajar Elidrissi
* Jorge Bustamante
* Michael Nweke
* Nuria Stephanie Sanchez Perez


***

### Project Question

**Regression:** Can we predict the number of bike rentals at different stations based on various factors such as time of day, day of the week, weather conditions, and local events?

### Dataset Overview
This dataset contains the hourly and daily count of rental bikes between years 2011 and 2012 in Capital bikeshare system with the corresponding weather and seasonal information.

|   |  |
|---|---|
| Source | UCI Machine Learning Repository - Bike Sharing | 
| Link | https://archive.ics.uci.edu/dataset/275/bike+sharing+dataset |  
| Author | Fanaee-T, H. (2013) |
| Instances | 17389 |
| Features | 13 |
| Period | 2011 - 2012 |


### Intended Audience
The intended audience for this project includes:
* Urban planners and transportation authorities
* Bike-sharing companies
* Policy makers working on sustainable transportation
* Business analysts and operations planners

This analysis can help these stakeholders understand bike usage patterns and make informed decisions about fleet management, infrastructure planning, and service optimization.



### Key Variables and Attributes

**Time-Based Variables**

|  Variable | Type | Description |
|---|---|---|
| dteday | Date	| date |
| yr | Categorical	| year (0: 2011, 1: 2012) | 
| mnth | Categorical | month (1 to 12) |
| hr | Categorical | hour (0 to 23)	| 
<br>

**Context Variables**
|  Variable | Type | Description |
|---|---|---|
| season | Categorical | 1:winter, 2:spring, 3:summer, 4:fall |
| weekday | Categorical | day of the week |
| holiday | Binary | weather day is holiday or not (extracted from http://dchr.dc.gov/page/holiday-schedule) |
| workingday | Binary | if day is neither weekend nor holiday is 1, otherwise is 0 |
<br>

**Weather Variables**
|  Variable | Type | Description |
|---|---|---|
| weathersit | Categorical | 1: Clear, Few clouds, Partly cloudy, Partly cloudy |
| temp | Continuous | Normalized temperature in Celsius. The values are derived via (t-t_min)/(t_max-t_min), t_min=-8, t_max=+39 (only in hourly scale) |
| atemp | Continuous | Normalized feeling temperature in Celsius. The values are derived via (t-t_min)/(t_max-t_min), t_min=-16, t_max=+50 (only in hourly scale) |
| hum | Continuous | Normalized humidity. The values are divided to 100 (max) |
| windspeed | Continuous | Normalized wind speed. The values are divided to 67 (max) |
<br>

**User Variables**
|  Variable | Type | Description |
|---|---|---|
| casual | Integer | count of casual users |
| registered | Integer | count of registered users |
| cnt | Integer | count of total rental bikes including both casual and registered |
<br>

### Data Cleaning Strategy
The dataset does not contain missing values, but some preprocessing is still required.
Cleaning steps include:
* Converting categorical variables (season, weather condition) into meaningful labels
* Removing unnecessary columns such as record index
* Checking for outliers in weather-related variables
* Creating features such as peak vs off-peak hours 

This will improve analysis accuracy and visualization clarity.


### Exploring Relationships Between Variables
Relationships can be explored using:
* Correlation analysis
* Time-series trends

Comparisons between:
* Weather conditions and rental counts
* Working days vs holidays
* Seasonal variations
* Hourly usage patterns

Visualization techniques such as scatter plots, line charts, and bar charts will help identify these relationships.



### Patterns and Trends in the Data
Expected patterns include:
* Higher rentals during warmer seasons
* Increased demand during commuting hours (morning and evening)
* Lower usage during poor weather conditions
* Higher registered user activity on working days
* Higher casual user activity on weekends and holidays

These trends provide insight into behavioral and environmental influences on bike usage.



### Suitable Libraries and Tools
The following tools are well-suited for this project:
Data Processing
* Pandas

Visualization
* Seaborn
* Plotly (for interactive visuals)

Analysis and Modeling
* Scikit-learn

