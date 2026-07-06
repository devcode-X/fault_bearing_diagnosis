# 🔧 Bearing Fault Diagnosis using Machine Learning
### Cross-Load Generalization on the CWRU Bearing Dataset

![Python](https://img.shields.io/badge/Python-3.10+-blue.svg)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-ML-orange.svg)
![XGBoost](https://img.shields.io/badge/XGBoost-Enabled-green.svg)
![License](https://img.shields.io/badge/License-MIT-lightgrey.svg)

---

## 📖 Overview

This project performs **bearing fault diagnosis** using vibration signals from the **Case Western Reserve University (CWRU) Bearing Dataset**.

The objective is to classify four bearing health conditions:

- Normal
- Inner Race Fault
- Ball Fault
- Outer Race Fault

Unlike conventional studies, this project evaluates models under a **strict cross-load protocol**.

- **Training Loads:** 0 HP, 1 HP, 2 HP
- **Testing Load:** 3 HP (completely unseen during training)

This ensures the models are evaluated under realistic operating conditions rather than memorizing patterns from identical motor loads.

---

# 📂 Repository Structure

```
fault_bearing_diagnosis/
│
├── data/
│   ├── (28 downloaded .mat files)
│
├── Bearing_Fault_Diagnosis_Report (2).docx
│
├── bearing_fault_diagnosis_v22_machine_learning_....ipynb
│
├── test_purpose_very_detailed_analysis_for_knowl....
│
└── README.md
```

### Files

| File | Description |
|------|-------------|
| **data/** | Contains all downloaded CWRU `.mat` vibration files |
| **Bearing_Fault_Diagnosis_Report (2).docx** | Final project report and research summary |
| **bearing_fault_diagnosis_v22_machine_learning...ipynb** | Main notebook containing EDA, feature engineering, model training and evaluation |
| **test_purpose_very_detailed_analysis...** | Additional experimentation and analysis notebook |
| **README.md** | Project documentation |

---

# 📥 Dataset

Dataset Source:

**Case Western Reserve University Bearing Data Center**

https://engineering.case.edu/bearingdatacenter

Download the following **28 MATLAB (.mat) files**.

---

## Normal

- Normal_0
- Normal_1
- Normal_2
- Normal_3

---

## Inner Race

- IR007_0
- IR007_1
- IR007_2
- IR007_3
- IR021_0
- IR021_1
- IR021_2
- IR021_3

---

## Ball Fault

- B007_0
- B007_1
- B007_2
- B007_3
- B021_0
- B021_1
- B021_2
- B021_3

---

## Outer Race Fault

- OR007@6_0
- OR007@6_1
- OR007@6_2
- OR007@6_3
- OR021@6_0
- OR021@6_1
- OR021@6_2
- OR021@6_3

---

# 📁 Place Dataset

After downloading, place all files inside

```
data/
```

The structure should become

```
fault_bearing_diagnosis/

data/
    Normal_0.mat
    Normal_1.mat
    ...
    OR021@6_3.mat
```

---

# 🚀 Running the Project

## Option 1 — Google Colab (Recommended)

Upload the **data** folder to Google Drive.

Mount Drive:

```python
from google.colab import drive
drive.mount('/content/drive')
```

Set

```python
DATASET_PATH="/content/drive/MyDrive/your_folder/data"
```

---

## Option 2 — Google Colab (Without Drive)

Upload the **data** folder directly using the Files panel.

Then set

```python
DATASET_PATH="/content/data"
```

> Files uploaded directly to Colab are temporary and will disappear when the session ends.

---

## Option 3 — Local (VS Code / Jupyter)

Clone the repository

```bash
git clone https://github.com/your_username/fault_bearing_diagnosis.git
```

Open the notebook and set

```python
DATASET_PATH="./data"
```

---

# 📦 Installation

Install all required packages

```bash
pip install antropy
pip install nolds
pip install pywavelets
pip install shap
pip install xgboost
pip install scikit-learn
pip install pandas
pip install numpy
pip install scipy
pip install matplotlib
pip install seaborn
```

Or simply

```bash
pip install antropy nolds pywavelets shap xgboost scikit-learn pandas numpy scipy matplotlib seaborn
```

---

# 🔬 Project Pipeline

The notebook follows the following workflow.

---

## 1. Exploratory Data Analysis

- Raw vibration signal visualization
- FFT analysis
- Welch Power Spectral Density
- Spectrograms
- Statistical comparison

---

## 2. Feature Engineering

Each vibration window consists of **4096 samples**.

Features are extracted from

- Time Domain
- Frequency Domain
- Wavelet Domain
- Nonlinear Dynamics

A total of **44 engineered features** are generated.

Examples include

- RMS
- Kurtosis
- Crest Factor
- Spectral Entropy
- Spectral Centroid
- Wavelet Energy
- Lyapunov Exponent
- Shannon Entropy

---

## 3. Leakage-Free Validation

To avoid data leakage:

- Dataset is split before preprocessing.
- StandardScaler is fit only on training data.
- ANOVA feature selection is fit only on training data.
- Test load remains completely unseen.

---

## 4. Machine Learning Models

The notebook benchmarks multiple ML algorithms including

- Logistic Regression
- Random Forest
- Extra Trees
- Decision Tree
- Support Vector Machine
- K-Nearest Neighbors
- Naive Bayes
- XGBoost
- AdaBoost
- Gradient Boosting
- MLP Neural Network

Models are evaluated using

- Accuracy
- Precision
- Recall
- Macro F1 Score
- Confusion Matrix

---

## 5. Model Explainability

Includes

- SHAP Analysis
- Feature Importance
- Feature Ablation
- Noise Robustness Testing

---

# 📊 Results

## Best Models

- Logistic Regression
- Random Forest

### Hold-Out Performance

- **Macro F1 Score: 1.000**
- **0 Misclassifications**
- Evaluated on **Load 3 HP**, which was never seen during training.

---

## Research Findings

Although the models generalize extremely well across unseen motor loads, they struggle when evaluated across unseen fault sizes.

Training only on larger defects (0.021") causes severe performance degradation on smaller defects (0.007"), indicating that **fault severity dominates the learned feature space more strongly than fault category**.

Unsupervised K-Means clustering further supports this observation by grouping samples primarily according to defect size rather than fault type.

---

# 📈 Technologies Used

- Python
- NumPy
- Pandas
- SciPy
- Matplotlib
- Scikit-learn
- XGBoost
- SHAP
- PyWavelets
- Antropy
- Nolds

---

# 📄 Report

A detailed explanation of

- Dataset
- Feature Engineering
- Experimental Design
- Results
- SHAP Interpretation
- Research Discussion

is available in

```
Bearing_Fault_Diagnosis_Report (2).docx
```

---

# 📌 Highlights

- Cross-load evaluation
- Leakage-free preprocessing
- 44 handcrafted features
- Benchmarking of 11 ML algorithms
- SHAP explainability
- Noise robustness analysis
- Feature ablation study
- K-Means fault-size analysis
- 1.000 Macro F1 on unseen operating conditions

---

# ⭐ If you found this project useful, consider giving the repository a Star!
