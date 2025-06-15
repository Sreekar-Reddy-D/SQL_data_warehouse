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
├── datasets/ # Raw source CSV files
├── docs/ # Project documentation and data model diagrams
├── scripts/ # SQL scripts organized by layer (bronze, silver, gold)
├── tests/ # SQL scripts for data validation
├── README.md # Project overview
└── requirements.txt # Optional dependencies

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

- Referential integrity (foreign keys)
- Non-null constraints
- Row counts across ETL stages
- Join consistency between fact and dimension tables
