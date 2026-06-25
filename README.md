# calgary-household-energy-analysis
Complete energy analytics for 140 Calgary households (2024-2025): BigQuery, Colab, Looker Studio

# 🏠 Calgary Household Energy Analysis 2024–2025

## 📋 Project Overview

End-to-end energy analytics project using a publicly available synthetic dataset 
of **140 Calgary households** across **731 days** (Jan 2024–Dec 2025).

Calgary's extreme climate (−28°C winters → +24°C summers) creates one of the 
most dramatic seasonal energy patterns among Canadian cities — making this an 
ideal case study for thermal demand modeling, EV impact analysis, and cost 
forecasting.

## Source of Dataset
[yonathanhary on Kaggle](https://www.kaggle.com/datasets/yonathanhary/household-energy-consumption-synthetic) — Original

---

## What can be analyzed from that dataset?
1. Seasonal Patterns — Energy consumption rises/falls in winter compared with summer

2. Correlation between Temperature and Energy Consumption — Does energy consumption increase as the temperature drops?

3. Household Segmentation — Differences in consumption based on household size, number of occupants and EV ownership

4. Cost Forecasting — A regression model for estimating electricity costs

5. Energy Efficiency — Which households are the most efficient/inefficient?

6. Air conditioning analysis — How often is the air conditioning used compared to the maximum capacity available?

7. Outlier Detection — Households with consumption levels outside the norm

8. Analysis of Energy Consumption
   A. Total and average daily consumption per household (Daily_kWh)
   B. Comparison between households — who is the most wasteful/thrifty?
   C. Daily/weekly/monthly/annual consumption trends
   D. Identification of seasonal patterns (Calgary’s winter and summer are very different due to heating)

9. Energy Cost Analysis
    A. Total electricity costs per household (Daily_Cost_CAD)
   B. Impact of changes to electricity tariffs (Tariff_Rate_CAD_kWh fluctuates — there are three visible tariff levels: 0.105, 0.098, 0.1206)
   C. Cost per square metre (Cost per m²)
   D. Price elasticity — do households save more when prices rise?

10. Analysis of the Impact of Outdoor Temperature (Heating/Cooling)
    A. Correlation between outdoor temperature and consumption — Winters in Calgary can reach -20°C, resulting in huge heating demand
    B. AC usage vs temperature (AC_Hours_Used vs Outside_Temperature_C)
    C. Identification of critical temperature points (threshold analysis) — below what temperature does heating demand rise sharply?
    D. Comparison of consumption between cold and warm days

11. Analysis of Household Characteristics
    A. Household Size (number of people) → does a larger household mean higher energy consumption?
    B. Living Area (m²) → correlation between house size and consumption
    C. Has_EV_Car (EV vs non-EV) → the impact of electric vehicles on electricity consumption
    D. Max_AC_Hours → air conditioning capacity – do homes with larger air conditioning units consume more electricity?
    E. Household segmentation by profile (small family, large household, EV owner, etc.)

12. Time-Series Analysis
    A. Seasonality: pattern of consumption/season (winter heating vs summer cooling)
    B. Day-of-week patterns: weekday vs weekend consumption
    C. Trend analysis: has consumption risen or fallen over the past two years?
    D. Anomaly detection: days with outlier consumption

13. Forecasting
    A. Forecasting future consumption based on historical data (time series forecasting)
    B. Cost estimates based on projected rates
    C. Input for ML model: predict daily kWh given temperature, household profile, tariff

14. Efficiency Benchmarking
    A. kWh per m² per household → energy efficiency between households
    B. Cost efficiency — who gets the cheapest electricity per kWh
    C. Ranking of households by efficiency (energy efficiency score)
    D. Identifying ‘spenders’ versus ‘savers’ based on similar characteristics

15. AC Usage Pattern Analysis
    A. Are air-conditioning hours used? (In the initial sample, AC_Hours_Used = 0.0; it is likely that the air conditioning is only switched on in summer)
    B. Relationship between Max_AC_Hours and actual usage
    C. The impact of air-conditioning usage on total daily consumption

16. Tariff Impact Analysis
    A. Comparison of consumption before and after the tariff change
    B. Demand response analysis — do higher tariffs encourage people to save energy?
    C. Optimal tariff planning scenarios

17. Statistical / ML Modeling
    A. Regression: predicting Daily_kWh based on temperature, house size, number of people, etc.
    B. Clustering: segmentation of households based on consumption patterns
    C. Classification: predicting whether a household is a high or low consumer
    D. Feature importance analysis

---

## 🔍 Key Findings

| # | Finding | Metric |
|---|---------|--------|
| 1 | ❄️ Winter heating dominates | 20.8 kWh/day vs 12.5 kWh/day summer (+66%) |
| 2 | ⚡ EV ownership impact | +54% more consumption (21.2 vs 13.7 kWh/day) |
| 3 | 🌡️ Critical cold threshold | Below −10°C: heating demand spikes dramatically |
| 4 | 🏆 Most efficient household | HH_077: 6.85 kWh avg (26m², 2 people, no EV) |
| 5 | 🔥 Highest consumer | HH_043: 28.6 kWh avg (142m², 5 people, EV owner) |
| 6 | 💰 2-year total cost | CAD $182,816 across all 140 households |
| 7 | 🤖 ML best model | XGBoost R² ≈ 0.85 (temp + area + EV = top features) |
| 8 | 📊 Temperature correlation | r = −0.72 (strong negative) |

---

## 🛠️ Tech Stack

| Phase | Tool | What I Did |
|-------|------|-----------|
| 1 | Google BigQuery | 12 SQL queries → seasonal, efficiency, outlier, tariff analysis |
| 2 | Google Colab (Python) | EDA, ML models (XGBoost/RF), clustering, time series forecasting |
| 3 | Google Looker Studio | 4-page interactive executive dashboard (connected to BigQuery) |
| 4 | GitHub | Version control, documentation, portfolio |
| 5 | Tableau Public | Visualization |

---

## 📈 Live Dashboards

| Platform | Link | Description |
|----------|------|-------------|
| 📊 Looker Studio | [Open Dashboard](https://datastudio.google.com/reporting/6bc83955-7184-46c1-9903-a92e17e049e7) | Dashboard (BigQuery) |
| 📉 Tableau Public | [Open Dashboard](https://public.tableau.com/views/CalgaryHouseholdEnergySyntheticAnalyst/ExecutiveOverview?:language=en-US&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link) | visualizations |

---

## 📊 Analysis Breakdown (17 Dimensions)

<details>
<summary>Click to expand full analysis list</summary>

| # | Analysis | Tool | Key Output |
|---|----------|------|-----------|
| 1 | Seasonal Patterns | BigQuery + Colab | Winter 66% higher than summer |
| 2 | Temp vs Consumption | BigQuery + Tableau | r = −0.72 correlation |
| 3 | Household Segmentation | BigQuery + Looker | 4 clusters identified |
| 4 | Cost Prediction Model | Colab (XGBoost) | R² = 0.85 |
| 5 | Efficiency Ranking | BigQuery + Tableau | kWh/m² benchmarking |
| 6 | AC Usage Analysis | BigQuery + Colab | Summer-only pattern |
| 7 | Outlier Detection | BigQuery + Colab | Z-score ±2.5σ method |
| 8A | Daily Consumption | Looker Studio | Per-household trending |
| 8B | Most/Least Efficient | Tableau | Ranked 140 households |
| 8C | Weekly/Monthly Trend | Looker + Colab | Seasonal decomposition |
| 9A | Cost per Household | BigQuery | Total 2yr cost breakdown |
| 9B | Tariff Impact | BigQuery + Tableau | 10 tariff levels analyzed |
| 10A | Temp-Consumption Corr | All platforms | Threshold at −10°C |
| 11C | EV Impact | BigQuery + Looker | +54% consumption |
| 12A | Seasonality | Colab (statsmodels) | Holt-Winters decomposition |
| 13 | Forecasting | Colab | 90-day Holt-Winters forecast |
| 17 | ML Clustering | Colab (K-Means) | 4 household archetypes |

</details>

---

## 👤 About

**[DWI FARHAN]** —  EE Data Analyst

Analyzing energy data to find patterns that drive smarter consumption decisions.

[![LinkedIn](https://www.linkedin.com/in/dwi-farhan/)
