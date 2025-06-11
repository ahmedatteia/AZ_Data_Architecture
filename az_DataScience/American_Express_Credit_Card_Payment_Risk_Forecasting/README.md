
# American Express Credit Card Payment Risk Forecasting Using Machine Learning

This project focuses on predicting credit card payment risk using machine learning techniques. Managing credit risk is critical for financial institutions, and this project aims to develop models that help predict whether a customer will default on their credit card payments.

## Project Overview

In this project, we explored various machine learning models to predict the likelihood of American Express customers defaulting on their credit card payments. Accurate credit risk prediction helps issuers make better lending decisions, optimizing both business performance and customer experience.

## Machine Learning Models Used:

- **Logistic Regression**:  
  Logistic regression is a linear model that estimates the probability of a binary outcome (e.g., default or no default). It's commonly used when the relationship between the features and the target is roughly linear. This model works well with structured, tabular data and is ideal when interpretability is important.

- **Decision Tree**:  
  A decision tree is a model that splits the data into branches based on feature values, creating a set of decision rules. It is intuitive and easy to visualize, making it useful when you want a clear understanding of the decision-making process. Decision trees handle both numerical and categorical data.

- **Random Forest**:  
  Random forest is an ensemble method that builds multiple decision trees and aggregates their predictions. It's particularly effective for reducing overfitting in decision trees and can handle both structured data and high-dimensional datasets. Random forests work well with numerical and categorical data.

- **Gradient Boosting Machines (GBM)**:  
  GBM is a boosting technique that builds models sequentially by combining weak learners to create a strong model. It is useful for complex datasets where patterns are difficult to capture, and it works best with structured, numerical data. GBM is often used in competitions due to its high predictive accuracy.

- **LightGBM**:  
  LightGBM is a gradient boosting framework optimized for speed and efficiency, especially with large datasets. It is well-suited for structured, tabular data and can handle both numerical and categorical features. LightGBM is preferred when working with large-scale datasets and high-dimensional features.

- **XGBoost**:  
  XGBoost is an optimized version of gradient boosting that delivers state-of-the-art performance in terms of both speed and accuracy. It works well for tabular data, both numerical and categorical. XGBoost is often the go-to model for structured datasets in machine learning competitions.

- **CatBoost**:  
  CatBoost is a gradient boosting algorithm designed to handle categorical variables without the need for extensive preprocessing. It’s especially useful when dealing with datasets that have many categorical features and can be applied to both numerical and categorical data. CatBoost is known for its ease of use and strong performance.

## Dataset Overview

The dataset consists of aggregated customer profile data and transaction history over multiple months. It includes various features related to spending patterns, balances, payment history, and delinquency, which serve as predictors for whether a customer defaults.

Key Features:

- **D_***: Delinquency variables that track the customer's overdue payments.
- **S_***: Spend variables that represent customer spending patterns.
- **P_***: Payment variables that describe the customer’s payment history.
- **B_***: Balance variables that track the customer’s current and past balances.
- **R_***: Risk variables that capture various risk factors for each customer.

Categorical features include variables such as B_30, B_38, D_63, D_64, D_66, and others, which require encoding or special handling before model training.

## Project Objectives

1. **Predict Payment Defaults**: Build machine learning models to predict whether customers will default on their credit card payments based on profile and transaction data.
2. **Feature Correlation Analysis**: Understand the relationships between various customer features and payment risk.
3. **Evaluate Model Performance**: Compare different models using metrics such as ROC-AUC, accuracy, and F1 score to identify the most effective model.
4. **Handle Categorical Variables**: Properly encode or exclude categorical variables to ensure accurate predictions.

## Data Preprocessing and Feature Engineering

The dataset required several preprocessing steps to prepare it for model training:

- **Missing Value Imputation**: Missing values were imputed using the `IterativeImputer` from `scikit-learn`.
- **Categorical Encoding**: Categorical variables were handled using one-hot encoding or label encoding, depending on their nature.
- **Scaling**: Features were scaled using StandardScaler to normalize the range of values.

## Model Evaluation

We trained and evaluated the following machine learning models to predict credit card payment risk:

- **Logistic Regression**: A linear model used to estimate the probability of default based on feature relationships.
- **Decision Tree**: A tree-based model that learns decision rules for predicting defaults.
- **Random Forest**: An ensemble method that builds multiple decision trees and aggregates their predictions.
- **Gradient Boosting Machines (GBM)**: A boosting method that combines weak learners to create a strong predictive model.
- **LightGBM**: A highly efficient gradient boosting algorithm optimized for large datasets.
- **XGBoost**: Another boosting algorithm known for its performance and speed.
- **CatBoost**: A gradient boosting algorithm that handles categorical variables without extensive preprocessing.

## Key Results

- **Random Forest** achieved the highest ROC-AUC score, making it the best model for predicting payment defaults.
- **LightGBM** and **XGBoost** also performed well, offering competitive results in terms of both speed and accuracy.

## Future Work

- **Feature Engineering**: Further feature engineering could be done to extract more meaningful insights from the dataset, such as analyzing time-based patterns in customer spending.
- **Hyperparameter Tuning**: Fine-tuning model hyperparameters can improve the accuracy and robustness of the models.
- **Real-Time Risk Prediction**: Implement real-time risk prediction using streaming platforms like Apache Kafka and Flink, enabling instant insights into customer risk profiles.
- **Deployment**: Deploy the models to a production environment, allowing American Express to use them for day-to-day credit risk assessments.

## How to Run the Code

1. **Clone the repository**:
   ```bash
   git clone https://github.com/your-username/amex-credit-risk-forecasting.git
   ```

2. **Install the required Python libraries**:
   ```bash
   pip install -r requirements.txt
   ```

3. **Run the Jupyter notebook or Python script**:
   ```bash
   jupyter notebook credit_risk_forecasting.ipynb
   ```

4. **Download the dataset**:
   The dataset used in this project can be obtained from [Kaggle](https://www.kaggle.com/competitions/amex-default-prediction/data).
