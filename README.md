# Retail-Data-Analysis-NoSQL

## Overview
This project explores transactional retail data using NoSQL databases (**MongoDB** and **Cassandra**) and Python-based data analytics. It focuses on querying and analyzing customer behavior, product sales, and purchasing patterns across countries and time segments. The dataset was ingested, preprocessed, and queried using **PyMongo** and the **Cassandra Python driver**, with derived features engineered both in Python and inside MongoDB.

## Objectives
- Load and preprocess a real-world e-commerce dataset
- Handle missing values, outliers, and inconsistent records
- Store and query the dataset using MongoDB and Cassandra
- Perform analytical queries to derive business insights
- Visualize patterns in customer spending and product demand

## Dataset Access
Due to file size limitations, the dataset is hosted externally:

🔗 [Download Online Retail Dataset](https://drive.google.com/drive/folders/1vFLlc8ApeZiqQTvonT8J5EpxnnAnEobG?usp=sharing)

> The dataset contains a CSV file of online retail transactions including **Invoice ID, Product Code, Quantity, Unit Price, Customer ID, Country, and Timestamp**.

## Key Features

### Preprocessing
- Dropped rows with missing product **Description**  
- Converted **Quantity** and **UnitPrice** to absolute values to remove negative entries (returns/cancellations not modeled in this version)  
- Converted `InvoiceDate` to datetime format  
- Created derived columns in Python:
  - `TotalCost = Quantity × UnitPrice`
  - `TimeOfDay` (based on hour): Morning, Afternoon, Evening, Night  
- Explored outliers using the IQR method (boxplots for `Quantity`, `UnitPrice`, and `TotalCost`) to understand data spread

### Analytical Queries
Both **MongoDB** (aggregation pipelines) and **Cassandra** (read queries with client-side Python analytics) were used to answer the same core business questions:
- Total revenue per country  
- Top 5 most sold products  
- Most frequent purchase times by country  
- Most purchased product per time of day  
- Top 5 spending customers  
- Average purchase value per customer  

### MongoDB Integration (via PyMongo)
- Inserted a **sample of 2,000 cleaned records** into MongoDB for analysis  
- Performed **in-database feature engineering**:
  - Converted `InvoiceDate` strings to BSON Dates (`$toDate`)
  - Recomputed `TotalCost` with `$multiply`
  - Derived `TimeCategory` (Morning/Afternoon/Evening/Night) using `$switch` on `{$hour: "$InvoiceDate"}`  
- Executed the analytical queries above using **MongoDB aggregation pipelines**

### Cassandra Integration (via Cassandra driver)
- Defined table schema with `PRIMARY KEY (InvoiceNo, StockCode)`  
- Inserted cleaned records after **replacing InvoiceDate with the TimeOfDay label** (stored as text instead of timestamp)  
- Executed the analytical queries above by running **read queries in Cassandra** and applying **aggregations in Python**  

### Data Visualization
- Validated cleaning steps and outlier detection using **boxplots** for numeric fields  
- Visualized aggregate insights (e.g., total quantity purchased by country) using **matplotlib** and **seaborn**  
- Produced exploratory plots to illustrate correlations between purchase behavior, geography, and time-of-day

## Technologies Used
- Python  
- pandas, NumPy  
- matplotlib, seaborn  
- PyMongo (MongoDB connector)  
- Cassandra driver for Python  
- Jupyter Notebook  
