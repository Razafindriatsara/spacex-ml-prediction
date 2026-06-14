# 🚀 SpaceX Falcon 9 Landing Prediction

> Predicting first-stage booster landing success using supervised machine learning — a complete end-to-end ML pipeline.

![Python](https://img.shields.io/badge/Python-3.10+-blue?logo=python)
![scikit-learn](https://img.shields.io/badge/scikit--learn-ML-orange?logo=scikit-learn)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?logo=jupyter)
![License](https://img.shields.io/badge/License-MIT-green)

---

## 📋 Project Overview

SpaceX drastically reduces launch costs by reusing Falcon 9 first-stage boosters. This project builds a binary classifier to predict whether a booster will land successfully — information that could be used to estimate launch cost and assess mission risk.

**Business question:** Can we predict Falcon 9 first-stage landing success from mission parameters alone?

---

## 🎯 Results

| Model | Cross-Val Accuracy | Test Accuracy |
|---|---|---|
| Logistic Regression | 84.6% | **83.3%** |
| Support Vector Machine | 84.8% | **83.3%** |
| K-Nearest Neighbors | 84.8% | **83.3%** |
| Decision Tree | 88.9% | 66.7% ⚠️ |

**Best model: Logistic Regression** — simplest model, no overfitting, tied for highest test accuracy.  
The Decision Tree showed overfitting (high CV score, low test score).

---

## 🛠️ Tech Stack

- **Python** — pandas, numpy, matplotlib, seaborn
- **Machine Learning** — scikit-learn (LogisticRegression, SVC, KNeighborsClassifier, DecisionTreeClassifier)
- **Model Selection** — GridSearchCV, cross-validation
- **Data** — SpaceX REST API + Wikipedia web scraping

---

## 📁 Project Structure

```
spacex-ml-prediction/
│
├── notebooks/
│   ├── 01_data_collection_api.ipynb       # SpaceX API data collection
│   ├── 02_data_collection_scraping.ipynb  # Wikipedia web scraping
│   ├── 03_data_wrangling.ipynb            # Cleaning & feature engineering
│   ├── 04_eda_sql.ipynb                   # Exploratory data analysis (SQL)
│   ├── 05_eda_visualization.ipynb         # EDA with charts
│   ├── 06_interactive_maps.ipynb          # Folium launch site maps
│   ├── 07_dashboard.ipynb                 # Plotly Dash dashboard
│   └── 08_ml_prediction.ipynb             # ← Main ML notebook
│
├── data/
│   └── spacex_launch_dash.csv
│
└── README.md
```

---

## 🔍 Pipeline

```
SpaceX API → Data Wrangling → EDA → Feature Engineering → GridSearchCV → Model Evaluation
```

1. **Data Collection** — REST API calls to `/launches/past`, `/rockets/{id}`, `/payloads/{id}`, `/launchpads/{id}`, `/cores/{id}`
2. **Data Wrangling** — Imputation, binary label creation (`Class`: 1=landed, 0=failed)
3. **EDA** — SQL queries, Seaborn visualizations, Folium maps
4. **ML** — 4 classifiers with GridSearchCV hyperparameter tuning
5. **Evaluation** — Confusion matrix, accuracy, cross-validation

---

## 🚀 Getting Started

```bash
git clone https://github.com/YOUR_USERNAME/spacex-ml-prediction
cd spacex-ml-prediction
pip install -r requirements.txt
jupyter notebook notebooks/08_ml_prediction.ipynb
```

---

## 📊 Key Findings

- Launch site **KSC LC-39A** had the highest success rate
- Higher payload mass correlates with higher landing success
- Orbits **ES-L1, GEO, HEO, SSO** showed 100% success in the dataset
- Logistic Regression and SVM generalize better than Decision Trees on this dataset

---

## 📜 Certificate

This project was completed as part of the **IBM Data Science Professional Certificate** (Coursera) — Applied Data Science Capstone.
