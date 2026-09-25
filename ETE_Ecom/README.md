# End-to-End Azure Databricks Data Lakehouse Pipeline

An end-to-end modern data engineering pipeline built using Azure Databricks, Delta Lake, Delta Live Tables (DLT), Azure Synapse Analytics, and Power BI. This project demonstrates a complete Medallion Architecture implementation for ingesting, transforming, modeling, and visualizing enterprise data.

---

## 🏗️ Architecture Overview

The architecture follows a multi-stage **Medallion Lakehouse Architecture** (Bronze → Silver → Gold) to deliver high-quality analytical data:

```text
[ Azure Data Factory / Data Sources ]
                 │
                 ▼
┌──────────────────────────────────────────────────┐
│               Databricks Workspace               │
│                                                  │
│   🥉 Bronze Layer (Raw Ingestion / ADLS Gen2)    │
│                 │                                │
│                 ▼ (PySpark Transformations)      │
│   🥈 Silver Layer (Cleaned Data / ADLS Gen2)     │
│                 │                                │
│                 ▼ (Delta Live Tables & Star Schema)│
│   🥇 Gold Layer (Fact & Dim Tables / ADLS Gen2)  │
└────────────────────────┬─────────────────────────┘
                         │
                         ▼
        🏢 Azure Synapse / Data Warehouse
                         │
                         ▼
                📊 Power BI Reports

## 🚀 Pipeline Flow & Tech Stack

### 1. Source & Orchestration
* **Azure Data Factory / Databricks Jobs**: Ingests raw data from source systems into the cloud lakehouse.
* **GitHub**: CI/CD integration for version control and deployment.

### 2. Medallion Architecture (Azure Data Lake Storage Gen2)
* 🥉 **Bronze Layer (Raw Ingestion)**: Ingests raw data into Azure Data Lake Storage Gen2.
* 🥈 **Silver Layer (Transformed Data)**: Cleanses and standardizes data using **PySpark** on Apache Spark.
* 🥇 **Gold Layer (Business Analytics)**: Implemented PySpark DeltaTable MERGE logic to incrementally update and insert records into Unity Catalog Gold tables stored on ADLS Gen2.

### 4. Serving & Visualization
* **Azure Synapse Analytics / Data Warehouse**: Serves structured Gold data for reporting
* **Power BI**: Interactive analytics and dashboards.

---