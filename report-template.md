# Module 12 Report Template

## Overview of the Analysis

<!---
In this section, describe the analysis you completed for the machine learning models used in this Challenge. This might include:

* Explain the purpose of the analysis.
* Explain what financial information the data was on, and what you needed to predict.
* Provide basic information about the variables you were trying to predict (e.g., `value_counts`).
* Describe the stages of the machine learning process you went through as part of this analysis.
* Briefly touch on any methods you used (e.g., `LogisticRegression`, or any resampling method).
--->

We analyzed the different predictive accuracy of a logistic regression model using an imbalanced data set and a resampling of that data set. The LogisiticRegression model implements regularized logistic regression using the ‘liblinear’ library, ‘newton-cg’, ‘sag’, ‘saga’ and ‘lbfgs’ solvers.

The data provides a series of data points on a given borrower, along with the loan's risk classification. Our goal is to predict the "loan_status" (0 for healthy and 1 for risky) of a given loan, given the characteristics of the loan and its borrower.

When running "value_counts" on the "loan_status" columns, we realize that there is an imbalance between the 1's and the 0's, so we run our ML model with the original set, as well as with a resampled data set that has the same number of 1's and 0's.

Our approach consisted of first splitting the data into a train and test set, so that we may validate the effectiveness of our model with new data that it hadn't seen. We then instantiated and fit a LogisticRegression model with the training data in order to prep it to make predictions with the test data. We then resampled the data by over-fitting the minority sample of loan_status entries, and reran a LogisticRegression model with the resampled data to compare the results.

**NOTE: We also ran the same analysis with first scaling the data, and obtained different comparisons (see the "(with scaling) credit_risk_resampling.ipynb" file)**

## Results

<!---
Using bulleted lists, describe the balanced accuracy scores and the precision and recall scores of all machine learning models.

* Machine Learning Model 1:
  * Description of Model 1 Accuracy, Precision, and Recall scores.

* Machine Learning Model 2:
  * Description of Model 2 Accuracy, Precision, and Recall scores.
--->

* Machine Learning Model 1: LogisticRegression with initial data
  * Accuracy: 95.2%; the accuracy is quite high for the model
  * Precision: 85%; True Pos / (True Pos + False Pos) - the model considers significantly more loans as positive (high-risk) than it should
  * Recall: 92%; True Pos / (True Pos + False Neg) - the model considers some loans as negative (normal) than it should mark as positive (high-risk)
  * F1 score: 88%; the model is relatively dependable, but not that much
<br><br>

* Machine Learning Model 2: LogisticRegression with resampled data
  * Accuracy: 99.4%; the accuracy is very high for the model
  * Precision: 84%; True Pos / (True Pos + False Pos)
  * Recall: 99%; True Pos / (True Pos + False Neg) - the recall improved significantly by 7% for a negligeable loss of precision of 1%
  * F1 score: 91%; the model is more dependable than the one with the initial data

## Summary

<!---
Summarize the results of the machine learning models, and include a recommendation on the model to use, if any. For example:
* Which one seems to perform best? How do you know it performs best?
* Does performance depend on the problem we are trying to solve? (For example, is it more important to predict the `1`'s, or predict the `0`'s? )

If you do not recommend any of the models, please justify your reasoning.<br>
--->

With a higher F1 score, and frankly higher scores on all metrics excel for a 1% dip in precision, model 2 with a LogisticsRegression run on over_sampled data outperforms model 1 which uses the original data.<br>

Performance does depend on the problem we're solving, as the results for predicting 1 vs 0 is considerable.
