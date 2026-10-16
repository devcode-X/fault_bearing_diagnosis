# ⚙️ Bearing Fault Diagnosis — ML-Based Industrial Equipment Health Monitoring with Cross-Load Generalization

> Vibration signal → ML classifier identifies bearing health state (normal, inner race fault, outer race fault, ball fault) — validated across different operating load conditions on the CWRU dataset.

![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=flat-square&logo=python&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat-square&logo=scikitlearn&logoColor=white)
![XGBoost](https://img.shields.io/badge/XGBoost-green?style=flat-square)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=flat-square&logo=jupyter&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-lightgrey?style=flat-square)

---

## 🎯 Overview

Industrial bearing failures cause \$1B+ in unplanned downtime annually. This project builds a **machine learning diagnostic system** using vibration signal features to classify bearing health states — and critically, tests **cross-load generalization**: does the model trained at load 0 still work at load 3?

Uses the **Case Western Reserve University (CWRU) Bearing Dataset** — the standard benchmark for bearing fault diagnosis research.

---

## 🔬 Fault Classes

| Class | Description |
|---|---|
| `Normal` | Healthy bearing |
| `Inner Race Fault` | Defect on inner raceway |
| `Outer Race Fault` | Defect on outer raceway |
| `Ball Fault` | Rolling element defect |

---

## ✨ Features

- 📊 **Time & Frequency Domain Features** — RMS, kurtosis, crest factor, FFT peaks
- 🤖 **Multiple Classifiers** — SVM, Random Forest, XGBoost, KNN compared
- 🔄 **Cross-Load Evaluation** — train on one load, test on another (domain shift analysis)
- 📈 **Confusion Matrices & ROC Curves** — full model evaluation suite
- 🧩 **Feature Importance Analysis** — SHAP values for interpretability

---

## 🛠️ Tech Stack

Python · scikit-learn · XGBoost · NumPy · SciPy · Pandas · Matplotlib · Seaborn · Jupyter

---

## 🚀 Quick Start

```bash
git clone https://github.com/devcode-X/fault_bearing_diagnosis
cd fault_bearing_diagnosis
pip install -r requirements.txt

# Download CWRU dataset (instructions in notebook)
jupyter notebook bearing_fault_diagnosis.ipynb
```
