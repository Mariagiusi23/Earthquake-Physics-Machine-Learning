# 🌍 Machine Learning to Extract Regime Information from the Pollino Seismic Catalog

![Python](https://img.shields.io/badge/python-3.11-blue)
![License](https://img.shields.io/badge/license-MIT-green)

**Author**: Mariagiusi Nicodemo  
**Email**: nicodemo.2114171@studenti.uniroma1.it  
**Course**: Earthquake Physics \& Machine Learning (a.y. 2025/2026) — Sapienza University of Rome


This repository contains the code, data processing pipeline, and documentation for a final project developed within the course **Earthquake Physics & Machine Learning**.

The project investigates whether temporal patterns in real seismic catalogs can be exploited to probabilistically classify short-term seismic activity regimes using supervised machine learning techniques.

---

## 🧠 Project Overview

Deterministic earthquake prediction remains an unsolved problem due to the complexity of fault systems and the intrinsic variability of seismic processes.  
Rather than attempting to forecast individual earthquakes, this project focuses on the **classification of seismic activity regimes** (high vs low activity) on short time scales.

Using a regional seismic catalog from the Pollino area (Southern Italy), the study evaluates whether historical seismicity contains exploitable predictive information when analyzed through a **time-aware machine learning framework**.

---

## 🎯 Scientific Objectives

- 🔍 Assess the presence of predictive information in real seismic catalogs  
- 📈 Identify temporal patterns associated with elevated seismic activity  
- 🤖 Compare linear and non-linear machine learning models  
- ⏳ Ensure strict temporal causality and avoid information leakage  
- ⚠️ Discuss intrinsic limitations related to data scarcity and noise  

---

## 🗂️ Dataset

- Regional seismic catalog retrieved via **FDSN web services**
- Event-based data including:
  - ⏱️ origin time
  - 📊 magnitude
- Catalog aggregated on a **weekly basis**
- Weeks with zero events explicitly retained to preserve temporal continuity

---

## 🛠️ Feature Engineering

Physically motivated features are extracted from the weekly aggregated catalog, including:

- 📉 Seismic rate (number of events per week)
- 🔁 Rolling averages over multiple time windows (4, 8, 12 weeks)
- 📐 Magnitude statistics (mean, maximum)
- 📏 Gutenberg–Richter **b-value**, estimated via maximum likelihood on rolling windows

All features are computed using **only past information**, ensuring strict temporal causality.

---

## 🧩 Problem Formulation

- ✅ **Supervised binary classification**
- 📥 Input: features at week *t*
- 📤 Target: seismic activity regime at week *t + 1*
- 🔀 Activity regimes defined via a **quantile-based threshold**, computed exclusively on the training set

---

## 🤖 Machine Learning Models

The following models are implemented and compared:

- Logistic Regression (baseline)
- 🌲 Tree-based ensemble models (e.g. Random Forest / Gradient Boosting)

Class imbalance is handled during training, and all models are evaluated using a **chronological train–test split**.

---

## 📊 Evaluation Metrics

Model performance is assessed on a held-out test set using:

- Precision
- Recall
- F1-score
- 📈 ROC–AUC
- Confusion matrix analysis

---

## ⭐ Key Results

- ✅ Ensemble models outperform the linear baseline  
- 📊 Stable discrimination between high- and low-activity regimes  
- 🔎 Rate-based and temporally aggregated features provide the strongest contribution  
- 🧪 Results highlight the presence of **probabilistic predictive information**, while confirming the limits of catalog-based approaches  

---

## ⚠️ Limitations

- 🌍 Analysis restricted to a single seismic region  
- 🕒 Weekly aggregation represents a compromise between resolution and stability  
- 📐 Regime definition is data-driven  
- 🧩 Models are purely data-driven and do not incorporate explicit physical constraints  


---
## 🔗 Project Materials

- 📓 **Code (Colab Notebook)**  
  👉 [View notebook](./notebook/eqxml_project.ipynb)

- 📊 **Presentation (PowerPoint)**  
  👉 [View slides](./presentation/presentation_project.pdf)

- 📄 **Final Report (PDF)**  
  👉 [Read the report](./paper/Final_Report.pdf)
---

## ❗ Disclaimer

This project does **not** aim to provide deterministic earthquake predictions.  
All results should be interpreted as **probabilistic and exploratory**, consistent with the intrinsic uncertainty of seismic processes.

