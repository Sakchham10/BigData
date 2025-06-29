
# 📊 Lab 4: Regression Analysis Using the Diabetes Dataset

## 🧪 Purpose of the Lab
The objective of this lab is to gain hands-on experience with regression techniques, specifically:
- Applying **simple linear regression** using a single predictor (`BMI`) from the diabetes dataset.
- Implementing **multiple linear regression** using all available features.
- Evaluating and comparing models using metrics like **Mean Squared Error (MSE)** and **R² score**.

This lab provides foundational understanding for interpreting model performance and learning the practical implications of using different sets of features in regression.

## 🔍 Key Insights Gained
- **Feature Impact**: The `BMI` feature alone showed significant predictive power in the simple linear regression model, highlighting its strong correlation with disease progression.
- **Model Accuracy**: The multiple linear regression model performed better overall, indicating that including more features can enhance prediction accuracy—albeit at the cost of model interpretability.
- **Evaluation Metrics**: The lab demonstrated how metrics like MSE and R² offer quantitative insight into model performance. R² values closer to 1 indicated better model fit.

## ⚙️ Challenges and Decisions
- **Feature Selection**: Choosing `BMI` for simple linear regression required understanding its domain relevance and statistical correlation with the target.
- **Model Comparison**: Balancing simplicity (fewer predictors) with performance was a key decision point, especially when interpreting trade-offs between the two regression approaches.
- **Data Split Strategy**: The use of an 80-20 train-test split with a fixed random seed ensured reproducibility, which is crucial for comparing model outputs.
