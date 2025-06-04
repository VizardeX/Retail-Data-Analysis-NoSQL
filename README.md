# Retail-Data-Analysis-NoSQL

## Overview
This project explores transactional retail data using NoSQL databases (MongoDB and Cassandra) and Python-based data analytics. It focuses on querying and analyzing customer behavior, product sales, and purchasing patterns across countries and time segments. The data was ingested, preprocessed, and queried using PyMongo and the Cassandra Python driver.

## Objectives
- Load and preprocess real-world e-commerce data
- Store and query the dataset using MongoDB and Cassandra
- Perform analytical queries to derive business insights
- Visualize patterns in customer spending and product demand

## Dataset Access

Due to file size limitations, the dataset is hosted externally:

🔗 [Download Online Retail Dataset](https://drive.google.com/drive/folders/1vFLlc8ApeZiqQTvonT8J5EpxnnAnEobG?usp=sharing)

> The dataset contains a CSV file of online retail transactions including Invoice ID, Product Code, Quantity, Unit Price, Customer ID, Country, and Timestamp.

## Key Features

### Preprocessing
- Cleaned missing and inconsistent data using pandas
- Converted `InvoiceDate` to datetime format
- Created derived columns:
  - `TotalCost = Quantity × UnitPrice`
  - `TimeOfDay` (based on hour): Morning, Afternoon, Evening, Night

### MongoDB Integration (via PyMongo)
- Inserted cleaned data into MongoDB
- Performed advanced aggregation queries:
  - Total revenue per country
  - Top 5 most sold products
  - Most frequent purchase times by country
  - Most purchased product per time of day
  - Top 5 spending customers
  - Average purchase value per customer

### Cassandra Integration (via Cassandra driver)
- Defined appropriate table schema
- Inserted records using Python and executed read queries
- Applied basic analytics using CQL

### Data Visualization
- Plotted insights using:
  - matplotlib
  - seaborn
- Bonus: Correlation between quantity purchased and country

## Technologies Used

- Python
- pandas, NumPy
- matplotlib, seaborn
- PyMongo (MongoDB connector)
- Cassandra driver for Python
- Jupyter Notebook

