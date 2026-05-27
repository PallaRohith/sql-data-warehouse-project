# 🚀 Modern SQL Data Warehouse Project

<p align="center">
  <img src="https://img.shields.io/badge/SQL%20Server-Data%20Warehouse-red?style=for-the-badge&logo=microsoftsqlserver" />
  <img src="https://img.shields.io/badge/Architecture-Medallion-blue?style=for-the-badge" />
  <img src="https://img.shields.io/badge/ETL-Pipeline-green?style=for-the-badge" />
  <img src="https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge" />
</p>

---

# 📖 Overview

This project demonstrates the implementation of a **Modern SQL Data Warehouse** using **SQL Server** and industry-standard **Medallion Architecture** principles.

The solution consolidates sales data from multiple business systems (**CRM** and **ERP**) into a unified analytical model optimized for reporting, analytics, and business intelligence.

The project simulates a real-world **Data Engineering pipeline** involving:

- Data Ingestion
- ETL Pipeline Development
- Data Cleansing
- Data Standardization
- Data Integration
- Dimensional Modeling
- Fact & Dimension Tables
- Analytical Data Modeling
- Star Schema Design

---

# 🏗️ Architecture

## Medallion Architecture

The project follows a layered Medallion Architecture approach:

```text
                 ┌─────────────────┐
                 │   CRM SYSTEM    │
                 └────────┬────────┘
                          │
                 ┌────────▼────────┐
                 │   ERP SYSTEM    │
                 └────────┬────────┘
                          │
             ┌────────────▼────────────┐
             │      BRONZE LAYER       │
             │    Raw Source Data      │
             └────────────┬────────────┘
                          │
             ┌────────────▼────────────┐
             │      SILVER LAYER       │
             │ Cleaned & Standardized  │
             └────────────┬────────────┘
                          │
             ┌────────────▼────────────┐
             │       GOLD LAYER        │
             │ Business Ready Model    │
             └────────────┬────────────┘
                          │
               ┌──────────▼──────────┐
               │ Analytics & Reports │
               └─────────────────────┘
```

---

# 🎯 Project Requirements

## Objective

Develop a modern data warehouse using SQL Server to consolidate sales data, enabling analytical reporting and informed decision-making.

---

## Specifications

### 📂 Data Sources
Import data from two source systems:

- CRM System
- ERP System

Source data is provided as CSV files.

---

### 🧹 Data Quality
Clean and resolve data quality issues before loading data into analytical layers.

Examples:

- Remove duplicate records
- Handle null values
- Standardize inconsistent values
- Remove unwanted spaces
- Validate business rules

---

### 🔄 Data Integration
Combine ERP and CRM datasets into a unified analytical data model.

---

### 📊 Scope

- Process latest available dataset only
- No historization required
- Full load ETL strategy

---

### 📝 Documentation
Provide structured documentation for:

- ETL Pipelines
- Data Models
- Layer Architecture
- Fact & Dimension Tables

---

# 🥉 Bronze Layer

## Purpose
The Bronze Layer stores raw source data exactly as received from the source systems.

## Characteristics

- Raw and unprocessed data
- Full data ingestion using BULK INSERT
- Maintains source-level traceability
- Supports debugging and recovery

## ETL Operations

- BULK INSERT
- TRUNCATE + LOAD
- Raw file ingestion


# 🥈 Silver Layer

## Purpose
The Silver Layer transforms raw datasets into clean, validated, and standardized data.

## Data Processing

### ✅ Data Cleansing

- Remove duplicates
- Handle null values
- Trim unwanted spaces
- Validate records

### ✅ Standardization

Examples:

| Raw Value | Standardized Value |
|---|---|
| M | Male |
| F | Female |
| S | Single |

---

### ✅ Deduplication

```sql
ROW_NUMBER() OVER (
    PARTITION BY cst_id
    ORDER BY cst_create_date DESC
)
```

---

### ✅ Null Handling

```sql
COALESCE(column_name, 'n/a')
```

---

### ✅ Data Cleaning

```sql
TRIM(cst_firstname)
```

---

## Example Silver Tables

```sql
silver.crm_cust_info
silver.crm_prd_info
silver.crm_sales_details
```

---

# 🥇 Gold Layer

## Purpose
The Gold Layer provides business-ready analytical datasets optimized for reporting and dashboarding.

## Architecture

The Gold Layer follows a **Star Schema** design.

```text
                 dim_products
                       │
                       │
      dim_customers ─ fact_sales
```

---

# 📌 Dimension Tables

## 👤 dim_customers
Contains:

- Customer information
- Demographics
- Geographic details
- Gender & marital status

---

## 📦 dim_products
Contains:

- Product hierarchy
- Product categories
- Product lines
- Maintenance information

---

# 📈 Fact Table

## 💰 fact_sales
Stores transactional sales metrics.

### Measures

- Sales Amount
- Quantity
- Price

### Foreign Keys

- customer_key
- product_key

---

# 🔄 ETL Pipeline

## Bronze ETL

```text
CSV Files → Bronze Tables
```

Processes:
- BULK INSERT
- Full Load
- Raw Ingestion

---

## Silver ETL

```text
Bronze → Data Cleansing → Silver
```

Processes:
- Deduplication
- Data Standardization
- Null Handling
- Data Validation

---

## Gold ETL

```text
Silver → Business Modeling → Gold
```

Processes:
- Fact Table Creation
- Dimension Table Creation
- Star Schema Modeling
- Analytical Data Preparation

---

# 🧠 Data Modeling Concepts Used

| Concept | Implementation |
|---|---|
| Medallion Architecture | ✅ |
| ETL Pipeline | ✅ |
| Star Schema | ✅ |
| Fact Table | ✅ |
| Dimension Tables | ✅ |
| Surrogate Keys | ✅ |
| Data Cleansing | ✅ |
| Window Functions | ✅ |
| Data Integration | ✅ |
| Business Rules | ✅ |
| Audit Columns | ✅ |

---

# ⚙️ Technologies Used

| Technology | Purpose |
|---|---|
| SQL Server | Database Platform |
| T-SQL | ETL Development |
| SSMS | SQL Development |
| CSV Files | Source Data |
| Stored Procedures | ETL Automation |

---

# 📂 Project Structure

```bash
sql-data-warehouse-project/
│
├── datasets/
│   ├── source_crm/
│   └── source_erp/
│
├── scripts/
│   ├── bronze/
│   ├── silver/
│   └── gold/
│
├── docs/
│   ├── data_catalog.md
│   └── architecture.png
│
├── README.md
└── LICENSE
```

---

# 🛡️ License

This project is licensed under the MIT License.

You are free to:

- Use
- Modify
- Distribute
- Share

this project with proper attribution.

---

# 👨‍💻 Author

## Rohith Palla

Junior Software Engineer | Data Engineering Enthusiast

---

# ⭐ If you found this project helpful, consider giving it a star!
