# 🚗 Car Price Prediction Project

## 📌 Overview
This project focuses on predicting car prices using a dataset from **CarDekho**.  
The notebook covers the entire **data science pipeline**, including:

- Data loading  
- Exploratory Data Analysis (EDA)  
- Data preprocessing  
- Feature engineering  
- Visualization  
- Machine learning model implementation  
- Model evaluation and interpretation  

---

## 📂 Project Structure
The notebook is organized into the following main sections:

1. **Importing Libraries**  
2. **Loading and Inspecting Data**  
3. **Data Cleaning and Preprocessing**  
4. **Exploratory Data Analysis (EDA)**  
5. **Feature Engineering**  
6. **Machine Learning Model Implementation**  
7. **Model Evaluation and Interpretation**

---

## 🔑 Key Steps and Explanations

### 1. Importing Libraries
Essential libraries for data manipulation, visualization, and machine learning are imported, including:

- `pandas`, `numpy` → Data handling  
- `matplotlib`, `seaborn` → Visualization  
- `scikit-learn` → Machine learning models and evaluation  

---

### 2. Loading and Inspecting Data
- Dataset: `cardekho.csv`  
- Initial inspection includes viewing the first few rows, checking datatypes, and handling missing values.  

**Why we can’t train with missing target values:**  
Missing values in the target variable (`selling_price`) would cause incomplete supervision. The model would not learn feature–target relationships properly, resulting in biased predictions.

---

### 3. Data Cleaning and Preprocessing
- Handling missing values (filling with mean for numeric columns).  
- Removing duplicates.  
- Converting columns like `max_power` to numeric.  

---

### 4. Feature Engineering
- **Car Age** → `car_age = current_year - year`  
- **Price per Kilometer** → `selling_price / mileage`  

---

### 5. Exploratory Data Analysis (EDA)
- **Boxplot of Selling Price** → Identified and removed outliers (only keeping prices between 10,000 and 5,000,000).  
- **Histogram of Selling Prices** → Right-skewed distribution (most cars at lower prices).  

**Why outliers matter:**  
Outliers can heavily influence model parameters, especially in linear models, leading to poor generalization. Removing them builds a more robust model.

---

### 6. Machine Learning Model Implementation
- **Target variable:** `selling_price`  
- **Features:** `year, km_driven, mileage, engine, max_power, seats, car_age, priceperkilometer`  
- **Categorical variables** (fuel, seller_type, transmission, owner) → Encoded with label encoding.  
- **Train-Test Split:** 80% train, 20% test  

**Models used:**
- Linear Regression → Baseline  
- Lasso Regression → Feature selection (shrinks coefficients)  
- Ridge Regression → Handles multicollinearity  

**Hyperparameter tuning:**  
- Done using `GridSearchCV` for best parameters (alpha values).

---

### 7. Model Evaluation and Interpretation
**Metrics used:**  
- Mean Squared Error (MSE)  
- R² score  

**Results:**
- **Linear Regression** → MSE: `2.16e+11`, R²: `0.67`  
- **Lasso Regression (alpha=1)** → MSE: `2.16e+11`, R²: `0.67`  
- **Ridge Regression (alpha=10)** → MSE: `2.16e+11`, R²: `0.67`  

**Interpretation:**
- All models performed similarly (`R² = 0.67`) → 67% of variance in car prices explained.  
- High MSE → Large prediction errors, possibly due to dataset complexity or non-linear patterns.  
- Lasso kept all features (none were eliminated), suggesting all features contribute to prediction.  

---

## ✅ Conclusion
- The models explain a good portion of car price variance but still leave room for improvement.  
- Feature engineering and advanced models (like **Random Forests, XGBoost, or Neural Networks**) could improve prediction accuracy.  
