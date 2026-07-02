# Cloud-Based E-commerce Data Pipeline (ETL & BI)

An end-to-end cloud data engineering and business intelligence project implementing the **Medallion Architecture** (Bronze ➔ Silver ➔ Gold) to process, clean, and visualize e-commerce operations data.

---

## Project Architecture & Data Flow

The project automates data movement across the modern data stack using an architecture built entirely on Microsoft Azure:

1. **Bronze Layer (Raw Storage):** Raw data (`20,000` transactional records) is securely stored in **Azure Blob Storage**.
2. **Silver Layer (Cleaned & Validated):** A **Python (Pandas)** ETL script extracts the raw data, applies rigorous cleaning logic, conducts feature engineering, and loads the data into an **Azure SQL Database**.
3. **Gold Layer (Aggregated Views):** Advanced **SQL queries and Views** pre-aggregate metrics to drive maximum query performance for business reporting.
4. **BI & Visualization:** An executive **Power BI Dashboard** connects live to the Azure SQL Gold views to stream key performance indicators (KPIs) and operational trends.

---

## Tech Stack & Tools
* **Language:** Python 3.12 (Pandas, SQLAlchemy, PyODBC, Python-Dotenv)
* **Cloud Infrastructure:** Microsoft Azure (Blob Storage, Azure SQL Database)
* **Database Management:** T-SQL (Views, Aggregations, Optimization)
* **Business Intelligence:** Power BI Desktop (Data Modeling, Dashboard Design)

---

## Key Business Insights Discovered
* **Operational Bottleneck:** Analysis revealed that orders in the *Processing* stage take an average of **4 days** internally before shipment—longer than the actual transit delivery time (3 days). This alerts management to warehouse fulfillment constraints.
* **Data Cleansing Impact:** Filtering out cancelled orders removed approximately 7% of data noise, protecting net revenue calculations from inflation.
* **Data Governance Enforcement:** Integrated financial validation equations directly into the ETL transformation phase to automatically verify that net amounts accurately match gross revenue minus discounts before analytical ingestion.

---

## Dashboard Features
*(Note: Replace this text with your final dashboard screenshot once uploaded to GitHub)*

The executive Power BI layout delivers insights at a glance:
* **Top-Line KPIs:** High-level summary cards tracking *Total Net Revenue*, *Total Orders*, and *Average Order Value*.
* **Monthly Sales Trends:** Line charts showing chronological net revenue fluctuations over time.
* **Fulfillment Monitoring:** Clustered bar charts breaking down average shipping durations across order statuses to point out logistical delays.

---

## How to Run Locally

### 1. Prerequisites
Ensure you have the required ODBC Driver installed on your machine for SQL Server connection.

### 2. Environment Setup
Create a `.env` file in the root directory and securely add your cloud credentials:
```env
BLOB_CONN_STRING="your_azure_blob_connection_string"
DB_SERVER="your_azure_sql_server_address"
DB_NAME="ecommerce_db"
DB_USER="your_database_username"
DB_PASS="your_database_password"
