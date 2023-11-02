# Module 20 Challenge - Credit Risk Classification
Python scripts by Peter Solis in Jupyter Notebook, code was written independently using the provided starter code & knowledge from class.

# Credit Risk Analysis Report

## Overview of the Analysis

In this analysis, I tested a Logistic Regression style model (a model that gives a probability of being part of a group) on a set of training data that had been prepared in two different ways. The data contained info on the loan size, interest rate, borrower's income, debt-to-income ratio, number of accounts, any derogatory marks, and the total debt. These variables were used to predict whether or not the loan's status was healthy or at high risk of defaulting.
The first model was trained & tested with the data as it was. The second was trained and tested on the same data, but the training set was resampled to evenly distribute the number of high-risk and healthy loans (this was done using random oversampling, which duplicates data points from the less common group (in this case, high-risk loans), to provide an equal quantity of data in each of the two groups for the model's training.

## Results

* Machine Learning Model 1 (Unaltered Training Data):
  * The balanced accuracy score of the first model was 95.2%. 
    * Balanced accuracy is the average of the true positive recall (correct high-risk guesses / all high-risk guesses) and the true negative recall (correct healthy guesses / all healthy guesses) 
  * The model was extremely precise in guessing healthy loans (almost 100% of guesses were correct), but struggled with high-risk loans (only 85% of loans the model classified as high-risk actually were.)
  * The model did similarly well on recall; about 99% of healthy loans were correctly classified, while 91% of high-risk loans were correctly classified.

* Machine Learning Model 2 (Resampled / Oversampled Training Data):
  * The balanced accuracy score for the resampled model was 99.4%.
  * This model had very similar precision scores, also nearing 100% for healthy loans, while actually falling a percentage to 84% precision with high-risk loans, meaning it incorrectly classified slightly more healthy loans as high-risk.
  * Where this model did best was on recall, keeping the 99% of healthy loans being correctly classified as such, while improving the recall of high-risk loans to 99% as well.
  
## Summary

The most important qualifiers for this model to do are:
  * Correctly classify high-risk loans as high-risk
  * Not incorrectly classify healthy loans as high-risk
The first is important, because finding high-risk loans amidst the far greater number of healthy loans would be extremely difficult, leading to big losses. The second is important for a similar reason, if even a few percentage of the healthy loans are classified as high-risk, this would still double or triple the size of the pool being classified as high-risk, leading to a lot more lost loans, many of which were healthy.

In this scenario, both models did quite well for first looks at the problems. Due to the high skew in the data towards healthy loans, I would say the second model, which was trained on the oversampled data, performs better, as it is much improved on the first qualifier. It classified far fewer high-risk loans as healthy, cutting down on loans that could lose the bank money slipping through the cracks (from 56 incorrectly classified as healthy to 4).

The two models performed almost identically in every other way, with one key weakness. Both models incorrectly classified a relatively small percent of the healthy loans as high-risk (less than 1% of all healthy loans), but due to the number of healthy loans being much bigger, this meant there was still a sizeable number of healthy loans being incorrectly classified, making up about 15% of the pool of loans classified as high-risk (or around 100 of the 700 high-risk guesses). This is a small enough number, however, that the model is still worth using, and due to the second model being very successful in not classifying high-risk loans as healthy, you could manually review the loans it classifies as high-risk to sort out the mistakes, while being confident that all but very few of the loans it classifies as healthy are indeed healthy.