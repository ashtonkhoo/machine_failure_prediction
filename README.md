# Table of contents

- [Project Title](#project-title)
- [Problem Statement](#problem-statement)
- [Dataset](#dataset)
- [Model Architecture](#model-architecture)
- [Training & Testing Workflow](#training--testing-workflow)
- [Results](#results)

# Project Title
Binary Classification of Machine Failures

# Problem Statement
This project is part of the 2023 edition of Kaggle's Playground Series, which aims to provide the community with a diverse range of moderately challenging tasks, carefully designed to facilitate skill enhancement in various facets of machine learning and data science. In this project, we will be aiming to predict the probability of machine failures.

# Dataset
The dataset is a csv file of roughly 7.2 MB, with 14 attributes and 136k instances. It contains a mix of numerical, categorical, and boolean variables.
There were no missing values in this dataset, which made this dataset simple. However, it was also found that the target classes were imbalanced. 
## Source: Kaggle. 2023. "Binary Classification of Machine Failures", version 1. Retrieved 15/06/2023 from https://www.kaggle.com/competitions/playground-series-s3e17/data.

# Model Architecture
XGBoost, or Extreme Gradient Boosting, is a machine learning library that employs gradient-boosted decision trees (GBDT) and can be scaled and distributed. It supports parallel tree boosting and is considered the dominant library for tackling regression, classification, and ranking problems.

I decided to use XGBoost to implement my solution because I was interested in experimenting with this powerful machine learning library and exploring its various hyperparameters. As XGBoost is known for its scalability, distributed computing capabilities, and strong performance in regression, classification, and ranking problems, it seemed like an ideal choice for my project. Additionally, by exploring its hyperparameters, I hoped to fine-tune the model and achieve the best possible performance for my particular use case.

# Training & Testing Workflow
The project workflow began with loading the dataset into a pandas dataframe and conducting exploratory data analysis to assess the presence of null values, duplicates, and obtain preliminary statistics about the data. A correlation matrix was then calculated to identify any correlated features. Since the selected algorithm, XGBoost, cannot handle categorical values, categorical features were encoded to numerical values. The distribution of label classes was examined, and the presence of class imbalance was discovered. To address this, ADASYN was implemented to oversample the minority class. The dataset was then split into training and testing sets using a 75/25 split. The XGBoost classifier was trained on the training set with initial parameters and used to make predictions on the test set. 

# Results 
The Area under the Receiver-Operator Curve (ROC-AUC) score was calculated by comparing the predicted and actual test set labels, resulting in an AUC score of 0.94. Hyperparameter tuning was then performed using Random Search on a candidate parameter grid, with a 5-fold cross-validation for 100 iterations, producing an improvement of performance to an AUC of 0.96.

The best model achieved a Public Leaderboard Score of 0.96497, and a Private Leaderboard Score of 0.97128, which ultimately placed me in the Top 38.5% of 1,502 teams.
![image](https://github.com/ashtonkhoo/machine_failure_prediction/assets/54165058/089ececf-5ce0-4afd-a4c3-df5ba27db37c)
