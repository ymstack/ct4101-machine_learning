# CT4101 Machine Learning Portfolio Project — Project Context

## 1. Project Overview

This repository contains my final CT4101 Machine Learning Portfolio Project.

The project is a focused machine learning investigation using the **UCI Student Performance dataset**, specifically the Mathematics dataset:

`student-mat.csv`

The aim is to demonstrate a complete and sensible machine learning workflow rather than simply trying to achieve the highest possible prediction accuracy.

The project should prioritise:

* Correct methodology
* Clear reasoning
* Reproducibility
* Appropriate model selection
* Fair evaluation
* Interpretation of results
* Error analysis
* Responsible use of machine learning
* Clear communication

The implementation should remain reasonably simple and beginner-friendly so that I can understand and explain all of the code, decisions and results myself.

---

# 2. Research Question

The main research question is:

> **Can machine learning predict a student's final Mathematics grade using demographic, social and educational characteristics available before the final grade is known?**

This is a **regression** problem because the target is a numerical grade from 0 to 20.

---

# 3. Dataset

The project uses the:

**UCI Student Performance Dataset**

Source:

UCI Machine Learning Repository
Student Performance
https://archive.ics.uci.edu/dataset/320/student+performance

The project uses:

`student-mat.csv`

This represents student performance in Mathematics.

The dataset contains information about students':

* Demographics
* Family background
* School information
* Study habits
* Educational support
* Social activities
* Absences
* Previous academic performance

The final grade is represented by:

`G3`

`G3` is the final Mathematics grade and ranges from 0 to 20.

The dataset also contains:

* `G1` — first period grade
* `G2` — second period grade

---

# 4. Important Feature Decision

`G1` and `G2` will **NOT** be used as predictor variables.

This is an important project decision.

The purpose of the project is to investigate whether student characteristics available before the final grade can provide useful predictions.

Using `G1` and `G2` would make the prediction task much easier because these grades are previous academic results and are strongly correlated with `G3`.

Therefore:

### Target

`G3`

### Predictors

The first 30 demographic, social and educational variables.

### Excluded

`G1`
`G2`

This decision should be clearly explained in the report because it is an important methodological choice.

---

# 5. Type of Machine Learning Problem

This project is:

**Supervised learning → Regression**

The model receives information about a student and attempts to predict their final Mathematics grade.

Example:

```text
Student characteristics
        ↓
Machine Learning Model
        ↓
Predicted final grade
```

The prediction will be compared against the student's actual `G3` grade.

---

# 6. Planned Machine Learning Workflow

The project will follow a standard machine learning workflow.

## Step 1 — Understand the problem

Define the research question and explain why predicting student performance is an interesting machine learning problem.

---

## Step 2 — Understand the dataset

Investigate:

* Number of records
* Number of variables
* Data types
* Numerical variables
* Categorical variables
* Target variable
* Missing values
* Duplicate rows
* Possible unusual values/outliers
* Distribution of the target

The dataset should be explored before modelling.

---

## Step 3 — Data preparation

The dataset contains both numerical and categorical variables.

Categorical variables will need to be converted into a suitable numerical representation before they can be used by the machine learning models.

The preprocessing approach should be implemented using appropriate scikit-learn tools such as:

* `ColumnTransformer`
* `OneHotEncoder`
* `Pipeline`

The preprocessing must be fitted using the training data rather than leaking information from the test set.

---

# 7. Train/Test Evaluation

The dataset will be divided into:

* Training data
* Testing data

The training data will be used to train the models.

The test data will be kept separate and used for final evaluation.

The test set must not be used to make modelling or tuning decisions.

The project should use a reproducible random state so that results can be reproduced.

---

# 8. Baseline Model

A baseline model will be included before the machine learning models.

The planned baseline is:

**DummyRegressor**

This provides a simple reference point.

The learned models should be compared against this baseline.

If a machine learning model does not perform meaningfully better than the baseline, that is an important finding rather than something to hide.

---

# 9. Planned Machine Learning Models

The project will compare a small number of suitable regression models.

## Model 1 — Linear Regression

`LinearRegression`

This provides a simple and interpretable model.

It can help establish whether there are useful approximately linear relationships between the student characteristics and final grade.

---

## Model 2 — Decision Tree Regressor

`DecisionTreeRegressor`

This can model non-linear relationships and interactions between variables.

It is also relatively easy to explain.

---

## Model 3 — Random Forest Regressor

`RandomForestRegressor`

This combines multiple decision trees and can model more complex relationships than a single decision tree.

It can also provide feature importance information that can be used as part of the interpretation.

---

# 10. Evaluation Metrics

The main evaluation metrics will be:

## MAE — Mean Absolute Error

Measures the average absolute difference between the predicted and actual grades.

It is useful because it can be interpreted in terms of grade points.

For example, an MAE of approximately 1.5 would mean predictions are, on average, about 1.5 grade points away from the actual grade.

---

## RMSE — Root Mean Squared Error

RMSE measures prediction error while giving larger errors more weight.

This is useful for identifying whether the model makes some particularly large mistakes.

---

## R² — R-squared

R² indicates how much variation in the target is explained by the model relative to a baseline.

R² should not be interpreted on its own.

---

# 11. Model Comparison

The models will be compared using the same test data and the same evaluation metrics.

A results table will be created containing something similar to:

| Model             | MAE | RMSE | R² |
| ----------------- | --: | ---: | -: |
| Dummy Regressor   |     |      |    |
| Linear Regression |     |      |    |
| Decision Tree     |     |      |    |
| Random Forest     |     |      |    |

The actual values must come from running the models.

No results should ever be invented.

The project should focus on explaining **why** the models performed differently rather than simply identifying the model with the lowest error.

---

# 12. Planned Visualisations

The project should contain useful visualisations rather than excessive graphs.

Planned visualisations include:

### Target Distribution

A plot showing the distribution of `G3`.

This helps understand the target before modelling.

### Actual vs Predicted Grades

A plot comparing actual `G3` values with model predictions.

This helps show how close the predictions are.

### Residual/Error Plot

A plot showing prediction errors.

This can help identify patterns or situations where the model performs poorly.

### Feature Importance

For the Random Forest model, feature importance can be examined to identify which variables contributed most strongly to predictions.

Feature importance should be treated as an interpretation tool, not proof that a variable causes student performance.

---

# 13. Error Analysis

The project will not stop at reporting MAE, RMSE and R².

Prediction errors will also be investigated.

Examples of questions to consider:

* Which students were predicted particularly inaccurately?
* Are large errors concentrated around certain grade ranges?
* Does the model struggle with very high or very low grades?
* Are there patterns in the residuals?
* Does the dataset contain characteristics that the models cannot capture well?

This section is important because it demonstrates critical analysis rather than simply reporting model scores.

---

# 14. Responsible Machine Learning

The project involves predicting student academic performance, so responsible ML considerations are important.

Areas to discuss include:

## Privacy

Student data can contain personal or sensitive information.

A real-world system should not expose individual student information unnecessarily.

---

## Fairness

Some variables relate to demographic and social characteristics.

A model could potentially produce systematically different errors for different groups.

The project should acknowledge this possibility and avoid presenting the model as automatically fair.

---

## Misuse

A prediction of academic performance should not automatically be treated as a definitive judgement about a student's ability or future.

Predictions are estimates and contain uncertainty.

A model should not be used as the sole basis for important decisions about students.

---

## Generalisation

The dataset comes from Portuguese secondary schools.

Therefore, results from this dataset may not generalise directly to:

* Other schools
* Other countries
* Different education systems
* Different age groups
* Current students

This limitation must be clearly acknowledged.

---

# 15. Limitations

The final report should discuss limitations such as:

* Relatively small dataset
* Data from a specific educational context
* Potential sampling limitations
* Limited ability of the available variables to capture all factors affecting academic performance
* Exclusion of previous grades `G1` and `G2`
* Model predictions are estimates rather than guarantees
* Results may not generalise to other populations

The limitations should be discussed honestly rather than hidden.

---

# 16. CT4101 Assessment Requirements

The project should address the main CT4101 assessment areas:

### Problem and Data Understanding

Clearly define the problem, research question and dataset.

### Data Preparation and Methodology

Demonstrate appropriate preprocessing and a valid evaluation strategy.

### Modelling and Comparison

Compare a baseline with multiple suitable machine learning models.

### Evaluation and Critical Analysis

Use appropriate metrics, visualisations and error analysis.

### Responsible ML and Limitations

Discuss privacy, fairness, misuse and generalisation.

### Communication and Understanding

The final code, report and presentation should be clear enough that I can explain the decisions and results myself.

---

# 17. Project Milestones

## Milestone 1 — Proposal

The proposal should include:

* Project title
* Research question
* Dataset and source
* Dataset licence/citation
* Target variable
* Candidate features
* Data-quality considerations
* Baseline
* Planned models
* Evaluation metrics
* Short responsible ML discussion
* Repository link

---

## Milestone 2 — Initial Implementation

By this stage the repository should contain:

* Working notebook/code
* README
* Environment/requirements file
* Data audit
* Data preparation
* Evaluation design
* Baseline model
* Assistance declaration

---

## Milestone 3 — Model Comparison

The project should contain:

* Baseline
* At least two learned models
* Model settings
* Any justified tuning
* Visualisation
* Error/residual analysis
* Draft conclusion
* Updated assistance declaration

---

## Milestone 4 — Final Submission

The final project should contain:

* Complete reproducible code
* Final report
* README
* Environment file
* Dataset/data instructions
* Results
* Visualisations
* Error analysis
* Responsible ML discussion
* Limitations
* 5-minute demonstration video
* GitHub repository
* AI/coding-assistant assistance declaration

---

# 18. Repository Structure

The intended repository structure is:

```text
ct4101-machine_learning/
│
├── data/
│   ├── student-mat.csv
│   └── README.md
│
├── notebooks/
│   └── student_performance_ml.ipynb
│
├── src/
│
├── reports/
│
├── README.md
├── PROJECT_CONTEXT.md
├── requirements.txt
└── .gitignore
```

The structure can be changed if there is a good reason, but unnecessary complexity should be avoided.

---

# 19. Coding Style

All code should follow these principles:

* Beginner-friendly
* Clear
* Reproducible
* Simple
* Well organised
* Easy to explain
* No unnecessary abstraction
* No unnecessary libraries
* No overly complicated architecture

Comments should explain important decisions rather than describing every obvious line.

Do not generate code that I cannot reasonably understand or explain.

---

# 20. Use of GitHub Copilot / Generative AI

GitHub Copilot and other generative AI tools may be used during development.

However, I must understand the submitted code and be able to explain:

* What the code does
* Why preprocessing was used
* Why the models were selected
* Why the evaluation metrics were selected
* How the train/test split works
* What the results mean
* What the limitations are

AI assistance must be declared according to the CT4101 assessment requirements.

Copilot must not fabricate results, sources, dataset information or experimental findings.

---

# 21. Important Rules for This Project

1. Do not use `G1` or `G2` as predictors.
2. Do not merge the Mathematics and Portuguese datasets.
3. Do not invent results.
4. Do not invent sources or citations.
5. Do not tune models using the final test set.
6. Do not claim a model is better without comparing the actual evaluation results.
7. Keep the methodology simple and defensible.
8. Prioritise understanding over complexity.
9. Explain important methodological decisions.
10. Keep the project reproducible.
11. Keep the final conclusions supported by the actual experimental evidence.
12. Do not add unnecessary machine learning models just to make the project look more complicated.

---

# 22. Overall Project Goal

The final project should tell a clear story:

```text
Real-world question
        ↓
Understand the dataset
        ↓
Prepare the data correctly
        ↓
Create a fair evaluation strategy
        ↓
Establish a simple baseline
        ↓
Train several suitable models
        ↓
Compare their performance
        ↓
Investigate prediction errors
        ↓
Interpret the results
        ↓
Discuss limitations and responsible ML
        ↓
Reach evidence-based conclusions
```

The goal is not simply to produce the most accurate model.

The goal is to demonstrate that I can carry out and explain a complete machine learning investigation from start to finish.
