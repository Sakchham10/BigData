Regression Analysis on the Diabetes Dataset
Project Overview
This project demonstrates various regression techniques to predict diabetes disease progression using the Diabetes dataset from sklearn.datasets. It covers the entire workflow from data preparation to model implementation, evaluation, and comparison. The primary goal is to explore how different regression models perform on the same dataset and to understand the impact of techniques like polynomial feature expansion and regularization.

Dataset
The project utilizes the Diabetes dataset, which is included in the scikit-learn library.

Source: sklearn.datasets.load_diabetes

Features: Ten baseline variables (age, sex, body mass index, average blood pressure, and six blood serum measurements) for 442 diabetes patients.

Target: A quantitative measure of disease progression one year after the baseline.

Prerequisites
To run the code, you need Python and the following libraries installed:

numpy

pandas

matplotlib

scikit-learn

You can install them using pip:

pip install numpy pandas matplotlib scikit-learn

Project Workflow
The analysis is structured into five main steps:

Data Preparation: Load and inspect the dataset. Since the sklearn dataset is pre-cleaned, no significant cleaning is required.

Simple Linear Regression: Build a model using a single feature (bmi) to establish a baseline.

Multiple Regression: Extend the model to use all available features to improve prediction accuracy.

Polynomial Regression: Introduce polynomial features to capture non-linear relationships in the data and analyze the trade-off between model complexity, underfitting, and overfitting.

Regularization: Implement Ridge (L2) and Lasso (L1) regression to handle potential overfitting and multicollinearity by penalizing large coefficient values.

Evaluation Metrics
The performance of each model is evaluated using the following standard regression metrics:

Mean Absolute Error (MAE): The average of the absolute differences between predicted and actual values.

Mean Squared Error (MSE): The average of the squared differences between predicted and actual values.

Root Mean Squared Error (RMSE): The square root of MSE, providing an error metric in the same units as the target variable.

R-squared (R²): The proportion of the variance in the dependent variable that is predictable from the independent variable(s).

Model Performance Summary
The following table compares the performance of all implemented models on the test set.

Model

MAE

MSE

RMSE

R²

Simple Linear Regression

49.78

3444.69

58.69

0.35

Multiple Linear Regression

42.79

2900.19

53.85

0.45

Polynomial Regression (Deg 2)

43.58

3065.53

55.37

0.42

Ridge Regression (alpha=1.0)

44.97

3051.35

55.24

0.42

Lasso Regression (alpha=0.1)

43.15

2948.52

54.30

0.44

Note: Results are based on a random_state of 42 for the train-test split and may vary slightly with different states or parameters.

How to Run
Save the Python code as a .py file (e.g., regression_analysis.py) and run it from your terminal:

python regression_analysis.py

The script will print the evaluation metrics for each model to the console and display a series of matplotlib plots visualizing the results.

Key Takeaways
Multiple Regression provides a significant improvement over Simple Linear Regression by leveraging all available features.

Polynomial Regression with a degree of 2 did not improve upon the multiple linear model for this dataset and showed signs of overfitting as the degree increased.

Ridge and Lasso Regression provide regularization to prevent overfitting. Their performance is comparable to the Multiple Linear Regression model, with Lasso offering the added benefit of potentially simplifying the model by shrinking some feature coefficients to zero.
