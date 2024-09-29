# Pure Gym Data Analysis

## Overview
This project is part of a group assignment during the Data Analytics course at the **London School of Economics (LSE)**, with myself serving as the project leader. The analysis focuses on understanding member behaviour and class attendance at PureGym, with the aim to optimise class schedules, reduce cancellations and no-shows, and improve overall member satisfaction. The analysis covers various metrics such as class popularity, attendance patterns, waitlist management, and gym capacity utilisation. It addresses key questions around class performance, member participation trends, and resource optimisation.

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
   - Used `file_data.info()` to understand the data types and non-null counts of each column.
   - Used `file_data.describe()` to generate summary statistics for numerical columns.
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

## Key Insights and Recommendation Summary

### Patterns, Trends, and Insights
![ClassesUtilisation](underutilised.png)
- **Challenges with Top Classes**: 
  - A substantial number of the most popular classes face issues related to cancellations, no-shows, and having long waiting lists. 
  - Classes like **"Cycle"** and **"Leg Bum & Tums" (LBT)** are the most impacted.
  - A trend is observed where classes with high cancellation rates also have moderately high non-attendance rates, suggesting potential dissatisfaction among members due to missed opportunities for attendance. This creates inefficiencies as sessions are left underutilized, even with waiting members eager to join.
  ![CLassesParticipation](Classes_Participation_Status.png)
- **Day of the Week Analysis**:
  - **Wednesday** has the highest attendance rate, exceeding **20%**, whereas other days fall below this threshold. Weekend days, **Saturday and Sunday**, have significantly lower attendance rates (<5%) compared to weekdays. 
  - This suggests that additional class offerings on **Wednesday** could capitalize on higher engagement levels, whereas additional weekend classes may not be as beneficial.

- **Popular vs. Underutilized Classes**:
  - On **Wednesdays**, popular classes include **Pump, Cycle, and Bodytone**, while **Yoga, Sweat, Zumba, Step, Pilates, and Burn It** have lower attendance.
  - On **weekends**, popular classes like **Bodytone** are unavailable, while **Zumba** is missing on Saturdays and **Pilates** on Sundays. Classes like **Yoga, Zumba, Dance, and Pilates** show persistently low attendance rates.

## Recommendations for Class Scheduling Optimization

1. **Adjust Wednesday Class Schedule**:
   - Increase availability for **LBT at 12 PM** by reducing the number of **Step sessions** from 10 to 4 and reallocating the remaining 6 sessions to LBT, increasing it to 7 sessions in total. This aims to better align class availability with demand.

2. **Discontinue Low-Performance Classes**:
   - Consider removing classes with low attendance and engagement, such as:
     - **'Move Your Mind Circuits Class'** (18.59% filled, 37 participants).
     - **'Learn To Run'** (25% filled, 2 participants).
   - Focus on reallocating these slots to higher-demand activities or introducing new classes that might attract more members.

3. **Enhance Engagement on Weekends**:
   - Since attendance is lower on weekends, focus on optimizing current offerings rather than adding more sessions. Consider:
     - Introducing **popular classes like Bodytone** to the weekend schedule.
     - Replacing underperforming sessions like **Yoga or Dance** with trial classes that can gauge member interest.

4. **Long-Term Optimization and Feedback Collection**:
   - Track the impact of implemented schedule changes on member satisfaction, retention, and overall gym performance.
   - Collect feedback by introducing a feature in the **PureGym application** for members to provide reasons for class cancellations, allowing for better insights into member preferences.
   - Continuously monitor the data to identify new opportunities for optimization and ensure long-term success.


