# Education

> This project addresses inequality of educational opportunity in U.S. high schools. Here we will focus on average student performance on the ACT or SAT exams that students take as part of the college application process.

---

## Project Overview

Educational inequality remains an important issue in the United States. Students from different socioeconomic backgrounds may have unequal access to educational resources and opportunities, potentially affecting their academic performance.

This project uses school-level educational and socioeconomic data to explore how factors such as household income, unemployment rates, parental education, and access to free or reduced-price lunch relate to standardized test performance.

- **Objective:** Investigate the relationship between socioeconomic conditions and average ACT/SAT scores among U.S. high schools.
- **Domain:** Education, Social Inequality 
- **Key Techniques:** Exploratory Data Analysis, Data Cleaning, Data Merging, Missing Value Imputation, Data Visualization

---

## Project Structure

```
├── data/                 # Raw and processed data
├── code/                 # Jupyter notebooks and Python scripts
├── reports/              # Generated reports and visualizations
├── requirements.txt      # Dependencies
└── README.md             # Project documentation
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

Key Variables:

School identification number

Academic year

State

ZIP code

School type

School level

Charter school status

The two datasets are merged using their common school identification number to combine socioeconomic characteristics with school information.

Data License: To be confirmed based on the original data providers.

---

## Analysis

The data preparation and exploratory analysis are performed in education_data_preparation.ipynb.

1. Data Exploration

Imported and examined both datasets using Pandas.

Checked column names, data types, missing values, and dataset sizes.

Used scatterplots and pair plots to explore relationships between socioeconomic variables and average ACT scores.

2. Data Preparation

Selected relevant variables from the school information dataset.

Renamed columns to improve readability and consistency.

Converted school identifiers to compatible data types.

Merged the datasets using a left join to retain all EdGap records.

3. Data Cleaning and Quality Control

Examined minimum and maximum values to identify invalid observations.

Replaced out-of-range ACT scores and free/reduced-price lunch percentages with missing values.

Filtered the dataset to include only high schools.

Checked for duplicate records.

Examined missing values and geographic coverage.

Removed observations without valid average ACT scores.

4. Missing Value Imputation

Applied Scikit-learn's IterativeImputer to estimate missing numerical socioeconomic values.

Checked the dataset after imputation to confirm that no missing values remained in the selected variables.

5. Data Export

The cleaned dataset is exported as:

education_clean.csv

This file can be used for further statistical analysis and modeling.

---

## Results

Include a short discussion of the findings and what they imply.

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
