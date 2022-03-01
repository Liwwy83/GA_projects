# CAPSTONE - Grade Predictions for A Level H2 Math

---
# Introduction
Grade predictions are important for students who wish to apply for overseas universities and/or scholarships in the cycle before their actual A level grades are available.

---
# Problem Statement
Grade prediction is an ordinal classification problem where classes have inherent ranking, i.e. A is better than B. We narrow our scope down to the subject of H2 Mathematics, which is one of the most common subjects taken by students at A levels in Singapore, and has an additional challenge of being imbalanced (a large majority is grade A while a small number is a failure grade of S or U).

We have 3 objectives in this project, and we met the first 2 objectives.

## Objective 1
Evaluate the effectiveness of a benchmark method using only Prelim marks and past years' results that does not involve machine learning.

The [benchmark](1_Benchmark.ipynb) method was found to be highly effective, with weighted kappa scores between 0.7 and 0.8, which is similar to what our best model could achieve. In addition, most of the 62 features created in our [Data Cleaning and EDA](2_Data_Cleaning_and_EDA.ipynb) notebook end up not being used, with Prelim marks being a very strong predictor by itself.

We highly recommend schools to implement this method systematically so that teachers need not look through each and every one of their dozens of students exam results to give a prediction. This will lighten the teachers' workload and the whole cohort will be given fairer predictions that do not depend on individual teachers' biases. The school could then give teachers the option of modifying the predicted grade manually if they desire.

## Objective 2
Sieve out factors that help predict use them to generate better predictions, so that the potentially high-achieving students can be given better predicted grades to boost their university and/or scholarship applications.

Our model achieves the aim of giving better predicted grades than the benchmark method as a higher proportion of students ended up with predicted grade better than actual grade.

In addition, we found that students who take H2 Chemistry have a higher chance of getting 'A' compared to students who do not, and similarly male students have higher chance of getting 'A' compared to female students if all other features are held constant. For students at the boundary of grade 'A' and grade 'B', we recommend that teachers focus more on the female students who do not take H2 Chemistry to help push her to an 'A' grade for Math A level.

## Objective 3
Reduce the number of students in the watchlist so that teachers can focus more attention on the true potential weak performers.

This objective was not met. Even though our final model only put 25 students on the watchlist compared to the benchmark method for batch 20 that highlighted 35 students, it did not capture 100% of the students in the lowest grade category.

---
# Tools for Evaluation
We evaluate the predictions on the following:

## Weighted Cohen's Kappa Score
The weighted Cohen's kappa score (weighted kappa) is particularly suitable here as it accounts for the ordinal ranking between classes, where a prediction that is 2 grades away is penalized more heavily than a prediction that is just 1 grade away. This will be the main metric that we will be attempting to maximize when modelling.

## Recall Scores
We look at the recall scores for the lowest grade category and aim for 100% recall rate as these are the students we wish to identify correctly to provide intervention measures. For a summarised recall score, we use the macro average as we do not want the results to be pulled up by the majority class of grade A.

## Confusion Matrix
The confusion matrix shows where the wrong predictions are. We will compare the number of predictions that are within 1 grade, 2 or more grades away, better than actual and worse than actual when comparing our machine learning model(s) against the benchmark method.

---
# Data Source and Confidentiality
3 years of data is provided by a school in Singapore with actual A level grades for H2 Mathematics. Batch 18 and batch 19 have actual A level results provided at the beginning of the project in Jan 2022, while the results of batch 20 was not available then and only released near the end of this project on 22 Feb 2022. We will use batch 18 and batch 19 data to create and evaluate our models before finally testing the predictions on batch 20.

We asked for data related to results as well as other data not directly related to academic results such as Co-Curricular Activities (CCA) and Community Involvement Projects (CIP).

While the project was carried out on the full dataset, due to confidentiality issues, this cannot be shared in public. Instead, we share a modified dataset, where some entries have been renamed where possible and some columns have been removed. For example, the data on CCA/CIP cannot be disclosed as the entries contain names of clubs or activities that are unique to the school. In addition, the number of rows of data is cut to the first 500 rows for sharing. Some numerical results are also redacted to prevent the data from being traced back to the school.

Nonetheless, the python notebooks shared here should provide sufficient information on the thought processes and results, so that anyone who wishes to carry out a similar project on their own school data may do so.

---
# Target Distribution
![](../assets/target_distribution.png)
The grade distribution for actual A level results are similar across both years, indicating stability across batches, hence it is reasonable to build a model to make predictions for future batches as well.

---
# Model Results vs Benchmark Scores
The best results were achieved using Logistic Regression with just the top 3 features of Math Prelim marks, Math C1 marks and Prelim overall points. The results are comparable to benchmark but unfortunately did not achieve 100% recall for ESU. This may be purely by chance and the benchmark method may meet the same issue if carried out on other batches, as we only have limited data on 3 batches.

|Batch|Model|Weighted Cohen's Kappa|Recall for ESU|Macro Average Recall|Number Predicted as ESU|
|---|---|---|---|---|---|
|18|Logistic Regression|0.7681|1.0|0.5431|36|
|18|Benchmark|0.7581|1.0|0.5729|19|
|19|Logistic Regression|0.7130|1.0|0.5150|24|
|19|Benchmark|0.7204|1.0|0.5099|38|
|20|Logistic Regression|0.7876|0.8235|0.5216|25|
|20|Benchmark|0.7768|1.0|0.5482|35|

The Logistic Regression models do better than the benchmarks at predicting grades correctly and are more optimistic as more of the predictions end up better than the actual grade.
|Batch|Model|Correct Predictions|Within 1 Grade|2 or More Grades Away|Better Than Actual|Worse Than Actual|
|---|---|---|---|---|---|---|
|18|Logistic Regression|82.3%|97.0%|3.0%|9.9%|7.7%|
|18|Benchmark|81.0%|97.5%|2.5%|9.1%|9.9%|
|19|Logistic Regression|78.4%|96.6%|3.4%|12.0%|9.6%|
|19|Benchmark|77.6%|95.9%|4.1%|10.3%|12.1%|
|20|Logistic Regression|80.4%|97.3%|2.7%|12.4%|7.1%|
|20|Benchmark|80.7%|97.3%|2.7%|10.1%|9.1%|

---
