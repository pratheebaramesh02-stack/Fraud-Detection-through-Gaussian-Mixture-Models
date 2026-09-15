# Fraud-Detection-through-Gaussian-Mixture-Models

In this project, we try to predict fraud from a dataset with PCA-transformed features through the usage of different iterations of GMMs:

 - An Unsupervised GMM which models the overall distribution of data using one or more components
 - A Semi-supervised (one-class kind) GMM that only learns from the non-fraud transactions
 - A Supervised version where we fit a GMM each for fraud and non-fraud transactions.

The dataset used is Kaggle's credit card fraud detection dataset (https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud)

This is a derivative of https://github.com/lukysummer/Fraud-Detection-using-Gaussian-Mixtures/tree/main. But with certain modifications/additions, such as: 

1. Splitting the data chronologically rather than a random stratified split so we realistically train on past data, and test on the future data - making sure no information from the future transactions leak into the training data
2. We employ feature selection through KS test rather than a Gaussian, since KS test has important implications in fraud detection and is generally widely used
3. We implement PR-AUC apart from ROC-AUC due to the highly imbalanced nature of the dataset
4. We calculate posterior fraud probability using Bayesian rule i.e. P(transaction being fraud given it's fraudulent)
5. We check if this probability is reliable by plotting its calibration curve/reliability diagram.

Findings show Supervised model is superior of all in terms of evaluation metrics, signifying the importance of existing labelled fraud data in detection of fraudulent transactions
