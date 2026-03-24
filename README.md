# 🏥 Hospital Data Pipeline using Snowflake

## 📌 Overview

This project demonstrates an end-to-end data pipeline built using **Snowflake** following the **Medallion Architecture (Bronze → Silver → Gold)**.

The pipeline ingests raw healthcare data from CSV files, performs data cleaning and transformations, and generates analytics-ready data for dashboards. It also includes **automation using Streams & Tasks** and a simple **alerting system for high billing values**.

---

## 🧱 Architecture

```
CSV Files → Stage → Bronze → Silver → Gold → Dashboard
                         ↓
                   Streams & Tasks
                         ↓
                     Automation
```

---

## 🚀 Features

* 📥 Data ingestion using **Stages & COPY INTO**
* 🧹 Data transformation and cleaning (casting, trimming, validation)
* 🥇 Gold layer for analytics (fact table)
* ⚡ Incremental processing using **Streams & Tasks**
* 🚨 Alert system for **high billing values**
* 📊 Dashboard using **Snowsight**
* 🔄 Pipeline designed for **scalability and automation**

---

## 📂 Project Structure

```
hospital-data-pipeline/
│
├── setup.sql        # Database and schema setup
├── bronze.sql       # Raw data ingestion
├── silver.sql       # Data cleaning & transformations
├── gold.sql         # Final analytics table
├── streams.sql      # Streams & Tasks (automation)
├── demo.sql         # Demo queries (testing pipeline)
│
└── data/
    ├── PATIENT_VISITS_Hospital.csv
    ├── BILLING_Hospital.csv
    ├── DIAGNOSIS_Hospital.csv
    ├── DIM_PATIENT_Hospital.csv
    └── DIM_DOCTOR_Hospital.csv
```

---

## 🔄 Data Flow

### 🥉 Bronze Layer

* Raw CSV data is loaded into Snowflake tables
* No transformations applied
* Acts as source of truth

### 🥈 Silver Layer

* Data cleaning and transformation
* Type casting (STRING → NUMBER/DATE)
* Handling null and invalid values
* Derived columns (e.g., `TOTAL_CHARGES`)

### 🥇 Gold Layer

* Final **fact table** created using joins
* Combines:

  * Patient visits
  * Billing
  * Diagnosis
  * Patient & Doctor details
* Optimized for analytics

---

## ⚡ Automation

* **Streams** track incremental changes in data
* **Tasks** automatically load new data into Gold layer
* Ensures near real-time processing

---

## 🚨 Alerting System

* Identifies unusually high billing values

```sql
SELECT * 
FROM GOLD.FACT_VISITS
WHERE TOTAL_CHARGES > 2000;
```

* Can be extended for real-time monitoring

---

## 📊 Dashboard Insights

### 🔹 KPIs

* Total Visits
* Total Revenue
* Unique Patients

### 🔹 Insights

* Revenue by Department
* Revenue by Doctor
* Visit Trends over Time

---

## ▶️ How to Run

1. Run `setup.sql`
2. Upload CSV files to Snowflake stage
3. Run `bronze.sql`
4. Run `silver.sql`
5. Run `gold.sql`
6. Run `streams.sql`
7. Use `demo.sql` for testing automation

---

## 💡 Key Concepts Used

* Snowflake Stages
* COPY INTO
* File Formats
* Streams & Tasks
* Data Transformation
* Medallion Architecture
* Incremental Processing

---

## 🔮 Future Enhancements

* Snowpipe for fully automated ingestion
* Real-time alerts (email/notifications)
* Advanced anomaly detection (ML-based)
* Role-based access control (RBAC)

---

## 🎯 Conclusion

This project demonstrates how to build a **scalable, automated, and analytics-ready data pipeline** using Snowflake, enabling real-time insights and better decision-making.

---
