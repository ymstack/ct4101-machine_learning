# CT4101 Machine Learning Portfolio Project

## Research question

Can machine learning predict a student's final Mathematics grade using demographic, social and educational characteristics available before the final grade is known?

This is a regression problem, and the aim is to predict a numerical grade from student information.

## Dataset

The project uses the Maths file, `student-mat.csv`, from the [UCI Student Performance dataset](https://archive.ics.uci.edu/dataset/320/student+performance). It contains 395 student records. The Portuguese file is not used or merged. Full dataset details, licensing and citation information are in [data/README.md](data/README.md).

The target is `G3`, the final Maths grade on a 0–20 scale. The first 30 demographic, social and educational variables are used as predictors. `G1` and `G2` are excluded because they are earlier grades closely related to `G3`. This lets the project examine what can be predicted without those grades.

## Milestone 3 implementation

The notebook includes:

- A data audit covering shape, data types, missing values, duplicates, valid grade ranges, potential outliers and the target distribution.
- An 80/20 train/test split using `random_state=42`.
- Numerical preprocessing with `StandardScaler` and categorical preprocessing with `OneHotEncoder` inside a `ColumnTransformer` and `Pipeline`. Preprocessing is fitted on training data only.
- A `DummyRegressor(strategy="mean")` baseline evaluated on the held out test set.

Milestone 3 adds Linear Regression, Decision Tree Regression and Random Forest Regression. Five fold cross validation compares the models using only the training set, with preprocessing fitted separately in each fold. The model with the lowest mean validation MAE is selected. There is no parameter search: the tree uses `max_depth=4, min_samples_leaf=5`; the forest uses `n_estimators=200, min_samples_leaf=5`. Both use `random_state=42`.

Results on the same 79 test students:

| Model             | Test MAE | Test RMSE | Test R² |
| ----------------- | -------: | --------: | ------: |
| Dummy Regressor   |   3.6459 |    4.5502 | -0.0097 |
| Linear Regression |   3.3953 |    4.1957 |  0.1415 |
| Decision Tree     |   3.5430 |    4.4648 |  0.0278 |
| Random Forest     |   3.0899 |    3.8557 |  0.2750 |

Random Forest had the lowest cross validation MAE (2.9689) and reduced test MAE by 0.5559 grade points compared with the baseline. Linear Regression beat the baseline on the test set but not in cross validation so the comparison can change across samples.

The notebook includes prediction and residual plots, errors by grade range and the ten largest errors for the selected forest. On this test set, its MAE was 1.485 for grades 10–14 (32 students), compared with 8.213 for zero grades (5 students) and 4.064 for grades 15–20 (20 students). It predicted too high for the lowest grades and too low for the highest grades. The improved overall score therefore hides some large errors.

## Setup and running the notebook on macOS

The notebook was run using **Python 3.9.6**. The package versions are listed in `requirements.txt`.

Run these commands from the repository root. Jupyter runs this notebook with `notebooks/` as its kernel working directory, so `../data/student-mat.csv` resolves to the dataset.

```bash
cd /path/to/ct4101-machine_learning
python3 -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
jupyter notebook notebooks/student_performance_ml.ipynb
```

Open and run the cells in order. If running the code outside Jupyter, use `notebooks/` as the working directory so the dataset path resolves correctly.

## Responsible machine learning

The data comes from Portuguese secondary schools and may not generalise elsewhere. The timing of variables such as absences is unclear so this does not establish how well the models would work early in the school year. Errors have not been checked across demographic groups. Privacy and fairness would need further attention before real use and predictions should not be the sole basis for decisions about students.

## AI assistance declaration

I used ChatGPT, Codex and GitHub Copilot for planning, repository setup, code generation and model comparison. Codex also ran the notebook to check the results. I am responsible for checking the work and understanding what I submit.
