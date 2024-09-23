# Pure Gym Data Analysis

## Overview

This project focuses on analysing member behavior and class attendance at PureGym to optimise class schedules, reduce cancellations and no-shows, and improve overall member satisfaction. The analysis covers various metrics such as class popularity, attendance patterns, waitlist management, and gym capacity utilisation. It addresses key questions around class performance, member participation trends, and resource optimisation.

## Business Background and Key Questions

PureGym, a leading UK gym chain, is facing challenges with underperforming classes, high cancellation rates, and no-shows, which negatively impact member satisfaction and overall gym performance. To address these concerns, this analysis aims to:

- Identify Class Popularity: Determine which classes are most and least popular across different demographics (gender, age) and times of the day.
- Attendance Trends: Analyze attendance patterns across the week, comparing weekdays to weekends, and identifying days with significant or low attendance.
- Class Optimization: Assess underperforming classes to determine whether they should be rescheduled, reduced, or replaced to better align with member preferences.
- Capacity Utilization: Explore how time of day impacts class capacity utilization and find ways to maximize resource use.
- Member Engagement: Suggest ways to optimize engagement by reducing cancellations, no-shows, and improving attendance for least utilized classes.

---

## Data Cleaning and Preparation

### Steps Taken:

1. **Missing Values**: 
   - Imputed missing values in attendance and waitlist columns using the mean to maintain the dataset’s integrity without introducing bias.

2. **Outliers**: 
   - Removed outliers using Z-scores and the Interquartile Range (IQR) method to prevent skewing the results.

3. **Normalisation**: 
   - Normalised data across variables such as class sises and waitlists to ensure comparability.

4. **Categorisation**: 
   - Grouped classes based on popularity, cancellation rates, and no-show frequencies to facilitate targeted analysis.

---

## Data Analysis Approach

### Tools and Libraries

- **Python**: Used for data analysis and visualisations.
- **Pandas**: For data manipulation (grouping, aggregating, merging).
- **Matplotlib**: For data visualisation (bar charts, histograms).
- **NumPy**: For numerical operations and normalisations.
- **Scikit-learn**: For regression analysis to predict the impact of scheduling changes on attendance.

### Techniques Used

1. **Descriptive Statistics**: 
   - Summarised key metrics such as total attendance, cancellations, no-shows, and waitlists.

2. **Comparative Analysis**: 
   - Compared attendance trends by demographics (age, gender) and across time periods (days of the week, time of day).

3. **Correlation Analysis**: 
   - Explored relationships between high waitlists, cancellations, and no-show rates. A significant finding was that overbooking led to higher no-show rates.

4. **Predictive Models**: 
   - Applied linear regression models to predict how schedule changes might impact class attendance, enabling data-driven decision-making.

---

## Key Insights and Findings

1. **Class Performance**:
   - Popular classes like "Cycle" and "Legs, Bums, & Tums" (LBT) had the highest cancellation and non-attendance rates, indicating potential dissatisfaction due to overbooking.
   - Certain classes like "Move Your Mind Circuits" and "Learn to Run" had very low participation and are candidates for removal or rescheduling.

2. **Day of the Week Trends**:
   - **Wednesdays** have the highest attendance rate (>20%), whereas **weekends** (Saturdays and Sundays) have less than 5% attendance.

3. **Time of Day**:
   - Classes during **morning** and **evening** hours are most popular, while **midday** classes see low attendance, suggesting that midday classes can be reduced or rescheduled.

4. **Underperforming Classes**:
   - Classes like **"Zumba"**, **"Step"**, **"Pilates"**, and **"Burn It"** showed consistently low attendance, especially on weekends, and should be reconsidered for optimisation or removal.

---

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

---

## Visualisations

1. **Stacked Bar Chart**: Visualises class capacity utilisation on Saturdays, showing the average attendance and remaining capacity.
2. **Histogram**: Displays check-in times on Wednesdays, highlighting peak hours.
3. **Dual-Axis Plot**: Shows the percentage of class capacity filled and the total number of participants in each class, comparing high attendance to low utilisation.
4. **Participation Status Bar Chart**: Shows the proportions of no-shows, cancellations, and waitlist occurrences for the top classes.

---

## Project Implementation

### Data Manipulation with Pandas

- Grouping and aggregating data to compute statistics like total attendance, cancellations, and no-shows.
- Merging datasets (e.g., class schedules, attendance records) to correlate attendance patterns with specific class attributes.

### Advanced Analytical Techniques

- Calculating the proportion of participation statuses (e.g., no-shows, cancellations).
- Analysing class capacity utilisation to gain insights into gym resource allocation and optimisation opportunities.

### Visualisation Techniques with Matplotlib

- Stacked bar charts for class capacity utilisation.
- Histograms for check-in time distributions.
- Simple bar charts for participation status proportions (cancellations, no-shows, waitlists).
  
### Example Code: Data Cleaning

```python
import pandas as pd

# Load datasets
attendance_data = pd.read_csv('gym_attendance_data.csv')
class_data = pd.read_csv('gym_class_schedules.csv')

# Convert date columns to datetime
attendance_data['date'] = pd.to_datetime(attendance_data['date'])

# Handle missing values by imputing the mean
attendance_data.fillna(attendance_data.mean(), inplace=True)

# Remove outliers using Z-score
from scipy.stats import zscore
attendance_data = attendance_data[(zscore(attendance_data['attendance']) < 3)]

# Normalise data for comparability
attendance_data['normalised_attendance'] = (attendance_data['attendance'] - attendance_data['attendance'].mean()) / attendance_data['attendance'].std()
