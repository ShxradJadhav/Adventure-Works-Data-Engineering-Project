# 🚀 AdventureWorks: End-to-End Azure Data Engineering Project
[![Azure](https://img.shields.io/badge/Provider-Azure-0072C6?style=flat-square&logo=microsoft-azure)](https://azure.microsoft.com/)
[![Databricks](https://img.shields.io/badge/Processing-Databricks-E25A1C?style=flat-square&logo=databricks)](https://www.databricks.com/)
[![Synapse](https://img.shields.io/badge/Analytics-Synapse-005A9E?style=flat-square&logo=microsoft-azure)](https://azure.microsoft.com/en-us/services/synapse-analytics/)

## 📌 Project Overview
This project implements a **Medallion Architecture** (Bronze, Silver, Gold) to transform raw transactional data into a cloud-based **Logical Data Lakehouse**. The solution automates the ingestion, cleaning, and aggregation of AdventureWorks sales data to provide actionable business intelligence.

---

## 🏗 Architecture Diagram

![Project Architecture](https://github.com/user-attachments/assets/4e7a265a-01b0-46e6-88c2-f9a7a69fedee)

The data flow follows these stages:
1. **Ingestion (Bronze):** Raw CSV files are moved from source to ADLS Gen2 via **Azure Data Factory**.
2. **Transformation (Silver):** Data is cleaned, standardized, and converted to **Parquet** format using **PySpark** in Databricks.
3. **Serving (Gold):** Business-level aggregates are created in **Azure Synapse Analytics** via Serverless SQL Pools for reporting.

---

## 🛠 Tech Stack
- **Orchestration:** Azure Data Factory (ADF)
- **Data Lake:** Azure Data Lake Storage (ADLS) Gen2
- **Compute:** Azure Databricks (Spark 3.x)
- **Data Warehouse:** Azure Synapse Analytics (Serverless SQL)
- **Visualization:** Power BI
- **Security:** Azure Key Vault & Managed Identities (SMI)

---

## ✅ Key Solutions Provided

### 1. Schema Drift & Evolution
Implemented recursive reads in **PySpark** to handle varying sales data schemas from 2015-2017. Used `mergeSchema` options to ensure consistent Dataframe writes.

### 2. Performance Optimization
Converted heavy CSV files into optimized **Snappy-compressed Parquet** files in the Silver layer. This reduced storage footprint and boosted query performance by **~10x** in the Gold layer.

### 3. "Secret-less" Architecture
Configured **Service Principals** and **Azure Key Vault** for secure authentication between Databricks and ADLS, eliminating the need for hard-coded access keys.

---

## 📂 Repository Structure
- `/pipelines/`: ADF JSON exports for ingestion logic.
- `/notebooks/`: PySpark notebooks for Silver & Gold transformations.
- `/sql/`: Synapse Serverless SQL scripts for views and CTAS.
- `/docs/`: Architecture diagrams and data dictionary.

---

## 📈 Final Result
The final pipeline serves a refined Gold layer accessible via **Synapse Serverless SQL**, enabling real-time Power BI dashboarding with zero infrastructure management.

---

### 👨‍💻 Author
**Sharad Jadhav** *Data Engineer | Azure Specialist* [LinkedIn](https://www.linkedin.com/in/iamsharadjadhav/) | [Portfolio](https://github.com/ShxradJadhav)
