# 🩺 Clinical Insights: A Diabetes Prediction Study

> Predicting the onset of diabetes based on diagnostic data using supervised machine learning.

---

## 📌 About the Project

Diabetes is one of the fastest growing health problems in the world today. Millions of people are affected every year and many of them do not even know they have it until serious complications develop.

In this project, I built a machine learning model that predicts whether a person is likely to develop diabetes based on their medical diagnostic data like glucose level, BMI, age and insulin. The model was built using Python and trained on a dataset of 768 female patients.

This project was completed as part of a **Mentor Led Internship** certified by **St James School of Medicine**.

---

## 🎯 Objective

Build a classification model that can accurately predict the onset of diabetes in a patient based on their routine medical diagnostic measurements.

---

## 🗂️ Project Structure

```
diabetes-prediction/
│
├── diabetes.ipynb       # Main Jupyter Notebook (complete project)
├── diabetes.csv         # Dataset
└── README.md            # Project documentation
```

---

## 📊 Dataset

The dataset contains diagnostic measurements of female patients along with whether they developed diabetes or not.

| Feature | Description |
|---|---|
| Pregnancies | Number of times pregnant |
| Glucose | Blood sugar level (mg/dL) |
| BloodPressure | Diastolic blood pressure (mmHg) |
| SkinThickness | Skinfold thickness (mm) |
| Insulin | Insulin level (µU/mL) |
| BMI | Body mass index |
| DiabetesPedigreeFunction | Family history score |
| Age | Age of patient |
| Outcome | 0 = Non-Diabetic, 1 = Diabetic |

**Total Records :** 768 patients
**Class Distribution :** 65% Non-Diabetic | 35% Diabetic

---

## 🔁 Project Workflow

### Step 1 — Data Loading
- Loaded dataset using Pandas

### Step 2 — Basic Data Exploration
- Checked shape, info, describe
- Found class imbalance (65-35)

### Step 3 — Data Cleaning
- Identified biologically impossible zero values in 5 medical columns
- Replaced zeros with column median using domain knowledge
- Investigated outliers individually using medical reference ranges
- Retained all 768 rows — no data deleted

### Step 4 — Outlier Treatment
- Used boxplots to detect outliers
- Investigated 4 rows with Insulin > 600 — all retained as medically genuine
- Fixed 1 row with SkinThickness = 99 (contradicted BMI of 34.7)

### Step 5 — Exploratory Data Analysis
- Feature distributions using histograms
- Class imbalance visualization
- Correlation heatmap
- Feature vs Outcome comparison
- Glucose vs BMI scatter plot

### Step 6 — Model Building
- Train/Test split : 80/20
- Trained 4 baseline models : Logistic Regression, KNN, Decision Tree, Random Forest
- Used class_weight='balanced' to handle class imbalance

### Step 7 — Feature Engineering
- Applied MinMax Scaler
- Applied Standard Scaler
- Compared accuracy across all scaling rounds
- Used Random Forest feature importance for feature selection
- Selected top 5 features : Glucose, BMI, Age, DiabetesPedigreeFunction, Insulin
- Ran models on top 5 features and compared results

### Step 8 — Model Evaluation
- Cross validation (5-fold) on best model
- Final model selection based on accuracy and stability

---

## 📈 Results

### Baseline Accuracy

| Model | Accuracy |
|---|---|
| Logistic Regression | 0.7013 |
| KNN | 0.6753 |
| Decision Tree | 0.7338 |
| **Random Forest** | **0.7597 ★** |

### Accuracy Across All Rounds

| Model | Baseline | MinMax | Standard | Top 5 Features |
|---|---|---|---|---|
| Logistic Regression | 0.7013 | 0.7078 | 0.7013 | 0.7078 |
| KNN | 0.6753 | 0.7338 | 0.7143 | 0.7403 |
| Decision Tree | 0.7338 | 0.7273 | 0.7273 | 0.7338 |
| **Random Forest** | **0.7597** | **0.7597** | **0.7597** | 0.7338 |

### Cross Validation (Random Forest — All 8 Features)

| Metric | Value |
|---|---|
| CV Scores | 0.7532, 0.7273, 0.7662, 0.8105, 0.7190 |
| Mean CV Accuracy | 0.7552 |
| Std of CV Scores | 0.0325 |

---

## 🏆 Final Model

**Random Forest Classifier with all 8 features**

**Why Random Forest :**
- Highest test accuracy of 75.97%
- Most stable across all experiment rounds
- Scaling had zero effect — model is robust
- Handles class imbalance well internally
- Handles feature selection internally
- Cross validation confirmed no overfitting

---

## 🔑 Key Findings

1. **Glucose** is the strongest predictor of diabetes with correlation of 0.49
2. **BMI** and **Age** are meaningful secondary predictors (0.31 and 0.24)
3. **BloodPressure** showed the weakest relationship with Outcome (0.17)
4. Dataset has a **65-35 class imbalance** — handled using class_weight='balanced'
5. **Feature selection helped KNN** but hurt Random Forest — because Random Forest already handles feature selection internally
6. **No multicollinearity** found between input features

---

## 🛠️ Tools and Technologies

| Tool | Purpose |
|---|---|
| Python | Main programming language |
| Pandas | Data loading and manipulation |
| NumPy | Numerical operations |
| Matplotlib | Data visualization |
| Seaborn | Statistical plots |
| Scikit-learn | Machine learning models and preprocessing |

---

## 🚀 How to Run

1. Clone the repository
```bash
git clone https://github.com/Strike-22/diabetes-prediction.git
```

2. Install required libraries
```bash
pip install pandas numpy matplotlib seaborn scikit-learn
```

3. Open the notebook
```bash
jupyter notebook diabetes.ipynb
```

4. Run all cells from top to bottom

---

## 📜 Certificate

This project is certified by **St James School of Medicine** as part of the MentorMind Mentor Led Internship Program.

---

## 👤 Author

**Atharv**
BSc IT Graduate | Data Science Enthusiast
upGrad Data Analytics & Data Science Program — Pune

---
