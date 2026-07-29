# Data Model

## Dataset Overview

This project uses a transactional coffee shop sales dataset.

Each row in the dataset represents a single sales transaction.

---

## Main Table

### Coffee Shop Sales

The dataset contains information about:

- Transaction Date
- Transaction Time
- Store Location
- Product Category
- Product Type
- Product Detail
- Quantity Sold
- Unit Price

---

## Data Preparation

The following transformations were performed using Power Query:

- Checked for missing values.
- Corrected data types.
- Removed duplicate records.
- Created Date hierarchy.
- Created Time hierarchy.
- Standardized text formatting.

---

## Star Schema

To improve performance and simplify reporting, the transactional table was connected to dimension tables.

### Fact Table

Fact_Sales

Measures:

- Revenue
- Quantity
- Transactions

---

### Dimension Tables

#### Dim_Date

Contains:

- Date
- Day
- Month
- Quarter
- Year
- Weekday

---

#### Dim_Product

Contains:

- Product Category
- Product Type
- Product Detail

---

#### Dim_Store

Contains:

- Store Location

---

## Relationships

Fact_Sales → Dim_Date

Fact_Sales → Dim_Product

Fact_Sales → Dim_Store

All relationships use a One-to-Many relationship from the dimension table to the fact table.

---

## Benefits of the Model

This star schema improves:

- Query performance
- Report scalability
- DAX calculation efficiency
- Dashboard responsiveness