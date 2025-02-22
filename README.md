# **ETL Process Presentation**

## 📌 Overview
This repository contains a presentation on **Extract, Transform, Load (ETL) Process**, covering its essential components, operations, and real-world applications. The presentation also includes an **SQL-based ETL example** to demonstrate how data is extracted, transformed, and loaded into a structured format.

## 📂 Contents
- 📄 **ETL_ppt_pdf.pdf** – Detailed explanation of the ETL process
- 📝 **SQL ETL Example** – Sample SQL queries demonstrating ETL in action

## 🚀 Topics Covered
- ✔ **What is ETL?** – Explanation of Extract, Transform, Load
- ✔ **Why ETL?** – Importance of ETL for data analytics
- ✔ **ETL Operations** – Data cleansing, keys/IDs, combining/merging data
- ✔ **ETL Tools** – SQL, IBM DataStage, AWS, Azure Data Factory, etc.
- ✔ **SQL ETL Example** – Demonstrating ETL using SQL queries

## 🛠 SQL ETL Example
```sql
SELECT * FROM sales_raw;

CREATE TEMP TABLE transformed_sales AS
SELECT DISTINCT sale_id, 
       product_name, 
       sales_amount, 
       cost_price, 
       (sales_amount - cost_price) AS profit, 
       DATE(sale_timestamp) AS sale_date
FROM sales_raw;

CREATE TABLE IF NOT EXISTS sales_data (
    sale_id INTEGER PRIMARY KEY, 
    product_name TEXT, 
    sales_amount NUMERIC, 
    cost_price NUMERIC, 
    profit NUMERIC, 
    sale_date DATE
);

INSERT INTO sales_data 
SELECT * FROM transformed_sales;
