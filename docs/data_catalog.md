# Data Catalog for Gold Layer

## Overview
The Gold Layer represents the business-ready data model designed for reporting, analytics, and dashboarding purposes.

This layer follows a Star Schema design consisting of:
- Dimension Tables
- Fact Tables

The goal is to provide clean, integrated, and analytical-friendly data for business users and analysts.

---

# Dimension Tables

## gold.dim_customers

### Purpose
Stores customer-related information enriched from CRM and ERP systems.

### Columns

| Column Name      | Data Type    | Description |
|------------------|--------------|-------------|
| customer_key     | INT          | Surrogate key for the customer dimension table. |
| customer_id      | INT          | Unique customer identifier from the source system. |
| customer_number  | NVARCHAR(50) | Business customer identifier. |
| first_name       | NVARCHAR(50) | Customer first name. |
| last_name        | NVARCHAR(50) | Customer last name. |
| country          | NVARCHAR(50) | Customer country information. |
| marital_status   | NVARCHAR(50) | Marital status of the customer. |
| gender           | NVARCHAR(50) | Gender of the customer. |
| birthdate        | DATE         | Customer birth date. |
| create_date      | DATE         | Record creation date. |

---

## gold.dim_products

### Purpose
Stores product-related information including categories and product hierarchy.

### Columns

| Column Name          | Data Type    | Description |
|----------------------|--------------|-------------|
| product_key          | INT          | Surrogate key for the product dimension table. |
| product_id           | INT          | Product identifier from source systems. |
| product_number       | NVARCHAR(50) | Business product code. |
| product_name         | NVARCHAR(50) | Product descriptive name. |
| category_id          | NVARCHAR(50) | Product category identifier. |
| category             | NVARCHAR(50) | High-level product category. |
| subcategory          | NVARCHAR(50) | Detailed product category. |
| maintenance_required | NVARCHAR(50) | Indicates whether maintenance is required. |
| cost                 | INT          | Product cost amount. |
| product_line         | NVARCHAR(50) | Product line classification. |
| start_date           | DATE         | Product availability start date. |

---

# Fact Tables

## gold.fact_sales

### Purpose
Stores transactional sales data used for business analysis and reporting.

### Columns

| Column Name   | Data Type    | Description |
|----------------|-------------|-------------|
| order_number   | NVARCHAR(50) | Unique sales order number. |
| product_key    | INT          | Foreign key to dim_products. |
| customer_key   | INT          | Foreign key to dim_customers. |
| order_date     | DATE         | Date when the order was placed. |
| shipping_date  | DATE         | Date when the order was shipped. |
| due_date       | DATE         | Payment due date. |
| sales_amount   | INT          | Total sales amount. |
| quantity       | INT          | Number of products sold. |
| price          | INT          | Unit price of the product. |

---

# Data Model

## Star Schema Overview

The Gold Layer follows a Star Schema model:

- `fact_sales` acts as the central fact table.
- `dim_customers` provides customer details.
- `dim_products` provides product details.

This structure is optimized for:
- Reporting
- Aggregation
- Dashboarding
- Business Intelligence tools

---

# Business Use Cases

The Gold Layer supports:
- Sales analysis
- Customer behavior analysis
- Product performance tracking
- Revenue reporting
- KPI dashboards

---

# Notes

- The Gold Layer contains only cleaned and validated data.
- Data is integrated from CRM and ERP systems.
- Surrogate keys are used for dimensional modeling.
- The model is optimized for analytical workloads.
