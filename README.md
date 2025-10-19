# BTW 2025 Data Science Challenge — Hourly Energy Price Forecasting

This repository contains my solution for the **BTW 2025 Data Science Challenge**, which asks participants to predict hourly day-ahead electricity prices in Germany.  

🗓️ **Challenge date to predict:** 18 February 2025  
📌 **Organized by:** Gesellschaft für Informatik (GI)  
📄 **Challenge page:** https://btw2025.gi.de/data-science-challenge :contentReference[oaicite:0]{index=0}  

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

Participants are tasked with forecasting **hourly day-ahead electricity prices** for a target date (Feb 18, 2025). The forecast consists of 24 hourly price values. The challenge encourages integrating domain knowledge, exploratory data analysis, and comparing different modeling strategies. :contentReference[oaicite:1]{index=1}  

Submissions require three artifacts:

1. A **PDF report** (narrative, methods, results)  
2. A **CSV** file containing the 24 predicted hourly prices  
3. A **ZIP archive** with the Jupyter notebook and any extra files/artifacts :contentReference[oaicite:2]{index=2}  

This repository documents my full end-to-end pipeline: data ingestion → preprocessing → modeling → evaluation → prediction.

---

## 🗂 Repository Structure

Here’s a high-level view of the folder layout:

```
.
├── config/
│ └── config.yaml # Hyperparameters, file paths, experiment settings
├── data/
│ ├── raw/ # Raw/untouched data files (CSV, etc.)
│ └── processed/ # Preprocessed, transformed datasets
├── src/
│ ├── data/ # Data loading & preprocessing
│ ├── models/ # Machine learning models, training/evaluation scripts
│ ├── utils/ # Helper functions (metrics, MLflow logging, etc.)
│ └── visualization/ # Code to visualize predictions vs. truth, error plots
├── scripts/ # Command-line scripts (preprocess, train, evaluate)
├── experiments/ # Experiment logs, model checkpoints, results
├── requirements.txt
└── README.md

```