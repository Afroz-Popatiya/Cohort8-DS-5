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
* Nuria Stephanie Sanchez Perez


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
>steps for regression, how models will be out-weighted.
>the rule for our proposal
>task breakdown

### Task Breakdown
|  Task | Responsible | 
|---|---|
| Data Extract and Exploration | Jorge Bustamante	|
| Data cleansing | Jorge Bustamante	|
| Model Development: Linear Regression | Hajar Elidrissi |
| Model Development: Random Forest | Andres Rojas | 
| Visualizations | Afroz Popatiya & Nuria Stephanie Sanchez Perez | 


### Business comebacks
>State why bike sharing is important. How those results should be used.

### Risks and Unknowns for the Bike Sharing Demand Prediction Project 

**1. Data Quality and Relevance Risks**

**Risk:** <br>
Data is not representative of the current operating environment.

**Description:**<br>
The dataset covers 2011-2012. Bike-sharing usage patterns, urban infrastructure, weather patterns, and user behavior (e.g., impact of dockless bikes, scooters, and COVID-19) have likely changed significantly. A model trained on this historical data may not accurately predict demand in a future or even current context.

**Mitigation:**<br>
Acknowledge the Limitation, explicitly state in the final presentation and report that the model is a proof-of-concept based on historical data (2011-2012) and is not intended for direct deployment without retraining on contemporary data.



**Risk:** <br>
The dataset has no missing values, but may contain measurement errors or biases.

**Description:** <br>
While the UCI dataset is clean, the source data may have inherent biases. For example, weather data from a single airport station may not accurately represent micro-climates across the city. The classification of "holiday" may not perfectly align with all user segments' behavior.

**Mitigation:** <br>
During exploration, test the model's sensitivity to key variables. For instance, does a slight variation in reported temperature (±1-2°C) lead to a large swing in predictions? This can highlight over-reliance on a potentially noisy feature.
Create robust features. For example, instead of relying solely on the binary holiday variable, we could create a feature that combines holidays with the day of the week to better capture long-weekend effects.

**Risk:** <br>
Feature limitations & lack of contextual data.

**Description:** <br>
The dataset lacks crucial information that likely drives demand, such as:
* Special Events: Concerts, festivals, sports games, or political rallies.
* Infrastructure Changes: New bike lanes, station closures, or the introduction of competing services (e.g., e-scooters).
* Real-time Data: Current bike availability at stations, which heavily influences a user's decision to rent.

**Mitigation:** <br>
Error Analysis: Systematically analyze the model's largest prediction errors. If errors cluster on specific dates, we can retrospectively research if a special event occurred, providing a qualitative explanation for the model's failure.<br>
Proxy Variables: Explore creating proxy variables. For example, a sudden, large anomaly in rentals on a non-holiday weekday might be cross-referenced with a major event calendar (if we can find one online for 2011-2012) during the error analysis phase.<br>
Scope Definition: Clearly define that the model predicts baseline demand based on routine patterns (weather, time) and explicitly state that it does not account for special events, which would require additional data sources. 

**2. Modeling and Methodological Risks**

**Risk:** <br>
Overfitting to Seasonal and Weather Patterns of 2011-2012.

**Description:** <br>
The model might learn patterns specific to the weather and seasonal transitions of those two years. For instance, if 2012 had an unusually warm spring, the model might incorrectly associate that specific temperature range with high demand, failing to predict demand for a typical, cooler spring.

**Mitigation:** <br>
Simpler, Robust Models: Prioritize models like regularized linear regression (Ridge, Lasso) or tree-based methods with limited depth (e.g., Gradient Boosting with careful tuning) that are less prone to overfitting than very complex, unregularized models.<br>
Cross-Validation: Use time-series cross-validation (e.g., expanding window or sliding window) instead of random k-fold cross-validation. This ensures the model is always trained on past data and validated on future data, simulating a real-world forecasting scenario and testing its ability to generalize to new time periods.

**Risk:** <br>
Seasonality Changes and Shifts in User Behavior.

**Description:** <br>
The fundamental patterns might shift (concept drift). For example, the morning commute peak in 2011 might have been at 8:00 AM, but cultural shifts could move it to 9:00 AM. The model would be blind to this.

**Mitigation:** <br>
Feature Engineering with Domain Knowledge: Create features that capture the reason for the pattern, not just the pattern itself. For example, an is_commute_hour feature (based on typical 8-9 AM and 5-6 PM slots) encodes domain knowledge. Even if the peak shifts slightly, this binary feature remains relevant.<br>
Modular Design: Frame the solution as a system where the model is one component. In a real-world application, this model would be part of a larger MLOps pipeline that continuously monitors prediction error and triggers retraining when significant drift is detected. 

**3. External Factors and Unknowns**
**Risk:** <br>
Unforeseen external shocks.

**Description:** <br>
Major events like a pandemic (COVID-19), economic downturns, sudden policy changes (e.g., free public transport days), or extreme weather events (e.g., a hurricane) are not represented in the training data. The model's predictions would be completely invalid under such conditions.

**Mitigation:** <br>
Model Limitations as a Feature: This is a fundamental unknown that cannot be fully mitigated. The best approach is to be transparent. The final report will include a section on "Model Limitations" that explicitly states the model assumes a stable operating environment and is not designed to predict demand during unprecedented external shocks. This sets appropriate expectations for stakeholders.

**Risk:** <br>
The "Unknown Unknowns".

**Description:** <br>
There may be critical factors influencing bike demand that we, as a team, haven't even considered. This could be anything from the rise of ride-sharing apps to changes in DC's tourism demographics.

**Mitigation:** <br>
Thorough Exploratory Data Analysis (EDA): A deep and curious EDA process is the first line of defense. By visualizing data from multiple angles, we might uncover unexpected patterns that prompt new questions and hypotheses about hidden drivers.<br>
Peer Review and Stakeholder Feedback: During the project, we will present our findings and assumptions to our cohort and instructors. External perspectives can challenge our thinking and point out factors we may have missed. In a real-world scenario, presenting to a domain expert (e.g., a Capital Bikeshare operations manager) would be critical for uncovering these blind spots.

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

