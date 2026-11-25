# Model Card – Random Forest Regressor

## Model Overview

The Random Forest is the best performing model from my CT4101 machine learning project. Its purpose is to predict a student's final Mathematics grade (G3) without using their previous grades (G1 and G2).

## Model Configuration

| Parameter                | Value |
| ------------------------ | ----- |
| Number of trees          | 200   |
| Minimum samples per leaf | 5     |
| Random state             | 42    |
| Training samples         | 316   |
| Testing samples          | 79    |
| Input variables          | 30    |
| Target range             | 0–20  |

All other model parameters were left at their defaults, apart from `n_jobs=-1`, which allows parallel processing. No hyperparameter tuning was performed.

Numerical variables are scaled and categorical variables are one hot encoded. Preprocessing is fitted within the pipeline using training data only.

## Model Performance

| Metric                                  | Result |
| --------------------------------------- | -----: |
| Mean cross-validation MAE               | 2.9689 |
| Cross-validation MAE standard deviation | 0.3400 |
| Training MAE                            | 2.0551 |
| Test MAE                                | 3.0899 |
| Test RMSE                               | 3.8557 |
| Test R²                                 | 0.2750 |

The Random Forest improved on the baseline test MAE by approximately 15%. However, the difference between training and testing MAE suggests that some overfitting may still be present.

## Where the Model Struggles

| Actual grade | Number of students |   MAE |
| ------------ | -----------------: | ----: |
| 0            |                  5 | 8.213 |
| 1–9          |                 22 | 3.375 |
| 10–14        |                 32 | 1.485 |
| 15–20        |                 20 | 4.064 |

The model tends to predict grades towards the middle of the scale. It overpredicted all five students who received a grade of zero and generally underpredicted students with higher grades.

This is an important limitation because the students who might benefit most from an early intervention could also be among those receiving the least accurate predictions.

The small number of students in some grade ranges should also be taken into consideration when interpreting these results.

## Limitations and Responsible Use

The model was evaluated on a relatively small dataset from Portuguese secondary schools. There is no evidence that it would perform equally well in other schools or education systems. I explain this better in my final report.

Some variables contain sensitive information about students including their health, family background and alcohol consumption. Performance across demographic groups has not been investigated so the model cannot be assumed to be fair.

It is also unclear when certain information such as absences would become available during the school year.

## Deployment Recommendation

I would not deploy this model in its current state.

Although it performed better than the baseline the errors are still too large to justify using it to rank students assign grades or decide who receives educational support.

Before considering any real world use, I would want to test the model on other student populations, investigate demographic differences in prediction errors and establish exactly when predictions would be made. I also explain this better in my final report.

## Future Monitoring

If the model were developed further I would monitor changes in student characteristics over time to identify data drift.

I would also monitor prediction errors once actual grades became available. Changes in teaching methods, grading systems or the relationship between student characteristics and grades could lead to concept drift.

These checks have not been implemented as part of the current project.
