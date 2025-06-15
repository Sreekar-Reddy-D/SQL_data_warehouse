# SQL Data Warehouse

A structured SQL-based data warehouse project designed to store, transform, and analyze organizational data using a star-schema-like approach. This includes ETL processes, dimension and fact tables, and data validation.

---

## 1. Overview

This repository demonstrates how to build a small-scale data warehouse using SQL. The core components include:

- **Schema Design**: Dimension tables like `dim_customer`, `dim_product`, etc., and a central fact table like `fact_sales`.
- **ETL Pipeline**: Scripts to extract raw source data, transform it into clean dimensional models, and load it into warehouse tables.
- **SQL Scripts**: Creation of staging tables, primary/foreign key indexing, and incremental loads.

---

## 2. ETL Pipeline

### Components:

- **Staging Tables**: Raw "landing zone" tables, often prefixed with `stg_`, receiving clean exports from source systems.
- **Dimensions**: Tables such as `dim_customer`, `dim_product`, `dim_region`, etc., with surrogate keys.
- **Fact Table**: `fact_sales` (or similar) stores numerical measures (e.g., revenue, quantity) with foreign key references to dimension tables.

### Flow:

1. **Extract**: Load raw data into staging tables.
2. **Transform**: Clean, deduplicate, and apply business logic.
3. **Load**: 
   - Upsert dimension tables.
   - Insert fact records referencing dimension surrogate keys.

---

## 3. Installation

### Requirements:

- PostgreSQL (or any ANSI-SQL-compatible database)
- psql command-line tool or GUI client

### Setup:

```bash
git clone https://github.com/Sreekar-Reddy-D/SQL_data_warehouse.git
cd SQL_data_warehouse

psql -f 0_create_schema.sql             # Create schema
psql -f 1_staging_tables.sql           # Create staging tables
psql -f 2_dim_tables.sql               # Create dimension tables
psql -f 3_fact_tables.sql              # Create fact tables
psql -f 4_etl_scripts.sql              # Run ETL to populate tables
psql -f 5_indices_and_constraints.sql  # Add keys and indexes
```

## 4. Usage

- **Populate** staging tables with source data.
- **Run ETL scripts** to load the data into dimension and fact tables:
  - `4_etl_scripts.sql` handles the transformation and loading.
- **Execute queries** from `6_queries/sample_queries.sql` for analysis and reporting purposes.

---

## 5. Testing & Validation

Data validation ensures the correctness and integrity of the warehouse. The `tests/` folder includes sample checks.

### Examples:

- ✅ Verify **dimension tables** have no duplicate surrogate keys.
- ✅ Ensure the **fact table** references valid dimension keys (foreign key checks).
- ✅ Use SQL checks such as:
  - `COUNT(*)` to verify row counts.
  - `IS NOT NULL` on critical columns.
  - `JOIN` operations to confirm key relationships.

Customize or extend tests as needed to match your business logic.
