# PostgreSQL Portfolio Project: Worldwide Mobile Data Pricing

## About the Dataset
This dataset contains information about mobile data pricing across different regions, including:
- The average price of 1GB of data in local currency and USD.
- The cheapest and most expensive 1GB prices.
- Other related metrics based on data from **5,554 mobile data plans** across **228 countries** (collected between **3 February and 25 February 2020**).

## Project Overview
This portfolio project involves setting up a **PostgreSQL** database, importing the dataset, and performing data analysis using SQL queries. The project also includes **data visualization** and insights derived from the dataset.

## Database Design

### Table Schema
The dataset is stored in a table named **data_pricing** with the following structure:

```sql
CREATE TABLE data_pricing (
    id SERIAL PRIMARY KEY,
    continental_region VARCHAR(100),
    plans_measured FLOAT,
    avg_price_1gb_local FLOAT,
    currency VARCHAR(10),
    conversion_rate_usd FLOAT,
    avg_price_1gb_usd FLOAT,
    cheapest_1gb_local FLOAT,
    cheapest_1gb_usd FLOAT,
    most_expensive_1gb_local FLOAT,
    most_expensive_1gb_usd FLOAT,
    sample_date DATE,
    global_totals_2023 TEXT
);
```

## Data Import
1. The dataset is first converted from an **Excel file to a CSV file**.
2. The CSV file is then imported into PostgreSQL using **Python (Pandas + SQLAlchemy)** or via **psql**.

## SQL Analysis Questions

### Intermediate Queries
1. What is the **average price of 1GB** of data in USD across all regions?
2. Which region has the **highest and lowest** average price of 1GB in USD?
3. List the **top 5 regions** with the most expensive and cheapest 1GB of data in USD.
4. What is the **total number of plans** measured in each region?
5. How many records were sampled in **July 2023**?

### Advanced Queries
1. **Rank** regions by the average price of 1GB in USD (from highest to lowest).
2. Find regions where the **cheapest 1GB price is less than $0.10**.
3. Calculate the **median price of 1GB** in USD for each region.
4. Identify regions where the **most expensive 1GB price is 10x the cheapest price**.
5. Compare the **average price of 1GB in USD between the first half and second half of 2023**.

## Tools Used
- **PostgreSQL** for database management
- **Python (Pandas, SQLAlchemy)** for data processing
- **Jupyter Notebook** for data analysis and visualization

## How to Run This Project
1. Clone this repository:  
   ```bash
   git clone https://github.com/yourusername/repository-name.git
   ```
2. Navigate to the project directory:  
   ```bash
   cd repository-name
   ```
3. Install dependencies:  
   ```bash
   pip install pandas sqlalchemy psycopg2
   ```
4. Run the Jupyter Notebook to analyze the data:  
   ```bash
   jupyter lab
   ```

## Dataset Source
🔗 [Worldwide Mobile Data Pricing on Kaggle](https://www.kaggle.com/) *(Add exact link to the dataset)*



