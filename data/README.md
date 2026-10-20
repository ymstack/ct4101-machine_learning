# Dataset

This project uses the **UCI Student Performance dataset**, Mathematics course file:

- File: `student-mat.csv`
- Source: [UCI Machine Learning Repository - Student Performance](https://archive.ics.uci.edu/dataset/320/student+performance)
- Official citation: Cortez, P. (2008). Student Performance [Dataset]. UCI Machine Learning Repository. [https://doi.org/10.24432/C5TG7T](https://doi.org/10.24432/C5TG7T)
- Licence: CC BY 4.0

The file contains 395 Mathematics students and uses a semicolon (`;`) as its separator. `G3` is the student's final Mathematics grade, measured from 0 to 20, and is the regression target.

The first 30 demographic, social and educational variables are candidate predictors. `G1` and `G2` are deliberately excluded because they are previous-period grades and are strongly related to `G3`. The Portuguese dataset is not merged with this Mathematics dataset.

The CSV is kept in the repository for this project and should not be replaced with a different copy.
