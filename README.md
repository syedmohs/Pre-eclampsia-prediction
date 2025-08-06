# preeclampsia-risk-prediction

This script implements a machine learning pipeline for predicting **pre-eclampsia (PE)** using gene expression data. It includes functionality for preprocessing gene expression matrix series files, applying various machine learning classifiers, performing feature selection, and evaluating model performance using clinical metrics such as accuracy, precision, sensitivity, specificity, F1-score, and AUC.

---

## Requirements

To run this code, you will need to install the following Python libraries:

### Python Packages:

- **pandas**: For data manipulation and analysis.
- **numpy**: For numerical operations.
- **scikit-learn**: For machine learning algorithms, preprocessing, model evaluation, and feature selection.
- **xgboost**: For XGBoost classifier and model training.
- **matplotlib**: For plotting graphs and visualizations.
- **seaborn**: For statistical data visualization.
- **tqdm**: For displaying progress bars in loops.
- **torch**: For deep learning models using PyTorch.
- **shap**: For model interpretation and SHAP values.
- **statistics**: For basic statistical operations like mean calculation.
- **time**: For tracking runtime and performance.
- **gzip**: For reading compressed gene expression files.

---

## Installation Instructions

You can install the required Python libraries using pip. Use the following command:

```bash
pip install pandas numpy scikit-learn xgboost matplotlib seaborn tqdm torch shap
