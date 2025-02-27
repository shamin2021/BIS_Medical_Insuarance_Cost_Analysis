# Medical Insurance Cost Analysis and Prediction

## Overview
Healthcare costs are a significant concern for individuals and insurance companies. Understanding the factors that influence medical insurance costs can help insurance providers develop fair pricing strategies .This report presents an analysis of a dataset containing medical insurance records to identify key patterns in insurance charges and develop a predictive model to estimate insurance costs based on customer profiles. \

The primary objective is to address the business question: **"Which atterns and factors affecting medical insurance costs.?"**

This analysis uses statistical methods and machine learning techniques to uncover key drivers of customer satisfaction and provide actionable recommendations for improving customer experiences.

---

## Dataset


**The Medical Insurance Cost Prediction** dataset provides information about individuals and their medical insurance charges. The dataset is sourced from Kaggle and contains 1,338 records with 7 features with the following Attributed 

| Column   | Data Type  | Description  |
|----------|-----------|-------------|
| **age**  | Integer   | Age of the individual (18-64 years) |
| **sex**  | Categorical | Gender of the individual (male, female) |
| **bmi**  | Float     | Measure of body fat based on height and weight |
| **children** | Integer | Number of dependents (children) covered by insurance |
| **smoker** | Categorical | Smoking status (yes = smoker, no = non-smoker) |
| **region** | Categorical | Geographic region of residence (northeast, northwest, southeast, southwest) |
| **charges** | Float | Target Variable - Medical insurance cost (in USD) |

---

## 2 Methodology

### 2.1 Data Preprocessing & Cleaning  
To ensure high-quality data for analysis and modeling, the following preprocessing steps were performed:  

1. **Handling Missing Values** - The dataset was checked for missing values. Since no missing values were found, no imputation was necessary.  
2. **Checking for Outliers** - Boxplots were generated using `seaborn.boxplot()` to detect outliers in numerical features (e.g., `bmi`, `charges`).  
3. **Encoding Categorical Variables** - The dataset contained three categorical variables (`sex`, `smoker`, `region`), which were converted into numerical values to be used in machine learning models:  
   - One-hot encoding was applied to `region`.  
   - Label encoding was used for `sex`.  

### 2.2 Exploratory Data Analysis (EDA)  
Before applying machine learning models, EDA was conducted to understand the dataset’s structure and characteristics:  

1. **Summary Statistics** - Measures like mean, median, and standard deviation were analyzed to understand the distribution of features.  
2. **Correlation Analysis** - Pearson correlation coefficients were computed to identify relationships between features and the target variable.  
3. **Outlier Detection** - Boxplots and histograms were used to detect extreme values that might impact model training.  
4. **Feature Importance** - Initial assessments using Random Forest and Gradient Boosting models helped determine the most significant predictors.  

The insights gained through EDA guided feature selection for predictive modeling.  

### 2.3 Statistical Analysis  
To predict insurance charge levels, four models were trained and evaluated:  
- **Linear Regression**  
- **Decision Tree Regressor**  
- **Random Forest Regressor**  
- **Gradient Boosting Regressor (XGBoost)**  

The dataset was divided into **training (80%)** and **testing (20%)** sets to evaluate model performance. Feature importance analysis was also performed to identify the most influential factors affecting insurance charges.  


---
# Results  

## 1. Correlation Analysis  
- **Smoking status** had the strongest correlation with insurance charges.  
- **Age** and **BMI** showed a positive correlation, but weaker than smoking.  
- **Gender** and **Number of Children** had minimal impact on charges.  

## 2. Insurance Charges vs. Risk Factors  
- **Smokers** had significantly higher insurance charges.  
- **Age** was positively correlated with higher charges.  
- **BMI** influenced medical expenses, but with variability.  
- **Region** and **Gender** did not significantly impact charges.  

## 3. Model Performance Comparison  
| Model                     | R²   | RMSE   | MAE   | Notes |  
|---------------------------|------|--------|------|------------------------------------------------|  
| **Linear Regression**      | 0.74 | 6319.27 | 4160.25 | Struggled with non-linear relationships. |  
| **Random Forest Regressor** | 0.95 | 2446.07 | 695.44 | Sensitive to outliers. |  
| **Gradient Boosting (GBR)** | 0.96 | 6319.27 | 4160.25 | Reduced errors via iterative optimization. |  
| **XGBoost**                | **0.96** | **2504.11** | **694.18** | Best model, handled categorical features efficiently. |  

## 4. Feature Importance & SHAP Analysis  
- **Top Predictors**: Smoking, BMI, and Age.  
- **SHAP Analysis** confirmed **smoking** had the most influence, followed by BMI and Age.  
- **SHAP Dependence Plot** showed Age’s influence was moderated by the number of children.  
- **SHAP Force Plot** illustrated feature-level contributions for individual predictions.  

## 5. Business Implications  
- **Risk-Based Premium Adjustments**: Higher premiums for smokers and high-BMI individuals.  
- **Preventive Health Programs**: Discounts for maintaining a healthy BMI or quitting smoking.  
- **Regional Pricing Strategies**: Adjust pricing based on localized health trends.  
- **Customizable Insurance Plans**: Personalized premiums based on health metrics.  
- **Health Monitoring Incentives**: Reward policyholders for regular check-ups and fitness activities.  

## 6. Conclusion  
This analysis confirmed that **smoking, BMI, and age** are key drivers of insurance costs. By leveraging **XGBoost and SHAP analysis**, insurers can develop **data-driven pricing models** that improve risk assessment, customer engagement, and profitability.  

---

# Business Implications  

## 1. **Risk-Based Premium Adjustments**  
- Implement **tiered pricing models** where smokers and individuals with high BMI pay higher premiums.  
- Offer **discounts for non-smokers** and individuals maintaining a healthy BMI.  

## 2. **Regional Pricing Strategies**  
- Analyze **regional health trends** and adjust insurance rates accordingly.  
- Offer **region-specific health interventions** to reduce claim costs.  

## 3. **Customizable Insurance Plans**  
- Develop **personalized insurance plans** based on individual health metrics and lifestyle choices.  
- Implement **dynamic pricing models** that adjust based on an individual’s health improvements.  

## 4. **Gender-Specific Plans**  
- Investigate whether gender-based pricing adjustments are necessary based on further statistical validation.  

## 5. **Health Monitoring Incentives**  
- Reward policyholders for **regular health check-ups, exercise, and preventive care**.  
- Introduce **wearable health tracking integration** to monitor risk factors in real time.  

---

## How to Run the Code
1. **Clone the repository**:
    ```bash
    git clone https://github.com/shamin2021/BIS_Medical_Insuarance_Cost_Analysis.git
    cd BIS_Medical_Insuarance_Cost_Analysis

2. **Install Dependencies**:
    Ensure you have Python 3.11 installed, then install the required libraries

3. **Run the Jupyter Notebook**:
    Open the notebook and execute the cells to reproduce the analysis

---

## View the Report

The final report is available in the [`20020376_report.pdf`](Final_Report.pdf) file.