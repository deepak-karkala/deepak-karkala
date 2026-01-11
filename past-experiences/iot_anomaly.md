# IoT Predictive Maintenance & Heating System Anomaly Detection

> ML Engineer
>
> [eSMART Technologies](https://myesmart.com/en/), Renens Switzerland
>
> Built an anomaly detection system that reduced emergency maintenance callouts by 20% through early fault detection


> '20% reduction in emergency maintenance callouts'
>
> 'Estimated 15-20% improvement in maintenance efficiency'
>
> '75% precision@50 for high-priority alerts'
>
> 'Human-in-the-loop validation workflow'


##
---

### The Problem

Residential buildings equipped with smart meters generate high-resolution data from temperature sensors, flow meters, and control systems — yet maintenance teams were still working **reactively**. In many cases, faults such as **stuck radiator valves, failing circulation pumps, boiler inefficiencies, or misconfigured thermostats** weren’t noticed until residents complained.

This led to:

* High number of emergency maintenance callouts
* Unpredictable technician workload
* Higher operating cost due to inefficient heating
* Poor resident comfort and avoidable system degradation

The challenge was to **detect faults early** using IoT data — even when **no labeled historical faults existed.**

---

### The Solution

I built a **production anomaly detection system** capable of analyzing energy and indoor-climate time series to identify patterns that indicate system malfunction.

The solution included:

| Component                 | Details                                                                              |
| ------------------------- | ------------------------------------------------------------------------------------ |
| **Detection Engine**      | Unsupervised anomaly scoring with regression residuals + Local Outlier Factor        |
| **Feedback Loop**         | Human-in-the-loop validation workflow with field technicians                         |
| **Refinement**            | Transition from unsupervised → semi-supervised → supervised modelling as labels grew |
| **Contextual Ranking**    | Alerts prioritized by severity, persistence, and building context                    |
| **Sensor Health Scoring** | Detection of missing data, drift, stuck values, and metadata inconsistencies         |

This evolution enabled the model to move from “noticing abnormal signals” to **identifying meaningful failure patterns** aligned with real-world operations.

---

### Business & Technical Results

The deployed system delivered measurable improvements:

* **~20% reduction in emergency maintenance callouts**
* **Estimated ~15–20% improvement in maintenance efficiency**
* **75% precision@50** for high-priority alerts reviewed by technicians
* Faster identification of faults such as **short-cycling boilers** and **stuck valves**

These gains translated directly into fewer urgent interventions, improved comfort, and reduced operational uncertainty.

---

### Technical Highlights

* Python, scikit-learn, time-series analytics
* Unsupervised → supervised modelling strategy
* Automated feature engineering (lags, gradients, weather data)
* Production MLOps pipeline with monitoring, evaluation, and scheduled retraining
* Integration into building-management dashboards with technician-validated labeling workflows

---

### What I Learned

This project reinforced that anomaly detection in the real world is not a one-shot model problem — it’s an **iterative system** combining:

* Data quality validation
* Human feedback
* Hybrid modelling techniques
* Operational resonance with domain experts

The biggest lesson: **accuracy isn’t enough — the model must produce alerts that technicians trust and can act on.**
