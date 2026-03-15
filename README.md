# Cardiovascular Disease Prediction using Machine Learning

## Project Summary

This project explores the use of machine learning models to predict the likelihood of cardiovascular disease based on patient health data. Logistic Regression, Random Forest, and Gradient Boosting models were trained and evaluated using multiple performance metrics, including Accuracy, Precision, Recall, F1 Score, and ROC-AUC. These three models were chosen because they fit the type of data (binary) and to compare a linear baseline against more complex ensemble methods. 

To better understand and communicate the results beyond Python charts, the model outputs were visualized through interactive dashboards built in Tableau. These dashboards provide insights into model performance, feature importance, and prediction behavior, allowing users to better compare each model and explore the results. 

As a whole, this repository covers an end-to-end machine learning workflow, including data preprocessing, model training, feature engineering, performance evaluation, and interactive data visualization. 

---

## Technologies Used

The project was implemented in Python using the following libraries:

* pandas
* numpy
* scikit-learn
* matplotlib

**Tableau** was used as an additional external visualizations tool.

---

## Overview and Project Goal

The overall workflow includes:

* Data exploration and preprocessing
* Baseline model training
* Feature engineering
* Model retraining with engineered features
* Model comparison using multiple evaluation metrics
* Results visualization

As mentioned, three machine learning models were evaluated:

* **Logistic Regression**: A linear classification model used as a baseline. Logistic Regression is simple, interpretable, and often performs well on structured datasets.
* **Random Forest**: An ensemble model that combines multiple decision trees to improve predictive performance and reduce overfitting.
* **Gradient Boosting**: A boosting-based ensemble method that sequentially builds trees to correct errors made by previous trees. This model achieved the strongest overall performance in this project.

The goal is to identify patterns in patient data that signal cardiovascular risk, evaluate how each model performs in this task, and provide visualizations for the results

---

## Dataset

The dataset used for the project, **Cardiovascular Disease Dataset**, is available on Kaggle.

Due to licensing restrictions, the dataset is not included in the repository. Instead, it must be downloaded directly from Kaggle.

Dataset source: https://www.kaggle.com/datasets/sulianova/cardiovascular-disease-dataset

You can download the dataset using the Kaggle CLI:

```bash
!pip install kaggle

# Set your Kaggle API credentials (replace with your own)
!export KAGGLE_USERNAME="your_username"
!export KAGGLE_KEY="your_key"

# Download dataset
!kaggle datasets download sulianova/cardiovascular-disease-dataset

# Unzip dataset
!unzip cardiovascular-disease-dataset.zip
```
---

## Project Structure

The repository includes the notebook with the code, the packaged tableau workbook, the exported .csv data files, and images of each of the three dashboards created. It also includes a requirements.txt file. 

```
Cardiovascular-Disease-Prediction/
│
├── notebooks/
│   └── Cardiovascular_Disease_Prediction.ipynb
│
├── tableau/
│   └── cardiovascular_disease_prediction.twbx
│
├── data/
│   ├── model_comparison_metrics.csv
│   ├── feature_importance.csv
│   ├── rf_feature_importance.csv
│   ├── gb_feature_importance.csv
│   ├── model_predictions_long.csv
│   └── model_predictions.csv
│
├── images/
│   ├── model_performance_dashboard.png
│   ├── model_explainability_dashboard.png
│   └── prediction_analysis_dashboard.png
│
├── requirements.txt
│
├── README.md
└── LICENSE

cardiovascular-disease-ml/
│
├── images/
│   ├── model_performance_dashboard.png
│   ├── model_explainability_dashboard.png
│   └── prediction_analysis_dashboard.png
│
├── notebooks/
│   └── cardiovascular_ml.ipynb
│
├── data/
│   ├── model_comparison_metrics.csv
│   ├── feature_importance.csv
│   └── model_predictions.csv
│
└── README.md
```

---

## Notebook Structure

1. **Data Loading**

Importing the dataset and preparing it for analysis.

2. **Data Exploration**

Examining feature distributions, correlations, and potential issues in the dataset.

3. **Data Cleaning and Wrangling**

Preparing the dataset for machine learning, including handling column formats and feature transformations.

4. **Baseline Models**

Training initial models to establish baseline performance.

5. **Feature Engineering**

Creating additional features such as BMI and pulse pressure to test whether they improve model performance.

6. **Retraining**

Retraining models using the final feature set.

7. **Model Comparison**

Evaluating model performance using several metrics:
   * Accuracy
   * Precision
   * Recall
   * F1 Score
   * ROC-AUC
  
8. **Export for Visualization**

Exporting the data to .csv format for external analysis and visualization.

9. **Conclusion**

Interpreting results and identifying the best performing model.

## Model Evaluation

The models were evaluated using multiple classification metrics:

* **Accuracy** — overall proportion of correct predictions
* **Precision** — proportion of predicted positives that are correct
* **Recall** — ability to correctly identify positive cases
* **F1 Score** — balance between precision and recall
* **ROC-AUC** — overall ability to distinguish between classes

The results of the models in each metric are exported as:

```
model_comparison_metrics.csv
```
Gradient Boosting achieved the strongest overall performance. In particular, it obtained the highest recall, which is an important metric in medical prediction tasks because it reflects the model's ability to correctly identify positive cases. This in turn results in fewer false negatives, which has a higher priority than reducing false positives. 

---

## Feature Importance

Feature importance analysis was performed for the tree-based models:

* Random Forest
* Gradient Boosting

The exported files with the results are:

```
rf_feature_importance.csv
gb_feature_importance.csv
```

The analysis shows that **systolic blood pressure (ap_hi)** is the most influential feature in both models, followed by variables such as age, cholesterol levels, and diastolic blood pressure (ap_lo).

---

## Prediction Outputs

Model predictions on the test set are exported as:

```
model_predictions_long.csv
```

This file includes:

* Actual labels
* Model predictions
* Predicted probabilities

All of these outputs can be used for further analysis or visualization, which was done here using Tableau. 

---

## Tableau Dashboards

### Model Performance

Comparison of Logistic Regression, Random Forest, and Gradient Boosting across the aforementioned evaluation metrics: Accuracy, Precision, Recall, F1 Score, and ROC-AUC.

![Model Performance](images/model_performance_dashboard.png)

[View Interactive Dashboard on Tableau Public](https://public.tableau.com/views/cardiovascular_disease_prediction_model_performance/CardiovascularDiseasePrediction-ModelPerformance?:language=es-ES&publish=yes&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link)

---

### Model Explainability

Feature importance visualization highlighting the variables that influence cardiovascular disease prediction the most.

![Feature Importance](images/model_explainability_dashboard.png)

[View Interactive Dashboard on Tableau Public](https://public.tableau.com/views/feature_importance_analysis/FeatureImportanceAnalysis?:language=es-ES&publish=yes&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link)

---

### Prediction Analysis

Analysis of model prediction behavior using confusion matrices, probability distributions, and probability vs. actual outcome comparisons.

![Prediction Analysis](images/prediction_analysis_dashboard.png)

[View Interactive Dashboard on Tableau Public](https://public.tableau.com/views/prediction_behavior_analysis/PredictionBehaviorAnalysis?:language=es-ES&:sid=&:redirect=auth&publish=yes&showOnboarding=true&:display_count=n&:origin=viz_share_link)

---

## Key Insights

- **Tree-based models slightly outperform Logistic Regression.**  
Random Forest and Gradient Boosting without additionally engineered features achieved the highest performance across most evaluation metrics, suggesting that nonlinear relationships between features and cardiovascular disease risk are present in the dataset.

- **All models show similar performance levels.**  
While tree-based models show a slight edge, all models perform within a narrow range (~0.73 accuracy), suggesting a robust baseline for the dataset.

- **ROC-AUC scores around 0.80 indicate good class separation.**  
This suggests the models can reasonably distinguish between patients with and without cardiovascular disease. A ROC-AUC of ~0.80 is generally considered good.

- **Precision and Recall trade-offs highlight prediction balance.**  
The models maintain relatively balanced precision and recall values, meaning they perform consistently in identifying true positive cases while limiting false positives, reflected in a stable F1-score across all models.

- **Feature importance analysis highlights the most influential health indicators.**  
Variables such as blood pressure, age, and other health-related features contribute significantly to cardiovascular disease prediction in the trained models. In particular, systolic blood pressure was by far the most influential variable in both Random Forest and Gradient Boosting.

- **Prediction probability distributions show clear separation between classes.**  
Higher predicted probabilities are generally associated with true positive cases, indicating that the models are able to capture meaningful patterns in the data.

---

## License

This repository is licensed under the **MIT License**.

Note that the dataset used in this project is provided by Kaggle and is not redistributed in this repository. To use the same dataset, you have to download it yourself directly from Kaggle. 

---

## Author

David Xu Hu  
BSc Software Engineering — Universidad Complutense de Madrid

GitHub: https://github.com/bigfoot-888
LinkedIn: www.linkedin.com/in/david-xu-hu-bb8abb350
