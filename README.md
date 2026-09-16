# 🛒 SmartKart Customer Churn Prediction

An end-to-end **Machine Learning project** that predicts whether a SmartKart customer is likely to **churn (leave the business)** using **Logistic Regression**.

The project demonstrates a complete ML workflow, including data inspection, data cleaning, outlier treatment, feature selection, preprocessing, model training, prediction, and evaluation.

---

## 📌 Project Overview

Customer churn is an important business problem for retail companies. Identifying customers who are likely to leave allows a business to take preventive retention actions.

In this project, customer information such as:

* **Age**
* **Monthly Spend**
* **Complaints**

is used to predict the target variable:

* **Churn = 1** → Customer churned
* **Churn = 0** → Customer did not churn

The dataset intentionally contains messy real-world data such as missing values, duplicate records, invalid values, inconsistent formatting, and outliers.

---

## 🎯 Business Objective

> **Predict customers who are at risk of churning so that SmartKart's retention team can take action before the customer leaves.**

The model can help a business:

* Identify high-risk customers
* Prioritize retention efforts
* Understand potential churn drivers
* Support data-driven customer retention strategies
* Reduce customer loss

---

## 🤖 Machine Learning Approach

This project treats customer churn as a **binary classification problem**.

### Algorithm Used

**Logistic Regression**

Logistic Regression was selected because:

* Churn has two possible outcomes
* It is suitable for binary classification
* It is relatively interpretable
* It provides churn probabilities
* Probabilities can be used to rank customers according to their churn risk

---

## 🔄 ML Pipeline

The project follows a **15-step machine learning pipeline**:

```text
Data Collection
      ↓
Data Understanding
      ↓
Data Cleaning
      ↓
Outlier Detection & Treatment
      ↓
Feature Selection
      ↓
Define Target Variable
      ↓
Encode Target Variable
      ↓
Train-Test Split
      ↓
Feature Standardisation
      ↓
Model Building
      ↓
Model Training
      ↓
Prediction
      ↓
Model Evaluation
      ↓
Model Interpretation
      ↓
Final Output
```

---

## 📊 Dataset

**Dataset:** `SmartKart_dirty_100_rows.csv`

The original dataset contains **100 customer records** and 5 columns:

| Column          | Description                              |
| --------------- | ---------------------------------------- |
| `Customer_ID`   | Unique customer identifier               |
| `Age`           | Customer age                             |
| `Monthly_Spend` | Customer's monthly spending              |
| `Complaints`    | Number of customer complaints            |
| `Churn`         | Target variable: 1 = churn, 0 = no churn |

The dataset intentionally contains data-quality issues to simulate a realistic business dataset.

---

## 🧹 Data Cleaning

Before training the model, several data-quality problems are handled.

### Problems identified

* Missing values
* Duplicate customer records
* Extra whitespace
* Incorrect data types
* Text values in numeric columns
* Invalid ages
* Negative monthly spending
* Extreme outliers

### Cleaning performed

* Removed duplicate records
* Removed unnecessary whitespace
* Converted `Age` into numeric format
* Converted `"thirty"` into `30`
* Replaced unrealistic ages with missing values
* Converted negative spending into missing values
* Filled missing values using the **median**

The five duplicate records reduce the dataset from **100 to 95 records** after cleaning.

---

## 📈 Outlier Treatment

Outliers are detected using the **Interquartile Range (IQR)** method.

The project treats extreme values by **capping them rather than deleting the complete customer record**.

Examples include:

* `Monthly_Spend = 99999`
* `Complaints = 50`

These values are capped to statistically reasonable boundaries to prevent extreme observations from disproportionately affecting the Logistic Regression model.

---

## 🔎 Feature Selection

The following three features are used for prediction:

```python
Age
Monthly_Spend
Complaints
```

`Customer_ID` is excluded because it is an identifier rather than a meaningful predictive variable.

### Input → Output

```text
Age
Monthly Spend
Complaints
      ↓
Logistic Regression
      ↓
Churn Probability
      ↓
Churn / No Churn
```

---

## 🎯 Target Variable

The target variable is:

```text
Churn
```

Where:

```text
0 = No Churn
1 = Churn
```

The dataset has a relatively balanced churn distribution, with approximately **54% churn and 46% non-churn** after duplicate removal.

---

## ⚙️ Data Preprocessing

### Train-Test Split

The cleaned dataset is divided into:

* **80% Training Data**
* **20% Testing Data**

Stratification is used to maintain a similar churn distribution in both datasets.

A fixed `random_state=42` is used to make the results reproducible.

### Feature Standardisation

`StandardScaler` is used to standardise the numerical features.

The scaler is:

1. Fitted only on training data
2. Applied to training data
3. Applied to testing data using the same learned parameters

This prevents test-data information from leaking into the training process.

---

## 🧠 Model

### Logistic Regression

The model is implemented using:

```python
from sklearn.linear_model import LogisticRegression

model = LogisticRegression(random_state=42)
```

The model learns the relationship between:

```text
Age
Monthly_Spend
Complaints
```

and:

```text
Churn
```

The resulting model can generate a probability indicating how likely a customer is to churn.

---

## 📋 Model Evaluation

The pipeline includes model evaluation to determine how effectively the model predicts unseen customer data.

Evaluation focuses on appropriate classification metrics and includes model interpretation and final customer-level predictions.

> **Note:** Exact performance metrics should be taken from the output generated when the notebook is executed. This README does not assume a specific accuracy, precision, recall, or F1-score without the executed model output.

---

## 💼 Business Application

The model can be incorporated into a customer-retention workflow:

```text
Customer Data
      ↓
ML Churn Model
      ↓
Churn Probability
      ↓
Risk Classification
      ↓
High-Risk Customers
      ↓
Retention Team
      ↓
Targeted Retention Action
```

For example, customers identified as having a higher probability of churn could be prioritised for appropriate retention campaigns.

---

## 🛠️ Technologies Used

* **Python**
* **Pandas** — Data manipulation
* **NumPy** — Numerical operations
* **Matplotlib** — Data visualisation
* **Seaborn** — Visualisation
* **Scikit-learn** — Machine Learning
* **Google Colab / Jupyter Notebook** — Development environment

---

## 📁 Project Structure

```text
smartkart-customer-churn-prediction/
│
├── SmartKart_Churn_Prediction_ML_Pipeline.ipynb
├── SmartKart_dirty_100_rows.csv
└── README.md
```

---

## 🚀 How to Run

### Option 1 — Google Colab

1. Open `SmartKart_Churn_Prediction_ML_Pipeline.ipynb`
2. Upload `SmartKart_dirty_100_rows.csv`
3. Run the notebook from top to bottom
4. Review the preprocessing, model predictions, and evaluation results

The notebook is designed to use Google Colab's file-upload functionality.

### Option 2 — Jupyter Notebook

Install the required libraries:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn
```

Then open:

```text
SmartKart_Churn_Prediction_ML_Pipeline.ipynb
```

---

## 📌 Key Learning Outcomes

This project demonstrates practical understanding of:

* Data preprocessing
* Data quality management
* Missing-value treatment
* Duplicate detection
* Outlier detection
* Feature selection
* Target-variable definition
* Train-test splitting
* Feature standardisation
* Logistic Regression
* Binary classification
* Model prediction
* Model evaluation
* Business interpretation of ML results

---

## ⚠️ Project Limitations

This is an educational ML project using a small, intentionally messy dataset of **100 customer records**.

The model should therefore **not be considered production-ready** without further validation.

For a real-world deployment, the project could be extended with:

* Larger customer datasets
* Additional behavioural features
* Cross-validation
* Hyperparameter tuning
* Multiple ML algorithms
* Model comparison
* Feature importance analysis
* Probability calibration
* Model monitoring
* Production data pipelines

---

## 🔮 Future Improvements

Potential future versions could compare Logistic Regression with:

```text
Logistic Regression
        ↓
Decision Tree
        ↓
Random Forest
        ↓
Gradient Boosting
        ↓
XGBoost
```

The best-performing model could then be selected based on business-relevant evaluation metrics.

Additional customer features could also be incorporated, such as purchase frequency, tenure, average order value, and engagement behaviour.

---

## 👨‍💻 Project Context

**Course:** Introduction to AI & ML
**Program:** BBA AI/ML
**Institution:** Chitkara Business School
**Project:** SmartKart Customer Churn Prediction

---

## ⭐ Project Summary

> **SmartKart Customer Churn Prediction is an end-to-end machine learning project that transforms messy customer data into actionable churn predictions using Logistic Regression. It demonstrates how data preprocessing, statistical treatment, machine learning, and business interpretation can work together to support customer-retention decisions.**
