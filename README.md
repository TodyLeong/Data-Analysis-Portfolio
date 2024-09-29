# Pure Gym Data Analysis

## Overview
This project focuses on analysing member behavior and class attendance at PureGym to optimise class schedules, reduce cancellations and no-shows, and improve overall member satisfaction. The analysis covers various metrics such as class popularity, attendance patterns, waitlist management, and gym capacity utilisation. It addresses key questions around class performance, member participation trends, and resource optimisation.

## Business Background and Key Questions
PureGym, a leading UK gym chain, is facing challenges with underperforming classes, high cancellation rates, and no-shows, which negatively impact member satisfaction and overall gym performance. To address these concerns, this analysis aims to:
- **Identify Class Popularity**: Determine which classes are most and least popular across different demographics (gender, age) and times of the day.
- **Attendance Trend**s: Analyse attendance patterns across the week, comparing weekdays to weekends, and identifying days with significant or low attendance.
- **Class Optimisation**: Assess underperforming classes to determine whether they should be rescheduled, reduced, or replaced to better align with member preferences.
- **Capacity Utilisation**: Explore how time of day impacts class capacity utilisation and find ways to maximise resource use.
- **Member Engagement**: Suggest ways to optimise engagement by reducing cancellations, no-shows, and improving attendance for least utilised classes.

## Data Cleaning and Preparation
### Steps Taken:
1. **Initial Data Exploration**
   - Used `class_data.info()` to understand the data types and non-null counts of each column.
   - Used `class_data.describe()` to generate summary statistics for numerical columns.
2. **Handling Missing Values**
   - Checked for missing values to determine if any imputation or removal was needed.
3. **Remove Redundant Columns**
   - Identified and removed columns that were not useful for analysis.
4. **Check for Duplicates**
   - Checked for and removed duplicate records to ensure data integrity.

## Data Analysis Approach
### Tools and Libraries
This analysis mainly focuses on **Python**.
#### Libraries Used
- **Pandas (`import pandas as pd`)**: 
  - For data manipulation like grouping, aggregating, and merging.
- **NumPy (`import numpy as np`)**: 
  - For numerical operations and data normalization.
- **Matplotlib (`import matplotlib.pyplot as plt`)**: 
  - For visualizations such as bar charts and histograms.
- **Seaborn (`import seaborn as sns`)**: 
  - For statistical graphics like heatmaps and pair plots.
- **Statsmodels (`import statsmodels.api as sm`, `import statsmodels.stats.api as sms`)**: 
  - For statistical modeling and hypothesis testing.
- **Scikit-Learn (`import sklearn`)**: 
  - For predictive modeling and regression analysis.

## Key Insights and Findings
1. **Class Performance**:
   - Popular classes like "Cycle" and "Legs, Bums, & Tums" (LBT) had the highest cancellation and non-attendance rates, indicating potential dissatisfaction due to overbooking.
   - 
   - Certain classes like "Move Your Mind Circuits" and "Learn to Run" had very low participation and are candidates for removal or rescheduling.
     
2. **Day of the Week Trends**:
   - **Wednesdays** have the highest attendance rate (>20%), whereas **weekends** (Saturdays and Sundays) have less than 5% attendance.
3. **Time of Day**:
   - Classes during **morning** and **evening** hours are most popular, while **midday** classes see low attendance, suggesting that midday classes can be reduced or rescheduled.
4. **Underperforming Classes**:
   - Classes like **"Zumba"**, **"Step"**, **"Pilates"**, and **"Burn It"** showed consistently low attendance, especially on weekends, and should be reconsidered for optimisation or removal.

## Recommendations
1. **Reschedule Classes to Peak Demand Hours**:
   - Increase class availability during peak demand periods (e.g., Wednesday mornings and evenings). For example, reduce **Step** from 10 to 4 sessions and increase **LBT** from 1 to 7 sessions.
2. **Remove or Replace Underperforming Classes**:
   - Consider removing low-performing classes like **"Move Your Mind Circuits"** and **"Learn to Run"**, which consistently had low attendance and high cancellation rates.
3. **Optimise Waitlist Management**:
   - Manage waitlists more effectively by reducing overbooking in popular classes to minimise cancellations and increase attendance.
4. **Focus on Weekday Engagement**:
   - Since weekends have low attendance, focus on offering more high-demand classes on weekdays (e.g., **Bodytone** on Wednesdays), while minimising additions to weekend schedules.
5. **Introduce Member Feedback**:
   - Implement a feedback mechanism within the PureGym app or website where members can provide reasons for cancellations, allowing continuous improvement of the class offerings and schedule.


