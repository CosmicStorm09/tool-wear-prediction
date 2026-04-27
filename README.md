# Tool Wear Prediction using Machine Learning

[![Intel Unnati](https://img.shields.io/badge/Intel%20Unnati-AI%20for%20Mechanical%20Engineers-blue?logo=intel)](https://www.intel.com/content/www/us/en/developer/tools/devcloud/edge/learn/unnati.html)
[![Python](https://img.shields.io/badge/Python-3.10-blue?logo=python)](https://www.python.org/)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-1.4-orange?logo=scikit-learn)](https://scikit-learn.org/)
[![Google Colab](https://img.shields.io/badge/Run%20on-Google%20Colab-yellow?logo=googlecolab)](https://colab.research.google.com/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green)](LICENSE)

> **Intel Unnati: AI for Mechanical Engineers | Batch 1 | Group 5**  
> Manipal Institute of Technology, Manipal – 576104

---

## 👥 Team

| Registration No. | Name | Department |
|---|---|---|
| 220909420 | Harsh More | Mechanical Engineering |
| 230909150 | Samagya Sharma | Mechanical Engineering |

---

## 📌 Project Overview

Tool wear is a critical issue in manufacturing — as cutting tools degrade, machined component accuracy drops and the risk of tool failure rises. This project builds and compares **5 supervised machine learning regression models** to predict tool wear (in mm) from real-time machining parameters such as spindle speed, vibration, cutting force, and temperature.

The best model — **Random Forest Regressor** — achieved an **R² of 0.9914** and an **RMSE of just 0.00188 mm**.

---

## 📂 Repository Structure

```
tool-wear-prediction/
│
├── tool_wear_prediction.py        # Main ML pipeline (EDA → training → evaluation → plots)
├── Tool_wear_dataset.csv          # Dataset (501 samples, 8 features)
│
├── plots/                         # Generated output plots
│   ├── eda_feature_distributions.png
│   ├── eda_correlation_heatmap.png
│   ├── eda_coating_vs_wear.png
│   ├── results_model_comparison.png
│   ├── results_actual_vs_predicted.png
│   ├── results_residual_plot.png
│   └── results_feature_importance.png
│
├── report/
│   └── Tool_Wear_Prediction_Report_Group5.docx   # Full project report
│
├── requirements.txt               # Python dependencies
└── README.md
```

---

## 📊 Dataset

| Feature | Description | Type |
|---|---|---|
| `Spindle_Speed_RPM` | Spindle rotation speed | Numerical |
| `Feed_mm_per_rev` | Feed rate in mm per revolution | Numerical |
| `Depth_of_Cut_mm` | Depth of cut in mm | Numerical |
| `Vibration_m_s2` | Vibration in m/s² | Numerical |
| `Cutting_Force_N` | Cutting force in Newtons | Numerical |
| `Temperature_C` | Tool temperature in °C | Numerical |
| `Tool_Coating` | Coating type (TiN, TiAlN, DLC, Uncoated) | Categorical |
| `Tool_Wear_mm` | **Target** – Tool wear in mm | Numerical |

- **501 samples**, no missing values
- Target range: 0.21 mm – 0.35 mm

---

## 🤖 Models Compared

| Model | MAE (mm) | RMSE (mm) | R² Score |
|---|---|---|---|
| **Random Forest** ⭐ | 0.00148 | 0.00188 | **0.9914** |
| Gradient Boosting | 0.00261 | 0.00370 | 0.9910 |
| Ridge Regression | 0.00321 | 0.00505 | 0.9832 |
| Linear Regression | 0.00322 | 0.00508 | 0.9829 |
| SVR (RBF) | 0.00612 | 0.00607 | 0.9755 |

---

## 📈 Key Results

### Actual vs Predicted (Random Forest)
![Actual vs Predicted](plots/results_actual_vs_predicted.png)

### Feature Importance
![Feature Importance](plots/results_feature_importance.png)

**Cutting Force (N)** and **Vibration (m/s²)** are the two dominant predictors, together accounting for ~70% of the model's decision making.

---

## ⚡ Intel Acceleration (sklearnex)

This project also demonstrates **Intel® Extension for Scikit-learn** for hardware-accelerated training on the MIT Intel server (via MobaXterm):

```python
from sklearnex import patch_sklearn
patch_sklearn()

# All subsequent sklearn calls now use Intel-optimized routines — no other changes needed!
```

This single-line patch transparently replaces sklearn estimators with Intel-optimised equivalents, providing measurable speedup on Intel hardware compared to standard Google Colab execution.

---

## 🚀 How to Run

### Prerequisites
```bash
pip install -r requirements.txt
```

### Run the pipeline
```bash
python tool_wear_prediction.py
```

All 7 plots will be saved in the current directory. Make sure `Tool_wear_dataset.csv` is in the same folder.

---

## 📦 requirements.txt

```
pandas
numpy
matplotlib
seaborn
scikit-learn
```

---

## 🎓 Course Info

**Intel Unnati: AI for Mechanical Engineers**  
Conducted by: Intel & EdGate Technologies  
Institution: Manipal Institute of Technology, Manipal  
Mentor: Raghavendra Kamath C [MAHE-MIT]  
Submission Date: April 30, 2026
