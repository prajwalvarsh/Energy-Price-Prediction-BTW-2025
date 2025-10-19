# BTW 2025 Data Science Challenge — Hourly Energy Price Forecasting
This was part of the course (M.Sc International Software System Science) @ Uni-Bamberg

This repository contains my solution for the **BTW 2025 Data Science Challenge**, which asks participants to predict hourly day-ahead electricity prices in Germany.  

🗓️ **Challenge date to predict:** 18 February 2025  
📌 **Organized by:** Gesellschaft für Informatik (GI)  
📄 **Challenge page:** https://btw2025.gi.de/data-science-challenge 

---

## 📋 Table of Contents

- [Challenge Overview](#challenge-overview)  
- [Repository Structure](#repository-structure)  
- [Installation & Setup](#installation--setup)  
- [Data & Preprocessing](#data--preprocessing)  
- [Modeling Approach](#modeling-approach)  
- [Experiments & Tracking](#experiments--tracking)  
- [Evaluation & Results](#evaluation--results)  
- [How to Reproduce](#how-to-reproduce)  
- [Future Work](#future-work)  
- [References](#references)  

---

## 🎯 Challenge Overview

Participants are tasked with forecasting **hourly day-ahead electricity prices** for a target date (Feb 18, 2025). The forecast consists of 24 hourly price values. The challenge encourages integrating domain knowledge, exploratory data analysis, and comparing different modeling strategies. 

Submissions require three artifacts: (only if participating in the competition)

1. A **PDF report** (narrative, methods, results)  
2. A **CSV** file containing the 24 predicted hourly prices  
3. A **ZIP archive** with the Jupyter notebook and any extra files/artifacts   

This repository documents my full end-to-end pipeline: data ingestion → preprocessing → modeling → evaluation → prediction.

---

## 🗂 Repository Structure

Here’s a high-level view of the folder layout:

```
.
├── config/
│ └── config.yaml       # Hyperparameters, file paths, experiment settings
├── data/
│ ├── raw/              # Raw/untouched data files (CSV, etc.)
│ └── processed/        # Preprocessed, transformed datasets
├── src/
│ ├── data/             # Data loading & preprocessing
│ ├── models/           # Machine learning models, training/evaluation scripts
│ ├── utils/            # Helper functions (metrics, MLflow logging, etc.)
│ └── visualization/    # Code to visualize predictions vs. truth, error plots
├── scripts/            # Command-line scripts (preprocess, train, evaluate)
├── experiments/        # Experiment logs, model checkpoints, results
├── requirements.txt
└── README.md

```


Each component is modular to allow reproducibility, ease of extension, and comparative experiments.

---

## 🧰 Installation & Setup

1. **Activate your virtual environment** (or create one)

```
uv venv btw
```

```
btw\Scripts\activate
```

2. **Install dependencies**:  
```
uv add -r requirements.txt
```
(Or pip install -r requirements.txt if you’re using pip)

# 3. **Set up MLflow (optional, for experiment tracking):**

```
uv run mlflow ui
```

Then browse to http://127.0.0.1:5000

# 4. **Prepare directory structure:**

Place raw input CSV(s) in data/raw/

Ensure config/config.yaml paths match your file setup

## 📊 Data & Preprocessing

The raw dataset is loaded and time-indexed.

I perform data cleaning (handling missing or anomalous values).

Feature engineering includes incorporating exogenous variables (e.g. generation by renewables, load forecasts) and temporal features (hour, weekday, etc.).

Scaling/normalization is done to ensure features are comparable.

I then window the data into sequences (e.g. lookback of 24 hours) for supervised learning.

Intermediate outputs (train/val/test splits, feature matrices) are saved in data/processed/, often in .npz or .npy format for fast loading.

## 💡 Modeling Approach

Instead of only using LSTM (as in earlier versions which was submitted as my project submission), I also experiment with classical machine learning models, such as:

Linear Regression / Ridge / Lasso

Random Forest Regressor

Gradient Boosting (e.g. XGBoost, LightGBM)

Support Vector Regression

I built a model factory to instantiate models via configuration, and a training script that logs metrics and model artifacts to MLflow.

Hyperparameters, feature sets, and experiment keys are all configurable via config.yaml.

## 📈 Experiments & Tracking

Each model run is tracked as an MLflow experiment/run, logging:

Hyperparameters (e.g. number of trees, max depth)

Metrics (MAE, RMSE, MAPE, R²)

Model artifacts (serialized model object)

Feature importance plots, error distributions

You can compare runs visually via the MLflow UI.

The best-performing model (on validation/test) is saved as the final checkpoint for prediction.

## 📐 Evaluation & Results

The models’ performance is reported on a held-out test set (never seen during training).

Metrics include: MAE, RMSE, MAPE.

Visualizations include:

Predicted vs actual price curves

Error histograms

Feature importance rankings

These help diagnose model behavior, overfitting, and possible improvements.