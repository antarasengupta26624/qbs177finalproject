<style>
  body {
    font-family: 'Times New Roman', Times, serif;
  }
	 h1 {
    text-align: center;
  }
</style>


# Socioeconomic Disparities in Mental Health

<iframe src="gender_phq9_box_plot.html" width=800 height=600 frameBorder=0></iframe>



## Contents 
I. Introduction \
II. Objectives \
III. Methods* \
IV. Conclusions \
V. References \
*All code can be found in Methods_final.pdf

## I. Introduction


### A. Background
Socioeconomic disparities have played as significant factors in individuals and communities’ wellness.  Factors such as race, gender, age, levels of education , marriage status, income, geographic location, and income could all be parts of very critical to one’s mental health. However, the resources are not equally distributed among everyone, individual’s can face barriers and limit access to helpful resources due to socioeconomic disparities.\
Although that mental health disorder can happen to anyone regardless of their socioeconomic background, those who have lower socioeconomic background may have a higher chance of mental illness. In addition, socioeconomic disparities and systemic inequalities may cause limited resources for mental health care, social support, and the proper help one might need.\

### B. Dataset
For our project, we help to explore the relationship between various socioeconomic factors and mental health illness, and we hope to reduce socioeconomic disparities and improve overall-health being. \
We are using data from the National Health and Nutrition Examination Survey (NHANES) for the years 2021-2023. This dataset provides us an overview of different demographic factors such as income, education, and household sizes and the PAtient Health Questionnaire responses(PHQ-9)\

## II. Objectives


## III. Methods

### A. Data Wrangling

### B. Data Visualizations

### C. Modeling

#### 1. {regression model}

##### Summary of Methodology
To analyze the relationship between depression scores and various demographic and socioeconomic factors, we first prepared the dataset by renaming and formatting variables for clarity. Categorical variables such as race, marital status, and gender were converted into factor variables. We then applied a series of simple linear regression models, each evaluating a single predictor's impact on depression scores. The regression outputs provided coefficient estimates, standard errors, t-values, and p-values to assess statistical significance. Key model fit metrics, including the residual standard error, multiple $R^2$, and F-statistics, were used to determine the explanatory power of each variable. This approach allowed us to identify significant predictors, such as gender, age, income-to-poverty ratio, and marital status, while also highlighting non-significant factors.

##### Results

###### Race
- Non-Hispanic Asians tend to have a significantly lower depression score compared to the baseline (Mexican American).  

###### Month of Survey
- No significant effect on depression scores.  

###### Gender
- Females have a significantly higher depression score compared to males.  

###### Age
- Age has a negative correlation with depression score. For each additional year of age, the depression score decreases by **-0.0456**.  

###### Military Status
- No statistically significant correlation with depression (**p = 0.0913**), but those who responded "No" to military service tend to have slightly lower depression scores.  

###### Country of Birth
- Individuals born outside the U.S. tend to have lower depression scores.  

###### Education Level
- Individuals with higher education (college graduate or above) have significantly lower depression scores compared to those with lower education levels.  

###### Marital Status
- Those who are widowed/divorced/separated tend to have higher depression scores compared to the baseline (married/live with partner). 
- Never-married individuals have the highest increase in depression scores among all marital groups.  

###### Household Size
- No significant effect on depression scores.  

###### Income-to-Poverty Ratio
- A higher income-to-poverty ratio is statistically associated with **lower depression scores**. As income-to-poverty ratio increases, depression scores decrease.  

##### Conclusion
Based on our linear model results, we conclude that the factors with the **strongest influence** on depression scores are:
- **Gender** (higher depression in females)
- **Age** (negative effect)
- **Marital status** (widowed/divorced/separated & never married increase depression scores)
- **Education level** (higher education lowers depression scores)
- **Income-to-poverty ratio** (higher income lowers depression scores)

However, **race, month of survey, military status, and household size** have **little or no effect** on depression scores.



#### 2. {lasso/decision tree}

#### 3. {cluster}

#### 4. **eXtreme Gradient Boosting (XGBoost)**

**What is XGBoost?**

1. Machine learning algorithm designed for structured data.  
2. It improves prediction accuracy by sequentially boosting weak models while reducing errors.

**How It Works:**

1. Builds decision trees sequentially
2. Each tree corrects errors from the previous one
3. Uses gradient boosting to optimize predictions


**Why XGBoost?**
1. Handles Complex Interactions Between SES Factors
- Mental health is influenced by multiple SES factors (e.g., income, education, household size).
- XGBoost captures nonlinear relationships & interactions better than traditional regression models.
  	- The impact of education on depression might depend on income level, and XGBoost can learn these dependencies on its own.

2. Feature Importance and Interpretability
- Ranks features by importance, showing which SES factors are most predictive of depression (PHQ-9 scores).
- Helps identify key factors driving mental health disparities.

3. Good at Handling Large, Imbalanced Datasets
- NHANES has imbalanced data (e.g., more people with low PHQ-9 scores than high).
- XGBoost has built-in handling for class imbalance, improving predictions across different groups.
- Confirms accurate predictions across different SES groups, even if some are underrepresented.
  

**Code Breakdown**
1. Defining Predictors
- Selected 10 SES features for predicting PHQ-9 scores.

2. Split Data Into Training & Testing Sets
- 80% training, 20% testing for model evaluation.

3. Convert Data for XGBoost
- XGBoost requires numeric matrix format.
- Target variable: PHQ-9 score (Depression severity).

4. Train XGBoost Model
- 100 boosting rounds, learning rate = 0.1, max tree depth = 6 levels.

5. Evaluate Model Performance
- RMSE (Root Mean Squared Error): Measures prediction accuracy.
- R-squared: Shows how well SES factors explain depression variability.

6. Feature Importance Analysis
- Identifies key predictors affecting PHQ-9 scores.


<iframe src="xgboost.html" width=800 height=600 frameBorder=0></iframe>

## IV. Conclusion


## V. References

