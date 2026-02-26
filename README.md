# Software Defect Prediction Using Machine Learning
## Project Overview

This project investigates machine learning approaches for predicting software module defects using static code metrics.
The objective is to compare a linear baseline model (Logistic Regression) with an ensemble method (Random Forest) and evaluate their performance under class imbalance conditions.

The study emphasizes proper evaluation metrics and decision threshold adjustment to better align model behavior with defect detection priorities.

## Dataset

The dataset consists of 2109 software modules described by 22 static code metrics, including:
- Halstead complexity measures (e.g., difficulty, intelligence, length)
- Size-related metrics (e.g., lines of code)
- Structural metrics (e.g., number of blank lines)

The target variable indicates whether a module is defective.

- Defective modules: 15%
- Clean modules: 85%

This class imbalance makes accuracy an insufficient evaluation metric.

## Methodology

The project follows a structured machine learning workflow:

1. Exploratory Data Analysis (EDA)
    - Analysis of feature distributions
    - Examination of class imbalance
    - Correlation analysis
    - Detection of multicollinearity
    - Feature reduction using a correlation threshold (0.9)

   After removing redundant predictors, the feature set was reduced from 21 to 8 features.

2. Logistic Regression (Baseline Model)
    - Standardized features
    - Class weights set to "balanced"
    - Evaluation using precision, recall, F1-score, and ROC-AUC

3. Random Forest
    - Trained without scaling
    - Class weights set to "balanced"
    - Feature importance analysis
    - Decision threshold adjustment (from 0.5 to 0.3)

## Model Performance Comparison

| Model                          | Recall | Precision | F1-score | ROC-AUC |
|--------------------------------|--------|-----------|----------|----------|
| Logistic Regression            | 0.65   | 0.35      | 0.45     | 0.80     |
| Random Forest (0.5 threshold)  | 0.35   | 0.62      | 0.45     | 0.81     |
| Random Forest (0.3 threshold)  | 0.62   | 0.46      | 0.53     | 0.81     |

## Key Findings

- Software defect prediction is strongly influenced by code complexity and size metrics.
- Logistic Regression provides a strong and interpretable baseline.
- Random Forest improves discrimination performance (higher ROC-AUC).
- Default classification thresholds may be suboptimal under class imbalance.
- Adjusting the decision threshold significantly improves recall–precision balance.
- Random Forest with threshold adjustment achieved the best overall F1-score.

## Feature Importance Insights

The most influential predictors included:
- Halstead intelligence (i)
- Halstead difficulty (d)
- Halstead length (l)
- Lines of Code (loc)

These results suggest that module complexity and size are strongly associated with defect likelihood.

## Limitations

- Moderate dataset size (2109 samples)
- Class imbalance (15% defective)
- Only static code metrics were used
- Limited hyperparameter tuning

Future improvements could include cross-validation, systematic hyperparameter optimization, and exploration of gradient boosting methods.

## Technologies Used

- Python
- pandas
- scikit-learn
- matplotlib

## Conclusion

This project demonstrates that machine learning models can effectively capture predictive signals in static software metrics. While linear models provide a strong baseline, ensemble methods combined with threshold adjustment offer improved balance between recall and precision.

The findings align with software engineering principles: larger and more complex modules tend to exhibit higher defect risk.
