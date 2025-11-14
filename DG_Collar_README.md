# 🐄 DG Collar – Multi-Architecture Telemetry Pipeline
*A comparative project exploring three different designs: Local, Hybrid (Kafka + Azure), and Full Azure.*

This repository contains three implementations of the **DG Collar** telemetry analytics pipeline.
Each version solves the same problem — collecting collar data (temperature, movement, battery), processing it, and generating health insights — but with **different architectural patterns**.

This project demonstrates **architecture thinking**, **trade-off evaluation**, and **cloud/data engineering fundamentals.**

---

# 📚 Project Structure

dg-collar/
│
├── v1-local/              # Local-only solution (Python + files + Power BI)
├── v2-hybrid-kafka-azure/ # Kafka streaming + Azure DWH
├── v3-azure-full/         # Complete Azure IoT architecture
│
└── README.md              # You're here

---

# 🎯 Project Goal

Simulate and process collar telemetry using different data engineering approaches:

✔ Understand ingestion patterns  
✔ Explore streaming vs batch  
✔ Design clean data layers (bronze/silver/gold)  
✔ Compare open-source and Azure-native tools  
✔ Build dashboards and simple alert logic  
✔ Show architectural thinking for cloud roles

---

# 🧩 Version Overview

## 1️⃣ V1 – Local-Only Pipeline (Python + Power BI)

A simple, fully local implementation — no cloud resources.

### Purpose
Understand the problem end-to-end without cloud complexity.

### Tech Stack
- Python (simulation + ETL)
- SQLite or CSV/Parquet storage
- Cron/Task Scheduler for jobs
- Power BI Desktop

### Pipeline
Simulator → Raw Files → ETL Scripts → Aggregates → Power BI

### Strengths
- Easiest to run anywhere  
- Shows ETL/data modeling fundamentals  

---

## 2️⃣ V2 – Hybrid Streaming (Kafka + Azure)

Combines **Kafka streaming** with **Azure for warehousing & analytics**.

### Tech Stack
- Kafka (producer + topic + consumer)
- Python consumer writing to Azure ADLS
- Azure ADLS Gen2 (bronze/silver/gold)
- Azure Synapse or Serverless SQL
- Power BI

### Pipeline
Kafka → ADLS → Synapse → Power BI

### Strengths
- Real streaming ingestion  
- Cloud analytics without cloud ingestion  
- Good intermediate architecture for discussing trade-offs  

---

## 3️⃣ V3 – Full Azure IoT Pipeline

A realistic Azure IoT reference architecture.

### Tech Stack
- Azure IoT Hub  
- Azure Event Hub  
- Azure Functions (rules engine)  
- ADLS Gen2 (bronze/silver/gold)  
- Cosmos DB (latest state)  
- Logic Apps (alerts)  
- Power BI  

### Pipeline
Collar → IoT Hub → Event Hub → Functions → ADLS + Cosmos → Power BI + Alerts

### Strengths
- Most aligned with real IoT architectures  
- Perfect for Azure/Cloud Solution Architect portfolios  

---

# ⚖️ Architecture Comparison

| Feature | V1 Local | V2 Hybrid | V3 Full Azure |
|--------|----------|-----------|---------------|
| Ingestion | File simulation | Kafka topic | IoT Hub |
| Processing | Python scripts | Kafka → Azure | Event Hub + Functions |
| Storage | CSV/SQLite | ADLS | ADLS + Cosmos |
| Alerts | Local logic | Basic rules | Logic Apps |
| Dashboards | Power BI Desktop | Power BI | Power BI |
| Difficulty | ⭐ Easy | ⭐⭐ Medium | ⭐⭐⭐ Hard |
| Best For | ETL fundamentals | Streaming concepts | Cloud architecture |

---

# 📊 Data Layers (All Versions)

All three versions share a simplified Medallion pattern:

- **Bronze** – raw telemetry  
- **Silver** – cleaned & validated  
- **Gold** – daily summaries & alert history  

---

# 🚨 Alert Logic (Shared Logic)

- High Temperature: ≥ 39.5°C  
- Temperature Warning: ≥ 38.5°C  
- Low Activity: below baseline  
- Activity Spike: > 2× baseline  
- Battery Critical: < 10%  
- Device Offline: no data 30+ minutes  

---

# 📝 How to Use This Repo

1. Start with **v1-local** to understand the pipeline.  
2. Explore **v2-hybrid** to learn streaming + cloud warehousing.  
3. Review **v3-azure-full** to understand IoT cloud architecture.  

---

**Status:** Concept-level architecture with partial code implementations.
