# SQL Data Warehouse Project

This project demonstrates how to build a data warehouse using Microsoft SQL Server, following structured ETL practices, data modeling, and basic analytics.

## Table of Contents

1. [Overview](#overview)
2. [Project Structure](#project-structure)
3. [Installation](#installation)
4. [Usage](#usage)
5. [Testing & Validation](#testing--validation)

---

## Overview

The goal of this project is to consolidate and transform raw sales data from ERP and CRM systems into a structured star-schema format using SQL Server. It covers:

- Schema design and data modeling (fact/dimension tables)
- ETL process (Bronze → Silver → Gold layers)
- SQL-based analytics and reporting

---

## Project Structure
data-warehouse-project/
- ├── datasets/ # Raw source CSV files
- ├── scripts/ # SQL scripts organized by layer (bronze, silver, gold)
- ├── tests/ # SQL scripts for data validation
- ├── README.md # Project overview
- └── requirements.txt # Optional dependencies

---

## Installation

### Requirements

- Microsoft SQL Server (2016 or later)
- SQL Server Management Studio (SSMS) or compatible T-SQL client

---


## Usage

- Load raw data into the staging tables using the provided CSV files.
- Run the ETL scripts to transform and populate dimension and fact tables.

---

## Testing & Validation

Use the SQL files in the `tests/` folder to validate:

To ensure data integrity and analytical reliability, the project includes dedicated validation scripts for both the Silver and Gold layers of the data warehouse.

### Silver Layer (`tests/silver/quality_check.sql`)
This script performs checks after transformation but before loading into the analytical model. It validates:

- **Primary Key Integrity** – No `NULL` or duplicate primary keys in CRM and product tables.
- **Data Cleanliness** – No unwanted spaces in key text fields.
- **Categorical Consistency** – Ensures standardized values in fields like marital status, gender, and product lines.
- **Date Validity** – Flags unrealistic or incorrectly ordered date values.
- **Business Logic** – Confirms calculated fields (e.g., `sales = quantity × price`) are consistent and non-null.

### Gold Layer (`tests/gold/quality_checks.sql`)
This script checks the final analytical model for:

- **Surrogate Key Uniqueness** – No duplicate `customer_key` or `product_key` values in dimension tables.
- **Referential Integrity** – All foreign keys in the fact table must have matching records in dimension tables.

> Run these checks after ETL stages. Resolve any violations before using the data for reporting or insights.

