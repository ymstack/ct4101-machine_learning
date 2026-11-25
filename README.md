# CT4101 – Machine Learning Portfolio

## Project Overview

For my machine learning portfolio, I wanted to investigate whether a student's final Maths grade could be predicted without knowing their previous grades.

**Research question:** Can machine learning predict a student's final Mathematics grade using demographic, social and educational characteristics available before the final grade is known?

This is a supervised learning problem, specifically regression, as the target is a numerical grade between 0 and 20.

## Dataset

I used the Mathematics file from the [UCI Student Performance dataset](https://archive.ics.uci.edu/dataset/320/student+performance).

The dataset contains 395 student records and 33 columns. The target variable is G3, which represents the student's final grade.

I excluded G1 and G2 as these are previous grades and would make predicting G3 considerably easier. The idea was to investigate how much could be predicted using the remaining 30 variables alone.

Further information about the dataset can be found in the [data statement](data/README.md).

## Methodology

The project follows a standard machine learning workflow:

- Initial data exploration and quality checks.
- 80/20 training and testing split using a random state of 42.
- StandardScaler for numerical variables and OneHotEncoder for categorical variables.
- A mean Dummy Regressor as the baseline.
- Five fold cross validation to compare the models.
- Final evaluation on the held-out test set.
- Visualisation and analysis of prediction errors.

Preprocessing is carried out inside a pipeline to prevent information from the validation or test data leaking into training.

The Decision Tree uses a maximum depth of 4 and a minimum of 5 samples per leaf. The Random Forest uses 200 trees and a minimum of 5 samples per leaf. No hyperparameter search was carried out.

## Results

| Model             | CV MAE | CV MAE SD | Test MAE | Test RMSE | Test R² |
| ----------------- | -----: | --------: | -------: | --------: | ------: |
| Dummy Regressor   | 3.4029 |    0.6293 |   3.6459 |    4.5502 | -0.0097 |
| Linear Regression | 3.5227 |    0.3819 |   3.3953 |    4.1957 |  0.1415 |
| Decision Tree     | 3.1758 |    0.2071 |   3.5430 |    4.4648 |  0.0278 |
| Random Forest     | 2.9689 |    0.3400 |   3.0899 |    3.8557 |  0.2750 |

Random Forest was selected because it achieved the lowest mean MAE during cross-validation. It also performed best on the test set, improving on the baseline MAE by approximately 15%.

One of the more interesting findings was that the model performed much better on students with grades around the middle of the scale. It struggled considerably with very low and very high grades.

Although the results show that the remaining student characteristics have some predictive value, I would not recommend using this model to make decisions about students.

## Running the Project

The project was tested using Python 3.9.6.

From the repository root, run:

```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
jupyter notebook notebooks/student_performance_ml.ipynb
```

Once the notebook is open, run all cells in order.

The notebook expects `notebooks/` to be its working directory and loads the dataset from `../data/student-mat.csv`.

## Project Documentation

- [Machine learning notebook](notebooks/student_performance_ml.ipynb)
- [Data statement](data/README.md)
- [Model card](MODEL_CARD.md)
- [Reflective changelog](REFLECTIVE_CHANGELOG.md)
- [Original project plan](PROJECT_CONTEXT.md)

## AI Assistance Declaration

I used ChatGPT, GitHub Copilot and Codex throughout this project to assist with planning, repository setup, code generation, model comparison and reviewing results. Codex also executed the notebook to verify that the results could be reproduced.

I am responsible for reviewing the work and understanding what I submit. I believe I used AI well to help me understand what I was doing and understanding all of the concepts Frank and Umay taught while also being as efficient as possible and reviewing my work.
