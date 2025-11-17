# Medical Insurance Cost Prediction using Linear Regression

## 🚀 Project Overview

This project uses a Linear Regression model to predict medical insurance costs (`charges`) based on a patient's personal and health-related attributes. The goal is to build a model that accurately estimates insurance charges, providing insights into the key factors that drive healthcare costs.

The model was trained on a dataset of 1338 entries and, after rigorous preprocessing, achieved an **R-squared score of 96.80%** on the unseen test data.

---

## 📋 Project Workflow

The project follows a standard machine learning workflow:
1.  **Data Loading:** Imported the `insurance_data.csv` dataset.
2.  **Data Cleaning:**
    * **Imputation:** Filled missing numerical values (like `bmi`) with the **median** and categorical values with the **mode**.
    * **Outlier Removal:** Used the Interquartile Range (IQR) method to identify and remove extreme outliers from key features.
3.  **Feature Engineering:**
    * **Label Encoding:** Converted categorical columns (`sex`, `smoker`, `region`) into numerical values.
4.  **Model Preparation:**
    * Split the data into training (75%) and testing (25%) sets.
    * **Feature Scaling:** Applied `StandardScaler` to all features (X) to normalize their range, which is critical for linear models.
5.  **Modeling & Evaluation:**
    * Trained a `LinearRegression` model on the scaled training data.
    * Evaluated the model on the scaled test data using $R^2$, MSE, and RMSE.

---

## 📊 Model Performance

The model performs exceptionally well on the test set, explaining the vast majority of the variance in the data.

* **R-squared ($R^2$)**: **96.80%**
* **Root Mean Squared Error (RMSE)**: **$759.56**

An $R^2$ of 96.80% indicates that the model can explain ~97% of the variability in insurance charges. An RMSE of ~$760 means that, on average, the model's predictions are off by about $760, which is a strong result given the range of charges.

---

## 💡 Key Findings: What Drives Costs?

By inspecting the model's coefficients, we can identify the most significant factors influencing insurance charges:

| Feature | Coefficient | Meaning |
| :--- | :--- | :--- |
| **`num_of_steps`** | 2698.84 | The strongest positive predictor. More steps may correlate with higher-cost health plans or procedures. |
| **`Anual_Salary`** | 1500.04 | Higher salary is a strong positive predictor of higher charges. |
| **`smoker`** | 558.97 | Being a smoker significantly increases charges. |
| **`age`** | 550.10 | Older age is a strong predictor of higher charges. |
| **`NUmber_of_past_hospitalizations`** | -482.32 | **(Interesting Finding)** A history of hospitalization has a strong *negative* impact, possibly indicating more preventative follow-up care. |

---

## 📁 Data Dictionary

This describes the columns found in the `insurance_data.csv` dataset.

| Column | Type | Description |
| :--- | :--- | :--- |
| `age` | float | Age of the primary beneficiary. |
| `sex` | object | Beneficiary's gender (male/female). |
| `bmi` | float | Body Mass Index. |
| `children` | float | Number of children covered by the insurance. |
| `smoker` | object | Whether the beneficiary smokes (yes/no). |
| `Claim_Amount` | float | Amount of insurance claim (likely past data). |
| `past_consultations` | float | Number of past medical consultations. |
| `num_of_steps` | float | Average number of steps taken per day. |
| `Hospital_expenditure` | float | Past expenditure on hospital visits. |
| `Number_of_past_hospitalizations`| float | Number of times hospitalized in the past. |
| `Annual_Salary` | float | Annual income of the beneficiary. |
| `region` | object | Beneficiary's residential area in the US (e.g., southeast). |
| **`charges`** | **float** | **(Target Variable)** Individual medical costs billed by health insurance. |

---

## ⚙️ How to Run This Project

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/your-username/medical-insurance-prediction.git](https://github.com/your-username/medical-insurance-prediction.git)
    cd medical-insurance-prediction
    ```

2.  **Create a virtual environment (Recommended):**
    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows: venv\Scripts\activate
    ```

3.  **Install the required libraries:**
    ```bash
    pip install -r requirements.txt
    ```

4.  **Run the script:**
    ```bash
    python predict_charges.py
    ```
