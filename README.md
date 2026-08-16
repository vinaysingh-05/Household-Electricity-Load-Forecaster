<div align="center">

⚡ Energy Consumption Prediction
End-to-End Machine Learning Regression Pipeline
<p> <img src="https://img.shields.io/badge/Python-3.13+-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python"> <img src="https://img.shields.io/badge/Scikit--Learn-ML-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white" alt="Scikit-Learn"> <img src="https://img.shields.io/badge/XGBoost-Boosting-189AB4?style=for-the-badge" alt="XGBoost"> <img src="https://img.shields.io/badge/LightGBM-Boosting-9ACD32?style=for-the-badge" alt="LightGBM"> <img src="https://img.shields.io/badge/CatBoost-Boosting-FFCC00?style=for-the-badge" alt="CatBoost"> </p>

<p> A robust regression project for predicting <b>Global Active Power</b> from household energy-consumption data. The project follows a complete ML workflow from data cleaning and cross-validation to ensemble learning, hyperparameter tuning, final evaluation, and model persistence. </p>

</div>

🧭 Project Navigation
<details open> <summary><b>📌 Quick Links</b></summary>

🎯 Problem Statement

✨ Key Features

🏗️ ML Workflow

🧹 Data Preprocessing

🤖 Models

📊 Evaluation

🔀 Ensemble Learning

🎛️ Hyperparameter Tuning

💾 Model Persistence

📁 Project Structure

⚙️ Installation

🚀 Running the Project

🛠️ Tech Stack

🔮 Future Improvements

</details>

🎯 Problem Statement
Accurately predicting energy consumption is important for:

⚡ Energy management

🏠 Smart-home optimization

🌐 Smart-grid planning

📈 Consumption forecasting

💰 Resource and cost optimization

Real-world energy datasets can contain:

Missing values

Invalid strings such as ?

Object-typed numerical columns

Redundant features

Features that may cause target leakage

The objective of this project is to build a reliable regression workflow capable of handling these challenges while comparing multiple machine-learning algorithms.

✨ Key Features
Feature	Implementation
🧹 Data Cleaning	Numeric conversion + missing-value handling
🎯 Target	Global_active_power
✂️ Train/Test Split	80/20
🔁 Cross-Validation	5-Fold K-Fold
📏 Scaling	StandardScaler for scale-sensitive models
🤖 Regression Models	10+ algorithms
🔀 Ensemble Learning	Voting + Stacking
🎛️ Hyperparameter Tuning	Grid Search + Randomized Search
📊 Metrics	MAE, RMSE, R²
💾 Persistence	joblib
🚀 Deployment Ready	Saved trained model for inference
🏗️ ML Workflow
                 ┌──────────────────────┐
                 │   Raw Energy Data    │
                 └──────────┬───────────┘
                            │
                            ▼
                 ┌──────────────────────┐
                 │ Data Cleaning        │
                 │ ? → NaN              │
                 │ Object → Numeric     │
                 └──────────┬───────────┘
                            │
                            ▼
                 ┌──────────────────────┐
                 │ Feature Selection    │
                 │ Target Separation    │
                 └──────────┬───────────┘
                            │
                            ▼
                 ┌──────────────────────┐
                 │ Train / Test Split   │
                 │       80 / 20        │
                 └──────────┬───────────┘
                            │
                            ▼
              ┌─────────────────────────────┐
              │      Model Development      │
              └─────────────┬───────────────┘
                            │
             ┌──────────────┴──────────────┐
             ▼                             ▼
      ┌───────────────┐             ┌───────────────┐
      │ Scaled Models │             │ Tree Models   │
      └───────┬───────┘             └───────┬───────┘
              │                             │
              └──────────────┬──────────────┘
                             ▼
                    ┌─────────────────┐
                    │  5-Fold CV      │
                    └────────┬────────┘
                             ▼
                    ┌─────────────────┐
                    │ Model Comparison│
                    └────────┬────────┘
                             ▼
                    ┌─────────────────┐
                    │ Hyperparameter  │
                    │    Tuning       │
                    └────────┬────────┘
                             ▼
                    ┌─────────────────┐
                    │ Voting /        │
                    │ Stacking        │
                    └────────┬────────┘
                             ▼
                    ┌─────────────────┐
                    │ Final Test      │
                    │ Evaluation      │
                    └────────┬────────┘
                             ▼
                    ┌─────────────────┐
                    │ Save Model      │
                    │    (.pkl)       │
                    └─────────────────┘
🧹 Data Preprocessing
1. Type Conversion
Numerical columns are converted from object to numeric values.

Invalid values such as:

?
are converted into:

NaN
2. Missing Value Handling
Missing numerical values are handled using column-wise statistical imputation.

3. Feature Separation
Target:

Global_active_power
Removed from features:

Global_active_power
Date
Time
Voltage
Note: Preprocessing steps that learn statistics from data should ideally be fitted only on the training data to prevent data leakage. For production use, place learned preprocessing operations inside the training pipeline.

🤖 Models
📏 Scale-Sensitive Models
These models use StandardScaler:

Linear Regression

Ridge Regression

Lasso Regression

ElasticNet Regression

KNN Regressor

Support Vector Regressor (SVR)

🌳 Tree-Based Models
These models do not require feature scaling:

Decision Tree Regressor

Random Forest Regressor

Gradient Boosting Regressor

AdaBoost Regressor

XGBoost Regressor

LightGBM Regressor

CatBoost Regressor

📊 Evaluation
The project evaluates models using three primary regression metrics.

MAE — Mean Absolute Error
Measures the average absolute difference between actual and predicted values.

Lower is better.

RMSE — Root Mean Squared Error
Penalizes larger prediction errors more strongly.

Lower is better.

R² Score
Measures how much variance in the target is explained by the model.

Higher is better.

Example evaluation:

print("MAE:", mean_absolute_error(y_test, y_pred))
print("RMSE:", mean_squared_error(y_test, y_pred) ** 0.5)
print("R2:", r2_score(y_test, y_pred))
🔀 Ensemble Learning
The project also experiments with ensemble regression.

🗳️ Voting Regressor
Combines predictions from multiple base regressors.

Model 1 ──┐
Model 2 ──┼──► Voting ──► Final Prediction
Model 3 ──┘
🧠 Stacking Regressor
Uses predictions from base models as inputs to a final meta-model.

Linear Regression ──┐
                    │
Ridge Regression ───┼──► Meta Model ──► Prediction
                    │
Other Models ───────┘
The initial ensemble experiments use strong linear base learners such as:

Linear Regression

Ridge Regression

🎛️ Hyperparameter Tuning
After baseline model comparison, promising models can be optimized using:

GridSearchCV
Tests a predefined parameter grid.

GridSearchCV(
    estimator=model,
    param_grid=params,
    cv=5,
    scoring="r2"
)
RandomizedSearchCV
Randomly samples combinations from the defined search space.

This can be significantly faster when the hyperparameter space is large.

🔁 Cross-Validation
A 5-Fold K-Fold Cross-Validation strategy is used during model development.

KFold(
    n_splits=5,
    shuffle=True,
    random_state=42
)
Conceptually:

Fold 1 → Train Train Train Train | Validate
Fold 2 → Train Train Train | Validate | Train
Fold 3 → Train Train | Validate | Train Train
Fold 4 → Train | Validate | Train Train Train
Fold 5 → Validate | Train Train Train Train
This gives a more reliable estimate of model performance than relying on a single validation split.

💾 Model Persistence
The final tuned model is serialized using joblib.

Example:

import joblib

joblib.dump(model, "models/final_model.pkl")
Load it later:

model = joblib.load("models/final_model.pkl")
This makes the trained model reusable for deployment and future predictions.

📁 Project Structure
Energy-Consumption-Prediction/
│
├── data/
│   ├── processed/
│   │   └── preprocessed.csv
│   │
│   └── test data/
│       ├── X_test.csv
│       └── y_test.csv
│
├── models/
│   └── final_model.pkl
│
├── notebooks/
│   └── models_train.ipynb
│
├── .gitignore
├── README.md
└── requirements.txt
⚙️ Installation
1. Clone the repository
git clone <YOUR_REPOSITORY_URL>
cd Energy-Consumption-Prediction
2. Create a virtual environment
python -m venv venv
3. Activate it
Windows:

venv\Scripts\activate
Linux / macOS:

source venv/bin/activate
4. Install dependencies
pip install pandas numpy scikit-learn xgboost lightgbm catboost joblib matplotlib seaborn jupyter
🚀 Running the Project
Launch Jupyter Notebook:

jupyter notebook
Then open:

notebooks/models_train.ipynb
Run the notebook cells sequentially.

🛠️ Tech Stack
Category	Technologies
Language	Python
Data Processing	Pandas, NumPy
Visualization	Matplotlib, Seaborn
ML	Scikit-Learn
Boosting	XGBoost, LightGBM, CatBoost
Validation	K-Fold Cross-Validation
Tuning	GridSearchCV, RandomizedSearchCV
Persistence	Joblib
Development	Jupyter Notebook
🔐 Reproducibility
The project uses fixed random seeds where applicable:

random_state=42
This helps make experiments reproducible across runs.

📈 Project Highlights
                 ENERGY ML PIPELINE
                         │
       ┌─────────────────┼─────────────────┐
       ▼                 ▼                 ▼
   DATA CLEANING     MODEL TRAINING    VALIDATION
       │                 │                 │
       ▼                 ▼                 ▼
 Missing Values      10+ Models         5-Fold CV
 Type Conversion     Ensembles          MAE/RMSE/R²
       │                 │                 │
       └─────────────────┼─────────────────┘
                         ▼
                  MODEL SELECTION
                         │
                         ▼
                 HYPERPARAMETER
                     TUNING
                         │
                         ▼
                 FINAL MODEL
                         │
                         ▼
                   JOBLIB MODEL
                         │
                         ▼
                    DEPLOYMENT
🔮 Future Improvements
Add time-series feature engineering

Add lag and rolling-window features

Compare chronological split with random split

Add Optuna-based hyperparameter optimization

Add SHAP-based model explainability

Build a Streamlit prediction interface

Create FastAPI inference endpoint

Add automated model monitoring

Add CI/CD workflow

Containerize the application with Docker

⚠️ Important ML Consideration
Energy consumption is inherently time-dependent.

For a real forecasting system, random K-Fold validation may not represent deployment conditions accurately because future observations should not influence training of past observations.

A stronger production setup would consider:

Chronological Data
       ↓
Time-Based Train/Test Split
       ↓
TimeSeriesSplit
       ↓
Lag Features
       ↓
Rolling Statistics
       ↓
Model Training
       ↓
Future Forecast
Therefore, this repository currently represents a general regression modeling workflow, while a true forecasting version should use time-aware validation and feature engineering.

📜 License
This project is intended for educational, experimentation, and portfolio purposes.

<div align="center">

⚡ Built with Python & Machine Learning
Data → Cleaning → Models → Validation → Tuning → Ensemble → Deployment

</div>

