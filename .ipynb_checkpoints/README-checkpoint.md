# Education

> This project investigates educational inequality in U.S. high schools by examining whether socioeconomic factors can predict average ACT scores.
---

## Project Overview

Educational inequality remains an important issue in the United States. Students from different socioeconomic backgrounds may have unequal access to educational resources and opportunities, potentially affecting their academic performance.

This project uses school-level educational and socioeconomic data to explore how factors such as household income, unemployment rates, parental education, and access to free or reduced-price lunch relate to standardized test performance.

In addition, charter school status is included as an additional predictor to examine whether school type improves predictions of average ACT scores.

## Research Questions:

Can socioeconomic factors predict average ACT scores among U.S. high schools?

Which socioeconomic factor has the strongest relationship with average ACT scores?

Does adding charter school status improve prediction accuracy?


- **Objective:** Investigate the relationship between socioeconomic conditions and average ACT/SAT scores among U.S. high schools.
- **Domain:** Education, Social Inequality 
- **Key Techniques:** Data Cleaning, Data Merging, Missing Value Imputation, Exploratory Data Analysis (EDA), Data Visualization, Correlation Analysis, and Linear Regression.

---

## Project Structure

```
Education-Project/
├── data/
│   ├── EdGap_data.xlsx
│   ├── ccd_sch_029_1617_w_la_11212017.csv
│   └── education_clean.csv
├── code/
│   ├── education_data_preparation.ipynb
│   └── education_eda.ipynb
├── reports/
├── requirements.txt
└── README.md
```

---

## Data

The project uses two datasets containing information about U.S. schools and their socioeconomic characteristics.

1. EdGap Dataset

The EdGap dataset contains information about standardized test performance and socioeconomic conditions associated with U.S. schools.

Format: Excel (.xlsx)

Size: 7,986 observations and 7 variables

Key Variables:

School identification number

Census tract unemployment rate

Percentage of adults with a college degree

Percentage of children living in married-couple families

Census tract median household income

Average school ACT score (or SAT equivalent)

Percentage of students receiving free or reduced-price lunch

2. School Information Dataset

This dataset contains school-level information for the 2016–2017 academic year.

Source: School Information CSV

Format: CSV

Size: 102,183 observations and 65 variables

Key variables include:
- School identification number
- Academic year
- State and ZIP code
- School type and level
- Charter school status
The two datasets are merged using their common school identification number to combine socioeconomic characteristics with school-level information.

---

## Analysis

The project uses two Jupyter notebooks:

education_data_preparation.ipynb — Loads, cleans, merges, and prepares the datasets.

education_eda.ipynb — Explores relationships between socioeconomic variables and average ACT scores and evaluates a regression model.

1. Data Exploration
Both datasets were imported and examined using pandas. The initial exploration included checking dataset sizes, column names, data types, missing values, and summary statistics.

2. Data Preparation
The following steps were performed:
- Selected relevant variables from both datasets.
- Renamed columns using lowercase and snake_case formatting.
- Converted school identifiers into compatible data types.
- Merged the datasets using a left join.
- Filtered the dataset to include high schools.
- Checked for duplicate records and invalid observations.
- Removing observations without valid average ACT scores.
  
3. Data Cleaning and Missing Values
Data cleaning included identifying invalid ACT scores and lunch participation percentages, examining missing values, and removing observations without valid average ACT scores.

Missing numerical socioeconomic values were estimated using Scikit-learn's IterativeImputer.

The cleaned dataset was exported as:

data/education_clean.csv

This file is used for exploratory analysis and predictive modeling.

4. Exploratory Data Analysis (EDA)
Exploratory data analysis was performed using pandas, Matplotlib, and Seaborn.

The analysis included correlation matrices, pair plots, scatterplots, boxplots, and summary statistics to examine relationships between socioeconomic factors and average ACT scores.

The correlation analysis showed that school lunch participation had the strongest individual linear relationship with average ACT scores.

These results suggest that schools with higher lunch participation tend to have lower average ACT scores. Median household income, college education, and married-couple family percentages show positive relationships with ACT scores.

However, correlation does not establish causation.

5. Median Household Income Analysis

To explore the relationship between median household income and average ACT scores, two regression models were examined.

The first model used a simple linear relationship between median income and ACT scores.

The second model included a squared income term to investigate whether the relationship was nonlinear.

The quadratic model showed a small improvement in fit, increasing R² from 0.211 to 0.219.

These results suggest that median household income is related to average ACT scores, but income alone explains only a limited portion of the variation.

These results were calculated on the data used to fit the income models and should not be directly compared with test-set results from the multiple regression models.

6. Multiple Linear Regression
Two linear regression models were developed to investigate whether socioeconomic factors can predict average ACT scores.

Model 1: Socioeconomic Factors
A multiple linear regression model was also developed to investigate whether several socioeconomic factors together could predict average ACT scores.

The five predictors were:

rate_unemployment

percent_college

percent_married

income_10k

lunch_pct_points

The income and lunch variables were transformed into more interpretable units.

The data was divided into training and testing sets using an 80/20 split with random_state=42.

The model was evaluated using Mean Absolute Error (MAE), Root Mean Squared Error (RMSE), and R-squared (R²).

7. Additional Predictor: Charter School Status

Charter school status from the NCES dataset was included as an additional predictor to investigate whether school type improves predictions after accounting for socioeconomic conditions.

A second multiple regression model was developed using the same five socioeconomic predictors with charter school status added.

The two models were compared using the same evaluation metrics.

---

## Results

The exploratory analysis suggests that socioeconomic conditions are associated with average ACT performance.

School lunch participation showed a strong negative correlation with average ACT scores (approximately r = -0.785). This suggests that schools with higher percentages of students receiving lunch assistance tend to have lower average ACT scores.

The regression results also indicate that socioeconomic factors have meaningful predictive value. However, adding charter school status did not substantially improve prediction accuracy in this analysis.

The dataset contains considerably fewer charter schools than non-charter schools, which may limit the information available for evaluating differences between these groups.

## Multiple Regression Model Performance

Both models achieved an R-squared value of approximately 0.615, indicating that they explained approximately 61.5% of the variation in average ACT scores in the test dataset, relative to the test-set mean.

The MAE of 1.161 indicates that predicted ACT scores differed from actual scores by approximately 1.16 points on average.

Adding charter school status did not noticeably improve prediction accuracy, as both models produced the same results when rounded to three decimal places.

These results suggest that socioeconomic factors provide useful information for predicting average ACT scores, while charter school status contributed little additional predictive value in this evaluation.



---

## Authors

- Linh Chung - [@linhchung21](https://github.com/linhchung21)

---

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## Acknowledgements

- Jupiter Notebook
- Seattle University
- Inspiration or collaborators
