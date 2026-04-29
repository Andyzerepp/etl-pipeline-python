# Mini ETL Pipeline in Python

## Overview
A lightweight ETL (Extract, Transform, Load) pipeline built in Python that simulates
a real-world data engineering workflow. Raw retail sales data is extracted from a CSV
file, cleaned and transformed using Pandas, and loaded into a SQLite database.
Pipeline activity is tracked via a log file.

## Tech Stack
- Python 3
- Pandas
- SQLite / sqlite3
- Google Colab
- Google Drive

## Project Structure
| File | Description |
|---|---|
| `data/sales_data.csv` | Raw input data (200 rows of retail sales) |
| `logs/etl.log` | Pipeline activity log |
| `etl_pipeline.db` | SQLite database (output) |
| `etl_pipeline.ipynb` | Main notebook |

## Pipeline Stages

### Extract
Reads raw sales data from a CSV file into a Pandas DataFrame.
Handles missing files gracefully with error logging.

### Transform
Applies the following cleaning steps:
- Converts order_date from string to datetime
- Fills missing customer_name with "Unknown"
- Fills missing category with "Uncategorized"
- Fills missing unit_price with the median price
- Standardizes status values to lowercase
- Removes rows with invalid (negative) quantity
- Adds a derived total_sale column (quantity x unit_price)

### Load
Writes the cleaned DataFrame into a SQLite database table called sales.
Verifies the load by querying row count and aggregating revenue by region.

### Logging
All pipeline stages are logged with timestamps to etl.log,
including row counts, errors, and completion status.

## Sample Output
region    orders    revenue
East      55        58467.39
West      44        50017.65
North     50        49647.68
South     50        34187.89

## Key Concepts Demonstrated
- ETL pipeline design and structure
- Data cleaning and transformation with Pandas
- Relational data storage with SQLite
- Error handling and logging best practices
- Reproducible data workflows in Google Colab
