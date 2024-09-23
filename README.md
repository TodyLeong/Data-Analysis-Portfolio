# Pure Gym Data Analysis

## Overview

This project focuses on analyzing member behavior and class attendance at PureGym to optimize class schedules, reduce cancellations and no-shows, and improve overall member satisfaction. The analysis covers various metrics such as class popularity, attendance patterns, waitlist management, and gym capacity utilization. It addresses key questions around class performance, member participation trends, and resource optimization.

## Business Problem

PureGym, a leading UK gym chain, has raised concerns about underperforming classes, cancellation rates, and no-shows affecting member satisfaction and overall gym performance. The main goals of this analysis are to:

- Identify which classes are most/least popular by gender, age, and time of day.
- Understand attendance trends across different days of the week.
- Determine which classes should be reduced, rescheduled, or removed.
- Examine how time of day impacts class capacity utilization.
- Suggest ways to optimize member engagement by minimizing cancellations and no-shows.

## Key Business Questions Addressed

1. Which classes had the highest and lowest participation according to gender, age, and time of day?
2. Which days experience the most and least attendance? How do weekdays compare to weekends?
3. Which classes are underperforming and need to be reduced or replaced?
4. How does the time of day impact class capacity utilization?
5. Are there opportunities for improving the least utilized classes based on percentage filled and total attendance?

---

## Data Cleaning and Preparation

### Steps Taken:

1. **Missing Values**: 
   - Imputed missing values in attendance and waitlist columns using the mean to maintain the dataset’s integrity without introducing bias.

2. **Outliers**: 
   - Removed outliers using Z-scores and the Interquartile Range (IQR) method to prevent skewing the results.

3. **Normalization**: 
   - Normalized data across variables such as class sizes and waitlists to ensure comparability.

4. **Categorization**: 
   - Grouped classes based on popularity, cancellation rates, and no-show frequencies to facilitate targeted analysis.

---

## Data Analysis Approach

### Tools and Libraries

- **Python**: Used for data analysis and visualizations.
- **Pandas**: For data manipulation (grouping, aggregating, merging).
- **Matplotlib**: For data visualization (bar charts, histograms).
- **NumPy**: For numerical operations and normalizations.
- **Scikit-learn**: For regression analysis to predict the impact of scheduling changes on attendance.

### Techniques Used

1. **Descriptive Statistics**: 
   - Summarized key metrics such as total attendance, cancellations, no-shows, and waitlists.

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
   - Classes like **"Zumba"**, **"Step"**, **"Pilates"**, and **"Burn It"** showed consistently low attendance, especially on weekends, and should be reconsidered for optimization or removal.

---

## Recommendations

1. **Reschedule Classes to Peak Demand Hours**:
   - Increase class availability during peak demand periods (e.g., Wednesday mornings and evenings). For example, reduce **Step** from 10 to 4 sessions and increase **LBT** from 1 to 7 sessions.

2. **Remove or Replace Underperforming Classes**:
   - Consider removing low-performing classes like **"Move Your Mind Circuits"** and **"Learn to Run"**, which consistently had low attendance and high cancellation rates.

3. **Optimize Waitlist Management**:
   - Manage waitlists more effectively by reducing overbooking in popular classes to minimize cancellations and increase attendance.

4. **Focus on Weekday Engagement**:
   - Since weekends have low attendance, focus on offering more high-demand classes on weekdays (e.g., **Bodytone** on Wednesdays), while minimizing additions to weekend schedules.

5. **Introduce Member Feedback**:
   - Implement a feedback mechanism within the PureGym app or website where members can provide reasons for cancellations, allowing continuous improvement of the class offerings and schedule.

---

## Visualizations

1. **Stacked Bar Chart**: Visualizes class capacity utilization on Saturdays, showing the average attendance and remaining capacity.
2. **Histogram**: Displays check-in times on Wednesdays, highlighting peak hours.
3. **Dual-Axis Plot**: Shows the percentage of class capacity filled and the total number of participants in each class, comparing high attendance to low utilization.
4. **Participation Status Bar Chart**: Shows the proportions of no-shows, cancellations, and waitlist occurrences for the top classes.

---

## Project Implementation

### Data Manipulation with Pandas

- Grouping and aggregating data to compute statistics like total attendance, cancellations, and no-shows.
- Merging datasets (e.g., class schedules, attendance records) to correlate attendance patterns with specific class attributes.

### Advanced Analytical Techniques

- Calculating the proportion of participation statuses (e.g., no-shows, cancellations).
- Analyzing class capacity utilization to gain insights into gym resource allocation and optimization opportunities.

### Visualization Techniques with Matplotlib

- Stacked bar charts for class capacity utilization.
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

# Normalize data for comparability
attendance_data['normalized_attendance'] = (attendance_data['attendance'] - attendance_data['attendance'].mean()) / attendance_data['attendance'].std()
