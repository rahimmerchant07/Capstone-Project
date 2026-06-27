# Using Machine Learning for Early Identification of Non-Optimal Manufacturing Conditions

Rahim Merchant

# Exectutive Summary

Manufacturing facilities collect large amounts of operating data every day, but that information is not always used to identify potential equipment issues before they lead to failures. From a reliability engineering perspective, being able to recognize changes in machine operating conditions early can help reduce unplanned downtime, improve maintenance planning, and support reliable production

The purpose of this project was to determine whether machine learning could be used to predict non-optimal manufacturing operating conditions using machine and process-related variables. Several classification models were developed and compared, including Logistic Regression, K-Nearest Neighbours (KNN), Decision Tree, and Random Forest. Cross-validation and Grid Search were also used to improve model performance and compare the models more fairly.

The results showed that tree-based models performed better than Logistic Regression and KNN when identifying non-optimal operating conditions. After hyperparameter tuning, the Decision Tree model produced the best overall balance between detecting failures and maintaining strong predictive performance. Feature importance analysis also showed that torque, rotational speed, and tool wear were the strongest indicators of non-optimal operating conditions.

Overall, this project demonstrates that machine learning can support reliability and maintenance teams by helping identify potential operating issues before equipment failures occur. These insights could be used to improve maintenance planning, reduce unexpected downtime, and support more informed decision-making.

# Rationale

Equipment reliability has a direct impact on production, maintenance costs, and overall plant performance. When machines begin operating outside of their normal conditions, the risk of equipment failure and unplanned downtime increases. Identifying these changes early gives maintenance and operations teams the opportunity to investigate potential issues before they become larger problems.

As a Corporate Reliability Engineer, I work with maintenance strategies, asset performance, and continuous improvement initiatives across manufacturing facilities. This project allowed me to apply the machine learning concepts learned throughout this program to a problem that closely relates to my professional experience.

Predicting non-optimal operating conditions has practical value because it can help organizations move from reactive maintenance toward a more proactive approach. Rather than waiting for equipment to fail, maintenance teams can use operating data to identify developing issues, prioritize inspections, and make better-informed maintenance decisions.

The goal of this project was not to replace the knowledge of maintenance or operations personnel, but to demonstrate how machine learning can be used as a decision-support tool to improve equipment reliability and reduce the likelihood of unexpected failures.


# Research Question

Can machine learning be used to predict whether manufacturing operating conditions are optimal or non-optimal based on machine and process-related variables?

# Data Sources

The dataset used for this project was the AI4I 2020 Predictive Maintenance Dataset, which is publicly available on Kaggle. It was selected because it closely represents the types of machine and process data commonly collected in manufacturing environments and is well suited for predictive maintenance and reliability applications.

The dataset contains 10,000 machine observations with 14 original variables, including air temperature, process temperature, rotational speed, torque, tool wear, machine type, and machine failure status. These variables describe the operating condition of each machine and were used to train and evaluate the machine learning models.

The target variable for this project was Machine Failure, where:

0 = Optimal operating condition
1 = Non-optimal operating condition

The datset can be found here:
https://www.kaggle.com/datasets/stephanmatzka/predictive-maintenance-dataset-ai4i-2020

# Methodology

The project followed a structured machine learning workflow, beginning with data exploration and preparation before model development.

The dataset was first reviewed to understand the available variables, check for missing values, and examine the distribution of the target variable. Columns that did not contribute meaningful predictive value, such as the unique identifier, product ID, and individual failure mode columns, were removed from the dataset. Machine type was converted into numerical features using one-hot encoding so it could be used by the classification models.

The data was then separated into predictor variables and the target variable (Machine Failure). An 80/20 train-test split was used to evaluate model performance on unseen data. Feature scaling using StandardScaler was applied for Logistic Regression and K-Nearest Neighbours because these models are sensitive to differences in feature magnitude. Decision Tree and Random Forest models were trained using the original feature values since tree-based models do not require feature scaling.

Four classification models were developed and compared:

Logistic Regression
K-Nearest Neighbours (KNN)
Decision Tree
Random Forest

Model performance was evaluated using Accuracy, Recall, F1-score, and Confusion Matrices. Since the dataset contained significantly fewer failure observations than normal operating conditions, Recall and F1-score were considered the most important metrics for comparing model performance.

To improve model performance, cross-validation was performed to evaluate model stability across multiple data splits. Grid Search was then used to identify the best hyperparameters for the K-Nearest Neighbours, Decision Tree, and Random Forest models before comparing the final tuned models.

# Results

Four classification models were developed and evaluated to determine their ability to identify non-optimal manufacturing operating conditions. While all four models achieved high overall accuracy, their performance differed when identifying failure conditions.

| Model | Accuracy | Failure Recall | Failure F1 Score |
|:------|---------:|---------------:|-----------------:|
| Logistic Regression | 96.75% | 0.10 | 0.18 |
| K-Nearest Neighbours | 97.40% | 0.29 | 0.43 |
| Decision Tree | 97.80% | 0.66 | 0.67 |
| Random Forest | 98.15% | 0.53 | 0.66 |

Although Random Forest achieved the highest overall accuracy, the Decision Tree model was more effective at identifying non-optimal operating conditions. This is an important consideration because correctly detecting potential failures is more valuable than simply achieving a high accuracy score on an imbalanced dataset.

After hyperparameter tuning using Grid Search, the Decision Tree model produced the strongest overall performance.

| Tuned Model | Failure Recall | Failure F1 Score |
|:------------|---------------:|-----------------:|
| K-Nearest Neighbours | 0.31 | 0.42 |
| Decision Tree | 0.69 | 0.76 |
| Random Forest | 0.59 | 0.70 |

The tuned Decision Tree correctly identified 47 of the 68 failure observations in the test dataset and achieved the highest F1-score for the failure class. Based on these results, it was selected as the best-performing model for this project.

Feature importance analysis showed that torque, rotational speed, and tool wear were the most influential variables when predicting non-optimal operating conditions. These findings are consistent with manufacturing reliability principles, where changes in mechanical loading, equipment speed, and tool condition are often early indicators of developing equipment issues.

Overall, the results demonstrate that machine learning can successfully support the identification of non-optimal manufacturing operating conditions and could be used to assist reliability and maintenance teams in making more proactive maintenance decisions.

# Next Steps

This project demonstrated that machine learning can successfully predict non-optimal manufacturing operating conditions using machine and process-related variables. While the results were encouraging, there are several opportunities to build on this work.

The first priority would be to validate the model using real manufacturing data collected from an operating facility. Although the AI4I 2020 dataset is well suited for learning and model development, testing the model on real production equipment would provide greater confidence in its practical application.

Future work could also include collecting additional failure data to reduce the class imbalance within the dataset. A larger number of failure examples would allow the models to learn more patterns associated with non-optimal operating conditions and could improve predictive performance.

Additional process variables and sensor data, such as vibration, pressure, or energy consumption, could also be incorporated to provide a more complete representation of equipment health.

Finally, the model could be integrated into a predictive maintenance workflow where reliability and maintenance teams receive early warnings when operating conditions begin moving away from normal ranges. This would allow maintenance activities to be planned before equipment failures occur, helping reduce unplanned downtime and improve overall equipment reliability.

## Outline of Project

- https://github.com/rahimmerchant07/Capstone-Project/blob/main/Capstone%20Initial%20Report%20%26%20EDA.ipynb
-

## Contact and Further Information

Author: Rahim Merchant
rahim.merchant07@gmail.com



  




