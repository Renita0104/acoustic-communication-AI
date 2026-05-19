# 🌊 Thermo-Acoustic Ultrasonic Optimization System

[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![TensorFlow 2.13](https://img.shields.io/badge/tensorflow-2.13-orange.svg)](https://tensorflow.org)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

A high-precision machine learning platform designed to optimize **Ultrasonic Frequency** and **Power** parameters based on environmental variables. This system leverages deep neural networks to ensure peak acoustic performance in variable thermodynamic conditions.

---

## 🚀 Overview

Ultrasonic transducer efficiency is highly sensitive to the surrounding medium's temperature and salinity. This project provides a **physics-aware AI pipeline** that:
1. **Predicts** the optimal operating frequency (kHz) and power (W).
2. **Validates** results against physical constraints.
3. **Calculates** hardware-level drive voltages (RMS/Peak) for immediate deployment.

### Key Operating Ranges
| Parameter | Range |
| :--- | :--- |
| **Temperature** | -10°C to 85°C |
| **Salinity** | 0 to 50 ppt |
| **Target Frequency** | 35 to 110 kHz |
| **Target Power** | 0.2 to 3.5 W |

---

## 🛠️ Tech Stack

- **Core Engine:** TensorFlow/Keras (MLP Architecture)
- **Data Science:** Scikit-learn, Pandas, NumPy
- **Visualization:** Matplotlib, Seaborn
- **Utilities:** Physics-based validation guards & hardware conversion logic

---

## 📁 Project Structure

```text
acoustic-ML/
├── new_models/          # Trained models, scalers, and training plots
├── tested-data/         # Evaluation results and exported predictions
├── train.py             # Deep learning training pipeline
├── predict.py           # CLI tool for real-time inference
├── evaluate.py          # Model performance & residual analysis
├── utils.py             # Physics guards, metrics, & 3D visualizations
└── new_dataset.csv      # Core experimental dataset
```

---

## ⚡ Quick Start

### 1. Installation
Ensure you are in a virtual environment, then install the dependencies:
```powershell
pip install -r requirements.txt
```

### 2. Training the Model
To retrain the neural network with the latest dataset:
```powershell
python train.py
```
*Outputs: `best_model.h5`, `scaler.pkl`, and `training_history.png` in the `new_models/` directory.*

### 3. Real-time Prediction
Run the interactive predictor to get optimal parameters for specific conditions:
```powershell
python predict.py
```
**Example Input:**
- Temperature: `25`
- Salinity: `35` (Average Seawater)

---

## 📊 Evaluation & Visualization

The system includes research-grade diagnostic tools in `evaluate.py` and `utils.py`. Running the evaluation script generates several key visualizations in the `new_models/` directory:

- **Model Performance (`model_performance.png`):** Actual vs. Predicted scatter plots with R² scores.
- **Residual Analysis (`residual_plot.png`):** Detects heteroscedasticity and model bias across the prediction range.
- **Error Distribution (`residual_distribution.png`):** Histogram of residuals to check for normality of errors.
- **3D Surface Mapping:** Visualizes how frequency and power shift across the entire thermo-saline envelope (via `utils.py`).

---

## 📐 Hardware Integration

The system translates acoustic power into electrical drive requirements using:
$$V_{rms} = \sqrt{\frac{P_{acoustic}}{\eta \cdot Z}}$$
Where:
- $\eta$ = Transducer Efficiency (Default: 40%)
- $Z$ = Impedance (Default: 8.0 $\Omega$)

---
