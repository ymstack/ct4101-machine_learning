# Reflective Changelog

## Milestone 1 – Planning the project

At the beginning of this project the main idea was to see whether it was possible to predict a student's final Maths grade without knowing their previous grades.

I decided to use the UCI Student Performance dataset and focus specifically on Mathematics. Excluding G1 and G2 made the problem more challenging but it also made the research question more interesting as the models would have to rely on other information about the students.

The initial plan was to establish a simple baseline and compare it against three different regression models.

## Milestone 2 – Preparing the data

For the second milestone the focus was on understanding the dataset and getting everything ready before introducing the machine learning models.

The dataset contained 395 records with no missing values or duplicate rows. The numerical and categorical variables needed to be handled differently, and the data was split into training and testing sets.

A simple mean baseline was introduced which gave a test MAE of 3.6459. This gave me something to compare the other models against rather than looking at their results in isolation.

## Milestone 3 – Comparing the models

This is where the project started to come together. Linear Regression, Decision Tree and Random Forest were introduced and compared using five fold cross validation.

Random Forest performed the best overall with a test MAE of 3.0899. Although this was an improvement of around 15% over the baseline the individual predictions showed that the model was far from perfect.

The model performed considerably better on students with average grades than students at either end of the grading scale. This became an important part of the final analysis.

## Milestone 4 – Finalising the project

For the final milestone the focus is on bringing everything together rather than introducing more models or changing the experiment.

The notebook has been checked again to make sure the results are reproducible. I've also added the model card, expanded the dataset documentation and completed the final report.

The results show that there is some predictive value in the student characteristics but not enough to justify using the model to make decisions about students in a real educational setting.

## Final reflection

The main takeaway from this project is that having the best performing model doesn't necessarily mean having a good enough model for the problem you're trying to solve.

If I were to continue working on this project, I would focus more on understanding why certain predictions are so inaccurate which features influence the results and whether the model performs differently across groups of students. I think this would be more valuable than simply trying to reduce the overall error by introducing more models.
