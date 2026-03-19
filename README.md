# Cardiovascular Disease Prediction using Machine Learning

## Overview

This project explores the use of machine learning to predict cardiovascular disease risk based on patient health data. Three classification models were trained and evaluated, including Logistic Regression, Random Forest, and Gradient Boosting. These were chosen to compare a linear baseline (Logistic Regression) against more complex ensemble methods on a binary classification task like this one. 

**Gradient boosting** achieved the strongest overall performance, with ~0.73 accuracy and ~0.80 ROC-AUC. In particular, it obtained the highest recall, which is a big priority in medical prediction tasks as it minimizes false negatives. The risk that comes with false negatives is almost always higher than having to deal with false positives. 

The full workflow includes: 
* Data exploration and preprocessing
* Baseline model training
* Feature engineering (BMI, pulse pressure)
* Model retraining with engineered features
* Model comparison and comparison with Accuray, Precision, Recall, F1 Score, ROC-AUC, and Confusion Matrix
* Interactive results visualization via Tableau

The end goal is to identify patterns in patient data that signal cardiovascular risk, evaluate how each model performs in this task, and provide good visualizations for the results through Tableau. 

---

## Technologies Used

The project was implemented in Python using the following libraries:

* Python
* Jupyter Notebook
* pandas, numpy — data manipulation
* scikit-learn — model training and evaluation
* matplotlib — plotting
* Tableau — interactive dashboard visualization

Python dependencies are listen in `requirements.txt`. 

---

## Getting Started

### 1. Clone the repository

git clone https://github.com/bigfoot-888/Cardiovascular-Disease-Prediction.git
cd Cardiovascular-Disease-Prediction

### 2. Install dependencies

pip install -r requirements.txt

### 3. Download the dataset

The dataset is not included in the repository due to licensing restrictions. Download it from Kaggle using one of the methods below.

**Option A — Kaggle CLI (terminal):**

export KAGGLE_USERNAME="your_username"
export KAGGLE_KEY="your_api_key"
kaggle datasets download sulianova/cardiovascular-disease-dataset
unzip cardiovascular-disease-dataset.zip -d data/

**Option B — Inside a Jupyter notebook:**

!pip install kaggle
import os
os.environ["KAGGLE_USERNAME"] = "your_username"
os.environ["KAGGLE_KEY"] = "your_api_key"
!kaggle datasets download sulianova/cardiovascular-disease-dataset
!unzip cardiovascular-disease-dataset.zip -d data/

Alternatively, download the dataset manually from:
https://www.kaggle.com/datasets/sulianova/cardiovascular-disease-dataset

### 4. Run the notebook

Open and run notebooks/Cardiovascular_Disease_Prediction.ipynb in Jupyter.

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
```

---

## Notebook Structure

1. **Data Loading**: Importing the dataset and preparing it for analysis.

2. **Data Exploration**: Examining feature distributions, correlations, and potential issues in the dataset.

3. **Data Cleaning and Wrangling**: Preparing the dataset for machine learning, including handling column formats and feature transformations.

4. **Baseline Models**: Training initial models to establish baseline performance.

5. **Feature Engineering**: Creating additional features such as BMI and pulse pressure to test whether they improve model performance.

6. **Retraining**: Retraining models using the final feature set.

7. **Model Comparison**

Evaluating model performance using several metrics:
   * Accuracy
   * Precision
   * Recall
   * F1 Score
   * ROC-AUC
  
8. **Export for Visualization**: Exporting the data to .csv format for external analysis and visualization.

9. **Conclusion**: Interpreting results and identifying the best performing model.

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
