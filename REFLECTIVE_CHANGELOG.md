# Reflective changelog

## Milestone 1 — Proposal and setup

I started with the UCI Mathematics dataset and set up the notebook and its dependencies. I defined the task as predicting the final grade, `G3`. I left out the earlier grades `G1` and `G2` to see how much I could predict from demographic, social and educational information alone. I planned to compare a mean baseline with three learned models and evaluate them on a held-out test set. [Original planning notes](PROJECT_CONTEXT.md)

## Milestone 2 — Data audit, preprocessing and baseline

I checked the 395 rows and found no missing values or duplicates. I made a reproducible 80/20 split, then fitted the numerical scaling and category encoding on the training data. I tested a dummy model that predicts the mean training grade. Its test MAE of 3.6459 grade points gave me a reference for the other models. I also updated the setup instructions and dependency versions.

## Milestone 3 — Model comparison and error analysis

I added Linear Regression, Decision Tree and Random Forest. I compared them with the dummy using the same five shuffled training folds and preprocessing steps. I fitted preprocessing separately in each fold using its training portion. I chose the model with the lowest mean validation MAE and used the held-out test results to compare the fitted models. I later clarified the notebook explanations and README.

Random Forest had the lowest mean CV MAE (2.9689) and lowered held-out MAE to 3.0899. Linear Regression had a lower MAE than the dummy on the test set and a higher mean CV MAE, so its ranking varied across the two evaluations. When I looked at the forest’s errors by grade band, it struggled at the extremes. Its MAE was 8.213 across the five students who received zero. The overall improvement still leaves room for large errors on individual grades. [Notebook](notebooks/student_performance_ml.ipynb)

## Milestone 4 — Final documentation and reproducibility

I expanded the data statement and added a model card and this changelog. The README now shows CV variation and held-out results together, and the notebook uses a generic Python kernel label. The experiment still uses the original research question, data split and model settings.

The dataset is small and comes from Portuguese secondary schools. Some predictors may only become available later in the school year, the model makes large errors at the grade extremes and I did not compare errors across demographic groups. The results are enough to compare the models for the portfolio. I recommend against deploying the selected model. [Model card](MODEL_CARD.md)

### Commit references

| Milestone | Commits |
| --- | --- |
| 1 | `0db49aa` |
| 2 | `5b291e5`, `b6cf4f7`, `826c847`, `e82b1bb` |
| 3 | `c3d544a`, `68c0a95`, `697b37c` |

**Personal reflection to confirm** — What I found most challenging, how my judgement changed and what I would do differently.
