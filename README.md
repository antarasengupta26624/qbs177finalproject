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

### B. Dataset

## II. Objectives


## III. Methods

### A. Data Wrangling

### B. Data Visualizations

### C. Modeling

#### 1. {regression model}

#### 2. {lasso/decision tree}

#### 3. {cluster}

#### 4. eXtreme Gradient Boosting (XGBoost)

##### What is XGBoost?
Machine learning algorithm designed for structured data.  
It improves prediction accuracy by sequentially boosting weak models while reducing errors.

##### How It Works:
- Builds decision trees sequentially
- Each tree corrects errors from the previous one
- Uses gradient boosting to optimize predictions


##### Why XGBoost?
###### Handles Complex Interactions Between SES Factors
- Mental health is influenced by multiple SES factors (e.g., income, education, household size).
- XGBoost captures nonlinear relationships & interactions better than traditional regression models.
  	- The impact of education on depression might depend on income level, and XGBoost can learn these dependencies on its own.

###### Feature Importance and Interpretability
- Ranks features by importance, showing which SES factors are most predictive of depression (PHQ-9 scores).
- Helps identify key factors driving mental health disparities.

###### Good at Handling Large, Imbalanced Datasets
- NHANES has imbalanced data (e.g., more people with low PHQ-9 scores than high).
- XGBoost has built-in handling for class imbalance, improving predictions across different groups.
- Confirms accurate predictions across different SES groups, even if some are underrepresented.
  

##### Code Breakdown
###### Defining Predictors
- Selected 10 SES features for predicting PHQ-9 scores.

###### Split Data Into Training & Testing Sets
- 80% training, 20% testing for model evaluation.

###### Convert Data for XGBoost
- XGBoost requires numeric matrix format.
- Target variable: PHQ-9 score (Depression severity).

###### Train XGBoost Model
- 100 boosting rounds, learning rate = 0.1, max tree depth = 6 levels.

###### Evaluate Model Performance
- RMSE (Root Mean Squared Error): Measures prediction accuracy.
- R-squared: Shows how well SES factors explain depression variability.

###### Feature Importance Analysis
- Identifies key predictors affecting PHQ-9 scores.


<iframe src="Feature_Importance_Plot.html" width=800 height=600 frameBorder=0></iframe>

## IV. Conclusion


## V. References

