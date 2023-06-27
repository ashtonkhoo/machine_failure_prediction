# Table of contents

- [Project Title](#project-title)
- [Problem Statement](#problem-statement)
- [Dataset](#dataset)
- [Training & Testing Workflow](#training--testing-workflow)
- [Model Architecture](#model-architecture)
- [Results](#results)

# Project Title
Binary Classification of Machine Failures

# Problem Statement
This project is part of the 2023 edition of Kaggle's Playground Series, which aims to provide the community with a diverse range of moderately challenging tasks, carefully designed to facilitate skill enhancement in various facets of machine learning and data science. In this project, we will be aiming to predict the probability of machine failures.

# Dataset
The dataset is a csv file of roughly 7.2 MB, with 14 attributes and 136k instances. It contains a mix of numerical, categorical, and boolean variables.
## Source: Kaggle. 2023. "Binary Classification of Machine Failures", version 1. Retrieved 15/06/2023 from https://www.kaggle.com/competitions/playground-series-s3e17/data.

I also incorporated the original data set used to generate this synthetic dataset, in an effort to try to improve model performance.
## Source: DineshManikanta. 2022. "Machine Failure Predictions", version 1. Retrieved 15/06/2023 from https://www.kaggle.com/datasets/dineshmanikanta/machine-failure-predictions.

# Training & Testing Workflow
The project workflow began with loading the dataset into a Pandas dataframe and conducting some simple exploratory data analysis to assess the presence of null values, duplicates, and obtain preliminary statistics about the data. A correlation matrix was then calculated to identify any correlated features. The dataset was then split into training and testing sets using a 80/20 split. 

# Model Architecture
After hours of testing individual models and submitting the results to the Kaggle leaderboard, I eventually ended up creating an ensemble model of the 4 best models I found from my experiments, which were XGBoost, LightGBM, Balanced Random Forest, and Histogram-based Gradient Boosting Classification Tree. 

For each of the models, I first set up isolated experiments using the Optuna library to find the best set of hyperparameters which would maximize the Area under the Receiver-Operator Curve (ROC-AUC) score.
I then combined these models using the Voting Classifier with soft voting, as submissions for this competition were evaluated on AUC score between the predicted probability and the observed target.

# Results 
The AUC score for the ensemble model was calculated by comparing the predicted and actual test set labels, resulting in an AUC score of 0.97. 

The best model achieved a Public Leaderboard Score of 0.96497, and a Private Leaderboard Score of 0.97128, which ultimately placed me in the Top 38.5% of 1,502 teams.
![image](https://github.com/ashtonkhoo/machine_failure_prediction/assets/54165058/089ececf-5ce0-4afd-a4c3-df5ba27db37c)
