# Spam Detection/Classification with Logistic Regression and Random Forest Models

This project develops supervised machine learning (ML) models that will accurately detect spam email.  The main objective is to classify email as spam or not spam and compare the performance of two classification models: **Logistic Regression** and  **Random Forest Classifier** .

**[Data](#data) | [Modeling](#modeling) | [Evaluation and Scoring](#evaluation-and-scoring) | [Technologies and Tools](#technologies-and-tools)**

---

## Abstract

The project creates classification models to fit data is sourced from the UCI Spambase dataset and predict whether an email is spam or not spam. Key focus is on accuracy comparison between the models, to determine the best approach for email classification.

The UCI Spambase dataset was pre-processed and scaled, and two models were created and trained:

* Logistic Regression Model
* Random Forest Model

---

## Data

**Sourcing** : Dataset Source: [UCI Machine Learning Library](https://archive.ics.uci.edu/dataset/94/spambase)

**Pre-Processing:**

* `pandas`, `sklearn.model_selection` used to load dataset, inspect the dataset's structure and data types, and separate the y/target from the X/feature data, and verify label balance.
* `sklearn.preprocessing` were used to apply `StandardScaler `to scale the features for both training and test data.

---

## Modeling

### Model Selection

* **Logistic Regression** from `sklearn.linear_model`
* **Random Forest Classifier** from `sklearn.ensemble`

---

### Evaluation and Scoring

**Accuracy Metric** : The primary evaluation metric was `accuracy_score` from `sklearn.metrics`.

* **Logistic Regression** training score: 0.9296
* **Logistic Regression** accuracy_score: 0.9279
* **Random Forest Classifier** training score: 0.9997
* **Random Forest Classifier** accuracy_score: 0.9652

---

## Interpretation and Insights

Random Forest Classification has a higher accuracy 96.5%, but the Training Score of 99.97% suggests this model is highly over-fit.  The Logistic Regression model performs well at 92.8%.

I had anticipated the following:

* **Logistic Regression** might struggle with non-linear data; however, the data appeared to be fairly linear, without too many outliers, so handed the data well.
* **Random Forest** model would handle colinear Features better, but might struggle with overfitting; that seems to be the case here and the overfitting is the more dominating effect.

**Note of interest:** Reviewing Random Forest 'feature_importances', the biggest predictors of 'spam' are the **character frequency** of ! (at 12.2%) and $ ()at 9.5%).  Additionally, the **presence of words**: free, remove, your, hp(?), and money dominated the feature importances:

[(0.12192112814008209, 'char_freq_!'),
 (0.09533933570058972, 'char_freq_$'),
 (0.07158337229698059, 'word_freq_free'),
 (0.06923901267709875, 'word_freq_remove'),
 (0.06811104369368015, 'capital_run_length_average'),
 (0.05579496385525832, 'capital_run_length_longest'),
 (0.0533025421651241, 'word_freq_your'),
 (0.045464200536752736, 'capital_run_length_total'),
 (0.03860171446883917, 'word_freq_hp'),
 (0.03164392902362354, 'word_freq_money')]


---

## Technologies and Tools

* **Data Preprocessing** : `pandas` for handling and cleaning data.
* **Scaling** : `StandardScaler` from `sklearn.preprocessing` for feature scaling.
* **Modeling** : `LogisticRegression` and `RandomForestClassifier` from `sklearn` for model training.
* **Environment** : Jupyter Notebook

---
