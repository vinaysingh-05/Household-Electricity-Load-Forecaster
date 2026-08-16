<div align="center">

⚡ Energy Consumption Prediction

An End-to-End Machine Learning Regression System

<p>
  <a href="#-overview">Overview</a> •
  <a href="#-workflow">Workflow</a> •
  <a href="#-models">Models</a> •
  <a href="#-evaluation">Evaluation</a> •
  <a href="#-installation">Installation</a> •
  <a href="#-usage">Usage</a>
</p>

<p>
  <img src="https://img.shields.io/badge/Python-3.13+-3776AB?style=for-the-badge&logo=python&logoColor=white">
  <img src="https://img.shields.io/badge/Scikit--Learn-ML-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white">
  <img src="https://img.shields.io/badge/XGBoost-Boosting-189AB4?style=for-the-badge">
  <img src="https://img.shields.io/badge/LightGBM-Boosting-9ACD32?style=for-the-badge">
  <img src="https://img.shields.io/badge/CatBoost-Boosting-FFCC00?style=for-the-badge">
  <img src="https://img.shields.io/badge/Status-Active-success?style=for-the-badge">
</p>

<p>
  <b>Predicting Global Active Power with a complete, reproducible ML workflow.</b>
</p>

</div>

---

<table>
<tr>
<td align="center">🧹<br><b>Data Cleaning</b><br>Dirty values → numeric</td>
<td align="center">📏<br><b>Preprocessing</b><br>Scaling where needed</td>
<td align="center">🤖<br><b>10+ Models</b><br>Regression comparison</td>
</tr>
<tr>
<td align="center">🔁<br><b>5-Fold CV</b><br>Robust validation</td>
<td align="center">🎛️<br><b>Hyperparameter Tuning</b><br>Grid + Random Search</td>
<td align="center">🔀<br><b>Ensembles</b><br>Voting + Stacking</td>
</tr>
<tr>
<td align="center">📊<br><b>Metrics</b><br>MAE • RMSE • R²</td>
<td align="center">💾<br><b>Persistence</b><br>Joblib</td>
<td align="center">🚀<br><b>Deployment Ready</b><br>Reusable model</td>
</tr>
</table>

---
## 📊 Dataset

<details>
<summary><b>🔍 Dataset Overview</b></summary>

This project uses a household electricity consumption dataset containing multiple measurements related to energy usage.
</details>

### 🎯 Prediction Target

```text
Global_active_power

🔁 Complete Architecture

                         ⚡ ENERGY DATA
                               │
                               ▼
                    ┌─────────────────────┐
                    │    DATA CLEANING    │
                    │                     │
                    │  ?  →  NaN          │
                    │  Object → Numeric   │
                    │  Missing Values     │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │ FEATURE SELECTION   │
                    │       + TARGET      │
                    │      SEPARATION     │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │  TRAIN / TEST SPLIT │
                    │       80 / 20       │
                    └──────────┬──────────┘
                               │
                    ┌──────────┴──────────┐
                    ▼                     ▼
             📏 SCALED MODELS       🌳 TREE MODELS
                    │                     │
                    ▼                     ▼
              StandardScaler         Direct Fit
                    │                     │
                    └──────────┬──────────┘
                               ▼
                     🔁 5-FOLD CV
                               │
                               ▼
                     📊 MODEL COMPARISON
                               │
                               ▼
                     🎛️ HYPERPARAMETER
                          TUNING
                               │
                    ┌──────────┴──────────┐
                    ▼                     ▼
                 🗳️ VOTING            🧠 STACKING
                    │                     │
                    └──────────┬──────────┘
                               ▼
                       🏆 FINAL MODEL
                               │
                               ▼
                       📊 TEST METRICS
                               │
                               ▼
                         💾 JOBLIB
                               │
                               ▼
                         🚀 INFERENCE

---

📊 End-to-End Summary

             ┌──────────────────────┐
             │   ⚡ ENERGY DATA     │
             └──────────┬───────────┘
                        ▼
             ┌──────────────────────┐
             │    🧹 CLEAN DATA     │
             └──────────┬───────────┘
                        ▼
             ┌──────────────────────┐
             │ 🎯 SELECT FEATURES   │
             └──────────┬───────────┘
                        ▼
             ┌──────────────────────┐
             │ ✂️ TRAIN / TEST      │
             └──────────┬───────────┘
                        ▼
             ┌──────────────────────┐
             │ 🤖 TRAIN MODELS      │
             └──────────┬───────────┘
                        ▼
             ┌──────────────────────┐
             │ 🔁 5-FOLD CV         │
             └──────────┬───────────┘
                        ▼
             ┌──────────────────────┐
             │ 📊 COMPARE MODELS    │
             └──────────┬───────────┘
                        ▼
             ┌──────────────────────┐
             │ 🎛️ TUNE BEST MODELS  │
             └──────────┬───────────┘
                        ▼
             ┌──────────────────────┐
             │ 🔀 VOTING/STACKING   │
             └──────────┬───────────┘
                        ▼
             ┌──────────────────────┐
             │ 🏆 FINAL EVALUATION  │
             └──────────┬───────────┘
                        ▼
             ┌──────────────────────┐
             │ 💾 SAVE MODEL        │
             └──────────┬───────────┘
                        ▼
             ┌──────────────────────┐
             │ 🚀 FUTURE INFERENCE  │
             └──────────────────────┘

```

<div align="center">

⚡ Energy Consumption Prediction

Data → Models → Validation → Tuning → Ensemble → Deployment

Built with Python & Machine Learning

</div>
