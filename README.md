Yes. Since you want to **keep Task 1 and add Task 2 to the same root README**, replace your current README with this updated version:

````markdown
# PowerGrid EV Analytics

## Project Overview

This repository contains my individual work for the **PowerGrid EV Analytics Programme**, focusing on the application of data science, machine learning, and business analytics techniques to EV charging data.

The project consists of multiple analytical tasks covering EV demand forecasting, revenue analysis, charger utilisation, customer behaviour, predictive maintenance, and other EV analytics problems.

---

# Task 1 — EV Charging Demand Forecasting

## Task Objective

The objective of this task is to analyse historical EV charging demand and develop a time-series forecasting model to predict future charging demand, supporting capacity planning and operational decision-making.

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

## Methodology

1. Loaded the EV charging session data.
2. Converted `start_timestamp` to datetime format.
3. Aggregated `energy_kwh` by day to calculate daily charging demand.
4. Prepared the daily time-series dataset.
5. Split the historical data into training and testing periods.
6. Trained a **Prophet** forecasting model.
7. Evaluated the model using **MAPE** and **RMSE**.
8. Generated a **365-day forecast for 2025**.
9. Analysed the forecast results and identified key business insights.

## Forecasting Model

### Prophet

**Prophet** was selected as the forecasting approach.

The model was used to capture:

- Long-term demand trends
- Weekly seasonality
- Recurring demand patterns

The historical dataset contained **1,096 daily observations**.

The final **30 days of 2024** were used as the test period.

## Model Performance

| Metric | Result |
|---|---:|
| MAPE | **8.29%** |
| RMSE | **2,061.55 kWh** |

## 2025 Forecast Results

| Forecast Metric | Result |
|---|---:|
| Average Daily Demand | **28,353.35 kWh** |
| Minimum Predicted Demand | **23,773.34 kWh** |
| Maximum Predicted Demand | **32,835.30 kWh** |
| Forecast Period | **1 January – 31 December 2025** |

## Business Implications

The forecast can support:

- Charging infrastructure capacity planning
- Energy requirement estimation
- Operational resource allocation
- Maintenance planning
- Preparation for periods of higher charging demand

---

# Task 2 — Revenue Forecasting & Price Sensitivity

## Task Objective

The objective of this task is to analyse how EV charging revenue changes with demand, pricing, and seasonal patterns, and to evaluate the potential impact of price adjustments on customer demand and revenue.

## Dataset

The same **EV Charging Dataset (2022–2024)** was used.

The `sessions` sheet was used to create a monthly revenue time-series dataset.

### Key Variables

| Variable | Description |
|---|---|
| `start_timestamp` | Charging session start time |
| `energy_kwh` | Energy delivered |
| `price_per_kwh` | Charging price per kWh |
| `total_cost` | Revenue generated from the session |
| `user_type` | User category |
| `station_region` | Geographic region |

## Methodology

1. Loaded and inspected the EV charging session data.
2. Created a monthly revenue time-series dataset.
3. Aggregated monthly revenue, energy demand, average price, and session count.
4. Analysed price-demand relationships.
5. Estimated price elasticity using a log-log regression model.
6. Built a **Prophet** model for monthly revenue forecasting.
7. Evaluated the forecasting model using **MAPE** and **RMSE**.
8. Generated a **12-month revenue forecast for 2025**.
9. Simulated price adjustment scenarios of **+5% and −10%**.
10. Analysed the estimated revenue impact.

## Revenue Time-Series Dataset

The monthly dataset contains **36 observations**, covering:

**January 2022 – December 2024**

The dataset includes:

- Monthly revenue
- Monthly energy demand
- Average price per kWh
- Number of charging sessions

## Revenue Forecasting Model

### Prophet

Prophet was used to forecast monthly EV charging revenue while accounting for yearly seasonal patterns.

### Model Performance

| Metric | Result |
|---|---:|
| MAPE | **4.11%** |
| RMSE | **22,242.75** |

The final six months of 2024 were used as the test period.

## Price Elasticity Analysis

A log-log regression model was used to estimate the relationship between average charging price and energy demand.

**Estimated price elasticity: 3.8077**

The positive coefficient indicates that price and demand moved together in the historical dataset. Therefore, the elasticity-based scenario results should be interpreted as **model-based estimates rather than causal predictions**.

## Price Scenario Simulation

| Scenario | Price Change | Estimated Demand Change | Estimated Revenue | Revenue Change |
|---|---:|---:|---:|---:|
| Baseline | 0% | 0.00% | 222,266.11 | 0.00% |
| Price +5% | +5% | +19.04% | 277,811.24 | +24.99% |
| Price −10% | −10% | −38.08% | 123,870.65 | −44.27% |

## Business Implications

The analysis can support:

- Monthly revenue planning
- Pricing scenario evaluation
- Demand and revenue analysis
- Revenue forecasting
- Data-driven pricing discussions

The scenario results are based on the estimated historical relationship between price and demand and should therefore be treated as analytical estimates.

---

# Repository Structure

```text
PowerGrid-EV-Analytics/
│
├── README.md
│
├── Task_01_EV_Demand_Forecasting.ipynb
│
└── Task_02_Revenue_Forecasting_Price_Sensitivity.ipynb
````

---

# Task Deliverables

### Task 1

**Notebook:** `Task_01_EV_Demand_Forecasting.ipynb`

Contains data preparation, Prophet forecasting, model evaluation, visualisations, forecast results, and business insights.

### Task 2

**Notebook:** `Task_02_Revenue_Forecasting_Price_Sensitivity.ipynb`

Contains revenue time-series preparation, price elasticity analysis, monthly revenue forecasting, price scenario simulations, and executive summary.

---

# Project Status

| Task                                             | Status      |
| ------------------------------------------------ | ----------- |
| Task 1 — EV Charging Demand Forecasting          | ✅ Completed |
| Task 2 — Revenue Forecasting & Price Sensitivity | ✅ Completed |

**Overall Progress: 2 / 16 Tasks**

```

This keeps **Task 1 intact** and adds **Task 2** underneath it in the same README.
```
