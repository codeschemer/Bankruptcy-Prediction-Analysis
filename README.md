### Bankruptcy Prediction Analysis   

**1. Introduction**  
This project aims to predict corporate bankruptcy using financial indicators. The dataset contains 96 features derived from financial ratios (e.g., profitability, leverage, liquidity) and a binary target variable (Bankrupt?), where 1 indicates bankruptcy. Machine learning models are trained to classify companies as bankrupt or non-bankrupt, with insights into key predictive features.  
  
**2. Dataset Overview**  
Source: Bankruptcy Prediction Data.csv (6,819 samples, 96 features).  
  
Target Variable: Bankrupt? (binary: 1 = bankrupt, 0 = non-bankrupt).  
  
Features: Financial metrics such as ROA, debt ratios, net income, and operating margins.  

Data Quality: No missing values detected.  
  
**3. Methodology**  
3.1 Feature Selection  
SelectKBest: Top 10 features selected using ANOVA F-test (f_classif).  

Key features: ROA(C) before interest, Net worth/Assets, Debt ratio %, and Retained Earnings to Total Assets.  

Recursive Feature Elimination (RFE): Identified 5 most important features using a Random Forest classifier (e.g., ROA(A) before interest, Persistent EPS).  

3.2 Models Evaluated  
Logistic Regression  
  
Decision Tree  
  
Random Forest  
  
3.3 Training & Evaluation  
Split: 70% training, 30% testing.  

Metrics: Accuracy, Precision, Recall, F1 Score, AUC-ROC.  

**4. Results**  
**Model                    &nbsp;Accuracy	&nbsp;Precision,	&nbsp;Recall,	  &nbsp;F1 Score,	&nbsp;AUC-ROC,**  
Logistic Regression:	     &nbsp;96%,	    &nbsp;0.71,	      &nbsp;0.06,	    &nbsp;0.12,	    &nbsp;0.934,  
Decision Tree:	           &nbsp;95%,	    &nbsp;0.33,	      &nbsp;0.24,	    &nbsp;0.28,	    &nbsp;0.612,  
Random Forest:	           &nbsp;97%,	    &nbsp;0.71,	      &nbsp;0.19,	    &nbsp;0.30,	    &nbsp;0.898,  
  
Key Observations:  
Random Forest outperformed others with 97% accuracy and 0.898 AUC-ROC, indicating strong overall performance.  

Logistic Regression had high accuracy but extremely low recall (6%), suggesting bias toward the majority class (non-bankrupt companies).  

Decision Tree showed lower precision and recall, likely due to overfitting.  
  
Feature Importance:  
Financial health indicators like ROA, debt ratios, and retained earnings were critical predictors.  

RFE highlighted ROA(A) before interest and Persistent EPS as top contributors.  
  
**5. Challenges & Limitations**  
Class Imbalance: The dataset likely has few bankrupt cases (class 1), causing models to prioritize majority-class accuracy.  

Recall Issues: Low recall for Logistic Regression implies missed bankrupt cases, a critical flaw in real-world risk assessment.  

Feature Redundancy: Warnings during feature selection (e.g., constant features) suggest potential data quality issues.  

**6. Recommendations**  
Address Class Imbalance: Use techniques like SMOTE or class weighting to improve recall.  

Hyperparameter Tuning: Optimize Decision Tree depth and Random Forest parameters to reduce overfitting.  

Alternative Models: Explore gradient boosting (XGBoost, LightGBM) or neural networks for better sensitivity.  

Feature Engineering: Investigate interactions between financial ratios or derive new metrics.  

**7. Conclusion**  
The Random Forest model demonstrated robust performance in predicting bankruptcy, leveraging key financial indicators. However, low recall for minority-class cases highlights the need for balancing techniques. Future work should focus on improving model sensitivity to ensure reliable identification of at-risk companies.  
