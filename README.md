

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

# Task 3 — Charger Utilisation & Efficiency Analysis

## Task Objective

The objective of this task is to measure charger utilisation, idle time, and peak-load patterns to identify bottleneck stations and support infrastructure capacity optimisation.

## Dataset

The **EV Charging Dataset (2022–2024)** was used.

The `sessions` sheet was analysed to evaluate charger-level and station-level performance.

### Key Variables

| Variable | Description |
|---|---|
| `station_id` | Charging station identifier |
| `charger_id` | Charger identifier |
| `charger_type` | Charger type |
| `start_timestamp` | Charging session start time |
| `end_timestamp` | Charging session end time |
| `session_duration_minutes` | Duration of charging session |
| `energy_kwh` | Energy delivered |

## Methodology

1. Loaded and inspected the charging session data.
2. Converted session timestamps into datetime format.
3. Calculated charging duration in hours.
4. Aggregated charging sessions at charger level.
5. Calculated charger utilisation percentage.
6. Calculated idle time and idle percentage.
7. Analysed hourly charging load to identify peak periods.
8. Ranked chargers according to utilisation.
9. Created a charger utilisation heatmap.
10. Aggregated charger performance at station level.
11. Developed capacity optimisation recommendations.

## Charger Utilisation Analysis

Charger utilisation was calculated using total charging hours relative to the overall dataset period.

The highest-utilisation charger was:

**STN_001_CH_04 — 12.06% utilisation**

Other highly utilised chargers included chargers at **STN_007** and **STN_001**.

The results indicate that charger demand is not evenly distributed across the infrastructure.

## Idle-Time Analysis

Idle time was calculated as the difference between total available hours and total charging hours.

Several chargers showed idle percentages above **99%** under the session-time-based utilisation measure, particularly some DC 150 kW and DC 300 kW chargers.

This indicates that a number of chargers have relatively low observed session occupancy during the analysed period.

> **Note:** Idle-time and utilisation percentages represent a session-time-based analytical measure using the overall dataset period. They should not be interpreted as direct measurements of physical charger availability.

## Peak-Load Analysis

Hourly charging activity was analysed using total energy consumed and number of charging sessions.

The highest observed hourly energy demand occurred at:

**10 AM — 1,134,524.0 kWh**

Other high-load periods included:

- 1 PM — 1,131,742.8 kWh
- 2 PM — 1,131,890.0 kWh
- 11 AM — 1,129,683.7 kWh
- 12 PM — 1,123,218.3 kWh

Overall, charging activity was relatively high during the daytime period from approximately **9 AM to 4 PM**.

## Charger Performance Ranking

Charger utilisation varied considerably across individual chargers.

### Highest Utilisation

| Rank | Station | Charger | Type | Utilisation |
|---:|---|---|---|---:|
| 1 | STN_001 | STN_001_CH_04 | DC_50kW | **12.06%** |
| 2 | STN_007 | STN_007_CH_02 | DC_50kW | **12.00%** |
| 3 | STN_007 | STN_007_CH_04 | DC_50kW | **11.98%** |

### Lowest Utilisation

| Station | Charger | Type | Utilisation |
|---|---|---|---:|
| STN_025 | STN_025_CH_02 | DC_300kW | **0.73%** |
| STN_027 | STN_027_CH_04 | DC_300kW | **0.73%** |
| STN_025 | STN_025_CH_03 | DC_300kW | **0.78%** |

## Station Capacity Analysis

Station-level analysis showed substantial variation in average charger utilisation.

| Station | Chargers | Average Utilisation |
|---|---:|---:|
| STN_007 | 4 | **10.09%** |
| STN_001 | 4 | **8.88%** |
| STN_006 | 4 | **6.99%** |
| STN_003 | 5 | **6.51%** |
| STN_014 | 4 | **5.79%** |

Stations such as **STN_025, STN_027, and STN_019** showed relatively low average utilisation.

## Capacity Optimisation Recommendations

Based on the analysis:

1. **Monitor high-utilisation stations:** Stations such as STN_007 and STN_001 should be monitored during peak periods to identify possible congestion or capacity constraints.

2. **Review low-utilisation chargers:** Chargers with consistently low utilisation should be evaluated before additional capacity is installed at the same locations.

3. **Plan capacity around peak hours:** Infrastructure planning should consider the high-demand daytime period between approximately 9 AM and 4 PM.

4. **Redistribute charging demand:** Where operationally feasible, users can be encouraged to use underutilised chargers or nearby stations through pricing or availability information.

5. **Use charger-level monitoring:** Individual charger utilisation should be tracked regularly to identify bottlenecks and inefficient capacity allocation.

## Conclusion

The analysis demonstrates that charger utilisation varies considerably across stations and individual chargers.

Peak charging activity is concentrated during daytime hours, while several chargers remain substantially underutilised.

These findings can support data-driven infrastructure planning by identifying locations that require closer monitoring and areas where additional capacity may not currently be necessary.

---

# Repository Structure

```text
PowerGrid-EV-Analytics/
│
├── README.md
│
├── Task_01_EV_Demand_Forecasting.ipynb
│
├── Task_02_Revenue_Forecasting_Price_Sensitivity.ipynb
│
└── Task_03_Charger_Utilisation_Efficiency_Analysis.ipynb
````

---

# Task Deliverables

### Task 1

**Notebook:** `Task_01_EV_Demand_Forecasting.ipynb`

Contains data preparation, Prophet forecasting, model evaluation, visualisations, forecast results, and business insights.

### Task 2

**Notebook:** `Task_02_Revenue_Forecasting_Price_Sensitivity.ipynb`

Contains revenue time-series preparation, price elasticity analysis, monthly revenue forecasting, price scenario simulations, and executive summary.

### Task 3

**Notebook:** `Task_03_Charger_Utilisation_Efficiency_Analysis.ipynb`

Contains charger utilisation analysis, idle-time analysis, peak-load analysis, performance ranking, utilisation heatmap, station-level capacity analysis, and capacity optimisation recommendations.

---

# Project Status

| Task                                               | Status      |
| -------------------------------------------------- | ----------- |
| Task 1 — EV Charging Demand Forecasting            | ✅ Completed |
| Task 2 — Revenue Forecasting & Price Sensitivity   | ✅ Completed |
| Task 3 — Charger Utilisation & Efficiency Analysis | ✅ Completed |

**Overall Progress: 3 / 16 Tasks**

````

*
````
