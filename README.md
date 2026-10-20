# CT4101 Machine Learning Portfolio Project

## Research question

Can machine learning predict a student's final Mathematics grade using demographic, social and educational characteristics available before the final grade is known?

This is a supervised regression project using a simple, reproducible workflow.

## Dataset

The project uses the Mathematics file, `student-mat.csv`, from the [UCI Student Performance dataset](https://archive.ics.uci.edu/dataset/320/student+performance). It contains 395 student records. The Portuguese file is not used or merged. Full dataset details, licensing and citation information are in [data/README.md](data/README.md).

The target is `G3`, the final Mathematics grade on a 0-20 scale. The first 30 demographic, social and educational variables are used as candidate predictors. `G1` and `G2` are deliberately excluded because they are previous-period grades strongly related to `G3`; excluding them keeps the research question focused on information available before the final grade.

## Milestone 2 implementation

The notebook currently includes:

- A data audit covering shape, data types, missing values, duplicates, valid grade ranges, potential outliers and the target distribution.
- An 80/20 train/test split using `random_state=42`.
- Numerical preprocessing with `StandardScaler` and categorical preprocessing with `OneHotEncoder` inside a `ColumnTransformer` and `Pipeline`. Preprocessing is fitted on training data only.
- A `DummyRegressor(strategy="mean")` baseline evaluated on the held-out test set.

The baseline results are:

| Metric | Test result |
| --- | ---: |
| MAE | 3.6459 |
| RMSE | 4.5502 |
| R² | -0.0097 |

The MAE means that the constant baseline prediction is about 3.65 grade points away from the actual grade on average. RMSE is higher because it gives larger errors more weight. The slightly negative R² shows that this baseline explains no useful variation on this test split and is a reference point for later models.

## Setup and running the notebook on macOS

Run these commands from the repository root. The working directory matters because the notebook loads the dataset with the relative path `../data/student-mat.csv`.

```bash
cd /path/to/ct4101-machine_learning
python3 -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
jupyter notebook notebooks/student_performance_ml.ipynb
```

Open and run the cells in order. The notebook should be launched while the repository root is the working directory; do not launch it from inside `notebooks/`.

## Responsible machine learning

The data comes from Portuguese secondary schools and may not generalise to other populations. Predictions should not be used to label students or make important decisions without human judgement. Privacy, fairness, misuse and uncertainty should be considered when interpreting results.

## AI assistance declaration

ChatGPT and GitHub Copilot were used substantially to assist with project planning, repository setup, code generation, debugging, documentation and interpretation of the analysis. The student remains responsible for reviewing the submitted implementation, understanding how it works, checking the results and sources, and ensuring that the conclusions are accurate and defensible.
