📊 Data Warehouse Project – Bronze Silver Gold Architecture
📌 Project Overview
This project implements a Data Warehouse using the Bronze–Silver–Gold architecture with a batch ETL pipeline.
The goal is to transform raw data from multiple source systems into business-ready dimension and fact tables suitable for analytics and reporting.

The pipeline follows a full extraction and full load strategy with SCD Type-1 (overwrite) logic for dimension handling.

🏗️ Architecture Overview
Source Systems
   ↓
Bronze Layer (Raw)
   ↓
Silver Layer (Cleansed & Standardized)
   ↓
Gold Layer (Dimensional Model)

📥 Source Systems
CRM systems
ERP systems
Flat files (CSV)
OLTP databases


Extraction Type:
Batch processing
Full data extraction

🥉 Bronze Layer – Raw Data
Purpose:
The Bronze layer stores raw, unprocessed data exactly as received from the source systems.
It acts as a data landing zone for audit, traceability, and reprocessing.

Characteristics:
Data stored as-is
No business logic applied
Full load on every run

Load Strategy:
Batch processing
Full extract
Full load
Truncate & Insert

Transformations:
None


🥈 Silver Layer – Cleansed & Standardized Data
Purpose:
The Silver layer contains cleaned, standardized, and conformed data.
This layer prepares data for dimensional modeling.

Key Transformations:
Data cleansing (null handling, trimming, validation)
Standardization (dates, formats, codes)
Deduplication
Derived columns
Data enrichment

Load Strategy:
Batch processing
Full load
Truncate & Insert
SCD Type-1 (Overwrite) for dimensions

Data Model:
Conformed tables
No historical tracking (overwrite only)


🥇 Gold Layer – Business / Presentation Layer
Purpose:
The Gold layer provides business-ready curated tables designed using dimensional modeling.
These tables are optimized for analytics, reporting, and downstream consumption.

Output Tables:
gold.dim_customer
gold.dim_product
gold.fact_sales

Load Strategy:
Batch processing
Full load
Truncate & Insert

Transformations:
Data integration across domains
Aggregations
Business rules
KPI calculations
Data Model
Star Schema
Fact and Dimension tables

🔄 ETL Processing Details
ETL implemented using batch jobs / stored procedures
Each run processes complete datasets

Dependencies follow:
Bronze → Silver → Gold


Errors and failures can be reprocessed from Bronze

📐 Design Decisions
Full Load chosen for simplicity and reliability
SCD Type-1 used where historical tracking is not required

Bronze–Silver–Gold separation ensures:
Data quality
Scalability
Clear responsibility per layer

🚀 Future Enhancements
Incremental loading
SCD Type-2 for dimensions
ETL orchestration using Airflow / ADF
Data quality and validation framework
BI or semantic layer on top of Gold


Conclusion:
This project demonstrates a production-style Data Warehouse design with clear layering, transformation responsibility, and dimensional modeling.
It follows industry-standard data engineering practices and is suitable for analytics-ready data delivery.
