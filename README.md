# Improving a Spam Email Filter

### Goals:

Develop a supervised machine learning (ML) model that will accurately detect spam emails.

Create two classification models to fit the provided data, and evaluate which model is more accurate at detecting spam

* Logistic Regression Model
* Random Forest Model.

---

### Data:

This dataset contains information about emails, with two possible classifications: spam and not spam.

* The data is located at [https://static.bc-edx.com/ai/ail-v-1-0/m13/challenge/spam-data.csv](https://static.bc-edx.com/ai/ail-v-1-0/m13/challenge/spam-data.csv)
* Dataset Source: [UCI Machine Learning Library](https://archive.ics.uci.edu/dataset/94/spambase)

---

### Steps:

* Split the data into training and testing sets.
* Scale the features.
* Create a logistic regression model.
* Create a random forest model.
* Evaluate the models.

###### Split the Data into Training and Testing Sets

1. Read data into a Pandas DataFrame
2. Inspect data and make a prediction as to which model  (Logistic Regression, Random Forest Classifier)
3. Create the labels set (`y`) from“spam” column, and features (`X`) DataFrame from remaining columns.
   * value of 0 in the “spam” column means that the message is legitimate.
   * value of 1 means that the message has been classified as spam.
4. Check the balance of the labels variable (`y`) by using the `value_counts` function.
5. Split the data into training and testing datasets by using `train_test_split`.

###### Scale the Features

1. Create an instance of `StandardScaler`.
2. Fit the Standard Scaler with the training data.
3. Scale the training and testing features DataFrames using the transform function.

###### Create a Logistic Regression Model

1. Create and Fit a logistic regression model using the scaled training data (`X_train_scaled` and `y_train`). Set the `random_state` argument to `1`.
2. Save the predictions on the testing data labels by using the testing feature data (`X_test_scaled`) and the fitted model.
3. Evaluate the model performance by calculating the accuracy score of the model.

###### Create a Random Forest Model

1. Create and Fit a random forest classifier model using the scaled training data (`X_train_scaled` and `y_train`).
2. Save the predictions on the testing data labels by using the testing feature data (`X_test_scaled`) and the fitted model.
3. Evaluate the model performance by calculating the accuracy score of the model.

###### Evaluate the Models

* **Logistic Regression** training score: 0.9296
* **Logistic Regression** accuracy_score: 0.9279
* **Random Forest Classifier** training score: 0.9997
* **Random Forest Classifier** accuracy_score: 0.9652

---

### **Results:**

Random Forest Classification has a higher accuracy, but the Training Score suggests this model is highly over-fit.  **The Logistic Regression model is a 'better' model even though it's accuracy is lower.**

My prediction was "I think it's possible that many Features will be colinear and that Random Forest will handle those better."  This was not correct. However, the models did behave as expected:

* I thought that Logistic Regression might struggle with non-linear problems, but this one appears to be fairly linear, without too many outliers.
* I mentioned that Random Forest might struggle with overfitting, and I believe that is the case here and the more dominating effect.

**Final thoughts:**

Reviewing the Random Forest Graph with 'feature_importances', I found it interesting that some of the biggest predictors of 'spam' are the frequency of ! and $ characters, as well as the words: free, remove, your, hp(?), and money.

This focus on money-related terms, as well as seeming 'demands' ("Your xyz needs attention ....") is expected, but interesting to see statistically.

```
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


```
