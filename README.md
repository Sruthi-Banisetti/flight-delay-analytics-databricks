# ✈️ Flight Delay Intelligence Platform
End-to-End Data Engineering, Analytics, and Machine Learning using Databricks

---

## 📌 Project Overview
Flight delays impact airline operations, airport efficiency, and passenger experience.  
This project builds an end-to-end data platform to analyze historical flight delays and predict whether a flight will be delayed before departure.

The focus of the project is not only model accuracy, but building a **complete, explainable workflow** from raw data ingestion to business insights and AI-driven decision support.

---

## 🎯 Problem Statement
Airlines and airports often struggle to answer:
- When do delays happen most frequently?
- Which airlines, routes, or airports are most affected?
- Are delays caused by operational issues or external factors?
- Can delays be predicted in advance to take proactive action?

Traditional rule-based approaches fail because flight delays depend on **multiple interacting factors** such as congestion, airline operations, time of day, and weather.

---

## 🧠 AI Framing
- **ML Task:** Binary classification  
- **Objective:** Predict whether a flight will be delayed (arrival delay > 15 minutes)
- **Why AI:** Delay patterns are non-linear and cannot be reliably captured using fixed rules
- **Output:** `is_delayed` (1 = delayed, 0 = on-time)
- **Evaluation Metric:** AUC (Area Under ROC Curve)

---

## 📂 Dataset
- **Source:** Public Kaggle dataset (US flight data, 2019–2023)
- **Granularity:** One record per flight
- **Key attributes:**
  - Airline, origin, destination
  - Scheduled and actual times
  - Delay duration and delay causes
  - Cancellation and diversion flags

---

## 🏗️ Architecture
The project follows a **Medallion Architecture** to ensure scalability, clarity, and data quality.

Raw CSV Files
↓
Unity Catalog Volume
↓
Bronze Layer (Raw Delta Tables)
↓
Silver Layer (Cleaned & Transformed)
↓
Gold Layer (Analytics & ML Ready)
↓
SQL Dashboards & ML Models


---

## 🧱 Data Processing Layers

### Bronze Layer
- Raw data ingested as Delta tables
- No transformations applied
- Ingestion timestamp added
- Acts as the source of truth

### Silver Layer
- Missing and noisy data handled
- Cancelled flights removed from ML dataset
- Business rules applied
- Derived time-based and operational features

### Gold Layer
- Final analytics and ML-ready dataset
- Used by dashboards and machine learning models

---

## 🔧 Feature Engineering & Preprocessing
Key features created include:
- Delay indicator (`is_delayed`)
- Departure hour, day of week, month
- Peak vs off-peak hour indicator
- Route and airline features
- Delay cause indicators (weather, carrier, NAS, late aircraft)

**Business rules applied:**
- A flight is delayed if arrival delay > 15 minutes
- Peak hours defined as 7–10 AM and 4–8 PM
- Extreme delay values capped using percentile logic

---

## 📊 Analytics & Insights
A SQL-based dashboard was created to provide operational insights, including:
- Overall delay rate
- Airline-wise delay comparison
- High-risk routes with high delay frequency
- Peak vs off-peak delay impact
- Primary contributors to delays

These insights help identify **where delays occur, when they spike, and why they happen**.

---

## 🤖 Machine Learning Model
- **Model:** Logistic Regression
- **Reasoning:** Interpretable, fast, and suitable as a baseline model
- **Training:** Train/test split on Gold-layer dataset
- **Metric:** AUC

The model predicts delay risk before departure, enabling proactive decision-making rather than reactive analysis.

---

## 🔁 MLflow & Experiment Tracking
MLflow is used to:
- Track experiments
- Log model parameters and metrics
- Store trained models as artifacts

Model artifacts are stored in a **Unity Catalog–managed volume**, ensuring governance and reproducibility on Databricks serverless compute.

---

## ⏱️ Orchestration
The data pipeline is automated using **Databricks Jobs**, executing:
1. Bronze ingestion
2. Silver transformation
3. Gold feature generation
4. ML model training 

This ensures consistent, repeatable execution without manual intervention.

---

## 🔐 Governance
- Tables and volumes are registered in **Unity Catalog**
- Managed volumes used for raw data storage
- Clear ownership and auditability

The design is enterprise-ready, even though the project runs in a single-user environment.

---

## 📈 Business Impact
This system helps:
- Airlines identify high-risk flights in advance
- Airports plan resources during peak congestion
- Reduce operational disruptions
- Improve passenger experience

The combination of analytics and AI enables **data-driven operational decisions**.

---

## ⚠️ Assumptions & Limitations
**Assumptions:**
- Historical delay patterns are representative
- Delay threshold fixed at 15 minutes

**Limitations:**
- No real-time weather integration
- Random train/test split
- Baseline model only

---

## 🔮 Future Enhancements
- Time-based validation
- Non-linear models (Random Forest, XGBoost)
- Real-time inference pipeline
- External weather data integration

---
This project demonstrates my ability to:
- Design scalable data pipelines
- Apply machine learning thoughtfully
- Generate business insights
- Automate workflows
- Document and explain complex systems clearly

It reflects **real-world data engineering and analytics practices** using Databricks.

