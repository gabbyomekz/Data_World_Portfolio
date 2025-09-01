# Bank Customer Churn Prediction / Data Exploratory Analysis  

## 📌 Project Overview  
Customer churn is a major challenge for banks and financial institutions, as retaining an existing customer is often more cost-effective than acquiring a new one. This project focuses on building machine learning models to **predict whether a customer is likely to churn** (exit the bank), based on demographic, account, and transactional features.  

The workflow covers:  
- Exploratory Data Analysis (EDA)  
- Feature Engineering (including one-hot encoding categorical variables)  
- Model training and evaluation  
- Comparison of multiple classifiers to identify the best performer  

---

## 📂 Dataset  
The dataset consists of **10,000 customer records** with the following key features:  

- **Identification**: `RowNumber`, `CustomerId`, `Surname`
- **Demographic features**: `Age`, `Gender`, `Geography`  
- **Banking features**: `CreditScore`, `Balance`, `NumOfProducts`, `HasCrCard`, `IsActiveMember`, `EstimatedSalary`, `Complain`,  
- **Target variable**: `Exited` (1 = customer churned, 0 = customer stayed)  

---

## 🔎 Exploratory Data Analysis (EDA)  
Some key insights observed:  
- Younger customers (20–30) are less likely to churn, while **middle-aged customers (35–50) show higher churn rates**.  
- Old-aged customers (50+) showed the highest churn rates
- Customers with **lower activity** tend to churn more.  
- Geographic and card type distributions also influence churn behavior.  

📊 **Age vs Churn**  
- Blue = Stayed, Orange = Exited  
- Old-aged customers showed the highest churn risk, with an impending middle-agged customer on the rise  

---

## ⚙️ Methodology  

1. **Data Preprocessing**  
   - Read in the data using pandas; no null values and duplicates
   - Correlation analysis on the numerical features to see each features correlation with the target variable `Exited`
   - Considered Numerical features only (with `Complain`) and (without `Complain`) due to the tricky correlation of `Complain` with `Exited`
   - One-Hot Encoding applied to categorical variables (`Geography`, `Gender`, `Card Type`)
   - Combination of numerical and one hot encoded categorical features
   - Features scaled using `StandardScaler` (for Logistic Regression)  

2. **Model Training & Evaluation**  
   Three models were trained and compared:  
   - Logistic Regression  
   - Random Forest Classifier  
   - XGBoost Classifier    

3. **Evaluation Metrics**  
   - Accuracy  
   - Precision  
   - Recall  
   - F1-Score  
   - Confusion Matrix  

---

## 🏆 Results

### Numerical Features only (with `Complain`)

| Model                  | Accuracy | Precision | Recall | F1-Score |
|-------------------------|----------|-----------|--------|----------|
| Logistic Regression     | 0.9985   | 0.9985    | 0.9985 | 0.9985   |
| Random Forest           | 0.9985   | 0.9985    | 0.9985 | 0.9985   |
| XGBoost Classifier      | 0.9985   | 0.9985    | 0.9985 | 0.9985   |

👉 The **best performing model** was:  
**`No best performer`**, all the model showed the same results (almost a perfect 100%) signalling that something is wrong as portrayed by the correlation matrix

### Numerical Features only (without `Complain`)

| Model                  | Accuracy | Precision | Recall | F1-Score |
|-------------------------|----------|-----------|--------|----------|
| Logistic Regression     | 0.8100   | 0.7839    | 0.8100 | 0.7585   |
| Random Forest           | 0.8655   | 0.8587    | 0.8655 | 0.8509   |
| XGBoost Classifier      | 0.8450   | 0.8321    | 0.8450 | 0.8329   |

👉 The **best performing model** was:
**`Random Forest Classifier`**, achieving the highest balance between recall (capturing churned customers) and precision (avoiding false positives).

### Numerical Features (without `Complain`) + One Hot encoded categorical features

| Model                  | Accuracy | Precision | Recall | F1-Score |
|-------------------------|----------|-----------|--------|----------|
| Logistic Regression     | 0.8130   | 0.7855    | 0.8130 | 0.7741   |
| Random Forest           | 0.8655   | 0.8582    | 0.8655 | 0.8515   |
| XGBoost Classifier      | 0.8490   | 0.8385    | 0.8490 | 0.8408   |

👉 The **best performing model** was:
**`Random Forest Classifier`**, achieving the highest balance between recall (capturing churned customers) and precision (avoiding false positives).

**The features that produced the best predictive strength to the models are a combination of numerical features (without complain) and one hot encoded categorical features**

---

## 📈 Key Business Insights  
- Churn is not evenly distributed across age groups — **old-aged customers had the most churn despite having the smallest customer size**.  
- Retention efforts should be **personalized**, with more focus on at-risk segments (e.g., high-balance inactive customers).
- Complaints should be recorded and addressed as soon as they are received to gain customers trust. It seemed complaints were recorded after customer had churned, reasons why it is not a valid predictor and biased the result.
- Predictive modeling can help banks **proactively identify churn risk** and design targeted interventions.  

---

## 🛠️ Tech Stack  
- **Python** (Pandas, NumPy, Matplotlib, Seaborn)  
- **Scikit-learn** (Logistic Regression, Random Forest Classifier, preprocessing utilities)  
- **XGBoost**  
- **Jupyter Notebook**  

---

## 📦 Installation & Setup  

Clone the repository:  
```bash
git clone https://github.com/gabbyomekz/bank-customer-churn-prediction.git
cd bank-customer-churn-prediction
```
Install dependencies:
```bash
pip install -r requirements.txt
```
Run the notebook:
```bash
jupyter notebook bank_customer_churn_prediction.ipynb
```

---

## ✅ Future Improvements
- Hyperparameter tuning of Xgboost with GridSearchCV
- Feature importance analysis for business interpretability
- Deployment as a web app (e.g., Streamlit or Flask)
