# CMSC408 – Homework 8 – Spring 2025

## Overview

This project analyzes the World Bank’s World Development Indicators (WDI) database.  
You’ll load WDI country, series, and data tables into MySQL, then write and execute a series of SQL queries—ranging from basic SELECTs to multi-CTE pivots—to explore global economic and social indicators.  

## Project Files

- `loader.qmd` — Quarto script that downloads the WDI CSV zip, extracts the three CSVs, and writes them into your MySQL database.  
- `report.qmd` — Quarto markdown file containing all 21 Tasks (SQL code cells) and your Reflection. Renders to `report.html`.  
- `.env` — Environment file with your database credentials (not checked into Git).  
- `helpers.py` — Python helper functions for Quarto: creating the SQLAlchemy engine, running queries, rendering HTML.  
- `HW8_Database_Data.pdf` — Reference PDF showing the WDI tables in phpMyAdmin.  

## Requirements

You need the following installed:

- Python 3.10+  
- Quarto  
- MySQL server with the `world_bank_data` schema  
- A MySQL user with SELECT (and, if doing Task 4/13 DDL, DROP/CREATE/UPDATE) privileges  

Python packages (install via pip):

```bash
pip install pandas sqlalchemy pymysql python-dotenv tabulate
```

## Setup & Run

1. **Clone the repo** and `cd` into it.  
2. **Configure your `.env`** (copy from `.env.example`) with:

   ```dotenv
   CMSC408_HW8_USER=…
   CMSC408_HW8_PASSWORD=…
   CMSC408_HW8_HOST=…
   CMSC408_HW8_DB_NAME=world_bank_data
   ```
3. **Load data** into MySQL (creates `wdi_country`, `wdi_series`, `wdi_data`):

   ```bash
   quarto render loader.qmd --to html
   ```
4. **Run the analysis** and generate your report:

   ```bash
   quarto render report.qmd --to html
   ```
   
5. **Verify** that all 21 tasks display results and that the Reflection section appears correctly in the rendered `report.html`.  