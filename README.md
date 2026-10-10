Multi-Class Intrusion Detection — NSL-KDD

Overview

This project explores multi-class classification of network connections using the NSL-KDD dataset. It compares Logistic Regression and Random Forest, with particular attention to class imbalance and the detection of rare attack types.

Objectives

- Group individual attack labels into broader attack categories.
- Develop and evaluate a Logistic Regression baseline.
- Compare its performance with a Random Forest classifier.
- Investigate the effects of class imbalance on minority-class detection.
- Explore custom decision thresholds to improve detection of user-to-root (U2R) attacks.

Dataset

The project uses the NSL-KDD network intrusion detection dataset.

The original attack labels are grouped into the following categories:

- "normal" — legitimate network connections
- "dos" — denial-of-service attacks
- "probe" — probing and scanning attacks
- "r2l" — remote-to-local attacks
- "u2r" — user-to-root attacks

An "other" category containing a single instance is excluded from model training because there are insufficient examples to support meaningful classification and evaluation.

Methodology

The analysis includes:

1. Loading the dataset and assigning feature names.
2. Mapping individual attack labels to broader categories.
3. Examining the distribution of the target classes.
4. Removing the original label and difficulty columns.
5. Applying one-hot encoding to categorical features.
6. Splitting the data into stratified training and test sets.
7. Standardising features for Logistic Regression.
8. Training and evaluating Logistic Regression and Random Forest.
9. Comparing class-specific precision, recall, and F1-score.
10. Exploring custom decision thresholds for U2R predictions.

Key Results

Model comparison

Metric| Logistic Regression| Random Forest
Overall accuracy| 96.73%| 99.85%
U2R precision| 0.06| 0.90
U2R recall| 0.75| 0.56
R2L precision| 0.31| 1.00
R2L recall| 0.94| 0.94

The Random Forest model achieved higher overall accuracy and substantially improved precision for minority attack classes. However, its baseline U2R recall was lower than that of Logistic Regression, illustrating the trade-off between prediction reliability and attack detection sensitivity.

Decision-threshold exploration

The project investigates custom thresholds of 0.2, 0.3, 0.4, and 0.5 for U2R predictions.

The saved classification report for a threshold of 0.2 shows U2R precision and recall of 0.75 each, compared with baseline values of 0.90 precision and 0.56 recall.

The threshold comparison table contains different figures and should be reconciled with the classification reports before the tuned results are finalised.

Limitations

- The U2R class is extremely rare, with only 52 instances in the dataset before the train-test split.
- The saved test set contains only 16 U2R instances, so a small number of predictions can substantially affect the reported metrics.
- The results are based on a single stratified train-test split.
- NSL-KDD is a benchmark dataset, and performance on it does not guarantee equivalent performance in real-world network environments.
- The threshold-selection process should be validated on separate data before the final model is evaluated on an untouched test set.

Tools and Libraries

- Python
- pandas
- NumPy
- scikit-learn
- Matplotlib
- Seaborn
- Jupyter Notebook

Project File

- "Portfolio for Project 2 - Suspicious Login Detection - Multi-Class Intrusion Detection.ipynb" — notebook containing data preparation, model training, evaluation, comparison, and threshold exploration.

Conclusion

This project demonstrates the importance of class-specific evaluation in intrusion detection and explores how model choice and decision thresholds affect the detection of rare attacks. It provides a foundation for further work on imbalanced classification and cybersecurity analytics.

This is an educational portfolio project, not a production-ready intrusion detection system.
