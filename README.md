# Task 1: EV Charging Demand Forecasting

## Objective

The objective of this task is to analyse historical EV charging demand and forecast future charging demand to support PowerGrid's capacity and operational planning.

## Dataset

The EV charging dataset contains historical charging session data from **2022–2024**.

For this task, the `sessions` sheet was used, with:

- `start_timestamp` — charging session start time
- `energy_kwh` — energy delivered during the session
- `station_id` — charging station identifier
- `charger_type` — type of charger
- `user_type` — customer category
- `station_region` — station region

## Data Preparation

The following preprocessing steps were performed:

1. Loaded the `sessions` sheet from the Excel dataset.
2. Converted `start_timestamp` to datetime format.
3. Aggregated `energy_kwh` by day to calculate daily charging demand.
4. Prepared the resulting time-series dataset for Prophet forecasting.

The resulting daily dataset contained **1,096 days** of historical demand.

## Forecasting Approach

### Prophet

Facebook Prophet was selected as the forecasting method.

Prophet was used to capture:

- Overall demand trends
- Weekly seasonality
- Recurring demand patterns

The model was trained on historical daily charging demand and used to forecast **365 days into 2025**.

## Model Evaluation

The last **30 days of 2024** were reserved as a test period.

| Metric | Result |
|---|---:|
| MAPE | **8.29%** |
| RMSE | **2,061.55 kWh** |

The model achieved a MAPE of 8.29%, indicating reasonable forecasting performance on the 30-day test period.

## 2025 Forecast Insights

- **Average predicted daily demand:** 28,353.35 kWh
- **Forecast range:** 23,773.34 – 32,835.30 kWh
- **Highest predicted demand:** 32,835.30 kWh on December 31, 2025
- **Lowest predicted demand:** 23,773.34 kWh on January 4, 2025

The forecast indicates an overall upward trend in EV charging demand throughout 2025, along with recurring weekly demand patterns.

## Business Implications

The forecast can help PowerGrid with:

- Charging infrastructure capacity planning
- Energy requirement planning
- Operational resource allocation
- Maintenance scheduling
- Preparation for periods of higher charging demand

## Files

- `Task_01_EV_Demand_Forecasting.ipynb` — Complete analysis, Prophet model, evaluation, forecast and visualisations.
- `README.md` — Task documentation and key findings.
