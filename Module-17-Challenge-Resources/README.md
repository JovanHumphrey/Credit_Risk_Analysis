# Credit_Risk_Analysis

## Project Overview

<p>Credit risk is an inherently unbalanced classification problem, as good loans easily outnumber risky loans. Different techniques are employed to train and evaluate models with unbalanced classes. In this project I used imbalanced-learn and scikit-learn libraries to build and evaluate models using resampling.</p>

<p>Using the credit card credit dataset from LendingClub, I oversampled the data using the RandomOverSampler and SMOTE algorithms, and undersampled the data using the ClusterCentroids algorithm. Then, I used a combinatorial approach of over and undersampling using the SMOTEENN algorithm. Lastly I compared two machine learning models that reduce bias, BalancedRandomForestClassifier and EasyEnsembleClassifier, to predict credit risk.</p>

<p>Once the data was loaded into Jupyter Notebook I removed rows with issued loans, and then converted interest rates to numerical value. Once that conversion was done I created a definition for low and high-risk. Any loan with 'Late (31-120 days)', 'Late (16-30 days)', 'Default', or 'In Grace Period' was defined as high-risk. Any loan listed as 'Current' was defined as low-risk. Everything else was dropped from the results. Lastly, I split the data into Training and Testing. Below are the results.</p>

![value counts](https://github.com/JovanHumphrey/Credit_Risk_Analysis/blob/main/Module-17-Challenge-Resources/images/resample_value_counts.JPG)

<p.With that out of the way I was able to get to work. I tested the dataset using the six models listed above.</p>

## Evaluation

### Oversampling
<p>Random oversampling involves randomly selecting examples from the minority class, with replacement, and adding them to the training dataset. The results of this model classified 51366 records for both high- and low-risk.
![naive oversampling](https://github.com/JovanHumphrey/Credit_Risk_Analysis/blob/main/Module-17-Challenge-Resources/images/resample_naive_classification_report_imbalanced.JPG)

### SMOTE
<p> SMOTE works by selecting examples that are close in the feature, drawing a line between the examples in the feature and drawing a new sample at a point along that line. The results of this model also classified 51366 records for both high- and low-risk.</p>

![SMOTE model](https://github.com/JovanHumphrey/Credit_Risk_Analysis/blob/main/Module-17-Challenge-Resources/images/resample__SMOTE_classification_report_imbalanced.JPG)

### Undersampling
<p> While undersampling introduces bias by deleting data, oversampling creates bias by duplicating samples from the minority class. The results of this model classified 246 records for both high- and low-risk</p>

![undersampling](https://github.com/JovanHumphrey/Credit_Risk_Analysis/blob/main/Module-17-Challenge-Resources/images/resample_undersampling_classification_report_imbalanced.JPG)

### Combination (Over and Under) Sampling
<p>Here I used a combination of over – and undersampling. The results of this model classified 68,458 records for high-risk and 62,022 for low-risk.</p>

![combination](https://github.com/JovanHumphrey/Credit_Risk_Analysis/blob/main/Module-17-Challenge-Resources/images/resample_combination_classification_report_imbalanced.JPG)

### Balanced Random Forest Classifier
<p>Using BalancedRandomForestClassifier I resampled the data. A balanced random forest randomly under-samples each bootstrap sample to balance it.</p>

![balanced](https://github.com/JovanHumphrey/Credit_Risk_Analysis/blob/main/Module-17-Challenge-Resources/images/ensemble_balance_random_forest_classifier_classification_report_imbalanced.JPG)

### Easy Ensemble Classifier
<p>Using EasyEnsembleClassifier I resampled the data. The Easy Ensemble involves creating balanced samples of the training dataset by selecting all examples from the minority class and a subset from the majority class.</p>

![ensemble](https://github.com/JovanHumphrey/Credit_Risk_Analysis/blob/main/Module-17-Challenge-Resources/images/ensemble_easy_ensemble_adaboost_classifier_classification_report_imbalanced.JPG)

### Summary

The six models have a variety of outcomes. Below is the ranking of most accurate to least using the results of the high-risk category:

•	EasyEnsembleClassifier: 93% accuracy, 8% precision, 92% recall and 15% F1 Score
•	BalancedRandomForestClassifier: 74% accuracy, 3% precision, 62% recall and 6% F1 Score
•	SMOTE: 66% accuracy, 1% precision, 63% recall and 2% F1 Score
•	SMOTEEN: % accuracy, 66% precision, 73% recall and 2% F1 Score
•	RandomOverSampler: 64% accuracy, 1% precision, 71% recall and 2% F1 Score
•	ClusterCentroids: 52% accuracy, 1% precision, 69% recall and 1% F1 Score


### Recommendation

The best results came from the Easy Ensemble Classifier with a recall of 94% for low-risk, and 92% recall for high-risk. The results of this model far outrank the results of the five others. My recommendation is that future analysis be done with this model.