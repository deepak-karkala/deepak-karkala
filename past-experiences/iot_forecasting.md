---
title: 'Building-Level Energy Forecasting & Smart Energy Advisor'
summary: 'Developed time-series forecasting models for building energy optimization and smart heating schedules'
date: '2022-08-10'
category: 'ML Engineer at eSMART Technologies'
categoryDuration: 'Jun 2018 - Dec 2020'
role: 'ML Engineer'
company: 'eSMART Technologies'
websiteUrl: 'https://myesmart.com/en/'
duration: ''
location: 'Remote'
techStack:
  - 'Python'
  - 'Time Series Models'
  - 'IoT Data Processing'
  - 'Forecasting'
highlights:
  - '<10% MAPE across seasonal variations'
  - '~15% increase in user engagement with energy tools'
  - '~10pp increase in solar self-consumption among participating households'
order: 6
---

##
---

### The Problem

Residents living in smart, energy-connected apartments had access to consumption dashboards — but **not predictive insights**.

Without forecasting:

* Solar-powered buildings lacked guidance for load shifting
* Residents couldn’t optimize appliance timing or consumption patterns
* Building-level planning for heating control was reactive rather than proactive

The key question:

> *“If we can predict tomorrow’s energy demand, can we help residents lower costs and increase renewable usage?”*

---

### The Solution

I developed a **24-hour ahead forecasting system** that predicts daily heating + electrical demand using historical smart-meter data, weather forecasts, and seasonal behavioral signals.

It powered a resident-facing feature called **Smart Energy Advisor**, which generates personalized recommendations based on predicted demand trends and solar availability.

| Component           | Details                                                                               |
| ------------------- | ------------------------------------------------------------------------------------- |
| **Forecast Model**  | XGBoost-based regression with time-series feature engineering                         |
| **Feature Inputs**  | Weather forecast, rolling windows, HDD, occupancy proxies, calendar effects           |
| **Validation**      | Walk-forward evaluation and drift analysis                                            |
| **Deployment**      | MLOps pipeline with automated retraining, weather-feed fallback, and error monitoring |
| **User Experience** | Forecast-driven nudges and appliance-timing suggestions in the mobile app             |

---

### Business & Technical Results

The system demonstrated meaningful impact:

* **<10% MAPE** across seasonal variations
* **~15% increase in user engagement** with energy tools
* **~10-percentage-point increase in solar self-consumption** among participating households
* Improved transparency, sustainability awareness, and behavioral adoption

---

### Technical Highlights

* Python, scikit-learn, XGBoost
* Time series pipeline: lag features, seasonality encoding, rolling statistics
* Robustness logic for missing intervals, sensor irregularity, and weather outage fallback
* Walk-forward CV, baseline benchmarking (ARIMA, Prophet, seasonal naive)
* MLOps evaluation dashboards and alerting for drift and unusual deviations

---

### What I Learned

This project emphasized that **forecasting alone doesn’t create value — behavior change does.**

Delivering the model as an **interactive, understandable energy insight tool** made the difference. The success came from:

* Transparent communication of predictions
* Integration into daily user context
* Iterative feedback from both product & engineering stakeholders

It showed how machine learning in the built environment can directly contribute to **sustainability, cost reduction, and user empowerment.**

___