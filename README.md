# Flu Shot Learning – Vaccine Prediction

This project explores the prediction of vaccination behavior using machine learning.

The goal is to predict the probability that an individual receives:

- the **seasonal flu vaccine**
- the **H1N1 vaccine**

The project is based on the **DrivenData Flu Shot Learning challenge**, where the objective is to model vaccination behavior using demographic and health-related survey data.

The problem is formulated as a **probabilistic binary classification task with two outputs**.

---

# Problem Description

Vaccination plays a critical role in public health, especially for preventing the spread of infectious diseases such as seasonal influenza and H1N1.

However, a large portion of the population remains unvaccinated each year. Understanding which individuals are more likely to get vaccinated can help design better public health strategies.

This project aims to build machine learning models capable of predicting the **probability of vaccination** based on demographic information, behavioral patterns, and health-related opinions.

---

# Dataset

Source: **DrivenData – Flu Shot Learning Challenge**

The dataset contains survey responses describing individuals and their vaccination behavior.

### Dataset size

Training set:
- **26,707 individuals**

Test set:
- **26,708 individuals**

Number of features:
- **36 variables**

These include both **numerical and categorical variables**, some of which contain missing values.

### Target variables

- `seasonal_vaccine`
- `h1n1_vaccine`

Each target variable indicates whether the individual received the vaccine (1) or not (0).

---

# Machine Learning Task

The task is a **supervised binary classification problem**.

For each individual, the model predicts the **probability of vaccination**.

Two separate prediction tasks are performed:

- prediction of **seasonal flu vaccination**
- prediction of **H1N1 vaccination**

---

# Data Preprocessing

A preprocessing pipeline was implemented using **scikit-learn tools**.

The preprocessing steps include:

### Handling missing values
- numerical variables: **median imputation**
- categorical variables: **most frequent value**

### Encoding categorical variables
Categorical features are transformed into numerical features using **One-Hot Encoding**.

### Data splitting

The dataset is split into:

- **80% training data**
- **20% validation/test data**

The split is **stratified** to preserve the class distribution.

---

# Models Used

Two supervised machine learning models were implemented and compared.

## Logistic Regression

Logistic regression is a simple and interpretable model commonly used for binary classification.

Hyperparameters:

```python
LogisticRegression(
    max_iter=1000,
    solver="lbfgs"
)
 ```

## Random Forest

Random Forest is an ensemble learning method based on multiple decision trees.

Hyperparameters:

```python
RandomForestClassifier(
    n_estimators=200,
    max_depth=None,
    random_state=42,
    n_jobs=-1
)
```
# Evaluation Metrics

Model performance was evaluated using multiple complementary metrics.

## Primary Metric

### ROC-AUC

This metric measures the model’s ability to discriminate between vaccinated and non-vaccinated individuals.

## Additional Metrics

### Accuracy

### Confusion Matrix

These metrics provide additional insight into classification errors.

# Results

The following ROC-AUC scores were obtained:

| Model | Target | ROC-AUC |
|------|------|------|
| Logistic Regression | Seasonal Vaccine | 0.8555 |
| Random Forest | Seasonal Vaccine | 0.8533 |
| Logistic Regression | H1N1 Vaccine | 0.8352 |
| Random Forest | H1N1 Vaccine | 0.8333 |

# Error Analysis

The confusion matrix analysis highlights that:

the model correctly identifies a large number of vaccinated and non-vaccinated individuals

however, some false negatives remain, meaning that certain vaccinated individuals are predicted as non-vaccinated

In a public health context, these errors may be important because they correspond to individuals whose vaccination behavior is not correctly captured by the model.

# Methodological Discussion

The results suggest that relationships between variables and vaccination decisions are mostly linear or quasi-linear, which explains the strong performance of logistic regression.

Although Random Forest can model complex interactions, its added complexity did not significantly improve performance on this dataset.

Possible improvements include:

- hyperparameter optimization

- cross-validation instead of a single train/test split

- exploration of more advanced models

# Repository Structure 

## Repository Structure

```bash
flu-shot-learning-ml/
│
├── Flu_Shot_Learning.ipynb
├── README.md
└── requirements.txt
```
Main file:

### Flu_Shot_Learning.ipynb

This notebook contains:

- data preprocessing

- model training

- evaluation

- prediction generation

# How to Run the Project

## Install dependencies

```bash
pip install -r requirements.txt
```

## Run the notebook

```bash
jupyter notebook Flu_Shot_Learning.ipynb
```
# Libraries Used

- pandas

- numpy

- scikit-learn

- matplotlib

- seaborn

- jupyter

# Author

LEFOUILI Lina Ikram