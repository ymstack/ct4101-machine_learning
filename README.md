# CT4101 Machine Learning Portfolio Project

## Research question

> Can machine learning predict a student's final Mathematics grade using demographic, social and educational characteristics available before the final grade is known?

This is a supervised **regression** project. The objective is to build a simple, reproducible workflow and critically examine how useful these characteristics are for predicting final Mathematics grades.

## Dataset

The project uses the Mathematics file, `student-mat.csv`, from the [UCI Machine Learning Repository Student Performance dataset](https://archive.ics.uci.edu/dataset/320/student+performance). The original dataset is cited as Cortez (2008), *Student Performance*, and is available under the CC BY 4.0 licence. Dataset details are documented in [data/README.md](data/README.md).

## Target and predictors

- Target: `G3`, the final Mathematics grade from 0 to 20.
- Candidate predictors: the first 30 demographic, social and educational variables.
- Excluded: `G1` and `G2`.

`G1` and `G2` are previous-period grades and are strongly correlated with `G3`. They are excluded deliberately so that the project studies whether characteristics available before the final grade can provide useful predictions. The Mathematics and Portuguese files are not merged.

## Planned methodology

1. Inspect and describe the dataset, including data types, missing values, duplicates and the target distribution.
2. Split the data into training and test sets using a reproducible random state.
3. Preprocess numerical and categorical variables with scikit-learn pipelines and a column transformer, fitting preprocessing on training data only.
4. Compare a simple baseline with several understandable regression models.
5. Evaluate the final models on the untouched test set, inspect residuals and discuss limitations.

### Planned models

- `DummyRegressor` baseline
- `LinearRegression`
- `DecisionTreeRegressor`
- `RandomForestRegressor`

### Evaluation metrics

- Mean Absolute Error (MAE)
- Root Mean Squared Error (RMSE)
- R-squared (R²)

No performance results or conclusions are claimed until the models have been run.

## Responsible machine learning

Student data can be sensitive. Results should not be used to label students or make important decisions without human judgement. The project will consider privacy, possible differences in error between demographic groups, misuse, uncertainty and the limited generalisation of data from Portuguese secondary schools to other educational contexts.

## Project structure

```text
ct4101-machine_learning/
├── data/
│   ├── student-mat.csv
│   └── README.md
├── notebooks/
│   └── student_performance_ml.ipynb
├── src/
├── reports/
├── README.md
├── PROJECT_CONTEXT.md
├── requirements.txt
└── .gitignore
```

## Setup and running the notebook

From the repository root:

```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
jupyter notebook notebooks/student_performance_ml.ipynb
```

The notebook currently covers imports, data loading, initial data checks, predictor/target separation and a simple target visualisation. Model training will be added in a later milestone.
