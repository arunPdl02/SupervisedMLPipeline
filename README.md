# Supervised Machine Learning Pipeline

## Overview
This project implements a reproducible machine learning pipeline for predictive modeling on a numeric dataset with 20 features and 20,000 observations. Multiple linear and non-linear models were evaluated, with a focus on correct evaluation discipline, feature selection, and model tuning.

The goal was to identify a model that generalizes well while avoiding common pitfalls such as data leakage and overfitting.

---

## Dataset
- **Size:** 20,000 rows  
- **Features:** 20 numeric predictors  
- **Target:** Continuous response variable (range approximately 0–21)

Exploratory data analysis revealed strong correlations among several predictors and evidence of non-linear structure, motivating the use of tree-based models.

---

## Modeling Approach
The following models were implemented and compared:

- Linear Regression  
- Ridge Regression  
- LASSO Regression  
- Random Forest  
- XGBoost  

Initial linear models performed poorly, indicating non-linear relationships in the data. Tree-based models were therefore explored in greater depth.

---

## Evaluation Strategy
- Data split: **75% training / 25% test**
- **Out-of-Bag Mean Squared Prediction Error (OOB MSPE)** was used for Random Forest hyperparameter tuning to avoid test-set leakage
- Final performance was evaluated on the held-out test set

This approach ensures fair model comparison and realistic generalization estimates.

---

## Feature Selection and Tuning
- Feature importance from the Random Forest model was used to remove low-impact predictors
- The model was retrained on a reduced feature set
- Hyperparameters tuned:
  - `mtry`
  - `nodesize`

The final Random Forest model achieved an OOB MSPE of approximately **14**, improving substantially over baseline models (~27 MSPE).

---

## Final Model
- **Model:** Random Forest  
- **Trees:** 500  
- **Key tuning parameters:**  
  - `mtry = 7`  
  - `nodesize = 1`  

Predictions on the test set were generated and saved for submission and downstream use.

---

## Reproducibility
To reproduce the final model:

1. Load the training data
2. Drop the specified low-importance variables
3. Set the random seed
4. Train the Random Forest with the tuned parameters

The full workflow and code are deterministic and reproducible.

---

## Technologies
- **Language:** R  
- **Libraries:** randomForest, corrplot  
- **Methods:** Feature importance analysis, hyperparameter tuning, supervised learning

---

## Notes
This project emphasizes **evaluation rigor, reproducibility, and ML system design** rather than maximizing performance through excessive tuning.

The full academic report with detailed analysis and figures is available in `STAT452_Report.pdf`.
