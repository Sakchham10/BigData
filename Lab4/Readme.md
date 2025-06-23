# Lab 4: Credit Card Fraud Detection using Autoencoder

This project demonstrates the use of an AutoEncoder neural network for anomaly detection, specifically for identifying fraudulent credit card transactions. The model is built using the `pyod` library.

## Dataset

The model is trained on the [Credit Card Fraud Detection](https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud) dataset from Kaggle. You need to download the `creditcard.csv` file and place it in the `Lab4/lab4_env/` directory alongside the `Lab4.ipynb` notebook.

## Setup and Installation

A Python virtual environment is included in `lab4_env`. If you want to set up your own environment, you need to install the following libraries:

```bash
pip install pandas scikit-learn pyod jupyter
```

The notebook was run with Python 3.9.

## Running the code

1.  Make sure `creditcard.csv` is in the `Lab4/lab4_env/` directory.
2.  Activate the virtual environment or make sure you have the required packages installed.
3.  Run the Jupyter Notebook:
    ```bash
    jupyter notebook Lab4/lab4_env/Lab4.ipynb
    ```

## Model and Implementation

The core of this project is an `AutoEncoder` model from the `pyod` library.

1.  **Data Loading and Preprocessing**: The `creditcard.csv` dataset is loaded. The `Time` and `Amount` columns are scaled using `StandardScaler`.
2.  **Data Splitting**: The data is split into training and testing sets. The training set consists only of normal transactions. The test set contains a mix of normal transactions (not seen during training) and all fraudulent transactions.
3.  **Model Training**: An `AutoEncoder` is trained on the normal transactions. The autoencoder learns to reconstruct normal data, so it will have a higher reconstruction error for fraudulent transactions.
4.  **Evaluation**: The model is evaluated on the test set.

## Results

The model's performance on the test set is as follows:

-   **ROC-AUC Score**: 0.9590

-   **Confusion Matrix**:
    ```
    [[56759   104]
     [  108   384]]
    ```
    - True Negatives (Normal, correctly identified): 56759
    - False Positives (Normal, incorrectly identified as Fraud): 104
    - False Negatives (Fraud, incorrectly identified as Normal): 108
    - True Positives (Fraud, correctly identified): 384

-   **Classification Report**:
    | | precision | recall | f1-score | support |
    | :--- | :--- | :--- | :--- | :--- |
    | **Normal** | 1.00 | 1.00 | 1.00 | 56863 |
    | **Fraud** | 0.79 | 0.78 | 0.78 | 492 |
    | | | | | |
    | **accuracy** | | | 1.00 | 57355 |
    | **macro avg** | 0.89 | 0.89 | 0.89 | 57355 |
    | **weighted avg** | 1.00 | 1.00 | 1.00 | 57355 |

The model achieves high accuracy, but more importantly a good F1-score for the minority class (Fraud), indicating it is effective at detecting fraudulent transactions. 