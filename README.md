# Sales Data Warehouse Project

## Overview

This project builds a modern **Sales Data Warehouse** on **SQL Server** to consolidate data from multiple source systems and provide a reliable foundation for **analytical reporting** and **business decision-making**.

The warehouse integrates data from **ERP** and **CRM** source systems delivered as **CSV files**, applies data cleansing and standardization, and exposes a business-ready analytical model using a **Medallion Architecture**.

---

## Objective

The main objective of this project is to develop a modern data warehouse that:

- Consolidates sales-related data from multiple source systems
- Cleans and resolves data quality issues before analysis
- Integrates source data into a single, user-friendly analytical model
- Supports reporting and business intelligence use cases
- Provides clear and accessible documentation for both technical and business users

---

## Architecture

This project follows the **Medallion Architecture**, which organizes the warehouse into three logical layers:

## 1. Bronze Layer

**Purpose:** Store raw source data as-is for traceability and debugging.

- **Objective:** Raw, unprocessed data from source systems
- **Object Type:** Tables
- **Load Method:** Full load (`TRUNCATE` + `INSERT`)
- **Transformation:** None
- **Data Modeling:** None
- **Target Audience:** Data Engineers

---

## 2. Silver Layer

**Purpose:** Prepare clean and standardized data for downstream analytics.

- **Objective:** Clean and standardized intermediate data
- **Object Type:** Tables
- **Load Method:** Full load (`TRUNCATE` + `INSERT`)
- **Transformations include:**
    - Data cleaning
    - Data standardization
    - Data normalization
    - Derived columns
    - Data enrichment
- **Data Modeling:** None (still intermediate)
- **Target Audience:** Data Analysts, Data Engineers

---

## 3. Gold Layer

**Purpose:** Deliver business-ready data for reporting and analytics.

- **Objective:** Curated analytical data model
- **Object Type:** Views
- **Load Method:** Derived from transformed layers
- **Transformations include:**
    - Data integration
    - Data aggregation
    - Business logic and rules
- **Data Modeling:**
    - Star schema
    - Aggregated objects
    - Flat tables
- **Target Audience:** Data Analysts, Business Users

---

## ETL / ELT Approach

The project uses a layered transformation approach:

1. **Ingest** raw CSV data from ERP and CRM into the **Bronze** layer
2. **Clean and standardize** the data in the **Silver** layer
3. **Integrate and model** the data in the **Gold** layer for analytics

---

## Load Strategy

Because the project focuses only on the **latest snapshot of data**, historization is not required.

### Loading Method

- **Bronze Layer:** Full load (`TRUNCATE` + `INSERT`)
- **Silver Layer:** Full load (`TRUNCATE` + `INSERT`)
- **Gold Layer:** Business-ready views built on top of transformed data

This simplified approach makes the solution easier to maintain while meeting the current analytical requirements.

---

## Technology Stack

- **Database:** SQL Server
- **Source Format:** CSV files
- **Architecture:** Medallion Architecture
- **Modeling Style:** Star Schema
- **Primary Use Case:** Sales analytics and reporting

---

## Summary

This project delivers a modern SQL Server-based sales data warehouse that integrates ERP and CRM data into a clean, business-ready analytical model. Using a Medallion Architecture and a star schema design, the solution ensures that raw data is traceable, transformed data is standardized, and final data assets are optimized for reporting and decision support.
