# Predicting ACT Scores based on Socio-Economic Factors
DATA 5100 Assignment 2

This project will explore the relationship between student outcomes and various socioeconomic variables

---

## Project Overview

- **Objective:** The goal of this project is to identify the relationship between the average ACT scores (or SAT equivalent) at a school-level with various socio-economic, regional, and school-specific characteristics.
- **Domain:** Education
- **Key Techniques:** Regression Analysis
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
**Source:**  
- **[EdGap Dataset](https://raw.githubusercontent.com/brian-fischer/DATA-5100/main/EdGap_data.xlsx):** Provides average ACT scores and socioeconomic factors at the census tract level.  
- **[National Center for Education Statistics (NCES) – School Info Dataset]:** Includes over 100k school records with key school identifiers and attributes such as Charter status.   

**Additional Data:**  
- **[Civil Rights Data Collection (CRDC)](https://raw.githubusercontent.com/brisamh/education/refs/heads/main/data/Referrals%20and%20Arrests.csv):** Provides the number of student referrals and arrests at the school level.
- **[National Center for Education Statistics](https://raw.githubusercontent.com/brisamh/education/main/data/CCD_elsi_table_generator_data.xlsx):** Used to generate a table of data at the public school level for various characteristics about each school, such as Student:Teacher ratio, the locale of the school (city/rural etc), and many other data points
- **[Higher Education Institutions by ZIP code](https://github.com/brisamh/education/raw/refs/heads/main/data/hd2017.csv):** Used to estimate the influence of nearby colleges and universities.  
- **[State-level ACT/SAT Testing Policy Data](https://www.piqosity.com/act-sat-graduation-requirements-by-state/):** Indicates whether testing is mandatory, optional, or not provided.

**Final Data:**   
After extensive pre-processing and transformation, the Regression Analysis uses the final dataset provided [here](https://raw.githubusercontent.com/brisamh/education/refs/heads/main/data/clean_education_project_data.csv)

**Description:**  
The final cleaned dataset combines these sources to form a robust foundation for analyzing school-level ACT outcomes.

**License:** All datasets were used for educational purposes under fair use for academic analysis.  

---

## Data Analysis  

The most challenging part of this analysis was the data preperation of the additional datasets. Extensive cleaning was needed on values, columns, keys, and careful validation of the joins. Once the final DataFrame was merged, it was exported for analysis using OLS (Ordinary Least Squares) linear regression modeling.

Despite my hypotheses on how the various additional data would improve the model, the best model was highly reduced: the most indicative predictor of ACT Scores was the % of students at the school receiving free or reduced lunch. My large multivariate model that included predictors such as student teacher ratio, law enforcement referrals or arrests, nearby higher education institutions, whether the ACT/SAT was mandated by the state, and numerous other factors ultimately failed to provide more than a marginal improvement in explanatory power when compared to a reduced model of three predictors. This model achieved an **R² of 0.655** while the reduced model using only three predictors (`rate_unemployment + percent_college + percent_lunch`) achieved an **R² of 0.624**.

---

## Results

- Reduced model showed strong correlation identified between ACT scores and three main factors: **unemployment rate**, **college education rate**, and **free/reduced lunch rate**
- Expanded models with school-type and testing-policy data improved explanatory power marginally (**R² = 0.655 vs 0.624**)
- All p-values of my expanded model were highly statistically significant, but the coefficients were very small and did not result in much change in ACT Scores
- Ultimately, the reduced model is preferred for interpretability and practical application.
- One way I could continue to investigate the correlations with my additional data to ACT Scores would be to count at the School District level: Higher Education Institutions by School District, rather than limiting it to just the same Zip Code. Include Referrals and Arrests at all schools in the school district rather than that specific High School in that specific year.


---

## Authors

- Authored by - [@brisamh](https://github.com/brisamh/brisamh/)

---

## License

This project is licensed under the [MIT License](./LICENSE).

---

## Acknowledgements

This project used Jupyter Notebooks, NumPy, Pandas, Seaborn, Matplotlib, and SciPy.  
Tutorials and guidance were provided by **Dr. Fischer of Seattle University**.
