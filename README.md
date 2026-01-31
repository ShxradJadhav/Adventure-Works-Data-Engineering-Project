# Adventure-Works-Data-Engineering-Project

![WhatsApp Image 2026-01-09 at 12 21 57 AM](https://github.com/user-attachments/assets/4e7a265a-01b0-46e6-88c2-f9a7a69fedee)




---

# End-to-End : AdventureWorks Azure Data Engineering Project

## 📌 Project Overview

This project implements a **Medallion Architecture (Bronze, Silver, Gold)** using the Azure Data Stack. The goal was to transform raw transactional data from an on-premise style source into a cloud-based **Logical Data Lakehouse** for business intelligence reporting.

### 🏗 Architecture Diagram

## ❓ The Problem

* **Data Silos:** Raw data was stored in disparate CSV formats making it difficult for analysts to query.
* **Scalability:** The previous system couldn't handle the increasing volume of sales data (2015-2017).
* **Manual Effort:** Data cleaning and aggregation were performed manually in Excel, leading to human error and delayed insights.

## ✅ The Solution (The "How")

I built a fully automated pipeline consisting of:

1. **Ingestion (Bronze):** Used **Azure Data Factory (ADF)** to ingest raw CSVs into **Azure Data Lake Storage (ADLS) Gen2**.
2. **Transformation (Silver):** Used **Azure Databricks (PySpark)** to:
* Clean and standardize schemas.
* Implement recursive reads for multi-year sales data.
* Apply business logic (Concatenating names, splitting SKUs, and Date/Timestamp conversions).
* Save data in optimized **Parquet** format.


3. **Serving (Gold):** Created a **Serverless SQL Pool in Azure Synapse Analytics**.
* Implemented **C-TAS (Create Table As Select)** to move final aggregated data to the Gold layer.
* Built an abstraction layer using **Views** to simplify access for BI tools.


4. **Visualization:** Connected **Power BI** to the Synapse Serverless Endpoint to build interactive dashboards.

## 🛠 Challenges & How I Overcame Them

| Challenge | Solution |
| --- | --- |
| **Authentication Security** | Moved from Account Keys to **Service Principals** in Databricks and **Managed Identities (SMI)** in Synapse for a "Secret-less" architecture. |
| **Schema Drift** | Used `inferSchema` and `mergeSchema` in Spark to ensure data consistency across multiple years of sales files. |
| **Performance Bottlenecks** | Converted data from CSV to **Parquet** in the Silver layer, reducing storage costs and increasing query speed by up to 10x. |
| **Connectivity Issues** | Debugged firewall and IAM roles to ensure Synapse had **Storage Blob Data Contributor** access to the Data Lake. |

---



---

