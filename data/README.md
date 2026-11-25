# Data Statement

## Dataset Information

- Dataset: UCI Student Performance
- File: `student-mat.csv`
- Source: [UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/320/student+performance)
- Licence: CC BY 4.0
- Number of records: 395
- Number of columns: 33
- File separator: Semicolon (;)

The dataset contains information about students attending Portuguese secondary schools. For this project, only the Mathematics dataset is used.

## Variables

The target variable is G3 which represents the student's final Mathematics grade on a scale of 0–20.

The project uses 30 predictor variables, consisting of 13 numerical and 17 categorical variables. These include information about student demographics, family background, study habits, school support and social activities.

G1 and G2 are excluded because they represent previous grades. The purpose of the project is to investigate prediction without relying on previous academic results.

## Data Quality

The initial data audit found no missing values or duplicate rows.

Some numerical variables, such as study time, represent ordered categories rather than continuous measurements. This is worth considering when interpreting the results.

The original CSV is included in the repository so that the notebook can be run without downloading the dataset separately.

## Limitations

The dataset is relatively small and comes from a specific educational setting. Results from these students may not represent students in other countries, schools or education systems.

It is also unclear when some variables were recorded. For e.g., the number of absences available at the end of the year may be different from what would be available when making an early prediction.

## Privacy and Fairness

Some of the information in the dataset is sensitive, particularly information relating to health, family circumstances and alcohol consumption.

Any real world use of similar data would require careful consideration of privacy, access and the purpose for which the information is collected.

The project investigates prediction errors across grade ranges but does not evaluate fairness across demographic groups.

## Citation

Cortez, P. (2008). Student Performance [Dataset]. UCI Machine Learning Repository.

https://doi.org/10.24432/C5TG7T
