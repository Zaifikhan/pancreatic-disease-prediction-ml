# Pancreatic Disease Prediction — Tabular ML & Neural Nets
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
![Python](https://img.shields.io/badge/Python-3.10%2B-blue.svg)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange.svg)
![scikit-learn](https://img.shields.io/badge/scikit--learn-1.x-informational.svg)
![CatBoost](https://img.shields.io/badge/CatBoost-1.x-informational.svg)
![LightGBM](https://img.shields.io/badge/LightGBM-4.x-informational.svg)
![XGBoost](https://img.shields.io/badge/XGBoost-2.x-informational.svg)
![PyTorch](https://img.shields.io/badge/PyTorch-2.x-red.svg)
![Optuna](https://img.shields.io/badge/Optuna-3.x-informational.svg)
![LightAutoML](https://img.shields.io/badge/LightAutoML-informational.svg)

This repository contains a **reproducible notebook** for predicting pancreatic disease status from tabular biomarker data (Debernardi et al., 2020).  
It compares a strong classical ML baseline (CatBoost / LightGBM / XGBoost / scikit‑learn) to a **PyTorch MLP** and an **AutoML** baseline (LightAutoML), with careful evaluation and ablation.

> **Status**: research notebook. The dataset itself is not included; see the *Data* section for instructions.

## Highlights
- End‑to‑end: EDA → feature prep → modeling → evaluation
- Models: Logistic Regression, SVM, Random Forest, CatBoost, LightGBM, XGBoost, PyTorch MLP
- HPO: Optuna sweeps for selected models
- Reports: `ydata-profiling` quick EDA, learning curves, metrics CSV
- Repro: `requirements.txt`, fixed random seeds where applicable

## Repo structure
```
.
├─ Practice_NN.ipynb              # main notebook (provided by author)
├─ requirements.txt
├─ LICENSE
├─ .gitignore
└─ README.md
```

## Data
The notebook expects the Debernardi et al. (2020) biomarker dataset.  
Place the CSV into a local `data/` folder and update the notebook path accordingly, e.g.:
```python
DATA_PATH = "data/Debernardi_et_al_2020_data.csv"
df = pd.read_csv(DATA_PATH)
```
*Note:* The original notebook may contain an absolute Windows path; replace it with the relative path above before running.

## Quickstart
```bash
# 1) Clone
git clone https://github.com/<YOUR_GH_USERNAME>/<YOUR_REPO>.git
cd <YOUR_REPO>

# 2) Create environment (pip)
python -m venv .venv && . .venv/Scripts/activate    # Windows PowerShell: .venv\Scripts\Activate.ps1
pip install -r requirements.txt

# 3) (Optional) Jupyter kernel
python -m ipykernel install --user --name pancreatic-ml --display-name "pancreatic-ml"

# 4) Run the notebook
jupyter lab  # or: jupyter notebook
```

## Reproducibility notes
- Python ≥ 3.10 recommended
- Set seeds where available, but stochasticity in PyTorch/GBDTs may still cause small variance
- GPU is **not required** but can speed up training for large Optuna sweeps

## Citation / Acknowledgment
- Dataset: Debernardi et al., 2020 (please cite the original authors).  
- This repository: © 2025 Konstantin N — MIT License.
