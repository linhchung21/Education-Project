# Education

> This project addresses inequality of educational opportunity in U.S. high schools. Here we will focus on average student performance on the ACT or SAT exams that students take as part of the college application process.

---

## Project Overview

Educational inequality remains an important issue in the United States. Students from different socioeconomic backgrounds may have unequal access to educational resources and opportunities, potentially affecting their academic performance.

This project uses school-level educational and socioeconomic data to explore how factors such as household income, unemployment rates, parental education, and access to free or reduced-price lunch relate to standardized test performance.

- **Objective:** Investigate the relationship between socioeconomic conditions and average ACT/SAT scores among U.S. high schools.
- **Domain:** Education, Social Inequality 
- **Key Techniques:** Data Cleaning, Data Merging, Missing Value Imputation, Exploratory Data Analysis, Data Visualization, Linear Regressio

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
3. Data Cleaning and Missing Values
Data cleaning included identifying invalid ACT scores and lunch participation percentages, examining missing values, and removing observations without valid average ACT scores.

Missing numerical socioeconomic values were estimated using Scikit-learn's IterativeImputer.

The cleaned dataset was exported as:

data/education_clean.csv

This file is used for exploratory analysis and predictive modeling.
4. Exploratory Data Analysis (EDA)
The EDA notebook examines relationships between socioeconomic factors and average ACT scores.

The analysis includes:
- Correlation matrices to identify relationships between numerical variables.
- Pair plots and scatterplots to visualize relationships with ACT scores.
- Boxplots to examine the distribution of variables and identify potential outliers.
- Comparisons between charter and non-charter schools.
The analysis also includes derived variables to make selected predictors easier to interpret.
5. Predictive Modeling
Two linear regression models were developed to investigate whether socioeconomic factors can predict average ACT scores.

Model 1: Socioeconomic Factors

This model uses the following predictors:
- Unemployment rate
- Percentage of adults with a college degree
- Percentage of children living in married-couple families
- Median household income
- Percentage of students receiving free or reduced-price lunch
Model 2: Socioeconomic Factors + Charter Status

The second model includes the same socioeconomic predictors, with charter school status added as an additional variable.

The purpose is to determine whether including school type improves prediction accuracy.

The models were evaluated using a training and testing split, with three performance metrics:
- Mean Absolute Error (MAE): Measures the average difference between predicted and actual ACT scores.
- Root Mean Squared Error (RMSE): Measures prediction error while giving more weight to larger errors.
- R-squared (R²): Measures how much variation in ACT scores the model explains.
- Both models achieved an R-squared value of approximately 0.615, indicating that they explain about 61.5% of the variation in ACT scores in the test data, relative to the test-set mean.

The MAE of 1.161 indicates that predicted ACT scores differ from actual scores by approximately 1.16 points on average.

Adding charter school status did not noticeably improve the model's performance, as both models produced the same evaluation results when rounded to three decimal places.

---

## Results

The exploratory analysis suggests that socioeconomic conditions are associated with average ACT performance.

School lunch participation showed a strong negative correlation with average ACT scores (approximately r = -0.785). This suggests that schools with higher percentages of students receiving lunch assistance tend to have lower average ACT scores.

The regression results also indicate that socioeconomic factors have meaningful predictive value. However, adding charter school status did not substantially improve prediction accuracy in this analysis.

The dataset contains considerably fewer charter schools than non-charter schools, which may limit the information available for evaluating differences between these groups.

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
