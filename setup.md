# Setup Instructions

## 1. Start and Access Docker Container
```bash
docker start myproject 
docker exec -it myproject /bin/bash
```

## 2. Setup PostgreSQL Database
```sql
-- Connect to PostgreSQL
psql -U postgres

-- Create a new database
CREATE DATABASE my_portfolio_internet_pricing;

-- Create a new user with a password
CREATE USER my_portfolio_internet_pricing WITH PASSWORD '12345';

-- Verify database creation
SELECT datname FROM pg_database;

-- Connect to the newly created database
\c my_portfolio_internet_pricing postgres

-- Grant all privileges on the public schema to the user
GRANT ALL ON SCHEMA public TO my_portfolio;
```

## 3. Install Dependencies
```bash
pip install xlsx2csv
```

## 4. Convert Excel File to CSV
```bash
xlsx2csv "Data pricing.xlsx" "Data pricing_formatted.csv"
```

## 5. Start Jupyter Notebook
```bash
jupyter lab
```

## 6. Set Up Environment Variable in Jupyter Notebook
```python
%reload_ext sql
%env DATABASE_URL=postgresql://my_portfolio:12345@localhost:5433/my_portfolio_internet_pricing
```

## 7. Import Data into PostgreSQL
```python
import pandas as pd
from sqlalchemy import create_engine
import os

# Retrieve the database URL from the environment variable
DATABASE_URL = os.getenv('DATABASE_URL')

# Create the SQLAlchemy engine
engine = create_engine(DATABASE_URL)

# Load your DataFrame from CSV
df = pd.read_csv("Data_pricing_formatted.csv")

# Insert data into PostgreSQL table
df.to_sql('internet_pricing', engine, if_exists='replace', index=False)

# Close the engine
engine.dispose()
```
