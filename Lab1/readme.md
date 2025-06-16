# Lab Work: Personality Trait Analysis

## Purpose of the Lab Work

The primary purpose of this lab was to perform an exploratory data analysis (EDA) on a dataset containing information about individuals' social behaviors and personality traits. The objectives included:

* **Data Cleaning**: Identifying and handling missing values within the dataset.
* **Data Exploration**: Understanding the basic characteristics of the data using descriptive statistics.
* **Visualization**: Creating visual representations (scatter and line plots) to uncover patterns, trends, and relationships between different variables.
* **Statistical Analysis**: Calculating measures of central tendency, dispersion, and correlation to quantify observations.
* **Insight Generation**: Drawing key insights about how various social behaviors (like time spent alone, social event attendance, frequency of going out, and online post frequency) relate to personality types (Introvert vs. Extrovert) and to each other.

## Key Insights

### 1. Missing Data Handling
Several columns in the dataset initially contained missing values:
* `Time_spent_Alone`: 63 missing
* `Stage_fear`: 73 missing
* `Social_event_attendance`: 62 missing
* `Going_outside`: 66 missing
* `Drained_after_socializing`: 52 missing
* `Friends_circle_size`: 77 missing
* `Post_frequency`: 65 missing

These missing values were handled by filling numerical NAs with `0` and object/categorical NAs with `'Unknown'`. While this ensures a complete dataset for analysis, it's a point to consider for the interpretation of results, as `0` or `'Unknown'` might not always be the most representative imputation.

### 2. Visualizations

**a. Time Spent Alone vs. Friends Circle Size by Personality**
* **Insight**: The scatter plot distinctly shows two clusters corresponding to 'Introvert' and 'Extrovert' personalities.
    * **Introverts** generally tend to spend more time alone (higher values on the x-axis) and have a smaller friends circle size (lower values on the y-axis).
    * **Extroverts** typically spend less time alone and tend to have a larger friends circle size.
    * This suggests a negative correlation between the time spent alone and the size of an individual's friend circle, with clear differentiation based on personality type.

**b. Trend of Mean Social Event Attendance vs. Going Outside by Personality**
* **Insight**: The line plot illustrates the relationship between the frequency of going out (days/week) and the average number of social events attended (events/month).
    * For **both Introverts and Extroverts**, there's a positive trend: as the frequency of going outside increases, the average social event attendance also tends to increase.
    * **Extroverts** consistently show a higher average social event attendance compared to Introverts across all levels of "Going Outside" frequency.

### 3. Statistical Measures

**a. Descriptive Statistics (`df.describe(include='all')`)**
* The dataset contains 2900 entries.
* `Time_spent_Alone`: Mean of approx. 4.5 hours/day, with a range from 0 to 11 hours.
* `Social_event_attendance`: Mean of approx. 4 events/month, ranging from 0 to 10.
* `Going_outside`: Mean of 3 days/week, ranging from 0 to 7.
* `Friends_circle_size`: Mean of approx. 6.3 friends, ranging from 0 to 15.
* `Post_frequency`: Mean of approx. 3.6 posts (presumably per week/month), ranging from 0 to 10.
* `Personality`: The dataset has slightly more 'Extrovert' (1491) entries than 'Introvert' (1409).
* `Stage_fear`: More individuals reported 'No' (1417) stage fear than 'Yes'.
* `Drained_after_socializing`: More individuals reported 'No' (1441) to being drained after socializing than 'Yes'. (This might be counter-intuitive for typical introversion definitions, highlighting the specific nature of this dataset or the impact of NA filling).

**b. Central Tendency (Mean, Median, Mode)**
* **Numerical Columns**:
    * `Time_spent_Alone`: Mean (4.51), Median (4.0), Mode ([0.0]) - The mode being 0 suggests a significant group spends very little time alone, or this is an artifact of filling NaNs with 0.
    * `Social_event_attendance`: Mean (3.96), Median (3.0), Mode ([2.0])
    * `Going_outside`: Mean (3.00), Median (3.0), Mode ([0.0]) - Similar to `Time_spent_Alone`, a mode of 0 for going out could be influenced by NaN filling.
    * `Friends_circle_size`: Mean (6.27), Median (5.0), Mode ([5.0])
    * `Post_frequency`: Mean (3.56), Median (3.0), Mode ([2.0])
* **Categorical Columns**:
    * `Stage_fear`: Mode (['No'])
    * `Drained_after_socializing`: Mode (['No'])
    * `Personality`: Mode (['Extrovert'])

**c. Dispersion (Range, IQR, Variance, Standard Deviation)**
* `Time_spent_Alone`: Std Dev (3.48), Range (11.0), IQR (6.0). This indicates a considerable spread in the amount of time individuals spend alone.
* `Friends_circle_size`: Std Dev (4.29), Range (15.0), IQR (7.0). Also shows a wide variation in the number of friends.
* Other numerical variables (`Social_event_attendance`, `Going_outside`, `Post_frequency`) also show moderate dispersion.

**d. Correlation Matrix (Numerical Columns)**
* **Strong Negative Correlations with `Time_spent_Alone`**:
    * `Social_event_attendance`: -0.733
    * `Going_outside`: -0.751
    * `Friends_circle_size`: -0.717
    * `Post_frequency`: -0.733
    * **Insight**: Individuals who spend more time alone tend to attend fewer social events, go out less often, have smaller friend circles, and post less frequently online. This aligns with typical characteristics associated with introversion.
* **Strong Positive Correlations among social activity indicators**:
    * `Social_event_attendance` is positively correlated with `Going_outside` (0.748), `Friends_circle_size` (0.735), and `Post_frequency` (0.745).
    * `Going_outside` is positively correlated with `Friends_circle_size` (0.736) and `Post_frequency` (0.771).
    * `Friends_circle_size` is positively correlated with `Post_frequency` (0.708).
    * **Insight**: These suggest that various forms of social engagement are interrelated. For example, those who go out more often also tend to attend more social events and have more friends.

## Challenges Faced or Decisions Made

* **Missing Data Handling**:
    * **Challenge**: A significant number of missing values were present across multiple key columns.
    * **Decision**: For this lab, missing numerical values were imputed with `0`, and categorical/object type missing values were imputed with `'Unknown'`.
    * **Rationale/Consideration**: This was a straightforward approach for ensuring a complete dataset for subsequent calculations and visualizations. However, it's important to acknowledge that filling with `0` (especially for features like `Time_spent_Alone` or `Going_outside` where 0 can be a valid reported value) or `'Unknown'` might introduce bias or affect the accuracy of statistical measures like the mean or mode. Alternative strategies like mean/median/mode imputation, or more advanced techniques, could be considered for a more robust analysis. The impact of this decision is visible in some modes (e.g., mode of 0 for `Time_spent_Alone`).
* **Visualization Interpretation**:
    * **Decision**: The colormaps ('viridis' for scatter, 'plasma' for line) and plot styles ('seaborn-v0_8-whitegrid') were chosen for clarity. Plot labels and titles were made descriptive.
    * **Challenge**: Ensuring that the visualizations clearly conveyed the intended insights, especially when dealing with overlapping data points or multiple categories. The use of `alpha` in the scatter plot helped with point density visualization. For the line plot, grouping by `Personality` and then by `Going_outside` to calculate mean attendance was a key step to reveal trends.
* **Statistical Measure Selection**:
    * **Decision**: A comprehensive set of descriptive statistics, central tendency measures, and dispersion measures were calculated to provide a thorough overview of the data. The correlation matrix was specifically used for numerical features to quantify linear relationships.
    * **Consideration**: For categorical variables, 'mode' was the primary central tendency measure. Further analysis for categorical data could involve frequency tables or chi-squared tests if specific hypotheses were being tested.
