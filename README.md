# PowerGrid EV Analytics

## Task 1 — EV Charging Demand Forecasting

### Project Overview

This repository contains my individual work for the **PowerGrid EV Analytics Programme**, focusing on the application of data science and machine learning techniques to EV charging data.

This submission covers **Task 1: EV Charging Demand Forecasting**, where historical EV charging session data is analysed and used to forecast future charging demand.

---

## Task Objective

The objective of this task is to analyse historical EV charging demand and develop a time-series forecasting model to predict future charging demand, supporting capacity planning and operational decision-making.

---

## Dataset

The analysis uses the **EV Charging Dataset**, containing charging data from **2022–2024**.

The `sessions` sheet was used for the forecasting analysis.

### Key Variables

| Variable | Description |
|---|---|
| `start_timestamp` | Charging session start time |
| `energy_kwh` | Energy delivered during the session |
| `station_id` | Charging station identifier |
| `charger_type` | Type of charging equipment |
| `user_type` | User category |
| `station_region` | Geographic region of the station |

---

## Methodology

The analysis followed these steps:

1. Loaded the EV charging session data.
2. Converted the `start_timestamp` column to datetime format.
3. Aggregated `energy_kwh` by day to calculate daily charging demand.
4. Prepared the daily time-series dataset for forecasting.
5. Split the historical data into training and testing periods.
6. Trained a **Prophet** forecasting model.
7. Evaluated the model using **MAPE** and **RMSE**.
8. Generated a **365-day forecast for 2025**.
9. Analysed the forecast results and identified key business insights.

---

## Forecasting Model

### Prophet

**Prophet** was selected as the forecasting approach for this task.

The model was used to capture:

- Long-term demand trends
- Weekly seasonality
- Recurring demand patterns

The historical dataset contained **1,096 daily observations**.

The final **30 days of 2024** were used as the test period for model evaluation.

---

## Model Performance

| Metric | Result |
|---|---:|
| MAPE | **8.29%** |
| RMSE | **2,061.55 kWh** |

The Prophet model achieved a **MAPE of 8.29%** on the 30-day test period, indicating reasonable predictive performance for daily EV charging demand.

---

## 2025 Forecast Results

| Forecast Metric | Result |
|---|---:|
| Average Daily Demand | **28,353.35 kWh** |
| Minimum Predicted Demand | **23,773.34 kWh** |
| Maximum Predicted Demand | **32,835.30 kWh** |
| Forecast Period | **1 January – 31 December 2025** |

### Key Forecast Insights

- The **highest predicted demand** is **32,835.30 kWh** on **31 December 2025**.
- The **lowest predicted demand** is **23,773.34 kWh** on **4 January 2025**.
- The forecast indicates an overall **upward trend in charging demand** during 2025.
- The model captures recurring **weekly demand patterns**.

---

## Business Implications

The forecast can support PowerGrid in:

- Planning future charging infrastructure capacity
- Estimating energy requirements
- Allocating operational resources
- Planning maintenance activities
- Preparing for periods of higher charging demand

---

## Repository Structure

```text
PowerGrid-EV-Analytics/
│
├── README.md
│
└── Task_01_EV_Demand_Forecasting.ipynb
```

---

## Task Deliverable

**Notebook:** `Task_01_EV_Demand_Forecasting.ipynb`

The notebook contains the complete data preparation, forecasting model, model evaluation, visualisations, forecast results, and business insights for Task 1.

---

## Project Status

**Task 1: Completed**

**Overall Progress: 1 / 16 Tasks**
