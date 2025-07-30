# Adventure Works - Azure Data Engineering Project

## 📌 Project Overview

This end-to-end data engineering project demonstrates how to build a scalable data pipeline using the **Medallion Architecture** (Bronze, Silver, Gold layers) in Microsoft Azure. It uses the **AdventureWorks** dataset from Kaggle, integrated into a data lake via **ADF**, transformed using **Azure Databricks**, and served through **Azure Synapse Analytics**.

---

## 🧩 Architecture

[![Data Architecture](https://github.com/Venne12/Adventure-Works/blob/main/Architecture/Data%20Architecture.jpeg?raw=true)](https://github.com/Venne12/Adventure-Works/blob/main/Architecture/Data%20Architecture.jpeg?raw=true)

> The data travels through three layers:
- **Bronze (Raw Layer)**: Raw ingestion from GitHub API using ADF.
- **Silver (Transformed Layer)**: Data transformation using PySpark in Azure Databricks.
- **Gold (Serving Layer)**: Data modeling and querying using Synapse SQL Views.

---

## 🗂️ Dataset Details

Pulled from GitHub (originating from Kaggle AdventureWorks data), consisting of the following files:

| Filename | Description |
|----------|-------------|
| `AdventureWorks_Calendar.csv` | Calendar dates |
| `AdventureWorks_Customers.csv` | Customer profiles |
| `AdventureWorks_Product_Categories.csv` | Product categories |
| `AdventureWorks_Product_Subcategories.csv` | Product subcategories |
| `AdventureWorks_Products.csv` | Product information |
| `AdventureWorks_Returns.csv` | Product returns |
| `AdventureWorks_Sales_2015.csv` | Sales for 2015 |
| `AdventureWorks_Sales_2016.csv` | Sales for 2016 |
| `AdventureWorks_Sales_2017.csv` | Sales for 2017 |
| `AdventureWorks_Territories.csv` | Sales territories |

---

## 🛠️ Tools & Technologies

- **Azure Data Factory (ADF)** – Data orchestration
- **Azure Data Lake Storage Gen2** – Data storage
- **Azure Databricks** – Data transformation with PySpark
- **Azure Synapse Analytics** – Data querying and serving
- **GitHub API** – Source for data ingestion
- **Apache Spark** – Big data processing engine

---

## 🚀 Project Phases

### 🔹 Phase 01 – Raw Data Ingestion (Bronze Layer)
- Created Azure resources: Resource Group, ADF, Data Lake Gen2
- Configured 3 containers: `raw-bronze`, `transformed-silver`, `serving-gold`
- Used a **dynamic parameterized pipeline** in ADF with:
  - HTTP source (GitHub)
  - JSON-driven parameters (lookup + ForEach)
  - Output to Bronze container (CSV format)

### 🔹 Phase 02 – Data Transformation (Silver Layer)
- Created Azure Databricks and configured access via **Service Principal**
- Performed data cleaning, joins, casting, and formatting in **PySpark**
- Saved transformed data in **Parquet** format in the Silver container
- Conducted basic data analysis and visualization

### 🔹 Phase 03 – Data Serving (Gold Layer)
- Created **Azure Synapse Analytics** workspace
- Configured **Managed Identity** to access ADLS Gen2
- Used **OPENROWSET()** to create **external Views**
- Served the final cleaned data through **Synapse SQL Serverless Pool**

---

## 📊 Power BI Dashboard – Sales & Returns Analysis

To complete the data pipeline, I connected **Azure Synapse Analytics** with **Power BI** using the **SQL serverless endpoint** to build an interactive report covering key sales and return insights.

This dashboard offers a comprehensive overview across categories, products, and years with filtering capabilities by **date, category, and region**.

### 🔹 Executive Overview Dashboard

![Executive Overview Dashboard](https://github.com/Venne12/Adventure-Works/blob/main/Power%20BI%20Visuals/Executive%20Overview.png?raw=true)

**KPIs Included:**
* Total Sales & Returns
* Return Rate
* Avg Sales per Customer
* Yearly Sales Trend
* Sales by Category
* Returns by Subcategory

### 🔹 Customer Insights Dashboard

![Customer Insights Dashboard](https://github.com/Venne12/Adventure-Works/blob/main/Power%20BI%20Visuals/Customer%20Insights.png?raw=true)

**Insights Provided:**
* Customer Level Insights
* Customer Returns by Marital Status
* Total Returns by Gender
* Average Sales by Income Group
* Total Sales by Marital Status and Gender
* Total Sales and Total Returns by Country

### 🔹 Product Performance Dashboard

![Product Performance Dashboard](https://github.com/Venne12/Adventure-Works/blob/main/Power%20BI%20Visuals/Product%20Performance.png?raw=true)

**Insights Provided:**
* Top 5 Selling Products
* Top 10 Returned Products
* Return Rate by Subcategory
* Sales vs Returns per Product

---

## 🔍 Key Learnings

- Implemented Medallion Architecture in Azure
- Automated data ingestion with ADF using parameterized pipelines
- Used Spark and Databricks for distributed transformations
- Built metadata-driven views using Synapse serverless SQL
- Built a Power BI report which provides key insights on adventure works data.

---

