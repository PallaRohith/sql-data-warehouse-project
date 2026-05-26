# Modern SQL Data Warehouse Project

## Overview

This project demonstrates the implementation of a modern SQL Data Warehouse using SQL Server and Medallion Architecture principles.

The solution consolidates data from multiple business systems (ERP and CRM), transforms raw datasets into analytical-ready structures, and delivers a clean and scalable data model for reporting and business intelligence.

The project focuses on:
- Data ingestion
- ETL pipeline development
- Data cleansing
- Data standardization
- Data integration
- Dimensional modeling
- Analytical reporting structures

---

# Project Requirements

## Objective

Develop a modern data warehouse using SQL Server to consolidate sales data, enabling analytical reporting and informed decision-making.

---

## Specifications

### Data Sources
Import data from two source systems:
- ERP System
- CRM System

Source data is provided as CSV files.

---

### Data Quality
Clean and resolve data quality issues before loading data into analytical layers.

Examples:
- Remove duplicate records
- Handle null values
- Standardize inconsistent data
- Trim unwanted spaces
- Validate business rules

---

### Data Integration
Combine ERP and CRM datasets into a unified and business-friendly analytical model.

---

### Scope
- Process only the latest available dataset
- No historization or Slowly Changing Dimensions (SCD)
- Full load processing approach

---

### Documentation
Provide clear and structured documentation for:
- Data model
- ETL processes
- Layer architecture
- Business entities

---

# Architecture

## Medallion Architecture

The project follows a three-layer Medallion Architecture approach:

```text
ERP + CRM Sources
        ↓
    Bronze Layer
        ↓
    Silver Layer
        ↓
     Gold Layer
        ↓
Analytics & Reporting
