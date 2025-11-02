Project: Hourly forecasting of ozone (O₃) and nitrogen dioxide (NO₂) using meteorology, forecasts, and time features.
Source: Colab notebook → production-ready script 

(This README documents the pipeline, usage, and key details)

⸻

Overview

This project trains and evaluates LightGBM and CatBoost regression models separately for O₃ and NO₂ targets.
The pipeline includes data extraction, cleaning, feature engineering (lags, rolling stats, cyclic time features), train/test split (time-aware), scaling, model training with early stopping, evaluation (RMSE & R²), and permutation-based feature importance.

⸻

Requirements
	•	Python 3.8+
	•	Pip packages:
	•	pandas
	•	numpy
	•	scikit-learn
	•	lightgbm
	•	catboost
	•	joblib (optional, for model dumps)
	•	seaborn / matplotlib (optional for plotting)

Install with:

pip install pandas numpy scikit-learn lightgbm catboost joblib

The Colab notebook used !pip install catboost at the top — include this when running in clean environments.

⸻

Dataset / Expected Input

The script expects a CSV with at least the following columns:
	•	datetime components: year, month, day, hour
	•	target columns: O3_target, NO2_target
	•	forecast / meteorology columns (examples): O3_forecast, NO2_forecast, T_forecast, q_forecast, u_forecast, v_forecast, w_forecast
	•	other station-specific features may be present.

⸻

Example (reported) results

	•	CatBoost O₃ — RMSE: 8.8943, R²: 0.9282
	•	CatBoost NO₂ — RMSE: 6.7908, R²: 0.8745
	•	LightGBM metrics are printed similarly during training (check logs).
