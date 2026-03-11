# DSI Cohort 8 Team Project - DS Team 05 - Topic: Infrastructure and Transportation <br>
## Bike Sharing Trends

*   [Project Objective](#project-objective)
    - [Members](#members)
    - [Team Reflection Videos](#team-reflection-videos)
*   [Project Question](#project-question)
*   [Dataset Overview](#dataset-overview)
*   [Intended Audience](#intended-audience)
*   [Task Breakdown](#task-breakdown)
*   [Business Context](#business-context)
*   [Risks and Unknowns](#risks-and-unknowns)
*   [Key Variables and Attributes](#key-variables-and-attributes)
*   [Data Cleaning Strategy](#data-cleaning-strategy)
*   [Exploring Relationships Between Variables](#exploring-relationships-between-variables)
*   [Patterns and Trends in the Data](#patterns-and-trends-in-the-data)
*   [Suitable Libraries and Tools](#suitable-libraries-and-tools)



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
* Nuria Stephanie Sanchez Perez


### Team Reflection Videos
* [Afroz Popatiya](https://drive.google.com/file/d/11kVmpLGC4ffcmlNsbGGTCZ0nmfrD95Eb/view?usp=sharing)
* [Andres Rojas](https://1drv.ms/f/c/20021ae7050179f4/IgBZK0rQavnPRIpvx26vrrPWAWO1QbDle80NfkFkCqnxZ7M?e=MJwoLF)
* [Hajar Elidrissi](https://drive.google.com/file/d/1wLvdGY-3ZVph9SUcEWYlCgYFkjpQbwpW/view?usp=sharing)
* [Jorge Bustamante](https://drive.google.com/drive/folders/1wNTYQzMBC9XB87g3JjqzjNKpCdumQ-Ht?usp=sharing)
* [Nuria S Sanchez P](https://drive.google.com/file/d/1IR-b-gRkgn6xREFwpEVDcQeml_2-VhP4/view?usp=sharing)


***

### Project Question

**Regression:** 

Can we predict the number of bike rentals for a giving hour based on various factors such as time of day, day of the week, weather conditions, and calendar(holiday, workinday)?


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

### Analytical Plan

This project will aim to predict hourly bike rental demand using historical bike-sharing data and weather-related variables. Since the target variable (cnt) is continuous, the problem will be treated as a regression task.

The analysis will begin with exploratory data analysis (EDA) to understand the dataset, check for missing values, and explore patterns in rental demand across time and weather variables such as hour, season, temperature, humidity, and working day.

Next, several regression models will be tested. Linear Regression (OLS) and Ridge Regression will serve as baseline models to evaluate whether linear relationships between features and rental demand provide reasonable predictive performance. A Random Forest Regressor will also be implemented to capture potential nonlinear relationships and interactions between variables.

Model performance will be evaluated using RMSE, MAE, and R² on a held-out test set. The model with the best predictive performance will be selected for final predictions and visualization of rental demand.

The planned workflow will follow these steps:
data preprocessing → EDA → baseline regression models → Random Forest modeling → model evaluation → final prediction and visualizations.

### Task Breakdown
|  Task | Responsible | 
|---|---|
| Data Extract and Exploration | Jorge Bustamante	|
| Data cleansing | Jorge Bustamante	|
| Model Development: Linear Regression | Hajar Elidrissi |
| Model Development: Random Forest | Andres Rojas | 
| Visualizations | Afroz Popatiya & Nuria Stephanie Sanchez Perez | 


### Business Context

Accurately predicting bike-sharing demand is important for both bike-sharing companies and urban planners. For bike-sharing operators, demand forecasting can help optimize bike availability, fleet distribution, and station management, ensuring that bikes are available where and when users need them. This can improve customer satisfaction and operational efficiency.

For urban planners, understanding patterns in bike usage can support transportation planning, infrastructure development, and sustainable mobility initiatives. Insights from demand prediction can help identify peak usage periods, high-demand areas, and the influence of weather or seasonal factors on ridership. These insights can inform decisions related to bike lane expansion, station placement, and integration with other public transportation systems.

Overall, predictive models of bike rental demand can support data-driven decision-making that improves urban mobility and promotes more efficient and sustainable transportation systems.

### Risks and Unknowns

Several factors in the dataset could affect model performance. For example, weather variables such as temperature, humidity, and windspeed may contain noise or measurement errors that could influence predictions. In addition, the dataset does not include external factors such as public events, additional local holidays, or changes in bike infrastructure, which may also affect rental demand.

Some variables are also simplified indicators. For instance, workingday only distinguishes working days from weekends or holidays, but it does not capture variations such as school schedules or special events. Similarly, the weathersit variable groups weather conditions into broad categories, which may hide more detailed weather effects.

The dataset only covers 2011–2012, so it may not reflect more recent changes in bike-sharing usage, infrastructure, or commuting behavior. As a result, the model may capture historical demand patterns that differ from current usage trends.

**Mitigation:**<br>
We acknowledge the limitations this model presents, and will use it as a precursor to inspire future models with new data.

To mitigate these risks, the project will include data cleaning and exploratory analysis, testing multiple models to compare performance, and evaluating results using RMSE, MAE, and R² on a held-out test set. This approach helps identify the model that best generalizes within the available data.

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

