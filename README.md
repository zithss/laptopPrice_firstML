# 💻 Laptop Price Prediction

Predict laptop prices (in euros) from hardware specifications using XGBoost (with Optuna tuning). Clean, single-notebook project aimed to help manufacturers, retailers, and consumers make data-driven pricing decisions.

# Project overview

* **Objective:** Predict laptop prices from specs (CPU, RAM, storage, screen, GPU, etc.) to support pricing decisions.
* **Approach:** EDA → preprocessing & feature engineering → modeling (Linear Regression, XGBoost) → hyperparameter tuning (Optuna) → evaluation.
* **Primary metrics:** R², MSE, RMSE, MAE.

# Dataset

* Source: Kaggle — `owm4096/laptop-prices` (`https://www.kaggle.com/datasets/owm4096/laptop-prices`)
* Place the CSV in `data/` (e.g., `data/laptops.csv`) before running the notebook.

# Project structure

Everything is in one notebook:

```
Machine Learning Project.ipynb
```

# Features (summary)

* **Base numerical:** `Inches, Ram, Weight, Price_euros, ScreenW, ScreenH, CPU_freq, PrimaryStorage, SecondaryStorage`
* **Base categorical:** `Company, Product, TypeName, OS, Screen, Touchscreen, IPSpanel, RetinaDisplay, CPU_company, CPU_model, PrimaryStorageType, SecondaryStorageType, GPU_company, GPU_model`
* **Engineered highlights:** `Resolution, PPI, Screen_Quality, GPU_Performance, Overall_Performance, Portable_Value, Storage_Feature(s), GPU_CPU, Computing_Value, Rendering_Value, Overall_Value`

# Models & performance

**Linear Regression (baseline)**

* R²: 0.8075
* MSE: 95,560.9917
* RMSE: 309.1294
* MAE: 214.5642

**XGBoost (base)**

* R²: 0.9170
* MSE: 41,172.9568
* RMSE: 202.9112
* MAE: 142.4063

**XGBoost (Optuna optimized)**

* **R²: 0.9300**
* **MSE: 34,745.3555**
* **RMSE: 186.4011**
* **MAE: 134.4414**

> Optimized XGBoost shows best generalization (lower RMSE/MAE and higher R²).

# Feature importance & insights

* Top drivers: **Resolution**, **RAM**, **Storage\_Feature1**, **ScreenW** (with tuned model giving more weight to resolution).
* Engineered performance/interaction features (GPU\_Performance, Overall\_Performance, GPU\_CPU) help capture real-world value beyond raw specs.
* Residual plots: optimized XGBoost predictions cluster tighter around the diagonal than linear regression.

# Conclusions & recommendations

* **Best model:** XGBoost with Optuna tuning — recommended for production use after additional validation.
* **For manufacturers & retailers:** prioritize specs and bundles that raise perceived value (higher resolution, RAM, GPU capabilities). Use model predictions to inform pricing tiers.
* **For consumers:** compare predicted vs listed prices to spot under-/over-priced offers.

# Future work

* Add temporal/market features (release date, depreciation, region-based pricing).
* Expand dataset to cover more brands/regions for improved generalization.
* Add explainability (SHAP/LIME) for per-item insights.
* Deploy as a lightweight API (FastAPI) or simple web UI for interactive price estimation.
