# Databricks Crypto Automation Project
## Overview  
This project wasn’t part of any class or assignment, I built it entirely for myself to improve my understanding of working within the Databricks framework and Apache Spark. 

I’ve used web scraping before (usually with pandas.read_html() when extracting tables from websites), but I wanted to go further this time, specifically, to automate the process so it could run on its own without manual intervention.

The data source itself wasn’t the main focus, but I decided to use cryptocurrency data because it’s dynamic, interesting, and something I wanted to learn more about along the way.

## Tools & Technologies

**Databricks** (for orchestration, scheduling, and SQL queries)

**Apache Spark** (for distributed data handling)

**Python** (for web scraping and ETL logic)

**SQL** (for dashboard-ready transformations)

**Yahoo Finance** (as the data source)

## Project Workflow
1. Automated Web Scraping

I began by creating a notebook called Crypto Data Scraper.ipynb, which scrapes Yahoo Finance for the 25 most actively traded cryptocurrencies.

The script cleans and stores the data into a historical Databricks table named historical_crypto_trends, with attributes including:
- symbol (primary key)  
- name  
- price  
- change  
- change_percent  
- market_cap  
- volume  
- circulating_supply  
- scrape_date  
Each new run appends fresh data, creating a continuously growing historical record.

2. Data Transformation (SQL)

Once the historical table was established, I wrote a series of SQL queries to extract insights such as:  
- The current price of each cryptocurrency  
- The price during the last few scrapes  
- Percent changes and ranking by volume or market cap  
- These queries were organized and stored inside a folder called Dashboard_queries.  

3. Dashboard Query Automation

To make the data easily consumable, I created a Dashboard Refresher Query, which automatically triggers the smaller queries after the scraper job completes.

This ensures all dependent tables update in sequence — keeping the dashboard in sync with the most recent data scrape.

4. Dashboard Visualization

Finally, I built a Databricks dashboard that displays:  
- The current prices of top cryptos like BTC, ETH, and SOL  
- A time-series graph showing BTC’s price trend over time  
- Summary metrics highlighting changes and rankings  
-  After configuring job sequencing in Databricks, the process runs automatically from data collection to dashboard refresh.

## Results

By the end of the project, I achieved a fully automated data pipeline that:  
- Scrapes live crypto data from Yahoo Finance  
- Stores it in a historical table  
- Runs multiple SQL transformations  
-  Updates a Databricks dashboard automatically  
While the dashboard itself isn’t the flashiest, this project was a personal success, it helped me strengthen my understanding of Databricks, Spark, and automation pipelines.

## Future Improvements
- Cleaner and more dynamic dashboards
- More efficient SQL queries
- Integrating ML-based forecasting (e.g., predicting BTC price trends)
- Broader data sources beyond Yahoo Finance
