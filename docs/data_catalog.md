# SQL Data Warehouse Project

## Overview
This project demonstrates an end-to-end SQL Data Warehouse implementation using the Medallion Architecture (Bronze, Silver, Gold layers).

The project focuses on:
- Data ingestion
- ETL processing
- Data cleansing
- Data standardization
- Data modeling
- Analytical reporting structures

Built using:
- SQL Server
- T-SQL
- Stored Procedures
- ETL Concepts
- Dimensional Modeling

---

# Architecture

## Medallion Architecture

### Bronze Layer
- Raw source data ingestion
- Stores data as-is from CRM and ERP systems
- Supports traceability and debugging

### Silver Layer
- Cleansed and standardized data
- Handles:
  - Null values
  - Duplicate records
  - Data trimming
  - Standardization
  - Data transformations

### Gold Layer
- Business-ready analytical model
- Contains:
  - Dimension tables
  - Fact tables
  - Aggregated business data

---

# Project Structure

```bash
datasets/
│
├── source_crm/
├── source_erp/

scripts/
│
├── bronze/
├── silver/
├── gold/

docs/
│
├── data_catalog.md
├── architecture.png

README.md
