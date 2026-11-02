# Dataset

This project uses the **UCI Student Performance dataset**, Mathematics course file:

- File: `student-mat.csv`
- Source: [UCI Machine Learning Repository - Student Performance](https://archive.ics.uci.edu/dataset/320/student+performance)
- Official citation: Cortez, P. (2008). Student Performance [Dataset]. UCI Machine Learning Repository. [https://doi.org/10.24432/C5TG7T](https://doi.org/10.24432/C5TG7T)
- Licence: CC BY 4.0

The file contains records for 395 Mathematics students and uses a semicolon (`;`) as its separator. `G3`, the final Mathematics grade from 0 to 20, is the value being predicted.

The first 30 demographic, social and educational variables are used as predictors. `G1` and `G2` are excluded because they are earlier grades closely related to `G3`. Only the Mathematics file is used.

The CSV is included so the notebook can run without a separate download.
