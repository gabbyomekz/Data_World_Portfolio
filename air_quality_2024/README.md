# 🌍 Air Quality Prediction (2024)

This project analyzes global air quality data across six cities—Brasilia, Cairo, Dubai, London, New York, and Sydney—and builds machine learning models to predict the Air Quality Index (AQI).

---

## 🔗 Dataset
Source: [Air Quality 2024 Dataset](https://www.kaggle.com/datasets/youssefelebiary/air-quality-2024/data)

---

## 📌 Project Objectives
- Clean and preprocess global air quality data.
- Build regression models to predict numeric AQI values.
- Build classification models to predict AQI categories (e.g., Good, Moderate, Unhealthy).
- Compare model performances and visualize results.

---

## 🛠️ Workflow

### 1. Data Cleaning & Preprocessing
- Dropped `CO2` column (81.69% missing values).
- Converted `Date` column from object → datetime.
- Checked for duplicates, and scaled numerical features.

### 2. Regression Task (Predict AQI)
- **Features**: CO, NO₂, SO₂, O₃, PM2.5, PM10  
- **Target**: AQI (numeric value)  
- **Models Tested**:
  - Linear Regression
  - Decision Tree Regressor
  - Random Forest Regressor
  - Gradient Boosting Regressor
  - Support Vector Regressor

### 3. Classification Task (Predict AQI Category)
- **Features**: CO, NO₂, SO₂, O₃, PM2.5, PM10  
- **Target**: AQI Category (categorical label)  
- **Models Tested**:
  - Logistic Regression
  - Decision Tree Classifier
  - Random Forest Classifier
  - Gradient Boosting Classifier
  - Support Vector Machine
  - K-Nearest Neighbors

### 4. Evaluation
- **Regression Metrics**: R², RMSE, MAE  
- **Classification Metrics**: Accuracy, Precision, Recall, F1-score  
- Visualizations:
  - Confusion Matrix for classification
  - Actual vs. Predicted plots for regression

---

## 📊 Key Insights
- Dropping `CO2` was necessary due to high missingness (>80%).
- Pollutants like PM2.5, PM10, and NO₂ strongly influence AQI predictions.
- Ensemble methods (Random Forest, Gradient Boosting) generally outperformed simpler models.

---

## 🚀 How to Run

Clone the repository:
```bash
git clone https://github.com/gabbyomekz/Data_World_Portfolio.git
cd air_quality_2024
```

## Install Dependencies
```bash
pip install -r requirements.txt
```

## Run the notebook
```bash
jupyter notebook air_quality_prediction.ipynb
```

---
## ✅ Future Improvements
- Time-series forecasting of AQI trends.
- Deployment of best model as an API or dashboard.

---

## 📚 References
- Kaggle Dataset: Air Quality 2024


